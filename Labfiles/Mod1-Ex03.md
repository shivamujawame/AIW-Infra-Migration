
## Exercise 3: Migrating your apps and your data, leveraging Microsoft services and tools including Azure Migrate: Server Migration 

Duration: 90 minutes

### Task 1: Register the Hyper-V Host with Migration and modernization

In this task, you will register your Hyper-V host(LabVM) with the Migration and modernization service. This service uses Azure Site Recovery as the underlying migration engine. As part of the registration process, you will deploy the Azure Site Recovery Provider on your Hyper-V host.

1. Return to the **Azure Migrate | Servers, databases and web apps** blade in the Azure Portal, and select **Servers, databases and web apps (1)** under **Migration goals** on the left. Under **Migration Tools**, select **Discover (2)**.

   **Note:** You may need to add the migration tool yourself by following the link below the **Migration Tools** section, selecting **Migration and modernization**, then selecting **Add tool(s)**.
   
    ![Screenshot of the Azure portal showing the 'Discover' button on the Azure Migrate Server Migration panel.](Images/migrationtools.png "Azure Migrate: Server Migration - Discover")

2. In the **Discover** panel, provide the following details:
   - Under **Are your machines virtualized**, select **Yes, with Hyper-V**.
   - Under **Target region** the region is automatically selected as same the Resource Group's region.
   - Check the **confirmation** checkbox and select **Create resources** to begin the deployment of the Azure Site Recovery resource used by Migration and modernization for Hyper-V migrations.

   ![Screenshot of the Azure portal showing the 'Discover machines' panel from Azure Migrate.](Images/discover-new.png "Discover machines - source hypervisor and target region")

   Once deployment is complete, the 'Discover machines' panel should be updated with additional instructions.
  
