---
lab:
    title: 'Create copilot actions'
    module: 'Enhance Microsoft Copilot Studio copilots'
---

# Create copilot actions

## Scenario

In this lab, you will:

- Create copilot actions

## What you will learn

- How to add use Power Automate to access data in Microsoft Dataverse

## High-level lab steps

- Create a Power Automate cloud flow to retrieve Dataverse data with a copilot action
- Create a Power Automate cloud flow to create Dataverse data with a copilot action
  
## Prerequisites

- Must have completed **Lab: Work with entities**

## Detailed steps

## Exercise 1 - Create Copilot action to retrieve data from Dataverse

Microsoft Copilot Studio can access data in Microsoft Dataverse using Power Automate cloud flows.

### Task 1.1 - Create Power Automate flow to retrieve a property

1. Navigate to the Microsoft Copilot Studio portal `https://copilotstudio.microsoft.com` and ensure you are in the appropriate environment.

1. Select **Copilots** from the left navigation pane.

1. Select the **Real Estate Booking Service** you created in the earlier lab.

1. Select the **Actions** tab.

1. Select **+ Add an action**.

    ![Screenshot of step 1 of add an action.](../media/add-action-step-1.png)

1. Select the **Flow** filter, then select **Create a new flow**.

1. Sign in to Power Automate if prompted.

    ![Screenshot of Power Automate flow with trigger and response steps.](../media/create-flow-step1.png)

1. Select **Run a flow from Copilot** in the top-left of the screen and enter `Get Property` as the flow name.

1. Select the trigger step **Run a flow from Copilot** and select **+ Add an input**.

1. Select **Text**.

1. Enter `Bedrooms` for **Input** and `Number of Bedrooms` for **Please enter your input**.

    ![Screenshot of trigger properties of the flow.](../media/create-flow-step2.png)

1. Select the **+** icon between the two steps in the flow and select **Add an action**.

1. Enter `Dataverse` in the **Search** field and select **See more** for the **Microsoft Dataverse** connector.

    ![Screenshot of searching for connector in the flow.](../media/create-flow-step3.png)

1. Select the **List rows** action.

1. If prompted for authentication, select **OAuth** and select **Sign in**.

    > **Note:** If you see a '**Failed to create OAuth connection**' error, you may need to allow popups in your browser.

    ![Screenshot of OAuth error.](../media/failed-oauth-popup.png)

    ![Screenshot of allowing popups in Edge.](../media/failed-oauth-popup-2.png)

1. Select **Real Estate Properties** for table name.

1. Enter `contoso_bedrooms eq ` (with a space after **eq**) in the **Filter Rows** field.

1. With the **Filter Rows** field still selected, select the **lightning** icon to its right, then select the **Bedrooms** parameter.

    ![Screenshot of configuring list rows action.](../media/create-flow-step4.png)

1. In the main Power Automate pane, select the **Respond to Copilot** action and select **+ Add an output**.

1. Select **Text**.

1. Enter `PropertyId` for **Enter a name**

1. Select the **Enter a value to respond with** field, and select **fx (Insert Expression)**.

1. Enter the following expression into the top field:

    ```
    first(outputs('List_rows')?['body/value'])['contoso_realestatepropertyid']
    ```

    ![Screenshot of configuring response action.](../media/create-flow-step5.png)

1. Select **Add**.

1. Select **+ Add an output**.

1. Select **Text**.

1. Enter `PropertyName` for **Enter a name**.

1. Select the **Enter a value to respond with** field, and select **fx (Insert Expression)**.

1. Enter the following expression:

    ```
    first(outputs('List_rows')?['body/value'])['contoso_propertyname']
    ```

1. Select **Add**.

1. Select the **Settings** tab in the **Respond to Copilot** pane.

1. Ensure that **Asynchronous Response** is set to **Off**.

    ![Screenshot of response action settings.](../media/create-flow-step6.png)

1. Select **Save** near the upper-right of the page.

1. Wait for the save to complete, then close the Power Automate tab.

### Task 1.2 - Add a Copilot action to retrieve a property

1. Select **Refresh** from the Copilot Studio dialog box to see the new Flow.

1. Select the **Get Property** flow.

    ![Screenshot of step 1 of add a flow action.](../media/add-action-flow-step-1.png)

1. Select **Next**.

1. Select **Next**.

1. Select **Finish**.

### Task 1.3 - Add the Get Property Copilot action to the topic

1. Select the **Topics** tab.

1. Select the **Book a Real Estate Showing** topic.

1. Select the the **+** icon below the **How many bedrooms do you need question?** node, select **Call an action**, then select the **Get Property** flow.

    ![Screenshot of step 2 of add a flow action.](../media/add-action-flow-step-2.png)

1. Select the **NumberofBedrooms** variable for the **Bedrooms** input parameter.

    ![Screenshot of step 3 of add a flow action.](../media/add-action-flow-step-3.png)

1. Select the **three dots** in the **Which property do you want to see?** node and select **Delete**.

1. Select the the **+** icon under the **Action** node and select **Send a message**.

