# Lab 300 : Provisioning Cloud Manager from Resource Manager.

## Introduction
Resource Manager is an Oracle Cloud Infrastructure service that helps you install, configure, and manage resources. Resource Manager uses Terraform (which is part of the service) to codify your infrastructure in declarative configuration files, which allows you to review and edit, version, persist, reuse, and share them across teams. You can then use Resource Manager to provision Oracle Cloud Infrastructure resources using your Terraform configurations.

In this tutorial, you obtain the configuration files, or stack, for Cloud Manager from the Oracle Cloud Infrastructure Marketplace, and use Resource Manager to create an instance and link it with associated resources such as a Virtual Cloud Network (VCN), subnet, gateways, and route tables. You enter the necessary passwords and other information in the Resource Manager interface, and choose the types of resources created.
Time: 80 min

## Part 1. Generating Keys

1. Ensure Git Bash is installed on your laptop/workstation.

2. Download the following script - [make_keys.sh](make_keys.sh)

3. Launch Terminal for Mac or Git Bash for Windows command line and navigate to the folder where the file was downloaded.

4. Give permission to the file by typing in command line: **chmod 777 make_keys.sh**

6. For Windows, run the script as **bash make_keys.sh**

For Mac terminal run the command - **./make_keys.sh**

![](./images/4.png "")

7. Below set of key files are generated.  There are two sets of keys:

	I.	API Signing keys – api\_key and api\_key.pub

	II.	SSH key pair – id\_rsa and id\_rsa.pub

```
Note: These Keys are necessary for you to be able to securely connect into your PeopleSoft Cloud Tenancy.
```
![](./images/apikeypub.png "")

## Part 2. Setting API keys for User01

1. In a browser, launch the OCI console. Login as User01. After you are succesfully logged in, click on the **profle button on top right**. Click on your user name - User01.
   (Refer to Lab 200 for details on how to login as User01.)

![](./images/api.png "")

2. Scroll to the bottom, on the left side click on **API Keys** and then click on **Add Public Key**

![](./images/apisetup.png "")

3. Click on **Paste public keys** and Copy paste the content of **api_key.pub** ( the one you just created). Click on **Add**.  

![](./images/apikeypub.png "")

![](./images/apipaste.png "")

## Part 3. Gather Information for the Cloud Manager Stack

Paste below information in a notepad, you will need it later while creating the stack.

1. From the same User detail page, copy the OCID by clicking on **copy**. 

![](./images/ocid.png "")

2. On the top right, click on the region. Note the home region displayed. 

![](./images/homeregion.png "")

## Part 4. Obtain the PeopleSoft Cloud Manager Stack from the Marketplace

To obtain the PeopleSoft Cloud Manager stack:

1. On the Oracle Cloud Infrastructure console home page, click the top left three-line menu icon and select Marketplace -> Applications.

![](./images/marketplace.png "")

2. Under Filters on the left, select Stack from the Type drop-down list, and Oracle from the Publisher drop-down list. Search for Peoplesoft on the search bar. Click the PeopleSoft Cloud Manager tile.

![](./images/searchpsft.png "")

3. On the Overview page for the PeopleSoft Cloud Manager stack, select the compartment to install the instance.
Review the Oracle terms, and then select the option indicating that you have reviewed and understand the conditions.
Click Launch Stack. 

![](./images/launch.png "")

4. On the Create Stack, Stack Information page, enter a stack name and description if desired.

Click Next

![](./images/psftname.png "")

Continue with the steps in Enter Cloud Manager Instance Values.

## Part 5. Enter Cloud Manager Instance Values

The Create Stack, Configure Variables page includes a list of the parameters needed to create and configure the Cloud Manager instance.

1. In the Cloud Manager Instance section, select the **Availability Domain as US-ASHBURN-AD-1**. 

2. For **Shape, select VM.Standard2.2**. 

3. Select the **storage volume size in GBs** for the secondary block volume for the Cloud Manager instance. We will set it as **200 GBs**.

4. For SSH public key, enter content of your **id_rsa.pub** key (the one you created with the script) in a single line, with no line feeds or spaces.

5. Enter your User OCID in a single line, with no line feeds or spaces.

6. For API private key, enter the contents of your **api_key** file. 
Below table summarizes the inputs in Configure Variables page.  

7. Leave API Private passphrase as blank (Enter if you have created one).

![](./images/values1.png "")

8. For **Tenancy Home Region**, Select the home region for your tenancy from the drop-down list.

9. Enter following value:

