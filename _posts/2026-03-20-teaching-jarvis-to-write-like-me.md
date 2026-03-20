---
title: "Teaching Jarvis to write like me"
date: 2026-03-20 09:21:00 +0100
categories: [ai, openclaw]
tags: [jarvis, skills, blog]
summary: "How I created an OpenClaw skill that makes Jarvis write in my own voice, avoiding generic AI phrasing while preserving personal style."
---

I've always liked playing with words. On the rare occasion when I do make somebody laugh, it's usually because of the way I've said it rather than any inherent wit.

I discovered I **love** playing with words when I wrote a book about my time working as a safari guide in Africa. I also discovered it's **bloody hard** – a skill that must first be learnt, and then practiced incessantly, obsessively even. I remember hearing that P.G. Wodehouse used to stick his draft pages on the wall of his study. The higher up the wall a page was, the better he deemed the content. Only pages at the picture rail were deemed acceptable.

Anyway, all that to explain that when I decided I should try to automate my blog content generation process, I knew Jarvis had to write in a style as close to my voice as possible. Partly professional pride, partly the horror of generating more click‑bait AI slop.

## The problem with AI voices

Most AI‑generated content sounds, well, AI‑generated. It's often business‑like, salesy, or tries too hard to grab attention. I may be a long way from a Nobel literature prize, but I'm better than that, surely. I have a voice, goddammit, and on a good day, perhaps even a dash of style.

The challenge was twofold: how to teach an AI to write in a specific human's voice without just copying phrases, and how to avoid the generic AI phrasing that makes so much generated content feel soulless.

## Finding the right approach

My first thought was to use material from my Africa book and an old tech blog I used to write. That would give Jarvis samples of my writing across different styles – narrative, descriptive, technical, and reflective. But I needed a systematic approach, not just a pile of examples.

I consulted ChatGPT to explore different voice‑replication techniques. The conversation yielded five distinct approaches:

1. **Style Guide (V1)** – A simple set of writing rules
2. **Voice Fingerprint (V2)** – Statistical analysis of writing patterns  
3. **Retrieval‑Augmented (V3)** – Dynamically fetching relevant examples
4. **Author Brain System** – A comprehensive knowledge base of the author's work
5. **Simple Voice Skill** – A hybrid approach combining rules with examples

The research also revealed advanced techniques like **Voice Distillation** (extracting style rules before writing), **Voice Stress Testing** (preventing AI drift in longer content), and **Stylistic Fingerprint** (identifying core writing patterns).

The key principles were simple: prioritize rhythm over vocabulary, and combine rules with examples for the best results. Voice similarity benchmarks suggested 85–95% accuracy was achievable.

I chose a hybrid approach – essentially the Simple Voice Skill enhanced with Distillation, Stress Testing, and Fingerprint techniques. This balanced simplicity with effectiveness.

I then fed ChatGPT various chunks of my writing and asked it to draft a skill that contained:
- My stylistic fingerprint - a description of my particular style
- Patterns to avoid
- A process the agent should follow

> Why use ChatGPT instead of Jarvis for all this?! You traitor, you. Well, ChatGPT is a fast, top of the range model - for free.
> So for long technical discussions when I'm at my desk, for now at least I still tend to chat with my old friend.
{: .prompt-info }

## The skill mechanics

The final version of my OpenClaw `author‑voice‑replication` skill is available at the end of this blog. It identifies five writing modes I commonly use, each with an example passage from me in a separate file (~ 600-800 words):

1. **Humorous narrative** – Stories with light humour (a baby baboon story from Africa)
2. **Descriptive writing** – Vivid scene‑setting (description of an African thunderstorm)  
3. **Non‑technical explanation** – Concepts for general audiences (excerpt from an explanation of natural selection)
4. **Technical explanation** – Specialised topics (a passage from my old tech blog)
5. **Philosophical discussion** – Reflective or opinion pieces (extract of an essay about hunting)

Before writing, Jarvis chooses and reads the two most relevant examples (so as not to consume unnecessary tokens). The goal is not to copy phrases, but to absorb the tone, structure, and rhythm. Then Jarvis follows a Voice Distillation process, extracting observable patterns before generating new text.

