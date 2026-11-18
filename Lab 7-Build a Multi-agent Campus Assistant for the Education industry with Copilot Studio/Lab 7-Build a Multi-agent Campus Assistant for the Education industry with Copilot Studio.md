# Build a Multi-agent Campus Assistant for the Education Industry with Copilot Studio

**Duration:** 50 minutes 

## Lab Overview

Riverbend University, home to about 18,000 students, sees the same
requests flood in every semester: fee balance checks, exam timetable
questions, admissions queries and certificate requests. An audit found
roughly 70% of the 6,400 helpdesk tickets last semester were repetitive,
two-minute questions buried behind a multi-day queue.

Priya Nair, Director of IT Services, has approved a pilot: one AI
assistant that gives students instant, accurate answers without them
needing to know which department holds the data. The hard rule is **no
guessing**. Fee, grade, and exam data must come from the official
student record files, and general answers must come from official
university documents.

In this lab, you will build the entire solution inside Copilot Studio.
You will create **Atlas**, the orchestrator agent, and a **Campus
Services Agent** that answers student-specific questions from uploaded
student record files. You will also add an agent flow that submits
bonafide certificate requests, then publish Atlas and test it as a
student.

### Lab Objectives

By the end of this lab, you will be able to:

- Build an orchestrator agent in Copilot Studio that grounds its answers
  in uploaded knowledge.

- Build a specialist agent that answers fee, grade and exam questions
  from uploaded student record files.

- Connect the specialist agent to the orchestrator as a connected agent.

- Create an agent flow, with student confirmation, to process bonafide
  certificate requests.

- Publish the agent and test the end-to-end student experience from
  Copilot Studio.

### Time Plan

[TABLE]

## Lab Prerequisites

- Access to Microsoft Copilot Studio at
  https://copilotstudio.microsoft.com with the lab credentials provided.

- The following files are available in C:\Labfiles\CampusFiles:
  Campus_faq.pdf, Student_handbook.pdf, Exam_regulation.pdf,
  Admission_faq.pdf, Student_Records.csv, Grade_Cards.csv, and
  Exam_Timetable.csv.

- The three CSV files hold the sample student data (IDs such as STU002,
  STU003 and STU007) that the Campus Services Agent answers from.

- Basic familiarity with the Copilot Studio authoring canvas.

## Exercise 1: Build Atlas, the Orchestrator Agent

Atlas is the single front door for every student interaction. You will
create it, give it routing instructions, and ground it in general
university documents.

### Task 1: Create and Configure the Atlas Agent

