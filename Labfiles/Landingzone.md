# Landing zone creation using ARM template

## Requirements

1. You will need Owner or Contributor permissions for an Azure subscription to use in the lab.

2. Your subscription must have sufficient unused quota to deploy the VMs used in this lab. To check your quota:

    - Log in to the Azure portal, select **All services** then **Subscriptions**. Select your subscription, then choose **Usage + quotas**.
  
    - From the **Select a provider** drop-down, select **Microsoft.Compute**.
  
    - From the **All service quotas** drop down, select **Standard DSv3 Family vCPUs**, **Standard FSv2 Family vCPUs** and **Total Regional vCPUs**.
  
    - From the **All locations** drop down, select the location where you will deploy the lab.
  
    - From the last drop-down, select **Show all**.
  
    - Check that the selected quotas have sufficient unused capacity:
  
        - Standard DSv3 Family vCPUs: **at least 8 vCPUs**.
  
        - Standard FSv2 Family vCPUs: **at least 6 vCPUs**.

        - Total Regional vCPUs: **at least 14 vCPUs**.

    > **Note:** If you are using an Azure Pass subscription, you may not meet the vCPU quotas above. In this case, you can still complete the lab, by taking the following steps:


### Task 1: Deploy the landing zone

You can deploy the template by selecting the 'Deploy to Azure' button below. You will need to create a new resource group. The suggested resource group base name (prefix) to use is **SmartHotel**. You will also need to select a location close to you to deploy the template to. Then choose **Review + create** followed by **Create**. 

  <a href="https://experienceazure.blob.core.windows.net/templates/mcw-line-of-business-application-migration/lob-lz-deploy.json" target="_blank">![Button to deploy the SmartHotelHost template to Azure.](images/BeforeTheHOL/deploy-to-azure.png "Deploy the SmartHotelHost template to Azure")</a>

   
   > **Note:** The template will take around 6-7 minutes to deploy. Once template deployment is complete, several additional scripts are executed to bootstrap the lab environment. **Allow at least 1 hour from the start of template deployment for the scripts to run.**
