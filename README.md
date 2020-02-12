
# Using Azure Budgets to Monitor Costs per Developer
## Business Problem
Throughout a project, you want developers to be able to test against resources in Azure. However, you need a way to monitor Azure consumption in order to enforce boundaries on how much each developer is spending.

## Logical Solution
Azure budgets in Cost Management enable you to account for consumption during a specific period. We can leverage budgets, scoped to resource groups, to monitor each dev's consumption during a given period and send out alerts at specified thresholds to the relevant parties.   

## How to Implement
### Create Resource Groups
First, we will need to create resource groups for each developer. All of the developer's resources should be created within this resource group and they will be accountable for any spending that happens inside of this gorup.

### Create an Action Group
Next, we will need to create an "action group". This action group defines the scope

In the portal, under Monitor > Alerts > Manage Actions > Add Action Group, create a new action group like so:
![actiongroup](https://github.com/clmccart/cost-monitoring/blob/master/image_refs/actiongroup.PNG)
Note: the email given here should be the email where you want the notifications for ALL budgets under this action group to go. This could be a budget admin, project lead, etc. 

## Creating Budgets
Once you have your resource groups and your action groups created, you can go into any of your resource groups under "Budgets" and add a budget.
Create a budget like so:
![image](image_refs/createbudget.png)

You will specify how often you want the bdget to reset, start and end dates for the budget, and what your budget amount is. Here, I have selected a budget of $10. 

Once you have done that, you will procedd to the next tab and set the alerts. 
Below is an example where I have alerts at 75% of my budget and 100% of my budget. I have specified the action group we created earlier and have added the developer whose resource group this is to the list of recipients.
![image](image_refs/createalerts.png)

Repeat this process for all of your developers.

## Leveraging Budgets
Once you are done, you can look at all of your budgets by navigating to your subscription in the portal, then going to the "Budgets" tab. Here you will see all of the budgets for your subscription and each of their current progress.
![image](image_refs/allbudgets.png)

If a user hits 75% or 100% of their budget, they (as well as the person specified in the action gorup) will receive an email notifying them of this.

## References
[Tutorial: Create and manage Azure budgets](https://docs.microsoft.com/en-us/azure/cost-management-billing/costs/tutorial-acm-create-budgets)


