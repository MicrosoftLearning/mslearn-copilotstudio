---
lab:
  title: ILT Setup
  module: Introduction
  description: In this exercise, you will access the Microsoft Copilot Studio portal and create an environment and solution to use throughout the remaining labs.
  duration: 10 minutes
  level: 200
  islab: true
  primarytopics:
    - Microsoft Copilot
    - Microsoft Copilot Studio
---

## Exercise 1 - Create a Power Platform environment

### Task 1.1 - Power Platform Admin Center

Before you start the lab exercises, you must create a development environment for you to work in.

1. Open a web browser, navigate to `https://admin.powerplatform.microsoft.com/manage/environments`, and sign in using your credentials for this exercise.

1. If prompted, choose the option to stay signed in.

1. Close any pop-up messages that are displayed.

### Task 1.2 - Add Dataverse to the default environment

1. Select the ellipses (**...**) for the **Contoso (default)** environment and select **Add Dataverse**.

   ![Add Dataverse to the default environment in the Power Platform Admin center.](../media/add-dataverse.png)

1. Leave all of the default settings and select **Add**.

### Task 1.3 - Create a new environment

1. In the **Environments** page, select **+ New** to create a new environment with the following settings:

   - **Type**: Developer
   - **Region**: default region
   - **Name**: *Your name*
   - **Environment group**: None
   - **Make this a Managed Environment**: No
   - **Get new features early**: No
   - **Create on behalf**: No

   ![Create an environment in the Power Platform Admin center.](../media/create-environment.png)

1. Select **Next** and in the **Add Dataverse** section:

   - **Language**: English (United States)
   - **Currency**: USD ($)
   - **Deploy sample apps and data**: No

1. Select **Save** and wait until the state of your environment is **Ready** (you can use the **Refresh** button to update the display).

   > [!NOTE]
   > Environment provisioning can take several minutes depending on tenant configuration.

   ![Environment created in the Power Platform Admin center.](../media/environment-created.png)

1. In a new browser tab, navigate to `https://copilotstudio.microsoft.com/` and sign in if prompted.

  > [!NOTE]  
  > If you experience issues loading Copilot Studio or your environment:
  > - First, capture your environment ID (GUID) from the Power Platform admin center:
  >   1. Open the environment you created at `https://admin.powerplatform.microsoft.com/manage/environments`.
  >   2. Locate the environment ID in the URL (a long string such as `12345678-90ab-cdef-1234-567890abcdef`).
  >   3. Copy and save this value.
  > - Then try accessing your environment directly by pasting your ID into the following URL:
  >   ```
  >   https://copilotstudio.microsoft.com/environments/<your-environment-id>/home
  >   ```

1. If prompted, select **Get Started** and keep the default country or region settings.

1. Skip any welcome messages.

1. In the upper right corner of the page, switch environments by using the Environment Selector and select the environment you created.

   ![Select your environment in the Copilot Studio.](../media/select-environment.png)

### Task 1.4 - Create a solution

1. In the left navigation pane, select the ellipses (**...**), and select **Solutions**.

1. You should see several solutions including the *Default Solution* and the *Common Data Services Default Solution*.

   ![List of solutions in Maker portal.](../media/solutions-list.png)

1. Select **+ New solution**.

1. In the **Display name** text box, enter **`Lab Exercises`**

1. Verify that **Name** is automatically populated.

1. Select **+ New publisher** below the **Publisher** drop-down.

1. For **Display name**, enter `Fabrikam`

1. For **Name**, enter `fabrikam`

1. For **Prefix**, enter `fab`

   ![New publisher.](../media/new-publisher.png)

1. Select **Save**.

1. Verify that **Fabrikam (fabrikam)** is selected in the **Publisher** drop-down.

1. Select the **Set as your preferred solution** checkbox.

   > [!NOTE]
   > Setting this as your preferred solution ensures new assets created during later labs are added to the Lab Exercises solution by default.

   ![New solution.](../media/new-solution.png)

1. Select **Create**.

1. Close the **Solutions** browser tab.

1. Refresh the **Copilot Studio** page.

You now have a Power Platform environment and solution to work in.
