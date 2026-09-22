---
lab:
  title: Evaluate and publish a support agent
  module: Evaluate, publish, and manage agents in Microsoft Copilot Studio
   description: Connect a specialist agent, evaluate delegation, correct an instruction defect, publish the main agent, and validate its behavior in Microsoft Teams.
   duration: 55 minutes
  level: 200
  islab: true
  primarytopics:
    - Microsoft Copilot Studio
    - Agents
---

## Scenario

In this exercise, you create the **Contoso Policy Agent** and a specialized escalation agent. You connect the agents, evaluate delegation with a structured set of test conversations, correct one deliberate instruction defect, publish the main agent to Microsoft Teams and Microsoft 365 Copilot, and validate its behavior as a published user.

This exercise takes approximately **55 minutes** to complete.

## What you learn

- How to create and run a repeatable agent evaluation.
- How to connect a specialist agent and test delegation boundaries.
- How to diagnose and correct an instruction defect.
- How to publish an agent to Microsoft Teams and Microsoft 365 Copilot.
- How to validate agent behavior as a published user.

## High-level lab steps

- Create and configure a support policy agent and an escalation specialist.
- Connect the specialist to the main agent.
- Create and run an evaluation test set.
- Identify and correct an instruction defect.
- Rerun the evaluation and compare results.
- Publish and validate the agent in Microsoft Teams.

## Prerequisites

To complete this exercise, you need:

