**Lab 8: Implement prompt action for a quiz generation agent's topic**

**Objective:**

Prompt actions are one of the ways to extend Microsoft Copilots. They do
this by creating business specific natural language actions. The actions
are interpreted by the GPT model to perform the necessary action as
instructed. These actions are wrapped within a AI plugin definition,
which copilots can invoke at runtime when a matching intent or utterance
is encountered.

In this lab, you will learn to create a prompt action for a quiz
generation topic which will generate quiz questions based on a given
topic.

Estimated duration - 40 minutes

## Exercise 1: Use natural language to create an agent

1.  Open a browser and login to
    +++<https://copilotstudio.microsoft.com/+++> and login with your lab
    credentials.

2.  From the **Home page**, in the text area - Start building by
    describing what your agent needs to do, enter +++I want you to be a
    question and answering assistant that can answer common questions
    from users using the content of a website+++ and click on **Send**.\
    ![](media/media/image1c.png){width="6.010416666666667in"
    height="1.75in"}

3.  The agent gets created as per the requirements:

![](media/media/image1d.png){width="5.270895669291338in"
height="3.4895833333333335in"}

4.  Scroll down and select **+ Add knowledge** under the Knowledge
    section.

![](media/media/image1e.png){width="4.354181977252844in"
height="2.697949475065617in"}

5.  Select the **Public websites** option.

![A screenshot of a computer AI-generated content may be
incorrect.](media/media/image4.png){width="6.268055555555556in"
height="3.911111111111111in"}

6.  Enter +++www.microsoft.com+++ and select **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](media/media/image5.png){width="6.268055555555556in"
height="3.9520833333333334in"}

7.  Select Add to agent.

![A screenshot of a computer AI-generated content may be
incorrect.](media/media/image6.png){width="6.268055555555556in"
height="3.904166666666667in"}

8.  The website is added as a knowledge source to the agent.\
    ![](media/media/image1f.png){width="6.010416666666667in"
    height="4.385416666666667in"}

9.  Click on **Test** icon to Test the agent. Enter +++What is Copilot
    Studio?+++ and hit **Enter**.

![](media/media/image20.png){width="6.260416666666667in"
height="5.822916666666667in"}

10. Enter +++What is the latest xbox model?+++

![](media/media/image21.png){width="6.260416666666667in"
height="5.78125in"}

For both the above questions, you will get an answer from the agent
which will be a generic one since the agent will be using its general
knowledge.

## Exercise 2: Create a Prompt action for a Topic for generative answers

Use **prompt** in **Copilot Studio** to natural language actions as
copilot extensions. These actions use the generative AI models from AI
Builder and natural language understanding to address specific scenarios
for your copilots. This means you can extend the capabilities of your
copilots by simply creating natural language based prompt actions.

In this exercise, you will learn how to add a prompt to action to a
topic node

1.  In your agent select the **Topics** tab, select **+ Add a
    topic** and select **From blank**.

![A screenshot of a computer AI-generated content may be
incorrect.](media/media/image10.png){width="6.268055555555556in"
height="3.3118055555555554in"}

2.  Enter the name for the Topic as +++Generate questions for a quiz+++.
    Enter the below details in
    the **Description**(Select **Copy** option and paste it in
    the **Description** area).

- create a number of questions for a quiz based on a topic and format
  the quiz based on the instruction provided

- creates a quiz with a number of questions based on the topic provided
  and formats the quiz

- generate a quiz with a number of questions using the topic provide and
  format the questions

- creates questions for a quiz on a specific topic and format

- format a quiz by a number of questions based on the topic provided

Select **Save** on the top right to save the topic.

![](media/media/image11.png){width="6.268055555555556in"
height="3.089583333333333in"}

3.  Click on the **+** symbol below the Trigger node. Select the **Add a
    tool** option and select **New prompt** option under that.

![](media/media/image12.png){width="6.268055555555556in"
height="3.9131944444444446in"}

