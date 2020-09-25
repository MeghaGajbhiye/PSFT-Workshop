# Lab 200: Creating Identity and Access Management (IAM) resources.  

## Introduction

Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) Service lets you control who has access to your cloud resources. You control the types of access a group of users has and to which specific resources. The purpose of this lab is to give you an overview of the IAM Service components and an example scenario to help you understand how they work together.

## Prerequisites

1.	Oracle Cloud Infrastructure account credentials (User, Password, and Tenant)

2. 	To sign in to the Console, you need the following: 

        1. Tenant, User name and Password
        2. URL for the Console: https://oracle.com
        3. Oracle Cloud Infrastructure supports the latest versions of Google Chrome, Firefox, and Internet Explorer 11

## **Step 1:** Signing in to the Console

Console Overview
In this, you sign in to the Oracle Cloud Infrastructure console using your credentials.

1.	Open a supported browser and go to the Console URL: https://oracle.com.

2.	Click on the portrait icon in the top-right section of the browser window, then click on the Sign in to Cloud link.

![](./images/1.png "")

3.	Enter the name of your tenancy (aka your account name, not your user name), then click on the Next button.

![](./images/2.png "")

4.	Oracle Cloud Infrastructure is integrated with Identity Cloud Services. You will see a screen validating your Identity Provider. Enter your username and password. Click Sign In.

![](./images/signin1.png "")

![](./images/3.png "")

5.	When you sign in to the Console, the dashboard is displayed.

![](./images/homepage.png "")

## **Part 2:** View Service Limit.

During the workshop, you might face problems related to service limit. 
Please check if you have enough resource availability in your Availability Domain or change the Availability Domain to 1/2/3 as per the resource availability. 

1. To check the service limit, navigate to the three-line menu on the top left and click on **Governance -> Limits, Quotas, and Usage**.

![](./images/slimit.png "")

2. Click on **Scope** and select AD-1 or AD-2 or AD-3 depending on which availability domain you want to see the service limit. 

![](./images/scope.png "")

3. Scroll down the list, and you will see all the resources available and usage. For example, in the below case, all my available resources are used.

![](./images/available.png "")

## **Step 3:** Creating Compartments

**Compartments Overview:**

A compartment is a collection of cloud assets, like compute instances, load balancers, databases, etc. By default, a root compartment was created for you when you created your tenancy (ie, when you registered for the trial account). It is possible to create everything in the root compartment, but Oracle recommends that you create sub-compartments to help manage your resources more efficiently.

1.	Click on the three-line menu, which is on the top left of the console. Scroll down till the bottom of the menu, click on **Identity -> Compartments**. Click on the blue **Create Compartment** button to create a sub-compartment.

![](./images/compartmentn.png "")

![](./images/createcompartment.png "")

2.	Name the compartment **Demo** and provide a short description. Be sure your root compartment is shown as the parent compartment. Press the blue **Create Compartment button** when ready.

![](./images/compartment.png "")

3.	You have just created a compartment for all of your work in this Test Drive.

## **Step 4:** Managing Users, Groups, and Policies to Control Access

**Security Overview:** 

A user's permissions to access services come from the groups to which they belong. Policies define the permissions for a group Policies explain what actions members of a group can perform, and in which compartments. Users can access services and perform operations based on the policies set for the groups.

We'll create a user, a group, and a security policy to understand the concept.

1.	After signing in to the console, click on the three-line menu on the top left. Click on **Identity -> Groups**.

![](./images/group.png "")

2.	Click **Create Group**.

3.	In the Create Group dialog box, enter the following:

        1. Name: Enter a unique name for your group, such as "oci-group” Note that the group name cannot contain spaces.

        2. Description: Enter a description (for example, “New group for OCI users”).

        3. Click Submit.

![](./images/creategroup.png "")

4.	Your new group is displayed.

![](./images/newgroup.png "")

5.	Now, let’s create a security policy that gives your group permissions in your assigned Compartment. In this case, we will create a policy that permits users belonging to group **oci-group to provision Peoplesoft Cloud Manager in Compartment Demo**:

    a) Click on the three-line Menu button on the top left. Click on **Identity -> Policies**.

    ![](./images/policyn.png "")    

    b) On the left side, navigate to **COMPARTMENT** and select **root compartment**. 

    ![](./images/compartmentselect.png "")

    c) After you have selected the root compartment, click **Create Policy**.

    d) Enter a unique Name for your policy (For example, "**Policy-for-oci-group**"). Note that the **name can NOT contain spaces**.

    e) Enter a Description (for example, "Policy for OCI Group").

    f) Enter the following Statement:
    
    ```
    Allow group oci-group to manage all-resources in compartment Demo
    Allow group oci-group to read all-resources in tenancy
    Allow group oci-group to manage App-catalog-listing in tenancy
    ```  

    ![](./images/policy.png "")    

    g) Click **Create**.


6. Create a **New User**
   
    a) Click on three-line menu on top left, and click on **Identity -> Users**.

    b) Click **Create User**.

    c) Select IAM user. 

    ![](./images/UserTypeIAM.png "")    

    d) In the New User dialog box, enter the following:

        Name: Enter a unique name. This user should have a unique name in the tenancy.

        Description: Enter a description - For example, New OCI user.

        Email: Enter your email ID and confirm it. Please make sure not to use the same email ID. Email ID has to be unique in the tenancy. If you don't have another email ID, you can leave it blank.

    ![](./images/createuser.png "")

    e) Click **Create**.


7.	Set a **Temporary Password** for the newly created User

    a) After the user is created, you can see the user details.

    b) Click **Create/Reset Password**.

    ![](./images/userdetail.png "")

    c) In the dialog, click **Create/Reset Password**.

    ![](./images/13.png "")

    d) The new one-time password is displayed. Click the **Copy button** and then click Close. Make sure to copy this password to your notepad.

    ![](./images/newpassword.png "")

    e) Scroll down and click on **Add User to Group**.

    ![](./images/scrolladdgroup.png "")

    f) Select the group you just created, and click on **Add**.

    ![](./images/adduser.png "")

    g) Click on **top-right icon button** and **Sign out** of the admin user account.

    ![](./images/signout.png "")


    This time, you will sign in using the local credentials box with the user you created. Note that the user you created is not part of the Identity Cloud Services.

    d) Enter the username **User01** and password that you copied.

    ![](./images/signin.png "")

    ```
    Note: Since this is the first-time sign-in, the user will be prompted to change the temporary password, as shown in the screen capture.
    ```

    e) Set the new password to Psft@1234. Click on **Save New Password**. 

    ![](./images/17.png ""){:height="50%" width="50%"}

    You are now logged in as local user: **User01**














