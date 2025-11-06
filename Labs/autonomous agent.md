# Create autonomous agent

In this exercise, you use Copilot Studio to create an agent that helps HR with onboarding a new employee. This exercise requires you to create a Microsoft Dataverse table.

## Scenario

As a member of the HR team, you're building an HR agent to simplify the employee onboarding process. Your goal is to create an agent that can perform the following activities:

- Provide general information and answer queries that relate to employee onboarding.
- Submit a request automatically to onboard a new employee through the system.
- Send an onboarding request approval email automatically to the hiring manager that includes tasks, such as procuring a laptop, setting up an email account, and other onboarding essentials.
- Analyze the response for approval after the hiring manager responds to the email. Then, based on the response, take action to send an email to the IT/procurement team to procure a laptop and set up their access.
- Wait for the IT/procurement team to confirm procurement and then email the new employee with onboarding instructions.

## Create the autonomous agent

To create a new agent in Copilot Studio:

1. On the Home screen, select **Create** in the left navigation pane. On the next page, select the **Create New Agent** box.
![Screeshot](/Labs/agent/1.svg)
2. From the Create New Agent screen, you can choose from two methods to create an agent:
    - Describe the chat window (1).
    - Create the agent manually by selecting **Skip to configure** (2).
    
    For this exercise, select **Skip to configure**.
![Screeshot](/Labs/agent/2.svg)
3. The Create New Agent screen has three fields: Name, Description, and Instructions. For this exercise, enter the following information in these fields:
    - **Name** (1) - Employee Onboarding Agent
    - **Description** (2) - An agent developed to simplify the employee onboarding process.
    - **Instructions** (3) - You are an agent responsible for employee onboarding. After you receive the onboarding request from HR, validate it and send the employee details to the hiring manager for approval. When the hiring manager approves it, forward the information to the IT and procurement teams so they can complete their respective tasks. After they finish their tasks, send the onboarding confirmation along with the onboarding instructions to the employee.
![Screeshot](/Labs/agent/3.svg)
4. Select the **Create** button to create the agent.

## Enhance agent intelligence

You can enhance the Employee Onboarding Agent that you created in the previous portion of this exercise by adding knowledge and intelligence to the agent.

1. To add generative reasoning to the agent, in the Orchestration section, turn on **Use generative AI to determine how best to respond to users and events (preview)**. This selection allows generative AI reasoning to respond to questions from different users.
![Screeshot](/Labs/agent/4.svg)
    In addition to enhancing knowledge from generative AI, you can use the Knowledge section to add your enterprise knowledge base.

2. To upload your resources and create a knowledge base, select the **Add knowledge** button to ensure that your agent has the information for accurate and efficient responses.
![Screeshot](/Labs/agent/5.svg)
3. For this exercise, create a Dataverse table with the columns from the Employee details.csv file.

4. In the Add knowledge wizard, select **Dataverse (preview)** to connect the table.
![Screeshot](/Labs/agent/6.svg)
5. On the **Step 1 of 3: Select Dataverse tables** wizard page, follow these steps to connect the table from Dataverse:
    1. In the search bar (1), search for the table named Employee Details.
    2. From the list of tables that contain Employee Details in their names, select the table that you want to connect to (2). You can select multiple tables as a knowledge source.
    3. Select **Next** to continue (3).
![Screeshot](/Labs/agent/7.svg)
6. On the **Step 2 of 3: Preview data** wizard page, follow these steps:
    1. Choose the table name from the **Select a table to review** dropdown list (1).
    2. Review the details of the selected table (2).
    3. Select **Next** to continue (3).
![Screeshot](/Labs/agent/8.svg)
7. On the **Step 3: Review and finish** wizard page, follow these steps:
    1. Name the knowledge source Employee Details (1).
    2. For the knowledge source description, enter This knowledge source answers questions found in the following Dataverse tables: Employee Details (2).
    3. Select the **Add** button to add the table as a knowledge source (3).
![Screeshot](/Labs/agent/9.svg)
8. Select **Knowledge** in the navigation bar to view resource details.
    - Select the **Add knowledge** option (1) to add more resources.
    - Under the All area, you can check the status of the added resources (2).
![Screeshot](/Labs/agent/10.svg)
## Create and configure actions

When you turn on generative orchestration, your agent can automatically choose the most suitable action or topic, or it can search through knowledge to respond to the user.

In this exercise, you have the agent manage the employee onboarding by sending an email approval to the hiring manager to onboard the new employee. Therefore, because the agent continues to take specific actions, you need to add actions to the agent.

1. Select the **+ Add Tool** option from the Overview screen to add an action.
![Screeshot](/Labs/agent/11.svg)
2. In the Add tool wizard, search for the send an email action and then select the **Send an email (V2)** connector to proceed to the next step.
![Screeshot](/Labs/agent/12.svg)
3. By default, Send an email (V2) links to the Microsoft Office 365 Outlook account that's associated with the Copilot Studio account (your organization's Office account). Select **Add and configure** to continue.
![Screeshot](/Labs/agent/13.svg)
4. In the **Name** field (1), enter Send an email to the hiring manager.

