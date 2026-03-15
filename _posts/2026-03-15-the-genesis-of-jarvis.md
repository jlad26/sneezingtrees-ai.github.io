---
title: "The Genesis of Jarvis"
date: 2026-03-15 17:32:00 +0100
categories: [ai, openclaw]
tags: [ai-assistant, openclaw, personal-automation]
summary: "How I ended up building a personal AI assistant called Jarvis, and why OpenClaw won out over the alternatives."
---

I've spent years working with AI, but until recently, I'd never built something that felt like *mine*. Models, APIs, RAG pipelines, chatbots for clients—plenty of those. But a system that lives in my pocket, knows my calendar, reads my emails, and quietly gets on with things? That was always someone else's demo, not something I actually used.

Then I stumbled across OpenClaw, and things got interesting.

## The Decision

The choice wasn't obvious. Claude Desktop was right there—polished, easy, and I already had a subscription. Copilot comes baked into everything Microsoft touches. Cursor and the various AI-powered editors are impressive. Why bother with something that requires actual setup?

A few reasons converged.

First, I wanted something that could *do* things, not just talk about them. Email triage. Calendar management. Notifications that matter. Most AI tools are brilliant conversationalists but helpless when you need them to actually touch your data.

Second, I wanted it on my terms. Telegram is where I live for messaging. My second brain lives in Obsidian. My calendar is Google, but spread across multiple accounts. I didn't want an AI that forced me into its ecosystem—I wanted one that adapted to mine.

Third, and this mattered more than I expected: I wanted to understand how it worked. Not the model internals, but the architecture. The wiring. The way pieces connect.

OpenClaw offered all three. It's open source, runs on my own infrastructure, and its skill system meant I could extend it to work with my tools rather than against them.

## The Architecture

The vision was simple enough: a unified personal assistant that connects communication channels, knowledge management, and task automation. The execution, as always, was where things got interesting.

Telegram became the primary interface—text and voice. Voice turned out to be crucial. There's something profoundly natural about talking to an assistant while walking the dog or driving, and having it respond like a competent colleague rather than a glorified search engine.

The second brain—an Obsidian vault with semantic search—gives Jarvis memory beyond the current conversation. Ideas, projects, interests, references. When I ask about something we discussed last month, it can actually find it.

Google Calendar integration handles the family chaos across multiple calendars. Gmail triage filters the noise and surfaces what matters. Morning briefings deliver weather, schedule, and tasks before I've finished my coffee.

None of this is revolutionary. Each piece is straightforward on its own. The magic is in the composition—a system that feels cohesive rather than cobbled together.

## The Journey

I'd love to say it all worked first time. It didn't.

The LinkedIn automation skill I found looked promising until I tried to use it. Turns out the documentation assumed a direct tool access pattern that didn't actually work. I spent hours discovering that tools needed to be searched first, that session IDs were dynamic, that rate limits were enforced with an iron fist. The first attempt failed hard; I had to wait fourteen hours for the quota to reset.

But here's the thing: when something didn't work, I could fix it. I rewrote the skill with the actual working pattern. Now it works every time.

That's the difference between a black box and something you own. When the black box fails, you wait for an update. When your system fails, you debug, learn, and improve it.

## The Voice Problem

One of the earliest challenges was voice input. Dictating a complex request in a single monologue is difficult. Natural speech requires pauses for thinking, structuring ideas, deciding what to say next. But an AI assistant interprets each message as a complete instruction—mid-thought execution leads to mid-thought errors.

The solution emerged through conversation: multi-message mode. A protocol that lets me send several voice messages in sequence, the assistant acknowledging each one but waiting until I signal completion before acting. Simple concept, profound impact on usability. Voice interaction went from frustrating to natural.

This is the kind of problem you don't encounter until you actually use something. And the kind of solution you can implement when you control the system.

## What's In a Name

I called it Jarvis. Yes, after the Iron Man assistant. No, I'm not embarrassed.

The name matters more than it should. When I'm asking something to read my emails and manage my calendar, "the AI assistant" feels clinical. "Jarvis" feels like a colleague. It's a small cognitive shift, but it changes how I interact with it—and how I think about what it's doing.

## What's Next

This is still early days. The architecture works, the core integrations are solid, but there's plenty of rough edges to sand down. More skills to build. More workflows to automate. More ways for it to anticipate what I need before I ask.

But that's the point. I'm not waiting for someone else's roadmap. I'm building this as I go, learning what works, fixing what doesn't, and gradually arriving at something that genuinely helps.

That's the genesis. Let's see where it goes.
