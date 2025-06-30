# Migrate Linux Servers to Azure

### Overall Estimated Duration: 4 Hours

## Overview

In this lab, you will access Hyper-V Manager to start and connect to a Red Hat VM hosting an OSS database, preparing it for migration to Azure using Azure Migrate. You will register your Hyper-V host (LabVM) with the Migration and Modernization service, which leverages Azure Site Recovery as the migration engine. As part of this process, you will deploy the Azure Site Recovery Provider on your Hyper-V host and configure replication of the on-premises VM to Azure Migrate Server Migration. You will then modify the replicated VM settings to assign a static private IP matching the on-premises configuration before executing the migration of the Red Hat VM to Azure.

## Objectives

- **Migrating your apps and your data, leveraging Microsoft services and tools like Azure Migrate, the Azure Hybrid Benefit, and other tools and programs**: Perform the migration of a Red Hat VM from Hyper-V to Azure using Azure Migrate and Azure Site Recovery.

## Prerequisites

- Basic knowledge of Hyper-V Manager and virtual machine management.
- Experience with Red Hat Linux administration and command-line operations.
- Understanding of Azure Migrate and its migration process.
- Familiarity with Azure Site Recovery as a migration engine.
- Ability to configure virtual machine networking, including setting static IP addresses.
  
## Architecture

The architecture flow begins with accessing Hyper-V Manager to start and connect to a Red Hat VM hosting an OSS database. The Hyper-V host (LabVM) is then registered with the Azure Migration and Modernization service, which utilizes Azure Site Recovery as the migration engine. As part of this setup, the Azure Site Recovery Provider is deployed on the Hyper-V host to facilitate replication. The on-premises VM is then configured for replication to the Azure Migrate Server Migration service. Before migration, the replicated VM settings are adjusted to use a static private IP matching its on-premises configuration. Finally, the migration process is executed, transferring the Red Hat VM from Hyper-V to Azure.

## Architecture Diagram

   ![](./Images/archmigrate.PNG)

## Explanation of Components

1. **Azure Migrate** – A Microsoft service that helps assess, replicate, and migrate on-premises workloads to Azure.
1. **Linux Server** – An open-source operating system that runs applications and services, commonly used for cloud and enterprise workloads.
1. **Hyper-V** – A Microsoft virtualization platform that allows running multiple virtual machines (VMs) on a single physical server.
1. **Red Hat** – A leading enterprise Linux distribution providing security, stability, and performance for cloud and on-prem workloads.
1. **Azure Virtual Networks** – A logically isolated network in Azure that enables secure communication between Azure resources, on-premises networks, and the internet.

## Getting Started with the lab
 
Welcome to your Migrate Linux Servers to Azure! We've prepared a seamless environment for you to explore and learn about Azure services. Let's begin by making the most of this experience:
 
## Accessing Your Lab Environment
 
Once you're ready to dive in, your virtual machine and **Lab Guide** will be right at your fingertips within your web browser.

   ![](./Images/G1.png)

## Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.
 
## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment** tab.

   ![](./Images/G2.png)
 
## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.
 
   ![](./Images/G3.png)
 
## Managing Your Virtual Machine
 
Feel free to start, stop, or restart your virtual machine as needed from the **Resources** tab. Your experience is in your hands!
 
  ![](./Images/G4.png)

  ## Lab Guide Zoom In/Zoom Out
 
To adjust the zoom level for the environment page, click the **A↕: 100%** icon located next to the timer in the lab environment.

   ![](./Images/G5.png)
 
## Let's Get Started with Azure Portal
 
1. On your virtual machine, click on the Azure Portal icon as shown below:
 
    ![](./Images/GS1.png)
 
2. You'll see the **Sign into Microsoft Azure** tab. Here, enter your credentials:
 
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
 
      ![](./Images/GS2.png)
 
3. Next, provide your password:
 
   - **Password:** <inject key="AzureAdUserPassword"></inject>
 
      ![](./Images/GS3.png)
 
4. If you see the pop-up **Stay Signed in?**, click **No**.

   ![](./Images/sign-in.png)

5. If you see the pop-up **You have free Azure Advisor recommendations!**, close the window to continue the lab.

6. If a **Welcome to Microsoft Azure** popup window appears, click **Cancel** to skip the tour.

7. Now you will see the Azure Portal Dashboard, click on **Resource groups** from the Navigate panel to see the resource groups.

     ![](Images/select-rg.png "Resource groups")
   
8. Confirm you have all resource groups present as shown below.

     ![](Images/upimage10.png "Resource groups")
 
## Support Contact
The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

   - Email Support: cloudlabs-support@spektrasystems.com
   - Live Chat Support: https://cloudlabs.ai/labs-support

Now you're all set to explore the powerful world of technology. Feel free to reach out if you have any questions along the way. Enjoy your workshop!

Now, click on the **Next** from the lower right corner to move to the next page.

   ![](./Images/GS4.png)

## Happy Learning!!
