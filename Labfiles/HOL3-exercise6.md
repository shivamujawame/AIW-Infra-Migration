## HOL3: Exercise 6: Azure Governance (Read Only)

The term governance describes the general process of establishing rules and policies and ensuring that those rules and policies are enforced. 
Azure Governance is the framework that determines how your organization conducts business activities, based on objectives and responsibilities. And when we talk about Cloud Governance, there are a number of principles that are relevant: Subscription Management, Cost Management, Security, Resource Consistency, Identity Baseline & Deployment Acceleration.

When running in the cloud, a good governance strategy helps you maintain control over the applications and resources that you manage in the cloud. Maintaining control over your environment ensures that you stay compliant with:

- Industry standards, like PCI DSS.
- Corporate or organizational standards, such as ensuring that network data is encrypted.

**Governance is most beneficial when you have:**

- Multiple engineering teams working in Azure.
- Multiple subscriptions to manage.
- Regulatory requirements that must be enforced.
- Standards that must be followed for all cloud resources.

**Azure Governance Framework:**
Azure Governance, a cloud security framework, is specialized guidelines that encourage security measures for cloud use within Microsoft Azure. The cloud security guidelines often outline the policies, tools, configurations, and rules needed to secure data and identities in the cloud environment.

Azure Governance Security Frameworks are the enforcement of your overall security strategy. Any cloud practitioner knows that securing cloud environments is a challenge. The scale of the cloud allows for exponential growth, with exponential complexity and headaches.

Security is one of the essential parts of your cloud governance plan. You want to enforce least access with everyone when managing your data. With Azure Policy, you can create and set your security policy to meet the least access. The security rules resulting from this security policy are automatically implemented in your environment, and new and existing resources are audited.

By enforcing these policies, you can ensure that your organization complies with your company’s standards and service level agreements.

Governance provides mechanisms and processes to maintain control over your applications and resources in Azure. It involves planning your initiatives and setting strategic priorities. 

  ![Screenshot of the govern.](Images/operational-transformation-govern-large.png "govern")
  
Azure governance is a combination of different Azure services and capabilities, allowing for the management of all your Azure resources at scale and following control guidelines. Azure governance works across multiple subscriptions and across resource groups, and is based on a combination of Azure identity, Role-Based Access Control (RBAC), Azure policies, and management groups.

**Services in Azure Governance:**

- **Management groups** provides a cross-subscription assignment of Azure Policy and Initiative.
- **Identity and role-based access control** enables you to create roles that define access permissions. Azure provides built-in roles that describe common access rules for cloud resources. You can also define your own roles. Each role has an associated set of access permissions that relate to that role.
- **Azure Policy** allows you to create, assign, and manage policy definitions to enforce rules for your resources. This feature keeps those resources in compliance with your corporate standards. This is a true governance management and control mechanism in Azure. As an organization, you define Azure policies: JSON files in which you specify what Azure resource requirements you want to enforce before the deployment of Azure resources can succeed. Azure policies can be grouped together into so-called **Azure policy initiatives**. This helps in enforcing several policies at once. After the Azure policies and policy initiatives are defined, they need to be assigned to a scope. This scope can be an Azure subscription, an Azure resource group, or individual Azure resources.
- **Azure Cost Management** allows you to track cloud usage and expenditures for your Azure resources and other cloud providers. Microsoft recently acquired Cloudyn, a multi-cloud cost reporting tool. The Cloudyn service enables any organization to pull up detailed dashboards, exposing cost consumption for any Azure resource or group of resources, based on resource type, region, or tags attached to the Azure resources itself. Another Cost Management feature is **Cost Budgets**. This is a soft setting, allowing you to define a ceiling of cost consumption for a certain Azure resource or resource group. 
- **Azure Blueprints** allows cloud architects and IT teams to define a structure of reusable, repeatable instructions for deployment and configuration, in compliance with company standards, regulations, and requirements. Relying on a combination of roles, controls, and infrastructure as code, Azure Blueprints orchestrates the full deployment life cycle of Azure resources.
