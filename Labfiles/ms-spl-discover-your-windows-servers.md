# Lab 01: Discover your Windows Server

### Estimated Duration: 60 minutes

In this Hands-on Lab, you will discover on-prem servers using use Azure Migrate Appliance. The Azure Migrate appliance is a tool provided by Microsoft to assist in the discovery and assessment of on-premises infrastructure for migration to Azure. It collects detailed information about servers, applications, databases, and workloads in your environment, including configuration, performance, and dependencies.

## Exercise: Discovery, Assess, and Plan: Evaluate your current environment

In this exercise, you will deploy the Azure Migrate appliance in the on-premises Hyper-V environment. This appliance communicates with the Hyper-V server to gather configuration and performance data about your on-premises VMs, and returns that data to your Azure Migrate project.

1. On the Azure portal click on **Show Portal Menu (1)** bar and select **All services (2)** in the portal's left navigation.
 
    ![Screenshot of the All services overview blade.](Images/DAA-image2.png "All services Overview blade")

1. In the search bar, search for **Azure Migrate** and select it from the suggestions to open the Azure Migrate Overview blade, as shown below. 
 
    ![Screenshot of the Azure migrate overview blade.](Images/DAA-image3.png "Azmigrate Overview blade")

1. On **Azure Migrate** blade, expand **Migration goals (1)** and select **Servers, databases and web apps (2)**. Click **Discover (3)** then from the drop down select **Using appliance (4)** to open the **Discover** blade.
 
    ![](Images/DAA-image5.png)
 
1. Under **Are your servers virtualized?**, select **Yes, with Hyper-V** from the **drop-down** menu.

    ![](Images/DAA-image4.png)

1.  In **1: Generate project key**, provide the below name for the **Azure Migrate appliance (1)** that you will set up for the discovery of Hyper-V VMs. Select **Generate key (2)** to start the creation of the required Azure resources.

     ```
     SmartHotelAppl
     ```
     ![](Images/DAA-image6.png)

1.  **Wait** for the key to be generated, then copy the **Azure Migrate project key** to your clipboard.

     ![](Images/DAA-image7.png)

1.  Read through the instructions on how to download, deploy and configure the Azure Migrate appliance, then close the 'Discover machines' blade by clicking on cross button **X** (do **not** download the .VHD file or .ZIP file, the .VHD has already been downloaded for you). 
 
    ![](Images/DAA-image8.png)

1. As we have created the Azure Migrate project key for the Discover and Assessment, you will be accessing the Hyper-V manager in the next tasks to start the discovery process with the help of Azure Migrate Appliance.

1. Now, to Connect to your on-premises environment, Go to **Start (1)** button in the VM, search for **Hyper-V Manager (2)** there and select it. You will be accessing your infrastructure from the hyper-V manager and will be connecting to the Azure Migrate Appliance VM to start the process of discovery.  

    > You can also open the **Hyper-V manager** by clicking on the ![](Images/Icon-hyperv.png) icon that is present in the taskbar. 

      ![](Images/DAA-image9.png)
    
1. In Hyper-V Manager, select **HOSTVMS<inject key="DeploymentID" enableCopy="false" /> (1)**. You should now see the AzureMigrateAppliance VM and seven VMs(2) that comprise the on-premises SmartHotel application and will be used in the next HOLs.

    ![](Images/DAA-image10.png)
     
1. In Hyper-V Manager, select the **AzureMigrateAppliance (1)** VM, then select **Start (2)** on the right if not already running.

    ![](Images/DAA-image11.png)
    
     > **Note**: If you get an error pop while starting the **AzureMigrateAppliance** VM try to **Turn off** the **AzureArcVM**, then start the **AzureMigrateAppliance** VM again.

1. In Hyper-V Manager, select the **AzureMigrateAppliance (1)** VM, then select **Connect (2)** on the right.

    ![](Images/DAA-image12.png)
    
1. Under Connect to AzureMigrateAppliance, click **Connect** and then log into the VM with the administrator password **<inject key="SmartHotel Admin Password" />** (the login screen may pick up your local keyboard mapping, use the 'eyeball' icon to check).
 
    ![](Images/DAA-image13.png)

