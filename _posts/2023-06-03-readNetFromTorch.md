---
title: readNetFromTorch
author: SeHoon
date: 2023-06-03 14:08:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is readNetFromTorch?

**cv2.dnn.readNetFromTorch(model, isBinary, evaluate)** reads a network model stored in Torch7 framework's format where<br>

+ model : Path to the file, dumped from Torch by using **torch.save()**.

+ isBinary : Specifies whether the network was serialized in ascii mode or binary.

+ evaluate specifies testing phase of network. If ture, it's similar to evaluate() in Torch.

Note that the loading file must contain serialized nn.Module object with importing network.
