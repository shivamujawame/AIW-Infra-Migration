## HOL3: Exercise 2: Configure ASR for on-premises infrastructure

In this exercise, you will deploy disaster recovery of on-premises Hyper-V VM to Azure. The Azure Site Recovery service contributes to your disaster-recovery strategy by managing and orchestrating replication, failover, and failback of on-premises machines. As part of the registration process, you will deploy the Azure Site Recovery Provider on your Hyper-V host.

### Task 1: Configure ASR to on-premises infrastructure

1. In the **search resources, services and docs bar**, type **Recovery services vaults** and select it from suggestions, as shown below:
   
    ![Screenshot of the search Recovery service vaults.](Images/upd-search-asr.png "Recovery service vaults")
    
1. Under Recovery services vaults, click on **SmartHotelMigration<inject key="DeploymentID" enableCopy="false" />-MigrateVault-_xxxx_** which we have configured in the previous HOL1 task.  

    ![Screenshot of the create Recovery service vaults.](Images/hol3-e2-s2.png "create Recovery service vaults")

1. Select **Site Recovery Infrastructure** under **Manage** on the left side of the panel.

    ![Screenshot of the Site Recovery Infrastructure.](Images/hol3-e2-s3.png)

1. Under Site Recovery Infrastructure page, select **Hyper-V hosts (1)** and then make sure that the status of the server is **Connected (2)**.

    ![Screenshot of the hyper-v-host.](Images/hol3-e2-s4.png "hyper-v-host")  

1. Go back to your **Recovery service vault page**, click on **Replicated Items (1)** under **Protected Items** and then click on **+Replicate (2)** and select **Hyper-V machines to Azure (3)** from the drop-down list.

    ![Screenshot of the add replicate items.](Images/hol3-e2-s5.png "add replicate items") 
   
1. Under **Source environment** tab, select the **SmartHotelMigration<inject key="DeploymentID" enableCopy="false" />-HyperVSite (1)**  and then click on **Next (2)**.
 
    ![Screenshot of the Source environment.](Images/hol3-e2-s6.png "Source environment") 
   
1. Under **Target environment** tab, fill the following details:

   - Post-failover resource group: **SmartHotelRG (1)**
   
   - Storage account: **select the one available in the drop-down list (2)**  
   
   - Virtual network: **SmartHotelVNet (3)**

   - Subnet: **SmartHotel (4)**
   
   - Leave other values as default and click on **Next (5)**
   
    ![Screenshot of the target environment.](Images/hol3-e2-s7.png "Source environment")    
    
1. Under **Virtual machine selection** tab, **check for AzureArcVM (1)** and click on **Next (2)**.

    ![Screenshot of the vm selection.](Images/hol3-e2-s8.png "vm selection")

1. Under **Replication settings** tab, select **Windows (1)** as OS type for AzureArcVM and then click on **Next (2)**.

    ![Screenshot of the Replication settings.](Images/hol3-e2-s9.png "Replication settings")
     
1. Under **Replication policy** tab, select **defaultSmartHotelMigration<inject key="DeploymentID" enableCopy="false" />-HyperVSite-policy (1)** from the drop-down and click on **Next (2)**.  

    ![Screenshot of the Replication settings.](Images/hol3-e2-s10.png "Replication settings")
   
1. Under **Review** tab, click on **Enable Replication**.

1. The process of replication might take 15-20 minutes to get completed. Once the Replication is successfully completed, the status of the replicated AzureArcVM will now become **Protected (2)**.

   > **Note:** You might have to refresh **(1)** a couple of times.

    ![Screenshot of the status-protected.](Images/hol3-e2-s13.png "status-protected")
   
**Summary:** In this exercise, you explored on how to set up Azure and on-premises prerequisites and create a Recovery Services vault for Site Recovery. Then you see how to set up the source and target replication environments and create a replication policy so that at the end you can enable replication for a server.

