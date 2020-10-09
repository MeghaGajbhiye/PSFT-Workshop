# PeopleSoft Migration to Oracle Cloud Infrastructure (OCI)

## Introduction
In this hands-on lab, the users are provided with step-by-step instructions on setting up a user group, creating and adding users to a group, and creating a compartment and respective policies in the **Oracle Cloud Infrastructure (OCI)**. Subsequently, this guide instructs how to install the Cloud Manager 11 using Marketplace. The final section provides the steps to provision a PeopleSoft Environment followed by some simple hands-on exercises for you to get familiar with the system.

You can download the Word file here : [PSFT-Workshop Doc](https://objectstorage.us-ashburn-1.oraclecloud.com/p/1EIFGD4wIGKmoToeJ241ly9AuzPIA-7oeYauUYv1Qoz-t2dmEP4OjCF5BRcmtC3Q/n/orasenatdpltoci03/b/TestDrive/o/PSFT-HOL-Workshop.docx)     

You can download the PPT file here : [PSFT-Workshop PPT](https://objectstorage.us-ashburn-1.oraclecloud.com/p/0QHo_3IYUvoU7mdHlc2CgyF9hySoay4jhb5BWNM-7ve_nQEJB4IwlK594fRVbie4/n/orasenatdpltoci03/b/TestDrive/o/PSFT-CM-LabOverview.pptx)    

You can download PDF file here: [PSFT-Workshop PDF](https://objectstorage.us-ashburn-1.oraclecloud.com/p/n7Khl1L7M_HC--UqWmwoiSv2vANQbCOFiqwFIF5xRQrZMLhzKrGviCzywpaBG67p/n/orasenatdpltoci03/b/TestDrive/o/PSFT-HOL-Workshop.pdf)  

The lab is divided into the following sections:

## Overview of Labs

**Lab 100**: Setting up Oracle Cloud Infrastructure.  

**Lab 200**: Creating Identity and Access Management (IAM) resources.  

**Lab 300**: Provisioning the Peoplesoft Cloud Manager using Marketplace.  

**Lab 400**: Configuring Cloud Manager Settings.  

**Lab 500**: Subscribing to PeopleSoft Download Channels.   

**Lab 600**: Reviewing and Updating a Topology.  

**Lab 700**: Creating a new Environment template.  

**Lab 800**: Creating Environment in Peoplesoft.  

## Time duration

**Lab 100** - 10 mins   
**Lab 200** - 20 mins   
**Lab 300** - 30 mins configuration + 1 hour waiting   
**Lab 400** - 10 mins   
**Lab 500** - 5 mins configuration + maximum 3 hours waiting   
**Lab 600** - 5 mins   
**Lab 700** - 10 mins   
**Lab 800** - 15 mins configuration + 1.5 hours waiting   


## Reviewing Prerequisite

1. User already has a tenancy with Administrator user access. 

2. My Oracle Support credentials. Please make sure that you can successfully login to [Oracle Support](https://support.oracle.com). Note down this login credential in a notepad. You will use it later to configure Cloud Manager.

3. User should bring their own workstation/laptop to access the OCI console, PSFT Cloud Manager, and provisioned instances. 

4. User has access to a workstation/laptop with the following installed:

    a. If you have a windows machine, please download Git Bash for Windows from here: https://git-scm.com/download/win  

    b. User must have admin privileges on their laptop to update the **etc/hosts** file to add URL/IP address for PSFT Cloud Manager. Please let the team know if you can't get this access.

    **NOTE: If you don't have admin privileges in your local machine, please make sure to follow the "Windows VM Compute" Lab. You can use the windows compute to follow this Workshop. Please also make sure to install Git Bash in Windows Compute.** You will also need to install **Remote Desktop Connection** in your local machine from this [link](https://www.microsoft.com/en-us/p/microsoft-remote-desktop/9wzdncrfj3ps).

    c. A web browser to connect to OCI web console and Cloud Manager PIA – Firefox or Chrome recommended.
	

## Acknowledgements

**Created By/Date**   
- Rich Konopka, Peoplesoft Specialist, October 2020  
- Megha Gajbhiye, Cloud Solutions Engineer, October 2020  

## See an issue?

Please submit feedback using this [form](https://apexapps.oracle.com/pls/apex/f?p=133:1:::::P1_FEEDBACK:1). Please include the **workshop name**, lab and step in your request. If you don't see the workshop name listed, please enter it manually. If you would like for us to follow up with you, enter your email in the **Feedback Comments** section.