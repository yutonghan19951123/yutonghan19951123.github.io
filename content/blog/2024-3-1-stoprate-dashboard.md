---
title: Greenwave Interactive Exhibition
description: Combined data visualization, interactive UI design, and real-time simulation logic to deliver a clear, engaging educational experience within a tight 3-week development cycle
date: 2024-3-1
image: /img/dashboard_stoprate.png
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
    <a href="https://ytsd.cc/9bcf324d-2d0c-4c63-92d5-4ea4b697be64/exhibition-cockpit/greenwave-exhibition/?lightsFrames=1&gaugeFrames=1&averageSpeedFrames=1#/exhibition-cockpit/green-wave-exhibition/city/330100/plans/a9511813-af20-48b4-8f50-d2f439e832d0?psid=38aa26c5-eab9-4200-9248-25d4a9cc500f" target="_blank" class="text-blue-600">
      Greenwave Interactive Exhibition
    </a>
  </div>
</div>

This project was designed for an **exhibition setting**, aimed at helping **non-technical visitors** intuitively understand the concept of “greenwave” traffic coordination and its strong correlation with stop rates. The interactive dashboard allows users to **manually adjust greenwave timing**, turning potential red lights into green ones for passing vehicles, thereby experiencing how traffic signal optimization improves flow efficiency.

<figure class="blog-img-container">
  <img src="/img/dashboard_stoprate.png" class="blog-img" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">UI I drawed for <a href="https://ytsd.cc/games/greenwave/#/" target="_blank" class="text-blue-600">Greenwave Interactive Exhibition</a></figcaption>
</figure>

## Design & Features

Left Panel – Time-Distance Diagram:

- Vertical axis: time

- Horizontal axis: distance

- Each intersection is represented by red (red light) and green (green light) bars, visualizing the **greenwave bandwidth**.

- A wider bandwidth indicates higher chances of continuous green lights, faster speeds, and lower stop rates.

<figure class="blog-img-container">
  <img src="/img/projects/stop_dashboard/left.png" class="blog-img" alt="img" loading="lazy" />
</figure>

Lower Section: Visual simulation of intersections, signal states, and moving vehicles, accompanied by **traffic flow distribution charts** and **turning ratios** for each intersection.

<figure class="blog-img-container">
  <img src="/img/projects/stop_dashboard/bottom.png" class="blog-img" alt="img" loading="lazy" />
</figure>

Right Panel:

- Top: Real-time stop rate by intersection and direction.

- Middle: Overall average speed.

- Bottom: Real-time speed per direction along the corridor.

<figure class="blog-img-container">
  <img src="/img/projects/stop_dashboard/right.png" class="blog-img-small" alt="img" loading="lazy" />
</figure>

## Technical Highlights

- Fully front-end solution: All computations, animations, and state changes run **client-side only**, with no backend or external API calls.

- Optimized for performance: Memory-safe implementation ensures smooth animations even under continuous user interaction.

- Interactive learning experience: Default configuration creates frequent stops (e.g., 4 red lights across 5 intersections). With careful adjustments, users can widen the greenwave bandwidth, reducing stops to just 1 and significantly improving simulated traffic flow.

This project combined **data visualization**, **interactive UI design**, and **real-time simulation logic** to deliver a **clear, engaging educational experience** within a tight 3-week development cycle.
