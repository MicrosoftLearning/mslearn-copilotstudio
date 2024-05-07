---
lab:
    title: 'Add Generative AI support'
---

# Add Generative AI support

You can add topics for all of the inputs that you expect a user to enter; but
you can’t realistically expect to know every question that will be asked. The
*Fallback* topic at least ensures that the user is informed that their question
wasn’t understood; but it would be better if the copilot had access to some
knowledge that isn’t “hard-coded” in its topic definitions, and which could be
used to generate appropriate responses to questions.

To support this scenario, you can enable *Generative answers*; which uses a
generative AI model to try to answer a user question based on a source of data,
such as a web site.

1.  In the navigation pane on the left, select the **Overview** page. Once
    again, you can close the **Test copilot** pane to see the page more easily:

    ![Screenshot of the Overview page in Copilot Studio](media/636521fcb34318c97b616c0389e1663b.png)

2.  In the **Set up your generative AI** section, under **Add a website**, enter
    https://www.microsoft.com/en-us/power-platform and add it to the copilot.
    After a short time, the **Generative AI** page will be displayed with the
    URL you entered added to the websites for this copilot.

3.  Scroll to the bottom of the **Generative AI** page until you see a box in
    which you can enter **Instructions** to describe how the copilot should
    behave. These instructions are used in the prompt for a generative model to
    influence the responses that are returned. Enter the following instructions:

    CodeCopy

    Answer the user's question politely, finishing with the phrase "This
    response was generated using AI.".

4.  Use the **Save** button (at the top left) to save the changes you have made.
    The copilot is configured to boost conversational capability with generative
    AI (which may take a few seconds).

5.  Open the **Test copilot** pane and enter the question What are components of
    Power Platform?.

6.  View the response, which should be based on information from the website you
    entered (with references) and end with the phrase *This response was
    generated using AI.*.