4.  The Prompt dialog will appear, and you may see a flyout appear that
    will guide you on how to create your prompt. Select **Next** to go
    through the guide.

5.  We\'ll create prompt that will generate questions for a quiz. Enter
    the name for the prompt as +++Quiz Generator +++.

![](media/media/image22.png){width="6.260416666666667in"
height="3.1145833333333335in"}

6.  Paste the below content in the Instructions field.

+++Generate a quiz with \[number\] questions to cover this \[topic\].
Decide on the format, such as multiple-choice questions or true/false
statements. Use this \[format\]. Designate the correct answer within
parentheses.+++\
![](media/media/image23.png){width="6.260416666666667in"
height="1.34375in"}

7.  Select \[number\], expand **+ Add content** section and
    select **Text**. Enter the name as +++number+++ and enter sample
    data such as +++5+++. Select **Close**.\
    ![](media/media/image24.png){width="6.010416666666667in"
    height="5.416666666666667in"}

8.  Select **\[topic\]**, expand **+ Add content** section and
    select **Text**. Enter the name as +++topic+++ and enter sample data
    such as +++Science+++.\
    ![](media/media/image25.png){width="6.010416666666667in"
    height="5.072916666666667in"}

9.  Select **\[format\]**, expand **+ Add content** section and
    select **Text**. Enter the name as +++format+++ and enter sample
    data such as +++bullet points+++. Select **Save** in the Prompt
    window.\
    ![](media/media/image26.png){width="6.010416666666667in"
    height="3.40625in"}

10. The prompt action node will now appear in the authoring canvas of
    the Topic. Next, the values of the input parameter need to be
    defined in order for the agent to populate them. Select
    the **\...** icon

![](media/media/image17.png){width="6.268055555555556in"
height="4.888888888888889in"}

11. Select the **System** tab and select the **Acivity.Text** as the
    input value for the action to use the user's entire response and
    identify the format value.

![](media/media/image18.png){width="5.597222222222222in"
height="6.465277777777778in"}

12. Repeat the same for the remaining input parameters of the prompt
    action.

![](media/media/image19.png){width="6.268055555555556in"
height="4.593055555555556in"}

13. Next, we need to define the output variable of the prompt action.
    This is so that the response can be referenced downstream in the
    topic. Select the **\>** icon and in the **Custom** tab,
    select **Create new** and name the variable as
    +++**VarQuizQuestionsResponse**+++.

![](media/media/image20.png){width="6.268055555555556in"
height="3.6333333333333333in"}

![](media/media/image21.png){width="6.268055555555556in"
height="3.0444444444444443in"}

![](media/media/image22.png){width="6.268055555555556in"
height="4.124305555555556in"}

14. Below the Prompt action, select the **+** icon to add a new node and
    select **Send a message**. Select the **{x}** variable icon.

> ![](media/media/image23.png){width="6.268055555555556in"
> height="2.9902777777777776in"}

15. Select the variable **VarQuizQuestionsResponse.text**. This will add
    the text property of the prompt action response to the send a
    message node. Select **Save** to save your topic.

![](media/media/image24.png){width="6.268055555555556in"
height="4.674305555555556in"}

16. The Topic details need to be updated next which will be used by your
    agent to associate the topic with the user\'s intent when Generative
    mode is enabled. Select **Details** and enter the following.

    - Display name - +++generate questions for a quiz+++

    - Description - +++This topic creates questions for a quiz based on
      the number of questions, the topic and format provided by the
      user+++

Select **Save** to save your topic.

![](media/media/image25.png){width="6.268055555555556in"
height="6.747916666666667in"}

17. Now we are ready to test the agent. Open the Test pane, and enter
    the following question and observe the output.

+++Create 5 questions for a quiz based on geography and format the quiz
as multi choice+++

![](media/media/image26.png){width="6.268055555555556in"
height="3.2569444444444446in"}

![](media/media/image27.png){width="4.6875in"
height="6.861111111111111in"}

**Summary**

In this lab, we have learnt how to create a prompt action for a topic by
creating a custom prompt and test it.
