---
layout: post
title: "Scrolling Through Slop: Quantifying AI Video Generation on Sora"
date: 2026-03-02
categories: "Fun"
permalink: "/post/sora-crawl/"
excerpt: "As part of a broader study on the environmental impacts of AI video generation, we crawled Sora's public feed to establish a baseline picture of current usage: how much is generated, how often, and with what characteristics."
description: "Large-scale crawl of Sora's public explore feed to establish a T0 baseline of AI video generation usage, as groundwork for prospective environmental impact modeling."
tags: Sora AI video-generation crawl environmental-impact sustainability prospective-analysis
---

> This post is a shorter and simpler version of the paper and poster "Scrolling Through Slop: A Large-Scale Analysis of AI Video Generation in the Wild" presented at CHI 2026.
> You can find the paper and its replication package on my [publications page](/publications) and the poster on my [talks page](/talks)


When OpenAI launched Sora's public explore feed, it opened a window into how people actually use text-to-video generation. Not cherry-picked demos. Not curated showcases. Just thousands of generations, scrollable by anyone.

We looked through that window, systematically.

We crawled Sora's public explore page over several weeks, collected metadata on thousands of generated videos, and asked a straightforward set of questions:

**How much video is being generated? What do the prompts and generation parameters look like? And what usage patterns emerge when a frontier video model meets the general public?**

This work is the first step in a larger research effort. Our broader goal is to anticipate the potential environmental impacts of AI video generation. The data collected here serves as a **baseline snapshot (T0)** of current usage, which will feed into prospective and baseline scenarios for future impact modeling. In a companion effort, we also plan to gather energy consumption metrics from open-source video generation models, so that we can model the full life cycle impacts of AI-generated video.

## Why This Matters

Text-to-video generation has progressed rapidly, but most evaluations happen in controlled settings: benchmark prompts, curated galleries, technical reports. These tell us what models *can* do, not what they *are used for*.

Sora's explore feed changed that. For the first time, a frontier video model had a public, browsable stream of real user generations. This gave us the opportunity to study AI video generation *in the wild*, at scale, with real prompts and real outputs.

Understanding these usage patterns is essential groundwork for environmental impact assessment. Before we can model how much energy AI video generation will consume in the future, we need to know how it is being used today: how frequently, with what parameters, and at what scale.

## What We Actually Did

Our pipeline had three stages:

1. **Crawl** the Sora explore feed at regular intervals over several weeks, collecting video metadata, prompts, engagement signals, and generation parameters.
2. **Characterize** each generation based on available metadata: prompt length, use of style modifiers, resolution, duration, and other generation settings.
3. **Analyze** distributions, temporal patterns, and correlations between prompt characteristics and generation parameters.

It is important to note what we did *not* do: we did not analyze the visual content of the generated videos themselves. Our analysis is based entirely on metadata and prompt text. As a result, we cannot make claims about the quality, creativity, or effort behind individual generations. What we can characterize is the *scale and shape* of usage.

## What We Found

### 1. Prompt characteristics cluster around short, generic descriptions

The vast majority of prompts were short. The median prompt length was well below 30 words, and use of specific stylistic or cinematic modifiers was rare. Only a small fraction of prompts showed signs of deliberate prompt engineering (style tokens, negative prompts, explicit aspect ratio or motion instructions).

| ![Distribution of prompt lengths and stylistic modifier usage across all crawled generations.](/post-contents/sora-crawl/fig_prompt_characteristics.svg) | 
|:--:| 
| *Distribution of prompt lengths and stylistic modifier usage across all crawled generations.* |

### 2. A handful of generation parameter settings dominate

Users overwhelmingly stuck with default or near-default generation parameters. A small number of resolution/duration combinations accounted for the bulk of all generations, suggesting that most users do not explore the parameter space extensively.

| ![Distribution of generation parameter combinations (resolution, duration, style preset) across all crawled generations.](/post-contents/sora-crawl/fig_parameter_distribution.svg) | 
|:--:| 
| *Distribution of generation parameter combinations (resolution, duration, style preset) across all crawled generations.* |

### 3. The explore feed is not a representative sample

When we compared the metadata distributions of featured/trending videos against the full crawl, clear differences emerged. Featured videos had significantly longer prompts, more frequent use of style modifiers, and less reliance on default parameters. The platform's curation layer filters aggressively, meaning that **scrolling the explore page gives a skewed impression of typical generation behavior**.

| ![Comparison of prompt characteristics between all generations and featured/trending generations.](/post-contents/sora-crawl/fig_featured_vs_all.svg) | 
|:--:| 
| *Comparison of prompt characteristics between all generations and featured/trending generations.* |

### 4. Generation volume follows strong temporal patterns

Activity spiked predictably around product announcements and social media virality cycles, then decayed rapidly. Weekend generation volumes were roughly 1.5x weekday volumes, and certain prompt topics showed sharp burst-and-fade dynamics tied to external events.

| ![Daily generation volume over the crawl period, annotated with external events.](/post-contents/sora-crawl/fig_temporal_volume.svg) | 
|:--:| 
| *Daily generation volume over the crawl period, annotated with external events.* |

### 5. Engagement is heavily concentrated

A tiny fraction of generations received the vast majority of likes, remixes, and views. The distribution followed a steep power law, consistent with other social and creative platforms. Most generations received little to no engagement.

| ![Distribution of engagement metrics (likes, views, remixes) across all crawled generations.](/post-contents/sora-crawl/fig_engagement_distribution.svg) | 
|:--:| 
| *Distribution of engagement metrics (likes, views, remixes) across all crawled generations.* |


## What Comes Next

This crawl establishes a **T0 baseline**: a quantitative picture of how AI video generation is being used right now on a major platform. But usage data alone does not tell us about environmental impact.

The next steps in our broader research program are:

1. **Measuring energy consumption** of open-source video generation models under realistic workloads, to build a per-generation energy model.
2. **Combining usage data with energy metrics** to estimate the current environmental footprint of AI video generation.
3. **Building prospective scenarios** that project how usage patterns and energy costs might evolve as models improve, costs drop, and adoption grows.

Together, these components will allow us to move from observing *what is happening* to modeling *what it means* for energy consumption and sustainability.

## Practical Takeaways

#### Public feeds are not representative samples

Researchers and journalists should be cautious about drawing conclusions from what platforms surface. The explore page is a curated view, not a census.

#### Baseline measurement is a prerequisite for impact claims

Any serious assessment of the environmental cost of AI video generation must start with empirical usage data. Speculation about energy consumption without grounding in actual usage patterns is premature.

#### The scale of casual generation matters

Even if each individual generation is cheap, the sheer volume of casual, default-parameter usage adds up. Impact modeling must account for the long tail of low-visibility generations, not just the viral highlights.

---

## Takeaway

Sora's explore feed offers an unprecedented look at how a frontier video model is actually used. What we found is that most usage is characterized by short prompts, default parameters, and low engagement, with a curated surface layer that paints a very different picture.

This baseline snapshot is a necessary first step. Before we can meaningfully assess or project the environmental costs of AI video generation, we need to know what the current landscape actually looks like.

Now we do.