## Overview

Before the lab, you will have pre-deployed an on-premises infrastructure hosted in Hyper-V.  This infrastructure is hosting a multi-tier application called 'SmartHotel', using Hyper-V VMs for each of the application tiers.

During the lab, you will migrate this entire application stack to Azure. This will include assessing the on-premises application using Azure Migrate; assessing the database migration using Microsoft Data Migration Assistant (DMA); migrating the database using the Azure Database Migration Service (DMS); and migrating the web and application tiers using Azure Migrate: Server Migration. This last step includes migration of both Windows and Linux VMs.

In hands on lab 1, you will evaluate the on-premises environment using Azure Migrate, choosing Azure Migrate tools, setting up the Azure Migrate appliance in an on-premises environment, doing a migration evaluation, and utilising the dependency visualisationl, develop a migration assessment for the SmartHotel application using Azure Migrate, register your LabVM Hyper-V host with the Migration and Modernization service in this activity. Azure Site Recovery serves as the foundational migration engine for this service. You will install the Azure Site Recovery Provider on your Hyper-V server as part of the registration procedure. In hands on lab 2, you will be using the Redhat VM and Cosmosdb for performing the above migration activities.

In hands on lab 3, you will install and set up the agent on a Windows machine (AzureArcVM) that is hosted outside of Azure so that it can be controlled by servers that support Azure Arc. Your disaster recovery plan benefits from the Azure Site Recovery service's supervision and automation of on-premises machine replication, failover, and failback, deploy a Test Failover to evaluate the stability of the virtualized workload without affecting your production workload or ongoing replication and also deploy a Failover so that Azure VM is built from replicated data following failover.

## Solution architecture

The SmartHotel application comprises 4 VMs hosted in Hyper-V:

- **Database tier** Hosted on the smarthotelSQL1 VM, which is running Windows Server 2016 and SQL Server 2017.

- **Application tier** Hosted on the smarthotelweb2 VM, which is running Windows Server 2012R2.

- **Web tier** Hosted on the smarthotelweb1 VM, which is running Windows Server 2012R2.

- **Web proxy** Hosted on the  UbuntuWAF VM, which is running Nginx on Ubuntu 18.04 LTS.

For simplicity, there is no redundancy in any of the tiers.

>**Note:** For convenience, the Hyper-V host itself is deployed as an Azure VM. For the purposes of the lab, you should think of it as an on-premises machine.


![A slide shows the on-premises SmartHotel application architecture.](Images/overview.png "SmartHotel Migration Overview")

Throughout this lab, you will use Azure Migrate as your primary tool for assessment and migration. In conjunction with Azure Migrate, you will also use a range of other tools, as detailed below.

To assess the Hyper-V environment, you will use Azure Migrate: Server Assessment. This includes deploying the Azure Migrate appliance on the Hyper-V host to gather information about the environment. For deeper analysis, the Microsoft Monitoring Agent and Dependency Agent will be installed on the VMs, enabling the Azure Migrate dependency visualization.

The SQL Server database will be assessed by installing the Microsoft Data Migration Assistant (DMA) on the Hyper-V host, and using it to gather information about the database. Schema migration and data migration will then be completed using the Azure Database Migration Service (DMS).

The application, web, and web proxy tiers will be migrated to Azure VMs using Azure Migrate: Server Migration. You will walk through the steps of building the Azure environment, replicating data to Azure, customizing VM settings, and performing a failover to migrate the application to Azure.

> **Note**: After migration, the application could be modernized to use Azure Application Gateway instead of the Ubuntu Nginx VM, and to use Azure App Service to host both the web tier and application tiers. These optimizations are out of scope of this lab, which is focused only on a 'lift and shift' migration to Azure VMs.
