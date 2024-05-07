---
lab:
    title: 'Lab: Create a copilot'
---

# Create a copilot

In this exercise, you’ll use Copilot Studio to create a simple copilot that can
answer questions based on topics that you define, and use generative AI to
generate answers based on information in a web site.

This exercise will take approximately 45 minutes to complete.

   > **Note**
   > To complete this exercise, you’ll need a work or school account with
[access to Copilot
Studio](https://learn.microsoft.com/microsoft-copilot-studio/requirements-licensing-subscriptions).
If you don’t already have access to Copilot Studio, depending on the
configuration of your Microsoft 365 organization, you may be able to [create a
trial account](https://aka.ms/trypva).

Create a copilot

Let’s start by using Copilot Studio to create a new copilot. The copilot will
initially have very limited capabilities, which you’ll extend later in the
exercise.

1.  In a web browser, navigate to [Copilot
    Studio](https://copilotstudio.microsoft.com/) at
    https://copilotstudio.microsoft.com/, signing in with your work or school
    account if prompted.

2.  In the navigation pane on the left, view the **Copilots** page, like this:

    ![Screenshot of the Copilots page in Copilot Studio](media/create-copilot/copilots-page.png)

3.  Select the option to create a **New copilot**, and then setup a new copilot
    with the following settings:

    -   **Copilot name**: Power Pilot

    -   **Language**: English (United States) (en-US)

    -   **Website**: *Leave this blank (for now)*

    -   **Advanced options**:

        -   **Copilot icon**: *Choose any icon*

        -   **Lesson topics**: Unselected *(not including lesson topics will
            provide a simple starting point for your copilot)*

        -   **Solution**: Common Data Services Default Solution

        -   **Schema name**: powerPilot

4.  Create the copilot and wait for it to be ready. When it has been
    provisioned, it will look similar to this:

    ![Screenshot of a new copilot in Copilot Studio](media/create-copilot/new-copilot.png)

5.  In the **Test copilot** pane, enter the message Hello, and view the
    response, which should be an appropriate welcome greeting.

6.  Now enter the message How do I use Copilot Studio?, and view the resulting
    response. This time, the response is not quite so helpful. You’ll address
    this in the next procedure.

