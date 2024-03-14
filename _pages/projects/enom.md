---
title: "ENOM: Embedded Non-Obtrusive Monitoring of Voice and Speech Disorders"
layout: page
sitemap: false
permalink: /research/enom/
---

## Project Goals

Stuttering is a well-known speech disorder with a prevalence of about 5% in children and 1% in adults. It is more commonly found in males than females. The cause of this speech disorder has not been conclusively identified. While not curable, it is treatable. Treatment approaches focus on symptom management, such as speech-assistive devices and rhythmization exercises. These can lead to rapid improvements but not necessarily to long-lasting therapeutic success. The behavioral therapy method used by our project partner, the [Kasseler Stottertherapie](https://kasseler-stottertherapie.de), specifically targets more fluent speech through a technique called "fluency shaping" that modifies the entire speech process.

This speech technique is typically learned in an intensive two-week therapy. Initially, visual biofeedback is used, where pronunciation is analyzed in real time and graphical feedback is displayed to the speaker. The technique is first learned on individual sounds and words, and then applied to connected sentences in spontaneous daily situations. After the initial on-site phase, clients continue to receive telemedical support.

A critical point is when clients leave the therapy environment, as this understandably leads to stress. At this point, continuous therapy progress monitoring, which is non-intrusive and functional in everyday client life, would be ideal. The project aims to analyze client speech in the background, log any anomalies, and provide therapists and clients with objective feedback on speaking behavior in daily situations. To comply with the General Data Protection Regulation (GDPR), it is essential that data is processed locally and not shared with third parties. Thus, a system that can process and classify speech on the device is needed. This requires a dataset containing modified speech, stutter-typical abnormal speech, and fluent spontaneous speech in realistic conditions. An intermediate goal is to create an extensively labeled dataset to train a classifier that can distinguish between fluent speech, modified speech, and stutter-typical symptoms, and then adapt it to work on mobile devices. The final step is to combine these results to create an overall system.

## Previous Research Work and Results

The foundation of automated speech analysis often lies in a speech recognition system. The first step was selecting a dataset containing spontaneous German speech, training a modern end-to-end speech recognizer, and comparing it with proven speech recognition methods. This comparison specifically targeted the usability of small to medium-sized datasets for syllable recognition (Bayerl and Riedhammer, 2019). The use of sub-word units is crucial in paralinguistic analyses. Additionally, the utility of various speech and syllable recognizers in paralinguistic analysis was compared and evaluated.

One project goal is creating a comprehensive labeled dataset suitable for training machine learning models. Thanks to excellent collaboration with the Kassel Stuttering Therapy, an extensively labeled dataset was completed in February 2019. This dataset contains data from 37 stutterers (9 female, 28 male), recorded at different stages of therapy. It includes general disfluencies, interjections, silent blocks, repetitions of syllables and words, and incomplete words and sentences. To our knowledge, this is the most comprehensive dataset of its kind, allowing for various experiments and paralinguistic analyses.

In collaboration with the Kassel Stuttering Therapy, various stuttering-related metrics were evaluated, and a connection to prosodic features, specifically average sound duration, was established. Statistical analyses were conducted to show that a modified speech recognizer can identify disfluent speech parts. The Speech Control Index (SCI) was introduced and compared with the Speech Efficiency Score (SES, Amir et al. 2018) for their suitability in stuttering therapy {% cite bayerl2020taa %}.

Classifying and distinguishing time series, which include audio data, is challenging. Before the labeled dataset was available, a foray into general time series analysis was made, developing a novel system using deep convolutional neural networks (CNNs). The system uses Recurrence Plots for visualizing and classifying time series. Applied to a large benchmarking dataset, excellent results were achieved, rivaling and in some cases surpassing the best existing systems. This method can potentially be adapted for distinguishing between stuttered and fluent speech.

To explore embedded and on-device recognition, collaboration with security researchers at the Technical University of Darmstadt led to adapting a speech recognizer to run on an embedded system in a secure, enclosed environment. This solves the conflict of interest between a service provider and the user: protecting the user's data from the provider and the provider's intellectual property from the user. For a prototype based on the Android system described in the project application, a "proof of concept" was created during two workshops. The results of the first workshop were published at the Interspeech Conference 2019 in Graz (Vasquez et al., 2019). Although the application's focus was on Parkinson's disease recognition, the results are transferable to stuttering by swapping the recognition models and incorporating stutter-specific speech exercises.

## Challenges

Particularly, changes to the Android operating system have resulted in the inability to continuously record speech in everyday situations or during phone calls. Therefore, an embedded analysis on smartphones is currently not a viable option, although its feasibility has been demonstrated (Vasquez et al., 2019). A potential alternative to smartphones could be devices similar to modern voice assistants like Alexa or Google Home that are always listening. However, unlike these devices, the speech data would be processed locally, not in the cloud. These devices would need to meet the same requirements as the app described in the research proposal, meaning they should be capable of speaker separation, speech recognition, and classifying speech into categories such as fluent, modified, and disfluent.

Creating and particularly labeling the data proved difficult and initially made slow progress. The accuracy and diversity of labels needed to enable classification outside laboratory conditions delayed the dataset creation process. The group of people who could consistently label stutter-specific and modified speech is very small. Due to the high time expenditure, the labeling process is expensive and slow.

## Results

The ENOM Project concluded 2022, the results were published in peer-reviewed conferences and journals:

{% bibliography --cited --group_by none %}
