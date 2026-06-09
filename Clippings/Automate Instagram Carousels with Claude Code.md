---
title: "Automate Instagram Carousels with Claude Code"
source: "https://ryanfrizelle.com/guides/claude-code-carousel-generator"
author:
  - "[[Ryan Frizelle]]"
published: 2026-04-19
created: 2026-06-09
description: "Built a Claude Code system that generates a full on-brand Instagram carousel from one idea. Hooks, copy, slide visuals, ready to post in minutes."
tags:
  - "clippings"
---
Free guide · part of the Claude Code Course

## Get the full Claude Code Course

Every build, every prompt, the security setups, and every future section — yours forever for one payment. This guide is a free taste of what’s inside.

[Or read the free guide ↓](#guide-content)

## Automate Instagram Carousels with Claude Code

I just built a system in Claude Code that generates a full on-brand Instagram carousel every time I finish a feature. Zero blank-page staring. Here is exactly how I did it.

By Ryan Frizelle · 5 min read

I just automated carousel creation. Every time I ship something in my day to day, Claude Code turns it into a full on-brand Instagram carousel. Cover slide, steps, CTA, all of it. Ready to post. Not even exaggerating.. this thing has already saved me hours a week.

Carousels are crushing right now. They get saved more than any other format, the algorithm is rewarding them hard, and every big account on Instagram has gone all-in on them. But a good one takes 30 minutes if you actually care. So most people post bad ones or give up. I wanted a system that makes good ones automatically. So I built one.

The secret is not asking AI to "write me a carousel." That gets you generic garbage every time. The real secret is feeding Claude three things: your best-performing content patterns, your exact brand style, and what you actually shipped that day. That combination is what makes it land.

Here is the workflow once it's set up. I finish a real task in my Claude Code project. Then I run one command. Claude looks at what I just built, pulls my top-performing past content patterns, and generates a full 7-slide carousel on-brand for my account. I approve the copy in 90 seconds. The images render. It ships to Instagram on autopilot at 2 PM.

Here is how to build your own version:

1. 1.Have Claude Code analyze your best-performing posts. It scans what you have already published and figures out which formats, hooks, and patterns actually work for you. Not for some random creator. You.
2. 2.Save those patterns in a single markdown file at your project root. Call it CAROUSEL-BRAND.md. This is the file that teaches Claude your exact carousel style. Your colors. Your typography. Your voice. Claude reads it fresh every run.
3. 3.Inside that file, define the slide types you use (cover, problem, list, steps, before/after, CTA). Each slide type gets a short image prompt template with placeholders Claude fills in per carousel.
4. 4.Build a slash command like /post-carousel that ties it all together. You run the command. Claude reads your brand file, looks at what you have been working on, drafts a 7-slide idea, fills the templates, and kicks off image generation.
5. 5.For the images, plug Claude into Gemini 3 Pro Image Preview, also known as nano banana. Right now it is the only model that can put real readable text on a slide without it looking warped. Claude passes each slide's prompt to it and gets back a finished 1080x1080 slide in seconds.

Find your winning content patterns

```
Analyze my last 20 Instagram posts and tell me what is actually working. For each post, look at the format (reel, carousel, static image), the hook, the structure, and the CTA. Then tell me:

1. The top 3 hook patterns that got the most saves, shares, and comments
2. The 2 to 3 carousel structures that consistently outperform (like "problem to steps to payoff" or "list of 5 things")
3. The tone and voice patterns my best posts have in common

Give me this as a short report I can paste into a file called CAROUSEL-BRAND.md. Do not invent patterns. Only pull what is actually in my data.
```

Once your brand file is dialed in, everything else gets easy. The hard part is not the code. The hard part is getting specific enough about your carousel style that Claude knows exactly what to render. Vague in, vague out. The more specific you are, the more scroll-stopping the output.

Here is what goes inside your CAROUSEL-BRAND.md:

1. 1.Your active style. One clear visual direction (handwritten notebook, terminal dark mode, minimal typographic, magazine editorial, whatever fits your brand). Pick one. Do not mix.
2. 2.Your exact color palette with hex codes. Not "warm tones." Actual hex values. The more specific you go here, the more on-brand the output.
3. 3.Your typography direction. Fonts, weights, which font goes where, what emphasis looks like. Claude needs this spelled out.
4. 4.Your slide type templates. For every slide type you use, write a short image prompt with {{variables}} for the headline, body, list items, and so on. Claude fills these in per carousel.
5. 5.Hard rules. The things to never do. No em dashes on slides. No emojis. No clip art. No phrases you would not say out loud. Constraints make the output way better.

Build your CAROUSEL-BRAND.md file

```
Create a CAROUSEL-BRAND.md file in the root of this project. This is the file you will read fresh every single time I ask you to generate a carousel. Never cache it.

Walk me through it section by section. Ask me:
1. My active style. Pick one clear visual direction that matches my brand (handwritten notebook, terminal dark mode, minimal typographic, magazine editorial, etc.).
2. My exact color palette. Give me hex codes, not adjectives.
3. My typography direction. Fonts, weights, which font goes where.
4. The slide types I use (cover, problem, list, steps, before/after, CTA). For each one, write a short image prompt template with {{variables}} I can fill in per carousel.
5. Hard rules. The stuff to never do on a slide.

After my answers, save the full file as CAROUSEL-BRAND.md in the project root. Format it cleanly so I can edit it later without asking you.
```

Now the fun part. The file is in place, the slide templates are written, and Claude knows your style. Everything from here is one command.

Generate a carousel from what you just built

```
I just finished [what you built today]. Read CAROUSEL-BRAND.md fresh (do not use a cached version) and pull my best-performing carousel structure based on my Instagram data. Draft a 7-slide carousel that teaches what I just shipped.

For each slide give me:
1. The slide type (cover, problem, list, steps, before/after, CTA)
2. The exact on-slide copy (headline, body, list items, whatever the slide type needs)
3. The image generation prompt filled with my brand's visual identity, palette, typography, and required elements from CAROUSEL-BRAND.md

Then generate the 7 slide images using Gemini 3 Pro Image Preview (nano banana) at 1080x1080. Save them to a local folder so I can review and post them.
```

Pro move: run this every single day after you finish real work. One command, one carousel, posted automatically. Most creators burn out at 3 posts a week. You are going to compound forever.

A few things to know before you build this. Your brand file has to be read fresh every single run, never cached. If Claude caches it, your edits never show up. Tell Claude to reload it on every single carousel.

Nano banana (Gemini 3 Pro Image Preview) is miles ahead of every other image model for slides with real text on them right now. Do not try to use DALL-E or Stable Diffusion for this. The text accuracy just is not there yet.

The brand file is the whole ballgame. A vague brand file gives you AI-looking carousels. A hyper-specific brand file gives you carousels that look like a designer made them. Spend 30 minutes getting it right. It pays you back forever.

That is the whole thing. Analyze your best posts. Build a brand file. Write one slash command. Generate 7 slides on autopilot. Ship. I went from 30 minutes per carousel to 3 minutes of approval. And honestly, the output looks better than anything I was making by hand.

The full course walks through my exact CAROUSEL-BRAND.md, the full slash command I use, and how I wire it into my Instagram posting queue so carousels ship every day without me thinking about it.

### Liked this? There's 50x more in the course.

Getting Started setup guide + prompts

Quick Wins library (growing monthly)

Step-by-step website and dashboard builds

All future sections + updates forever

One-time purchase. Keep forever.

## Keep going

More walkthroughs from the library.

### [Create Unlimited Ads With AI](https://ryanfrizelle.com/guides/unlimited-ai-ads-claude-code)

Create unlimited ad creatives with AI. Build a brand brain in Obsidian, then Claude Code generates ready-to-run ads with no designer and no design skills.

Read the guide

### [Redesign Any Room With AI (for Under $2)](https://ryanfrizelle.com/guides/redesign-any-room-with-ai)

Redesign any room with AI for under $2. Real photos in, photorealistic renders out. See every wall color and layout before buying furniture.

Read the guide

### [Humanizer + VOICE.md: Make Claude Write Like You](https://ryanfrizelle.com/guides/humanizer-claude-code)

Sick of copy that screams AI wrote this? Install one Claude Code skill plus a VOICE file and your writing finally sounds like you, not a robot.

Read the guide