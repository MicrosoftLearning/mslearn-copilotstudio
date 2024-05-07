---
lab:
    title: 'Add a topic to your copilot'
---

# Add a topic to your copilot

The conversational capabilities of your copilot are limited by the *topics* it
understands. Topics are the basic building blocks of a copilot in Copilot
Studio, and determine how responses are triggered during chat sessions.

1.  In the navigation pane on the left, select the **Topics** page to see the
    topics defined in your copilot. You can close the **Test copilot** pane to
    make it easier to see them, like this:

    ![Screenshot of the Topics page in Copilot Studio](media/b94eadabd9a5ef0f169ba7ba3386c705.png)

    The copilot has a few standard conversational topics on the **Topics** tab,
    and some additional system topics on the **System** tab. These topics are
    triggered by common phrases entered by the user or by specific events, such
    as errors or the intent of a user-entered phrase being unknown.

2.  On the **Topics** tab, select the **Greeting** topic to view it on the
    *authoring canvas*, which is a visual designer for creating and editing
    topics and looks similar to this:

    ![Screenshot of the authoring canvas for the Greeting topic in Copilot Studio](media/08e6b6d9dd503c3c5e623c2d0fb8a18c.png)

    The *Greeting* topic is triggered by an input in which one of the following
    phrases is present:

    -   *Good afternoon*

    -   *Good morning*

    -   *Hello*

    -   *Hey*

    -   *Hi*

        The response to this trigger is to return a message to the user saying
        *Hello. How can I help you today?*. The inclusion of this topic in the
        copilot in the copilot explains the response you saw previously when
        testing it.

3.  Return to the **Topics** page, and on the **System** tab, select the
    **Fallback** topic to view it on the authoring canvas; where it looks like
    this:

    ![Screenshot of the authoring canvas for the Fallback topic in Copilot Studio](media/80f6b71345565d7484c69d9fa7aa119a.png)

    The *Fallback* topic is triggered when the user enters a phrase for which
    the intent is unknown (there’s no topic with a trigger that understands what
    the user is asking). This topic has a more complex flow than the *Greeting*
    topic: It starts by checking a condition to see if the fallback count (the
    number of times the user has attempted to ask the question) is less than 3,
    and if so it reponds with the message *I’m sorry. I’m not sure how to help
    with that. Can you try rephrasing?* (which you may remember as the reponse
    when you asked how to use Copilot Studio). If the intent is still not
    understood on the third attempt, the topic redirects the conversation flow
    to the *Escalate* topic, which can be used to enable the user to speak to a
    human operator.

4.  Return to the **Topics** page. Then in the **+ Create** menu, select
    **Topic** \> **Create from description with copilot**.

5.  In the **Create a description with copilot** dialog box, name the new topic
    Ask About Copilot Studio and enter the following text to tell copilot what
    the topic should do:

    CodeCopy

    Let the user ask how to use Copilot Studio, and tell them to visit
    https://learn.microsoft.com/microsoft-copilot-studio.

6.  After a short wait, a new topic named *Ask About Copilot Studio* should be
    created and opened in the authoring canvas, where it should look similar to
    this:

    ![Screenshot of the copilot-generated Ask About Copilot Studio topic](media/82ddbabe122ade341ab16294443b5949.png)

    The new topic should be triggered by phrases that ask about Copilot Studio,
    and respond with a message telling the user to visit the Copilot Studio
    documentation web page.

7.  Use the **Save** button (at the top right) to save the new topic in your
    copilot.

8.  Use the **Test copilot** button to re-open the **Test copilot** pane, and
    enter the text How do I use Copilot Studio?. Then view the response, which
    should be based on the topic you just added (even though the text you
    entered doesn’t match any of the phrases in the trigger exactly - it should
    be close enough semantically to trigger the topic).

    **Note**: It’s worth pausing for a second here to think about what you’ve
    just done. You’ve created a copilot in Copilot Studio, in which you used a
    copilot to automatically add a topic that enables a user to ask about
    Copilot Studio! Mind-blowing stuff!