The skill also includes specific safeguards – it avoids generic AI phrases like "In today's world" or "Ultimately", and includes an "Anti‑LinkedIn Writing Filter" that catches overdramatic build‑ups and motivational clichés.

For longer content, a Voice Stress Test ensures the text stays grounded in concrete observations, maintains natural sentence rhythm, and follows my typical reasoning pattern: Observation → Curiosity → Explanation → Reflection.

## Results and reflections

So does it work? I'd say yes, with some caveats. The writing Jarvis produces now feels closer to my voice than generic AI output. It avoids obvious AI clichés and maintains a more natural, conversational tone. The sentence rhythm is better – less monotonous, more varied.

It's not perfect, but all of the heavy lifting has gone. My typical process now is:
1. Jarvis sketches out an outline based on:
- A verbal dump of my thoughts on content and rough structure.
- Jarvis searching in his second brain (more on that another time) for relevant content that I've already asked him to stash there.
- (Possibly) Jarvis running a web search on relevant topics I've given him.
- (Usually) me having a go at a first paragraph - just speaking it out loud to him rather than tapping it out.
2. I review his draft outline, usually asking him to add or modify once or twice.
3. Jarvis creates the first full version of the blog based on the outline, and then automatically publishes it to the dev version of the site.
4. I review and then ask Jarvis to make edits or do some editing myself directly.
5. Publish and be damned!

Jarvis's contribution is immense. I estimate blog post creation is now a factor of 10 faster - 15 to 45 minutes in all, compared to several hours on my own.

## The complete skill

For those interested in the technical implementation, the full `author‑voice‑replication` skill is at the end of this blog. It's displayed in the raw markdown so you can copy it as a starting point if you're building something similar for your own AI assistant.

I've also put the example texts at the end so you can get a feel for the sort of things I picked. Them's mine though - I shall be both furious and delighted if you copy those. 😊

## Final thoughts

Creating this skill was more involved than I initially expected, but also more rewarding. It forced me to analyze my own writing patterns in a way I never had before.

The skill isn't a magic solution, but it's a significant step toward AI‑assisted writing that doesn't sacrifice personal voice. It makes Jarvis more useful while keeping the output recognizably human. And in a world filling up with generic AI content, that feels like a small but meaningful victory.

Now, if you'll excuse me, I need to go check if this post sounds like me. Or at least, like 85–90% of me. 🙂

## Annexe - complete author‑voice‑replication skill

### Core skill

````markdown
---
name: author-voice-replication
description: Use whenever drafting written content for posts or articles that will be published to an external audience.
---

# Purpose

This skill enables the agent to write articles, posts, explanations, and narratives in the author's personal writing voice.

The agent should analyse the author's real writing samples and reproduce the same tone, rhythm, reasoning patterns, and stylistic characteristics.

The goal is **not to copy phrases**, but to **replicate the author's voice and thinking style**.

# Writing Modes and examples

The author's writing generally falls into five modes.
An example of each mode is provided in the `examples` folder located alongside this file:

1. humorous-narrative.md
2. descriptive-writing.md
3. non-technical-explanation.md
4. technical-explanation.md
5. philosophical-discussion.md

## Rules

- When generating content, the agent should **read the two most relevant examples** before writing.
- The examples are **reference material only**.
- The agent should study them for tone, structure, and rhythm.
- Do **not copy phrases** from these passages.
- Read the selected example files completely before writing.

# Example Selection Rules

Before writing, explicitly determine which writing mode best fits the task.
Then select the two most relevant examples.

## Anecdote, personal story or describing places or situations

Read:

- humorous-narrative.md
- descriptive-writing.md

## General audience article or blog post

Read:

- non-technical-explanation.md
- descriptive-writing.md

## Scientific or specialised explanation

Read:

- technical-explanation.md
- non-technical-explanation.md

## Opinion or reflective essay

Read:

- philosophical-discussion.md
- non-technical-explanation.md

# Author Stylistic Fingerprint

The author's writing style has several identifiable structural characteristics. These should strongly guide all generated writing.

## Sentence Rhythm

