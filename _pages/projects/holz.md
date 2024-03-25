---
title: "Detection of Wood Rot using Machine Learning"
layout: page
sitemap: false
permalink: /research/holz/
---

## Project Goals

During the processing steps of raw lumber into building materials, checking the lumber for defects and grading lumber quality is of major concern. Wood rot is the major factor degrading lumber quality. It takes expert knowledge and time to manually check lumber for the various types of wood rot occurring within. 

This project aims to drastically reduce the workload in lumber production by automatically detecting and segmenting rot and decay on the cross-section of wooden logs, specifically spruce logs.
Employing state-of-the-art semantic segmentation machine learning models allows a direct grading of lumber by predicting the wood rot percentage, which is a direct metric for grading lumber.

## Data

An extensive dataset was collected to train a semantic segmentation machine learning model for our specific task.
The dataset was initially annotated by biology students.
Annotations were double-checked by experts to guarantee correctness and increase objectivity.

Consultation with experts indicates that objectively detecting wood rot is non-trivial, even for human annotations.
Our data were further refined by using post-processing techniques to remove annotation artifacts and by updating potentially faulty annotations with model predictions.
