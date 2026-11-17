Lab 13 - Build a Healthcare Agent to Automate Patient Appointments
Scenario
Northstar Community Hospital operates multiple outpatient clinics and
receives hundreds of appointment requests every day through phone calls
and emails. This manual scheduling process often results in long wait
times, booking conflicts, and increased administrative workload for
front-desk staff.
To improve patient experience and operational efficiency, the hospital
is implementing an AI-powered patient assistant built with Microsoft
Copilot Studio. The assistant enables patients to securely verify their
identity, ask hospital-related questions, view available appointment
slots, book appointments, and cancel existing bookings. Behind the
scenes, Power Automate orchestrates appointment retrieval and booking
while Microsoft Dataverse stores appointment information.
By the end of this lab, you will have built an intelligent healthcare
agent that combines conversational AI with business process automation
to streamline patient appointment management.
Lab Objectives
After completing this lab, you will be able to:
Create and populate Microsoft Dataverse tables for healthcare
appointment management.
Build a healthcare conversational agent using Microsoft Copilot
Studio.
Configure knowledge sources and implement responsible AI guardrails.
Create reusable conversational topics for identity verification,
appointment booking, cancellation, and emergency assistance.
Build Power Automate agent flows that retrieve available appointment
slots and confirm bookings.
Connect Copilot Studio topics with Power Automate flows.
Test an end-to-end AI-powered appointment booking experience.
Persona
Emily Carter  
Role: Digital Transformation Lead – Northstar Community Hospital
Emily is responsible for modernizing patient services by implementing
AI-powered healthcare solutions. Her objective is to reduce
administrative effort, improve appointment scheduling efficiency, and
provide patients with a secure self-service experience while ensuring
sensitive healthcare interactions follow responsible AI practices.
Exercise 0: Prepare the Healthcare Data Foundation
Create and populate the Dataverse table that will store appointment slot
information used throughout the lab.
Task 1: Create and Populate the Appointment Slot Table
Create the Appointment Slot Dataverse table and import the provided
appointment schedule so the healthcare agent has appointment data
available during booking.
Open a web browser and navigate to +++make.powerapps.com+++.
Select Tables from the left navigation menu. Then select +New
table.
![](./media/image1.png)
Select +Create new tables.
![A screenshot of a computer AI-generated content may be](./media/image2.png)
Select Create.
![A screenshot of a computer AI-generated content may be](./media/image3.png)
Select Import an Excel file or .CSV.
![A screenshot of a computer AI-generated content may be](./media/image4.png)
Select Browse, navigate to
C:/Labfiles/Healthcare/AppointmentSlot.csv file. Select
Import.
![A screenshot of a computer AI-generated content may be](./media/image5.png)
Select all the columns and click Save.
![A screenshot of a computer AI-generated content may be](./media/image6.png)
Select Save and exit(twice).
![A screenshot of a computer AI-generated content may be](./media/image7.png)
![A screenshot of a computer AI-generated content may be](./media/image8.png)
Your table will appear in the table list. Select the Appointment
Slot table.
![A screenshot of a computer AI-generated content may be](./media/image9.png)
Select Columns->Save these name values for the next exercise.
![](./media/image10.png)
![](./media/image11.png)
Exercise 1: Build the Conversational Healthcare Agent
Develop a secure patient assistant using Copilot Studio that can answer
hospital questions, verify patient identity, and manage appointment
conversations.
Task 1: Create the Northstar Patient Assistant
Create a healthcare agent, configure its instructions, connect
organizational knowledge, and apply responsible AI settings to ensure
grounded responses.
Open a web browser and navigate to
+++https://copilotstudio.microsoft.com+++.
Click Agents from the left-navigation menu, and then select
+Create a blank agent.
![](./media/image12.png)
Enter agent name as: +++Northstar Patient Assistant+++. Click
Create.
![](./media/image13.png)
Click Edit to enter the following agent’s description:
+++An AI assistant that helps patients book and cancel appointments
while answering hospital-related questions.+++
Click Save.
![](./media/image14.png)
Move to the Instruction section and click Edit. Enter the following
instructions in the field:
    ```
You are the Northstar Patient Assistant.
Use the connected SharePoint knowledge only to answer operational questions such as clinic opening hours, appointment preparation instructions, insurance information, parking, accessibility, and contact details.
Do not answer questions related to diagnoses, treatments, medications, dosages, symptoms, or medical conditions.
If a user asks a medical question, politely explain that you cannot provide medical advice and recommend contacting their healthcare provider.
At the end of every informational response generated from the knowledge source, include the following disclaimer:
This information is provided for general guidance only. Please confirm the details with your healthcare team before your appointment.
    ```