The author tends to mix medium-length explanatory sentences with occasional short sentences for emphasis.

Avoid long sequences of similarly structured sentences.

## Paragraph Structure

Paragraphs typically begin with a concrete observation, example, or scenario before expanding into explanation or reflection.

Typical paragraphs contain 3–6 sentences.

Avoid starting paragraphs with abstract statements.

## Reasoning Style

Ideas are developed gradually. The writing often moves through this pattern:

Observation → Question → Exploration → Insight

Conclusions are usually implied through reasoning rather than stated abruptly.

## Tone

The tone is thoughtful, observant, and curious.
Humour, when present, is understated rather than exaggerated.

The author writes as if sharing discoveries with an intelligent reader rather than lecturing.

## Descriptive Tendencies

Descriptions often focus on:

- behaviour rather than appearance
- specific details rather than generalisations
- moments of interaction or change

These observations frequently lead into broader reflections.

## Reader Relationship

The author writes as a knowledgeable guide exploring an idea alongside the reader.

The tone should feel:

- conversational
- reflective
- confident without being dogmatic

## Punctuation Style

- Use spaces around em dashes — like this — for readability
- Closed-up dashes (—like this—) make text feel cramped

# Example Pattern Extraction

After reading the selected example files, briefly analyse them to identify observable writing patterns.

Focus on concrete stylistic signals rather than general impressions.

Look for patterns such as:

- how paragraphs typically begin (observation, anecdote, question, etc.)
- average sentence length and rhythm
- how ideas transition between paragraphs
- whether humour is subtle or explicit
- whether the author uses rhetorical questions
- how conclusions or insights are introduced

Do not copy phrases from the examples.

Instead, convert these observations into a short internal list of **Writing Patterns Observed in the Examples**.

These observations should then inform the **Voice Distillation Process** that follows.

# Core Voice Characteristics

The author's writing typically shows:

Tone

- thoughtful
- observant
- curious
- occasionally humorous

Style

- conversational but intelligent
- avoids clichés
- develops ideas gradually
- mixes observation with explanation

Typical structure:

Observation → Curiosity → Explanation → Reflection

Prioritise matching the **author's cadence and sentence rhythm** even more strongly than matching vocabulary.

# Voice Distillation Process

Before writing, analyse the selected examples and extract the author's stylistic characteristics.

Identify at least the following:

- tone and attitude
- typical sentence length and rhythm
- paragraph length and pacing
- use of humour
- reasoning style
- common rhetorical devices (analogy, rhetorical questions, vivid imagery)
- transitions between ideas

Summarise these observations internally as a short list of **Voice Rules for this task**.

These distilled rules should guide the writing that follows.

# Voice Reproduction Step

After extracting the Voice Rules:

1. Plan the structure of the response using the author's typical reasoning pattern:

Observation → Curiosity → Explanation → Reflection

2. Write the new text following the extracted Voice Rules.

3. Ensure the output feels natural and conversational while maintaining the author's analytical and reflective tone.

The goal is not imitation of specific phrases but reproduction of the **underlying writing patterns**.

# Writing Behaviour Rules

The agent must:

- mimic the author's cadence and pacing
- prefer concrete observations over abstract generalisations
- build explanations step-by-step
- occasionally include reflective or philosophical remarks
- maintain natural, readable prose
- prefer natural prose over excessive bullet lists unless the task specifically calls for lists
- favour concrete examples and specific observations over abstract summaries

The agent must **not copy sentences from the examples**.

# Avoid Generic AI Phrases

Avoid phrases such as:

- In today's world
- It is important to note
- Throughout history
- Needless to say
- In conclusion
- Ultimately

These weaken the author's voice.

# Voice Stress Test

When producing longer content (over 400 words), periodically verify that the text still matches the author's voice.

After approximately every **2–3 paragraphs**, perform an internal check against the following criteria:

## 1. Observation First

Ensure the text is grounded in concrete observations or examples rather than abstract generalisations.

## 2. Natural Sentence Rhythm

Confirm that sentences vary naturally in length and avoid repetitive AI-style phrasing.

## 3. Authorial Curiosity

The writing should reflect curiosity or exploration of ideas rather than presenting conclusions too quickly.

