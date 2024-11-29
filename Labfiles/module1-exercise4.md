
# HOL1: Exercise 4: Optimizing newly Migrated Workloads and Emphasizing commonalities across all Stacks


### Estimated time: 25 minutes

In this exercise, you will focus on enhancing business resilience through the use of Azure Virtual Machine Scale Sets (VMSS). It involves creating and deploying a specialized virtual machine image, which is captured and stored in a gallery named "imagemigration." Additionally, a VM scale set called "migrationscaleset" is established to showcase Azure's scalability and business continuity capabilities. As part of this process, you will also enable Automanage on existing machines to streamline management and optimize performance.

## Lab objectives

In this exercise, you will complete the following tasks:

- Task 1: Using VM Scale Sets to Drive Business Resiliency
- Task 2: Azure auto manage

### Task 1: Using VM Scale Sets to Drive Business Resiliency

In this task, you will be using Azure Virtual Machine Scale Sets (VMSS) to improve business resilience by creating and deploying a specialized virtual machine image. The image is captured and stored in a gallery called imagemigration, and a VM scale set named migrationscaleset is created, demonstrating Azure's scalability and business continuity capabilities.

1. If you are not logged in already, click on the Azure portal shortcut that is available on the desktop and log in with below Azure credentials.
    * Azure Username/Email: <inject key="AzureAdUserEmail"></inject> 
    * Azure Password: <inject key="AzureAdUserPassword"></inject>

2. In the Azure portal's navigation pane, select **Resource groups**.

3. From the Resource groups blade, select the **SmartHotelHostRG** resource group.

4. Select **smarthotelweb1** VM to create image.

2. On the page for the VM, on the upper menu, select **Capture > Image**.
   
   ![](Images/30-09-2024(8).png)

4. To create the image in a gallery, select **Yes, share it to a gallery as an image version** under **Instance details**.

   ![](Images/md1-ex-4-t1-s6.png)

5. In **Gallery details**, create a new gallery by selecting **Create new (1)** and enter **imagemigration<inject key="DeploymentID" enableCopy="false" /> (2)** and click **Ok (3)**.

   ![](Images/upd-e4-t1-s7.png)

6. In the Operating system state select **Specialized**.

7. On the Target VM definition click **Create new (1)** and create a VM Image definition by providing the following details and then click **Ok (6)**: 
  
   - Image VM definition name: **imagedefinition<inject key="DeploymentID" enableCopy="false" /> (2)**

   - Publisher: **Microsoft (3)**
    
   - Offer: **windows (4)**
  
   - SKU: **migration (5)**

   ![](Images/upd-4-t1-s9.png)

8. Enter an **image version** number. If this is the first version of this image, type **1.0.0**

9. Select **Review + create**.

10. After validation passes, select **Create** to create the image and wait for the image creation.

11. On the page for the image gallery, on the upper menu, select **+ Create VMSS**.

    ![](Images/upd-vmss1.png)

12. Under the Basics tab, enter the **Virtual Machine name scale set** name as **migrationscaleset<inject key="DeploymentID" enableCopy="false" />**

    ![](Images/upd-vmname.png)

13. Select **Standard_D2s_v3** for the **size**.

14. Select the License type as **Window server**.

     ![](Images/30-09-2024(9).png)

15. Select **Review + create** and then **Create**.

     > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
     > - Hit the Inline Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
     > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
     > - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help.

     <validation step="1dff74eb-dff7-4fd6-a103-04ff946cae88" />

### Task 2: Azure auto manage

In this task, you will Enable Automanage on existing machines.

1. If you are not logged in already, click on the Azure portal shortcut that is available on the desktop and log in with below Azure credentials.
    * Azure Username/Email: <inject key="AzureAdUserEmail"></inject> 
    * Azure Password: <inject key="AzureAdUserPassword"></inject>

2. In the search bar, search for and select **Automanage**.

3. From the left side panel select **Automanage machines (1)** under Machine best practices and click on **+ Enable on existing machine (2)**.
   
   ![](Images/upd-zero-vm-list-view.png)

4. Under **Configuration profile**, select your profile type: **Azure Best Practices - Production or Azure Best Practices - Dev/Test or Custom profile** and click on **Next: Machines >**
   
   ![](Images/upd-existing-vm-quick-create.png)
   
   > Click **View best practice profiles** to see the differences between the environments.
    
   ![](Images/upd-browse-production-profile.png)

5. On the **Select Machines** blade:

   i. Filter the list by your Subscription and Resource group and click on **Check eligibility on machines (1)**.
   
   ii. **Check the checkbox of the virtual machine (2)** you want to onboard. (for example: let's enable automanage for smarthotelweb2.)
   
   iii. Click on the **Review + Create (3)** button.
   
   ![](Images/updt-existing-vm-select-machine.png)

6. Click **Create**.

### Summary 

In this exercise, you focused on enhancing business resilience through the use of Azure Virtual Machine Scale Sets (VMSS). It involved creating and deploying a specialized virtual machine image, which was captured and stored in a gallery named "imagemigration." Additionally, a VM scale set called "migrationscaleset" was established to showcase Azure's scalability and business continuity capabilities. As part of this process, Automanage was enabled on existing machines to streamline management and optimize performance.

Click on **Next** from the lower right corner to move on to the next page.