Click Save.
![](./media/image15.png)
In the knowledge section, select Add knowledge to add a
knowledge source to the agent.
![](./media/image16.png)
Click Select to browse option. Select files from
C:/Labfiles/Healthcare/.
![](./media/image17.png)
Click Add to agent.
![A screenshot of a computer AI-generated content may be](./media/image18.png)
Disable the web search option.
![A screenshot of a computer AI-generated content may be](./media/image19.png)
Select Setting.
![A screenshot of a computer AI-generated content may be](./media/image20.png)
Now set the following settings in the setting window:
Set Content moderation level to medium.
Turn off Allow ungrounded responses in the knowledge section.
Click Save to save the changes.
Close the setting window
![A screenshot of a computer AI-generated content may be](./media/image21.png)
![A screenshot of a computer AI-generated content may be](./media/image22.png)
Task 2: Create the Emergency Assistance Topic
Build a safety topic that immediately identifies emergency medical
situations and directs patients to emergency services instead of
continuing the conversation.
Select Topics. Select +Add a topic. Select +From blank.
![A screenshot of a computer AI-generated content may be](./media/image23.png)
Enter the name of the topic as +++Emergency Assistance+++.
Enter the following value in the trigger:
    `Use this topic when a user reports a medical emergency or mentions symptoms such as chest pain, difficulty breathing, severe bleeding, unconsciousness, or asks for emergency medical assistance.`
![A screenshot of a computer AI-generated content may be](./media/image24.png)
Click the plus sign(+) below trigger and then select Send a
message.
![A screenshot of a computer AI-generated content may be](./media/image25.png)
Enter the following message in the message box:
    `If you believe you are experiencing a medical emergency, call your local emergency services 999 immediately or visit the nearest emergency department. I can't provide assistance in emergency medical situations.`
![A screenshot of a computer AI-generated content may be](./media/image26.png)
Click the plus sign below the message box and select Topic
management->select End conversation.
![](./media/image27.png)
Click the Save button to save the topic.
![](./media/image28.png)
Task 3 –Build the Patient Identity Verification Topic
Create a reusable topic that securely collects patient identity
information before allowing appointment-related actions.
Select Topics. Select +Add a topic. Select +From blank.
![A screenshot of a computer AI-generated content may be](./media/image23.png)
Enter the name of the topic as +++Verify Patient Identity+++.
![A screenshot of a computer AI-generated content may be](./media/image29.png)
Enter the description:
    `Internal helper topic. This topic is only called from other topics. It should verify the patient's identity once and then immediately return control to the calling topic. It should never be selected directly based on user input or called more than once in the same conversation.`
