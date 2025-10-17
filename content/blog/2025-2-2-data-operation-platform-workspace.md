---
title: Geospatial Data Visualization Workspace
description: A highly decoupled, standalone workspace capable of stacking multiple data sources and supporting various types of geospatial visualizations
date: 2025-2-2
image: /img/projects/dop-workspace/diff-radius.png
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
    Adobe Illustrator  &nbsp;  MapLibre.js  &nbsp;  Element Plus
  </div>
</div>

This was one of my favorite projects to date. The goal was to create a **highly decoupled, standalone workspace** capable of **stacking multiple data sources** and supporting **various types of geospatial visualizations**. Users can freely combine datasets—such as intersection point data, roadway line data, and population density heatmaps—and manage them in a single, interactive interface.

<figure class="blog-img-container">
  <img src="/img/projects/dop/1.png" class="blog-img" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">Choose data source in Workspace</figcaption>
</figure>

## Key Features

Automated Visualization: Inspired by ArcGIS Online and Kepler.gl, the workspace automatically detects data types from dimension tables and applies optimal visual styles:

- Varchar fields (e.g., traffic signals) are color-coded by category (SCATS, non-SCATS, unknown).

<figure class="blog-img-container">
  <img src="/img/projects/dop/2.png" class="blog-img" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">Different bubble color accoding to varchar field: singal brand</figcaption>
</figure>

- Numeric fields (e.g., stop rates) are visualized with threshold-based colors, gradients, or heatmaps.

<figure class="blog-img-container">
  <img src="/img/projects/dop/3.png" class="blog-img" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">Different bubble radius accoding to double field: speed</figcaption>
</figure>

Layer Management: Users can add multiple data sources, adjust layer order, and fully customize styling.

- Point layers support multiple rendering modes: point, cluster, icon, heatmap, grid, and hexbin.

<figure class="blog-img-container">
  <img src="/img/projects/dop/4.png" class="blog-img" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">Different modes for point layer</figcaption>
</figure>

- Style options include fill/stroke color, size, opacity, and advanced configurations for each type.

<figure class="blog-img-container">
  <img src="/img/projects/dop/5.png" class="blog-img-small" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">Multiple options for layer style</figcaption>
</figure>

Optimized Large-Scale Rendering: Implemented batch rendering of **1,000 features at a time**, enabling smooth visualization of up to **100,000+ data points** without performance crashes—particularly effective for city-wide grid-based heatmaps.

<figure class="blog-img-container">
  <img src="/img/projects/dop/6.png" class="blog-img" alt="img" loading="lazy" />
  <figcaption class="blog-img-caption">Over 50,000 geohash rect data displaying grid-based heatmap</figcaption>
</figure>

## Outcome

The result is a **flexible, scalable, and user-friendly geospatial visualization workspace**, empowering data analysts to explore, style, and interpret complex datasets without writing code.

<figure class="blog-video-container">
  <video 
    src="/img/projects/dop/workspace.mp4" 
    controls 
    class="blog-video"
    preload="metadata"
    poster="/img/projects/dop/6.png"
  >
    <p>Your browser doesn't support HTML5 video. Here is a <a href="/img/projects/dop/workspace.mp4">link to the video</a> instead.</p>
  </video>
  <figcaption class="blog-img-caption">Data Operation Platform Workspace Demo</figcaption>
</figure>