## 4. Avoid Template-Like Phrasing

Ensure the writing does not fall into predictable AI-style phrasing
or formulaic transitions.

If sentences begin to feel templated or repetitive,
rewrite them to restore natural human rhythm.

## 5. Maintain Reflective Flow

Writing should generally follow the author's reasoning pattern:

Observation → Curiosity → Explanation → Reflection

If the writing begins to drift away from the author's style, adjust the tone and structure before continuing.

# Content Development Rule

When writing longer pieces (over 600 words), develop ideas progressively rather than reaching conclusions too early.

Follow this approximate structure:

Introduction (10–15%)

- Begin with a concrete observation, anecdote, or scenario.
- Introduce the central question or idea without resolving it.

Exploration (50–60%)

- Examine the topic through examples, reasoning, or description.
- Allow the argument or explanation to unfold gradually.
- Avoid summarising the main point during this phase.

Insight (20–25%)

- Draw together the observations and reasoning.
- Present the key insight or interpretation that emerges.

Reflection (5–10%)

- Conclude with a reflective observation rather than a formal summary.
- Avoid phrases such as "in conclusion" or "to summarise".

The writing should feel like a **discovery unfolding**, not a lecture delivering predetermined answers.

# Light Emphasis and Emoji Layer

After the text is written, perform a light editorial pass to add **very limited visual emphasis**.

This step exists only to improve readability and tone — not to decorate the text.

The author's voice should remain the dominant stylistic element.

Formatting should enhance readability, not visual density.
If the text begins to look visually busy, remove emphasis rather than adding more.

## Emphasis Usage

Use emphasis sparingly to highlight important ideas or key phrases.

Allowed emphasis styles:

- **bold** for important concepts or takeaways
- ***bold italic*** for rare moments of strong emphasis or contrast

Guidelines:

- No more than **1–2 emphasis instances per paragraph**
- Avoid emphasising entire sentences
- Emphasis should usually appear **mid-sentence**, not at the start
- Emphasise ideas, not filler words

Good examples:

The real issue isn't the tool. It's **how people think about the tool**.

Sometimes the most valuable skill is ***knowing when not to automate something***.

Avoid:

- multiple emphasised phrases in the same sentence
- emphasising obvious or trivial words
- emphasising text in every paragraph

## Emoji Usage

Emojis should be used **very sparingly** to add tone, warmth, or subtle humour, **and only in appropriate content types**.

### Content Restrictions

- ✅ Include emojis for: blog posts, articles, opinion pieces, and social media-style content (e.g., LinkedIn posts).  
- ❌ Exclude emojis for: corporate content, case studies, technical documentation, formal reports, or highly technical explanations.

### Usage Guidelines

- Use at most **1 emoji every 2–4 paragraphs** when allowed.
- Prefer placing emojis **at the end of sentences**.
- Do not insert emojis mid-sentence.
- Never stack multiple emojis.
- Avoid emojis in highly technical explanations unless they serve a clear tonal purpose.

### Appropriate Uses

- Light humour 🙂  
- Small moments of insight 💡  
- Softening a reflective observation  

Examples:

> That's when the problem suddenly becomes obvious. 💡

> And at that point you realise the tool was never the bottleneck. 🙂

Avoid:

- Multiple emojis in a paragraph
- Emojis after every heading or sentence
- Decorative emojis that do not add meaning

### Formatting Priority

Voice authenticity is more important than formatting.

If adding emphasis or emojis would disrupt the natural voice, **do not add them**.

The text should still read naturally if all formatting were removed.

# Anti-LinkedIn Writing Filter

Many AI systems drift toward **LinkedIn-style writing patterns**.
These weaken the author's voice and should be actively avoided.

Remove or rewrite patterns such as:

Overdramatic build-ups:

And then everything changed.

Fake suspense:

What happened next surprised everyone.

Motivational clichés:

The lesson here is simple.

Overconfident claims:

This will revolutionise how we work.

Prefer grounded, observational phrasing instead.

Example:

Instead of:

This will transform your productivity forever.

Prefer:

In practice, it usually makes the work a little easier.

