# PeopleSoft Migration to Oracle Cloud Infrastructure 

## Introduction
In this hands on lab, the users are provided with step-by-step instructions on setting up a user group, creating and adding users, creating compartment and respective policies in the Oracle Cloud Infrastructure. Subsequently, this guide instructs how to install the Cloud Manager 11 using Marketplace. The final section provides the steps to provision a PeopleSoft Environment followed by some simple hands-on exercises for you to get familiar with the system.

The lab is divided into the following sections:

## Overview of Labs

Lab 100: Setup Oracle Cloud Infrastructure.

Lab 200: Create Identity and Access Management (IAM) resources.

Lab 300: Provision Peoplesoft Cloud Manager using Marketplace.

Lab 400: Configure Cloud Manager Settings 

Lab 500: Subscribe to PeopleSoft Download Channels 

Lab 600: Review and Update a Topology

Lab 700: Create a new Environment template

Lab 800: Create Environment in Peoplesoft

## Time duration

Review Lab 600 for details on the resources created by deployment automation. This session should take about 90 minutes approximately. 

Lab 400, when you subscribe to download channels, time taken for downloads to complete depends on network speed and the number of subscribed download channels. If only one application channel and one PeopleTools channel with only the latest patch is subscribed, then downloads should complete in about 60 to 90 minutes depending on the download speed. 

Lab500, 600, 700, should take you approximately 60 to 75 minutes, you will be able to create a Topology, an Environment Template and provision a new PeopleSoft environment.


## Reviewing Pre-requisistes

1. User already has a tenancy with Administrator user access. 

2. My Oracle Support credentials

3. Minimum resources in Home region of the tenancy:

	a. 4 x VM shapes (VM.Standard2.2 or VM.Standard2.1, VM.StandardE2.2 or VM.StandardE2.1)

	b. 1 TB block storage

4. User brings their own Windows workstation/laptop to access OCI console, PSFT Cloud Manager and provisioned instances. 

5. User has access to a Windows workstation/laptop with the following installed:

	a. Git Bash for Windows - https://git-scm.com/download/win 

	b. A web browser to connect to OCI web console and Cloud Manager PIA – Firefox or Chrome recommended.

	c. User must have admin privileges on windows laptop to update the ETC/Hosts file to be able to add URL/IP address for PSFT Cloud Manager.


