---
layout: post
title: Access Globus from a Jupyter Notebook
feature-img: "assets/img/background-color.png"
date: 26 November 2024
---

## Introduction
### Globus SDK

The [Globus Python SDK](https://globus-sdk-python.readthedocs.io/en/stable/)
allows you to access and control [Globus services using Python code](https://www.globus.org/blog/using-globus-jupyter-notebooks) in a Jupyter Notebook

<img src="/assets/img/tutorialsimages/nbk/1.png" >
<!--![image](https://user-images.githubusercontent.com/79628214/118164353-05291200-b3f1-11eb-985c-ccc4fac32b9a.png)-->


### Summary of the steps

[Get a Client](https://globus-sdk-python.readthedocs.io/en/stable/tutorial.html#tutorial-step1) <br>
[Get and Save Client ID](https://globus-sdk-python.readthedocs.io/en/stable/tutorial.html#tutorial-step2) <br>
[Get Some Access Tokens!](https://globus-sdk-python.readthedocs.io/en/stable/tutorial.html#tutorial-step3) <br>
[Use Your Tokens, Perform operations.](https://globus-sdk-python.readthedocs.io/en/stable/tutorial.html#tutorial-step4) <br>

<!--#Image 2 -->
<!-- ![image](https://user-images.githubusercontent.com/79628214/118171830-aa47e880-b3f9-11eb-9f70-b81f8710265d.png)-->
<img src="/assets/img/tutorialsimages/nbk/2.png" >

* Use the [Globus Developers page](https://developers.globus.org/) to register an application. <br>
* Use the drop down menu to select your institution.  

### Create the Project
<!-- #Image 3 -->
<!-- ![image](https://user-images.githubusercontent.com/79628214/118172605-90f36c00-b3fa-11eb-8119-690e9313046a.png)-->
<img src="/assets/img/tutorialsimages/nbk/3.png" >


Follow screen directions, to create a project. <br>
Fill in the details that are required for the project. <br>
After successfully creating a project, click on ‘add app’.
Use this example [tutorial](https://globus-sdk-python.readthedocs.io/en/stable/clients/transfer.html) .

### Application registration
<!-- #Image 4 -->
<!-- ![image](https://user-images.githubusercontent.com/79628214/118172672-a2d50f00-b3fa-11eb-9814-c97d50c8f631.png)-->
<img src="/assets/img/tutorialsimages/nbk/4.png" >


* By clicking on add new app, App registration page opens. <br>
* Enter all the required information for the app registration. <br>
* Make sure, you click on “Native app” if you  would like to run the app on local host otherwise, you may use the URI and other required information related to your application. <br>
* By clicking on “Create App,”  the app is successfully created under the project. <br>
* For this tutorial, a ‘Native app’ is created and used same redirect URLs and scopes as specified  in the [tutorial.](https://globus-sdk-python.readthedocs.io/en/stable/tutorial.html#tutorial-step1) <br>

### Generating client ID

<!-- #Image 5 -->
<!--![image](https://user-images.githubusercontent.com/79628214/118172708-acf70d80-b3fa-11eb-9bc2-699fe98203d9.png)-->
<img src="/assets/img/tutorialsimages/nbk/5.png" >

By creating an application, a Client ID is generated. <br>
This Client ID is very important for the further steps in the process. <br>

### Accessing Jupyter notebook

<!--#Image 6 -->
<!-- <img width="565" alt="image" src="https://user-images.githubusercontent.com/79628214/118180232-4e369180-b404-11eb-91c0-3723a61e417c.png"> -->
<!--<img width="565" alt="image" src="https://i.imgur.com/gDC89xy.png">-->
<img src="/assets/img/tutorialsimages/nbk/6.png" >


Open the Jupyter Notebook and start importing libraries. <br>
Gather the UUIDs of the endpoints you wish to exchange the information with. <br>
The Globus Python SDK makes transfer functionality available via a TransferClient class. <br>
We want to configure a TransferClient with an OAuth2 access token, to authenticate its connections with Globus. <br>
The client ID generated is used.

### Authenticating the application in jupyter notebook

<!-- #Image 7 -->
<!--![image](https://user-images.githubusercontent.com/79628214/118180294-5bec1700-b404-11eb-97bb-9933c1a07438.png)-->
<img src="/assets/img/tutorialsimages/nbk/7.png" >
Since the app is native app, when we run the Oauth, and this generates a link in the output. <br>
By clicking on the link, you will be redirected to a page with the authentication code. <br>
Copy the authentication code. This code is valid for only 10 minutes. <br>
Every time we rerun the cell; it generates new link with new code. <br>



<!--#Image 8 -->
<!--![image](https://user-images.githubusercontent.com/79628214/118180329-673f4280-b404-11eb-9f48-653fab680f34.png)-->
<img src="/assets/img/tutorialsimages/nbk/8.png" >

The authorization code looks like this

<!--#Image 9 -->
<!--![image](https://user-images.githubusercontent.com/79628214/118180386-76be8b80-b404-11eb-8214-2dd3ff6ec5a6.png)-->
<img src="/assets/img/tutorialsimages/nbk/9.png" >

This is very important step in accessing Globus from Jupyter notebook. The authorization code generated is copied and pasted here. By running this cell, it authenticates and lets the user perform further operations.

### Transferring files in Globus

<!--#Image 10 -->
<!-- ![image](https://user-images.githubusercontent.com/79628214/118180408-7e7e3000-b404-11eb-90ad-7951e9239fbc.png)-->
<img src="/assets/img/tutorialsimages/nbk/10.png" >

To perform the transfer operation, get the source and destination path and perform the transfer operation. 
This block of code generates the task ID. 
Task ID is used to get the status of the task and other information related to the task.

<!--#Image 11-->
<!--![image](https://user-images.githubusercontent.com/79628214/118180439-863dd480-b404-11eb-89c9-2768798033b7.png)-->
<img src="/assets/img/tutorialsimages/nbk/11.png" >


By using the generated task ID, the status of the task can also be determined.

<!--#Image 12-->
<!--![image](https://user-images.githubusercontent.com/79628214/118180483-935ac380-b404-11eb-9cc9-f69c179adaf3.png)-->
<img src="/assets/img/tutorialsimages/nbk/12.png" >

* Different operations can be performed. This includes:
  * Getting the previously generated task listed with their status,   
  * searching for the active,
  * successful or failed status, and
  * terminating active task.
* If the task has been successful, then you cannot terminate the task. 
