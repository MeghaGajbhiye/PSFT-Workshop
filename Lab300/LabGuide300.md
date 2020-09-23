# Lab 400 : Configure Cloud Manager Settings

## Introduction
This lab will guide you how to configure the system settings on Cloud Manager

Time: 30 min

## Part 1. Create Windows Instance

1. On the Oracle Cloud Infrastructure console home page, click Create a VM Instance under Quick Action

   ![](./images/vmw.png "") 

2. On the Create Compute Instance page, enter a name for the Windows instance eg. windows-custom-image.

    ![](./images/WNAME.png "") 

3. Click on **Change Image**. Select Windows Server 2016 Standard, and accept the document.

    ![](./images/shapew.png "") 

4. Click on **Show Shape, Network, Storage Options**. Please select Availability Domain as AD-2. 

    ![](./images/shape3.png "") 

5. Make sure that the shape is **VM.Standard.2.1**. If not, click on **change shape** and select Instance Type as **Virtual Machine**, Shape Series as **Intel Skylake**, and Shape name as **VM.Standard.2.1**. 

    ![](./images/shapeselect.png "") 

6. In **configure networking** section, make sure that Virtual Cloud Network Compartment is **Demo**, Virtual Cloud Network is **OCIHOLVCN**, Subnet Compartment is **Demo** and Subnet is **Public Subnet-OCIHOLVCN**.

    ![](./images/nwin.png "") 

7. Click Create.

8. On the Details page, make a note of the Public IP Address, the username, opc and copy Initial Password to your local clipboard.

    ![](./images/wdetail.png "")

## Part 2. Access the Windows Instance with Remote Desktop Connection

After you create the Windows instance, use Remote Desktop Connection to access it.

1. Launch Remote Desktop Connection, for example from the Start menu of a local Microsoft Windows host.

2. In the Computer field, enter the Public IP address of the Microsoft Windows VM that you noted in the previous section. Enter opc in the User name field.

![](./images/pwin6.png "")

3. Click Connect.

4. Enter the default password you noted from the instance details page.

5. Click Yes on the security message, which mentions that the identity of the remote computer cannot be verified.

6. Change the password to a complex password. You will change it again in a later section.

## Part 3. Create a Generalized Image

1. In the Windows instance VM, open a browser and go to Windows Generalized Image Support Files.

2. Download the support file that is appropriate for the shape you are using.

3. Save the file in the default location.

4. Right-click the file you downloaded, and select Run as Administrator.

5. Extract the files to C:\Windows\Panther. The following files are extracted for all Windows Server versions:

    - Generalize.cmd
    - Specialize.cmd
    - unattend.xml
    - Post-Generalize.ps1

6. Right-click Generalize.cmd and select Run as Administrator. The process typically ends the Remote Desktop session. If not, log out of the session.

7. Wait a few minutes for the process to complete.

## Part 4. Create a Custom Image

1. In Compute Console, select Compute, Instances.

2. Locate the updated Windows instance.

3. Click the Actions icon, and select Create Custom Image.

4. Select the compartment where you want the custom image to reside.

5. Enter a name, such as custom-win-image.

![](./images/pwin7.png "")

6. Click Create Custom Image

7. Monitor the progress on the Compute, Custom Images page.

8. When the status of the custom image changes to Available, copy the OCID for the image. You use it in the next section.

![](./images/pwin8.png "")

**NOTE**: After you create the custom image, you can safely remove the instance used to create the image.

## Part 5. Configuring settings

1.	Navigate to **Cloud Manager Dashboard -> Cloud Manager Settings -> Cloud Manager Settings**.

2.	Update **My Oracle Support (MOS) Credentials**.  This is required to download DPKs and PRPs automatically. 

![](./images/1.png "")

3.	Navigate to Infrastructure Settings and update Operating System Images.     
    For Linux, enable **“Marketplace Image”** radio button and choose the latest version from the displayed list.

    For Windows image, please paste the OCID of the custom image you just created.
 
    ![](./images/image.png "")

4.	Click ‘**Save**’ to save the configuration. 

5.	Click ‘**Refresh OCI Metadata**’ button on top of the page and wait for few minutes.

6.	Next, navigate to **File Server tab**.  Accept the defaults.   For Mount Target, type “**lab**”.

![](./images/3.png "")

7.	Click Create.  This action will create a file server in a few minutes. 

    This will take some time. Please wait until the file server status shows ‘FSS Configured’, and then the system will be ready for downloads. 




