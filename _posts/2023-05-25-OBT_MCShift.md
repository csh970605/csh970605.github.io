---
title: Motion Tracking with Mean Shift & CAM SHIFT
author: SeHoon
date: 2023-05-25 20:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Mean Shift?
Mean shift is a hill climbing algorithm which involves shifting this kernel iteratively to a higher density region until convergence. Every shift is defined by a mean shift vector. The mean shift vector always points toward the direction of the maximum increase in the density.<br><br>

Consider we have a set of points. We are given a small window and we have to move that window to the area of maximum pixel density. It will take several steps given below:
<br><br><br><br>

## Steps of Meanshift Object Tracking
---
<br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/e50fb457-b8ef-4c99-8da9-6dc71fc3ada2" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/31981580-a933-4db2-bb8c-99b797c6d9c4" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/3dd6271a-98a9-4d19-b3bd-2900e8c2b6bb" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/008491db-6109-4e92-9e4f-40417b0d5490" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/8aa235dd-f952-445d-ab5b-9b7a2be7b6dd" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/f27ba0af-b61d-4dd3-b738-1ba6ebd560fe" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/f4e1d41e-cfa1-4f59-b387-6862a85651f2" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/bee6bb19-2525-491a-b9a4-ce4d9a2f02b7" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/a6840381-c6c9-4b7c-ba55-04a049aa4b9f" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/fff8641a-6346-42bc-b194-798586cea46c" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/5f495d69-9f4e-47f7-98e4-41dc604626ce" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/65225303-bbc0-432c-b323-b2651eec3c2b" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/73398615-f1a4-4615-be73-e722bdeecf89" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/031504c9-80b3-4bf0-b0de-90d4c905c98c" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/cad9c65c-f423-4142-a682-c8ac6d08a2d5" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/7606208f-47d1-4408-9512-4c4b01d5339c" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/6ed9bbf5-b013-4638-883a-91cd74316cbf" width=500 height=500>
</center>

<br><br><br><br>

## Result
---
<br>

<br><br><br><br>

# What is Cam Shift Object Tracking?