3. Click on the **Download** link for the Hyper-V replication provider software installer to download the Azure Site Recovery provider installer.

   ![Screenshot of the Discover machines' panel from Azure Migrate, highlighting the download link for the Hyper-V replication provider software installer.](Images/e3%20t2%20s33.png?raw=true "Replication provider download link")

4. Return to the **Discover** page in your browser and select the blue **Download** button and download the registration key file.

   ![Screenshot of the Discover machines' panel from Azure Migrate, highlighting the download link Hyper-V registration key file.](Images/discover-4.png "Download registration key file")


5. Open the **AzureSiteRecoveryProvider.exe** installer you downloaded a moment ago. On the **Microsoft Update** tab, select **Off** and select **Next**. Accept the default installation location and select **Install**.

   ![Screenshot of the ASR provider installer.](Images/asr-provider-install.png "Azure Site Recovery Provider Setup")

6. When the installation has completed select **Register**. Browse to the location of the key file you downloaded. When the key is loaded select **Next**.

   ![Screenshot of the ASR provider registration settings.](Images/asr-registration.png "Key file registration")

7. Select **Connect directly to Azure Site Recovery without a proxy server** and select **Next**. The registration of the Hyper-V host with Azure Site Recovery will begin.

8. Wait for registration to complete (this may take several minutes). Then select **Finish**.

   ![Screenshot of the ASR provider showing successful registration.](Images/asr-registered.png "Registration complete")

9. Return to the Azure Migrate browser window. **Refresh** your browser, then re-open the **Discover machines** panel by selecting **Discover** under **Migration and modernization** and selecting **Yes, with Hyper-V** for **Are your machines virtualized?**.

10. Select **Finalize registration**, which should now be enabled.

    ![Screenshot of the Discover machines' panel from Azure Migrate, highlighting the download link Hyper-V registration key file.](Images/e3%20t2%20s10.png?raw=true "Finalize registration")

11. Azure Migrate will now complete the registration with the Hyper-V host. **Wait** for the registration to complete. This may take several minutes.

    ![Screenshot of the 'Discover machines' panel from Azure Migrate, showing the 'Finalizing registration...' message.](Images/discover-6.png "Finalizing registration...")

12. Once the registration is complete, close the **Discover machines** panel using **X** button.

    ![Screenshot of the 'Discover machines' panel from Azure Migrate, showing the 'Registration finalized' message.](Images/discover-7.png "Registration finalized")

13. The **Migration and modernization** panel should now show 5 discovered servers..

    ![Screenshot of the 'Azure Migrate - Servers' blade showing 6 discovered servers under 'Azure Migrate: Server Migration'.](./Images/discoveredservers5.png "Discovered servers")

#### Task summary 

In this task you registered your Hyper-V host with the Azure Migrate Server Migration service.

### Task 2: Enable Replication from Hyper-V to Azure Migrate

In this task, you will configure and enable the replication of your on-premises virtual machines from Hyper-V to the Azure Migrate Server Migration service.

1. Under **Migration and modernization**, select **Replicate**. This opens the **Replicate** wizard.

   ![Screenshot highlighting the 'Replicate' button in the 'Azure Migrate: Server Migration' panel of the Azure Migrate - Servers blade.](Images/replicate.png "Replicate link")
   
1. Under **Specific Intent** page, provide the below details:

    -  What do you want to migrate? : Select **Servers or Virtual machines (VM)** **(1)**
    -  Where do you want to migrate to? : Select **Azure VM** **(2)**
    -  Click on **Continue (3)**

    ![](Images/specifi%20intent.png)

2. In the **Source settings** tab, under **Are your machines virtualized?**, select **Yes, with Hyper-V** from the drop-down. Then select **Next**.

   ![Screenshot of the 'Source settings' tab of the 'Replicate' wizard in Azure Migrate Server Migration. Hyper-V replication is selected.](Images/replicate-2.png "Replicate - Source settings")

3. In the **Virtual machines** tab, under **Import migration settings from an assessment**, select **Yes, apply migration settings from an Azure Migrate assessment**. Select the **SmartHotel VMs** VM group and the **SmartHotelAssessment** migration assessment.

   ![Screenshot of the 'Virtual machines' tab of the 'Replicate' wizard in Azure Migrate Server Migration. The Azure Migrate assessment created earlier is selected.](Images/replicate-3.png "Replicate - Virtual machines")

4. The **Virtual machines** tab should now show the virtual machines included in the assessment. Select the **UbuntuWAF**, **smarthotelweb1**, and **smarthotelweb2** virtual machines, then select **Next**.

   ![Screenshot of the 'Virtual machines' tab of the 'Replicate' wizard in Azure Migrate Server Migration. The UbuntuWAF, smarthotelweb1, and smarthotelweb2 machines are selected.](Images/replicate-4.png "Replicate - Virtual machines")

5. On the **Target settings** tab, select the below information,
   - Select your subscription and the existing **SmartHotelRG (1)** resource group. 
   - **Replication storage account**: Select the **migrationstorage<inject key="DeploymentID" enableCopy="false" /> (2)** storage account.
   - **Virtual Network**: Select **SmartHotelVNet (3)**. 
   - **Subnet**: Select **SmartHotel (4)**. 
   - Select **Next (5)**.
 
 
   ![Screenshot of the 'Target settings' tab of the 'Replicate' wizard in Azure Migrate Server Migration. The resource group, storage account and virtual network created earlier in this exercise are selected.](Images/target%20settings.png "Replicate - Target settings")

 > **Note:** For simplicity, in this lab you will not configure the migrated VMs for high availability, since each application tier is implemented using a single VM.

6. On the **Compute** tab, select the below configuration,
   - Select the **Standard_F2s_v2** VM size for each virtual machine. 
   - Select the **Windows** operating system for the **smarthotelweb1**, **smarthotelweb2** virtual machines.
   - Select the **Linux** operating system for the **UbuntuWAF** virtual machine. 
   - Select **Next**. 


   ![Screenshot of the 'Compute' tab of the 'Replicate' wizard in Azure Migrate Server Migration. Each VM is configured to use a Standard_F2s_v2 SKU, and has the OS Type specified.](Images/replicate-6.png "Replicate - Compute")
    

7. In the **Disks** tab, review the settings but do not make any changes. Select **Next: Tags**, then select **Replicate** to start the server replication.

8. In the **Azure Migrate - Servers, databases and web apps** blade, under **Migration and modernization**, select the **Overview** button.

    ![Screenshot of the 'Azure Migrate - Servers' blade with the 'Overview' button in the 'Azure Migrate: Server Migration' panel highlighted.](Images/overviewnew.png "Overview link")
    
9. Confirm that the 3 machines are replicating.

   ![Screenshot of the 'Azure Migrate: Server Migration' overview blade showing the replication state as 'Healthy' for 3 servers.](Images/replicate-8.png "Replication summary")

10. Select **Replicating Machines** under **Manage** on the left.  Select **Refresh** occasionally and wait until all three machines have a **Protected** status, which shows the initial replication is complete. This will take 5-10 minutes.

    ![Screenshot of the 'Azure Migrate: Server Migration - Replicating machines' blade showing the replication status as 'Protected' for all 3 servers.](Images/replicate-9.png "Replication status")

   > **Note**: Please make sure to run the **validation steps** for this task before moving to next tasks as there are few dependencies. **Not** running the validation after performing this task will result in **validation failure**  as the status of the Virtual Machine will be changed from **Protected** to **Planned  failover** when you migrate the servers in Task6.

#### Task summary 

In this task you enabled replication from the Hyper-V host to Azure Migrate, and configured the replicated VM size in Azure.

### Task 3: Configure Networking

In this task you will modify the settings for each replicated VM to use a static private IP address that matches the on-premises IP addresses for that machine.

1. Still using the **Migration and modernization - Replicating machines** blade, select the **smarthotelweb1** virtual machine. This opens a detailed migration and replication blade for this machine. Take a moment to study this information.

   ![Screenshot from the 'Azure Migrate: Server Migration - Replicating machines' blade with the smarthotelweb1 machine highlighted.](images/Exercise3/config-0.png "Replicating machines")

2. Select **Compute and Network** under **General** on the left, then select **Edit**.

   ![Screenshot of the smarthotelweb1 blade with the 'Compute and Network' and 'Edit' links highlighted.](images/Exercise3/config-1.png "Edit Compute and Network settings")

3. Confirm that the VM is configured to use the **F2s_v2** VM size.

4. Under **Network Interfaces**, select **InternalNATSwitch** to open the network interface settings.

   ![Screenshot showing the link to edit the network interface settings for a replicated VM.](images/Exercise3/nic.png "Network Interface settings link")

5. Change the **Private IP address** to **192.168.0.4**.

   ![Screenshot showing a private IP address being configured for a replicated VM in ASR.](images/Exercise3/private-ip.png "Network interface - static private IP address")

6. Select **OK** to close the network interface settings blade, then **Save** the **smarthotelweb1** settings.

7. Repeat these steps to configure the private IP address for the other VMs.
 
   - For **smarthotelweb2** use private IP address **192.168.0.5**
  
   - For **UbuntuWAF** use private IP address **192.168.0.8**

#### Task summary 

In this task you modified the settings for each replicated VM to use a static private IP address that matches the on-premises IP addresses for that machine

> **Note**: Azure Migrate makes a "best guess" at the VM settings, but you have full control over the settings of migrated items. In this case, setting a static private IP address ensures the virtual machines in Azure retain the same IPs they had on-premises, which avoids having to reconfigure the VMs during migration (for example, by editing web.config files).


### Task 4: Server migration

In this task you will perform a migration of the UbuntuWAF, smarthotelweb1, and smarthotelweb2 machines to Azure.

> **Note**: In a real-world scenario, you would perform a test migration before the final migration. To save time, you will skip the test migration in this lab. The test migration process is very similar to the final migration.

1. Return to the **Migration and modernization** overview blade. Under **Step 3: Migrate**, select **Migrate**.

   ![Screenshot of the 'Azure Migrate: Server Migration' overview blade, with the 'Migrate' button highlighted.](images/Exercise3/migrate-1.png "Replication summary")

2. On the **Migrate** blade, select **yes** for **Shutdown machines before migration to minimum data loss** and select the 3 virtual machines then select **Migrate** to start the migration process.

   ![Screenshot of the 'Migrate' blade, with 3 machines selected and the 'Migrate' button highlighted.](images/Exercise3/e3%20t6%20ss2.png?raw=true "Migrate - VM selection")

   > **Note**: You can optionally choose whether the on-premises virtual machines should be automatically shut down before migration to minimize data loss. Either setting will work for this lab.

3. The migration process will start.

   ![Screenshot showing 3 VM migration notifications.](images/Exercise3/migrate-3.png "Migration started notifications")

4. To monitor progress, select **Jobs** under **Manage** on the left and review the status of the three **Planned failover** jobs.

   ![Screenshot showing the **Jobs* link and a jobs list with 3 in-progress 'Planned failover' jobs.](images/Exercise3/migrate-4.png "Migration jobs")

5. **Wait** until all three **Planned failover** jobs show a **Status** of **Successful**. You should not need to refresh your browser. This could take up to 15 minutes.

   ![Screenshot showing the **Jobs* link and a jobs list with all 'Planned failover' jobs successful.](images/Exercise3/migrate-5.png "Migration status")

6. Navigate to the **SmartHotelRG** resource group and check that the VM, network interface, and disk resources have been created for each of the virtual machines being migrated.

   ![Screenshot showing resources created by the test failover (VMs, disks, and network interfaces).](images/Exercise3/migrate-6.png "Migrated resources")

#### Task summary 

In this task you used Azure Migrate to create Azure VMs using the settings you have configured, and the data replicated from the Hyper-V machines. This migrated your on-premises VMs to Azure.


### Task 5: Configure the database connection

The application tier machine **smarthotelweb2** is configured to connect to the application database running on the **smarthotelsql** machine.

On the migrated VM **smarthotelweb2**, this configuration needs to be updated to use the Azure SQL Database instead.

> **Note**: You do not need to update any configuration files on **smarthotelweb1** or the **UbuntuWAF** VMs, since the migration has preserved the private IP addresses of all virtual machines they connect with.

1. From the Azure portal menu which is present at the top left, click on **All services**. Select **compute** from the left hand menu and select **Virtual machines**.

2. Click on **smarthotelweb2** VM, from the overview blade, and select **Connect**. Select **Bastion** from the available options and click on **Use Bastion**.

   **Note:** You may have to wait a few minutes and refresh to have the option to enter the credentials. 

3. Connect to the machine with the username **Administrator** and the password <inject key="SmartHotelHost Admin Password"></inject>. When prompted, **Allow** clipboard access.

   ![Screenshot showing the Azure Bastion connection blade.](images/Exercise3/web2-connect.png "Connect using Bastion")

4. In the **smarthotelweb2** remote desktop session, open File Explorer and navigate to the **C:\\inetpub\\SmartHotel.Registration.Wcf** folder. Double-select the **Web.config** file and open with Notepad.

5. Update the **DefaultConnection** setting to connect to your Azure SQL Database.

   You can find the connection string for the Azure SQL Database in the Azure portal. Navigate to the **SmartHotelRG** resource group, and then to the database **smarthoteldb** and  from the overview, select **Show database connection strings**.

   ![Screenshot showing the 'Show database connection strings' link for an Azure SQL Database.](images/Exercise3/show-connection-strings.png "Show database connection strings")

    Copy the **ADO.NET** connection string, and paste into the web.config file on **smarthotelweb2**, replacing the existing connection string.  **Be careful not to overwrite the 'providerName' parameter which is specified after the connection string.**

    > **Note:** You may need to open the clipboard panel on the left-hand edge of the Bastion window, paste the connection string there, and then paste into the VM.

    Set the password in the connection string to **<inject key="SmartHotelHost Admin Password" />**.

    ![Screenshot showing the user ID and Password in the web.config database connection string.](images/Exercise3/web2-connection-string.png "web.config")

6. **Save** the `web.config` file and exit your Bastion remote desktop session.

#### Task summary 

In this task, you updated the **smarthotelweb2** configuration to connect to the Azure SQL Database.

### Task 6: Configure the public IP address and test the SmartHotel application

In this task, you will associate an Application Gateway with Web Application Firewall (WAF) to replace the Ubuntu VM with the Azure managed service.

1. Navigate to the **SmartHotel-WAF** Application Gateway in the **SmartHotelRG** resource group

1. Select **Backend pools** under the Settings section, and select the **WebBackend** pool

    ![Screenshot showing the backend pool selection for the Application Gateway](images/Exercise3/waf-backend-pool.png "Select WebBackend")

1. Set the Target type to **Virtual machine** and the Target to the NIC of **smarthotelweb1**; select **Save** to update the backend pool

    ![Screenshot showing virtual machine add to the backend pool of Application Gateway](images/Exercise3/backendpool-01.png "Add VM to backend pool")

    > **Note:** This backend pool is already associated with the front-end IP address of the Application Gateway via the SmartHotelApp rule. The front-end IP, listener, rule, and backend pool were all created with the Application Gateway. This step now ties the migrated VM to the front end.

1. Navigate to the **SmartHotelRG** resource group, and then to the **SmartHoteldb<inject key="DeploymentID" enableCopy="false" />** database server to update the Firewall settings.
           
1. Under Security, select **Networking** then **Public access** tab. Now, set **Public network access** to **Selected networks** and **Save** your changes.

    ![](images/Exercise3/website1.1.png)
     
1. Now, on the **Public access** tab, click on **Add a virtual network rule** to add a virtual network so that the access to the database will be allowed from specific network.

    ![](images/Exercise3/website2.1.png)
   
1. On the **Create/Update** blade, enter the below information.

    - **Name**: **AllowaccesstoDB**
    - **Subscription**: Select your subscription from the dropdown.
    - **Virtual Network**: Select **SmartHotelVNet**. 
    - **Subnet**: Select **SmartHotel**.
    - Click on **Enable** and then **Ok**.

    ![](images/Exercise3/website3.png)
   
1. Navigate back to the **Public access** tab of **Networking** section. Set **Public network access** to **Disabled** and **Save** your changes.

    ![](images/Exercise2/deny-firewalls-sqlserver1.png)
   
1. Navigate back to the **SmartHotel-WAF** Application Gateway then **Frontend IP configurations** way in the Settings section, and note the IP address associated with the public IP address **appGwPublicFrontendIp**.

    ![Screenshot showing public IP address of the Application Gateway that is now associated with the backend VM.](images/Exercise3/waf-public-ip-address.png "Public IP address of AppGW")

1. Open a new browser tab and paste the IP address into the address bar. Verify that the SmartHotel360 application is now available in Azure.

    ![Screenshot showing the SmartHotel application.](images/Exercise3/lob-issue-02.png "Migrated SmartHotel application")
 
    > **Note**: 
      1. The Check-in and Check-out might differ for you when compared to the above screenshot.
      2. At this point the base Application Gateway service is providing access to the backend application. This validates that the application is working and can be further protected by the WAF in following steps.

1. Select **Web application firewall** under the Settings section and change the Tier to **WAF V2**.  Also, change the Firewall status to **Enabled**, the Firewall mode to **Prevention**, and set the Max request body size (KB) to **32**.  Select **Save** to commit the changes.

    ![Screenshot changing Application Gateway to WAF V2 tier and enabling the WAF in prevention mode](images/Exercise3/waf-enable-waf-v2.png "Enable WAF v2")

1. Once the application gateway changes have been saved, go back to your web browser with the public IP address of the application gateway you used earlier and refresh the browser to have a page processed by the WAF.


#### Task summary 

In this task, you assigned a public IP address to the UbuntuWAF VM and verified that the SmartHotel application is now working in Azure.

