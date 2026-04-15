# Add Dataverse to the default environment
1. Open a web browser, navigate to `https://admin.powerplatform.microsoft.com/manage/environments`, and sign in using your credentials for this exercise. If prompted, choose the option to stay signed in.
1. Close any pop-up messages that are displayed.
1. Select the ellipses (**...**) for the **Contoso (default)** environment and select **Add Dataverse**.
1. Leave all of the default settings and select **Add**.

# Create an environment
Before you start the lab exercise, let's create a development environment for you to work in.

1. **Refresh** the **Environments** list.
2. Select **+New** to create a new environment with the following settings:
    - **Name**: *Your name*
    - **Make this a Managed Environment**: *No*
    - **Group**: *None*
    - **Region**: ***default** region*
    - **Get new features early**: No
    - **Type**: Developer
    - **Create on behalf**: *No*
    - **Add a Dataverse data store**: Yes
    - **Pay-as-you-go with Azure**: No
    - **Add Dataverse options**:
        - **Language**: English
        - **Currency**: USD ($)
        - **Deploy sample apps and data**: No
1. **Save** and wait until the state of your environment is **Ready** (you can use the **Refresh** button to update the display)
1. Navigate to `https://copilotstudio.microsoft.com/` (sign in with your credentials if prompted).
1. Skip any welcome messages.
