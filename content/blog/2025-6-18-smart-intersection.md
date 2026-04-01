---
title: Holographic Intersection Dashboard
description: Designed and developed a high-performance intersection traﬃc visualization. Used native canvas for custom rendering and integrated WebAssembly to optimize frame interpolation.
date: 2025-06-18
image: /img/smart_intersection.png
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
    Adobe Illustrator  &nbsp;  WebAssembly  &nbsp;  Element Plus  &nbsp;  Native Canvas
  </div>
</div>

This project was one of the most challenging yet rewarding experiences of my front-end development career. The client required an interactive **“Holographic Intersection Dashboard”** that could visually represent real-time traffic operations at individual intersections.

The goal was to create a dynamic cockpit-style display showing **traffic signal phases, lane-level turn ratios, red/green countdowns, vehicle trajectories, and daily flow statistic**s per phase—all in a single, easy-to-read dashboard.

## The Challenge

From the start, the project had a nearly impossible timeline: **three weeks** from requirement handoff to a working demo, including **UI/UX design, front-end development, backend integration, and deployment**. The client wanted a **high-fidelity visualization** that would impress stakeholders and traffic engineers alike while supporting **large volumes of real-time vehicle data**.

On top of that, the data came from advanced computer vision systems that detected vehicles at each lane, meaning that the dashboard needed to **animate every detected car** in a realistic way while maintaining smooth performance. The backend team was concerned that calculating frame-by-frame positions for every vehicle on the server would overload the system, leading to dropped frames or lag. My task was to solve this problem on the front end while keeping the UI clean, intuitive, and professional.

## Design Process

The design phase lasted about **one week**, during which I iterated quickly on several concepts with my manager and colleagues. I started with low-fidelity wireframes to define the layout: intersection diagrams at the center, traffic phase details on the sides, vehicle counts and turning ratios displayed per lane, and time-based statistics arranged at the bottom. Once we agreed on the information hierarchy, I used **Adobe Illustrator** to produce high-fidelity mockups, experimenting with **color schemes that clearly distinguished signal states, phase groupings, and congestion levels**.

<figure class="blog-img-container">
  <img src="/img/projects/smart_vertex/1.png" class="blog-img" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">UI: Holographic Intersection Dashboard Overview with mock data</figcaption>
</figure>

<figure class="blog-img-container">
  <img src="/img/projects/smart_vertex/2.png" class="blog-img" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">UI: Holographic intersection lane congestion index visualization (red, yellow, green)</figcaption>
</figure>

<figure class="blog-img-container">
  <img src="/img/projects/smart_vertex/3.png" class="blog-img" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">UI: Holographic intersection car speed visualization</figcaption>
</figure>

<figure class="blog-img-container">
  <img src="/img/projects/smart_vertex/4.png" class="blog-img" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">UI: Holographic intersection lane level traffic volume</figcaption>
</figure>

During review sessions, stakeholders liked the overall UI but requested **simplified functionality** to meet the deadline. We had to cut several non-critical features, focusing first on delivering the core visualization. My goal was to **retain clarity and usability** despite these reductions—so every visual element had to earn its place.

## Development and Technical Implementation

With only **1.5 weeks left for development**, I transitioned from design to coding. The project used **TypeScript, Native Canvas for rendering, Element-plus for UI components, and WebAssembly for high-performance animation**.

Key technical highlights:

- **Vehicle Trajectory Interpolation**

Instead of relying on the backend to send every frame’s vehicle position, I implemented a **WebAssembly module** to calculate interpolated positions locally. This reduced network load and allowed us to animate hundreds of vehicles smoothly at 60 FPS.

- **Real-Time Signal Countdown**

Each lane’s red/green phase was represented with a **countdown timer** that updated dynamically as signal cycles changed, giving operators instant situational awareness.

- **Canvas Optimization**

Drawing hundreds of vehicles and lane-level signals on the canvas was computationally intensive. I implemented **layered canvas rendering and frame-diff drawing**, ensuring only changed elements were re-painted each frame, improving performance on lower-end machines.

- **Data Synchronization**

The dashboard consumed real-time data streams from multiple sources. I wrote a **synchronization utility** to ensure vehicle data, signal phase changes, and statistics stayed consistent even if some packets were delayed.

## Challenges and Debugging

The speed of development meant encountering several unexpected issues:

- **“Reverse Driving” Bug**

Early in testing, vehicles occasionally appeared to **drive backward** out of the intersection. The cause was a position calculation error: when a car reached its endpoint (distance = 0m), the next frame reused the previous position without filtering negative values, effectively making it reverse. This bug became an internal joke (“ghost cars in reverse gear”) before we fixed it by adding proper position validation.

<figure class="blog-video-container">
  <video 
    src="/img/projects/smart_vertex/bug.mp4" 
    controls 
    class="blog-video"
    preload="metadata"
    poster="/img/projects/smart_vertex/2.png"
  >
    <p>Your browser doesn't support HTML5 video. Here is a <a href="/img/projects/smart_vertex/bug.mp4">link to the video</a> instead.</p>
  </video>
  <figcaption class="blog-img-caption">Drive Backward Bug</figcaption>
</figure>

- **Animation Performance**

Initial tests showed frame drops when simulating over 1000 vehicles. We resolved this by **batch processing vehicle updates** and offloading calculations to WebAssembly threads.

- **Deadline Pressure**

The final demo deployment was scheduled for **March 20**, one day before my own wedding. To avoid delays, I pushed all my code to Git early, documented the remaining optimizations, and handed it over to a teammate who finalized deployment while I was offline. This project truly tested my ability to **deliver under pressure while collaborating effectively**.

## Final Delivery and Post-Launch Iterations

The first demo, using mock data, was deployed on time. It already allowed stakeholders to view lane-level activity, traffic signal timing, and vehicle flows in near real time. The visual impact was strong enough to spark high engagement from city traffic managers.

<figure class="blog-video-container">
  <video 
    src="/img/projects/smart_vertex/demo.mp4" 
    controls 
    class="blog-video"
    preload="metadata"
    poster="/img/projects/smart_vertex/1.png"
  >
    <p>Your browser doesn't support HTML5 video. Here is a <a href="/img/projects/smart_vertex/demo.mp4">link to the video</a> instead.</p>
  </video>
  <figcaption class="blog-img-caption">Holographic Intersection Dashboard Demo</figcaption>
</figure>

After my wedding, I rejoined the team to **iterate on the dashboard**. The next phase included:

- **Integration with real visual recognition data**, showing every detected car, classified by type and direction.

- **Improved lane geometry rendering**, ensuring scale accuracy for different intersection layouts.

- **Performance tuning** for larger datasets across multiple intersections.

This collaboration with the **computer vision team** was particularly exciting, as it gave me a deeper appreciation of traffic analytics and sparked my personal interest in **visual recognition technology** beyond traffic signal detection.

## Key Takeaways

This project taught me several valuable lessons:

- **Balancing ambition and feasibility** under extreme deadlines is crucial—design clarity and feature prioritization can make or break a project.

- **High-performance data visualization** requires careful optimization at both architectural and rendering levels, especially when handling thousands of moving objects.

- **Cross-functional teamwork** is essential when front-end, back-end, and computer vision teams collaborate on a real-time dashboard.

Despite the initial constraints, the Holographic Intersection Dashboard became one of my favorite projects, combining UI/UX design, data visualization, and performance engineering to deliver a visually compelling, technically robust solution.
