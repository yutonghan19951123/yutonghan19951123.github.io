---
title: A Day as a Traﬃc Signal Timer
description: As a traffic signal Timing Clerk, the gamer is free to drag the greenwave. There will be a change in traffic flow in response to the change in the signal after the user drags the greenwave.
date: 2023-12-1
image: /img/traffic_light_game.png
minRead: 4
author:
  name: Yutong Han
  avatar:
    src: /img/yutong.jpg
    alt: Yutong Han
---

<div class="project-info-grid">
  <div class="project-info-item">
    <strong class="project-info-label">Client</strong><br>
    Tranalytic Technology Co., Ltd.
  </div>
  <div class="project-info-item">
    <strong class="project-info-label">Tool</strong><br>
    Adobe Illustrator  &nbsp;  Native Canvas  &nbsp;  Echarts
  </div>
    <div class="project-info-item">
    <strong class="project-info-label">Link</strong><br>
    <a href="https://ytsd.cc/games/greenwave/#/" target="_blank" class="text-blue-600">
      A Day as a Traﬃc Signal Timer
    </a>
  </div>
</div>

This project was a **time-sensitive independent development assignment** aimed at delivering an interactive web-based mini-game for Hangzhou Wen Guang Traffic 91.8’s December 2 campaign.

The game’s primary goal was to visually demonstrate **“greenwave” traffic coordination** to a non-technical audience, serving both as a **public awareness tool** and a **pre-sales demo** for potential clients. The concept also opened possibilities for future gamification of traffic signal management systems.

## Gameplay

- Players act as **traffic signal coordinators**, dynamically dragging and adjusting greenwave timing.

- Traffic flow reacts in real-time, with scores calculated based on **congestion levels and vehicle throughput**.

- Designed a simple yet **intuitive drag-and-drop interface** for a non-expert audience.

## Technical Challenges & Solutions

- Challenge: Simulating vehicle movements **without backend APIs**, while ensuring realistic reactions to greenwave adjustments.

- Solution: Re-engineered and extended an earlier simulation core written by my teammate (9 months prior), implementing:
  - Custom traffic flow physics in pure TypeScript.
  - Real-time signal-light state transitions and vehicle response animations.
  - Optimizations for smooth frame rates in a browser environment.

## Additional Contributions

- Led **end-to-end UI/UX design**, from wireframes to final assets, ensuring a visually engaging, user-friendly experience.

- Coordinated closely with colleagues to refine the simulation logic for more **realistic braking behavior** (gradual deceleration near red lights) in a subsequent large-scale visualization dashboard version.

This project showcased my ability to rapidly prototype interactive simulations, merge **visual storytelling with technical execution**, and deliver a functional product under a tight deadline.

<figure class="blog-img-container">
  <img src="/img/projects/green_wave_game.png" class="blog-img" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">UI I drawed for <a href="https://ytsd.cc/games/greenwave/#/" target="_blank" class="text-blue-600">A Day as a Traﬃc Signal Timer</a></figcaption>
</figure>
