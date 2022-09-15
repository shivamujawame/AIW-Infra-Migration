### HOL3: Exercise 2: Configure ASR for on-premises infrastructure


### Task 1: Create a storage account

1. If you are not logged in already, click on Azure portal shortcut that is available on the desktop and log in with below Azure credentials.
    * Azure Username/Email: <inject key="AzureAdUserEmail"></inject> 
    * Azure Password: <inject key="AzureAdUserPassword"></inject>

1. Click on **Show Portal Menu (1)** bar and select **All services (2)** in the portal's left navigation.
 
    ![Screenshot of the All services overview blade.](Images/Allservices.png)
    
1. Click on **+Create a resource** and then search for **storage account** and click **Create**.   
    
    ![Screenshot of the search storage account.](Images/upd-create-storage-1.png "search storage account")
    
1. Under **Create a storage account** tab, fill the following details and click **Create**:
     
   - Subscription: **Select your subscription (1)**
    
   - Resource group: **SmartHotelRG (2)**
   
   - Storage account name: **storage<inject key="DeploymentID" enableCopy="false" /> (3)**
  
   - Region: **Same as your resource group (4)**
   
   - Leave other values as default and Click **Review (5)**    
    
     ![Screenshot of the storage account.](Images/storage.png "create storage account")
     
1.  Go to the storage account that you created and select **Data Protection (1)** under **Data Management**.

1.  Make sure to uncheck **Enable soft delete for blobs (2)** and **Enable soft delete for containers (3)** and then click **Save (4)**.  

     ![Screenshot of the data protection.](Images/dataprotection.png "data protection")


### Task 2: Configure ASR to on-premise infrastructure

1. In the **search resources, services and docs bar**, type **Recovery service vaults** and select it from suggestions, as shown below:
   
    ![Screenshot of the search Recovery service vaults.](Images/search-asr.png "Recovery service vaults")
    
1. Under Recovery service vaults, click **+Create**.  

    ![Screenshot of the create Recovery service vaults.](Images/create-asr1.png "create Recovery service vaults")
    
1. Under **Basics tab** of create a recovery service vault, fill the following details and ckick **Create**: 

   - Subscription: **Select your subscription (1)**
    
   - Resource group: **SmartHotelRG (2)**
   
   - Vault name: **asrvault-<inject key="DeploymentID" enableCopy="false" /> (3)**
  
   - Region: **Same as your resource group (4)**
   
   - Leave other values as default and Click **Review+Create (5)**  
  
    ![Screenshot of the create Recovery service vaults basics tab.](Images/create-asr2.png "create Recovery service vaults basics")
    
1. On the **Overview page** of recovery service vault that you created, select **+Enable Site Recovery**.

    ![Screenshot of the Enable Site Recovery.](Images/siterecovery.png "Enable Site Recovery")   
    
1. Under Site Recovery page, select **Prepare Infrastructure** under **Hyper-V machines to Azure**.
    
    ![Screenshot of the prepare infrastructure.](Images/prepare-infra-1.png "prepare infrastructure")  

1. Under **Deployment planning** tab, for Deployment planning completed?: select **I will do it later** from the drop down arrow list.
  
    ![Screenshot of the Deployment planning tab.](Images/prepare-infra-2.png "Deployment planning tab")  
    
1. Under **Source settings** tab, fill the following details:   
   
   - Are you using system Centre VMM to manage Hyper-V hosts?: **No (1)**
   
   - In Hyper-V site, click **Add Hyper-V site (2)** and then under Create Hyper-V site, enter **Hyper-v-site-<inject key="DeploymentID" enableCopy="false" /> (3)** as name and click **Ok (4)**.

    ![Screenshot of the Source setting tab.](Images/prepare-infra-3.png "Source setting tab")  
 
1. After successfully adding the Hyper–V site, click **Add Hyper-V servers**. 

   ![Screenshot of the Add Hyper-V server.](Images/prepare-infra-4.png "Add Hyper-V server")  
   
1. Under Add Server page, Click on the **Download** the installer for the Microsoft Azure Site Recovery provider.  
    
   ![Screenshot of the download installer.](Images/prepare-infra-5.png "download installer")
 
1. Under Add Server page, select the **blue Download button (1)** and download the registration key file and then close the **Add server** panel using **X (2)** button.

    ![Screenshot of the download key.](Images/prepare-infra-6.png "download key")
    
1. Open the **AzureSiteRecoveryProvider.exe** installer you downloaded a moment ago. On the **Microsoft Update** tab, select **Off** and select **Next**. Accept the default installation location and select **Install**.

   ![Screenshot of the ASR provider installer.](Images/asr-provider-installer.png "Azure Site Recovery Provider Setup") 
   
1. When the installation has completed select **Register**. Browse to the location of the key file you downloaded. When the key is loaded select **Next**.

   ![Screenshot of the ASR provider registration settings.](Images/upd-asr-registration.png "Key file registration")
   
1. Select **Connect directly to Azure Site Recovery without a proxy server** and select **Next**. The registration of the Hyper-V host with Azure Site Recovery will begin.

   ![Screenshot of the ASR provider registration settings.](Images/upd-e3-t2-s8.png)
   
1. Wait for registration to complete (this may take several minutes). Then select **Finish**.

   ![Screenshot of the ASR provider showing successful registration.](Images/upd-asr-registered.png "Registration complete")

1. Return to your Recovery service vault overview page in the Azure Portal, and select **Site Recovery Infrastructure** under **Manage** on the left side of the panel.

   ![Screenshot of the Site Recovery Infrastructure.](Images/Site Recovery Infrastructure.png)


   
   
 
