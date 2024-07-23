---
lab:
    title: 'Import Dataverse solution'
    module: 'Course Introduction'
---

# Validate lab environment

In this exercise, you'll import a Dataverse solution to use for the following labs.

> **Note**: This exercise assumes you already have a Copilot Studio license or have signed up for a [free trial](https://go.microsoft.com/fwlink/p/?linkid=2252605) and have a Power Apps environment to work in.

## Exercise 1 – Import solution

In this exercise, you will import a Dataverse solution into your environment that contains the tables needed for the labs.

### Task 1.1 – Sign in to Power Apps

1. In a new browser tab, navigate to `https://make.powerapps.com`.

1. If prompted for credentials, sign in with your email address and password if prompted.

1. If prompted for contact information, leave the Country/region as the default value and enter `0123456789` for Phone number and select **Submit**.

1. In the upper-right of the screen, verify that the **Environment** is set to your environment. This is where you will be working for the entirety of the labs. If it is not, select the appropriate environment.

### Task 1.2 – Download solution

1. Download [**Bookings_1_0_0_0.zip**](../../Allfiles/Bookings_1_0_0_0.zip) from GitHub. The file is located at `https://github.com/MicrosoftLearning/mslearn-copilotstudio/blob/main/Allfiles/Bookings_1_0_0_0.zip`

### Task 1.3 – Import solution

1. Navigate to `https://make.powerapps.com`.

1. Make sure you are in the appropriate environment.

1. Select **Solutions**.

1. Select **Import solution**.

1. Select **Browse** and locate the **Bookings_1_0_0_0.zip** file and select **Open**.

    ![Solution to import.](../media/solution-to-import.png)

1. Select **Next**.

1. Select **Import**.

    The solution will import in the background. This may take a few minutes.

    ![Solution imported.](../media/solution-imported.png)

    > **Alert:** Wait until the solution has finished importing before continuing to the next step.

1. When the solution has imported successfully, open the **Bookings** solution.

1. In the solution, select the **Overview** page.

    ![Solution Overview tab.](../media/solution-overview.png)

1. Select **Publish all customizations**.

### Task 1.4 – Test data

1. In the solution, select the **Objects** page.

1. Select the **ellipsis …** menu for the **Real Estate Property Management** model-driven app, and select **Play**.

    ![Overview.](../media/play-app.png)

1. Select **+ New**.

1. Enter the following data:

    - **Property Name:** `1100 High Villas`
    - **Owner:** select any owner
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
    - **Owner:** select any owner
    - **Asking Price:** `300,000`
    - **Street:** `Oak Lane`
    - **City:** `Denver`
    - **Bedrooms:** `4`
    - **Bathrooms:** `3`

    ![Overview.](../media/add-record.png)

1. Select **Save & Close**.
