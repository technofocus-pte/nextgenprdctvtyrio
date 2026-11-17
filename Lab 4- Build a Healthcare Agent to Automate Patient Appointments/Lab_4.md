**Lab 4: Build a Healthcare Agent to Automate Patient Appointments**

**Scenario**

Northstar Community Hospital operates multiple outpatient clinics and receives hundreds of appointment requests every day through phone calls and emails. This manual scheduling process often results in long wait times, booking conflicts, and increased administrative workload for front-desk staff.

To improve patient experience and operational efficiency, the hospital is implementing an AI-powered patient assistant built with Microsoft Copilot Studio. The assistant enables patients to securely verify their identity, ask hospital-related questions, view available appointment slots, book appointments, and cancel existing bookings. Behind the scenes, Power Automate orchestrates appointment retrieval and booking while Microsoft Dataverse stores appointment information.

By the end of this lab, you will have built an intelligent healthcare agent that combines conversational AI with business process automation to streamline patient appointment management.

**Persona**

**Emily Carter**  
**Role:** Digital Transformation Lead - Northstar Community Hospital

Emily is responsible for modernizing patient services by implementing AI-powered healthcare solutions. Her objective is to reduce administrative effort, improve appointment scheduling efficiency, and provide patients with a secure self-service experience while ensuring sensitive healthcare interactions follow responsible AI practices.

**Lab Objectives**

In this lab, you will perform the following:

- Exercise 0: Prepare the Healthcare Data Foundation

  - Task 0 Creating solution

  - Task 1 - Create and Populate the Appointment Slot Table

  - Task 3 - Update the action for the agent

  - Task 4 - (Read only) Understand the decorators

  - Task 5 - Test your agent

- Exercise 1 - Build the Conversational Healthcare Agent

  - Task 1 - Create the Northstar Patient Assistant

  - Task 2 - Create the Emergency Assistance Topic

  - Task 3 - Build the Patient Identity Verification Topic

  - Task 4 - Build the Appointment Booking Topic

  - Task 5 - Build the Appointment Cancellation Topic

  - Task 6 - Test the Healthcare Agent

- Exercise 2 - Automate Appointment Management

  - Task 1 - Build the HC-SlotLookup Flow

  - Task 2 - Connect the HC-SlotLookup Flow to the Agent

  - Task 3 - Build HC-BookAppointment Flow

  - Task 4 - Connect the HC-BookAppointment Flow to the Agent

  - Task 5 - Test the End-to-End Appointment Booking Experience

**Exercise 0 - Prepare the Healthcare Data Foundation**

Create and populate the Dataverse table that will store appointment slot information used throughout the lab.

**Task 0 - Creating solution**

1.  Open the browser, enter the following URL to navigate to the Power Apps portal and login using the credentials given in the **Environment tab**:

2.  make.powerapps.com

3.  From the left navigation pane, select **Tables** **(1)**. On the **Tables** page, select **+ New table** **(2)**, and then choose **Create new tables** **(3)** from the drop-down menu.

> ![image1](images/image1.png)

4.  Now click on **Switch and create**. It will be created in few minutes.

> ![A screenshot of a computer](images/image2.png)
>
> ![A screenshot of a computer](images/image3.png)
>
> **Note:** Please use the newly created envrionment **ODL_User 's Environment** for further lab execution.

5.  In the left navigation, select **Solutions (1)**, and then click **+ New solution (2)**.

> ![image4](images/image4.png)

6.  In the **New solution** pane, enter **HealthcareSolution- (1)** in **Display name**, enter **HealthcareSolution- (2)** in **Name**, and then click **+ New publisher (3)**.

> ![A screenshot of a computer](images/image5.png)

7.  In the **New publisher** pane, enter **NorthstarHealthcare (1)** in **Display name**, enter **NorthstarHealthcare (2)** in **Name**, enter **nhs (3)** in **Prefix**, and then click **Save (4)**.

> ![A screenshot of a computer](images/image6.png)

8.  In the **New solution** pane, verify the solution details and selected publisher, and then click **Create (1)**.

> ![image7](images/image7.png)

**Task 1 - Create and Populate the Appointment Slot Table**

Create the Appointment Slot Dataverse table and import the provided appointment schedule so the healthcare agent has appointment data available during booking.