1.  Navigate to
    [*https://copilotstudio.microsoft.com/*](https://copilotstudio.microsoft.com/)
    and login with your credentials.

2.  From the Copilot Studio home page, select **Agents** from the left
    navigation menu, and then select **New agent**.  
    ![](./media/image15.png)

3.  In the **Name** field, enter +++Atlas+++

4.  In the **Instructions** field, enter the following:

You are Atlas, the university's intelligent student support assistant.  
  
Your responsibilities:  
- Welcome students and answer general university-related questions using
your own knowledge sources.  
- Route any request involving fees, certificates, enrolment, grades,
GPA, exam timetables, admissions, or eligibility to the Campus Services
Agent.  
- Coordinate responses when a request involves both a general question
and a specialist request: answer the general part yourself, delegate the
specialist part, and combine both into a single clear reply.  
  
Guidelines:  
- Be friendly, concise, and professional in every response.  
- Do not answer on behalf of the Campus Services Agent when the request
should be delegated.  
- Do not make up information. Use the connected agent and available
knowledge sources to provide accurate responses.  
- If you cannot find sufficient information, politely inform the student
and recommend contacting the university helpdesk.

![](./media/image4.png)

5.  Select **Create**.

### Task 2: Ground Atlas in General University Knowledge

1.  On the Atlas **Overview** page, scroll to the **Knowledge**
    section.  
    ![](./media/image21.png)

2.  Turn off **Use general knowledge** and **Web search** so Atlas
    answers only from trusted sources.  
    ![](./media/image44.png)

3.  Select **Add knowledge**, then select **Files**.

4.  Select **Select files to upload**, browse to
    C:\Labfiles\CampusFiles, and select **Campus_faq.pdf** and
    **Student_handbook.pdf**.  
    ![](./media/image35.png)

5.  Select **Open**, and then select **Add to agent**.

6.  Wait until both files show a status of **Ready**.  
    ![](./media/image36.png)

7.  Publish the agent.  
    ![](./media/image6.png)

### 

### Task 3: Test Atlas

1.  Move to the **Preview** tab, enter the following prompt and press
    Enter:

+++Hi Atlas! Can you introduce yourself and explain how you can help
me?+++  
![](./media/image3.png)

2.  Review the response. Confirm Atlas introduces itself, describes its
    role and mentions the categories of help it provides.  
    ![](./media/image8.png)

## Exercise 2: Build the Campus Services Agent 

Fee balances, grades and exam schedules are student-specific. In this
exercise, you will build a specialist agent that answers them only from
the uploaded student record files.

### Task 1: Create and Configure the Campus Services Agent

1.  From the left navigation menu, select **Agents**, and then select
    **New agent**.  
    ![](./media/image13.png)

2.  In the **Name** field, enter +++Campus Services Agent+++

3.  In the **Instructions** field, enter the following:

You are the Campus Services Agent for Riverbend University. You work as
a connected agent for Atlas. Atlas delegates to you whenever a student
needs fee, certificate, enrolment, grade, GPA, exam timetable, or
admissions information.  
  
Responsibilities:  
- Fee balances and enrolment status: answer only from
Student_Records.csv.  
- Grades, GPA, and academic performance: answer only from
Grade_Cards.csv. Summarize GPA, semester, subject grades and overall
standing. If no record exists, say that no academic record was found.  
- Exam timetable, dates, and venues: answer only from
Exam_Timetable.csv.  
- Admissions questions (eligibility, required documents, application
process, deadlines): answer only from Admission_faq.pdf. If the answer
is not there, recommend contacting the Admissions Office.  
  
Guidelines:  
- Before returning any student-specific information, ask for the Student
ID if it has not been provided.  
- Verify the Student ID exists in Student_Records.csv before returning
any fee, grade, or exam data.  
- Never guess or invent fees, grades, exam schedules, or admissions
policy. If information cannot be found, say so clearly and recommend
contacting the relevant office.  
- Return concise, structured responses suitable for Atlas to present to
students.

![](./media/image22.png)

5.  Select Save.  
    ![](./media/image27.png)

6.  On the agent **Overview** page, scroll to **Knowledge** and turn off
    **Web search**.  
    ![](./media/image7.png)

### Task 2: Add Admissions Knowledge and Student Records

1.  Under **Knowledge**, select **Add knowledge**, then select
    **Files**.

2.  Upload **Exam_regulation.pdf**, **Admission_faq.pdf**,
    **Student_Records.csv**, **Grade_Cards.csv** and
    **Exam_Timetable.csv** from C:\Labfiles\CampusFiles.  
    ![](./media/image43.png)

3.  Select **Add to agent** and wait until all five files show
    **Ready**.  
    ![](./media/image30.png)

### Task 3: Publish and Test the Agent

1.  Select **Publish** at the top right, and then select **Publish**
    again to confirm.

2.  In the **Preview tab**, enter +++What is the fee balance for Student
    ID STU007?+++ and confirm the agent returns fee details.”  
    ![](./media/image23.png)

> ![](./media/image11.png)

3.  Enter +++What are my exam dates? My Student ID is STU003.+++ and
    confirm the agent returns the timetable entries.  
    ![](./media/image28.png)

## Exercise 3: Connect the Campus Services Agent to Atlas

### Task 1: Connect the Specialist Agent

1.  From the left navigation menu, select **Agents**, and open
    **Atlas**.  
    ![](./media/image20.png)

2.  On the **Build** page, select **Connected Agents.  **
    ![](./media/image26.png)

3.  Select **Connect to an existing agent**, and then select **Campus
    Services Agent**.  
    ![](./media/image46.png)

4.  In the **Description** field, enter the following:

Handles fee balances, certificate requests, enrolment verification,
grades, GPA, exam timetables, and admissions questions (eligibility,
documents, application process, deadlines). Combines student record
files with knowledge sources to deliver accurate, data-grounded answers
on Atlas's behalf.

![](./media/image37.png)

5.  Select **Add and configure**, and confirm the agent now appears in
    the **Agents** section.  
    ![](./media/image40.png)

6.  Select **Publish**, and then **Publish** again.  
    ![](./media/image18.png)

### Task 2: Validate Delegation

1.  In the **Preview tab** for Atlas, enter: +++I want to check my fee
    balance. My Student ID is STU007.+++  
    ![](./media/image33.png)

2.  Review the response. In the activity map, confirm Atlas called the
    Campus Services Agent.

> ![](./media/image45.png)

3.  Return to Atlas and enter: +++Can you show me my grade card? Student
    ID STU003.+++  
    ![](./media/image38.png)

4.  Confirm the agent returns GPA and subject grades that match
    **Grade_Cards.csv**.  
    ![](./media/image39.png)

## Exercise 4: Create the Certificate Request Flow

A certificate request should only be submitted once the student confirms
it. In this exercise, you will build an agent flow that submits a
bonafide certificate request and returns a reference number, and
instruct the agent to collect the student's confirmation in chat first.

### Task 1: Create the Agent Flow

1.  Open the **Campus Services Agent**, select the **Tools** tab, and
    then select **Add tool**.  
    ![](./media/image25.png)

2.  Select **New tool**, and then select **Agent flow**.  
    ![](./media/image31.png)

3.  Select the **When an agent calls the flow** trigger. Select **Add an
    input**, choose **Text**, and name it +++StudentID+++  
    ![](./media/image29.png)

> ![](./media/image10.png)

4.  Repeat to add two more **Text** inputs: +++StudentEmail+++ and
    +++RequestPurpose+++  
    ![](./media/image2.png)

5.  Select the **+** icon below the trigger, search for +++Compose+++,
    and select **Compose** under **Data Operation**.  
    ![](./media/image24.png)

6.  In the **Inputs** field, select the **fx** icon, enter
    +++concat('BON-', formatDateTime(utcNow(), 'yyyyMMddHHmmss'))+++ and
    select **Add**.  
    ![](./media/image32.png)

> ![](./media/image1.png)
>
> ![](./media/image5.png)

7.  Select the **+** icon below the action and search for +++Respond to
    the agent+++.  
    ![](./media/image41.png)

8.  Select **Add an output**, choose **Text**, and enter +++Status+++ as
    the name with +++Sent+++ as the value.

9.  Select **Add an output** again, choose **Text**, enter
    +++ReferenceID+++ as the name, and select the lightning icon to
    choose the **Outputs** of the **Compose** action as the value.

10. Select **Add an output** once more, choose **Text**, and enter
    +++Message+++ as the name with +++Request submitted to Student
    Services+++ as the value.  
    ![](./media/image12.png)

11. Select the flow name at the top left and rename it +++Certificate
    Request Notification+++  
    ![](./media/image9.png)

12. Select **Save draft**, and then select **Publish**.

> ***Note:** In this lab, the flow generates a reference number and
> records the request in its run history. In production, you would add a
> step that emails or saves the request for Student Services.  *
> ![](./media/image19.png)

### Task 2: Connect the Flow to the Agent

1.  Return to the **Campus Services Agent** and select **Tools**, then
    **Add tool**.  
    ![](./media/image16.png)

2.  Select the **Flow** filter and choose **Certificate Request
    Notification**.  
    ![](./media/image47.png)

3.  Under **Instructions**, add the following to the end of the
    **Responsibilities** section:

\- Certificate requests: collect the Student ID and the reason for the
request. Verify the Student ID exists in Student_Records.csv and
retrieve the student's email. Show the student a summary (Student ID,
request type, reason) and ask them to confirm with Yes or No before
continuing.  
- If the student confirms, call the Certificate Request Notification
tool, passing StudentID, StudentEmail and RequestPurpose. When the tool
returns Status = Sent, tell the student their request has been submitted
to Student Services, and give them the ReferenceID. Do not claim it has
been read or acted on.  
- If the student declines, do not call the tool. Tell the student the
request was not submitted and ask what they would like to change.

![](./media/image17.png)

5.  Select **Save**, then **Publish**.  
    ![](./media/image14.png)

## Exercise 5: Publish and Test End to End (9 min)

### Task 1: Test the Student Experience

1.  On the Preview tab, enter:

+++I need a bonafide certificate for my visa application. My Student ID
is STU002.+++  
![](./media/image34.png)

2.  When Atlas asks you to confirm the details, reply +++Yes+++.  
    ![](./media/image42.png)

## Summary

In this lab, you built a complete multi-agent student support solution
for Riverbend University entirely in Copilot Studio. You built the Atlas
orchestrator grounded in university documents, and a Campus Services
Agent that answers fee, grade and exam questions from student record
files.

You connected the two agents, added an agent flow that submits bonafide
certificate requests after the student confirms, and published Atlas to
a demo website channel to validate the student experience from request
to flow run.
