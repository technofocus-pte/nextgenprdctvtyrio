# **Govern and Monitor the Zava Retail Agent Ecosystem with Agent 365**

## **Scenario**

Zava Retail\'s frontline and project teams are already using two live
agents: the Holiday helper agent, which supports store staff with
schedules, SOPs, and daily operations, and the Project Knowledge
Assistant, which helps employees find project documents and summaries.
With the holiday season approaching, Jordan Blake, VP of Store
Operations, has asked IT to stand up a third agent --- a Holiday Returns
Helper --- that gives frontline employees short, mobile-friendly answers
about the holiday return window, exchange policy, and refund methods.
Priya Nair, the Store Operations Manager, has written the return-policy
content the agent will rely on and is expected to be named its business
owner once it goes live.

You are Maya Chen, the AI Administrator for Zava Retail. You are
responsible for more than just building this new agent. You need to make
sure it --- and every other agent already running in the tenant --- is
visible in a single inventory, routed through proper approval before it
goes live, installed where frontline staff will actually use it
(Microsoft Teams), and covered by the same governance controls
(ownership, blocking, risk review, and exportable reporting) that Zava
Retail already applies to its other agents. Partway through your review,
Riley Osei from Compliance & Risk flags a concern about Sam Torres\'s
Holiday helper agent and asks you to pause it while the wording of one
of its SOP responses is reviewed. In this lab, you will build the
Holiday Returns Helper in Copilot Studio, publish and install it, then
use the Agent 365 Overview and Registry in the Microsoft 365 admin
center to inspect, approve, block/unblock, export, and audit ownership
across Zava Retail\'s full agent ecosystem.

## **Personas:**

- Maya Chen(AI Administrator, Zava Retail IT)-owns the Agent 365
  Registry and is responsible for approving, publishing, blocking, and
  auditing every agent in the tenant.

- Jordan Blake(VP, Store Operations)- Sponsored the Holiday Returns
  Helper project and requested it be available to all store staff ahead
  of the holiday season.

- Priya Nair(Store Operations Manager)- Day-to-day process owner for
  returns and exchanges. Priya wrote the return-policy content used as
  the agent\'s knowledge source and is the intended business owner for
  Holiday Returns Helper.

- Riley Osei(Compliance & Risk Analyst)- Submitted the request to
  temporarily block Holiday helper agent pending a policy-language
  review, and will confirm when it\'s safe to unblock.

## **Lab objectives**

In this lab, you will:

1.  Create and publish a new agent, Holiday Returns Helper, in Copilot
    Studio using an uploaded knowledge source.

2.  Review the Agent 365 Overview page to understand tenant-wide
    metrics: agent count, active users, pending requests, and ownerless
    agents.

3.  Inspect pending agent requests in the Registry and publish the
    Holiday Returns Helper agent to the store.

4.  Install the newly published agent in Microsoft Teams and verify it
    responds correctly to real user prompts.

5.  Block and unblock an existing agent (Holiday helper agent) and
    understand the impact of each action.

6.  Export the full agent inventory to CSV for offline reporting and
    audit purposes.

7.  Identify agents that are missing a business owner and understand how
    to close that governance gap.

## **Agents used in this lab**

## **Exercise 1: Create a New Agent --- Holiday Returns Helper**

Build the Holiday Returns Helper agent from scratch in Copilot Studio,
give it clear instructions and a knowledge source, and publish it so it
is ready for governance review. You are building this on behalf of
Jordan Blake\'s request, using the return-policy document supplied by
Priya Nair as the knowledge source.

1.  Open web browser and navigate to
    +++<https://copilotstudio.preview.microsoft.com/+++>

2.  Sign in with the lab credentials.\
    ![](media/media/image.png){width="6.25in" height="5.0in"}

3.  Enter your password.\
    ![](media/media/image2.png){width="6.25in"
    height="4.322916666666667in"}

4.  You will be redirected to Copilot Studio homepage. Select **Agents**
    from the left navigation bar.\
    ![](media/media/image3.png){width="6.25in"
    height="1.5520833333333333in"}

5.  Select **Create a blank agent.**\
    ![](media/media/image4.png){width="6.25in"
    height="2.0416666666666665in"}

6.  Enter the **Agent** **Name +++**Holiday Returns Helper+++. Select
    **Create.**\
    ![](media/media/image5.png){width="6.25in" height="2.65625in"}

7.  Paste the **Instructions** and Click Save.

+++You are Holiday Returns Helper for Zava Retail.\
Your role is to assist store associates with questions about holiday
returns, exchanges, and refunds.\
Always answer using information from the uploaded Holiday Return Policy
document.\
Keep responses concise, professional, and suitable for frontline
employees using a mobile device.\
If the information is not available in the knowledge source, state that
you couldn\'t find the answer rather than making assumptions.\
Do not answer unrelated questions.+++\
![](media/media/image6.png){width="6.5in" height="5.572916666666667in"}

