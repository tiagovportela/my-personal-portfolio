---
title: Elite Paddlers Stroke Classification
subtitle: Development of a method to classify elite paddlers strokes.
date: 2022-07-26T12:16:08.532Z
draft: false
featured: false
image:
  filename: featured.jpg
  focal_point: Smart
  preview_only: false
---
One of the most important challenges in the competitive Kayaks production industry is figuring out whether a new model performs better and where it can be improved. This task is not trivial, as it is not always clear how to measure performance as well as ensure that tests are performed under similar conditions.

Ideally, the metric that best represents boat performance is speed, but it is not always possible to guarantee similar conditions between tests, as there are many variables to consider - for example, water current, wind direction and speed, and athlete's performance .

If the environmental variables are easy to verify, the athlete's performance proves to be an arduous task. Thus, a systematic method of evaluating the athlete's performance is imperative.

To mitigate this problem a form of classification of the athlete's strokes was developed. In this way, it is possible to verify if in a series (exercise), there was a similar number of good strokes.

For this task, we used a data acquisition system (DAS) consisting of an inertial sensor (IMU) and a web server, plus an Android application, which allows recording and synchronizing video frames with DAS data.

![](reference_frame.png "DAS Reference Frame")

After collecting the data, 3 datasets were chosen that meet the following requirements.

* Same Environmental conditions
* Same training routine
* Equal speed

### Roadmap

1. Find starting point of the stroke
2. Divide Stroke into its various phases
3. Calculate indicators for eche phases
4. Classify strokes groups based on its indicators

# Stroke Phases Division

"Canoe paddle strokes are the means by which a paddle (or paddles) is used to move a canoe through the water.";

For this study, it is important to divide the stroke into its various components or phases.

From the observation of the movement of the boat-paddle-athlete system, we can divide the different phases according to the image below:
 

![](observational-model-for-kayak-analysis-including-two-levels-of-analysis-phases-and.png)

The signals that are collected look like this.

![](das_signal_translation_full.jpeg "Translation acceleration signals")

![](das_signal_angular_full.jpeg "Angular position signals")

Observing the signal above we can see that there are 3 strokes (3 peaks), considering that the loss of acceleration is maximum at the exact moment before the paddle enters the water, we can say that the phase in the water starts at this point and lasts until first negative peak, entering area phase

The entry lasts until the maximum acceleration point, then entering the pull phase which lasts until the acceleration is negative, entering the exit face.