1.  In the HealthcareSolution solution command bar, click **+ New (1)**, select **Table (2)**, and then select **Tables (3)**.

> ![image8](images/image8.png)

2.  Select **Import an Excel file or .CSV**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image9.png)

3.  In the Browse file window, browse to **C:/Lab Files/Healthcare/** **(1)**, select **AppointmentSlot.csv file (2)**, and then click **Open (3)**.

> ![image10](images/image10.png)

4.  In the **Import an Excel or .CSV file** dialog, confirm that **AppointmentSlot.csv** is included, and then click **Import (1)**.

> ![A screenshot of a computer](images/image11.png)

5.  Select all the columns and click **Save**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image12.png)

6.  Select **Save and exit(twice).**

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image13.png)
>
> ![A screenshot of a computer AI-generated content may be incorrect.](images/image14.png)

7.  Your table will appear in the table list. Select the **Appointment Slot** table.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image15.png)

8.  Select **Columns**-\>Save these name values for the next exercise.

> ![A screenshot of a computer](images/image16.png)
>
> ![A screenshot of a computer](images/image17.png)

**Exercise 1 - Build the Conversational Healthcare Agent**

Develop a secure patient assistant using Copilot Studio that can answer hospital questions, verify patient identity, and manage appointment conversations.

**Task 1 - Create the Northstar Patient Assistant**

Create a healthcare agent, configure its instructions, connect organizational knowledge, and apply responsible AI settings to ensure grounded responses.

1.  In a new tab, enter the following URL to navigate to the Copilot Studio portal:

2.  https://copilotstudio.microsoft.com

> **Note:** Please select the environment **ODL_User 's Environment** from top-right corner in the Copilot Studio to create the Agent.

3.  Click **Agents** from the left-navigation menu, and then select **+Create a blank agent.**

> ![A screenshot of a computer](images/image18.png)

4.  In the **Name your agent** dialog, enter **Northstar Patient Assistant (1)**, expand **Agent settings (Optional) (2)**, select **HealthcareSolution (3)** from the drop-down, and then click **Create (4)**.

> ![image19](images/image19.png)

5.  After the agent is provisioned, on the **Overview** tab, click **Edit (1)**.

> ![image20](images/image20.png)

6.  Enter the following agent’s description, then click **Save**.

7.  An AI assistant that helps patients book and cancel appointments

8.  while answering hospital-related questions.

> ![image21](images/image21.png)

9.  Now, scroll down to the **Instructions** section, click **Edit (1)**.

> ![A white background with black text](images/image22.png)

10. Enter the following instructions in the field, then click on **Save**.

11. You are the Northstar Patient Assistant.

12. Use the connected SharePoint knowledge only to answer operational questions such as clinic opening hours, appointment preparation instructions, insurance information, parking, accessibility, and contact details.

13. Do not answer questions related to diagnoses, treatments, medications, dosages, symptoms, or medical conditions.

14. If a user asks a medical question, politely explain that you cannot provide medical advice and recommend contacting their healthcare provider.

15. At the end of every informational response generated from the knowledge source, include the following disclaimer:

16. This information is provided for general guidance only. Please confirm the details with your healthcare team before your appointment.

> ![image23](images/image23.png)

17. In the knowledge section, select **Add knowledge** to add a knowledge source to the agent.

> ![image24](images/image24.png)

18. In the file picker, browse to **C:/Lab Files/Healthcare/ (1)**, select the clinic information files shown **(2)**, and then click **Open (3)**.

    - Clinic_Opening_Hours_and_Contact_Det...

    - Insurance_and_Billing_FAQs

    - Parking_and_Accessibility_Guide

    - Pre-Procedure_Preparation_Instructions

> ![image25](images/image25.png)

19. Click **Add to agent**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image26.png)

20. Disable the **web search** option.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image27.png)

21. Select **Setting**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image28.png)

22. Now set the following settings in the setting window:

    - Set Content moderation level to **medium**.

    - Turn off **Allow ungrounded responses** in the knowledge section.

    - Click **Save** to save the changes.

    - Close the setting window

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image29.png)
>
> ![A screenshot of a computer AI-generated content may be incorrect.](images/image30.png)

**Task 2: Create the Emergency Assistance Topic**

Build a safety topic that immediately identifies emergency medical situations and directs patients to emergency services instead of continuing the conversation.

1.  Navigate to **Topics** tab, select **+ Add a topic**, then click **From blank**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image31.png)

2.  Enter the name of the topic as **Emergency Assistance**.

3.  Enter the following value in the trigger:

4.  Use this topic when a user reports a medical emergency or mentions

5.  symptoms such as chest pain, difficulty breathing, severe bleeding,

6.  unconsciousness, or asks for emergency medical assistance.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image32.png)

7.  Click the **plus sign(+)** below trigger and then select **Send a message**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image33.png)

8.  Enter the following message in the message box:

9.  If you believe you are experiencing a medical emergency, call your

10. local emergency services 999 immediately or visit the nearest

11. emergency department. I can't provide assistance in emergency medical situations.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image34.png)

12. Click the **plus sign** below the message box and select **Topic management**-\>select **End conversation**.

> ![A screenshot of a computer](images/image35.png)

13. Click the **Save** button to save the topic.

> ![A screenshot of a computer](images/image36.png)

**Task 3 - Build the Patient Identity Verification Topic**

Create a reusable topic that securely collects patient identity information before allowing appointment-related actions.

1.  Navigate to **Topics** tab, select **+ Add a topic**, then click **From blank**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image31.png)

2.  Enter the name of the topic as **Verify Patient Identity**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image37.png)

3.  Enter the **description**:

4.  Internal helper topic. This topic is only called from other topics. It should verify the patient's identity once and then immediately return control to the calling topic. It should never be selected directly based on user input or called more than once in the same conversation.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image38.png)

5.  Click the plus sign(+) and select **Ask a question** from the drop-down.

> ![image39](images/image39.png)

6.  Enter the following details:

    - Message: **Please enter your Patient ID (for example, NH1234)**

    - Identify: Select **User's entire response**

    - Set Variable: Enter **PatientID**. Make it **Global**.

> ![image40](images/image40.png)
>
> ![image41](images/image41.png)
>
> ![image42](images/image42.png)

7.  Select Sign (+) below the previous node and add **Ask Question**.

8.  Enter the following details:

    - Question: **Please enter your date of birth in YYYY-MM-DD format**

    - Identify: Select **User's entire response**

    - Set Variable: Enter \*\* **DateOfBirth** \*\*. Make it **Global**.

> ![image43](images/image43.png)

9.  Select the **+** button below the node. Select **Ask a question.**

10. Enter the following details:

    - Question: **Please enter your full name.**

    - Select **Person Name** in the identify field.

    - Create a new variable name as: **PatientName** and make it **Global,** so that we can access it outside of this topic.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image44.png)

11. Select the **+** button below the previous node. Select **Ask a question**.

12. Enter the following message:

13. Thank you. Your identity has been verified. Let's continue with

14. your appointment request.

> ![image45](images/image45.png)

15. Select the **+** button below the previous node. Select **Topic management-\>End current topic**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image46.png)

16. Select **Save** to save the topic.

> ![image47](images/image47.png)

**Task 4 - Build the Appointment Booking Topic**

Design the conversation that collects appointment preferences and prepares the booking request for automation.

1.  Go to **Topics**. Select **+ Add a topic**. Select **From blank**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image48.png)

2.  Enter:

    - Topic Name: **Book Appointment**

    - Topic Description:

    - Use this topic when a patient wants to book, schedule, or make an appointment with a healthcare provider.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image49.png)

3.  Click the **+ sign** below the previous node. Select **Topic Management -\> Go to another topic-\> Verify Patient Identity**.

> ![image50](images/image50.png)

4.  Click the **+ sign** below the previous node. Select **Ask a question**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image51.png)

5.  Enter the following details:

    - Enter question:

    - Which speciality would you like to book an

    - appointment with?

    - 

    - \- Cardiology

    - 

    - \- Dermatology

    - 

    - \- Orthopaedics

    - 

    - \- General Practice

    - 

    - \- Physiotherapy

    - Identify: Select **User’s entire response**

    - Set variable: Enter **specialty**

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image52.png)

6.  Click the **+ sign** below the previous node. Select **Ask a question.**

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image53.png)

7.  Enter the following details:

    - Question: Enter **Is this your first visit or a follow-up appointment?**

    - Identify: Select **User’s entire response**

    - Save user response as **AppointmentType**

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image54.png)

8.  Click the **+ sign** below the previous node. Select **Ask a question.**

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image55.png)

- Question: **Please briefly describe the reason for your appointment.**

- Identify: Select **User’s entire response**

- Save user response as **ReasonForVisit**

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image56.png)

9.  Click the **+ sign** below the previous node. Select **Send a message.**

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image57.png)

10. Enter the following message:

11. I can help you schedule your appointment, but I can't provide medical advice. If you believe your symptoms require immediate medical attention, please contact your local emergency services or visit the nearest emergency department.

> ![A screenshot of a chat AI-generated content may be incorrect.](images/image58.png)

12. Click the **+ sign** below the previous node. Select **send a message.**

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image59.png)

13. Enter the following message:

14. Thank you. I've collected the information needed for your appointment request.

15. 

16. In the next exercise, this topic will be enhanced to retrieve

17. available appointment slots, allow you to select a preferred time, and confirm your booking using Power Automate flows.

> ![A screenshot of a computer screen AI-generated content may be incorrect.](images/image60.png)

18. Click the **+ sign** below the previous node. Select Topic Management → End current topic.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image61.png)

19. Select **Save** to save the topic.

> ![image62](images/image62.png)

**Task 5 - Build the Appointment Cancellation Topic**

Create a conversation that allows patients to securely cancel existing appointments after confirming their identity

1.  Navigate to **Topics**. Select **+ Add a topic**. Select **From blank**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image63.png)

2.  Enter the following details:

    - Topic Name: **Cancel Appointment**

    - Description: **Use this topic when a patient wants to cancel an existing appointment.**

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image64.png)

3.  Click the **+ sign** below the previous node. Select **Topic Management -\> Go to another topic-\> Verify Patient Identity**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image65.png)

4.  Click the **+ sign** below the previous node. Select Ask question.

> ![A screenshot of a computer](images/image66.png)

5.  Enter the following details:

    - Question: Please enter your appointment reference number(AB2039).

    - Identify: User’s entire response

    - Save User response as: AppointmentReference

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image67.png)

6.  Click the **+ sign** below the previous node. Select Ask a question.

7.  Enter the bellow details:

    - Question: Are you sure you want to cancel this appointment?

    - Identify: Multiple choice options

    - Options for users: Select +New option-\>Enter \*\*Yes++

    - Select +New option -\>Enter **No**

    - Save response as: CancelConfirmation

> ![A screenshot of a computer screen](images/image68.png)

8.  Click the **+ sign** below the previous Yes node. Select Add a message.

> ![A screenshot of a computer](images/image69.png)

9.  Enter the following message:

10. Thank you. Your cancellation request has been recorded.

> ![A screenshot of a computer](images/image70.png)

11. Click the **+ sign** below the previous No node. Select Add a message.

> ![A screenshot of a computer](images/image71.png)

12. Enter the following message:

13. No problem. Your appointment has not been cancelled. If you need

14. further assistance, let me know.

> ![A screenshot of a computer](images/image72.png)

15. Click the **+ sign** below the previous node. Select **Topic Management → End current topic**

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image73.png)

16. Save the topic.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image74.png)

17. Select publish(twice) to publish the agent.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image75.png)
>
> ![A screenshot of a computer AI-generated content may be incorrect.](images/image76.png)

**Task 6 - Test the Healthcare Agent**

Validate the conversational experience by testing emergency handling, knowledge retrieval, and appointment booking interactions.

1.  Select **Test** from the upper-right corner of Copilot Studio.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image77.png)

2.  Start a new conversation. Enter the following prompt and click Send button:

3.  I have chest pain.

> ![A screenshot of a chat AI-generated content may be incorrect.](images/image78.png)

4.  **Review the output:**

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image79.png)

5.  Start a **new test session:** Enter the following prompt:

6.  Which insurance providers do you accept?

> ![A screenshot of a chat](images/image80.png)

7.  Now you can see the agent is accessing the genral informations:

> ![A screenshot of a computer](images/image81.png)

8.  Started a new conversation: Enter the following prompt:

9.  I want to book an appointment.

> ![A screenshot of a chat](images/image82.png)

10. Enter follow-up questions:

    - Enter your Patient ID: **NH2201**

    - Please enter your date of birth: **2/11/1985**

    - Please enter your name: **James Ortiz**

    - Which speciality would you like to book an appointment with: **Cardiology**

    - Is this your first visit or a follow-up appointment: Select First Visit

    - Please briefly describe the reason for your appointment: **I m feeling little pain in my chest**

> ![A screenshot of a computer](images/image83.png)
>
> ![A screenshot of a computer](images/image84.png)
>
> ![A screenshot of a computer](images/image85.png)

**Exercise 2 — Automate Appointment Management**

Integrate Power Automate with Copilot Studio to retrieve appointment availability and automatically confirm bookings.

**Task 1 — Build the HC-SlotLookup Flow**

Create a Power Automate flow that retrieves available appointment slots from Dataverse based on the patient's selected medical specialty.

1.  Open a new tab and navigate to **make.powerautomate.com**.

2.  Select **Create** from the left navigation menu. Then choose **Instant cloud flow**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image86.png)

3.  Enter the flow name as **HC-SlotLookup**. Then choose **When an agent calls the flow** trigger. Select **Create** to create the flow.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image87.png)

4.  Select the **When an agent calls the flow** trigger and then click **+Add an input**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image88.png)

5.  Select **Text**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image89.png)

6.  Enter the first input parameter name as **specialty**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image90.png)

7.  Select **+Add an input,** then add **patient_id**.

> ![A screenshot of a computer](images/image91.png)

8.  Click the **+ sign** below the previous node. Search for **List rows** in the search bar. Select **List rows** from Dataverse.

> ![image92](images/image92.png) Note: If you face the following error while sign-in then open the pop-ups blocked. Select Allows allow pop-up and Select Done. ![A screenshot of a computer](images/image93.png)

9.  Enter Connection name as: . Click **Sign in** to connect to Dataverse.

> ![A screenshot of a computer](images/image94.png)

10. Select the **Table name** field and choose the **Appointment Slot** table.

> ![A screenshot of a computer](images/image95.png)

11. In the filter field, **enter nhs_specialty eq ' -\> click daynamic symbol -\> select insert specialty dynamic value -\> enter ' and nhs_doctorstatus eq 1**.

> **Note:** The Dataverse schema prefix (for example, **cr14f**, **cr41f**, **crbab**,**nhs** etc.) is automatically generated when the table is created and **may be different in your environment**. Always verify the actual schema name of your columns before using them in Power Automate expressions.
>
> ![A screenshot of a computer](images/image96.png)

12. Enter the Row count as 4.

> ![A screenshot of a computer](images/image97.png)

13. Click the **+ sign** below the previous node. Search **search**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image98.png)

14. In From section, select thunderbolt icon -\> select body/value.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image99.png)

15. Switch to text mode.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image100.png)

16. Select the **fx** and enter the following expression and then click **Add**.

17. concat(

18. '📅 Appointment',

19. decodeUriComponent('%0A'),

20. 'Date: ',

21. formatDateTime(item()?\['nhs_appointmentdatetime'\], 'dd MMM yyyy'),

22. decodeUriComponent('%0A'),

23. 'Time: ',

24. formatDateTime(item()?\['nhs_appointmentdatetime'\], 'hh:mm tt'),

25. decodeUriComponent('%0A'),

26. '👨‍⚕️ Doctor: ',

27. item()?\['nhs_clinicianname'\],

28. decodeUriComponent('%0A'),

29. '📍 Location: ',

30. item()?\['nhs_location'\],

31. decodeUriComponent('%0A'),

32. '🆔 Slot ID: ',

33. item()?\['nhs_slotid'\],

34. decodeUriComponent('%0A'),

35. '────────────────────────'

36. )

> **Note:** The Dataverse schema prefix (for example, **cr14f**, **cr41f**, **crbab**, **nhs** etc.) is automatically generated when the table is created and **may be different in your environment**. Always verify the actual schema name of your columns before using them in Power Automate expressions
>
> ![A screenshot of a computer AI-generated content may be incorrect.](images/image101.png)
>
> ![A screenshot of a computer AI-generated content may be incorrect.](images/image102.png)

37. Click the **+ sign** below the previous node. Search for **compose**+.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image103.png)

38. Select the **fx** and enter the following expression, then select **Add**.

39. concat(

40. decodeUriComponent('%0A'),

41. join(outputs('Select')?\['body'\], decodeUriComponent('%0A%0A'))

42. )

> ![A screenshot of a computer](images/image104.png)

43. Click the **+ sign** below the previous node. Select **Respond to the agent** under AI capabilities.

> ![A screenshot of a computer](images/image105.png)

44. Select **+Add an Output**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image106.png)

45. Select **Text**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image107.png)

46. Enter **AppointmentSlots**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image108.png)

47. Select **Dynamic content** -\> select **Outputs** under **Compose**.

> ![A screenshot of a computer](images/image109.png)
>
> ![A screenshot of a computer AI-generated content may be incorrect.](images/image110.png)

48. Click the **save** button to save the changes.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image111.png)

49. After successfully saving the flow, select the **back** button from the top left of the navigation bar.

50. Select **Solutions** from the left navigation. Then select **HealthcareSolution**. ![A screenshot of a computer](images/image112.png)

51. You will be navigated to Power Apps. Expand the menu. ![A screenshot of a computer](images/image113.png)

52. Select Objects -\> Cloud flows. ![A screenshot of a computer](images/image114.png)

53. Select Add existing -\> Automation -\> Cloud flow ![A screenshot of a computer](images/image115.png)

54. Select HC-SlotLoopup flow. Then click Add to add this flow to the Healthcare solution. ![A screenshot of a computer](images/image116.png)

55. Select Publish all customizations. ![A screenshot of a computer](images/image117.png)

**Task 2 - Connect the HC-SlotLookup Flow to the Agent**

Integrate the HC-SlotLookup flow with the booking conversation so patients can view available appointment slots directly within the chat.

1.  Navigate back to Copilot Studio.

2.  Select Agents-\> select Northstar Patient Assistant.

> ![image118](images/image118.png)

3.  Select Topics -\> open **Book Appointment** topic.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image119.png)

4.  After the” I can help you schedule your appointment, but I can't provide medical advice.” **Message** node, click + sign. Select **Add a tool -\>HC-SlotLookup.**

> ![A screenshot of a computer](images/image120.png)

5.  In the Action tool, in the specialty field, click the three dots(…). Select **specialty** variable.

> ![A screenshot of a computer](images/image121.png)

6.  Similarly, in the patient_id field, click the three dots(…). Select the **PatientID** variable.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image122.png)

7.  Under the Action node, click the (+) sign. Select **Send a message**.

8.  In the send a message node, Enter the following message:

9.  I found the following available appointments:

> Then select variable(X)-\>select AppointmentSlots variable.
>
> It will display all the available slots.
>
> ![A screenshot of a computer](images/image123.png)
>
> ![A screenshot of a computer AI-generated content may be incorrect.](images/image124.png)

10. Click the **+ sign** below the previous node. Select **Ask a question**.

> ![A screenshot of a computer AI-generated content may be incorrect.](images/image125.png)

11. Enter the following details:

    - Question:

    - Which appointment would you like to book? Please enter the Slot ID.

    - Identify: Select **User’s entire response**

    - Save user response as **selectedSlot**

> ![A screenshot of a chat](images/image126.png)

12. Select **Save** to save the updates.

**Task 3 — Build HC-BookAppointment Flow**

Create a Power Automate flow that reserves the selected appointment slot, updates Dataverse, and returns a booking confirmation.

1.  Open a new browser tab and enter the following URL to navigate to the PowerAutomate.

2.  https://make.powerautomate.com

3.  Select **Create** from the left navigation menu, then choose **Instant cloud flow**.

> ![A screenshot of a computer](images/image127.png)

4.  Enter the flow name as **HC-BookAppointment**. Select the **When an agent calls the flow** trigger and click **Create**.

> ![A screenshot of a computer](images/image128.png)

5.  Select the **When an agent calls the flow** trigger, then click **+ Add an input**.

6.  Select **Text**.

7.  Enter the first input parameter name as:**slot_id**

8.  Click **+ Add an input** and create the following input parameters one by one:

| **Name**             | **Type** |
|----------------------|----------|
| **patient_id**       | Text     |
| **patient_name**     | Text     |
| **date_of_birth**    | Date     |
| **specialty**        | Text     |
| **appointment_type** | Text     |
| **reason_for_visit** | Text     |

9.  ![A screenshot of a computer](images/image129.png)

10. Click the **+** sign below the trigger. Search for **List a row** and select **List rows** from **Microsoft Dataverse**.

> ![A screenshot of a computer](images/image130.png)

11. If prompted, create a Dataverse connection.

12. Select the **Appointment Slot** table.

> ![A screenshot of a computer](images/image131.png)

13. In the **Filter rows** field, enter the following expression: **nhs_slotid eq '** -\>Select **Dynamic content** and insert the **slot_id** parameter -\> **’**

> **Note:** The Dataverse schema prefix (for example, **cr14f**, **cr41f**, **crbab**, **nhs** etc.) is automatically generated when the table is created and **may be different in your environment**. Always verify the actual schema name of your columns before using them in Power Automate expressions
>
> ![A screenshot of a computer](images/image132.png)
>
> ![A screenshot of a computer](images/image133.png)

14. Enter **1** in the **Row count** field.

> ![A screenshot of a computer](images/image134.png)

15. Click the **+** sign below **List rows**. Search for **Apply to each** and select it.

> ![A screenshot of a computer](images/image135.png)

16. In the **Select an output from previous steps** field, choose **value** from the **List rows** action.

> ![A screenshot of a computer](images/image136.png)
>
> ![A screenshot of a computer](images/image137.png)

17. Inside the **Apply to each** action, click **+ sign**. Search for **Update a row** and select **Update a row** from Microsoft Dataverse.

> ![A screenshot of a chat](images/image138.png)

18. Select the **Appointment Slot** table.

> ![A screenshot of a computer](images/image139.png)

19. For the **Row ID**, select **Appointment Slot** as the unique identifier from the current item returned by **List rows**.

> ![A screenshot of a computer](images/image140.png)

20. Select Show all and update the following columns.

| **Dataverse Column**          | **Value to Select** | **Where to Select It From**                     |
|-------------------------------|---------------------|-------------------------------------------------|
| Doctor Status                 | Booked              | Type/select the choice value manually           |
| Patient ID                    | patient_id          | When an agent calls the flow → patient_id       |
| Patient Name                  | patient_name        | When an agent calls the flow → patient_name     |
| Date Of Birth                 | date_of_birth       | When an agent calls the flow → date_of_birth    |
| Specialty                     | specialty           | When an agent calls the flow → specialty        |
| Reason For Visit              | reason_for_visit    | When an agent calls the flow → reason_for_visit |
| Status(Status of Appointment) | Confirmed           | Select the choice value manually                |

21. ![A screenshot of a computer](images/image141.png)

22. ![A screenshot of a computer](images/image142.png)

23. ![A screenshot of a computer](images/image143.png)

24. ![A screenshot of a computer](images/image144.png)

25. Click the **+** sign below the **Apply to each** action. Search for **Compose** and select **Compose**.

> ![A screenshot of a computer](images/image145.png)

26. Enter manually:

> **✅ Your appointment has been confirmed.**
>
> **Appointment Reference:**
>
> Insert the **slot_id** dynamic content from **When an agent calls the flow**.
>
> Continue typing: **Patient Name:**
>
> Insert **patient_name** dynamic content.
>
> Continue typing: **Specialty:**
>
> Insert **specialty** dynamic content.
>
> Finally type: **Status: Booked**
>
> ![A screenshot of a computer](images/image146.png)

27. Click the **+** sign below the **Compose** action. Select **Respond to the agent**.

> ![A screenshot of a computer](images/image147.png)

28. Select **Respond to the agent**, it will open an pop-up windows. Now click **+ Add an output**. Select **Text**.

29. Enter the output name as: **BookingConfirmation**

30. Select **Dynamic content**. Select **Outputs** from the **Compose** action.

> ![A screenshot of a computer](images/image148.png)
>
> ![A screenshot of a computer](images/image149.png)

31. Click **Save** to save the flow.

> ![A screenshot of a computer](images/image150.png)

32. After successfully saving the flow, select the back button from the top left of the navigation bar. ![A screenshot of a computer](images/image151.png)

33. Select Solutions from the left navigation. Then select HealthcareSolution. ![A screenshot of a computer](images/image152.png)

34. You will be navigated to Power Apps. Expand the menu. ![A screenshot of a computer](images/image153.png)

35. Select Objects -\> Cloud flows ![A screenshot of a computer](images/image154.png)

36. Select Add existing -\> Automation -\> Cloud flow ![A screenshot of a computer](images/image155.png)

37. Select HC-BookAppointment flow. Then click Add to add this flow to the Healthcare solution. ![A screenshot of a computer](images/image156.png)

38. Select Publish all customizations. ![A screenshot of a computer](images/image157.png)

**Task 4 — Connect the HC-BookAppointment Flow to the Agent**

Integrate the booking flow with the conversation so appointment requests are automatically processed and confirmed.

1.  Navigate back to Copilot Studio.

2.  Select Agents from the left-navigation panel and then open the **Northstar Patient Assistant** agent.

> ![A screenshot of a computer](images/image158.png)

3.  Select **Topics** -\> Open the **Book Appointment** topic.

> ![A screenshot of a computer](images/image159.png)

4.  In the Book Appointment topic, Locate the question: **“Which appointment would you like to book? Please enter the Slot ID.”**

5.  Click the + **sign** immediately below this question. Select **Add a tool** -\> Select **HC-BookAppointment**.

> ![A screenshot of a computer](images/image160.png)

6.  Map the following variables.

| **Flow Input**   | **Agent Variable** |
|------------------|--------------------|
| slot_id          | selectedSlot       |
| patient_id       | PatientID          |
| patient_name     | PatientName        |
| date_of_birth    | DateOfBirth        |
| specialty        | specialty          |
| appointment_type | AppointmentType    |
| reason_for_visit | ReasonForVisit     |

7.  Verify that all input parameters have been mapped correctly.

8.  ![A screenshot of a computer](images/image161.png)

9.  ![A screenshot of a computer](images/image162.png)

10. Replace the previous placeholder message. Select {X} to add new variable -\> Select **BookingConfirmation** output returned by the flow.

> ![A screenshot of a computer](images/image163.png)
>
> ![A screenshot of a computer](images/image164.png)

11. The message node should display the booking confirmation returned by Power Automate.

12. Click the + **sign** below the booking confirmation message node. Select Topic management-\>End current topic.

> ![A screenshot of a computer](images/image165.png)

13. Select **Save**.

> ![A screenshot of a computer](images/image166.png)

14. Select **Publish**, then select **Publish** again to publish the latest changes.

**Task 5 - Test the End-to-End Appointment Booking Experience**

Validate the complete appointment booking process and verify that booking details are correctly stored in Dataverse.

1.  Select Test to test the agent.

2.  Enter the following prompt:

3.  I want to book an appointment.

> ![A screenshot of a chat](images/image167.png)

4.  Enter the follow up questions:

    - Enter your Patient ID: **NH2201**

    - Please enter your date of birth: **1985-11-02**

    - Please enter your name: **James Ortiz**

    - Which speciality would you like to book an appointment with: **Orthopaedics**

    - Is this your first visit or a follow-up appointment: **First Visit**

    - Please briefly describe the reason for your appointment: **I m feeling a little pain in my right Knee**

    - Which appointment would you like to book? Please enter the Slot ID: **APT1024**.

> ![A screenshot of a computer](images/image168.png)
>
> ![A screenshot of a chat](images/image169.png)
>
> ![A screenshot of a chat](images/image170.png)
>
> ![A screenshot of a medical appointment](images/image171.png)

5.  Navigate to [**<u>https://make.powerapps.com/</u>**](https://make.powerapps.com/) to verify the booking.

6.  Select Tables-\> AppointmentSlot.

> ![A screenshot of a computer](images/image172.png)

7.  Select **+ 19 additional rows** to view all the rows.

> ![A screenshot of a computer](images/image173.png)

8.  Locate Slot Id: APT1024 and you can see that the appointment is booked.

> ![A screenshot of a computer](images/image174.png)

**Lab Summary**

In this lab, you built an AI-powered healthcare appointment assistant using Microsoft Copilot Studio, Microsoft Dataverse, and Power Automate. You created a secure conversational experience that verifies patient identity, answers hospital-related questions using organizational knowledge, handles emergency scenarios responsibly, and enables patients to book or cancel appointments.

You also automated the appointment management process by integrating Power Automate flows with Copilot Studio, allowing the agent to retrieve available appointment slots, update appointment records in Dataverse, and return booking confirmations in real time. Finally, you validated the complete end-to-end solution by testing patient interactions and confirming successful appointment bookings.