Attribute | Value
--------- | -----
DB CONNECT PASSWORD	| Passw0rd
ACCESS PASSWORD | Passw0rd
DB ADMIN PASSWORD | Passw0rd#
CLOUD MANAGER ADMINISTRATOR PASSWORD | Passw0rd
INTEGRATION GATEWAY USER PASSWORD | Passw0rd
WEBLOGIC ADMINISTRATOR USER PASSWORD | Passw0rd
WEB PROFILE USER PASSWORD | Passw0rd
DOMAIN CONNECT PASSWORD | Passw0rd123

![](./images/values2.png "")

![](./images/values3.png "")

10. In the Networking section, enter a host name for the Cloud Manager instance.
This name will be used as part of the URL you use to access Cloud Manager in a browser.

11. Clear the option Create Network Resources.

12. From the Network Compartment drop-down list, select **Demo**.

13. From the Existing Network drop-down list, select **OCIHOLVCN**.

14. From the Existing Subnet for Cloud Manager drop-down list, select **Public Subnet-OCIHOLVCN (Regional)**

15. Clear the option for **Create a Jump Host**

![](./images/networkvalues.png "")

16. Click Next. Review the configuration variables, and then click Create.  

![](./images/review.png "")

17.	This will add a new stack and open the stack details page. You can navigate to Variables to see all the assigned variables.

![](./images/variablestack.png "")

18. Click on **Terraform Actions** -> **Plan**.

![](./images/plan.png "")

19. Give plan name as **plan-job-1** and click on **Plan**

![](./images/plandetail.png "")

20. After plan is succeeded, click on **Terraform Actions** -> **Apply**.

![](./images/plans.png "")

![](./images/apply.png "")

21. Give apply name as **apply-job-1** and click on **Apply**.

![](./images/applydetail.png "")


Terraform Apply job is a long running process.  After it completes, the output from this job will have the IP address and PIA URL of CM instance.  To obtain those details, click on the Job name. 

![](./images/12.png "")

On the job details page, click on **Logs** under Resources. 

Make a note of CM\_public\_ip and CM\_http\_url.

12.	Windows: Add an entry to C:\Windows\System32\drivers\etc\hosts entry on your laptop/workstation as shown below. Use the hostname value for attribute CM\_http\_url. 

	I.	Open Windows Search “Notepad”. Right Click on Notepad and open as Administrator.

	![](./images/14.png "")

	II.	Go to File -> Open -> C:\Windows\System32\drivers\etc\hosts, and append below entry

	```
	129.213.145.213  labcm.cm.labnet.oraclevcn.com
	```
12.	Mac: Add an entry to /private/etc/hosts entry on your laptop/workstation. Use the hostname value for attribute CM\_http\_url. 

	I.	Open Terminal and type **sudo /private/etc/hosts**
	Add following with your CM HTTPS URL
	```
	129.213.145.213  labcm.cm.labnet.oraclevcn.com (This will change as per your IP address and URL)
	```
	![](./images/host.png "")

## Part 3. Accessing Cloud Manager using SSH

SSH key pair required to access Cloud Manager instance was created in step 6 in Part 1 of Lab 200. 

1.	Launch terminal or Git Bash and navigate to the keys folder. 

2.	Retrieve the Cloud Manager IP address.  It was provided as output when the stack was applied.

![](./images/16.png "")

3.	Navigate to the folder where you have created the keys. SSH into the Cloud Manager instance using below command. 

```
$ ssh -i id_rsa opc@129.213.145.213 //Use your IP
```

## Part 4. Monitoring Cloud Manager

1. SSH into Cloud Manager instance to check status of deployment.  Monitor Cloud Manager bootstrap installation using below command.

```
$ tail -f /home/opc/bootstrap/CloudManagerStatus.log
```

![](./images/18.png "")

2. While Cloud Manager is being installed, review Associated Resources for the list of all resources created by automation.

The deployment automation (Resource Manager Stack) provisions numerous resources in the tenancy.  To find the list of resources that were created, navigate to OCI console -> Resource Manager -> Stacks -> <Stack> -> Apply Job details.  On this page, click Associated Resources under Resources.  

![](./images/19.png "")

3. After Cloud Manager bootstrap is complete, the CloudManagerStatus.log will show the following messages. 

		The PeopleSoft Environment Setup Process Ended.
		CM installed successfully
		Cloud Manager PIA URL: http://labcm.cm.labnet.oraclevcn.com:8000 
		Cloud Manager PIA SSL URL: https://labcm.cm.labnet.oraclevcn.com:8443

## Part 5. Access Cloud Manager

1. Launch a browser to access your Cloud Manager PIA URL (CM\_http\_url) –  http://labcm.cm.labnet.oraclevcn.com:8000

2. To login, use the username CLADM and password as Passw0rd.

























