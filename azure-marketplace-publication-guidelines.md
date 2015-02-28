# Microsoft Azure Marketplace Publication Guidelines
This document describes the steps that a publisher must follow to publish an offer to the Microsoft Azure Marketplace.

## Step 1: Approval to Publish an Offer
As a provider of software applications or services, you must be given approval to publish to the Azure Marketplace. The approval process reviews a publisher's attainment of the business and technical requirements to be integrated into the Azure Marketplace. 
- Business Requirements: refer to the Azure Marketplace Participation Policies
- Technical requirements: refer to details for each of the integration types described below

### 1.1 Where to apply
Publishers must first apply via the Request Information link on http://azure.com/certified

## Step 2: Publisher Contact & Seller Registration 

### 2.1 Create Microsoft Account
In order to complete the publishing process, you will need to create a Microsoft account. This account will be used to log in to both the Publishing Portal and the Seller Dashboard. You should only have one Microsoft Account for your Azure Store offerings. They should not be specific to individual VMs. 

The address that forms the user name should be on your domain and controlled by your IT team (such as azurepublishing@yourcompany.com). Payment, tax information, and reporting will be routed through this account. 

1.	Within your own domain, create a Distribution List (DL) or Security Group with an email address such as AzureStore@yourcompany.com
2.	Add your Azure VM publishing team to the DL. The DL must be live to receive the confirmation email necessary to create your account. 
3.	Register for a Microsoft Account using Distribution List Email using the DL email. You can register for a Microsoft Account at https://signup.live.com/signup.aspx
4.	When registering, use a valid phone number. The system will send a send verification code as a text message or an automated call if identity verification is required.
5.	Respond to the verification email sent to the Azure VM publishing DL. 

### 2.2 Register in the Publishing Portal
1.	Go to http://publish.windowsazure.com and create an account using the Microsoft Account you created in step 2.1. 
2.	Read and agree to the terms of the publishing portal. 
3.	Click “I want to publish for the Virtual Machine Marketplace…”
4.	At this point, do not continue working in the Azure Publishing Portal

