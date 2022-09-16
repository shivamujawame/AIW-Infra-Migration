### HOL3: Exercise 3: Setup test failover

1. If you are not logged in already, click on Azure portal shortcut that is available on the desktop and log in with below Azure credentials.
    * Azure Username/Email: <inject key="AzureAdUserEmail"></inject> 
    * Azure Password: <inject key="AzureAdUserPassword"></inject>

1. In the **search resources, services and docs bar**, type **Recovery service vaults** and select it from suggestions, as shown below:
   
    ![Screenshot of the search Recovery service vaults.](Images/upd-search-asr.png "Recovery service vaults")
    
1. Select the Recovery service vault that you created in the previous exercise.    
    
1. On the **Recovery Service Vault page**, click **Replicated Items (1)** under **Protected Items** and select **smartholweb1 (2)** that you replicated in the previous exercise.     

    ![Screenshot of the replicate items.](Images/failover-1.png "replicate items") 
   
1. On the **smarthotelweb1** page, click on **Test Failover**.  

    ![Screenshot of the Test Failover.](Images/failover-2.png "Test Failover") 
   
1. On the **Test failover page**, select the Azure virtual network: **SmartHotelVNet (1)** and click **Ok (2)**.

    ![Screenshot of the Test Failover page.](Images/failover-3.png "Test Failover page") 

1. Wait for 10-15 minutes, for the job status of the test failover to get completed successfully.

    ![Screenshot of the Test Failover status.](Images/failover-4.png "Test Failover status") 
  
1. In the **search resources, services and docs bar**, type **Virtual Machines** and select it from suggestions.

1. Under **Virtual Machines** page, select the **smarthotelweb1-test** which is automatically created after test failover.

    ![Screenshot of the Test vm.](Images/test-vm.png "Test vm") 
  
1. On the **smarthotelweb1-test page**, verify that the status of the VM is in **Running state (1)** and also you are able to **Connect it through RDP (2)**.  

    ![Screenshot of the Test vm status.](Images/test-vm-status.png "Test vm status") 