8.  Select **knowledge** from the left navigation menu to add a
    knowledge source. Select **Upload File.**\
    ![](media/media/image7.png){width="6.25in" height="4.4375in"}

9.  Select **Add to agent** to upload the document.

![](media/media/image8.png){width="6.5in" height="4.53125in"}

10. Preview the uploaded file.\
    ![](media/media/image9.png){width="6.25in"
    height="5.333333333333333in"}

11. Ensure that **Web Search** option is disabled.\
    ![](media/media/imagea.png){width="6.25in" height="5.34375in"}

12. Click **Publish** to publish the agent.\
    ![](media/media/imageb.png){width="6.25in" height="3.46875in"}

13. Navigate to the Channels section. Select M365 and Microsoft Teams.\
    ![](media/media/imagec.png){width="6.25in"
    height="2.9166666666666665in"}

14. Select Availability Options.\
    ![](media/media/imaged.png){width="4.628992782152231in"
    height="4.739583333333333in"}

15. Select Show to everyone in my org.\
    ![](media/media/imagee.png){width="3.21875in"
    height="3.933299431321085in"}

16. Select Submit to org catalog.\
    ![](media/media/imagef.png){width="3.310659448818898in"
    height="3.8645833333333335in"}

17. Select the **Test** tab to test the agent.\
    ![](media/media/image10.png){width="6.25in"
    height="2.1770833333333335in"}

18. Paste the following prompt in the prompt field. Select the **Send**
    button.

+++What is the holiday return window?+++\
![](media/media/image11.png){width="4.479166666666667in" height="6.5in"}

19. The agent should explain the return window using the uploaded
    policy.\
    ![](media/media/image12.png){width="6.25in" height="5.78125in"}

20. Enter the following prompt and select the **Send** button.

+++Can a customer exchange an item instead of requesting a refund?+++\
![](media/media/image13.png){width="6.5in" height="6.072916666666667in"}

21. The exchange policy should match the knowledge document.\
    ![](media/media/image14.png){width="6.25in"
    height="5.260416666666667in"}

## **Exercise 2: Explore the Agent Registry and Monitor Agent Activity**

Get a tenant-wide snapshot of Zava Retail\'s agent ecosystem --- total
agents, active usage, open requests, and ownership gaps --- before
drilling into individual agents

1.  Open a browser and navigate to
    +++<https://admin.cloud.microsoft/+++>

2.  In the left navigation pane, expand **Agents**, and then select
    **Overview**.\
    ![](media/media/image15.png){width="6.25in"
    height="3.2604166666666665in"}

3.  On the **Agent Overview** page, locate the following metrics and
    note their current values:

    a.  **Agent Registry** --- total count of agents in the tenant.

    b.  **Active users** --- unique users who interacted with an agent
        in the last 30 days.

    c.  **Pending requests for agents** --- open requests to add
        specific agents.

    d.  **Agents without owners** --- agents whose owner has left the
        company.

    e.  **Agent analytics** --- agents by creators, top platforms used
        to build agents, and active users in Copilot over time.\
        ![](media/media/image16.png){width="5.75in"
        height="3.7708333333333335in"}

## **Exercise 3: Inspect, Publish, and Validate the Holiday Returns Helper Agent**

In this exercise, you will review the submitted **Holiday Returns
Helper** agent in the Agent Registry, approve it for organizational use,
publish it to the agent store, install it in Microsoft Teams, and verify
that it provides accurate responses for frontline retail employees.

### **Task 1: Review and Publish the Agent from the Agent Registry**

Review the submitted Holiday Returns Helper agent in the Agent Registry
and complete the approval workflow so it becomes available to users
across the organization.

1.  In the left navigation pane, select **Agents**. Select **All
    agents**. Then select the **Requests** tab.\
    ![](media/media/image17.png){width="6.25in" height="3.3125in"}

2.  In the agent list, locate **Holiday Returns Helper** agent and
    select the vertical **\...** next to the name.\
    ![](media/media/image18.png){width="6.25in" height="2.5in"}

3.  From the two options, you can either **Reject submission** or
    **Publish to store**. For now, select **Publish to store**.\
    ![](media/media/image19.png){width="6.25in"
    height="1.8854166666666667in"}

4.  On the **Publish new agent** flow, under **Select users or groups
    who can install the agent**, select **All users**. Under **Select
    users or groups who will have the agent pre-installed (optional)**,
    select All Users. Select Next.\
    ![](media/media/image1a.png){width="6.25in"
    height="4.677083333333333in"}