### 2.3 Create your Seller Dashboard account
Creating your Seller Dashboard account is a one-time task. You should check to make sure your company does not already have a Seller Dashboard account before attempting to create one. During the process, we will collect bank account information, tax information, and company address information. These are typically obtainable from finance or business contacts. For complete instructions on how to create a Seller Dashboard account, see “Create Your Account and Add Payout Information in the Microsoft Seller Dashboard” (http://msdn.microsoft.com/en-us/library/jj552460.aspx)

1.	From the Publishing Portal, click the link that says “seller profile.” 
2.	Complete the “Help us protect your account” wizard, which will verify your identity via phone number or email address. 
3.	Go to Account Details. On this screen, you will enter your PERSONAL information, which is only used for identity verification. That means your name, email address, residential address, and personal phone number. This information is not shared with anyone outside of Microsoft. 
4.	Designate your account type as Company, NOT Individual. Click Next. 
5.	Fill out the Company Details. This is the marketing profile for your company. When it is complete, click Submit for approval. 
6.	If you want to offer apps for purchase, you also need to add payout and tax information and submit it for validation. If you are only offering free apps, then you do not need to add this information. You can add it later, but it takes some time to validate the tax information. If you know that you will offer apps for purchase, we recommend that you add and submit it as soon as possible. In order to add payout and tax information, go to Account > Payout & Tax and click Add. Enter your company’s information. You will be required to provide a Tax Identification Number and other tax information matching the country in which your business is headquartered.

You can monitor the status of your approvals via the Azure Publishing Portal. 

## Step 3: Create and certify your Azure-compatible VHD and Request Certification in the Publishing Portal

This section walks you through preparing your VHDs, which will are the foundation of your SKU you will publish into the Microsoft Azure Store. The process will differ depending on whether you are providing a Linux- or Windows-based SKU. This section covers both scenarios. This process can be performed in parallel with Step 2, above. 

A SKU is the commercial name for a VM Image. A VM Image contains one OS disk and zero or more data disks. It is essentially the complete storage profile for a virtual machine. One VHD is needed per disk; even blank data disks require a VHD to be created.

Regardless of which operating system you use, add only the minimum number of data disks needed by the SKU. The end user cannot remove disks that are part of an image at time of deployment, but can always add disks during or after deployment if they need them.

### 3.1 Define Offers and SKUs
In this section, you will define the Offers and the SKUs underneath them. An offer is a “parent” to all of its SKUs. You can have multiple offers. How you decide to structure your offers is up to you. When an offer is pushed to staging, it is pushed along with all of its SKUs. Carefully consider your SKU identifiers, as these will be visible in the URL.

**Add an offer **
1.	Log in to the Publishing Portal (publish.windowsazure.com) using your seller account.
2.	Enter the Virtual Machines tab of the Publishing Portal.In the prompted entry field, enter your offer name, and create.Under seller account, enter your namespace. 
3.	Add any other administrators you want to be able to work with the publishing portal.

**Define SKU**
Once you have added an offer, you will need to define/identify your SKU(s).
1.	Add a SKU. It will require an identifier, which will be used in the URL. This will need to be unique within your Publishing Profile, but there is no risk of identifier collision with other publishers.
2.	Add a summary description for your SKU. This will be read by humans in the UX, so it is advised to make it easily readable. This information does not need to be locked until “Push to Staging”. Until then, you are free to edit it. 
3.	If you are using Windows-based SKUs, follow the suggested links to acquire the approved versions of Windows Server.


### 3.2 Create an Azure-compatible VHDs (Linux-based)
The following section focuses on best practices for creating a Linux-based VM Image for the Microsoft Azure Store. For a step-by-step walkthrough, refer to the following documentation: [Creating and Uploading a Virtual Hard Disk that Contains the Linux Operating System.] (http://azure.microsoft.com/en-us/documentation/articles/virtual-machines-linux-create-upload-vhd/)

**Choose the correct VHD size**
Published SKUs (VM Images) should be designed to work with all VM sizes that support the number of disks for the SKU. You can provide guidance on recommended sizes, but these will be treated as recommendations and not enforced.

1.	Linux OS VHD: The Linux OS VHD in your VM Image should be created as a 30GB – 50GB fixed format VHD. It cannot be less than 30GB.  If the physical size is less than VHD size, the VHD should be sparse. Linux VHDs larger than 50GB will be considered on a case by case basis. If you already have a VHD in a different format, you can use the [Convert-VHD PowerShell cmdlet to change the format.] (http://technet.microsoft.com/en-us/library/hh848454.aspx)
2.	Data disk VHD: Data disks can be as large as 1TB. Data disk VHDs should be created as a fixed format VHD, but also be sparse. When deciding on the disk size, please keep in mind that end users cannot resize VHDs within an image. 

**Ensure the latest Azure Linux Agent is installed**
When preparing the OS VHD, make sure the latest Azure Linux Agent is installed, using the RPM or Deb package. The agent provides key functions for deploying Linux IaaS deployment in Azure, such as image provisioning and networking capabilities. 

While the agent can be configured in a variety of ways, we recommend that you use a generic agent configuration to maximize compatibility. While it is possible to install the Agent manually, it is strongly recommended that you use the preconfigured installer packages.

If you do choose to install the agent manually from the GitHub repository, first copy the ‘waagent’ file to /usr/sbin and run the following commands as root: 


Prepare technical artifacts for publication and complete certification tests (Artifact type specific)
Virtual Machine Image
Required artifacts
Certification tests
Virtual Machine Extension
Required artifacts
Certification tests
Application Service
Required artifacts
Certification tests
Data Service
Required artifacts
Certification tests

Offers, Pricing and Marketing Content (artifact type specific)
Virtual Machine image
Offers may contain multiple SKUs
One VM image is required per SKU
All SKUs must complete certification 
Virtual Machine Extension
Application Service
Data Service

Test in Staging and Request Approval for Production

