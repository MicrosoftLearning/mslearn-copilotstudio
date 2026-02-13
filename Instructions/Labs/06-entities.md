---
lab:
    title: 'Work with entities'
    module: 'Work with entities and variables in Microsoft Copilot Studio'
---

# Work with entities

## Scenario

In this exercise, you will:

- Create and use entities

This exercise will take approximately **15** minutes to complete.

## What you will learn

- How to use entities with generative AI
- How entities turn free-form input into structured variables

## High-level lab steps

- Create entities
- Use entities in nodes
  
## Prerequisites

- Must have completed **Lab: Manage nodes**

## Detailed steps

## Exercise 1 - Create a Property Type entity

Microsoft Copilot Studio uses entities to understand user intent. There are many prebuilt entities included for commonly used information. You can create custom entities for your specific purpose.

### Task 1.1 - View prebuilt entities

1. Navigate to the Microsoft Copilot Studio portal `https://copilotstudio.microsoft.com` and ensure you are in the appropriate environment.

1. Select **Agents** from the left navigation pane.

1. Select the **Real Estate Booking Service** agent you created in the earlier lab.

1. Select **Settings** in the upper-right of the screen.

1. Select the **Entities** tab. You should see a list of the prebuilt entities for your agent.

    ![Screenshot of the Entities tab.](../media/system-entities.png)

### Task 1.2 - Create the Property Type entity

1. Select **+ Add an entity** and select **+ New entity**.

    ![Screenshot of the selecting the method for a new entity.](../media/add-an-entity.png)

1. Select **Closed list**.

1. Enter **`Property Type`** in the **Name** field.

1. Enter **`Apartment`** in the **Enter item** field and select **Add**.

1. Enter **`Condominium`** in the **Enter item** field and select **Add**.

1. Enter **`Duplex`** in the **Enter item** field and select **Add**.

1. Enter **`House`** in the **Enter item** field and select **Add**.

1. Select **+ Synonyms** for **Apartment**, enter **`Flat`** and select the **+** icon and select **Done**.

1. Select **+ Synonyms** for **Condominium**, enter **`Townhouse`** and select the **+** icon and select **Done**.

1. Select **+ Synonyms** for **House**, enter **`Single-family home`** and select the **+** icon and select **Done**.

1. Enable **Smart matching**.

    ![Screenshot of the a new entity.](../media/add-list-entity.png)

1. Select **Save**.

1. Once the entity is saved, close the Property Type window.

### Task 1.3 - Create number of bedrooms entity

1. Select **+ Add an entity** and select **+ New entity**.

1. Select the **Regular expression (Regex)** tile.

1. Enter **`Number of Bedrooms`** in the **Name** field.

1. Enter **`[1-5]`** in the **Pattern** field.

1. Select **Save**.

1. Once the entity is saved, close the Number of Bedrooms pane.

1. Select the **X** icon in the top-right to close out of Settings and return to your agent.

## Exercise 2 - Use entities to improve the agent

Use entities in the conversational flow to improve the agent.

### Task 2.1 - Use entities

1. Select the **Topics** tab.

1. Select the **Book Showing** topic.

1. Select the the **+** icon between the **Condition** and property **Question** nodes, then select **Ask a question**.

1. In the **Enter a message** field, enter the following text:

    `What type of property do you want to see?`

1. Select **Property Type** for **Identify**.

1. Select **Select options for user** and check the **Display** option for all four values.

1. Select the variable in **Save user response as** and enter **`PropertyType`** for **Variable name**

    ![Screenshot of the a new entity.](../media/question-node-entity.png)

1. Select the the **+** icon below the new **Question** node and select **Ask a question**.

1. In the **Enter a message** field, enter the following text:

    `How many bedrooms do you need?`

1. Select **Number of Bedrooms** for **Identify**.

1. Select the variable in **Save user response as** and enter **`NumberofBedrooms`** for **Variable name**

1. Select **Save**.

### 2.2 - Test entity extraction

1. Open the **Test** panel.

1. Enable **Track between topics**.

1. Start a new test session.

1. When the Conversation Start message appears, type and send `I want to book a real estate showing`.

1. Confirm that the agent responds with the greeting message from the **Book Showing** topic.

1. Provide a name and email address when prompted and confirm the information.

1. When asked which type of property you want to see, enter `I'm looking for a house`.

    > This response is intentionally using natural language. The **Property Type** entity should capture **House**.

1. When asked which property you want to see, enter `555 Oak Lane, Denver, CO 80203`.

1. When asked what date and time you want to see the property, enter `Tomorrow 8:00 AM`.

Confirm that the agent responds with the message indicating the booking request is being scheduled.

### 2.3 - Validate the results
In this task, you will confirm that the Property Type entity successfully captured a structured value from natural language input.

1. In the **Test your agent** panel, look at the conversation transcript.

1. Select the message corresponding to your response: I'm looking for a house.

1. In the right-hand side of the test panel, expand the **Variables** section (you may need to scroll).

1. Locate the **PropertyType** variable and confirm that its value is set to **House**.

This confirms that the Property Type entity extracted a structured value from natural language input.

## Summary

In this lab, you used entities to extract structured values from natural language while keeping generative AI enabled. Entities allow your agent to accept flexible input while maintaining predictable behavior.

In the next lab, you will use tools to act on these structured values and perform real operations, such as retrieving or creating data.
