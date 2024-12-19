---
title: "Data"
layout: page
sitemap: false
permalink: /data/
---

# Kassel State of Fluency

Stuttering is a complex speech disorder that negatively affects an individual’s ability to communicate effectively.
Persons who stutter (PWS) often suffer considerably under the condition and seek help through therapy.
Fluency shaping is a therapy approach where PWSs learn to modify their speech to help them to overcome their stutter.
Mastering such speech techniques takes time and practice, even after therapy.
Shortly after therapy, success is evaluated highly, but relapse rates are high.
To be able to monitor speech behavior over a long time, the ability to detect stuttering events and modifications in speech could help PWSs and speech pathologists to track the level of fluency.
Monitoring could create the ability to intervene early by detecting lapses in fluency.
To the best of our knowledge, no public dataset is available that contains speech from people who underwent stuttering therapy that changed the style of speaking.
This work introduces the Kassel State of Fluency (KSoF), a therapy-based dataset containing over 5500 clips of PWSs.
The clips were labeled with six stuttering-related event types: blocks, prolongations, sound repetitions, word repetitions, interjections, and – specific to therapy – speech modifications.
The audio was recorded during therapy sessions at the Institut der Kasseler Stottertherapie.
The data will be made available for research purposes upon request and after signing the respective data license.

[KSoF](https://zenodo.org/records/6801844) {% cite bayerl2022ksof-data %}


# Kassel State of Fluency - Challenge

The stuttering Kassel State of Fluency corpus KSoF-C, provided is derived from
the Kassel State of Fluency (KSoF) corpus. The original corpus fea-
tures some 5500 typical and nontypical (stuttering) 3-sec segments
from 37 German speakers with an overall duration of 4,6 hours. The
segments contain speech of persons who stutter (PWO). The record-
ings from which the segments were extracted were recorded before,
during, and after PWOs underwent stuttering therapy.

KSOF-C only features the 4601 non-ambiguously labeled segments.
The task proposed in this challenge is the classification of speech
segments as one of the 8 classes - the seven stuttering-related classes
mentioned above and an eighth “garbage” class, denoting unintelligible segments, segments containing no speech, or segments that
are negatively affected by loud background noise. The dataset is split by speaker (train, 23 spk, devel, 6 spk, test, 8 spk)

[KSoF-C](https://zenodo.org/records/6801844) {% cite bayerl2022ksof-c %}


### References

{% bibliography --cited --group_by none %}