![A screenshot of a computer AI-generated content may be](./media/image30.png)
Click the plus sign(+) and select Ask a question from the
drop-down.
![](./media/image31.png)
Enter the following details:
Message: +++Please enter your Patient ID (for example, NH1234)+++
Identify: Select User's entire response
Set Variable: Enter +++PatientID+++. Make it Global.
![](./media/image32.png)
![](./media/image33.png)
![](./media/image34.png)
Select Sign(+) below the previous node and add Ask Question.
Enter the following details:
Question: +++Please enter your date of birth in YYYY-MM-DD formate.+++
Identify: Select User's entire response
Set Variable: Enter +++ DateOfBirth +++. Make it Global.
![](./media/image35.png)
Select the + button below the node. Select Ask a question.
Enter the following details:
Question: +++Please enter your full name.+++
Select Person Name in the identify field.
Create a new variable name as: +++PatientName+++ and make it
Global, so that we can access it outside of this topic.
![A screenshot of a computer AI-generated content may be](./media/image36.png)
Select the + button below the previous node. Select Ask a
question.
Enter the following message:
+++Thank you. Your identity has been verified. Let's continue with
your appointment request.+++
![](./media/image37.png)
Select the + button below the previous node. Select Topic
management->End current topic.
![A screenshot of a computer AI-generated content may be](./media/image38.png)
Select Save to save the topic.
![](./media/image39.png)
Task 4 – Build the Appointment Booking Topic
Design the conversation that collects appointment preferences and
prepares the booking request for automation.
Go to Topics. Select + Add a topic. Select From blank.
![A screenshot of a computer AI-generated content may be](./media/image40.png)
Enter:
Topic Name: +++Book Appointment+++
Topic Description: +++Use this topic when a patient wants to book,
schedule, or make an appointment with a healthcare provider.+++
![A screenshot of a computer AI-generated content may be](./media/image41.png)
Click the + sign below the previous node. Select Topic
Management -> Go to another topic-> Verify Patient Identity.
![](./media/image42.png)
Click the + sign below the previous node. Select Ask a
question.
![A screenshot of a computer AI-generated content may be](./media/image43.png)
Enter the following details:
Enter question:
    ```
Which speciality would you like to book an
appointment with?
      - Cardiology
      - Dermatology

      - Orthopaedics

      - General Practice

      - Physiotherapy
    ```



Identify: Select User’s entire response
Set variable: Enter +++specialty+++
![A screenshot of a computer AI-generated content may be](./media/image44.png)
Click the + sign below the previous node. Select Ask a
question.
![A screenshot of a computer AI-generated content may be](./media/image45.png)
Enter the following details:
Question: Enter +++Is this your first visit or a follow-up
appointment?+++
Identify: Select Multiple Choice options
Options for user: Select +New option -> Enter +++First Visit+++
Again select +New option -> Enter +++Follow-up+++
Save user response as +++AppointmentType+++
![A screenshot of a computer AI-generated content may be](./media/image46.png)
![A screenshot of a computer screen](./media/image47.png)
Click the + sign below the previous node. Select Ask a
question.
![A screenshot of a computer AI-generated content may be](./media/image48.png)
Question: +++Please briefly describe the reason for your
appointment.+++
Identify: Select User’s entire response
Save user response as +++ReasonForVisit+++
![A screenshot of a computer AI-generated content may be](./media/image49.png)
Click the + sign below the previous node. Select **Send a
message. **
![A screenshot of a computer AI-generated content may be](./media/image50.png)
Enter the following message:
    `I can help you schedule your appointment, but I can't provide medical advice. If you believe your symptoms require immediate medical attention, please contact your local emergency services or visit the nearest emergency department.`
    !\[A screenshot of a chat AI-generated content may be](./media/image51.png)

Click the + sign below the previous node. Select send a
message.
![A screenshot of a computer AI-generated content may be](./media/image52.png)
Enter the following message:
    ```
Thank you. I've collected the information needed for your appointment
request.
    In the next exercise, this topic will be enhanced to retrieve
available appointment slots, allow you to select a preferred time, and
confirm your booking using Power Automate flows.
```
    !\\\[A screenshot of a computer screen AI-generated content may be](./media/image53.png)



