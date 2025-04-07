---
lab:
    title: 'Deploy agent to Microsoft Teams'
    module: 'Create an agent with Microsoft Copilot Studio and Dataverse for Teams'
---

# Deploy agent to Microsoft Teams

## Scenario

In this lab, you will:

- Create agent actions

## What you will learn

- How to deploy an agent to Microsoft Teams

## High-level lab steps

- Publish
- Deploy agent to Microsoft Teams
  
## Prerequisites

- Must have completed **Lab: Use Generative AI in Microsoft Copilot Studio**

## Detailed steps

## Exercise 1 - Publish the agent

### Task 1.1 - Publish the latest content

1. Navigate to the Microsoft Copilot Studio portal `https://copilotstudio.microsoft.com` and ensure you are in the appropriate environment.

1. Select **Agents** from the left navigation pane.

1. Select the agent you created in the earlier lab.

1. Select **Publish** and select **Publish** again.

   ![Screenshot of the publish dialog.](../media/copilot-publish.png)

   > **Note:**
   > Publishing can take a few minutes.

## Exercise 2 - Channels

With your agent published, you can make your agent available to users in Teams. This way you, your teammates, and your broader organization can interact with it.

### Task 2.1 - Microsoft Teams channel

1. With your agent open in Microsoft Copilot Studio, select the **Channels** tab.

    ![Screenshot of the channels tab.](../media/channels.png)

1. Select the **Microsoft Teams** tile.

    ![Screenshot of the Teams dialog.](../media/teams-enable.png)

1. Select **Turn on Teams**.

    ![Screenshot of the Teams channel dialog.](../media/teams-channel.png)

1. Select **Availability options**.

    ![Screenshot of the Teams channel availability options.](../media/teams-availability-options.png)

1. Selecy **Copy link**.

1. Select **Show to my teammates and shared users**.

1. Select your user.

1. Select the back arrow in the top-left of the pane.

1. Select **Share**.

### Task 2.2 - Microsoft Teams

1. Go to Microsoft Teams `https://teams.microsoft.com` in a new tab.

1. Sign in to Teams if prompted.

1. Select **Teams** in the left navigation.

1. You will see a Team named **Contoso** with a **General** channel.

1. Open a new tab and go to the URL link copied in the previous task.

1. Select **Cancel** in the dialog box for **This site is trying to open Microsoft Teams**.

1. Select **Use the web app instead**.

1. Select **Add**.

    ![Screenshot of dialog to add the app to Teams.](../media/teams-add-app.png)

1. Test the agent.

    ![Screenshot of the agent in Teams.](../media/teams-copilot.png)
