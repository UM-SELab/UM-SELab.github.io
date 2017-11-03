---
layout: post
title:  "Traditional Chinese Prescription Process, Analysis and Prediction"
date:   2017-11-03 
categories: EHRs 
author: Yilong Yang, Xiaoshan Li, Peng Liu
---

The traditional Chinese medicines prediction project is composed of a lot of tools with different functions, including records processing tools(XML generation tool, JSON generation tool and database importing tool), statistics tools and prediction tools. The main tools of the project include: 

- XML generation tool
- JSON generation tool
- Database importing tool
- Machine Learning data processing tool
- Records query tool
- Records statistics tool
- Traditional Chinese medicines prediction tool

The main features of the project include:
- Format records data with a standard and unified structure to store into database.
- Query records based on the input conditions, including patient's name, processing method, traditional Chinese medicines and the input symptoms.
- Statistics records with different targets, such as the frequency and percent of traditional Chinese medicines in all records, the frequency and percent of medicines diagnose in all records and the frequency and the percent of different conbination of Chinese medicines in all records to find and generate a lot of rules. 
- Prediction tool is used to predict the traditional Chinese medicines based on the input symptoms or the exist records.In the tool, there are three main prediction methods: case-based reasoning method, machine learning and rule-based method.

### Architecture
EHR application has seven main tools: XML generate tool, JSON generate tool, Database import tool, Machine learning data processing tool, query tools, statistics tools and prediction tools. Figure 1 show the architecture of application. Struts 2, Spring and Hibernate (SSH) make up a framework for development of Java web application. It uses the Model-View-Controller design pattern and JavaBean as the basic technologies. Java and JSP are used as the implementing language in SSH development.Above this framework, we built the application with different functions, including query, statistics and prediction function. MongoDB is the basic database to store records.

{% include img.html url="ehrarchitecture.png" %}

#### Automated Prescription Prediction based on Nerual Network
{% include img.html url="ml-lungcancer.png" %}

#### Integrated Prediction based on Statistics, Rule and Machine Learning
{% include img.html url="ehrprediction.png" %}

### System Demo
{% include video.html url="EHR.mp4" %}

