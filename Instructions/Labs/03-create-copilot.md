---
lab:
    title: 'Build an initial agent'
    module: 'Manage topics in Microsoft Copilot Studio'
---

# Build an initial agent

## Scenario

In this exercise, you will:

- Create and name an agent
- Add description for what the agent should do
- Configure Generative AI answers

This exercise will take approximately **15** minutes to complete.

## What you will learn

- How to create an agent using natural language
- How to configure Generative AI answers for an agent

## High-level lab steps

- Create a new agent
- Tell your agent what its primary purpose is and how it should act
- Add Generative AI instructions
  
## Prerequisites

- Must have completed **Lab: Import Dataverse solution**

## Exercise 1 - Create agent

In this exercise, you will access the Microsoft Copilot Studio portal, the Developer environment and create a new agent.

### Task 1.1 – Create an agent in the Bookings solution

1. In a new browser tab, navigate to `https://copilotstudio.microsoft.com`.

1. Make sure that you are in the appropriate environment.

1. Select **Agents** in the left navigation.

1. Select the arrow next to **Create blank agent** \> **Advanced create**.

1. Update the **Solution** to **Bookings**

1. Enter `labagent` for **Schema Name**.

1. Select **Confirm and create**.

> **Note:** if **Confirm and create** is grayed out once you delete the originally proposed schema name, close the popup and repeat the steps above. While trying to update the schema name, select the proposed one instead of deleting it, and overwrite it with `labagent`.

### Task 1.2 – Configure your agent

1. In the **Details** section, select **Edit**

1. In the **Name** text box, enter **`Real Estate Booking Service`**

1. In the **Description** text box, enter **`Create bookings for real estate properties`**

1. Select **Save**.

1. In the **Instructions** section, select **Edit**

1. Update the instructions to **`Create an agent for topics relating to creating bookings for real estate properties`** and **Save**.

1. In the right **Test your agent** pane, enter **`How do I make a booking?`** and view the response.

Leave this window open.

## Exercise 2 - Add Generative AI answers

In this exercise, you will access the Microsoft Copilot Studio portal and add knowledge that the agent will use to answer questions by using Generative AI.

### Task 2.1 - Disable generative orchestration

1. Select **Settings**.

1. For **Use generative AI orchestration for your agent's responses?** select **No - Use classic orchestration, limiting responses to the content and behavior defined in your agent's topics**. This turns Orchestration off for the purpose of this lab.

1. Select **Save**.

1. Close out of the Settings window.

### Task 2.2 – Add a knowledge source

1. Select the **Knowledge** tab.

    ![Knowledge tab in Copilot Studio portal.](../media/knowledge-tab.png)

1. Select **+ Add knowledge**.

1. Select **Public websites**

1. In the **Public website link** text box, enter **`https://word.cloud.microsoft/en/create`**. This public website has many templates for marketing materials that could be useful for your agent.

1. Select **Add**.

1. Select **Add to agent**.

> ### ⚠️ Important: Enable Web Search 
> **Please ensure that the _"Web Search"_ feature is turned on.** 

1. Select the **Overview** tab.

1. Select the **ellipses …** menu at the top of the **Test your agent** pane.

1. Enable **Track between topics**.

    ![Screenshot of the Testing panel options.](../media/test-pane-options.png)

1. At the top of the **Test your agent** pane, select the  **Start new test session** icon.

    ![Screenshot of the Testing panel options.](../media/copilot-test-pane-start-new-conversation.png)

1. In the **Ask a question or describe what you need** text box, enter **`How do I boost real estate promotion?`** View your response.

    ![Screenshot of the Testing panel results.](../media/test-pane-results.png)
