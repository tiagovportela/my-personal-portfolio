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