Click the + sign below the previous node. Select Topic Management →
End current topic.
![A screenshot of a computer AI-generated content may be](./media/image54.png)
Select Save to save the topic.
![](./media/image55.png)
Task 5 – Build the Appointment Cancellation Topic
Create a conversation that allows patients to securely cancel existing
appointments after confirming their identity
Navigate to Topics. Select + Add a topic. Select From
blank.
![A screenshot of a computer AI-generated content may be](./media/image56.png)
Enter the following details:
Topic Name: +++Cancel Appointment+++
Description: +++Use this topic when a patient wants to cancel an
existing appointment.+++
![A screenshot of a computer AI-generated content may be](./media/image57.png)
Click the + sign below the previous node. Select Topic
Management -> Go to another topic-> Verify Patient Identity.
![A screenshot of a computer AI-generated content may be](./media/image58.png)
Click the + sign below the previous node. Select Ask question.
![](./media/image59.png)
Enter the following details:
Question: Please enter your appointment reference number(AB2039).
Identify: User’s entire response
Save User response as: AppointmentReference
![A screenshot of a computer AI-generated content may be](./media/image60.png)
Click the + sign below the previous node. Select Ask a question.
Enter the bellow details:
Question: Are you sure you want to cancel this appointment?
Identify: Multiple choice options
Options for users: Select +New option->Enter +++Yes++
Select +New option ->Enter +++No+++
Save response as: CancelConfirmation
![](./media/image61.png)
Click the + sign below the previous Yes node. Select Add a
message.
![](./media/image62.png)
Enter the following message:
+++Thank you. Your cancellation request has been recorded.+++
![](./media/image63.png)
Click the + sign below the previous No node. Select Add a
message.
![](./media/image64.png)
Enter the following message:
    `No problem. Your appointment has not been cancelled. If you need further assistance, let me know.`
    !\[](./media/image65.png)

Click the + sign below the previous node. Select Topic
Management → End current topic
![A screenshot of a computer AI-generated content may be](./media/image66.png)
Save the topic.
![A screenshot of a computer AI-generated content may be](./media/image67.png)
Select publish(twice) to publish the agent.
![A screenshot of a computer AI-generated content may be](./media/image68.png)
![A screenshot of a computer](./media/image69.png)
Task 6 – Test the Healthcare Agent
Validate the conversational experience by testing emergency handling,
knowledge retrieval, and appointment booking interactions.
Select Test from the upper-right corner of Copilot Studio.
![A screenshot of a computer AI-generated content may be](./media/image70.png)
Start a new conversation. Enter the following prompt and click Send
button:
+++I have chest pain.+++
![A screenshot of a chat AI-generated content may be](./media/image71.png)
Review the output:
![A screenshot of a computer AI-generated content may be](./media/image72.png)
Start a new test session: Enter the following prompt:
+++Which insurance providers do you accept?+++
![](./media/image73.png)
Now you can see the agent is accessing the genral informations:
![](./media/image74.png)
Started a new conversation: Enter the following prompt:
+++I want to book an appointment.+++
![](./media/image75.png)
Enter follow-up questions:
Enter your Patient ID: +++NH2201+++
Please enter your date of birth: +++2/11/1985+++
Please enter your name: +++James Ortiz+++
Which speciality would you like to book an appointment with:
+++Cardiology+++
Is this your first visit or a follow-up appointment: Select First
Visit
Please briefly describe the reason for your appointment: +++I m
feeling little pain in my chest+++
![](./media/image76.png)
![](./media/image77.png)
![](./media/image78.png)
Exercise 2 — Automate Appointment Management
Integrate Power Automate with Copilot Studio to retrieve appointment
availability and automatically confirm bookings.
Task 1 — Build the HC-SlotLookup Flow
Create a Power Automate flow that retrieves available appointment slots
from Dataverse based on the patient's selected medical specialty.
Open a new tab and navigate to +++make.powerautomate.com+++.
Select Create from the left navigation menu. Then choose
Instant cloud flow.
![A screenshot of a computer AI-generated content may be](./media/image79.png)
Enter the flow name as +++HC-SlotLookup+++. Then choose When an
agent calls the flow trigger. Select Create to create the
flow.
![A screenshot of a computer AI-generated content may be](./media/image80.png)
Select the When an agent calls the flow trigger and then click
+Add an input.
![A screenshot of a computer AI-generated content may be](./media/image81.png)
Select Text.
![A screenshot of a computer AI-generated content may be](./media/image82.png)
Enter the first input parameter name as +++specialty+++.
![A screenshot of a computer AI-generated content may be](./media/image83.png)
Select +Add an input, then add +++patient_id+++.
![](./media/image84.png)
Click the + sign below the previous node. Search for +++List
rows+++ in the search bar. Select List rows from Dataverse.
![](./media/image85.png)
Enter Connection name as: +++
@lab.CloudPortalCredential(User1).Username+++. Click Sign in to
connect to Dataverse.
![](./media/image86.png)
Select the Table name field and choose the Appointment Slot
table.
![](./media/image87.png)
In the filter field, enter +++cr41f_medicalspecialty eq '+++ ->
click daynamic symbol -> select insert specialty dynamic value ->
enter +++ ' and cr41f_doctorbookingstatus eq 1+++.
Note: The Dataverse schema prefix (for example, cr14f,
cr41f, crbab, etc.) is automatically generated when the table is
created and may be different in your environment. Always verify the
actual schema name of your columns before using them in Power Automate
expressions
![](./media/image88.png)
Enter the Row count as 4.
![](./media/image89.png)
Click the + sign below the previous node. Search +++search+++.
![A screenshot of a computer AI-generated content may be](./media/image90.png)
In From section, select thunderbolt icon -> select body/value.
![A screenshot of a computer AI-generated content may be](./media/image91.png)
Switch to text mode.
![A screenshot of a computer AI-generated content may be](./media/image92.png)
Select the fx and enter the following expression:
    ```
concat(
'📅 Appointment',
decodeUriComponent('%0A'),
'Date: ',
formatDateTime(item()?['cr41f_appointmentdateandtime'], 'dd MMM yyyy'),
decodeUriComponent('%0A'),
'Time: ',
formatDateTime(item()?['cr41f_appointmentdateandtime'], 'hh:mm tt'),
decodeUriComponent('%0A'),
'👨‍⚕️ Doctor: ',
item()?['cr41f_clinicianname'],
decodeUriComponent('%0A'),
'📍 Location: ',
item()?['cr41f_cliniclocation'],
decodeUriComponent('%0A'),
'🆔 Slot ID: ',
item()?['cr41f_slotidentifier'],
decodeUriComponent('%0A'),
'────────────────────────'
)
    ```
    Click \*\*Add\*\*.

    \*\*Note:\*\* The Dataverse schema prefix (for example, \*\*cr14f\*\*,

cr41f, crbab, etc.) is automatically generated when the table
is created and may be different in your environment. Always verify
the actual schema name of your columns before using them in Power
Automate expressions
    !\[A screenshot of a computer AI-generated content may be](./media/image93.png)
    !\\\[A screenshot of a computer AI-generated content may be](./media/image94.png)



