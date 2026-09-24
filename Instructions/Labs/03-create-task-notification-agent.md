---
lab:
  title: Create a task notification agent and workflow
  module: Automate agent tasks with workflows in Microsoft Copilot Studio
  description: Create a workflow that sends task notification emails, add it to an agent as a tool, and test success, missing-information, cancellation, and failure paths.
  duration: 55 minutes
  level: 200
  islab: true
  primarytopics:
    - Microsoft Copilot Studio
    - Workflows
---

## Scenario

In this exercise, you create the **Contoso Task Alert Agent**, a standalone workflow that sends task notification emails, add the workflow to the agent as a tool with end-user confirmation, and run all four required test paths.

This exercise takes approximately **55 minutes** to complete.

## What you'll learn

- How to create a standalone workflow for an agent.
- How to define workflow inputs and outputs.
- How to add and configure a workflow as an agent tool.
- How to test success, missing-information, cancellation, and failure paths.

## High-level lab steps

- Create and configure an agent.
- Build and publish a task notification workflow.
- Add the workflow to the agent as a tool.
- Test the agent and workflow.
- Review the configuration and clean up resources.

## Prerequisites

To complete this exercise, you need:

- A Microsoft Entra work or school account.
- [Access to Microsoft Copilot Studio](https://learn.microsoft.com/microsoft-copilot-studio/requirements-licensing-subscriptions).
- Permission to create an agent in a Power Platform environment.
- A Microsoft 365 account with an Outlook mailbox. The Outlook connection uses this account to send email.
- Access to a solution in the environment if your organization requires agents and workflows to be created in a solution.

> [!NOTE]
> Building and testing an agent powered by the GitHub Copilot harness might consume Copilot Credits.

## Exercise 1 - Create the agent

### Task 1.1 - Create and configure the Contoso task alert agent

1. Go to [Microsoft Copilot Studio](https://copilotstudio.preview.microsoft.com/) at `https://copilotstudio.preview.microsoft.com/` and sign in.

1. Confirm that the correct environment is selected.

1. On the **Home** page, select **Agent**. Alternatively, select **Agents** in the left navigation, and then select **New agent**.

1. In the **Name** field, enter `Contoso Task Alert Agent <your initials>`. Replace `<your initials>` with your initials or another unique value.

1. If your organization requires a solution, in the upper-right corner, select **More options** (**...**), and then select **Settings**. In **Agent settings** > **Agent details**, select the solution provided for the exercise from the **Solution** list.

1. In **Instructions**, enter the following text:

   ```prompt
   You are the Contoso Task Alert Agent. You help operations team members send task notification emails.

   ## Your role

   - Help users send task notification emails with consistent, accurate content.
   - Answer questions about the notification process.
   - Do not send a notification unless the user explicitly asks you to.

   ## When a user asks to send a task notification

   1. Identify the following required details from the conversation:
      - Complete work or school email address
      - Task title
      - Task details or description
      - Due date

   2. If any required detail is missing, ask the user for it before proceeding.

   3. Summarize the notification details for the user and ask them to confirm before sending.

   4. When the user confirms, use the Send task notification email tool to send the notification.

   5. After the workflow runs, relay the confirmation to the user.

   ## Boundaries

   - Do not guess or infer the recipient email address. Always confirm it with the user.
   - Do not send notifications to multiple recipients in a single workflow call.
   - If the user cancels at any point, acknowledge the cancellation and do not send the email.
   ```

1. Select **Save**.

## Exercise 2 - Create the workflow

### Task 2.1 - Create the send task notification email workflow

1. In the left navigation, select **Workflows**.

1. Select **New workflow**.

1. Select the **Start** trigger on the canvas.

1. On the right panel, set **Trigger type** to **When an agent calls the workflow**. Confirm that the canvas contains both the **When an agent calls the workflow** trigger and the connected **Respond to the agent** action. If the response action is missing, add **Respond to the agent** after the trigger.

### Task 2.2 - Rename the workflow

1. Select the **Workflow name** on the top left of the designer canvas.

1. For **Workflow name**, enter:

   ```text
   Send Task Notification Email <your initials>
   ```

   Replace `<your initials>` with a unique identifier, such as your initials. For example: `Send Task Notification Email CS`.

1. Select **Save**.

1. Continue working on the workflow canvas.

### Task 2.3 - Configure the trigger inputs

1. Select the **When an agent calls the flow** trigger to open its configuration panel on the right side of the designer canvas.

1. Select **+ Add an input** and configure the first input:

   | Field | Value |
   | --- | --- |
   | Type | **Text** |
   | Input name | `Recipient Email` |
   | Description | `The complete work or school email address of the person who should receive the task notification. Do not guess or infer this value.` |

1. Select **+ Add an input** and configure the second input:

   | Field | Value |
   | --- | --- |
   | Type | **Text** |
   | Input name | `Task Title` |
   | Description | `The short title of the task that the notification is about.` |

1. Select **+ Add an input** and configure the third input:

   | Field | Value |
   | --- | --- |
   | Type | **Text** |
   | Input name | `Task Details` |
   | Description | `A brief description of what the task involves, including any relevant context.` |

1. Select **+ Add an input** and configure the fourth input:

   | Field | Value |
   | --- | --- |
   | Type | **Text** |
   | Input name | `Due Date` |
   | Description | `The due date of the task, stated as the user provided it, such as October 15, 2026.` |

1. Select **Save** to save your progress.

### Task 2.4 - Add the send an email (V2) action

1. Select the **+** icon between the **When an agent calls the flow** step and the **Respond to the agent** step to insert a new action.

1. In the search field, enter `Send an email`.

1. From the results, select the **Send an email** (it may also appear as **Send an email (V2)**) action under the **Office 365 Outlook** connector.

   If this is the first time you use this connector, Copilot Studio prompts you to sign in. Sign in with the Microsoft 365 account that has the Outlook mailbox you want to use for sending notifications.

   > [!NOTE]
   > If a browser pop-up is blocked, allow pop-ups from `https://copilotstudio.preview.microsoft.com` and then select sign in again.

1. In the **To** field, select the **Insert dynamic content** icon and select **Recipient Email**.

1. In the **Subject** field, enter the following, inserting dynamic content where indicated:

   ```text
   Task notification: [Task Title]
   ```

   To compose this:

   - Type `Task notification:` followed by a space as static text.
   - In the **Subject** field, select the **Insert dynamic content** icon (lightning bolt) to open the dynamic content panel.
   - Under **When an agent calls the flow**, select **Task Title**.

1. In the **Body** field, compose the following email body. Use static text for the labels and dynamic content references for the values:

   ```text
   Task notification

   Task: [Task Title]
   Details: [Task Details]
   Due date: [Due Date]

   This notification was sent by the Contoso Task Alert Agent.
   ```

   To compose this:

   - Enter `Task notification` on the first line, then add a blank line.
   - Enter `Task:` followed by a space and insert the **Task Title** dynamic content.
   - Enter `Details:` followed by a space and insert the **Task Details** dynamic content.
   - Enter `Due date:` followed by a space and insert the **Due Date** dynamic content.
   - Add a blank line, then enter the closing text as static text.

1. Leave all other fields at their default values.

1. Select **Save**.

### Task 2.5 - Configure the response outputs

1. Select the **Respond to the agent** step to open the configuration panel.

1. Select **+ Add an output** and configure the first output:

   | Field | Value |
   | --- | --- |
   | Type | **Text** |
   | Output name | `Status` |
   | Output value | Enter the static text: `Email sent` |

1. Select **+ Add an output** and configure the second output:

   | Field | Value |
   | --- | --- |
   | Type | **Text** |
   | Output name | `Confirmation` |
   | Output value | Combine `Task notification sent to:` followed by a space with the **Recipient Email** dynamic content reference from the trigger inputs. |

1. In the **Respond to the agent** configuration panel, select **More options (...)**, and then select **Settings**.

1. Expand **Networking** and confirm that **Asynchronous response** is set to **Off**. If it is on, turn it off so the workflow waits for the response outputs and returns them to the agent in real time.

1. Select **Save**.

### Task 2.6 - Publish the workflow

1. Select **Publish** in the upper-right corner of the workflow designer.

1. Wait for the publishing process to complete.

1. Return to the **Workflows** list by selecting **Workflows** in the left navigation.

1. Verify that the workflow you created shows a status of **Published**.

   If the status shows **Error**, select the workflow and review the error details before continuing.

## Exercise 3 - Add and configure the workflow tool

### Task 3.1 - Add the workflow as a tool

1. Select **Agents** in the left navigation and open the **Contoso Task Alert Agent** you created in Exercise 1.

1. On the **Build** tab, select the **Tools** section of the components panel to open the **Add a tool** dialog.

1. In the **Add tool** dialog, select the **Workflows** filter.

1. Select the **Send Task Notification Email** workflow that you published. Confirm the name matches the one you created.

1. In the **Tools** section, select the workflow to open its configuration panel.

### Task 3.2 - Configure the tool name and description

1. In the **Name** field, verify or update the name to:

   ```text
   Send task notification email
   ```

1. In the **Description for AI** field, enter:

   ```text
   Sends a formatted task notification email to a specified recipient. Use when the user asks to send a notification about a task and all required details are available and confirmed: recipient email, task title, task details, and due date.
   ```

### Task 3.3 - Configure the inputs

In the **Inputs** section, configure each input:

1. For **Recipient Email**, confirm the description reads: `The complete work or school email address of the person who should receive the task notification. Do not guess or infer this value.`

1. For **Task Title**, confirm the description reads: `The short title of the task that the notification is about.`

1. For **Task Details**, confirm the description reads: `A brief description of what the task involves, including any relevant context.`

1. For **Due Date**, confirm the description reads: `The due date of the task, stated as the user provided it, such as October 15, 2026.`

### Task 3.4 - Configure the workflow outputs

1. On the **Outputs** tab, review the workflow outputs.

1. Verify that the workflow includes the **Status** and **Confirmation** output parameters.

   The agent uses the `Status` and `Confirmation` outputs to compose a natural confirmation response.

### Task 3.5 - Save the configuration

1. Select **Save** to apply the tool configuration.

1. Make sure you are on the **Build** tab to update the agent instructions.

### Task 3.6 - Reference the tool in agent instructions

1. In the **Instructions** section, locate the line that reads:

   ```text
   4. When the user confirms, use the Send task notification email tool to send the notification.
   ```

1. Place your cursor on `Send task notification email` and replace it with the exact name of the connected tool: **Send Task Notification Email**.

1. Select **Save**.

## Exercise 4 - Test the agent and workflow

Open the **Preview** tab in Copilot Studio. Use the following tasks to run all four test paths.

### Task 4.1 - Test the success path

1. At the top of the **Preview** pane, start a new conversation session.

1. Enter the following message exactly. Replace `<your email address>` with your own work or school email address.

   ```prompt
   Send a task notification to <your email address> for the task "Server Patch Update." The task involves applying monthly security patches to production servers. It's due October 15, 2026.
   ```

   **Expected behavior**:

   - The agent extracts the recipient email, task title, task details, and due date from the message.
   - The agent presents the confirmation prompt you configured.

1. Approve the confirmation when prompted.

   **Expected behavior after approval**:

   - The agent calls the workflow.
   - The workflow runs the **Send an email** action.
   - The agent responds with a confirmation that uses the `Status` and `Confirmation` outputs.

1. Verify success by checking the inbox of the email account you specified as the recipient. Confirm:

   - The subject line reads `Task notification: Server Patch Update`.
   - The body contains the task title, task details, and due date.
   - The closing line reads `This notification was sent by the Contoso Task Alert Agent.`

**Completion criteria for Task 4.1**: The email arrives with the correct subject, body, and formatting, and the agent confirms the action in the conversation.

### Task 4.2 - Test the missing-information path

1. Start a new conversation session in the **Preview** tab.

1. Enter the following message:

   ```text
   Send a notification for the task "Backup Validation."
   ```

   **Expected behavior**:

   - The agent recognizes that required information is missing.
   - The agent asks for the missing inputs, including the recipient email address and due date.

1. Provide each piece of missing information as the agent asks for it. Use these values:

   - **Task title**: `Backup Validation.`
   - **Recipient email**: Your own work or school email address.
   - **Task details**: `Verify that nightly backups completed successfully and review the backup logs.`
   - **Due date**: `October 20, 2026`

1. When the agent presents the confirmation prompt, approve it.

   **Expected behavior after approval**:

   - The workflow runs and the email is sent.
   - The agent confirms the action.

**Completion criteria for Task 4.2**: The agent asks for missing inputs rather than guessing or skipping them, and the workflow runs successfully after all required information is provided.

### Task 4.3 - Test cancellation at the confirmation prompt

1. Start a new conversation session in the **Preview** tab.

1. Enter the following message. Replace `<your email address>` with your own work or school email address.

   ```text
   Send a task notification to <your email address> for "Access Review." The task involves reviewing and removing inactive user accounts. It's due November 1, 2026.
   ```

1. When the agent presents the confirmation prompt, decline it by entering:

   ```text
   Cancel, don't send the email.
   ```

   **Expected behavior**:

   - The agent acknowledges the cancellation.
   - No email is sent.
   - The agent remains ready for the next message in the same conversation.

1. Verify that no email arrives. Open the workflow's **Activity** tab and confirm that cancellation didn't create a workflow run.

**Completion criteria for Task 4.3**: The agent cancels cleanly, does not send the email, and remains responsive in the conversation.

### Task 4.4 - Test a controlled failure path

This test runs the workflow directly with a deliberately malformed email address. You then inspect the **Activity** panel to understand the failure.

> [!NOTE]
> This test intentionally produces a failure. The purpose is to practice using workflow activity to diagnose problems. No real email is sent to a real address.

1. In the left navigation pane, select **Workflows**, and then select the **Send Task Notification Email** workflow to open it in the workflow designer. On the top of the page, select **Run** (**▶**) from the command bar.

1. Enter these test values:

   | Input | Value |
   | --- | --- |
   | Recipient Email | `not-an-email` |
   | Task Title | `Incident Report` |
   | Task Details | `Document the root cause of a recent service outage.` |
   | Due Date | `November 5, 2026` |

1. Select **Run**. The workflow encounters an error at the **Send an email (V2)** step because `not-an-email` isn't a valid address.

1. After the failed attempt, inspect the workflow activity:

   1. In the workflow designer, open the **Activity** tab.
   1. Filter the runs by **Failed**.
   1. Select the most recent failed run to load its step details on the canvas.
   1. Identify the step that failed (the **Send an email** action) and read the error message.

   **What to look for**:

   - The **Recipient Email** input received `not-an-email`, which confirms the workflow test used the value you entered.
   - The **Send an email** step shows a validation or delivery error because the address is malformed.
   - All preceding steps, including the trigger, ran without error.

1. Note the error type and the step that failed. This is the information you use to decide whether to add input validation, update the input description, or adjust the confirmation prompt.

1. Restore normal operation by returning to the agent's **Preview** tab, starting a new conversation, and completing the success path test again with your own email address.

**Completion criteria for Task 4.4**: You can locate the failed run in the **Activity** panel, identify the step that failed, and read the error details.

## Exercise 5 - Verify and reflect

### Task 5.1 - Review the full configuration

After completing all four test paths, review the configuration as a whole:

1. Open the agent's **Build** tab and select the **Send Task Notification Email** tool.
1. Confirm the tool description accurately reflects what the workflow does and when to use it.
1. Confirm **AI** is selected under **How is this filled?** for all four inputs.
1. Confirm the confirmation prompt is clear and informative.

### Task 5.2 - Optional: Refine based on test results

If any test path revealed a problem, such as the agent guessing the recipient email instead of asking or presenting an unclear confirmation prompt, make one targeted change and retest the affected path.

Common refinements:

- **Agent guessed the recipient email**: Update the **Recipient Email** input description to include: `Do not guess or infer this value; ask the user if it is not provided.`
- **Confirmation prompt was unclear**: Update the prompt to show the specific values the workflow uses, such as the recipient address and task title.
- **Agent didn't select the tool**: Review the tool description and the agent instructions. The description may be too vague or may not match the language users are likely to use.

## Clean up

After completing the exercise, remove the assets you created to keep your environment tidy.

1. **Remove the workflow from the agent**:

   - Open the agent, select the **Build** tab, select **Tools**, find the **Send Task Notification Email** tool, and remove it.

1. **Delete the workflow**:

   - In the left navigation, select **Workflows**.
   - Select the ellipsis (**...**) next to the **Send Task Notification Email** workflow you created.
   - Select **Delete** and confirm the deletion.

1. **Delete the agent**:

   - In the left navigation, select **Agents**.
   - Find the **Contoso Task Alert Agent** you created, select the ellipsis (**...**) next to it, and select **Delete**.
   - Confirm the deletion.

> [!NOTE]
> Deleting the workflow before removing it from the agent may show an error. Remove the workflow from the agent first, then delete the workflow.
