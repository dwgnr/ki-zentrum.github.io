---
title: "NNFuze"
layout: page
sitemap: false
permalink: /research/nnfuze/
---

## Project Description 

Deep neural networks (DNNs) have become the de-facto standard in the field of automatic image, speech and text recognition in recent years. 
The number of parameters of such systems often reaches hundreds of millions, which requires considerable memory and computational resources.

The problem increases when different networks need to be evaluated in parallel for different tasks (e.g. for speech and speaker recognition) or, in the case of multimodal classification, for different sensors {% cite wagner2023speaker %}.

As a result, these networks often have to use powerful computers to make predictions in a distributed manner, following which the predictions are then aggregated again. In the context of embedded systems or mobile devices, the use of cloud technologies is therefore inevitable. The negative aspects associated with this are higher latency and an Internet connection that is not permanently available (e.g. in the automotive sector).

For real-time-critical systems, calculations performed by neural networks are not guaranteed. In addition, increased data volumes put a strain on the infrastructure and have led to growing doubts about data security. Consequently, local inference using neural networks is an important area of research, especially on embedded systems (DSP, SoC, TPU).

For the reasons mentioned above, the market leaders for cloud solutions and smartphones are working to develop on-device solutions, using special hardware where required.  Examples of this include Apple (CoreML on A13), as well as Amazon and Google, which have been increasingly working on local solutions for their digital assistants since last year. There is growing interest in the use of machine learning in safety-critical and real-time systems or for processing particularly sensitive data.

In these areas, hardware-aware AI on embedded systems is of particular importance. This research project focuses on memory and computational optimization of neural networks for use on embedded systems and addresses the question of how different neural networks can be replaced by or merged to create a single network. Furthermore, it examines the extent to which additional resources can be saved by suitably incorporating compression approaches.


## Results

Results related to this project were published in the following peer-reviewed conferences and journals:

{% bibliography --cited --group_by none %}