Click the + sign below the previous node. Search for
+++compose++++.
![A screenshot of a computer AI-generated content may be](./media/image95.png)
Select the fx and enter the following expression:
    `concat( decodeUriComponent('%0A'), join(outputs('Select')?\\\['body'], decodeUriComponent('%0A%0A')) )`
    Select **Add**.
    !\\\[](./media/image96.png)



Click the + sign below the previous node. Select Respond to
the agent under AI capabilities.
![](./media/image97.png)
Select +Add an Output.
![A screenshot of a computer AI-generated content may be](./media/image98.png)
Select Text.
![A screenshot of a computer AI-generated content may be](./media/image99.png)
Enter +++ AppointmentSlots+++.
![A screenshot of a computer AI-generated content may be](./media/image100.png)
Select Dynamic content -> select Outputs under Compose.
![](./media/image101.png)
![A screenshot of a computer AI-generated content may be](./media/image102.png)
Click the save button to save the changes.
![A screenshot of a computer AI-generated content may be](./media/image103.png)
Task 2: Connect the HC-SlotLookup Flow to the Agent
Integrate the HC-SlotLookup flow with the booking conversation so
patients can view available appointment slots directly within the chat.
Navigate back to Copilot Studio.
Select Agents-> select Northstar Patient Assistant.
![](./media/image104.png)
Select Topics -> open Book Appointment topic.
![A screenshot of a computer AI-generated content may be](./media/image105.png)
After the” I can help you schedule your appointment, but I can't
provide medical advice.” Message node, click + sign. Select
Add a tool ->HC-SlotLookup.
![](./media/image106.png)
In the Action tool, in the specialty field, click the three dots(…).
Select specialty variable.
![](./media/image107.png)
Similarly, in the patient_id field, click the three dots(…). Select
the PatientID variable.
![A screenshot of a computer AI-generated content may be](./media/image108.png)
Under the Action node, click the (+) sign. Select Send a
message.
In the send a message node, Enter the following message:
+++I found the following available appointments:+++
Then select variable(X)->select AppointmentSlots variable.
It will display all the available slots.
![](./media/image109.png)
![A screenshot of a computer AI-generated](./media/image110.png)
Click the + sign below the previous node. Select Ask a
question.
![A screenshot of a computer AI-generated content may be](./media/image111.png)
Enter the following details:
Question: +++Which appointment would you like to book? Please enter
the Slot ID.+++
Identify: Select User’s entire response
Save user response as +++selectedSlot+++
![](./media/image112.png)
Select Save to save the updates.
Task 3 — Build HC-BookAppointment Flow
Create a Power Automate flow that reserves the selected appointment
slot, updates Dataverse, and returns a booking confirmation.
Open a new browser tab and navigate to
+++https://make.powerautomate.com+++.
Select Create from the left navigation menu, then choose
Instant cloud flow.
![](./media/image113.png)
Enter the flow name as +++HC-BookAppointment+++. Select the
When an agent calls the flow trigger and click Create.
![](./media/image114.png)
Select the When an agent calls the flow trigger, then click +
Add an input.
Select Text.
Enter the first input parameter name as:+++slot_id+++
Click + Add an input and create the following input parameters
one by one:
Name	Type
+++patient_id+++	Text
+++patient_name+++	Text
+++date_of_birth+++	Date
+++specialty+++	Text
+++appointment_type+++	Text
+++reason_for_visit+++	Text
![](./media/image115.png)
Click the + sign below the trigger. Search for +++List a
row+++ and select List rows from Microsoft Dataverse.
![](./media/image116.png)
If prompted, create a Dataverse connection.
Select the Appointment Slot table.
![](./media/image117.png)
In the Filter rows field, enter the following expression:
+++ppa_slotidentifier eq '+++ ->Select Dynamic content and
insert the slot_id parameter -> +++’+++
Note: The Dataverse schema prefix (for example, cr14f,
cr41f, crbab, etc.) is automatically generated when the table
is created and may be different in your environment. Always verify
the actual schema name of your columns before using them in Power
Automate expressions
![](./media/image118.png)
![](./media/image119.png)
Enter 1 in the Row count field.
![](./media/image120.png)
Click the + sign below List rows. Search for Apply to
each and select it.
![](./media/image121.png)
In the Select an output from previous steps field, choose
value from the List rows action.
![](./media/image122.png)
![](./media/image123.png)
Inside the Apply to each action, click + sign. Search for
Update a row and select Update a row from Microsoft
Dataverse.
![](./media/image124.png)
Select the Appointment Slot table.
![](./media/image125.png)
For the Row ID, select Appointment Slot as the unique
identifier from the current item returned by List rows.
![](./media/image126.png)
Select Show all and update the following columns.
Dataverse Column	Value to Select	Where to Select It From
Doctor Status	`Booked`	Type/select the choice value manually
Patient ID	`patient\\\_id`	When an agent calls the flow → `patient\\\_id`
Patient Name	`patient\\\_name`	When an agent calls the flow → `patient\\\_name`
Date Of Birth	`date\\\_of\\\_birth`	When an agent calls the flow → `date\\\_of\\\_birth`
Medical Specialty	`specialty`	When an agent calls the flow → `specialty`
Reason For Visit	`reason\\\_for\\\_visit`	When an agent calls the flow → `reason\\\_for\\\_visit`
Status	`Confirmed`	Select the choice value manually
    !\[](./media/image127.png)
    !\\\[](./media/image128.png)

    !\\\[](./media/image129.png)

    !\\\[](./media/image130.png)



