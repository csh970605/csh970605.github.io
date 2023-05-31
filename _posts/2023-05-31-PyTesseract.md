---
title: PyTesseract
author: SeHoon
date: 2023-05-31 20:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is PyTesseract?
Python-tesseract is an optical character recognition (OCR) tool for python. That is, it will recognize and read the text embedded in images.
<br><br><br><br>

## Functions of PyTesseract
---
<br>

+ get_languages : Returns all currently supported languages by Tesseract OCR.

+ get_tesseract_version : Returns the Tesseract version installed in the system.

+ image_to_string : Returns output as string from Tesseract OCR processing.

+ image_to_boxes : Returns result containing recognized characters and their box boundaries.

+ image_to_data : Returns result containing box boundaries, confidences, and other information.

+ image_to_osd : Returns result containing information about orientation and script detection.

+ image_to_alto_xml : Returns result in the form of Tesseract ALTO XML format.

+ run_and_get_output : Returns the raw output from Tesseract OCR. Gives a bit more control over the parameters that are sent to tesseract.

<br><br><br><br>

## Parameters of functions
---
<br>

+ image : input image.

+ lang : Tesseract language code string. Default = eng. If you want to use multiple languages : set it **lang='eng+kor'**.

+ config : Any addition custom configuration flags that are not available via the pytesseract function.

+ nice : modifies the processor priority for the Tesseract run. Note that it doesn't work on Windows.

+ output_type : specifies the type of the output. Default = string.

+ timeout : duration in seconds for OCR processing.

+ pandas_config : Used only for the pyTesseract.Output.DATAFRAME type in image_to_data function.


<br><br><br><br>

## Flags of config
---
<br>
It is used as **configu= '--oem 1 --psm 0'**

+ oem : OCR Engine mode

    + 0 : Legacy engine only.
    
    + 1 : [LSTM](https://csh970605.github.io/posts/LSTM/) engine only.

    + 2 : Legacy + LSTM engines.

    + 3 : Default.

+ psm : page segmentation mode

    + 0 : Orientation and script detection (OSD) only.

    + 1 : Automatic page segmentation with OSD.

    + 2 : Automatic page segmentation, but no OSD, or OCR.

    + 3 : Default. Fully automatic page segmentation, but no OSD.

    + 4 : Assume a single column of text of variable sizes.

    + 5 : Assume a single uniform block of vertically aligned text.

    + 6 : Assume a single uniform block of text.

    + 7 : Treat the image as a single text line.

    + 8 : Treat the image as a single word.

    + 9 : Treat the image as a single word in a circle.

    + 10 : Treat the image as a single character.

    + 11 : Sparse text. Find as much text as possible in no particular order.

    + 12 : Sparse text with OSD.

    + 13 : Raw line. Treat the image as a single text line, bypassing hacks that are Tesseract-specific.

    
    
