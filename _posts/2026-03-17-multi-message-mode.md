---
title: "Multi-message Mode"
date: 2026-03-17 15:00:00 +0100
categories: [jarvis]
tags: [openclaw, voice, productivity, workflow]
summary: "A simple solution to a specific frustration: how to send multiple voice messages to an AI assistant without it reacting to each one."
---

Never a pretty sight, someone looking unbearably pleased with themselves. But I'm afraid that's what you're looking at right now.

If everything else I do on this Jarvis project turns out to be utter rubbish, multi-message mode is at least something that just worked.

## The Problem

The frustration built up gradually. I'd have an idea I wanted to capture—a blog post outline, a new feature—and I'd reach for my phone to send it via Telegram. Voice message, naturally. Much faster than typing.

But Jarvis reacted to every message immediately. I'd record my first thought, hit send, and before I could collect the second thought, he'd be responding. The problem wasn't just the interruption—it was that I'd start trying to structure things in my head before I was ready, losing the thread entirely.

What I wanted was simple: a way to send multiple voice messages and have Jarvis wait until I was done before doing anything.

## The Solution

Multi-message mode. When I say "Multi-message mode," Jarvis responds "Multi-message mode activated." Then for every message I send, he replies only with "Multi-message mode: message received." When I'm finished, I say "Multi-message complete," and only then does he process everything together.

It's a handful of rules in a configuration file:

```markdown
The goal of multi-message mode is to allow Jon to send a set of instructions using several messages (usually voice)
one after the other without you doing anything until the end of all the messages.

Follow these instructions whenever you are asked to switch into multi-message mode:
1. Confirm that you are in multi-message mode by replying "Multi-message mode activated."
2. Until multi-message mode is deactivated, when you receive a new message from Jon, even if it tells you to do something, you must do **NOTHING**, I repeat **NOTHING**, except to reply "Multi-message mode: message received".
3. When you receive a message saying "Multi-message complete":
   - Confirm to Jon that you have understood by replying "Multi-message mode deactivated. Processing messages."
   - Review all the messages you have received since multi-message mode was last activated and act or respond to the overall message accordingly.
   - Revert to the normal behaviour of responding and acting after each message.
```

That's it. But the impact on my workflow has been significant.

## How It Feels

I can talk through an idea now without stopping, no need to get the structure right before I start. I just say the thing, say the next thing, realise I forgot something and say that too, then let Jarvis figure out what I was getting at. He's surprisingly good at it—I stammer, I repeat myself, I go off on tangents and circle back—but the transcription holds up (OpenAI's Whisper API, which costs pennies), and Jarvis synthesizes the jumble into something useful.

Here's what I didn't expect: I now use voice almost exclusively. Maybe 95% of my communication with Jarvis is spoken rather than typed, and when something requires typing—uploading a file, for instance—I feel actual reluctance. The friction of switching modes has become noticeable.

## The Trade-off

Which raises a question I've been turning over. If I'm typing less, what happens to the skill of structuring thoughts in writing? It's a familiar concern with AI assistance generally: the tools that help us can also erode the skills they were meant to support. I don't have an answer yet. Just something I'm watching.

For now, multi-message mode stays. It solved a real problem with remarkably little code, and it changed how I interact with Jarvis more than I expected.

Sometimes the simple things just work. 🙂
