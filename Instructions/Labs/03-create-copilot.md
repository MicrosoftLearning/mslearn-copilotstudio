---
lab:
    title: 'Build an initial agent'
    module: 'Manage topics in Microsoft Copilot Studio'
---

# Build an initial agent

## Scenario

In this exercise, you will:

- Create and name an agent
- Define how the agent should behave using instructions
- Configure Generative AI answers

This exercise will take approximately **15** minutes to complete.

## What you will learn

- How to create an agent using natural language
- How agent instructions influence generative behavior
- How Generative AI answers work with configured knowledge

## High-level lab steps

- Create a new agent
- Define agent behavior using instructions
- Add Generative AI knowledge sources
  
## Prerequisites

- Must have completed **Lab: Import Dataverse solution**

## Exercise 1 - Create agent

In this exercise, you will access the Microsoft Copilot Studio portal, select the appropriate environment, and create a new agent.

### Task 1.1 – Create an agent in the Bookings solution

1. In a new browser tab, navigate to `https://copilotstudio.microsoft.com`.

1. Make sure that you are in the appropriate environment.

1. Select **Agents** in the left navigation.

1. Select the arrow next to **Create blank agent** \> **Advanced create**.

1. Update the **Solution** to **Bookings**

1. Enter `labagent` for **Schema Name**.

1. Select **Confirm and create**.

    > **Note:** if **Confirm and create** is grayed out once you delete the originally proposed schema name, close the popup and repeat the steps above. While trying to update the schema name, select the proposed one instead of deleting it, and overwrite it with `labagent`.

### Task 1.2 – Configure agent details and instructions

1. In the **Details** section, select **Edit**

1. In the **Name** text box, enter **`Real Estate Booking Service`**

1. In the **Description** text box, enter **`Create bookings for real estate properties`**

1. Select **Save**.

1. In the **Instructions** section, select **Edit**

1. Update the instructions to:

    ```prompt
    You are a real estate booking assistant.
    Help users with questions related to real estate properties and booking showings by using the knowledge and data that are available to you.

    When responding:
    Use the information provided through your configured knowledge sources whenever possible.
    If a user’s request is unclear or missing required details, ask a follow‑up question to gather the information you need.
    If you do not have enough information to answer confidently, do not guess. Instead, explain what information is missing or guide the user to provide it.
    
    Keep responses clear, helpful, and focused on assisting the user with booking‑related tasks.
    ```

1. **Save** the instructions.

    > **Note**: Agent instructions guide how the agent should behave, but they do not strictly enforce behavior.
In later labs, you will learn how to make this behavior predictable by using topics, generative answers with restricted knowledge sources, and fallback configuration

1. In the right **Test your agent** pane, enter **`How do I make a booking?`** and view the response.

Leave this window open.

## Exercise 2 - Add Generative AI answers

In this exercise, you will add knowledge that the agent can use to generate responses.

### Task 2.1 - Add a knowledge source

1. Select the **Knowledge** tab.

    ![Knowledge tab in Copilot Studio portal.](../media/knowledge-tab.png)

1. Select **+ Add knowledge**.

1. Select **Public websites**

1. In the **Public website link** text box, enter **`https://word.cloud.microsoft/en/create`**. This public website has many templates for marketing materials that could be useful for your agent.

1. Select **Add**.

1. Select **Add to agent**.

### Task 2.1 - Test Generative AI responses

1. Select the **Overview** tab.

1. Select the **ellipses …** menu at the top of the **Test your agent** pane.

1. Enable **Track between topics**.

    ![Screenshot of the Testing panel options.](../media/test-pane-options.png)

1. At the top of the **Test your agent** pane, select the  **Start new test session** icon.

    ![Screenshot of the Testing panel options.](../media/copilot-test-pane-start-new-conversation.png)

1. In the **Ask a question or describe what you need** text box, enter **`How do I boost real estate promotion?`** View your response.

    ![Screenshot of the Testing panel results.](../media/test-pane-results.png)


## Summary
In this lab, you created an agent and defined its expected behavior using instructions. While these instructions guide generative responses, later labs will show how to enforce predictable behavior using topics, entities, tools, and fallback configuration
