---
title: "Semmeldetector"
layout: page
sitemap: false
permalink: /research/semmel/
---

## Project Goals

The Semmeldetector, named after the locally used German word for bread bun, is a machine learning application that utilizes state-of-the-art object detection models to detect, classify, and count baked goods in images. 
The Semmeldetector aims to help commercial bakers to track unsold baked goods, which allows them to optimize production, increase resource efficiency, and reduce workload, by eliminating the otherwise required manual tracking of unsold baked goods.

To facilitate model scalability, we limit our training data to images of individual baked goods, positioned roughly in the center, which allows us to semi-automatically annotated our training data. 
To facilitate model training, we heavily employ image synthesis to enrich our training data.

## Results 1st Prototype

To train our 1st prototype we compiled a dataset comprising 1151 images that distinguishes between 18 different types of baked goods. Our training data were semi-automatically annotated using the Segment Anything Model (SAM).
(Bread buns were manually classified; localization was automated.)

We employed a custom Copy-Paste augmentation pipeline to expand our training data.
Our detection model was primarily trained on synthetic data. 
State-of-the-art object detection YOLOv8 (primarily trained on synthetic data) achieved an AP@0.5 of 89.1% on our detection task, despite our weak data foundation.
