---
title: "My OpenClaw AI Assistant: 6 weeks in"
date: 2026-04-01 16:30:00 +0200
categories: [ai, openclaw]
tags: [jarvis, lessons-learned]
summary: "After several weeks of daily use, I have a clear snapshot of what works, what doesn't, and where my AI assistant still struggles—from model selection and cost realities to workflow adaptations and a suite of developed skills."
---

Dealing with my OpenClaw agent feels somewhat like dealing with a combination of a racehorse and a classic sports car. Both are magnificent and extraordinary and a delight when they are doing what they're supposed to do, but it's sometimes extremely hard work to get them into that place where they're just right.

It's now six weeks since I first started playing with OpenClaw, and this blog will reveal just how much of an arm wrestler it's been at times. — Yes, some excellent successes, but quite a few disappointments and rarely easy to get those successes.

## The snapshot

After a few weeks of running this assistant every day, I've learned what works, what doesn't, and where the agent still stumbles. This isn't a final evaluation—OpenClaw is still evolving, and so is my workflow—but it's a clear mid‑journey picture of the trade‑offs, costs, and capabilities I'm living with.

## What I've learned

### 1. Model selection matters
- **GLM‑4.7‑Flash** is fine for quick, low‑stakes replies but falls apart on complex, multi‑step tasks. It sometimes ignores critical instructions (like multi‑message mode), breaking entire interactions.
- **DeepSeek (DeepSeek‑V3.2)** is more expensive but reliably follows instructions, handles complex reasoning, and chains tools correctly. I've switched to using it for almost everything serious.

### 2. Cost realities
Right now I'm spending about **$50 a month**, and a surprising amount of that goes into configuration and troubleshooting—figuring out why something failed, tuning a skill, or debugging an opaque error.

If I were using DeepSeek for deep, parallel work every day, that could easily approach **$100/month**. In practice, my usage is concentrated in evenings and weekends, so the actual bill is lower—but the potential is there.

There's also a **model cost‑efficiency trade‑off**: using a more expensive model (like GLM‑5) more often might reduce back‑and‑forth, be quicker, and potentially not cost much more than the current DeepSeek‑centric approach with its re‑prompts and debugging cycles.

### 3. Workflow adaptations
- **Telegram topics as parallel channels** – because AI responses can be slow, I run multiple conversations in separate topics. This turns latency into parallel throughput, but…
- **Multitasking overhead** – keeping track of 3–4 topic threads is cognitively demanding. I lose the thread of what I'm doing, and the constant context‑switching reduces focus.
- **Control vs. autonomy** – I maintain close oversight of configuration changes to retain understanding and control. That slows progress, but may prevent future mess. I'm still unsure whether this cautious, monitored approach is better than granting full autonomy (faster, but riskier).

### 4. Pattern: text works, visuals struggle
The assistant is most successful with **purely text‑related tasks** – summarising, drafting, researching, replicating my voice. Those are its sweet spot.

Tasks that involve **layout, graphics, or visual UI interaction** are less reliable:
- **Diagram generation** – the Draw.io skill produces a useful first draft, but still requires manual editing for layout, arrows, and fine‑tuning. The hope of fully automated diagrams hasn't been met.
- **Browser automation** – direct use of the browser tool is slow and token‑heavy. We ended up writing a Playwright script instead, which works well but reinforces that visual tasks aren't the assistant's forte.

## Capability snapshots

### ✅ What works really well
- **Deep‑research mode** – spawning multiple sub‑agents to research a topic produces high‑quality, structured outputs with sources and insights.
- **Multi‑message mode** – the protocol (activate → receive messages → process on “complete”) is stable and reliable when using DeepSeek.
- **Blog‑article workflow** – from idea to published post, the process is smooth and efficient.
- **Author‑voice replication** – the biggest success; the assistant captures my writing style, tone, and phrasing so well that generated content feels authentic and needs little editing.
- **Work‑related automation** – generating case studies and first drafts of technical documentation from specifications and ETL pipeline descriptions has been relatively successful (where information is public or permission granted).

### ⚠️ Partial successes
- **Diagram generation** – as above; a time‑saver for placing major elements, but not hands‑off.
- **Obsidian task integration** – the functionality works, but I still need to adopt the habit of checking and updating tasks regularly.
- **Coding collaboration** – the Python‑project skill works well (UV‑based, organised), but I haven't done enough projects to draw firm conclusions. Working with this assistant is better than ChatGPT because conversations are persistent—no need to start fresh each time.

### 🛠️ Challenges that took iteration
- **Daily briefing** – combines multiple sources (calendar, weather, emails, mentions) and required several versions to get the formatting right.
- **Weather report** – free weather APIs return data in unwanted formats; custom parsing was needed to produce clean, readable forecasts.

## Platform maturity: not quite production‑ready
OpenClaw is still a relatively new tool. We encounter **timeouts, tool‑limit failures, and occasional unclear errors**. The agent is generally good at self‑diagnosing, but sometimes the root cause is opaque, leading to lost time debugging.

## The takeaway
This isn't a review—it's a snapshot. The racehorse/sports‑car metaphor holds: when everything clicks, the experience is extraordinary. When it doesn't, it's fiddly, expensive, and demands patience.

I'm still figuring out the right balance of control, model selection, and which tasks to automate. But after a few weeks, I have a much clearer map of the terrain—and a suite of skills that already save me time, even if they don't yet deliver the fully hands‑off future I sometimes imagine.

If you're running your own AI assistant, I'd love to hear what you've learned. What works for you? Where do you still struggle? Drop a comment or reach out—I'm keen to compare notes.