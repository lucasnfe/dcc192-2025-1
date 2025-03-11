---
layout: page
title:  FP3 - Project Presentation
permalink: /assignments/fp3-project-presentation
nav_exclude: true
---

# FP3 - Project Presentation

#### Due date: 18/12, 11:59PM

## Introduction

You spent the last 3 weeks implementing a Transformer Network “from scratch” in PyTorch to reproduce the results of a paper of your interest. In this last and final part of the final project, you will write a techical report and present your work.

## Instructions

### 1. Source code

The source code of your project has to be hosted in a github repo with a README file with a summary of the project in a README file. Include as well a brief tutorial on how to run your code. Here is an example from a project of mine: [https://github.com/lucasnfe/music-sentneuron](https://github.com/lucasnfe/music-sentneuron)

### 2. Technical Report

Your technical report needs to have at max 4 pages and contain the following sections:

1. Introduction

    This section should be similar to what you wrote in your project proposal. Describe the paper motivation, the dataset that was used, and summarize its main contributions in terms of methods and results. Include a footnote with a link to the dataset and/or github repository.

2. Implementation Detais

    Describe the overall strutucture of your code, focusing on how each class implements a particular layer of the transformers. Explain which parts you used from the pytorch framework and which ones you created "from scratch". Describe how your code is different from the authors' code and, if you used as references, what you had to change for your project.

3. Experimental Setup

    Present all the details of your training loop: sizes of the model, optimizer, learning rate, number of epochs, dropout rate, hardware configuration, etc. Discuss how it differs from the original papers's setup. If you had to change the dataset (e.g., reduce the size), describe these changes as well.

4. Results

    Show your results using tables (e.g., accuracy) and/or graphs (learning curves). Discuss how they differ from the authors' results.

5. Discussion

    Briefly discuss the main challenges you had when reproducing a transformer.

### 3. Presentation

You will have **10 minutes** to present your work! Make a deck of slides **on google drive** (to make it easier to switch slides during the presentations) to present the content you wrote in your technical report. Try to follow the same structure of the report in your presentation. Feel free to show some of your code during the presentation if you want. 

### 4. Submission

Submit (a) your proposal as a pdf file, (b) your code as a github url and (c) your slides as a google drive url to the FP3: Project Presentaion task on Moodle.
