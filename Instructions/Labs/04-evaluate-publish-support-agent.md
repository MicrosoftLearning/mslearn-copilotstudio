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

# Evaluate, publish, and manage agents in Microsoft Copilot Studio

## Scenario

In this exercise, you create the **Contoso Policy Agent** and a specialized escalation agent. You connect the agents, evaluate delegation with a structured set of test conversations, correct one deliberate instruction defect, publish the main agent to Microsoft Teams, and validate its behavior as a published user.

This exercise takes approximately **55 minutes** to complete.

## What you learn

- How to create and run a repeatable agent evaluation.
- How to connect a specialist agent and test delegation boundaries.
- How to diagnose and correct an instruction defect.
- How to publish an agent to Microsoft Teams.
- How to validate agent behavior as a published user.

## High-level lab steps

- Create and configure a support policy agent and an escalation specialist.
- Connect the specialist to the main agent.
- Create and run an evaluation test.
- Identify and correct an instruction defect.
- Rerun the evaluation and compare results.
- Publish and validate the agent in Microsoft Teams.

## Prerequisites

To complete this exercise, you need:

- A Microsoft Entra work or school account.
- [Access to Microsoft Copilot Studio](https://learn.microsoft.com/microsoft-copilot-studio/requirements-licensing-subscriptions).
- Permission to create and publish two agents powered by the GitHub Copilot harness in the same Power Platform environment.
- Access to the **Evaluate** feature, including the **Classification** and **Capability use** test methods. Evaluate is in production-ready preview. Confirm with your instructor or administrator that these methods are enabled for your agent in your environment before you begin Exercise 2.
- A Microsoft Teams account to validate the agent after publishing.
- Permission to install the agent for yourself or access to an administrator who can approve the agent after you publish it.

> [!NOTE]
> Building, testing, and evaluating an agent powered by the GitHub Copilot harness may consume Copilot Credits. Check with your administrator if you're uncertain about your organization's credit balance before starting.

## Exercise 1 - Create the Contoso policy agent

### Task 1.1 - Create the agent

1. Go to [Microsoft Copilot Studio](https://copilotstudio.microsoft.com/) at `https://copilotstudio.microsoft.com/` and sign in with your work or school account.

1. Confirm that the correct environment is selected.

1. On the **Home** page, select **Agent**. Alternatively, select **Agents** in the left navigation and then select **New agent** in the upper-right corner.

1. In the **Name** field, enter the agent name:

   ```text
   Contoso Policy Agent <your initials>
   ```

   Replace `<your initials>` with your own initials or another short, unique identifier. For example: `Contoso Policy Agent CS`. Using your initials ensures the agent name is unique in a shared training environment.

1. If your organization requires a solution, in the upper-right corner, select **More options** (**...**), and then select **Settings**. In **Agent settings** > **Agent details**, check the **Solution** list. If the solution provided for the exercise isn't already selected, select it and then select **Done**. If it's already selected, you don't need to select **Done**; close the settings dialog.

1. Remain on the agent's **Build** page. In the next task, you configure the agent's instructions from this page.

### Task 1.2 - Add the agent instructions

> [!IMPORTANT]
> The instructions below contain a deliberate defect in the **Scope boundaries** section. Do not change the escalation instruction at this stage. You identify the defect in Exercise 3 and correct it in Exercise 4.

1. On the **Build** page, locate the **Instructions** section. Insert the text below:

   ```text
   You are the Contoso Policy Agent. You help Contoso employees find answers to questions about IT and HR support policies.

   ## Your role

   - Answer questions about Contoso IT support policies, HR support procedures, and help desk processes.
   - Provide accurate, complete answers based on the policy content in your instructions.
   - Keep responses professional, concise, and helpful.

   ## Scope boundaries

   - Only answer questions related to the Contoso IT and HR support policies listed in your instructions.
   - If a question is outside your scope, let the user know you can only help with Contoso IT and HR support topics.
   - If a user needs to speak with a person or escalate an unresolved IT or HR issue, do not delegate the request to a connected agent. Let them know this is an automated assistant and that you cannot connect them directly to a human. Direct them to search the employee portal for contact information.

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

1. Return to the **Agents** page, and then select **New agent**.

1. In the **Name** field, enter `Contoso Escalation Agent <your initials>`. Use the same unique identifier that you used for the policy agent.

1. In the **Instructions** section, insert the following text:

   ```text
   You are the Contoso Escalation Agent. You handle unresolved IT and HR support cases when an employee asks to escalate an issue or speak with a person.

   - For IT issues, direct the employee to call the IT Help Desk at extension 4357. The help desk is available Monday through Friday, 8:00 AM to 6:00 PM.
   - For HR matters, direct the employee to contact HR Support at hr-support@contoso.com or call the benefits and HR hotline at extension 2840.
   - Ask one clarifying question if you can't determine whether the issue is related to IT or HR.
   - Don't answer routine policy questions. Handle only escalation and human-support requests.
   ```

1. Select **Save**. On the **Preview** tab, send `I need to escalate an unresolved laptop ticket.` Confirm that the agent provides extension 4357.

1. On the **Build** page, select **Publish** > **Publish agent**. If publishing starts automatically, you don't need to select **Publish** a second time. The specialist must be published before the policy agent can connect to it. When publishing is complete, select **Done**.

### Task 1.4 - Connect the escalation specialist

1. Return to the **Agents** page, and then open `Contoso Policy Agent <your initials>`.

1. On the **Build** tab, select **Connected agents** in the components panel.

1. Search for and select `Contoso Escalation Agent <your initials>`. If necessary, select **Refresh** to make the agent available for selection.

1. Use the following description:

   ```text
   Handles unresolved Contoso IT or HR support cases when an employee asks to escalate an issue or speak with a person. Provides approved human-support contact information. Do not use for routine policy questions.
   ```

1. Select **Connect**, and then confirm that the specialist appears under **Connected agents**.

The specialist's distinct description helps the main agent decide when to delegate. The deliberate instruction defect in the main agent still conflicts with this routing. You identify and correct the conflict after you run the baseline evaluation.

## Exercise 2 - Create evaluation conversations

> [!IMPORTANT]
> The **Evaluate** feature for agents powered by the GitHub Copilot harness is in production-ready preview. Confirm it's available in your environment before proceeding. If Evaluate or the required test methods aren't enabled, complete Exercise 4, skip Exercise 5, and continue with Exercise 6. Validate using Preview and the published channel, and leave the automated-evaluation completion criteria unchecked. Record that automated evaluation of delegation remains incomplete; manual review or a response-text check isn't a substitute for **Capability use**.

You create four evaluation conversations that cover the most important scenarios for the support policy agent: a direct answer retained by the main agent, an ambiguous request requiring clarification, an out-of-scope boundary, and an escalation request that should delegate to the connected agent. You then create a separate evaluation to check whether the main agent calls the connected escalation specialist.

### Task 2.1 - Configure a new test set

1. Select the **Evaluate** tab.

1. If prompted, review and accept any preview terms or notices.

1. Select **New evaluation** or **+ Create your first evaluation**.

1. In **Create or select a data set**, select **Conversations** as the data type, then select **Or, write some questions yourself**.

1. Enter `Contoso support release evaluation` for the evaluation name and confirm that **General quality** appears as the test method.

### Task 2.2 - Create conversation 1: In-scope answer

1. Select **+ Add conversations** > **Write a conversation**.

1. In the new row, select the empty field under **Conversation**, and then add the following user question:

   ```text
   What are the IT Help Desk hours?
   ```

1. Optionally, add this expected agent response:

    ```text
    The IT Help Desk is available Monday through Friday, 8 AM to 6 PM in your local time zone.
    ```

   > [!NOTE]
   > Expected agent responses are for your own reference during manual review. General quality doesn't compare the actual response against the expected response, and Classification evaluates responses against the instructions and labels you define.

1. Select **Done**, and then select **Save**.

### Task 2.3 - Create the remaining conversations

1. Repeat steps 1 through 4 from the previous task to add each conversation listed in the following table:

| Conversation | User question | Expected agent response |
| --- | --- | --- |
| Ambiguity and clarification | I need help with my benefits. | What would you like help with: benefits enrollment, leave requests, or another HR topic? |
| Out-of-scope boundary | Can you recommend a good restaurant near the office for a team lunch? | I can only help with Contoso IT and HR support topics, so I can't recommend a restaurant. |
| Connected-agent delegation | I submitted a ticket about my laptop three days ago, and nobody has responded. I need to speak with someone urgently. What should I do? | For urgent help with your laptop ticket, call the IT Help Desk at extension 4357. The help desk is available Monday through Friday, 8 AM to 6 PM. |

### Task 2.4 - Add a Classification test method

General quality checks qualities such as relevance and completeness. **Classification** checks whether the response follows the rules you provide, including giving the correct support contact and avoiding conflicting guidance. It checks the response text, not whether the specialist was called. You check that separately in Task 2.5.

1. Under **Select test methods**, select **Add test method**.

1. In the **Select a test method** dialog, select **Classification**, and then select **OK**.

1. In the **Configure classification** dialog, enter `Escalation response check` in the **Name** field.

1. In the **Evaluation instructions** field, enter:

   ```text
   Evaluate the response text, not whether a connected agent was called. If the user asks to escalate an issue or speak with a person about IT, label the response Pass only if it provides IT Help Desk extension 4357. For an HR escalation, require hr-support@contoso.com or extension 2840. Label an escalation response Fail if it omits the appropriate contact, says that the agent cannot connect the user to a person, or tells the user to search the employee portal, even if it also provides a contact. For routine IT or HR questions, label the response Pass if it answers the question or asks a relevant clarifying question without presenting the request as an escalation. For out-of-scope requests, label the response Pass if it declines and states the IT and HR support boundary without presenting the request as an escalation. Routine and out-of-scope responses do not need an escalation contact. Label all other responses Fail.
   ```

1. Under **Labels**, for the **Pass** label, keep **Pass** selected, and enter the following criteria:

   ```text
   For an IT escalation, the response provides extension 4357; for an HR escalation, it provides hr-support@contoso.com or extension 2840. Neither escalation response says that the agent cannot connect the user to a person or tells the user to search the employee portal. For a routine IT or HR question, the response answers or asks a relevant clarifying question without presenting it as an escalation. For an out-of-scope request, the response declines and states the IT and HR support boundary without presenting it as an escalation. No escalation contact is required for routine or out-of-scope requests.
   ```

1. For the **Fail** label, keep **Fail** selected, and enter the following criteria:

   ```text
   For an escalation request only, the response omits the appropriate contact (extension 4357 for IT, or hr-support@contoso.com or extension 2840 for HR), says that the agent cannot connect the user to a person, or tells the user to search the employee portal, even if it also provides a contact. For a routine IT or HR question, the response neither answers nor asks a relevant clarifying question, or presents the request as an escalation. For an out-of-scope request, the response fulfills the request, fails to state the IT and HR support boundary, or presents the request as an escalation. Do not fail routine or out-of-scope responses merely because they omit an escalation contact.
   ```

1. Select **OK**, and then select **Save**.

### Task 2.5 - Create an evaluation that checks delegation

**Capability use** checks whether the agent used the expected tools or skills. In this lab, you use it to check whether the main agent called the connected escalation specialist. Providing extension 4357 in the response isn't enough to confirm this.

Create a separate evaluation containing only the escalation conversation. Routine questions and requests outside IT and HR support shouldn't require the specialist.

1. Return to the **Evaluate** tab and create another evaluation by following Task 2.1. Name it `Contoso delegation evaluation`.

1. Add only the **Connected-agent delegation** conversation from Task 2.3, using the same user question and expected response.

1. Add the **Escalation response check** Classification test method using the instructions and labels from Task 2.4.

1. Under **Select test methods**, select **Add test method**, select **Capability use**, and then select **OK**.

1. For the escalation conversation, set the expected capability to the entry corresponding to `Contoso Escalation Agent <your initials>`. Select the pencil beside **Tools**, select only the connected specialist, not the main policy agent, and then select **OK**. Save the capability expectation and the evaluation.

   > [!IMPORTANT]
   > Use the connected specialist's actual capability entry rather than extension 4357, the expected response, or a guessed tool name. If the specialist cannot be configured as an expected capability, record that automated delegation validation remains incomplete.

1. Confirm that this evaluation contains one conversation and the **General quality**, **Escalation response check**, and **Capability use** test methods. Both **Classification** and **Capability use** must evaluate the same conversation in the same run.

## Exercise 3 - Run the baseline evaluation and observe the defect

A baseline run is the first evaluation run, before you correct the agent's instructions. You use these results to compare the agent's behavior before and after the change.

### Task 3.1 - Run the evaluation

1. On the **Evaluate** page, open **Contoso support release evaluation** and confirm that all four conversations are listed.

1. Confirm that the evaluation will use the saved agent instructions containing the deliberate defect, rather than a different published version. Use the same agent version selection for both evaluations.

1. Select **Run**.

1. If the **Manage connections** dialog opens, select the connection and confirm you are using your lab account. Then select **Continue**.

   > [!NOTE]
   > If the evaluation doesn't start, refresh the page, create a new connection and sign in to authenticate the account. Then try to run the evaluation again.

1. Wait for the evaluation run to complete. If the **evaluation is ready** notification appears, select **View results**. You can also open the completed run from the **Evaluations** list.

1. Open **Contoso delegation evaluation** and run it using the same steps. Confirm that its one conversation has the connected escalation specialist configured as the expected capability.

### Task 3.2 - Review baseline results

1. Open the completed **Contoso support release evaluation** baseline run.

1. Review the **General quality** score and the **Classification** label for each conversation. Record your observations in the table below.

   | Conversation | General quality | Classification |
   | --- | --- | --- |
   | IT Help Desk hours | | |
   | Vague benefits question | | |
   | Out-of-scope restaurant request | | |
   | Unresolved ticket escalation | | |

   > [!NOTE]
   > General quality can label the out-of-scope restaurant request **Fail** because the agent intentionally declines to answer it. This isn't an escalation defect. The **Classification** label should be **Pass** when the agent correctly declines the request.

1. Open the completed **Contoso delegation evaluation** run and select its escalation conversation. Record both automated results:

   | Conversation | Classification | Capability use |
   | --- | --- | --- |
   | Unresolved ticket escalation | | |

1. Review **Capability use** and record the reported status.

1. Review **Classification** and the actual response. The expected baseline result is **Fail** if the response omits extension 4357 or includes the guidance that the agent can't connect the user to a person or that the user should search the employee portal.

   > [!NOTE]
   > These tests check different things: whether the response is correct and whether the specialist was called. One test can pass while the other doesn't. If a result fails, review the result details and evaluation settings before drawing a conclusion. If both tests pass before you correct the instructions, check that the deliberately incorrect instructions are still saved and that you're testing the intended agent version. Run the baseline again. If both tests still pass, record that this run didn't show the expected problem.

### Task 3.3 - Identify the defect

1. Based on the **Capability use** and **Classification** results, identify which instruction blocks delegation or causes conflicting escalation guidance.

1. Return to the **Build** tab and locate this statement in the **Scope boundaries** section of the agent's instructions:

   ```text
   If a user needs to speak with a person or escalate an unresolved IT or HR issue, do not delegate the request to a connected agent. Let them know this is an automated assistant and that you cannot connect them directly to a human. Direct them to search the employee portal for contact information.
   ```

1. Notice that this instruction explicitly prohibits delegation and conflicts with the connected agent's purpose. It also directs the main agent to provide unhelpful guidance instead of the approved support contact. Replace the entire statement so that matching requests can reach the specialist without conflicting response instructions.

## Exercise 4 - Correct the defect

### Task 4.1 - Update the agent instructions

1. Replace the escalation boundary statement you identified in the previous task with:

    ```text
    If a user asks to speak with a person or escalate an unresolved IT or HR issue, delegate the request to the connected escalation specialist. Don't block the request or attempt to provide escalation details yourself.
    ```

1. Select **Save**.

1. In the **Preview** tab, start a new conversation and send the message `I need to speak to someone about my laptop ticket.` Confirm that the main agent delegates the request and the response provides extension 4357.

1. Start another conversation and send `What are the IT Help Desk hours?` Confirm that the main agent answers the routine policy question without delegating it to the escalation specialist.

## Exercise 5 - Rerun the evaluation and compare results

### Task 5.1 - Run the evaluation again

1. Select **Evaluate** in the top navigation, open **Contoso support release evaluation**, and then select **Configuration**.

1. Confirm that your four conversations and the **General quality** and **Escalation response check** test methods are still listed.

1. Select **Run** or **Run again**.

1. If the **Manage connections** dialog opens, select the connection and confirm you are using the account provided for the lab. Then select **Continue**.

1. Wait for the evaluation run to complete.

1. Open **Contoso delegation evaluation** if it isn't already open. Confirm that its escalation conversation, the expected specialist capability, and all three test methods are unchanged.

1. Select **Run** or **Run again**.

1. If the **Manage connections** dialog opens, select the connection for your lab account, and then select **Continue**.

1. Wait for the delegation evaluation run to complete before proceeding to Task 5.2.

### Task 5.2 - Compare results

1. Open the latest **Contoso delegation evaluation** run. Compare its **Capability use** and **Classification** results with the baseline run.

   | Test method | Expected baseline result | Required result after the fix |
   | --- | --- | --- |
   | Capability use | Record observed status | Pass: the expected specialist is called |
   | Classification | Fail: contact information is missing or guidance conflicts | Pass: extension 4357 is provided without conflicting guidance |

1. Check that **Classification** and **Capability use** both show **Pass** in the same run. Classification checks the response; Capability use checks whether the specialist was called.

   > [!NOTE]
   > **Capability use** may show **Invalid** if the expected tool wasn't saved; this doesn't mean delegation failed. Verify **Classification** is **Pass** and the escalation agent appears under **Tools referenced**. Record automated delegation validation as incomplete.

1. Select the conversation to inspect the supporting evidence. Under **Tools referenced**, confirm that the connected escalation agent appears, and confirm that the response provides IT Help Desk extension 4357 without the conflicting guidance. This inspection explains the automated results; it isn't the only way the evaluation detects missing delegation.

1. Open the latest **Contoso support release evaluation** run. Confirm that Classification labels all four conversations **Pass**. Review General quality and the responses for regressions. The restaurant request should still be declined; a General quality **Fail** for that refusal doesn't override its expected Classification **Pass**.

> [!NOTE]
> Copilot Studio saves each evaluation run separately. Compare baseline and corrected runs within each evaluation. If a baseline method already passed, record that it remained Pass rather than claiming it changed from Fail.

## Exercise 6 - Add the Teams + Microsoft 365 channel and publish the agent

### Task 6.1 - Configure the Teams + Microsoft 365 channel and publish the agent

1. On the **Build** page, select **Publish**.

1. Select **+ Add channel**.

1. Select **Teams + Microsoft 365**.

1. Select **Microsoft Teams only**.

1. On the **About info** tab, complete the following fields, where available:

   | Field | Value |
   | --- | --- |
   | **Short description** | `Answers Contoso employee questions about IT and HR support policies.` |
   | **Long description** | `Use this agent to find answers about password resets, hardware issues, software requests, remote access, leave requests, benefits enrollment, and performance reviews.` |

1. Select **Add channel**.

1. Select **Publish agent**.

### Task 6.2 - Install the agent for yourself

Choose the path that matches your organization's policy.

**If your organization permits self-installation:**

1. When the publishing confirmation appears, select **View in Teams + Microsoft 365** or **View in Microsoft Teams**.

1. In the browser prompt to open Microsoft Teams, select **Cancel**, select **Use the web app instead**. If prompted, sign in with your lab account.

1. In Microsoft Teams, select **Add**. This action installs the agent in Microsoft Teams when Microsoft 365 availability is enabled.

**If your organization requires administrator approval:**

1. In the components panel, under **Channels**, select **Teams + Microsoft 365** or **View in Microsoft Teams**.

1. Select **Use and share**, and then select **Submit to org catalog** twice.

1. In the **Give everyone access to this agent?** dialog, select **Yes, submit** to send the agent for administrator approval.

1. Contact your Teams administrator and request approval. Provide the agent's display name and a brief description of its purpose.

1. Do not proceed to validation until the administrator confirms the agent is available in the catalog or is pre-installed for your account.

> [!NOTE]
> If tenant policy prevents installation and no administrator is available during the exercise, use Preview as the fallback validation path for the next task. Preview doesn't prove published-channel behavior. Record this limitation and complete channel validation with your administrator later.

## Exercise 7 - Validate as the published user

### Task 7.1 - Test the agent in Microsoft Teams

After the agent is installed by you or your administrator, open and test it from Microsoft Teams, not from the Copilot Studio authoring environment.

1. Open Microsoft Teams, and then locate and open the **Contoso Policy Agent** app you installed. Use the display name you configured. If the agent's dialog is still open, select **Open**.

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
- [ ] The Contoso Escalation Agent is created, tested, and published in the same environment.
- [ ] The escalation specialist is connected to the policy agent with a distinct routing description.
- [ ] The support release evaluation contains four conversations and the Escalation response check Classification test method.
- [ ] The separate delegation evaluation contains the escalation conversation, the specialist's expected capability, and both Classification and Capability use test methods.
- [ ] The results from both baseline evaluations are recorded.
- [ ] You can identify the specific instruction text that caused the escalation defect.
- [ ] The corrected instructions allow the main agent to delegate escalation requests to the connected specialist.
- [ ] The corrected delegation evaluation returns Pass for both Capability use and Classification in the same run, confirming specialist invocation was successful and extension 4357 without conflicting guidance.
- [ ] The corrected support release evaluation returns Classification Pass for all four conversations, including routine and out-of-scope requests that don't require an escalation contact.
- [ ] The agent is published and the Teams + Microsoft 365 channel is added.
- [ ] You accessed the agent in Microsoft Teams, contacted your administrator for approval, or documented the fallback validation path.
- [ ] You validated in-scope answers, boundary behavior, and escalation behavior through the published Teams channel or the available fallback path.

## Clean up

After you complete the exercise, disconnect and delete both agents to avoid consuming Copilot Credits from future testing or accidental interactions.

1. In Copilot Studio, open `Contoso Policy Agent <your initials>`.

1. On the **Build** tab, select **Connected agents**. Open the escalation specialist, and then select **Disconnect**.

1. Locate your agent in the **Agents** list, and then select **More options** (**...**) in the upper-right corner.

1. From the menu, select **Delete agent**.

1. Enter the agent's exact name, and then select **Delete agent** to confirm the permanent deletion.

1. Repeat the deletion steps for `Contoso Escalation Agent <your initials>`.

If you created the agents within a solution, remove them from the solution before deleting them from the environment to ensure a complete cleanup.