- A Microsoft Entra work or school account.
- [Access to Microsoft Copilot Studio](https://learn.microsoft.com/microsoft-copilot-studio/requirements-licensing-subscriptions).
- Permission to create and publish two agents powered by the GitHub Copilot harness in the same Power Platform environment.
- Access to the **Evaluate** feature. Evaluate is in production-ready preview. Confirm with your instructor or administrator that it's enabled in your environment before you begin Exercise 2.
- A Microsoft Teams account to validate the agent after publishing.
- Permission to install the agent for yourself or access to an administrator who can approve the agent after you publish it.

> [!NOTE]
> Building, testing, and evaluating an agent powered by the GitHub Copilot harness may consume Copilot Credits. Check with your administrator if you're uncertain about your organization's credit balance before starting.

## Exercise 1 - Create the Contoso policy agent

### Task 1.1 - Create the agent

1. Go to [Microsoft Copilot Studio](https://copilotstudio.microsoft.com/) and sign in with your work or school account.

1. Confirm that the correct environment is selected.

1. On the **Home** page, select **Agent**. Alternatively, select **Agents** in the left navigation and then select **+ New agent** in the upper-right corner.

1. In the **Name** field, enter the agent name:

   ```text
   Contoso Policy Agent <your initials>
   ```

   Replace `<your initials>` with your own initials or another short, unique identifier. For example: `Contoso Policy Agent CS`. Using your initials ensures the agent name is unique in a shared training environment.

1. If your organization requires a solution, in the upper-right corner, select **More options** (**...**), and then select **Settings**. In **Agent settings** > **Agent details**, select the solution provided for the exercise from the **Solution** list.

1. Remain on the agent's **Build** page. In the next task, you configure the agent's instructions from this page.

### Task 1.2 - Add the agent instructions

> [!IMPORTANT]
> The instructions below contain a deliberate defect in the **Scope boundaries** section. Do not change the escalation instruction at this stage. You identify the defect in Exercise 3 and correct it in Exercise 4.

On the **Build** page, locate the **Instructions** section. Insert the text below:

```text
You are the Contoso Policy Agent. You help Contoso employees find answers to questions about IT and HR support policies.

## Your role

- Answer questions about Contoso IT support policies, HR support procedures, and help desk processes.
- Provide accurate, complete answers based on the policy content in your instructions.
- Keep responses professional, concise, and helpful.

## Scope boundaries

- Only answer questions related to the Contoso IT and HR support policies listed in your instructions.
- If a question is outside your scope, let the user know you can only help with Contoso IT and HR support topics.
- If a user needs to speak with a person, let them know this is an automated assistant and that you cannot connect them directly to a human. Direct them to search the employee portal for contact information.

## Contoso support policies

### IT support

**Password reset**
Employees can reset their own password at https://aka.ms/sspr. If self-service password reset fails, contact the IT Help Desk. Self-service reset is available 24 hours a day, 7 days a week.

**Hardware issues**
Report hardware failures to the IT Help Desk within 24 hours of discovery. Include the device serial number and a description of the issue. Replacement or repair typically takes 3 to 5 business days.

**Software requests**
Submit all software installation requests through the IT Service Catalog. Standard software requests are approved within 2 business days. Licensed software requires manager approval and may take up to 10 business days.

**Remote access**
Contoso employees use the Contoso VPN client for remote access. Contact the IT Help Desk if you have trouble connecting. Remote access is available to all full-time employees and approved contractors.

**IT Help Desk hours**
The IT Help Desk is available Monday through Friday, 8:00 AM to 6:00 PM in your local time zone.

### HR support

**Leave requests**
Submit leave requests through the HR portal linked from the Contoso employee home page. Submit planned leave at least 5 business days in advance. Submit emergency leave on the day of absence with a brief reason.

**Benefits questions**
For benefits questions, contact the HR Benefits team at benefits@contoso.com or call the benefits hotline at extension 2840. Benefits enrollment is open each year during November.

**Performance reviews**
Contoso conducts performance reviews twice per year: in June and in December. Employees complete a self-evaluation in Workday before their review meeting.

**New hire onboarding**
New hires complete IT setup on their first day using the onboarding checklist in the employee portal. HR onboarding sessions are scheduled automatically during the first week.
```

1. After pasting the instructions, select **Save** to save the agent.

1. In the **Preview** tab, send the message `What are the IT Help Desk hours?` to confirm the agent responds. You should see a response that states Monday through Friday, 8 AM to 6 PM. If the agent doesn't respond or returns an error, verify the instructions are saved and that your environment supports agents powered by the GitHub Copilot harness.

### Task 1.3 - Create and publish the escalation specialist

1. Return to the **Agents** page, and then select **+ New agent**.

1. In the **Name** field, enter `Contoso Support Escalation Agent <your initials>`. Use the same unique identifier that you used for the policy agent.

1. In the **Instructions** section, insert the following text:

   ```text
   You are the Contoso Support Escalation Agent. You handle unresolved IT and HR support cases when an employee asks to escalate an issue or speak with a person.

   - For IT issues, direct the employee to call the IT Help Desk at extension 4357. The help desk is available Monday through Friday, 8:00 AM to 6:00 PM.
   - For HR matters, direct the employee to contact HR Support at hr-support@contoso.com or call the benefits and HR hotline at extension 2840.
   - Ask one clarifying question if you can't determine whether the issue is related to IT or HR.
   - Don't answer routine policy questions. Handle only escalation and human-support requests.
   ```

1. Select **Save**. On the **Preview** tab, send `I need to escalate an unresolved laptop ticket.` Confirm that the agent provides extension 4357.

1. On the **Build** page, select **Publish** > **Publish agent**. The specialist must be published before the policy agent can connect to it.

### Task 1.4 - Connect the escalation specialist

1. Return to the **Agents** page, and then open `Contoso Policy Agent <your initials>`.

1. On the **Build** tab, select **Connected agents** in the components panel.

1. Search for and select `Contoso Support Escalation Agent <your initials>`.

1. Use the following description:

   ```text
   Handles unresolved Contoso IT or HR support cases when an employee asks to escalate an issue or speak with a person. Provides approved human-support contact information. Do not use for routine policy questions.
   ```

1. Select **Connect**, and then confirm that the specialist appears under **Connected agents**.

The specialist's distinct description helps the main agent decide when to delegate. The deliberate instruction defect in the main agent still conflicts with this routing. You identify and correct the conflict after you run the baseline evaluation.

## Exercise 2 - Create evaluation conversations

> [!IMPORTANT]
> The **Evaluate** feature for agents powered by the GitHub Copilot harness is in production-ready preview. Confirm it's available in your environment before proceeding. If Evaluate is not enabled, skip to Exercise 4 and validate the agent using Preview and the published channel.

You create four evaluation conversations that cover the most important scenarios for the support policy agent: a direct answer retained by the main agent, an ambiguous request requiring clarification, an out-of-scope boundary, and an escalation request that should delegate to the connected agent.

### Task 2.1 - Configure a new test set

1. Select the **Evaluate** tab.

1. If prompted, review and accept any preview terms or notices.

1. Select **New evaluation** or **+ Create your first evaluation**.

1. In **More ways to start**, select **Or, write some questions yourself**.

1. In the **Configure test set** panel, enter `Contoso support release evaluation` for the name and confirm that **General quality** appears as the test method.

### Task 2.2 - Create conversation 1: In-scope answer

1. In **Review your test cases**, select **+ Add conversations** > **Write**.

1. In the new row, select the empty field under **Conversation**, and then add the following user question:

   ```text
   What are the IT Help Desk hours?
   ```

1. Optionally, add this expected agent response:

   ```text
   Agent states that the IT Help Desk is available Monday through Friday, 8 AM to 6 PM in the user's local time zone.
   ```

   > [!NOTE]
   > Expected agent responses are for your own reference during manual review. General quality evaluates standards such as relevance and completeness. It doesn't compare the actual response against the expected response.

1. Select **Done**, and then select **Save**.

### Task 2.3 - Create the remaining conversations

1. Repeat steps 1 through 4 from the previous task to add each conversation listed in the following table:

| Conversation | User question | Expected agent response |
| --- | --- | --- |
| Ambiguity and clarification | I need help with my benefits. | Agent asks a clarifying question to understand whether the user has a question about benefits enrollment, leave requests, or another HR topic. Agent does not assume a specific intent. |
| Out-of-scope boundary | Can you recommend a good restaurant near the office for a team lunch? | Agent declines the request and explains that it can only help with Contoso IT and HR support topics. Agent does not attempt to answer the restaurant question. |
| Connected-agent delegation | I submitted a ticket about my laptop three days ago, and nobody has responded. I need to speak with someone urgently. What should I do? | Main agent delegates the request to the connected escalation specialist, which provides the IT Help Desk extension. |

## Exercise 3 - Run the baseline evaluation and observe the defect

### Task 3.1 - Run the evaluation

1. On the **Evaluate** page, confirm that all four conversations appear under the **Review your test cases** section.

1. In the **Configure test set** panel, select **Evaluate**.

1. If the **Manage profile and connections** dialog opens, under **User**, select or add the account used for the lab. If prompted, sign in to authenticate the account, and then select **Run**.

1. Wait for the evaluation run to complete. The run appears in the **Evaluations** list when finished.

### Task 3.2 - Review baseline results

1. Open the completed evaluation run, if not already open.

1. Review the General quality score for each conversation. Record your observations in the table below.

   | Conversation | Observed General quality result |
   | --- | --- |
   | IT Help Desk hours | |
   | Vague benefits question | |
   | Out-of-scope restaurant request | |
   | Unresolved ticket escalation | |

1. Select the **Unresolved ticket escalation** conversation to expand the detail view.

1. Read the agent's actual response to the user message. Observe that the agent says something similar to: *"I'm an automated assistant, so I can't connect you with a person or escalate your ticket myself. For IT Help Desk contact details, please search the employee portal."*

1. Compare this response to the expected agent response. The expected response provides specific escalation contact information. The agent's actual response doesn't.

### Task 3.3 - Identify the defect

1. Based on your review of the evaluation results, identify the cause of the low-quality escalation response.

1. Return to the **Build** tab and locate this statement in the **Scope boundaries** section of the agent's instructions:

   ```text
   If a user needs to speak with a person, let them know this is an automated assistant and that you cannot connect them directly to a human. Direct them to search the employee portal for contact information.
   ```

1. Notice that this instruction conflicts with the connected agent's purpose and prevents delegation to the escalation specialist. This instruction must allow the main agent to delegate matching requests.

## Exercise 4 - Correct the defect

### Task 4.1 - Update the agent instructions

1. On the **Build** tab, in the **Instructions** area, locate the escalation boundary statement under **Scope boundaries:**

   ```text
   If a user needs to speak with a person, let them know this is an automated assistant and that you cannot connect them directly to a human. Direct them to search the employee portal for contact information.
   ```

1. Replace that sentence with the following text:

   ```text
   If a user asks to speak with a person or escalate an unresolved IT or HR issue, delegate the request to the connected escalation specialist. Don't block the request or attempt to provide escalation details yourself.
   ```

1. Select **Save**.

1. In the **Preview** tab, start a new conversation and send the message `I need to speak to someone about my laptop ticket.` Confirm that the main agent delegates the request and the response provides extension 4357.

1. Start another conversation and send `What are the IT Help Desk hours?` Confirm that the main agent answers the routine policy question without delegating it to the escalation specialist.

## Exercise 5 - Rerun the evaluation and compare results

### Task 5.1 - Run the evaluation again

1. Select **Evaluate** in the top navigation, open **Contoso support release evaluation**, and then select **Configuration**.

1. Confirm that your four conversations are still listed.

1. On the **Configure test set** panel, select **Evaluate**.

1. Wait for the evaluation run to complete.

### Task 5.2 - Compare results

1. If the results view is not displayed, select the latest evaluation run to open its results.

1. Compare the General quality result and actual response for the delegation conversation between the baseline run and this run. The score might change, but the updated response must show successful delegation and include the specific escalation contact.

1. Select the conversation detail to read the agent's updated response. Confirm that the connected escalation specialist provides the IT Help Desk extension when the user asks for escalation.

1. Review the other three conversations and confirm that the instruction change didn't reduce their scores.

> [!NOTE]
> Copilot Studio saves each evaluation run separately. Compare the latest run with the earlier baseline run after you save the corrected agent.

## Exercise 6 - Publish and add the Teams and Microsoft Copilot channel

### Task 6.1 - Publish the agent

1. On the **Build** page, select **Publish** > **Publish agent**.

1. After publishing completes, select **Add channels**.

1. Select **Teams + Microsoft 365**. Under **Available in**, select **Microsoft 365 Copilot and Microsoft Teams**, then select **Add channel**.

1. In the **Channels** section, select the **Teams + Microsoft 365** channel. Select the **About info** tab, and then complete the following fields where available:

   | Field | Value |
   | --- | --- |
   | **Short description** | `Answers Contoso employee questions about IT and HR support policies.` |
   | **Long description** | `Use this agent to find answers about password resets, hardware issues, software requests, remote access, leave requests, benefits enrollment, and performance reviews.` |

1. Select **Save**.

### Task 6.2 - Install the agent for yourself

Choose the path that matches your organization's policy.

**If your organization permits self-installation:**

1. In the **Teams + Microsoft 365** channel configuration panel, under **Use and share**, select **View in Teams**.

1. In the browser prompt to open Microsoft Teams, select **Cancel**, select **Use the web app instead**, and sign in with your work or school account.

1. In Teams, select **Add**. This action installs the agent in Teams and Microsoft 365 Copilot when Microsoft 365 availability is enabled.

**If your organization requires administrator approval:**

1. In **Availability options**, select **Use and share**, and then select **Submit to org catalog** twice.

1. In the **Give everyone access to this agent?** dialog, select **Yes, submit** to send the agent for administrator approval.

1. Contact your Teams administrator and request approval. Provide the agent's display name and a brief description of its purpose.

1. Do not proceed to validation until the administrator confirms the agent is available in the catalog or is pre-installed for your account.

> [!NOTE]
> If tenant policy prevents installation and no administrator is available during the exercise, use Preview as the fallback validation path for the next task. Preview doesn't prove published-channel behavior. Record this limitation and complete channel validation with your administrator later.

## Exercise 7 - Validate as the published user

### Task 7.1 - Test the agent in Microsoft Teams

After the agent is installed by you or your administrator, open and test it from within Microsoft Teams, not from the Copilot Studio authoring environment.

1. Open Microsoft Teams, and then locate and open the **Contoso Policy Agent** app you installed. Use the display name you configured.

1. Send the following messages one at a time and observe the responses:

   | Test message | Expected behavior |
   | --- | --- |
   | `What are the IT Help Desk hours?` | Agent states Monday through Friday, 8 AM to 6 PM local time |
   | `How do I request new software?` | Agent explains the IT Service Catalog process and approval timelines |
   | `Can you book a meeting room for me?` | Agent declines and states it can only help with Contoso IT and HR support topics |
   | `I've been waiting three days on a ticket. I need to talk to someone now.` | Main agent delegates to the escalation specialist, which provides IT Help Desk extension 4357 |

1. For each response, verify:

   - The response is accurate and matches the policy content in the agent's instructions.
   - The agent declines out-of-scope requests without attempting to answer them.
   - The main agent retains routine policy questions.
   - The escalation request is delegated and the response includes extension 4357.

1. If a response is incorrect or missing expected content, open **Monitor** in Copilot Studio to review the conversation and determine whether the issue is a quality defect, a permission failure, or a runtime error.

### Task 7.2 - Record validation results

In your lab notes, record the result of each validation test in the following table:

| Validation area | Result | Notes |
| --- | --- | --- |
| Authentication (agent loads without error) | Pass / Fail | |
| In-scope answer accuracy | Pass / Fail | |
| Out-of-scope decline | Pass / Fail | |
| Connected-agent delegation | Pass / Fail | |
| Routine request retained by main agent | Pass / Fail | |
| No unexpected errors in responses | Pass / Fail | |

## Completion criteria

You have completed this exercise when you can confirm all of the following:

- [ ] The Contoso Policy Agent is created with a unique name that includes your initials.
- [ ] The Contoso Support Escalation Agent is created, tested, and published in the same environment.
- [ ] The escalation specialist is connected to the policy agent with a distinct routing description.
- [ ] Four evaluation conversations are saved in the Evaluate page.
- [ ] A baseline evaluation run is complete, and the escalation response lacks a specific support contact.
- [ ] You can identify the specific instruction text that caused the escalation defect.
- [ ] The corrected instructions allow the main agent to delegate escalation requests to the connected specialist.
- [ ] A second evaluation run shows successful delegation and includes the IT Help Desk extension.
- [ ] The agent is published and the Teams + Microsoft 365 Copilot channel is added.
- [ ] You installed the Teams app for yourself, contacted your administrator for approval, or documented the fallback validation path.
- [ ] You validated in-scope answers, boundary behavior, and escalation behavior through the published Teams channel or the available fallback path.

## Clean up

After you complete the exercise, disconnect and delete both agents to avoid consuming Copilot Credits from future testing or accidental interactions.

1. In Copilot Studio, open `Contoso Policy Agent <your initials>`.

1. On the **Build** tab, select **Connected agents**. Open the escalation specialist, and then select **Disconnect**.

1. Locate your agent in the **Agents** list, and then select **More options** (**...**) in the upper-right corner.

1. From the menu, select **Delete agent**.

1. Enter the agent's exact name, and then select **Delete agent** to confirm the permanent deletion.

1. Repeat the deletion steps for `Contoso Support Escalation Agent <your initials>`.

If you created the agents within a solution, remove them from the solution before deleting them from the environment to ensure a complete cleanup.