5. In the **Description for the agent to know when to use this action** field (2), enter This action sends an email to the hiring manager requesting approval for employee onboarding so that the agent knows when to trigger this action.

6. Select **Save** (3) to continue.
![Screeshot](/Labs/agent/14.svg)
For the employee onboarding use case, you need to create two more actions:

- Send an email to the IT team for approval.
- Send a final email to the employee with onboarding details.

7. Repeat the same step for Add tool to create the remaining two actions. After you create the actions, the Add tool screen displays all three actions. On the agent screen, you can turn off specific actions for the agent.
![Screeshot](/Labs/agent/15.svg)
## Create and configure the triggers

Triggers help to initiate an action based on the agent functions. In this case, you need to create triggers to:

- Initiate the onboarding process when an employee is added to the Dataverse table.
- Initiate an email to the hiring manager to onboard an employee.
- Send another email to the IT team to set up the employee's access when the agent receives the approval email.
- Send a Welcome email to the employee that includes all access details after the agent receives the completion email from the IT team.

Follow these steps to create the triggers:

1. To add a trigger to the agent, select **Add trigger** in the Triggers section of the agent's Overview tab. The Add trigger wizard opens.
![Screeshot](/Labs/agent/16.svg)
2. From the Add trigger wizard, select **When a row is added, modified or deleted**.
![Screeshot](/Labs/agent/17.svg)
3. Name the trigger When a new employee is added.
![Screeshot](/Labs/agent/18.svg)
4. From the **Change type** dropdown list (1), select **Added**.

5. From the **Table name** dropdown list (2), select the Dataverse table that you want to connect to.

6. From the **Scope** dropdown list (3), select the scope.

7. Select **Create trigger** (4).
![Screeshot](/Labs/agent/19.svg)
8. To add a trigger to the agent, select **Add trigger** in the Triggers section of the agent's Overview tab. The Add trigger wizard opens.
![Screeshot](/Labs/agent/20.svg)
9. Select **When a new email arrives (V3)** in the Add trigger wizard.
![Screeshot](/Labs/agent/21.svg)
10. In the **Trigger name** box (1), enter the trigger name as When a confirmation email arrives from IT team (V3).

11. In the sign-in section for the Microsoft Copilot Studio app (2), if a green check mark appears, it means that the app is connected. If you want to change the account, select the ellipsis (...) and then add a new account.

12. In the sign-in section for the Office 365 Outlook app (3), if a green check mark appears, it means that the app is already connected. Select the **Next** button to continue.
![Screeshot](/Labs/agent/22.svg)
13. In the Next section, you can add a trigger and an action based on a message. In the next part, you edit the trigger and add a Power Automate flow to perform the action. However, for now, leave this screen blank. Select the **Create trigger** option to create the trigger.
![Screeshot](/Labs/agent/23.svg)
14. To edit the trigger that you created, follow these steps:
    1. Select the ellipsis (...) on the When an approval email arrives (V3) trigger to open a dialog (1).
    2. Select **Edit in Power Automate** in the dialog to go to the Power Automate page (2).
![Screeshot](/Labs/agent/24.svg)
15. To set up the trigger for the agent to respond to the email from the hiring manager when the email is received, follow these steps:
    1. Select **When a new email arrives(V3)** (1).
    2. In the Subject filter section, add Onboarding request for the Employee (2).
    3. Select **Save draft** (3).
![Screeshot](/Labs/agent/25.svg)
16. To create another trigger when a confirmation email arrives from the IT team, follow these steps:
    1. Select the **Add trigger** option in the Triggers section of the agent home page to open the Add trigger wizard.
    2. Select **When a new email arrives (V3)** from the Add trigger wizard.
    3. In the **Trigger name** box (1), enter the trigger name as When a confirmation email arrives from IT team (V3). In the sign-in section for the Microsoft Copilot Studio app (2), if a green check mark appears, it means that the app is connected. In the sign-in section for the Office 365 Outlook app (3), if a green check mark appears, it means that the app is connected.
    4. Select **Next** to continue (4).
![Screeshot](/Labs/agent/26.svg)
17. To edit the created trigger:
    1. Select the ellipsis (...) to open a dialog (1).
    2. Select **Edit in Power Automate** in the dialog to go to the Power Automate page (2).
![Screeshot](/Labs/agent/27.svg)
18. To create an action based on specific messages of the event:
    1. Select **When a new email arrives (V3)** (1).
    2. In the Subject filter section (2), add Account creation request for the Employee (3).
    3. Select **Save draft** (4).
![Screeshot](/Labs/agent/28.svg)
The list of actions and triggers for the Employee Onboarding agent should display under the Actions and Triggers sections on the Overview tab.
![Screeshot](/Labs/agent/29.svg)