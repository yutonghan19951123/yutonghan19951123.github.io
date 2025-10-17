---
title: Why Cities Need Greenwaves
description: Built a five-step interactive visualization to communicate the necessity and benefits of green wave corridors to non-expert audiences.
date: 2024-04-23
image: /img/projects/why-greenwave/index.png
minRead: 8
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
    Adobe Illustrator  &nbsp;  UI & UX Design  &nbsp;  Sketch
  </div>
</div>

This was a large-format interactive display project designed for public exhibition. The target audience: citizens with little or no background in traffic systems. The core question we aimed to answer was simple but fundamental—**why do cities need greenwave corridors**?

The challenge was to communicate this complex traffic strategy in a highly intuitive and engaging way. To meet this challenge, I designed a dynamic five-step data storytelling experience, blending geospatial visualization with narrative design. Each step was animated and interactive, drawing from real traffic data to help users see the logic and impact of greenwave planning in action.

1. **Where do vehicles come from, and where are they going?**

The first screen introduces viewers to the natural flow of traffic throughout the city. The base map shows animated dots representing individual vehicles, with each dot color-coded by district. A timeline bar at the bottom left indicates the time and date of the flow, dynamically updating as the animation progresses.

<figure class="blog-img-container">
  <img src="/img/projects/why-greenwave/index.png" class="blog-img-large" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">UI page 1: Where do vehicles come from, and where are they going</figcaption>
</figure>

A clear tidal pattern emerges: in the morning, vehicles move from District A to District B; in the evening, the flow reverses. This simple visualization introduces the concept of commuting corridors and how directional demand fluctuates with time—setting the stage for the traffic challenges that follow.

<figure class="blog-img-container">
  <img src="/img/projects/why-greenwave/1.png" class="blog-img-large" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">The Vehicle migration layer will auto showing up for page 1</figcaption>
</figure>

2. **Where does congestion occur—and how bad is it?**

The second screen zooms into the morning peak period, focusing specifically on the corridor from District A to District B. Here, we visualize congestion intensity: red segments represent heavily congested roads, while red intersection icons indicate jammed traffic lights and queuing zones.

<figure class="blog-img-container">
  <img src="/img/projects/why-greenwave/2.png" class="blog-img-large" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">UI page 2: Where does congestion occur—and how bad is it</figcaption>
</figure>

The standout area is Avenue XX, a major arterial road connecting both districts. Supporting text explains its critical role during rush hour: despite carrying the bulk of the traffic, it’s under severe strain—slowing down average speeds and increasing travel time unpredictably.

This screen is crucial for helping users emotionally connect with the issue. Everyone has experienced traffic jams, and this visualization gives that pain point both clarity and context.

<figure class="blog-img-container">
  <img src="/img/projects/why-greenwave/3.png" class="blog-img-large" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">The stoprate index and congestion index layers will be presented in this page</figcaption>
</figure>

3. **What strategies can reduce congestion?**

The third screen shifts the viewer’s focus from problem to solution. It zooms out to introduce **alternative routes** that run parallel to Avenue XX: for instance, a pair of cross-district corridors like A–B and C–D.

<figure class="blog-img-container">
  <img src="/img/projects/why-greenwave/4.png" class="blog-img-large" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">UI page 3: What strategies can reduce congestion</figcaption>
</figure>

Using real-time traffic simulations, we illustrate how these corridors are less congested, marked in orange and green. At the same time, a side-by-side panel compares congestion indicators between Avenue XX and the proposed greenwave alternatives during the same time period.

This portion makes the case for distributed traffic. By synchronizing signals across alternative roads and turning them into greenwave corridors, cities can offload congestion from overburdened main roads and make better use of underutilized infrastructure.

<figure class="blog-img-container">
  <img src="/img/projects/why-greenwave/5.png" class="blog-img-large" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">The Vehicle Traffic Flow layer will be rendered in this page</figcaption>
</figure>

4. **Was the traffic diversion successful?**

This screen evaluates the effectiveness of the implemented greenwave strategy. We use a simple but powerful set of metrics:

- How many vehicles were diverted from Avenue XX?

- How much did congestion decrease on the main corridor?

- What portion of traffic successfully used the new greenwave roads?

<figure class="blog-img-container">
  <img src="/img/projects/why-greenwave/6.png" class="blog-img-large" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">UI page 4: Was the traffic diversion successful</figcaption>
</figure>

Through visual counters, real-time charts, and animated flow diagrams, users can clearly see that thousands of vehicles now pass through AB and CD routes during peak hours—proving that the diversion was not just a theory, but a measurable success.

This is where the abstract concept of “traffic optimization” becomes tangible.

<figure class="blog-img-container">
  <img src="/img/projects/why-greenwave/7.png" class="blog-img-large" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">The stoprate index and congestion index layers will be presented in this page</figcaption>
</figure>

5. **What changed after the greenwave strategy was implemented?**

The final screen brings everything together with a comprehensive before-and-after analysis. We compare five key indicators:

- Traffic volume

- Average speed

- Congestion index

- Number of incidents

- Average stop rate

<figure class="blog-img-container">
  <img src="/img/projects/why-greenwave/8.png" class="blog-img-large" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">UI page 4: What changed after the greenwave strategy was implemented?</figcaption>
</figure>

Each indicator is visualized with intuitive bar graphs and time series charts. For instance, one chart shows the average number of vehicles passing per hour on Avenue XX before and after the greenwave was activated—highlighting a dramatic increase in throughput and reduction in stops.

The conclusion is clear: greenwave corridors don’t just move cars faster—they create safer, more predictable, and more efficient urban mobility.

<figure class="blog-img-container">
  <img src="/img/projects/why-greenwave/9.png" class="blog-img-large" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">The Vehicle Traffic Flow layer will be rendered in this page</figcaption>
</figure>

## Design Considerations

From the start, I knew the success of this project would hinge on clarity and emotional resonance. The target users were not engineers or traffic officials—they were members of the public visiting an exhibit. So I relied heavily on motion design, color encoding, and spatial storytelling.

Each of the five steps was designed as a self-contained screen but with smooth transitions between them to maintain narrative flow. I deliberately avoided technical jargon, instead using animated visuals and everyday language to guide users through the logic of urban traffic management.

Tools like **Sketch** and **Adobe Illustrator** were used to design the UI and animations. I worked closely with the data engineering team to ensure all visuals were based on accurate simulations and historical data.

## Reflection

This was one of my favorite projects because it combined my UI/UX design skills with my passion for making data accessible and engaging. By the end of it, I had created not just a dashboard, but an **interactive public education experience**—one that helped non-experts understand and appreciate the value of traffic engineering strategies like greenwave optimization.

Most importantly, it served a dual purpose: while tailored for the public, the visualization also became a powerful internal tool for stakeholder communication and cross-department alignment.
