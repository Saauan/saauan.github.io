---
layout: post
title: "Scrolling Through Slop: Quantifying AI video generation on Sora"
date: 2026-03-02
categories: "Research"
permalink: "/post/sora-crawl/"
excerpt: "AI video generation is booming, but how much is actually happening? We scraped Sora's public feed for 13 days and collected nearly a million videos. Here is what we found."
description: "An empirical study of public AI video generation on Sora, measuring daily volume, usage patterns, user behaviour, and content characteristics through large-scale scraping."
tags: AI video Sora scraping environmental-impact generative-AI
---

> This post is a shorter and simpler version of the poster "Scrolling Through Slop: Quantifying AI video generation on Sora with scraping" presented at Green Days 2026.
> You can find the poster on my [talks page](/talks).

AI video generation has become remarkably accessible. Tools like [Sora](https://sora.chatgpt.com/), Runway, or Gemini let anyone produce short clips from a text prompt in seconds. This democratisation is happening fast, and it is accompanied by a wave of enthusiasm about creative potential and productivity gains.

But every one of those generations runs on a GPU cluster somewhere.

The environmental cost of that infrastructure is real, and largely invisible. Before we can estimate it, we need to answer a more basic question:

**How much AI video generation is actually happening?**

## Why We Need a Baseline

Our broader research goal is to anticipate the environmental impacts of AI video generation, modelling energy use, carbon emissions, and resource consumption across the full life cycle of these systems.

But you cannot model what you cannot measure. Official usage data from platforms like Sora is not publicly available, and there is no regulatory requirement to disclose it. This leaves researchers with no reliable starting point.

So we built one ourselves.

## A Lucky Accident: Sora Is Easy to Scrape

Most platforms are opaque by design. Sora happened not to be, at least for its public feed.

Sora's feed of publicly shared videos is **chronologically ordered**, which means it is straightforward to scrape systematically without needing to reverse-engineer any ranking algorithm. We deployed 6 bots to scrape the feed and 10 bots to scrape individual video metadata, running continuously over 18 days in February 2025.

The result: **1.33M videos collected**, with metadata including timestamp, duration, resolution, prompt language, and like counts.

It is worth pausing on how fragile this window is. One API change, one decision to randomise the feed, and this kind of external measurement becomes impossible. The study exists because of an accident of platform design, not because of any commitment to transparency.

## How Much Is Being Generated?

The headline figure: **~74,000 public videos are generated every day** on sora.chatgpt.com. That translates to roughly **5.81 TiB of video data every month**.

To put that in perspective: it sounds like a lot, until you compare it to TikTok, where an estimated [269 million videos are posted daily](https://arxiv.org/pdf/2504.13279). Sora's public output is about **0.028% of that volume**. AI video generation, for now, is a rounding error in the broader media landscape.

But the trajectory matters more than the current scale. These numbers represent a baseline from which we can build on to build predictions and scenarios modeling the evolution of this technology.

## When Is It Used?

Sora does not seem to be used only for entertainement purposes. The usage patterns looks a lot like that of a **working day**.

| ![Hourly usage of Sora broken down by prompt language (French, German, Italian, Japanese, Korean), showing peaks at 11:00 and 14:00 and a sharp decline at night.](/post-contents/sora-crawl/fig_hourly_usage.png) |
|:--:|
| *Number of videos generated per hour of the day, by prompt language. Generations peak during working hours and drop sharply at night.* |

Generations peak around **11:00 and again at 14:00**, then gradually decline through the afternoon and evening. Usage at night is a fraction of the daytime peak. Evening hours (18:00–00:00) see roughly **25% fewer generations** than peak daytime.

This pattern holds consistently across the languages we tracked, French, German, Italian, Japanese, and Korean users all show similar temporal shapes, which suggests it reflects global professional rhythms rather than any single region's habits.

## Does Usage Change Over Time?

Remarkably little.

| ![Daily video volume on Sora from February 6 to February 24, 2025, with weekend days highlighted. Bars are near-uniform in length across all dates.](/post-contents/sora-crawl/fig_daily_volume.png) |
|:--:|
| *Number of videos published per day over the scraping period. Weekend days are highlighted. Usage is stable across both weekdays and weekends.* |

Daily volume stays **stable across both weekdays and weekends**, with no meaningful dip on Saturdays and Sundays. This further reinforces the idea that Sora is already embedded in ongoing workflows rather than being used purely for leisure.

## Who Is Using It?

Prompts are written overwhelmingly in **English (67.5%)**, but the long tail is genuinely global: Russian (4.6%), Spanish (4.5%), Portuguese (3.6%), French (2.7%), and German (2%) are all meaningfully represented, along with Indonesian, Italian, and Chinese.

| ![Horizontal bar chart of prompt language proportions, with English dominant at ~0.65 and a long tail of other languages.](/post-contents/sora-crawl/fig_language_distribution.png) |
|:--:|
| *Proportion of videos by prompt language. English dominates, but Sora is used across a wide range of languages worldwide.* |

Interestingly, **20% of users have generated prompts in more than one language**, suggesting a layer of multilingual or internationally mobile users.

The user distribution is also heavily skewed: **50% of users have generated 2 videos or fewer**, and 90% have generated 7 or fewer. A small number of power users account for a disproportionate share of activity.

## What Gets Made, and Does Anyone Watch It?

The content itself is notably uniform in format:

- **71%** of videos are in portrait orientation
- **80%** are in 480p resolution, the default quality
- **75%** last 5 seconds; **20%** last 10 seconds

Moreover, **Only 0.79% of videos receive at least one like within 7 days.** The most-liked video in our dataset has 2,000 likes. For the vast majority of generated content, there is no visible audience at all.

| ![Right-skewed histogram of videos per user, showing the large majority of users have generated very few videos.](/post-contents/sora-crawl/fig_videos_per_user.png) |
|:--:|
| *Distribution of total videos generated per user. The distribution is heavily right-skewed: most users generate very few videos.* |

This is the sharpest version of the "slop" question. If 99% of generated videos are never liked, never meaningfully engaged with, and likely never watched by anyone other than their creator, what are they *for*? The honest answer is that we do not know. They may be downloaded and used privately, or shared on social medias. Or they may be used for communication on the internet.

## What We Still Do Not Know

The public feed is only part of the picture. Sora's API allows developers and businesses to generate videos programmatically, without any public visibility. This is almost certainly a significant source of additional volume, and arguably the more environmentally relevant one, since automated pipelines can generate at far higher rates than individual users.

We also have no visibility into what the videos are actually used for once they leave the platform. Understanding downstream use is essential for building realistic environmental impact models.

## Why This Matters

A 5-second, 480p video does not feel like a large environmental action. But at 73,000 per day, the cumulative compute starts to add up, and that is before accounting for API usage, or for the trajectory of growth as the technology matures and adoption accelerates.

This study is one piece of a larger effort to make the environmental footprint of generative AI legible. The next steps involve modelling the actual energy cost per generation, estimating carbon emissions under different data centre scenarios, and building prospective models of what usage might look like in 2–5 years.

---

## Takeaway

Every day, tens of thousands of AI videos are generated on Sora, short, low-resolution, rarely liked, and most probably unseen. Usage follows working hours, spans the globe, and is remarkably stable over time.

These numbers are modest by social media standards, but they represent **the floor, not the ceiling**, of a fast-moving technology. 
Understanding the scale of AI video generation is only the first step toward understanding its cost.