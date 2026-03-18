---
lab:
  title: Use Generative AI in Microsoft Copilot Studio
  module: Enhance Microsoft Copilot Studio agents
  description: 'In this lab, you actively configured generative AI behavior for production readiness by:'
  duration: 120 minutes
  level: 100
  islab: true
  primarytopics:
    - Microsoft Copilot
    - Microsoft Copilot Studio
---

# Use Generative AI in Microsoft Copilot Studio

## Scenario

In this lab, you will prepare your agent for production use by configuring grounding, fallback behavior, and safety controls while keeping generative AI enabled.

In this exercise, you will:

- Configure your agent to use generative AI only within approved knowledge sources
- Guide your agent to respond predictably and safely when it cannot answer a question

This exercise will take approximately **20** minutes to complete.

## What you will learn

- How to constrain generative AI using grounding
- How to configure system topics for safe fallback behavior
  
## Prerequisites

- Must have completed **Lab: Create agent flows**

## Detailed steps

## Exercise 1 - Configure authentication

### Task  - Configure authentication

1. If it's not still open, go to the Microsoft Copilot Studio portal `https://copilotstudio.microsoft.com` and ensure you are in the appropriate environment.

1. Open the **Real Estate Booking Service** agent.

1. Select **Settings** in the upper-right of **Real Estate Booking Service**.

1. Select the **Security** tab.

1. Select **Authentication**.

    ![Screenshot of the authentication settings.](../media/configure-authentication.png)

1. Select **Authenticate with Microsoft**.

1. Select **Save**.

1. Select **Save** in the confirmation window.

1. Select the **X** in the upper-right to close out of the **Settings**.

1. Select **Publish**.

## Exercise 2 - Ground generative answers to approved data

In this exercise, you will configure generative answers so the agent can only respond using approved knowledge.

### Task 2.1 - Restrict generative answers in Conversational boosting

1. Select **Topics**

1. Filter by **System** topics.

1. Open the **Conversational boosting** topic.

1. Select the **Create generative answers** node.

1. Select **Edit** for **Data sources**.

1. Select **Search only selected sources.**

1. Select **Add knowledge**.

1. Select the **Real Estate Property** Dataverse table and **Add to agent**.

1. Check both the **website** and the **Real Estate Property** table as the knowledge sources.

1. Scroll down and disable **Allow the AI to use its own general knowledge**.

1. Select **Save**.

The agent can no longer answer open-ended questions using general model knowledge.

## Exercise 3 - Replace default fallback with a grounded fallback
In this exercise, you will reconfigure the system fallback behavior.

### Task 3.1 - Use generative answers in System fallback topic

1. Select the **Topics** tab and select the **System** filter.

1. Select the **Fallback** topic.

    ![Screenshot of the system fallback topic nodes.](../media/fallback-topic-original.png)

1. Select the **ellipses (...)** menu in the **Message** node and select **Delete**.

1. Select the the **+** icon under the **Condition** node, select **Advanced** \> **Generative answers**.

1. In the **Input** field, select the **System** tab and select **Activity.Text**.

1. Select **Edit** under **Data sources**.

    ![Screenshot of the create generative answers node.](../media/fallback-topic-answers-2.png)

1. Select **Search only selected sources**.

1. Add the **website** and the **Real Estate Property** Dataverse table.

1. Scroll down and disable **Allow the AI to use its own general knowledge**.

1. Select the **Customize** checkbox under **Content moderation level** and select **Medium**.

1. Select **Save**.

When an agent cannot answer a question, it will respond safely using grounded data instead of guessing.

## Task 3.2 - Add a controlled fallback response

1. In the Fallback topic, add a **Send a message** node after the Generative answers node.

1. Enter the following message: `Sorry, I don’t have enough information to help with that request. I can assist with booking real estate showings or questions related to available properties.`

1. Select **Save**.

The agent now communicates scope and limitations clearly instead of generating ambiguous responses. Note that the Fallback topic only triggers when the agent cannot confidently select any topic of generative answer path. The Fallback topic is only for unknown intent.

## Exercise 4 - Validate production behavior through action
In this exercise, you will ask your agent questions that are both inside and outside of its scope of knowledge.

### Task 4.1 - Trigger a supported scenario

1. Open the **Test** panel.

1. Start a new test session.

1. Ask a question that is supported by your configured knowledge, such as `Is there a property on Oak Lane?`

The agent should respond using grounded, approved data.

### Task 3.2 - Trigger an unsupported scenario

1. In the same test session, ask a question outside the agent's scope, such as `What's for dinner?`

The agent should avoid guessing at an answer.

## Summary

In this lab, you actively configured generative AI behavior for production readiness by:

- Grounding generative answers to approved data
- Replacing default fallback behavior
- Enforcing safe, scoped responses

### Challenge - Add knowledge from a file

For an added challenge, add a file as an additional knowledge source for your agent. Ensure that it is also added for Conversational boosting.

To download the file: open a new window and navigate to `https://download.microsoft.com/documents/customerevidence/Files/4000007499/SummitRealtyCaseStudy.docx`


