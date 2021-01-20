# NSFW Detection 
##### *Not Safe For Work content detection API*

## Introduction
1. The NSFW Detection is a RESTful API which can identify adult content through a CNN-model
2. The NSFW Detection is built with Django
3. The NSFW Detection is containerized into Dockerfile and docker-compose, so you can deploy them in any docker-installed instance

## Concept
1. The NSFW Detection uses the [Tensorflow Implementation of Yahoo's Open NSFW Model](https://github.com/mdietrichstein/tensorflow-open_nsfw) to act as the detector
2. When NSFW Detection receives an API request, it would first be distributed through Nginx
3. Then the uwsgi would receive the data from Nginx so Django may be able to process the info
4. The Django engine would identify the input type, e.g. url, image or base64 and issue them to relative corresponding serializers
5. Serializers would then preprocessing each image and use the detection model to detect the image
6. Then the result which contains file_name, user_id, test_score and etc. would be returned 
7. The NSFW Detection also has an admin backstage which can be access through browser and monitor the status of the detection status
8. The NSFW Detection can deal high-concurrency problems using Nginx
9. The average response time is 3~4 seconds

![](Pics/structure.drawio.png)

## Github Links
1. https://github.com/tpchris1/nsfw_detection