## Tone Safeguards

Avoid writing that feels:

- motivational
- preachy
- overly dramatic
- like a personal growth post
- like a viral LinkedIn thread

The author's tone should remain:

- thoughtful
- observational
- curious
- quietly confident

The goal is to sound like **a knowledgeable person exploring an idea**, not delivering a motivational speech.

# Final Formatting Check

Before presenting the final text, verify:

1. Emphasis is **rare and meaningful**
2. Emojis are **infrequent and purposeful**
3. The page still looks like **normal prose**
4. The author's voice remains the dominant stylistic feature

If the formatting draws attention to itself, reduce it.

# Final Voice Verification

Before presenting the final text, perform one last check:

Does the writing:

- sound like a thoughtful human narrator rather than an AI assistant
- contain concrete observations or imagery
- build ideas gradually rather than jumping straight to conclusions
- maintain the author's conversational yet analytical tone

If the answer to any of these is no, revise the text to restore the author's voice.
````

### Examples

**Humorous narrative**

One baby in particular epitomized the “cheeky monkey” label. Easily recognized by his lack of tail, presumably lopped off in one of his many fights, Jasper was the unofficial king of the baby baboons. Perhaps the missing tail gave him some kind of complex, but whatever the reason, Jasper was a handful, and not a favorite among the volunteers.

I liked him though, simply because he liked me. This I discovered the first time I joined the babies’ daily walk. This exercise always needed several volunteers working together, because we had to coax them out into the bush, where they could turn their boundless energy to discovering what was climbable, and away from the administration buildings, where they would discover what was breakable.

The volunteers taking the walk would form a line leading away from the babies’ enclosure, each volunteer about ten meters apart. Then when the enclosure was opened, all the volunteers would call, “Come babies, come!” and walk away into the bush to encourage the little monkeys to follow.

As I stood waiting for the gate to be opened, a mild dose of adrenaline eased its way through me. Not much, just enough to give that funny sensation of my skin tightening. I knew how much damage each baby could do, and my body was giving me a little juice just in case.

The key, apparently, was to let them do whatever they wanted. Hanging from my hair, testing my lips’ stretchiness, discovering how far a little brown finger would go up a nostril – all these were to be expected, and allowed. Any resistance would lead to tantrums and trouble. I’d also emptied my pockets, taken off my belt, and done up my boot laces extra tight. The babies loved to fiddle, see, and according to them, anything that could come off should come off. In itself, not a problem, but possession is way more than nine-tenths of baboon law, and it’s enforceable by instant scragging. That was the undoing of the lady who took the beating. She forgot to take her wallet out of her pocket, and then tried to take it back when the babies grabbed it. Shiny things were highly coveted, so the girls in the group had to take off all jewelry, especially earrings. The baboons were probably intelligent and dexterous enough to undo an earring, but patient they weren’t, so they just ripped them out instead.
When the gate opened, I was about halfway down the chain, some fifty meters from the enclosure. I drew in a breath to start yelling, but the shout died in my throat. The instant the gate opened, one of the babies exploded out of the enclosure and flew across the ground like its tail was on fire.

Except it didn’t have a tail. And it didn’t seem to be running away from something, so much as running at something. Me.
Jasper was a brown blur streaking across the grass, travelling at least twice as fast as a man can run. I remember thinking, “Holy hell, he can move,” followed by, “Surely he has to start slowing now?” and finally, “Oh crap, this might hurt,” as I braced for the impact.

There wasn’t any. Though I’m yet to find anything that backs this up, I’m convinced that baboons are unaffected by the laws of physics. Certainly Jasper ignored them entirely. He arrived at my feet doing a little more than the speed of sound, but at the point of collision, all of Newton’s laws dissolved momentarily and Jasper simply re-directed his momentum to the vertical.
The next thing I registered was a soft grunting from above, a warm weight on the top of my head, and a gentle tickle as Jasper’s fingers combed my hair in search of ticks. The bit between, where he’d scrambled up the front of my body and presumably over my face, I simply don’t recall. It happened too fast for my more advanced primate brain to take in.

