# Lab 7: Implement prompt action for a quiz generation agent’s topic

Estimated duration - 40 minutes

**Objective:**

Prompt actions are one of the ways to extend Microsoft Copilots. They do this by creating business specific natural language actions. The actions are interpreted by the GPT model to perform the necessary action as instructed. These actions are wrapped within a AI plugin definition, which copilots can invoke at runtime when a matching intent or utterance is encountered.

In this lab, you will learn to create a prompt action for a quiz generation topic which will generate quiz questions based on a given topic.

## Exercise 1: Use natural language to create an agent

1.  Open a browser and login to <https://copilotstudio.microsoft.com/> and login with your lab credentials.

2.  From the **Home page**, in the text area - Start building by describing what your agent needs to do, enter I want you to be a question and answering assistant that can answer common questions from users using the content of a website and click on **Send**.  
    ![Screenshot 1](images/image01.png)

3.  The agent gets created as per the requirements:

![Screenshot 2](images/image02.png)

4.  Scroll down and select **+ Add knowledge** under the Knowledge section.

![Screenshot 3](images/image03.png)

5.  Select the **Public websites** option.

![Screenshot 4](images/image04.png)

6.  Enter www.microsoft.com and select **Add**.

![Screenshot 5](images/image05.png)

7.  Select Add to agent.

![Screenshot 6](images/image06.png)

8.  The website is added as a knowledge source to the agent.  
    ![Screenshot 7](images/image07.png)

9.  Click on **Test** icon to Test the agent. Enter What is Copilot Studio? and hit **Enter**.

![Screenshot 8](images/image08.png)

10. Enter What is the latest xbox model?

![Screenshot 9](images/image09.png)

For both the above questions, you will get an answer from the agent which will be a generic one since the agent will be using its general knowledge.

## Exercise 2: Create a Prompt action for a Topic for generative answers

Use **prompt** in **Copilot Studio** to natural language actions as copilot extensions. These actions use the generative AI models from AI Builder and natural language understanding to address specific scenarios for your copilots. This means you can extend the capabilities of your copilots by simply creating natural language based prompt actions.

In this exercise, you will learn how to add a prompt to action to a topic node

1.  In your agent select the **Topics** tab, select **+ Add a topic** and select **From blank**.

![Screenshot 10](images/image10.png)

2.  Enter the name for the Topic as Generate questions for a quiz. Enter the below details in the **Description**(Select **Copy** option and paste it in the **Description** area).

- create a number of questions for a quiz based on a topic and format the quiz based on the instruction provided

- creates a quiz with a number of questions based on the topic provided and formats the quiz

- generate a quiz with a number of questions using the topic provide and format the questions

- creates questions for a quiz on a specific topic and format

- format a quiz by a number of questions based on the topic provided

Select **Save** on the top right to save the topic.

![Screenshot 11](images/image11.png)

3.  Click on the **+** symbol below the Trigger node. Select the **Add a tool** option and select **New prompt** option under that.

![Screenshot 12](images/image12.png)

4.  The Prompt dialog will appear, and you may see a flyout appear that will guide you on how to create your prompt. Select **Next** to go through the guide.

5.  We'll create prompt that will generate questions for a quiz. Enter the name for the prompt as Quiz Generator .

![Screenshot 13](images/image13.png)

6.  Paste the below content in the Instructions field.

Generate a quiz with \[number\] questions to cover this \[topic\]. Decide on the format, such as multiple-choice questions or true/false statements. Use this \[format\]. Designate the correct answer within parentheses.  
![Screenshot 14](images/image14.png)

7.  Select \[number\], expand **+ Add content** section and select **Text**. Enter the name as number and enter sample data such as 5. Select **Close**.  
    ![Screenshot 15](images/image15.png)

8.  Select **\[topic\]**, expand **+ Add content** section and select **Text**. Enter the name as topic and enter sample data such as Science.  
    ![Screenshot 16](images/image16.png)

9.  Select **\[format\]**, expand **+ Add content** section and select **Text**. Enter the name as format and enter sample data such as bullet points. Select **Save** in the Prompt window.  
    ![Screenshot 17](images/image17.png)

10. The prompt action node will now appear in the authoring canvas of the Topic. Next, the values of the input parameter need to be defined in order for the agent to populate them. Select the **...** icon

![Screenshot 18](images/image18.png)

11. Select the **System** tab and select the **Acivity.Text** as the input value for the action to use the user’s entire response and identify the format value.

![Screenshot 19](images/image19.png)

12. Repeat the same for the remaining input parameters of the prompt action.

![Screenshot 20](images/image20.png)

13. Next, we need to define the output variable of the prompt action. This is so that the response can be referenced downstream in the topic. Select the **\>** icon and in the **Custom** tab, select **Create new** and name the variable as **VarQuizQuestionsResponse**.

![Screenshot 21](images/image21.png)

![Screenshot 22](images/image22.png)

![Screenshot 23](images/image23.png)

14. Below the Prompt action, select the **+** icon to add a new node and select **Send a message**. Select the **{x}** variable icon.

![Screenshot 24](images/image24.png)

15. Select the variable **VarQuizQuestionsResponse.text**. This will add the text property of the prompt action response to the send a message node. Select **Save** to save your topic.

![Screenshot 25](images/image25.png)

16. The Topic details need to be updated next which will be used by your agent to associate the topic with the user's intent when Generative mode is enabled. Select **Details** and enter the following.

    - Display name - generate questions for a quiz

    - Description - This topic creates questions for a quiz based on the number of questions, the topic and format provided by the user

Select **Save** to save your topic.

![Screenshot 26](images/image26.png)

17. Now we are ready to test the agent. Open the Test pane, and enter the following question and observe the output.

Create 5 questions for a quiz based on geography and format the quiz as multi choice

![Screenshot 27](images/image27.png)

![Screenshot 28](images/image28.png)

**Summary**

In this lab, we have learnt how to create a prompt action for a topic by creating a custom prompt and test it.
