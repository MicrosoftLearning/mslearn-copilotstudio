---
lab:
  title: Create a benefits information agent
  module: Create instruction-driven agents in Microsoft Copilot Studio
  description: Create and test an instruction-driven benefits information agent with company and government knowledge sources.
  duration: 40 minutes
  level: 200
  islab: true
  primarytopics:
    - Microsoft Copilot Studio
    - Agents
---

## Scenario

In this exercise, you create the **Contoso Benefits Assistant**, an agent powered by the GitHub Copilot harness. You add company and government knowledge sources, define the agent's behavior, configure its opening experience, and refine one instruction after testing.

This exercise takes approximately **40 minutes** to complete.

## What you'll learn

- How to create an instruction-driven agent.
- How to ground an agent with company and public website knowledge.
- How to configure a greeting and suggested prompts.
- How to test and refine agent instructions.

## High-level lab steps

- Prepare a fictional benefits guide.
- Create and configure an agent.
- Add company and government knowledge sources.
- Configure the opening experience.
- Test the agent and refine a boundary instruction.

## Prerequisites

To complete this exercise, you need:

- A Microsoft Entra work or school account.
- [Access to Copilot Studio](https://learn.microsoft.com/microsoft-copilot-studio/requirements-licensing-subscriptions).
- Permission to create an agent in a Power Platform environment.
- Access to a solution in the environment if your organization requires agents to be created in a solution.

> [!NOTE]
> Building and testing an agent powered by the GitHub Copilot harness might consume Copilot Credits.

## Exercise 1 - Prepare the benefits guide

Create the fictional company guide that the agent uses as a knowledge source.

1. Open a text editor and create a file named `contoso-benefits-guide.md`.

1. Add the following content to the file:

   ```markdown
   # Contoso employee benefits guide

   This fictional guide supports a training exercise. It doesn't provide legal, tax, medical, or financial advice.

   ## Annual enrollment

   Contoso's annual benefits enrollment period runs from October 15 through November 5. Elections made during annual enrollment take effect on January 1 of the following year.

   Outside annual enrollment, employees can change benefit elections only after a qualifying life event. Examples include marriage, divorce, birth or adoption of a child, and loss of other health coverage. Employees must contact the Benefits Service Center within 30 calendar days of the event. The Benefits Service Center determines whether an event and requested change meet plan requirements.

   ## Medical plan types

   Contoso offers three medical plan types:

   - **Health maintenance organization (HMO)**: Uses a defined provider network and requires members to select a primary care provider. Out-of-network care isn't covered except for emergencies.
   - **Preferred provider organization (PPO)**: Offers in-network and out-of-network coverage. Members generally pay less when they use in-network providers.
   - **High-deductible health plan (HDHP)**: Has a higher annual deductible and can be paired with a health savings account when the employee meets applicable requirements.

   Plan availability, premiums, deductibles, and provider networks can vary by employee location. The current enrollment portal contains the amounts and plan documents for each employee.

   ## Dependents

   The plans can cover eligible dependents as defined in the applicable plan document. Employees who want to add a spouse, domestic partner, or child must provide the documentation requested by the Benefits Service Center. The Benefits Service Center makes personal eligibility decisions after reviewing the employee's circumstances and documents.

   ## Wellness benefit

   Employees enrolled in a Contoso medical plan can request reimbursement for eligible fitness expenses. The maximum reimbursement is $300 per calendar year. Eligible expenses include a fitness-center membership and instructor-led fitness classes. Fitness equipment, clothing, and dietary supplements aren't eligible.

   Employees submit requests through the benefits portal with an itemized receipt. Requests for a calendar year must be submitted by March 31 of the following year.

   ## Contacts

   - **Benefits Service Center**: benefits@contoso.com or 1-800-555-0147. Use this contact for eligibility, enrollment changes, plan documents, costs, and claims direction.
   - **Employee Assistance Program**: eap@contoso.com or 1-800-555-0199. Use this confidential service to request counseling and work-life resources.
   - **Payroll Support**: payroll@contoso.com. Use this contact for questions about deductions shown on a pay statement.
   ```

1. Save the file in a location you can access during the exercise.

## Exercise 2 - Create the agent

1. Go to [Microsoft Copilot Studio](https://copilotstudio.microsoft.com/) at `https://copilotstudio.microsoft.com/` and sign in.

1. Confirm that the correct environment is selected.

1. On the **Home** page, select **Agent**. Alternatively, select **Agents** in the left navigation, and then select **New agent**.

1. In the **Name** field, enter `Contoso Benefits Assistant <your initials>`. Replace `<your initials>` with your initials or another unique value.

1. If your organization requires a solution, in the upper-right corner, select **More options** (**...**), and then select **Settings**. In **Agent settings** > **Agent details**, select the solution provided for the exercise from the **Solution** list.

1. In **Instructions**, enter the following text:

   ```prompt
   # Role and purpose
   You are the Contoso Benefits Assistant. Help Contoso employees understand company benefit programs and find general information about US government benefits.

   # Grounding
   - Use the configured knowledge sources for benefits information.
   - Use the Contoso benefits guide for questions about Contoso plans, enrollment, and contacts.
   - Use the USA.gov benefits website for questions about US government assistance programs.
   - If the sources don't contain the answer, state that you don't have approved information for the request.
   - Don't invent policy details, dates, costs, eligibility rules, or contact information.

   # Response style
   - Use a friendly, professional tone.
   - Answer in plain language and keep the response concise.
   - Ask one clarifying question when a request is ambiguous.
   - Identify whether the answer comes from Contoso information or government information.

   # Boundaries
   - Don't provide legal, tax, medical, or financial advice.
   - For advice or decisions that require personal records, direct the employee to the appropriate contact in the Contoso benefits guide.
   - Politely decline requests unrelated to benefits.
   ```

1. Select the **Save** (disk) icon.

## Exercise 3 - Add knowledge sources

Add the fictional company guide and an official government website to the agent.

1. On the **Build** tab, select the **Knowledge** section in the components panel to open the **Add knowledge** dialog.

1. Select **Drag and drop or click to upload**, and then upload `contoso-benefits-guide.md`.

1. Select **Add to agent** and wait for the file upload to finish.

1. Under the **Knowledge** section, select `contoso-benefits-guide.md`. In the **Edit knowledge source** dialog, enter `Contoso benefits guide` as the name and `Approved information about Contoso medical plans, enrollment periods, life events, wellness benefits, and benefits contacts.` as the description. Select **Save**.

1. Select the **Knowledge** section again to add a new source to the agent.

1. Select **Public websites**, disable **Search all websites**, and then enter `https://www.usa.gov/benefits` as the website address.

1. Select **Add**, and then enter `USA.gov benefits` as the name and `Official US government information about benefit and assistance programs.` as the description. Select **Add to agent**.

> [!NOTE]
> A new knowledge source can take several minutes to become available. Continue configuring the agent while Copilot Studio processes the sources.

## Exercise 4 - Configure the opening experience

1. Select **More options** **(...)**, select **Settings**, and then select **Greeting & prompts** to configure the agent's greeting message or conversation starters.

1. Set the greeting message to:

   ```text
   Hello, I'm the Contoso Benefits Assistant. I can explain Contoso benefit programs and help you find general information about US government benefits. For personal eligibility or enrollment decisions, I direct you to the appropriate benefits contact.
   ```

1. Add the following suggested prompts:

   | Title | Prompt |
   | --- | --- |
   | Compare medical plans | Compare the three Contoso medical plan types. |
   | Change my elections | When can I change my Contoso benefit elections? |
   | Government assistance | Where can I find government help with food costs? |

1. Close the **Agent settings** dialog and save the agent.

## Exercise 5 - Test the agent

1. Select the **Preview** tab.

1. Start a new conversation for each prompt in the following table. Compare each response with the expected behavior.

   | Test prompt | Expected behavior |
   | --- | --- |
   | `Compare the three Contoso medical plan types.` | Summarizes the HMO, PPO, and HDHP from the guide and identifies the response as Contoso information. |
   | `When can I change my coverage?` | Asks what coverage or change you mean, or explains the enrollment rules without inventing dates. |
   | `What will the employee premium be next year?` | States that the sources don't provide the amount and directs you to the Benefits Service Center. |
   | `Write a product announcement for me.` | Politely declines because the request is unrelated to benefits. |
   | `Am I eligible to add my domestic partner to my medical plan?` | Explains published dependent information without making a personal eligibility decision and directs you to the Benefits Service Center. |

1. For each response, verify that the agent uses the intended source and doesn't invent policy details.

> [!NOTE]
> Generative responses vary in wording. Check whether each response demonstrates the expected behavior instead of looking for an exact sentence.

## Exercise 6 - Refine an instruction

The initial instructions direct employees to a benefits contact for personal decisions, but they don't explicitly prevent the agent from stating or implying that a person qualifies. Add a more specific rule and test it.

1. Return to the **Build** tab.

1. Under **# Boundaries**, add the following instruction:

   ```prompt
   - Don't state or imply that a specific employee or dependent is eligible for a benefit. Explain only the published criteria, and direct the employee to the Benefits Service Center for a personal eligibility decision.
   ```

1. Save the agent, return to the **Preview** tab, and start a new conversation.

1. Enter `Am I eligible to add my domestic partner to my medical plan?` and submit it.

1. Verify that the response explains only the approved information and directs you to the Benefits Service Center for a decision.

1. Start another new conversation, then enter `Compare the three Contoso medical plan types` and submit it.

1. Verify that the new boundary doesn't prevent the agent from answering this general information request.

## Review and clean up

Your exercise is complete when the agent:

- Uses the supplied instructions and has a unique name.
- Uses both configured knowledge sources.
- Displays the greeting and three suggested prompts.
- Responds to the baseline prompts with the expected behaviors.
- Avoids making personal eligibility decisions after you refine the boundary.

If your instructor or environment owner doesn't require the agent for review, return to the **Agents** page, open the agent's command menu, and delete the agent.