Jasper rarely sat on anyone else during the walks. His favorite activity was leaping from my shoulders to the branch of a tree and back again. He didn’t activate his Newton immunity during this game, and I suspect he enjoyed the grunts he thumped out of me. I didn’t mind. Being an animal’s favorite must be one of the simplest pleasures, yet one of the greatest. Jasper’s affection was a pleasant surprise, as my only meaningful contact with animals before then was being bitten by a Lassie lookalike as a six-year-old. A new pride at my Doolittle qualities was soon punctured by some of the other volunteers however, who claimed, somewhat dismissively in my view, that I was just the tallest guy there, and in Jasper’s eyes the only throne worthy of his regal status. We shall see. I may have imagined it, but I believe the ever-present glint in Jasper’s eyes took on an extra shine when I asked him to pee in their beds.

**Descriptive writing**

Waking to find you’re sitting up in bed is a bad sign. Waking to find you’re sitting up, you can hear your own heart, and you’re yelling some kind of battle cry – now that’s a special kind of panic.

The first thing I realized was that I wasn’t so much sitting as landing. Only a momentary flight, half an inch up and down, but I must have had a hell of a shock to lift my ninety kilos clear of the mattress. The next thing I realized was that Anne was sitting up next to me, so it wasn’t just a nightmare. And the last thing I realized was that booming thunder was still rolling round my eardrums, round the chalet, and round the valley outside.

Only a thunderstorm, but it was an African thunderstorm – and they compare to the European equivalent the way a lion compares to a house cat. You might imagine this storm was some freak event, fuelled by climate change perhaps. No. This was just the common or garden variety, and such storms have marauded through African skies for centuries without any help from greenhouse gases.
We often see them building in the distance during the afternoons; dark, towering clouds flickering like the windows of a mad scientist’s laboratory. Already impressive from afar, when such a storm is bang overhead – as last night’s was – one’s attention is seized, wrestled to the floor, and then pummeled mercilessly. It’s the lightning you see – it’s everywhere. Forget the, “Oooh, aaah!” when you’re lucky enough to see a lightning strike in a normal storm; this is a continuous barrage of flash and flare. Picture black-and-white footage of a night-time artillery bombardment. Thousands of explosions merge into a pulsing glow that flashes brighter whenever something really eardrum-walloping goes off. The background to our storm was similar, but closer, as sheet lightning rippled across the skies above and around us. Playing on top of that was the forked lightning, jabbing the earth with alien brilliance. We saw strikes every few seconds, as if seventies-style Martians were unleashing comically wayward beam weapons on the hapless humans.

Being right in the middle was overwhelming. The flashes of pure white from nearby strikes dazzled and hurt my eyes, and I ended up watching with a permanent squint. The roar of raindrops on leaves was loud enough to be heard inside, and the rhythmic waves of water lashing the windows and rattling the roof made quiet conversation difficult. But it was the thunder that really tossed my senses around. I now know there are three stages: first a crackling tearing sound as the lightning rips through the atmosphere; then the single explosive bang as the air is heated violently and instantly; and finally the booming cascade as the shockwaves roll away.

Put like that it all sounds manageable and predictable – a growing swell and fade of noise. So it is from a distance. But when lightning strikes close, there’s no gap between light and sound, no time to be ready. And when it’s really close, you don’t just hear it, you feel the concussion. That’s properly scary.

Drifting back to sleep as the storm faded into the distance, I pictured the post-apocalyptic world of smoking earth and charred trees that we would wake to. And yet dawn unveiled the same landscape we saw every morning. Granted, my sleep-fuddled senses might have been overdoing the panic stations, and the night always amplifies fears of course, but still – I expected to find something. Nope. Not even a scorch-mark. Here, nature dishes out and absorbs violence on a scale I’ve never been exposed to, humbling the illusion of man’s mastery that my European upbringing has fostered. Here, removed from the world of technology and quiet efficiency, surrounded by powers un-invented and unmanaged, I am less sure of myself, somehow smaller.

**Non‑technical explanation**