Click the + sign below the Apply to each action. Search for
+++Compose+++ and select Compose.
![](./media/image131.png)
Enter manually:
+++✅ Your appointment has been confirmed.
Appointment Reference:+++
Insert the slot_id dynamic content from When an agent calls the
flow.
Continue typing: +++Patient Name:+++
Insert patient_name dynamic content.
Continue typing: +++Specialty:+++
Insert specialty dynamic content.
Finally type: +++Status: Booked+++
![](./media/image132.png)
Click the + sign below the Compose action. Select Respond
to the agent.
![](./media/image133.png)
Click + Add an output. Select Text.
Enter the output name as: +++BookingConfirmation+++
Select Dynamic content. Select Outputs from the Compose
action.
![](./media/image134.png)
![](./media/image135.png)
Click Save to save the flow.
![](./media/image136.png)
Task 4 — Connect the HC-BookAppointment Flow to the Agent
Integrate the booking flow with the conversation so appointment requests
are automatically processed and confirmed.
Navigate back to Copilot Studio.
Select Agents from the left-navigation panel and then open the
Northstar Patient Assistant agent.
![](./media/image137.png)
Select Topics -> Open the Book Appointment topic.
![](./media/image138.png)
In the Book Appointment topic, Locate the question: “Which
appointment would you like to book? Please enter the Slot ID.”
Click the + sign immediately below this question. Select Add a
tool ->Select HC-BookAppointment.
![](./media/image139.png)
Map the following variables.
Flow Input	Agent Variable
`slot\\\_id`	`selectedSlot`
`patient\\\_id`	`PatientID`
`patient\\\_name`	`PatientName`
`date\\\_of\\\_birth`	`DateOfBirth`
`specialty`	`specialty`
`appointment\\\_type`	`AppointmentType`
`reason\\\_for\\\_visit`	`ReasonForVisit`
Verify that all input parameters have been mapped correctly.
![](./media/image140.png)
![](./media/image141.png)
Replace the previous placeholder message. Select {X} to add new
variable -> Select BookingConfirmation output returned by the
flow.
![](./media/image142.png)
![](./media/image143.png)
The message node should display the booking confirmation returned by
Power Automate.
Click the + sign below the booking confirmation message node.
Select Topic management->End current topic.
![](./media/image144.png)
Select Save.
![](./media/image145.png)
Select Publish, then select Publish again to publish the
latest changes.
Task 5 —Test the End-to-End Appointment Booking Experience
Validate the complete appointment booking process and verify that
booking details are correctly stored in Dataverse.
Select Test to test the agent.
Enter the following prompt:
+++I want to book an appointment.+++
![](./media/image146.png)
Enter the follow up questions:
Enter your Patient ID: +++NH2201+++
Please enter your date of birth: +++1985-11-02+++
Please enter your name: +++James Ortiz+++
Which speciality would you like to book an appointment with:
+++Orthopaedics +++
Is this your first visit or a follow-up appointment: Select First
Visit
Please briefly describe the reason for your appointment: +++I m
feeling a little pain in my right Knee+++
Which appointment would you like to book? Please enter the Slot ID:
+++APT1024+++.
![](./media/image147.png)
![](./media/image148.png)
![](./media/image149.png)
![](./media/image150.png)
Navigate to +++ https://make.powerapps.com/+++ to verify the
booking.
Select Tables->Appointment slot.
![](./media/image151.png)
Select +19 additional rows to view all the rows.
![](./media/image152.png)
Locate Slot Id: APT1024 and you can see that the appointment is
booked.
![](./media/image153.png)
Lab Summary
In this lab, you built an AI-powered healthcare appointment assistant
using Microsoft Copilot Studio, Microsoft Dataverse, and Power Automate.
You created a secure conversational experience that verifies patient
identity, answers hospital-related questions using organizational
knowledge, handles emergency scenarios responsibly, and enables patients
to book or cancel appointments.
You also automated the appointment management process by integrating
Power Automate flows with Copilot Studio, allowing the agent to retrieve
available appointment slots, update appointment records in Dataverse,
and return booking confirmations in real time. Finally, you validated
the complete end-to-end solution by testing patient interactions and
confirming successful appointment bookings.
