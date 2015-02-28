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
In order to complete the publishing process, you will need to create a Microsoft account. This account will be used to log in to both the Publishing Portal and the Seller Dashboard. You should only have one Microsoft Account for your Azure Marketplace offerings. They should not be specific to individual VMs. 

The address that forms the user name should be on your domain and controlled by your IT team (such as azurepublishing@yourcompany.com). Payment, tax information, and reporting will be routed through this account. 

1.	Within your own domain, create a Distribution List (DL) or Security Group with an email address such as azurepublishing@yourcompany.com
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
Creating your Seller Dashboard account is a one-time task. You should check to make sure your company does not already have a Seller Dashboard account before attempting to create one. During the process, we will collect bank account information, tax information, and company address information. These are typically obtainable from finance or business contacts. For complete instructions on how to create a Seller Dashboard account, see [Create Your Account and Add Payout Information in the Microsoft Seller Dashboard] (http://msdn.microsoft.com/en-us/library/jj552460.aspx)

1.	From the Publishing Portal, click the link that says “seller profile.” 
2.	Complete the “Help us protect your account” wizard, which will verify your identity via phone number or email address. 
3.	Go to Account Details. On this screen, you will enter your PERSONAL information, which is only used for identity verification. That means your name, email address, residential address, and personal phone number. This information is not shared with anyone outside of Microsoft. 
4.	Designate your account type as Company, NOT Individual. Click Next. 
5.	Fill out the Company Details. This is the marketing profile for your company. When it is complete, click Submit for approval. 
6.	You must provide payout and tax information and submit it for validation. In order to add payout and tax information, go to Account > Payout & Tax and click Add. Enter your company’s information. You will be required to provide a Tax Identification Number and other tax information matching the country in which your business is headquartered.

You can monitor the status of your approvals via the Azure Publishing Portal. 

## Step 3: Provide technical artifacts for your offer

- [Instructions for publishing a Virtual Machine Image](http://azure.microsoft.com/en-us/documentation/articles/azure-marketplace-publication-guidelines-vm-image/)
- [Instructions for publishing a Virtual Machine Extension](http://azure.microsoft.com/blog/2014/04/11/vm-agent-and-extensions-part-1/)
- [Instructions for publishing a Application Service](https://github.com/Azure/azure-resource-provider-sdk)
- [Instructions for publishing a Data Service](https://datamarket.azure.com/about)
- [Instructions for publishing a Web Application](http://www.iis.net/learn/publish)


#Step 4: Getting to staging
In this step, you will provide the content, pricing, and other information necessary to push your offer to staging. 

##4.1 Provide Azure Marketplace content 
English is the default and only supported language; please ensure that all information provided in the fields is in English. All information can be edited at any time until you push to staging.

1.	Enter the offer summary, long summary, and description for your offer. 
2.	Upload images of the required specifications (provided by the tool), one for each size.
3.	All fields must have entries, including the images, in order to be able to push to staging.
4.	In the links tab on the left bar, enter any links with information that may help customers. Enter a name and URL for each link.
5.	In the Legal tab, provide a link to your policies/terms of use. Enter or paste the terms in the large Terms of Use box.

##4.2 Set your prices

1.	Under pricing, you will see all of the supported markets. Select the appropriate one to bring up the pricing fields.
2.	The provided link will show pricing information to help you in determining the prices of your SKU(s). Note that if your SKU is Bring Your Own License (BYOL), you must put 0s in all fields.
3.	Enter your base prices for your hourly SKU (if applicable), and click Accept.
4.	A pricing wizard will open; proceed through this to complete your pricing, including pricing for other countries, if you choose to allow purchases from outside your specified market. Exchange rates are current, but are not calculated hourly, and become static upon selection. Conversion is not performed automatically once prices are accepted. 
5.	Some countries are ISV Remit countries. To sell in an ISV Remit country, you must be able to charging and collecting tax on your SKUs, and calculating and paying tax to the government of the country. Microsoft is not in a position to provide legal or tax guidance. 
6.	Add Tax Remittance information. 

##4.3 Provide support information
Some of this information will have been completed during the certification step. You may add or edit information as in the steps below. Customers will not see this data. It is used for internal communications between you and Microsoft only.

1.	Go to the Support heading on the left side of the Publishing Portal.
2.	Enter information under Engineering Contact. 
3.	Enter information under Customer Support. If you only provide email support, enter a dummy phone number, and your provided email will be used instead.

##4.4 Choose Azure Marketplace categories 
In the categories tab, there will be an array of selections provided. Your offer may fall under these, and you may select up to five (5) categories.

##4.5 Try out your offer in staging
Staging means deploying your SKU in a private “sandbox” where you can test and verify its functionality before publishing it. 

1.	Click Push to Staging in the Publish tab.
2.	Correct any errors or discrepancies of which the service may notify you at this point.
3.	Provide the information about the Azure subscription(s) you will use to preview your offer.
4.	Your offer will remain in staging until you notify Microsoft that you are ready to push to production. This is an ideal time to have all members of the team check over everything in preparation for your offer going live.

##Step 5: Publish
When you are satisfied that everything is correct and you are ready to go live, request Push to Production. 