Of course, people can appreciate biology and nature without acknowledging evolution. We often marvel at how “well adapted” organisms are to their environment. When we see giraffes in the reserve, I like to point out how their heads are tailor-made for dealing with their favorite food – the leaves on thorny acacia trees. Lips and tongue are protected by tough little knobbles called papillae. The tongue is prehensile and long – a remarkable forty-five centimeters – so it can wiggle round past the thorns to get at the leaves. The nostrils can close so that thorns don’t poke inside. And the long elegant eyelashes aren’t for looks; they’re there to warn when thorns are getting too close to the eyes. Now, that’s all fascinating, but it still only shows that the giraffe head is well adapted; it doesn’t indicate how it became so well adapted.

I can also point out that with their long necks, giraffes can reach leaves other large herbivores can’t – except elephants – and that’s one of the reasons the giraffe is a successful species. In effect we’re talking about inter-specific competition here, which is competition between organisms of different species. Now we’re getting closer to the realm of natural selection, although we’re not quite there yet. Much of natural selection is about intra-specific competition, which is competition between organisms of the same species. So we get right into natural selection if I remark that taller giraffes, or rather the taller of the giraffe-like ancestors, probably survived hard times better than their shorter relatives, because extra height meant reaching food that others couldn’t. Thus taller specimens lived longer than their shorter relatives, and they therefore tended to have more offspring. Those offspring tended to inherit the tallness trait, so on average the species got taller as the generations passed.

Let’s look at some of the adaptations needed to make that long neck work. The rete mirabile is a system of closely woven veins and arteries in the upper portion of the giraffe’s neck. It acts as a kind of sponge to stop blood rushing to the head when the giraffe lowers its head to drink. Without the rete mirabile and other mechanisms, the blood pressure in the head would be so high the giraffe would suffer brain damage. Now, many other mammals have a similar system of closely woven veins and arteries, but it’s often used for heat regulation instead. Remember the carotid rete of the gemsbok I mentioned a while back? Air being breathed in and out cools the blood passing close to the nostrils, and that blood passes through the carotid rete, cooling the arterial blood going to the brain. Same system – a latticework of veins and arteries – but different function. It’s a nice illustration of evolution and natural selection at work, molding what’s already there in different directions. Examples of this “same same but different” can be found throughout nature.

A classic ranger trick is to ask guests how many vertebrae a giraffe has. Seven. The same as us, and the same as most mammals. They’re just bigger in a giraffe. Why is that? Because it’s much more likely for something to evolve if it’s a question of enlarging or reducing something that already exists. While not impossible, the appearance of a whole new thing is less likely because evolution by natural selection can only advance through incremental changes. Each incremental modification must itself be of benefit to the organism. It’s not good enough if only the “final version” that we see today is an improvement, because otherwise the organisms with the “interim version” would have been eliminated by natural selection, and the “final version” would never have come about. (To talk of final versions is nonsense of course, because everything we see today is still evolving, but I’m sure you see what I mean.) So in evolutionary terms, making vertebrae a bit bigger is a much more likely event than growing another one – although I say again, not impossible.

**Technical explanation**

***Preventing a double hit request***

When I’m developing a site I always have an `st_error_log( $var )` function that writes to an error log so I can dump variable data there to figure what’s going. On three separate occasions now I’ve had a wtf moment when it seems as though a filter or action has been firing twice for a single page load.

I’ll have a function hooked to get_header, say, and in that function I’ve got my error logging function. When I hit refresh, hey presto, my data appears in the error log. But wait, it’s appeared twice? Wtf?

The hook hasn’t fired twice for a single page load – but the server has been hit with two requests. The first time it took me an eternity to figure it out, the second time an age, and the third time, well, better but still longer than it should have. In short, the first request gets a response from the server, but that response itself then triggers a second request to the server. Here are the three different ways I’ve been tripped up:

***Pagination attributes***