1. Launch the **Azure Migrate appliance configuration Manager wizard** using the shortcut available on the desktop (wait for a minute or two, the browser will open showing the Azure Migrate appliance configuration wizard)

     > **Note:** If you are prompted with New updates available pop-up when connected with AzureMigrateAppliance VM, just click on View updates and then close the settings panel for now.

    ![Screenshot of the Azure Migrate appliance terms of use.](Images/HOL1-EX1-S15.png "Desktop shortcut")
    
    >**Note**: If you receive a prompt asking for credentials after launching the **Azure Migrate appliance configuration wizard** using the shortcut available on the desktop, please follow the instructions from [here](https://github.com/CloudLabsAI-Azure/Know-Before-You-Go/blob/main/AIW-KBYG/AIW-Infrastructure-Migration.md#1-exercise1---task3---step3) to connect to Azure Migrate appliance configuration wizard.

1. On opening of the appliance configuration wizard, if a pop-up with the license terms appears, accept the terms by selecting **I agree**.

    ![](Images/DAA-image15.png)

1. Under **Set up prerequisites**, the following two steps to verify Internet connectivity and time synchronization should pass automatically.

    ![](Images/DAA-image16.png)

1. **Wait** for some time while the wizard installs the latest Azure Migrate updates. If prompted for credentials, enter username **Administrator** and password **<inject key="SmartHotel Admin Password" />**. Once the Azure Migrate updates are completed, you may see a pop-up if the management app restart is required, and if so, select **Refresh** to restart the app.  

    ![Screenshot of the Azure Migrate appliance configuration wizard, showing the prompt to restart the management app after installing updates.](Images/upd-refresh.png "New update installed - Refresh")

1. At the next phase of the wizard, **Check latest updates and register appliance**, paste the **Azure Migrate project key (1)** that you copied from the Azure portal earlier and select **Verify (2)** to verify the Azure Migrate project key. 

     ![](Images/DAA-image17.png)

1. Wait for the **Appliance auto-update status (1)** to complete and select **Login (2)**. 

    ![](Images/DAA-image18.png)
   
    - Now, follow the below instructions to complete the login process.
    
     1. At first, you will be presented with a **Continue with Azure login** pop-up. On the **Continue with Azure login** pop-up dialog, click on **Copy code & Login**.
   
        ![](Images/DAA-image19.png)
  
     2. This will open an Azure login prompt in a new browser tab (if it doesn't appear, make sure the pop-up blocker in the browser is disabled) paste the **code (1)** and click on **Next (2)**. You will then be asked for your Azure portal credentials to complete the login process.

        ![](Images/DAA-image20.png)

     3. Login using the below Azure credentials and select **Continue** on the **Are you trying to sign in to Microsoft Azure PowerShell?** window to complete the login process. Once you have logged in, return to the Azure Migrate Appliance tab and the appliance registration will start automatically and displays below message once the registration is successful.
    
         * Azure Username/Email: <inject key="AzureAdUserEmail"></inject> 
         * Azure Password: <inject key="AzureAdUserPassword"></inject> 
     
           ![](Images/DAA-image23.png)

           ![](Images/DAA-image24.png)

   Once the registration has been completed, you can proceed to the next panel, **Manage credentials and discovery sources**.

1. In **Step 1: Provide Hyper-V host credentials for the discovery of Hyper-V VMs** under **2. Manage credentials and discovery sources**, select **Add credentials**.

    ![](Images/DAA-image25.png)

1. Specify the following details on the **Add credentials** blade for the Hyper-V host/cluster that the appliance will use to discover VMs and select **Save (4)**.
 
      1. Friendly name: Enter **hostlogin (1)** 
      2. Username: **<inject key="SmartHotelHost Admin Username" /> (2)**
      3. Password: **<inject key="SmartHotelHost Admin Password" /> (3)**

     ![](Images/DAA-image26.png)

     > **Note**: The Azure Migrate appliance may not have picked up your local keyboard mapping. Select the 'eyeball' in the password box to check the password was entered correctly.

1. In **Step 2: Provide Hyper-V host/cluster details**, select **Add discovery source** to specify the Hyper-V host/cluster IP address/FQDN and the friendly name for credentials to connect to the host/cluster.

    ![](Images/DAA-image27.png)

1. On the **Add discovery source** blade, provide the following details:
     
      1. Select **Add single item (1)**
      1. IP Address / FQDN:  Enter **HOSTVMS<inject key="DeploymentID" enableCopy="false" /> (2)** 
      1. Friendly name: Select **hostlogin (3)** from the dropdown and 
      1. Select **Save (4)**.

    ![](Images/DAA-image28.png)

    > **Note:** You can either **Add single item** at a time or **Add multiple items** in one go. There is also an option to provide Hyper-V host/cluster details through **Import CSV**.

1. The appliance will validate the connection to the Hyper-V hosts/clusters added and show the **Validation status** in the table against each host/cluster

   ![](Images/DAA-image29.png)

    > **Note:** When adding discovery sources:
    > - For successfully validated hosts/clusters, you can view more details by selecting their IP address/FQDN.
    > - If validation fails for a host, review the error by selecting the Validation failed in the Status column of the table. Fix the issue and validate again.
    > - To remove hosts or clusters, select **Delete**.
    > - You can't remove a specific host from a cluster. You can only remove the entire cluster.
    > - You can add a cluster, even if there are issues with specific hosts in the cluster.

1. In **Step 3: provide server credentials to perform software inventory and agentless dependency analysis**, **Disable the slider (1)** and select **Start discovery (2)** to kick off VM discovery from the successfully validated hosts/clusters.

   > **Note:** The discovery process can take up to 10 minutes. 
   
   ![](Images/DAA-image30.png)

1. Wait for the Azure Migrate status to show **Discovery has been successfully initiated**. This will take several minutes. After the discovery has been successfully initiated, you can check the discovery status against each host/cluster in the table.

1. Return to the **JumpVM** then to **Azure Migrate** blade in the Azure portal.  Select **Servers, databases, and web apps (1)**, then select **Refresh (2)**.  Under **Azure Migrate: Servers, databases and web apps** you should see a **count (3)** of the number of servers discovered so far. If discovery is still in progress, select **Refresh** periodically until 7 discovered servers are shown. This may take several minutes.

   ![](Images/DAA-image31.png)


   >**Note:** **Wait for the discovery process to complete before proceeding to the next Task**.


## Summary 

In this hands-on lab, you explored an Azure Migrate project and the default built-in tools for server assessment and server migration. You have also configured the Azure Migrate appliance in the on-premises Hyper-V environment and started the migration assessment discovery process using Azure Migrate.

### You have successfully completed the lab. Click on Next >> to procced with next lab.
