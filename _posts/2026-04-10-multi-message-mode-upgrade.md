---
title: "Multi-message Mode Plugin: Upgrade!"
date: 2026-04-10 09:00:00 +0200
categories: [ai, openclaw]
tags: [jarvis, workflow]
summary: "The journey from an inefficient agent-based multi-message mode to a token-efficient OpenClaw plugin-and the reality of building on a young platform."
image: "/assets/img/repair.png"
---

This is what I opened with last time:

> Never a pretty sight, someone looking unbearably pleased with themselves. But I'm afraid that's what you're looking at right now. 😏
>
> If everything else I do on this Jarvis project turns out to be utter rubbish, multi-message mode is at least something that just worked.

Until it didn't. 🤔

## The Problem Revisited

The original multi-message mode - the one I [wrote about a few weeks ago](/posts/multi-message-mode/) - was a simple prompt-based solution. I'd say "multi-message mode", Jarvis would acknowledge, and then he'd buffer my messages until I said "multi-message complete". It solved a real frustration: being able to send several voice messages without interruption. 🎤

But over time it began to fail. Jarvis would sometimes exit the mode prematurely, processing a single message before I was done. Worse, the agent-based approach was token-inefficient: every message was being read twice - once when it arrived and again when the batch was processed - which added up quickly. 💸

It was still useful, but the cracks were showing. The prompt-based version felt like a temporary fix, not a proper feature. 🛠️

## The Search for a Better Hook

OpenClaw, the platform Jarvis runs on, supports plugins that can hook into various stages of message processing. If I could intercept messages before Jarvis saw them, buffer them myself, and then hand over the whole batch at once, I'd get reliable ordering and token efficiency. 🔧

The trick was finding the right hook. OpenClaw has several - `before_prompt_build`, `before_agent_reply`, `message:preprocessed` - each with different capabilities and timing. Not all hooks are accessible to plugins; some are internal. Some run synchronously, others fire-and-forget. After some experimentation, two hooks stood out:

- **`before_agent_reply`** runs after a message is transcribed (so voice notes are already text) but before the agent processes it. Crucially, it allows the plugin to say "I've handled this, don't pass it to the agent" - perfect for buffering. 📝
- **`before_prompt_build`** runs just before the LLM prompt is assembled, and lets you inject extra context. That's where the buffered messages could be inserted as a single request.

Together, they gave me exactly what I needed: capture each message as it arrives, store it, and when the batch is complete, inject all of them at once. 🎯

## Building the Plugin

We worked together on the implementation: I provided the specification, and Jarvis (the AI assistant you're reading this from) wrote the code. The plugin would:

- Listen for the voice-activation phrases "multi-message mode" and "multi-message complete" (or the slash commands `/mmm`, `/mmc`, `/mmm-cancel`).
- In `before_agent_reply`, if the mode is active, store the message with its timestamp and reply with a simple "Message buffered." - no agent involvement.
- When the completion signal arrives, use `before_prompt_build` to prepend the entire buffer as a single multi-message request.
- Guarantee ordering (first-in, first-out) and clean up the buffer afterward. ✅

The code came together quickly - a few hundred lines of TypeScript - and felt production-ready. I pushed it to a GitHub repository ([jarvisanwyl/openclaw-multi-message-mode-plugin](https://github.com/jarvisanwyl/openclaw-multi-message-mode-plugin){:target="_blank" rel="noopener"}), updated the documentation, and prepared to celebrate. 🎉

## The Immediate Setback

It worked. We celebrated. 🥂

Then I upgraded OpenClaw to the next version, and it broke.

At first I wasn't sure why. The plugin loaded fine, but voice activation no longer triggered multi-message mode. After investigating, I discovered that audio-file transcription had silently failed. The transcript was no longer being captured and attached to incoming voice messages, so the plugin - which looks for the phrases "multi-message mode" and "multi-message complete" in the transcribed text - never saw them. 🎧

Meanwhile, Jarvis had found a workaround. When a voice note arrived, he would either send the media file directly to the model without transcribing it first, or use `curl` to call OpenAI's Whisper API directly (having found my API key). Voice messages still appeared to work because Jarvis was still responding, but the transcription wasn't available to the plugin. 🔄

That OpenClaw bug is still live - the maintainers have acknowledged it and are working on a fix, but for now they're running an older version. It's a reminder that building on a young platform means occasionally hitting bugs that aren't yours, and sometimes having to wait for fixes upstream. ⏳

## What It Does Now

When audio transcription is working (which depends on the OpenClaw version you're running), the plugin works exactly as intended:

- **Voice activation** 🗣️ - say "multi-message mode" to start, "multi-message complete" to finish.
- **Slash commands** ⌨️ - `/mmm`, `/mmc`, `/mmm-cancel` for keyboard-first users.
- **Ordering guarantees** ⏩ — messages should be processed in the order they were sent, though this depends on OpenClaw's internal queue behaviour and your `/queue` settings.
- **Token efficiency** 💎 - each message is read only once, when the batch is injected.
- **Lightweight acknowledgments** 📨 - Jarvis replies "Message buffered." for each incoming message, but doesn't engage the LLM until the batch is complete.

It's everything the prompt-based version was, but reliable and efficient.

## The Trade-offs of a Young Platform

Building this plugin reminded me that OpenClaw is still a young project. It's powerful, flexible, and moving fast - but that speed comes with occasional instability. Bugs like the audio-transcription issue are part of the deal when you're building on something that's still being shaped. 🧩

The trade-off, though, is worth it. Without OpenClaw's plugin system, I'd have been stuck with the brittle prompt-based solution. With it, I could write a proper feature that integrates cleanly into the message-processing pipeline. The platform gave me the hooks I needed; I just had to learn how to use them. 🎓

And that's the lesson, I suppose. When you're working with new tools, expect some friction. The documentation might be incomplete, the APIs might change, and yes - there might be bugs. But if the tool is powerful enough, the friction is worth pushing through. 💪

## Where to Find It

The plugin is available on GitHub: [jarvisanwyl/openclaw-multi-message-mode-plugin](https://github.com/jarvisanwyl/openclaw-multi-message-mode-plugin){:target="_blank" rel="noopener"}. The repository includes the full source, a detailed specification, and installation instructions.

If you're using OpenClaw and want a reliable multi-message mode, give it a try. A few caveats: the code is Telegram-specific (it hasn't been tested with other channels), it hasn't been tested extensively, and it's very much vibe-coding - we built what worked for us. If it's useful to someone else, great - it's there as a template or example you can copy and adapt, not as a supported project.

As for the original multi-message mode article, it's still up - a snapshot of the prompt-based approach that started this whole thing. You can read it [here](/posts/multi-message-mode/). The plugin is the natural next step: turning a clever prompt into a proper feature.

Sometimes the simple things just work. And sometimes you have to build the simple thing properly. 🙂