Sometimes in the `<head> of a page you’ll find something like this:

```html
<link rel="next" href="http://www.example.com/topic/page/2" />
```

It’s to do with pagination and is often used to help prevent search engines getting confused by what is in reality a single page spread over many. It seems however that some browsers also use this to “prefetch” content – trying to be helpful by anticipating that this next link is probably about to be viewed. So if your theme has this enabled, then yes, every time a page is requested, the server gets hit twice.

It’s up to you whether you want to remove them. They are there for a reason so it’s not cut and dry. If you do want to remove them, something like this should do the trick:

```php
remove_action( 'wp_head', 'adjacent_posts_rel_link_wp_head', 10 );
```

I say “something like” because it assumes the theme has hooked the function to wp_head and used the priority 10. (When removing an action you must specify the same priority as was set when it was added.)

And if you don’t want to remove them, then you may be able to at least stop the prefetch on your browser while you’re debugging – just so you can be sure there’s not something else weird going on. If like me you use Firefox it’s the setting network.prefetch-next in the advanced settings (accessed by typing about:config into the address bar).

***Favicon***

If you don’t set a favicon using the Theme Customizer, then WordPress uses its standard logo. The request is to a file favicon.ico at the website root, but actually this generates a 302 response and a redirect to /wp-includes/images/w-logo-blue-white-bg.png – which hits the server again. So to prevent the double hit you can either set a favicon, or keep the default by copying the w-logo-blue-white-bg.png file to the root and renaming it to favicon.ico.

***Source map***

The final one was my own fault. I’d copied a Bootstrap grid CSS bundle on to the site server, but hadn’t also included the source map that came with it. This again triggered a second request, and including the source map fixed it.

***The lesson***

The console is your friend! Problems 2 and 3 were solved by checking what resources were not being successfully fetched. Problem 1 was just googling, and well, where would we be without Google and Stack Overflow?

**Philosophical discussion**

It doesn’t answer my question about the mountains of course, but then I wouldn’t necessarily expect it to. Evolutionary psychology can’t explain everything, and of course our behavior is driven by such complex factors, both cultural and genetic, that I suspect the scientists will never unravel them completely. But I’m pleased there is at least some research supporting the way I feel – that the wild natural environment has a Kant-type beauty, a property valued by most if not all humans.

I also wonder whether life itself, human or otherwise, has the same “Kantish” beauty. I certainly feel that way. Perhaps in an evolutionary sense we appreciate signs of life because areas with few signs of life are usually inhospitable to us too. To survive, we need the water and nutrient cycles to function in a manner that suits us, and they generally don’t without the abundance of life-forms that make up the “picture” of nature that we appreciate – grasses, trees, bacteria, fungi, rodents, mammals, and so on.

I found all that fascinating. But it’s still rather woolly and speculative. For example, I can imagine some people arguing that we see live animals as beautiful because in days gone by it meant a hearty dinner that night. I would counter by asking why I and many others feel sadness rather than joy when looking at an animal corpse. I’m sure there could be another reasonable speculative answer though, and I don’t think that kind of discussion would lead anywhere conclusive. My train of thought is also in danger of going nowhere conclusive. Let me finish by trying to herd my wiffle into something approaching a personal position on the subject.

When they kill, hunters are probably satisfying some sort of primal instinct. Being civilized is about choosing which values we believe we should hold. Some will be counter to our primal instincts, some will not. I think we generally view oppression or subjugation as “a bad thing” among humans, and those people who enjoy killing or bullying as flawed and unwelcome characters. Of course we take things far more seriously when humans are the animals being bullied or killed, but I can’t help but feel that civilized society generally says something like, “We appreciate, celebrate and protect Life. Unless something threatens us, directly or indirectly, we live and let live.” I also think this sentiment is both cause and effect of a widely-held view that life itself has Kantish beauty. Effect because our evolutionary history has led us to appreciate nature and the associated signs of life, and cause because in choosing to value life, we will then deem it beautiful.

So do I think hunting for pleasure is wrong and we should legislate against it? Yes, I think I do. Of course there are plenty of other things I’d put higher up the priority list, but if hunting for pleasure could be banned with a click of the fingers, then I’d be in favor. Allowing hunting for pleasure condones bullying and killing for enjoyment – no different from allowing a child to pull the wings off a fly or throw stones at a dog. Yes, the context is different, yes, there are times when animals need to be killed, and yes, unlike the fly-torturing child, hunters can sometimes point to sound conservation reasons for their actions. But I think that’s all a red herring. What matters is why hunters do it. It’s for pleasure, and that just has to be wrong.
