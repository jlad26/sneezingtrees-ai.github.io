---
title: "The Genesis of Jarvis"
date: 2026-03-15 17:32:00 +0100
categories: [ai, openclaw]
tags: [ai-assistant, openclaw, personal-automation]
summary: "How I ended up building a personal AI assistant called Jarvis, and why OpenClaw won out over the alternatives."
---

I heard Peter Steinberger talking about OpenClaw on the Lex Fridman podcast, and something clicked. Not in a dramatic "everything changed" way, more like a quiet "oh, this is what I've been looking for" moment. By the end of the episode I'd decided to build a personal AI assistant.

I called it Jarvis, because of course I did.

## Why Bother?

The choice wasn't obvious. Claude Desktop was right there — polished, easy, already on my machine. Copilot comes baked into everything Microsoft touches. Cursor and the various AI editors are genuinely impressive. Why go to the trouble of setting up something from scratch?

A few things nudged me toward OpenClaw.

I wanted something that could actually *do* things, not just talk about them. Email triage, calendar management, notifications that cut through the noise rather than add to it. Most AI tools are brilliant conversationalists but frustratingly helpless when you need them to touch your actual data.

I also wanted it on my terms. Telegram is where I live for messaging. My second brain lives in Obsidian. My calendar situation is... complicated, spread across multiple Google accounts. I didn't want an AI that forced me into its ecosystem — I wanted one that would work with mine.

And honestly, I wanted to understand how it worked. Not the model internals, I'm not that kind of engineer, but the architecture. The wiring. The way pieces actually connect.

OpenClaw is open source, runs on my own infrastructure, and has a skill system that means I can extend it rather than work around it.

## The Ground Rules

Before diving in, I set some parameters for myself. Partly to keep things sane, partly because this is a side project alongside a full-time job and there are only so many hours in the week.

**Learn by doing.** I wanted to understand how to build an OpenClaw agent through hands-on experience, not just copy-paste someone else's config and hope for the best.

**Cost-conscious.** The default model for OpenClaw is Claude Opus 4.6 — excellent, but expensive. I wanted to find the right balance between cost and performance, using cheaper models where they make sense rather than defaulting to the premium option every time. Right now I'm running Kimi K2.5 as my default, with GLM 4.7 Flash for lighter tasks.

**Embrace the mess.** The development process is not going to be as robust as what I do professionally. That's fine. This is a personal project.

**Fun over friction.** Where there are barriers, I'll use AI to get around them. This should be enjoyable.

**Share the journey.** Hence this blog. My previous attempt at a web developer blog fell silent because writing posts took too long. This time, Jarvis helps me produce content. The assistant isn't just the subject of the story — it's the tool that makes sharing the story possible.

## The Architecture (Such As It Is)

The vision was straightforward enough: a unified personal assistant connecting communication, knowledge, and tasks. The reality, as always, is messier.

Telegram is the primary interface. Text works well, but voice turned out to be crucial. There's something natural about talking to an assistant while walking the dog, having it respond like a competent colleague rather than a glorified search engine.

The second brain — an Obsidian vault with semantic search — gives Jarvis actual memory. Ideas, projects, interests, references. When I ask about something we discussed last month, it can find it, which is more than I can say for myself sometimes.

Google Calendar integration handles family chaos across multiple calendars. Gmail triage filters the noise. Morning briefings land before I've finished my coffee with weather, schedule, and anything pressing.

None of this is revolutionary. Each piece is simple on its own. The interesting part is how it composes into something that feels cohesive.

## The Journey So Far

I'd love to say everything worked first time.

The LinkedIn automation skill I found looked promising until I actually tried to use it. The documentation assumed a tool access pattern that didn't exist. Hours of discovery followed: tools needed to be searched first, session IDs were dynamic, rate limits were enforced with an iron fist. My first attempt failed completely — I had to wait fourteen hours for the quota to reset.

But here's the thing: when something didn't work, I could fix it. I rewrote the skill with the actual working pattern. Now it works every time.

That's the difference between a black box and something you own. When the black box fails, you wait for an update. When your system fails, you debug, learn, improve it.

## What's Next

Still early days. The architecture works, the core integrations are solid, but there are plenty of rough edges. More skills to build, more workflows to automate, more ways for it to anticipate what I need before I ask.

But that's the point. I'm not waiting for someone else's roadmap. I'm building this as I go, learning what works, fixing what doesn't.

That's the genesis. Let's see where it leads.
