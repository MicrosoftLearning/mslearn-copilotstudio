---
lab:
    title: 'Import Dataverse solution'
    module: 'Build an initial agent with Microsoft Copilot Studio'
---

# Import Dataverse solution

In this exercise, you'll import a Dataverse solution to use in the following labs.

This exercise will take approximately **10** minutes to complete.

> **Note**: This exercise assumes you already have a Copilot Studio license or have signed up for a [free trial](https://go.microsoft.com/fwlink/p/?linkid=2252605) and have a Power Platform environment to work in.

## Exercise 1 – Import solution

In this exercise, you will import a Dataverse solution into your environment that contains the tables needed for the labs.

### Task 1.1 – Download solution

1. In a new browser tab, navigate to `https://github.com/MicrosoftLearning/mslearn-copilotstudio/raw/main/Allfiles/Bookings_1_0_0_0.zip` to download the **Bookings_1_0_0_0.zip** file.

### Task 1.2 – Import solution

1. In a new browser tab, navigate to `https://make.powerapps.com`.

1. If prompted for credentials, sign in with your email address and password.

1. If prompted for contact information, set the Country/region and select **Get Started**.

1. In the upper-right of the screen, verify that the **Environment** is set to your environment. This is where you will be working for the entirety of the labs. If it is not, select the appropriate environment.

1. In the left navigation, select **Solutions**.

1. In the top bar, select **Import solution**.

1. Select **Browse** and locate the **Bookings_1_0_0_0.zip** file from your Downloads folder and select **Open**.

    ![Solution to import.](../media/solution-to-import.png)

1. Select **Next**.

1. Select **Import**.

    The solution will import in the background. This may take a few minutes. You may refresh the window.

    ![Solution imported.](../media/solution-imported.png)

    > **Alert:** Wait until the solution has finished importing before continuing to the next step.

1. When the solution has imported successfully, open the **Bookings** solution.

1. In the left navigation, select the **Overview** tab.

    ![Solution Overview tab.](../media/solution-overview.png)

1. Select **Publish all customizations**.

### Task 1.3 – Set preferred solution

1. Select **Solutions**.

1. Select **Manage** in the *Current preferred solution* tile.

1. Select **Bookings (contoso)**.

1. Select **Apply**.

### Task 1.4 – Test data

1. In the left navigation of the Bookings solution, select the **Objects** tab.

1. Select the **ellipses …** menu for the **Real Estate Property Management** Model-Driven App, and select **Play**. This is a simple model-driven app that will allow you to create new Real Estate Property records.

    ![Overview.](../media/play-app.png)

1. Select **+ New**.

1. Enter the following data:

    - **Property Name:** `1100 High Villas`
    - **Owner:** Select your user (search for your provided username)
    - **Asking Price:** `250,000`
    - **Street:** `Main Avenue`
    - **City:** `Redmond`
    - **Bedrooms:** `3`
    - **Bathrooms:** `2`

    ![Overview.](../media/add-record.png)

1. Select **Save & Close**.

1. Select **+ New**.

1. Enter the following data:

    - **Property Name:** `555 Oak Lane`
    - **Owner:** Select your user
    - **Asking Price:** `300,000`
    - **Street:** `Oak Lane`
    - **City:** `Denver`
    - **Bedrooms:** `4`
    - **Bathrooms:** `3`

    ![Overview.](../media/add-record2.png)

1. Select **Save & Close**.

You now have 2 Active Real Estate Properties in the view.
