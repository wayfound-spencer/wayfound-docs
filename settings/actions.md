# Actions

Actions enhance the functionality of your agents by enabling them to interact with other systems. You can add an individual agent's actions using the [actions.md](../agents/actions.md "mention") page in the Agents tab, where all available actions are listed.

Users with admin level permissions can add or remove the actions available to agents in their organization. They can do so in the Actions page in the Settings tab:

<figure><img src="../.gitbook/assets/Screenshot 2024-10-07 at 10.59.06 AM.png" alt=""><figcaption></figcaption></figure>

### Creating Actions

Some actions come pre-built with Wayfound, while others can be built by users using a custom action. Both kinds of actions can be made by selecting the corresponding button at the top of the tab. Note that if a pre-made action has already been added, the corresponding button will no longer activate; instead, it will appear in the **Available Actions** table.

**Pre-built Actions**

Some pre-made actions require an account with a third-party service. If you have not yet authenticated the required third-party account information on Wayfound, creating a pre-made action will direct you to the Authentication page, where you can sign into the third-party service. Once you have authenticated your account on Wayfound, you can return to the Actions page and add the action.

**Custom Actions**

Creating a new custom action opens a new window:

<figure><img src="../.gitbook/assets/Screenshot 2024-10-07 at 11.00.31 AM.png" alt=""><figcaption></figcaption></figure>

This window allows you to define the custom action's function and HTTP request. These windows are pre-filled with an example and can be changed to create your own action. Note that Wayfound does not currently support custom actions that require OAuth; it does, however, allow the use of API tokens. When creating a custom action with a third-party API, you may need to consult with the third-party API's corresponding documentation.

Note: admins are given full control over naming new actions. We recommend using names that fully but succinctly describe the purpose of the action. For consistency and clarity, we also recommend beginning names with verbs (e.g., "Send Email," "Create Jira Ticket").

### Managing Actions

Once an action is created, it will appear in the **Available Actions** table. You can update the description by clicking on the action name. You can delete the action by clicking the <img src="../.gitbook/assets/Screenshot 2024-10-03 at 10.22.50 AM (1).png" alt="" data-size="line">delete button on the right side of table.

