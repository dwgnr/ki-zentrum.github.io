---
title: "Voice Transformation"
layout: page
sitemap: false
permalink: /research/voice-trafo/
---

## Motivation

Whispered speech is a form of communication that is usually used only for a limited period of time, e.g. to guard against unwanted listeners or in areas where loud noises are prohibited.

In clinical interventions necessitated by throat cancer (laryngectomy), affected individuals face permanent limitations in verbal communication. 
After the procedure, patients learn to use a substitute voice that does not involve the larynx in the formation of sounds. 
However, the substitute voices that patients learn are often characterized by hoarseness, low volume, and an altered or non-existent fundamental frequency. 
This makes many everyday situations more difficult for throat cancer patients and ultimately reduces their quality of life.

Speech without the larynx and whispered speech have similar characteristics. 
Therefore, the transformation of breathed or whispered speech into voiced speech has become an active research area with a high practical relevance.

## Project Goals 

The aim of this project is to improve the intelligibility and naturalness of the voices of laryngectomy patients based on whispered speech by leveraging the advances made in the field of generative models. 

The approaches used include Variational Autoencoders (VAEs) and Generative Adversarial Networks (GANs) {% cite wagner2023generative %}. 
As these systems were not originally developed to transform whispered speech or substitute voices, they require suitable modification, for example in terms of their cost function and other model elements. 
Following this, they can be trained using speech recordings of laryngectomy patients and whispered voices.  

## Results

Results related to this project were published in the following peer-reviewed conferences and journals:

{% bibliography --cited --group_by none %}
