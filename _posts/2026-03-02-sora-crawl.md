---
layout: post
title: "Scrolling Through Slop: Quantifying AI Video Generation on Sora"
date: 2026-03-02
categories: "Fun"
permalink: "/post/sora-crawl/"
excerpt: "Sora's public feed promises a new era of creative video. We crawled it, classified thousands of generations, and measured what people actually make — and what the platform actually serves."
description: "Large-scale analysis of Sora's public explore feed revealing content patterns, prompt strategies, and the prevalence of low-effort AI-generated video."
tags: Sora AI video-generation slop crawl content-analysis generative-AI
---

> This post is a shorter and simpler version of the paper and poster "Scrolling Through Slop: A Large-Scale Analysis of AI Video Generation in the Wild" presented at CHI 2026.
> You can find the paper and its replication package on my [publications page](/publications) and the poster on my [talks page](/talks)


When OpenAI launched Sora's public explore feed, it opened a window into how people actually use text-to-video generation. Not cherry-picked demos. Not curated showcases. Just thousands of generations, scrollable by anyone.

We looked through that window — systematically.

We crawled Sora's public explore page over several weeks, collected metadata on thousands of generated videos, and asked a straightforward set of questions:

**What are people making? How much of it is low-effort slop? And what patterns emerge when a generative video model meets the general public?**

## Why This Matters

Text-to-video generation has progressed rapidly, but most evaluations happen in controlled settings: benchmark prompts, curated galleries, technical reports. These tell us what models *can* do, not what they *are used for*.

Sora's explore feed changed that. For the first time, a frontier video model had a public, browsable stream of real user generations. This gave us the opportunity to study AI video generation *in the wild* — at scale, with real prompts and real outputs.

Understanding these usage patterns matters for platform design, content moderation, and for anyone trying to separate genuine creative use from low-quality noise.

## What We Actually Did

Our pipeline had four stages:

1. **Crawl** the Sora explore feed at regular intervals over several weeks, collecting video metadata, prompts, engagement signals, and generation parameters.
2. **Classify** each generation along several axes: content category, apparent effort level, prompt complexity, and visual quality.
3. **Analyze** distributions, temporal patterns, and correlations between prompt characteristics and output quality.
4. **Compare** what the platform surfaces (trending/featured) versus what users actually generate.

We developed a taxonomy of content types and a lightweight "effort score" combining prompt length, specificity, and use of style modifiers:

<div class="text-center"> $$Effort = f(\text{prompt length},\ \text{specificity},\ \text{style tokens},\ \text{negative prompts})$$
</div>

## What We Found

### 1. A small number of content categories dominate

Over half of all public generations fell into just five categories: nature/landscape scenes, anime-style characters, cinematic slow-motion effects, abstract/surreal imagery, and celebrity likenesses. The long tail of genuinely creative or unusual uses was thin.

| ![Distribution of content categories across all crawled generations.](/post-contents/sora-crawl/fig_content_categories.svg) | 
|:--:| 
| *Distribution of content categories across all crawled generations.* |


### 2. Most generations are low-effort

Using our effort taxonomy, roughly **60–70% of generations** scored in the lowest effort tier: short prompts, no style modifiers, and generic subject matter. These are the "a cat walking on the moon" tier — functional, but not meaningfully creative.

Only about 8% of generations showed evidence of deliberate prompt engineering or iterative refinement.

| ![Distribution of effort scores across generations, broken down by content category.](/post-contents/sora-crawl/fig_effort_distribution.svg) | 
|:--:| 
| *Distribution of effort scores across generations, broken down by content category.* |

### 3. The explore feed heavily over-represents high-quality outputs

When we compared the full distribution of generations against what appeared on the trending or featured sections, the gap was stark. The platform's curation layer filters aggressively: **featured videos had effort scores 3–4× higher** than the median generation.

This means that scrolling the explore page gives a misleading impression of typical output quality.

| ![Comparison of effort scores between all generations and featured/trending generations.](/post-contents/sora-crawl/fig_featured_vs_all.svg) | 
|:--:| 
| *Comparison of effort scores between all generations and featured/trending generations.* |

### 4. Prompt length correlates weakly with visual quality

Longer prompts did tend to produce slightly higher-quality outputs, but the relationship was noisy. Beyond ~40 words, additional prompt length showed diminishing returns. The strongest predictor of visual quality was the use of specific cinematic or stylistic terms, not raw verbosity.

### 5. Generation volume follows strong temporal patterns

Activity spiked predictably around product announcements and social media virality cycles, then decayed rapidly. Weekend generation volumes were roughly 1.5× weekday volumes, and certain content categories (celebrity likenesses, meme formats) showed sharp burst-and-fade dynamics.

| ![Daily generation volume over the crawl period, annotated with external events.](/post-contents/sora-crawl/fig_temporal_volume.svg) | 
|:--:| 
| *Daily generation volume over the crawl period, annotated with external events.* |


## Practical Takeaways

#### Public feeds are not representative samples

Researchers and journalists should be cautious about drawing conclusions from what platforms surface. The explore page is a curated view, not a census.

#### Prompt engineering matters more than prompt length

A few well-chosen style tokens outperform long, rambling descriptions. If you want better generations, be specific about *how* something should look, not just *what* it depicts.

#### Most generative video use is casual

The dominant use case is not filmmaking or professional content creation — it's casual experimentation. Platform design and moderation strategies should account for this reality.

---

## Takeaway

Sora's explore feed offers an unprecedented look at how a frontier video model is actually used. What we found is that most of it is low-effort, repetitive, and clustered around a handful of content types.

This isn't necessarily a problem — casual use is a valid use. But it does mean that **the curated showcases and viral highlights paint a dramatically different picture from the typical generation**.

If we want to understand the real impact of generative video, we need to look past the highlights reel.