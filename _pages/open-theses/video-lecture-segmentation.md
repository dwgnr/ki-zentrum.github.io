---
title: "Thesis: Video Lecture Segmentation"
layout: page
sitemap: false
permalink: /open-theses/video-lecture-segmentation
---

The [Hochschul-Assistenz-System (HAnS)](https://www.th-nuernberg.de/fakultaeten/sw/forschung/laufende-forschungsprojekte/entwicklung-und-implementierung-eines-intelligenten-hochschul-assistenz-systems-hans/) is a platform to browse and work with video lectures.
Starting out from an indexed and time-referenced transcript, we use machine learning to compute topic segments, summaries and even provide an AI tutor that can be used to produce automated questionnaires or to interact with the document.

The objective of the thesis is to develop an algorithm for the extraction of information from lecture materials (audio, video, slides).
The extracted information will then be indexed and made searchable through an information retrieval system based on elasticsearch.

![video lecture segmentation](/images/segmentation.png)

The necessary steps include:

1. Alignment between slides and audio.
2. Alignment between audio and video transcript.
3. Object detection and recognition on the slides.
4. Extraction of information on the slides in a suitable format.
5. Recognition of connections between slides and text elements.
6. Consolidation of all extracted information.
7. Indexing of information in a Retrieval System.

Prerequisites:

- Good programming skills in python, ideally with experimence innumpy, pandas, torch, and Matplotlib.
- Independent and reliable work
- Basic skills in applied machine learning, eg.
	- object detection (eg. YOLO, G-RCNN)
	- OCR from pdf or video stills
	- NLP, especially NER, Dependency Parsing, and Text Classification.

If interested, please email [Fabian Schneider](mailto:fabian.schneider@th-nuernberg.de)