5.  On **Apply template**, select **Next**.\
    ![](media/media/image1b.png){width="6.25in"
    height="4.677083333333333in"}

6.  On **Review permissions**, select **Next**.\
    ![](media/media/image1c.png){width="6.25in" height="4.34375in"}

7.  On **Review and finish**, select **Publish**.\
    ![](media/media/image1d.png){width="6.25in" height="4.53125in"}

8.  The agent is now published and available in the Registry.\
    ![](media/media/image1e.png){width="6.25in"
    height="4.479166666666667in"}

### **Task 2: Install the Agent in Microsoft Teams**

Install the published Holiday Returns Helper agent in Microsoft Teams so
it is available to frontline employees during customer interactions.

1.  Open **Microsoft Teams**. Navigate to
    +++<https://teams.cloud.microsoft/+++>

2.  In the left navigation pane, select **Apps**. And locate **Holiday
    Returns Helper**.\
    ![](media/media/image1f.png){width="3.8541666666666665in"
    height="6.25in"}

3.  Select **Add** to install the agent.\
    ![](media/media/image20.png){width="6.25in" height="4.78125in"}

### **Task 3: Verify the Agent\'s Responses**

Test the Holiday Returns Helper agent by asking common customer service
questions and confirm that it provides accurate and relevant responses.

1.  Open the **Holiday Returns Helper** agent in Microsoft Teams.\
    ![](media/media/image21.png){width="6.25in"
    height="3.8645833333333335in"}

2.  Paste the following prompt:

+++Can a customer exchange an item instead of requesting a refund?+++\
![](media/media/image22.png){width="6.5in"
height="3.6145833333333335in"}

3.  Review the response and verify that the exchange policy is explained
    correctly.\
    ![](media/media/image23.png){width="6.25in"
    height="3.3541666666666665in"}

4.  Paste the following prompt:

+++What refund methods are supported?+++\
![](media/media/image24.png){width="6.5in"
height="2.6770833333333335in"}

5.  Review the response and verify that the supported refund methods are
    accurately described.\
    ![](media/media/image25.png){width="6.25in"
    height="3.4791666666666665in"}

## **Exercise 4: Block and Unblock the Holiday helper agent**

Practice the emergency control every AI admin needs: immediately
stopping an agent tenant-wide, and safely restoring it once a concern
has been resolved. Riley Osei from Compliance & Risk has asked you to
pause Sam Torres\'s Holiday helper agent while a policy-wording issue is
reviewed.

### **Task 1: Block an Agent**

Use the Registry to halt the Holiday helper agent for all users and
record why it was blocked, per Riley Osei\'s request.

1.  On the **All agents** page, select the **Registry** tab, then search
    for and select Holiday helper agent in the agent list.\
    ![](media/media/image26.png){width="6.25in"
    height="3.3229166666666665in"}

2.  On the details panel, select **Block**.\
    ![](media/media/image27.png){width="6.25in"
    height="4.104166666666667in"}

3.  On the **Block agent** pane, review the message confirming that
    blocking will prevent all users in the organisation from accessing
    the agent. Check the box next to **Block agent**. Also select the
    reason for block: Not approved for use. Select **Save**.\
    ![](media/media/image28.png){width="6.25in"
    height="5.010416666666667in"}

4.  Confirm that agent now displays a **Blocked** status.\
    ![](media/media/image29.png){width="6.25in"
    height="3.1041666666666665in"}

### **Task 2: Unblock an Agent**

Restore the Agent to Active status once Riley Osei confirms the
policy-wording review is complete and the block is no longer needed.

1.  Select the block agent.

2.  On the **Unblock agent** pane, select the **Unblock agent**
    checkbox.\
    ![](media/media/image2a.png){width="6.25in"
    height="3.4583333333333335in"}

3.  Select the unblock agent checkbox. Select **Save**. Close the
    details panel.\
    ![](media/media/image2b.png){width="6.25in" height="4.03125in"}

4.  In the agent list, confirm that Agent now displays an **Active**
    status.\
    ![](media/media/image2c.png){width="6.25in" height="2.75in"},∫µ˜v,u

## **Summary**

In this lab, you created and published a new agent in Microsoft Copilot
Studio, explored the Agent 365 Overview to monitor tenant-wide agent
activity, and used the Agent Registry to review, approve, and publish an
agent for organizational use. You also installed the agent in Microsoft
Teams, validated its responses, practiced blocking and unblocking an
agent, exported the agent inventory for reporting, and identified
potential ownership gaps. These tasks demonstrated the core capabilities
of Agent 365 for governing, monitoring, and managing AI agents across an
organization.
