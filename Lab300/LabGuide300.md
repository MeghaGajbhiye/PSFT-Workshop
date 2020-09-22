# Lab 400 : Configure Cloud Manager Settings

## Introduction
This lab will guide you how to configure the settings on Cloud Manager

Time: 20 min

## Part 1. Configuring settings

1.	Navigate to Cloud Manager Dashboard -> Cloud Manager Settings -> Cloud Manager Settings.

2.	Update My Oracle Support (MOS) Credentials.  This is required to download DPKs and PRPs automatically. 

![](./images/1.png "")

3.	Navigate to Infrastructure Settings and update Operating System Images. For Linux, enable “Marketplace Image” radio button and choose the latest version from the displayed list.

    For Windows image, please select the custom image from the following site depending on your region. 

    https://docs.cloud.oracle.com/en-us/iaas/images/image/146ab34c-064a-4255-b5ea-e26bbfa6591d/

    For example, I have selected following image from us-ashburn-1 region as that is my home region: **ocid1.image.oc1.iad.aaaaaaaahobtltelwdrzm6sd3nn6j7fsb3bwinq2ggmpcnsgdvhihnz2mhga**
 
    ![](./images/image.png "")

4.	Click ‘Save’ to save the configuration. 

5.	Click ‘Refresh OCI Metadata’ button on top of the page and wait for few minutes.

6.	Next, navigate to File Server tab.  Accept the defaults.   For Mount Target, type “lab”.

![](./images/3.png "")

7.	Click Create.  This action will create a file server in a few minutes. 

8.	Wait until the file server status shows ‘FSS Configured’, and then the system is ready for downloads. 