1. In the **Enter a message** field, enter `Property ` (with a space following it).

1. In the same node, select the **{X} (Insert variable)** icon and select the **PropertyName** variable.

    ![Screenshot of step 4 of add a flow action.](../media/add-action-flow-step-4.png)

1. Select **Save**.

## Exercise 2 - Create Copilot action to create data in Dataverse

Microsoft Copilot Studio can ceate data in Microsoft Dataverse using Power Automate cloud flows.

### Task 2.1 - Create Power Automate flow to make a booking

1. Select the **Actions** tab in **Real Estate Booking Service**.

1. Select **+ Add an action**.

1. Scroll down and select **Create a new flow**.

1. Select **Run a flow from Copilot** in the top-left of the screen and enter `Create Booking Request` as the flow name.

1. Select the trigger step **Run a flow from Copilot** and select **+ Add an input**.

1. Select **Text**.

1. Enter `PropertyId` for **Input** and `Property` for **Please enter your input**.

1. Select **+ Add an input**.

1. Select **Text**.

1. Enter `ViewerName` for **Input** and `Viewer Name` for **Please enter your input**.

1. Select **+ Add an input**.

1. Select **Text**.

1. Enter `ViewerEmail` for **Input** and `Viewer Email` for **Please enter your input**.

    ![Screenshot of configuring flow parameters action.](../media/create-flow2-step1.png)

1. Select the **+** icon between the two steps in the flow and select **Add an action**.

1. Enter `Dataverse` in the **Search** field and select **See more** for the **Microsoft Dataverse** connector.

1. Select the **Add a new row** action.

1. Select **Booking Requests** for table name.

1. Enter `Copilot booking` in the **Booking Name** field.

1. Select **Show all** under **Advanced parameters**.

1. Enter `contoso_bookingrequests()` in the **Property (Real Estate Properties)** field, move the cursor within the parentheses, select the **lightning** icon, then select the **PropertyId** parameter.

1. Select the **Viewer Email** field, select the **lightning** icon, then select the **ViewerEmail** parameter.

1. Select the **Viewer Name** field, select the **lightning** icon, then select the **ViewerName** parameter.

    ![Screenshot of configuring flow add row action.](../media/create-flow2-step2.png)

1. Select the **Respond to Copilot** action.

1. Select the **Settings** tab.

1. Ensure that **Asynchronous Response** is set to **Off**.

1. Select **Save** in the upper-right of the window.

1. Wait for the save to complete, then close the Power Automate tab.

### Task 2.2 - Add a Copilot action to create a booking request

1. Select **Refresh** from the Copilot Studio dialog box to see the new Flow.

1. Select the **Create Booking Request** flow.

1. Select **Next**.

1. Select **Next**.

1. Select **Finish**.

### Task 2.3 - Add the Create Booking Request Copilot action to the topic

1. Select the **Topics** tab.

1. Select the **Book a Real Estate Showing** topic.

1. Select the the **+** icon below the **What date and time do you want to see the property?** node, select **Call an action**, then select the **Create Booking Request** flow.

1. Select the **PropertyId** variable for the **PropertyId** input parameter.

1. Select the **Name** variable for the **ViewerName** input parameter.

1. Select the **EmailAddress** variable for the **ViewerEmail** input parameter.

1. Select the the **+** icon below the new **Action** node, select **Topic management**, select **Go to another topic** and select **End of Conversation**.

1. Select **Save**.

1. Select **Publish** and select **Publish** again.

## Exercise 3 - Test the copilot actions

### Task 3.1 - Make a booking request

1. If closed, select the **Test** button in the upper-right of the screen to open the testing panel.

1. Select the **three dots** at the top of the testing panel in the upper-right of the screen.

    ![Screenshot of the Testing panel options.](../media/test-pane-options.png)

1. If it's not enabled, enable **Track between topics**.

1. Select the **Start a new conversation** icon at the top of the testing panel.

1. When the **Conversation Start** message appears, your copilot will start a conversation. In response, enter a trigger phrase for the topic that you've created:

    `I want to book a real estate showing`

1. Enter the following information:

    ```
    Name: <Your name>
    Email address: <Your email address>
    ```

1. After you supply the information, an Adaptive Card displays the information that you entered and asks if the details are correct. Select **Yes**.

1. Select **House** for the type of property prompt.

1. Enter `3` for the number of bedrooms prompts.

    ![Screenshot of the test pane with the information entered.](../media/test-pane-action-results.png)

1. Enter `Tomorrow 2:00 PM` to the **What date and time do you want to see the property?** prompt.

1. Select **Yes** to the **Did that answer your question?** prompt.

1. Select any rating.

1. Select **No** to the **Can I help with anything else?** prompt.

### Task 3.2 - Verify the booking request

1. If it's not still open, navigate to `https://make.powerapps.com` in a new tab.

1. Make sure you are in the appropriate environment.

1. Select **Play** on the **Real Estate Property Management** Model-Driven App.

1. In the left navigation, select **Booking Requests**.

    ![Screenshot of Maker portal showing booking request data.](../media/booking-request-row.png)
