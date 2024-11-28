# HOL2: Exercise 2: Set up your environment on Azure to migrate servers

### Estimated time: 40 minutes

In this exercise, you will learn how to migrate machines as physical servers to Azure, using the Azure Migrate: Server Migration tool. Migrating machines by treating them as physical servers is useful in several scenarios such as, Migrate on-premises physical servers, Migrate Hyper-V VMs and much more.

## Lab objectives

In this exercise, you will complete the following task:

- Task 1: Configure dependency visualization

### Task 1: Configure dependency visualization

When migrating a workload to Azure, it is important to understand all workload dependencies. A broken dependency could mean that the application doesn't run properly in Azure, perhaps in hard-to-detect ways. Some dependencies, such as those between application tiers, are obvious. Other dependencies, such as DNS lookups, Kerberos ticket validation or certificate revocation checks, are not.

In this task, you will configure the Azure Migrate dependency visualization feature. This requires you to first create a Log Analytics workspace and then deploy agents on the to-be-migrated VMs.

1. Return to the **Azure Migrate** blade in the Azure Portal, select **Servers, databases and web apps (1)**. Under **Discovery and assessment** select **Groups (2)**.

    ![](Images/upd-nwgrpopen.png)   

2. Under the **Groups (1)** pane, select the **SmartHotel VMs (2)** group to see the group details. 

    ![](Images/upd-hol1-e2-t2-s2.png)  

3. Note that each VM has their **Dependencies** status as **Requires agent installation**. Select **Requires agent installation** for the **redhat** VM.

    ![Screenshot showing the SmartHotel VMs group. Each VM has dependency status 'Requires agent installation'.](Images/upd-hol2-e2-s3.png "SmartHotel VMs server group")

4. Navigate to **AzureMigrateWS<inject key="DeploymentID" enableCopy="false" />** by clicking on it.

    ![Screenshot of the Azure Migrate 'Configure OMS workspace' blade.](Images/omsworkspace.png "OMS Workspace settings")

7. Select **Agents** (1) under **Settings** from the left-hand side menu. Make a note of the **Workspace ID (2)** and **Primary Key (3)** (for example by using Notepad).

    ![Screenshot of part of the Azure Migrate 'Dependencies' blade, showing the OMS workspace ID and key.](Images/upd-workspace-id-key1.png "OMS Workspace ID and primary key")

8. You will now deploy the Linux versions of the Microsoft Monitoring Agent and Dependency Agent on the **redhat** VM. To do so, you will first connect to the Redhat VM remotely using an SSH session.

9. Open a command prompt using the desktop shortcut.  

10. Enter the following command to connect to the **redhat** VM running in Hyper-V on the SmartHotelHost:

    ```bash
    ssh administrator@192.168.1.19
    ```

11. Enter 'yes' when prompted whether to connect. Use the password **<inject key="SmartHotel Admin Password" />**.

    ![Screenshot showing the command prompt with an SSH session to UbuntuWAF.](Images/upd-ssh.png "SSH session with UbuntuWAF")

12. Enter the following command, followed by the password **<inject key="SmartHotel Admin Password" />** when prompted:
  
    ```
    su
    ```

    > This gives the terminal session elevated privileges.

13. Enter the following command, substituting \<Workspace ID\> and \<Primary Key\> with the values copied previously. Answer **Yes** when prompted to restart services during package upgrades without asking.  

    ```
    wget https://raw.githubusercontent.com/Microsoft/OMS-Agent-for-Linux/master/installer/scripts/onboard_agent.sh && sh onboard_agent.sh -w <Workspace ID> -s <Primary Key>
    ```

14. Enter the following command, substituting \<Workspace ID\> with the value copied earlier:

    ```s
    /opt/microsoft/omsagent/bin/service_control restart <Workspace ID>
    ```

15. Enter the following command. This downloads a script that will install the Dependency Agent.

    ```s
    wget --content-disposition https://aka.ms/dependencyagentlinux -O InstallDependencyAgent-Linux64.bin
    ```

16. Install the dependency agent by running the script download in the previous step.

    ```s
    sh InstallDependencyAgent-Linux64.bin -s
    ```

    ![Screenshot showing that the Dependency Agent install on Linux was successful.](Images/upd-da-linux-done.png "Dependency Agent installation was successful")
    

17. Return to the Azure Portal and refresh the Azure Migrate **SmartHotel VMs** VM group blade. The Redhat VM on which the dependency agent was installed should now show its status as **Installed**. (If not, refresh the page **using the browser refresh button**, not the refresh button in the blade.  It may take up to **5 minutes** after installation for the status to be updated.)

    ![Screenshot showing the dependency agent installed on each VM in the Azure Migrate VM group.](Images/upd-Linux-depencyagent.png "Dependency agent installed")
   
    >**Note**: If you notice that the dependency agent status is showing as **Requires Agent Installation** instead of Installed even after installing dependency agents in all the three VMs, please follow the steps from [here](https://github.com/CloudLabsAI-Azure/Know-Before-You-Go/blob/main/AIW-KBYG/AIW-Infrastructure-Migration.md#4-exercise1---task6---step1) to confirm dependency agent installation in VMs using Log Analytics workspace.
 
18. Select **View dependencies**.

    ![Screenshot showing the view dependencies button in the Azure Migrate VM group blade.](Images/upd-view-dependencies.png "View dependencies")
   
19. Take a few minutes to explore the dependencies view. Expand each server to show the processes running on that server. Select a process to see the process information. See which connections each server makes.

    ![Screenshot showing the dependencies view in Azure Migrate.](Images/upd-dependencies1.png "Dependency map")
 
### Summary 

In this exercise, you configured the Azure Migrate dependency visualization feature, by creating a Log Analytics workspace and deploying the Azure Monitoring Agent and Dependency Agent on a Linux on-premises machine.

Click on **Next** from the lower right corner to move on to the next page.
