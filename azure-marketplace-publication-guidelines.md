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

**Add an offer**

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

When preparing the OS VHD, make sure the latest [Azure Linux Agent](http://azure.microsoft.com/en-us/documentation/articles/virtual-machines-linux-agent-user-guide/) is installed, using the RPM or Deb package. The agent provides key functions for deploying Linux IaaS deployment in Azure, such as image provisioning and networking capabilities. 

While the agent can be configured in a variety of ways, we recommend that you use a generic agent configuration to maximize compatibility. While it is possible to install the Agent manually, it is strongly recommended that you use the preconfigured installer packages.

If you do choose to install the agent manually from the [GitHub repository](https://github.com/Azure/WALinuxAgent), first copy the ‘waagent’ file to /usr/sbin and run the following commands as root: 
```
# chmod 755 /usr/sbin/waagent
# /usr/sbin/waagent –install
```
The agent configuration file will be placed at /etc/waagent.conf. 

**Verify that required libraries are included**

In addition to the Azure Linux Agent, the following libraries should also be included:
3.	[Linux Integration Services](http://www.microsoft.com/en-us/download/details.aspx?id=41554) Version 3.0 or higher
4.	Kernel Patch for Azure I/O stability (likely not needed for any recent kernel, but should be verified)
5.	[Python](https://www.python.org/) 2.5 or above (Python 2.6+ is highly recommended)
6.	Python pyasn1 package, if not already installed
7.	[OpenSSL](https://www.openssl.org/) v 1.0 or greater

**Set up disk partitions**

We recommend not using Logical Volume Manager. Create a single root partition for the OS disk. Do not use a swap partition on the OS or data disk. We do recommend removing a SWAP partition, even if is not mounted in /etc/fstab. If needed, a swap partition can be created on the local resource disk by the Linux Agent. 

**Add required Kernel Boot Line parameters**

The following parameters also need to be added to the Kernel Boot Line: 
```
console=ttyS0 earlyprintk=ttyS0 rootdelay=300 
```
This ensures that Azure Support can provide customers with serial console output when needed. It also provides adequate timeout for OS disk mounting from cloud storage. Even if your SKU blocks end customers from directly SSHing into the virtual machine, serial console output must be enabled.

**Include SSH Server by Default**

We strongly recommend enabling SSH for the end user.  If SSH Server is enabled, add the SSH keep alive to sshd config with the following option: ClientAliveInterval 180.  While 180 is recommended, the acceptable range is 30 to 235.  Not all applications desire allowing direct SSH to the virtual machine for the end user.  If SSH is explicitly blocked, the ClientAliveInterval does not need to be set.

**Meet networking requirements**

The following are networking requirements for an Azure-compatible Linux VM Image.
- Network Manager must not be installed, since it conflicts with the Azure Linux Agent. The Agent will not install if it detects the network manager package. 
- Networking configuration should use the ifcfg-eth0 file and should be controllable via the ifup/ifdown scripts.
- There should be no custom network configuration. You need to delete the resolv.conf file. This will be done as part of deprovisioning. You can also perform this step manually with the following command: 
```
rm /etc/resolv.conf
```
- The network device needs to be brought up on boot and use DHCP.
- IPv6 is not supported on Azure.  If this property is enabled, it will not work.  

**Ensure security best practices are in place**

It is critical for SKUs in the Azure Store to follow best practices in regards to security. These include the following. 
- Install all security patches for your distribution. 
- Follow distribution security guidelines. 
- Avoid creating default accounts, which remain the same, across provisioning instances. 
- Clear bash history entries 
- Include iptables (firewall) software, but do not enable any rules. This will provide a seamless default experience for customers. Customers who want to use a VM firewall for additional configuration can configure the iptables rules to meet their specific needs. 

**Generalize the image**

All images in the Azure Store must be re-usable in a generic fashion, which requires stripping them of certain configuration specifics. To accomplish this in Linux, the OS VHD must be ‘deprovisioned’.

The Linux command for deprovisioning is as follows: 
```
#waagent –deprovision
```
This command automatically performs the following actions:
- Removes the nameserver configuration in /etc/resolv.conf 
- Removes cached DHCP client leases 
- Resets host name to localhost.localdomain 

We recommend setting the configuration file to ensure the following actions are also completed: 
- Set Provisioning.RegenerateSshHostKeyPair to 'y' in the configuration file to remove all SSH host keys
- Set Provisioning.DeleteRootPassword to 'y' in the configuration file to remove the ‘root’ password from /etc/shadow

## 3.3 Create an Azure-compatible VHD (Windows-based)
The following section focuses on the steps to create a SKU based on Windows Server for the Microsoft Azure Store.

**Ensure you are using the correct base VHDs**

The OS VHD for your VM Image must be based on a Microsoft Azure-approved base image, containing Windows Server or SQL Server. 

To begin, create a VM from one of the following images, located at the Microsoft Azure Portal (portal.azure.com):

- Windows Server [2012 R2 Datacenter](http://go.microsoft.com/fwlink/?LinkID=511809&clcid=0x409), [2012 Datacenter](http://go.microsoft.com/fwlink/?LinkID=511808&clcid=0x409), [2008 R2 SP1](http://go.microsoft.com/fwlink/?LinkID=511806&clcid=0x409)
- SQL Server 2014 [Enterprise](http://go.microsoft.com/fwlink/?LinkID=511810&clcid=0x409), [Standard](http://go.microsoft.com/fwlink/?LinkID=511817&clcid=0x409), [Web](http://go.microsoft.com/fwlink/?LinkID=511818&clcid=0x409)
- SQL Server 2012 SP2 [Enterprise](http://go.microsoft.com/fwlink/?LinkID=511812&clcid=0x409), [Standard](http://go.microsoft.com/fwlink/?LinkID=511815&clcid=0x409), [Web](http://go.microsoft.com/fwlink/?LinkID=511816&clcid=0x409) 
- SQL Server 2008 R2 SP2 [Enterprise](http://go.microsoft.com/fwlink/?LinkID=511819&clcid=0x409), [Standard](http://go.microsoft.com/fwlink/?LinkID=511820&clcid=0x409), [Web](http://go.microsoft.com/fwlink/?LinkID=511821&clcid=0x409) 

These links can also be found in the Publishing Portal under the SKU page. 

Note: if you are using the current Azure Management Portal or PowerShell, Windows Server Images published on September 8, 2014 and later are approved. 

**Create your Windows VM**

From the Microsoft Azure Portal, you can create your VM based on an approved base image in just a few simple steps. The following is an overview of the process. 

1.	From the base image page, select Create VM to be directed to the new [Microsoft Azure Portal](https://portal.azure.com).
2.	Log in to the portal with the Microsoft account and password for the Azure subscription you wish to use.
3.	Follow the prompts to create a VM using the base image you have selected. At the very least, you will need to provide a host name (name of the computer), username (admin user registered), and password for the VM.
4.	Select the size of the VM to deploy.
- If you plan to develop the VHD on premises, the size does not matter. Consider using one of the smaller VMs. 
- If you plan to develop the image in Azure, consider using one of the recommended VM sizes for the selected image. 
- For pricing information, refer to the Recommended Pricing Tier selector displayed on the portal. It will provide the three recommended sizes provided by the publisher. (In this case, the publisher is Microsoft.)
5.	Set properties. 
- For quick deployment, you can leave the default values for the properties under Optional Configuration and Resource Group. 
- If desired, under Storage Account, you can select the storage account in which the OS VHD will be stored. 
- If desired, under Resource Group, you can select the logical group in which to place the VM. 
6.	Select the Location to which to deploy. 
- If you plan to develop the VHD on premises, the location does not matter as you will be uploading the image to Azure later. 
- If you plan to develop the image in Azure, consider using one of the US-based Microsoft Azure regions from the beginning. This will speed up the VHD copying process that Microsoft performs on your behalf when you submit your image for certification. 
7.	Click Create. The VM will begin deploying. Within minutes, you will have a successful deployment and can begin to create the image for your SKU.

**Develop your VHD in the cloud**

It is strongly recommended that you develop your VHD in the cloud using Remote Desktop Protocol (RDP). You will connect to RDP with the username and password specified during provisioning. 

Note: if you are developing your VHD on-premises (which is not recommended) see Appendix 2 for instructions on how to download the VHD to a local system. Downloading your VHD is NOT necessary if you are developing in the cloud. 

**Connect via RDP using the Microsoft Azure Portal**

1.	Select Browse and then VMs. 
2.	The VMs blade will open. Ensure the VM you want to connect with is running and select it from the list of deployed VMs. 
3.	A blade opens describing the selected VM. At the top, click Connect.
4.	You will be prompted to enter the username and password you specified at time of provisioning. 

**Connect via RDP using PowerShell**

To download a remote desktop file to a local machine, use the [Get-AzureRemoteDesktopFile cmdlet](http://msdn.microsoft.com/en-us/library/dn495261.aspx). In order to use this cmdlet, you will need to know the name of the service and name of the VM. If you created the VM from the [Microsoft Azure Portal](https://portal.azure.com), you can find this information under VM Properties.
1.	In the Microsoft Azure Portal, Select Browse and then VMs.
2.	The Virtual Machines blade will open. Select the VM that you deployed from the list of VMs.
3.	A blade opens describing the selected VM.
4.	Click Properties.
5.	The first portion of the domain name is the service name. The host name is the VM name.
6.	The cmdlet to download the RDP file for the created VM to the Administrator’s local desktop is as follows:
```
Get-AzureRemoteDesktopFile -ServiceName “baseimagevm-6820cq00” -Name “BaseImageVM” –LocalPath “C:\Users\Administrator\Desktop\BaseImageVM.rdp”
```
More information about RDP can be found on MSDN in the article [Connect to an Azure VM with RDP or SSH](http://msdn.microsoft.com/library/azure/dn535788.aspx).

**Configure a VM and create your SKU**

Once the OS VHD is downloaded, use Hyper-V and configure a VM to begin creating your SKU. Detailed steps can be found at the following TechNet link: [Install Hyper-V and Configure a VM.](http://technet.microsoft.com/en-us/library/hh846766.aspx)


**Choose the correct VHD size**

The Windows OS VHD in your VM Image should be created as a 128 GB fixed format VHD.  If the physical size is less than 128GB, the VHD should be sparse. The base Windows and SQL Server images provided already meet these requirements; do not change the format or the size of the VHD obtained. 

Data disks can be as large as 1TB. When deciding on the disk size, remember that end users cannot resize VHDs within an image at time of deployment. Data disk VHDs should be created as a fixed format VHD, but also be sparse. Data disks can be empty or contain data.

**Install the latest Windows patches**

The base images contain the latest patches up to their published date. Before publishing the OS VHD you have created, ensure that Windows Update has been run and that all the latest ‘Critical’ and ‘Important’ security patches have been installed. 

**Perform additional configuration and schedule tasks as necessary**

If additional configuration is needed, consider using a scheduled task that runs at startup to make any final changes to the VM once it has been deployed.
- It is a best practice to have the task delete itself upon successful execution.
- No configuration should rely on drives other than C:\ or D:\, since these are the only two drives that are always guaranteed to exist. C:\ is the OS disk and D:\ is the temporary local disk. 

**Generalize the image**

All images in the Azure Store must be re-usable in a generic fashion. In other words, the OS VHD must be generalized. 
- For Windows, the image should be “sysprepped” and no configurations should be done that do not support the `sysprep` command. 
- You can run the command `sysprep.exe /generalize /oobe /shutdown` from the directory `%windir%\System32\Sysprep`. Guidance on how to sysprep the operating system is provided in Step 1 of the following MSDN article - Create and upload a Windows Server VHD to Azure.

## 3.4 Deploy a VM from your VHDs
Once your VHD(s), generalized OS VHD and zero or more data disk VHDs, are uploaded to an Azure storage account, you can register them as a user VM Image with which to test. Note, since your OS VHD is generalized, you cannot directly deploy the VM by providing the VHD URL.

To learn more about VM Images review the following blog posts: [VM Image](http://azure.microsoft.com/blog/2014/04/14/vm-image-blog-post/),[VM Image PowerShell How To](http://azure.microsoft.com/blog/2014/05/01/vm-image-powershell-how-to-blog-post/), and [About VM Images in Azure](http://msdn.microsoft.com/en-us/library/azure/dn790290.aspx). 

**Create a User VM Image**

To create a user VM Image from your SKU to begin deploying multiple VMs, you need to use the Create VM Image Rest API to register VHDs as a VM Image.

You can use the Invoke-WebRequest cmdlet to create a VM Image from PowerShell. The below PowerShell script shows how to create a VM Image with an OS disk and one data disk. Note, the PowerShell session should already be set up and a subscription set.
```
# Image Parameters to Specify
$ImageName=’myVMImage’
$Label='IMAGE_LABEL'
$Description='My VM Image to Test’
$osCaching='ReadWrite'
$os = 'Windows'
$state = 'Generalized'
$osMediaLink = 'http://mystorageaccount.blob.core.windows.net/vhds/myOSvhd.vhd'
$dataCaching='None'
$lun='1'
$dataMediaLink='http://mystorageaccount.blob.core.windows.net/vhds/mydatavhd.vhd'

# Subscription Related Properties
$SrvMngtEndPoint='https://management.core.windows.net'
$subscription = Get-AzureSubscription -Current -ExtendedDetails
$certificate = $subscription.Certificate
$SubId = $subscription.SubscriptionId


$body = 
"<VMImage xmlns=`"http://schemas.microsoft.com/windowsazure`" xmlns:i=`"http://www.w3.org/2001/XMLSchema-instance`">" +
    "<Name>" + $ImageName + "</Name>" +    
    "<Label>" + $Label + "</Label>" +
    "<Description>" + $Description + "</Description>" +
    "<OSDiskConfiguration>" +
      "<HostCaching>" + $osCaching + "</HostCaching>" +
      "<OSState>" + $state + "</OSState>" +
      "<OS>" + $os + "</OS>" +
      "<MediaLink>" + $osMediaLink + "</MediaLink>" +
    "</OSDiskConfiguration>" +
    "<DataDiskConfigurations>" + 
         "<DataDiskConfiguration>" +
            "<HostCaching>" + $dataCaching + "</HostCaching>" +
            "<Lun>" + $lun + "</Lun>" +
            "<MediaLink>" + $dataMediaLink + "</MediaLink>" +
         "</DataDiskConfiguration>" +
    "</DataDiskConfigurations>" + 
"</VMImage>"
```

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

