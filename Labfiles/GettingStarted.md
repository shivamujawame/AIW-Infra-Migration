# Getting Started with Lab

1. Once the environment is provisioned, a virtual machine (JumpVM) and lab guide will get loaded in your browser. Use this virtual machine throughout the workshop to perform the lab. You can see the number on the bottom of the lab guide to switch to different exercises of the lab guide.

   ![](Images/upd-cloudlab-vm-guide.png "Lab Environment")

1. To get the lab environment details, you can select the **Environment Details** tab. Additionally, the credentials will also be emailed to your registered email address. You can also open the Lab Guide on the separate and full windows by selecting the **Split Window** from the lower right corner. Also, you can start, stop, and restart virtual machines from the **Resources** tab.

   ![](Images/upd-splitwindow1.png "Lab Environment")
 
    > You will see the DeplymentID value on the **Environment Details** tab, use it wherever you see SUFFIX or DeploymentID in lab steps.

1. You can validate each task by navigating to **Lab Validation** tab and clicking on **Validate** button. Please make sure you run the validation steps for each task after performing it. 

   ![](Images/upd-validation.png "Lab Environment")

## Login to Azure Portal
1. In the JumpVM, click on the Azure portal shortcut of the Microsoft Edge browser which is created on the desktop.

     ![](Images/upd-cloudlab-vm-guide.png "Lab Environment")
   
1. On the **Sign into Microsoft Azure** tab you will see the login screen, in that enter the following email/username and then click on **Next**. 
   * Email/Username: <inject key="AzureAdUserEmail"></inject>
   
     ![](Images/image7.png "Enter Email")
     
1. Now enter the following password and click on **Sign in**.
   * Password: <inject key="AzureAdUserPassword"></inject>
   
     ![](Images/image8.png "Enter Password")
     
   > If you are presented with **Help us protect your account** dialog box, then select **Skip for now** option.

      ![](Images/MFA.png "Enter Password")
  
1. If you see the pop-up **Stay Signed in?**, click No

1. If you see the pop-up **You have free Azure Advisor recommendations!**, close the window to continue the lab.

1. If a **Welcome to Microsoft Azure** popup window appears, click **Maybe Later** to skip the tour.
   
1. Now you will see the Azure Portal Dashboard, click on **Resource groups** from the Navigate panel to see the resource groups.

     ![](Images/select-rg.png "Resource groups")
   
1. Confirm you have all resource groups present as shown below.

     ![](Images/upimage10.png "Resource groups")
   
1. Now, click on the **Next** from the lower right corner to move to the next page.
