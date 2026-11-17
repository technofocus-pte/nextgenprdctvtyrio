# Govern and Monitor the Zava Retail Agent Ecosystem with Agent 365 

Lab Duration: 45 minutes

## **Scenario**

Zava Retail's frontline and project teams are already using two live
agents: the Holiday helper agent, which supports store staff with
schedules, SOPs, and daily operations, and the Project Knowledge
Assistant, which helps employees find project documents and summaries.
With the holiday season approaching, Jordan Blake, VP of Store
Operations, has asked IT to stand up a third agent — a Holiday Returns
Helper — that gives frontline employees short, mobile-friendly answers
about the holiday return window, exchange policy, and refund methods.
Priya Nair, the Store Operations Manager, has written the return-policy
content the agent will rely on and is expected to be named its business
owner once it goes live.

You are Maya Chen, the AI Administrator for Zava Retail. You are
responsible for more than just building this new agent. You need to make
sure it — and every other agent already running in the tenant — is
visible in a single inventory, routed through proper approval before it
goes live, installed where frontline staff will actually use it
(Microsoft Teams), and covered by the same governance controls
(ownership, blocking, risk review, and exportable reporting) that Zava
Retail already applies to its other agents. Partway through your review,
Riley Osei from Compliance & Risk flags a concern about Sam Torres's
Holiday helper agent and asks you to pause it while the wording of one
of its SOP responses is reviewed. In this lab, you will build the
Holiday Returns Helper in Copilot Studio, publish and install it, then
use the Agent 365 Overview and Registry in the Microsoft admin center to
inspect, approve, block/unblock, export, and audit ownership across Zava
Retail's full agent ecosystem.

## **Personas:**

- Maya Chen(AI Administrator, Zava Retail IT)-owns the Agent 365
  Registry and is responsible for approving, publishing, blocking, and
  auditing every agent in the tenant.

- Jordan Blake(VP, Store Operations)- Sponsored the Holiday Returns
  Helper project and requested it be available to all store staff ahead
  of the holiday season.

- Priya Nair(Store Operations Manager)- Day-to-day process owner for
  returns and exchanges. Priya wrote the return-policy content used as
  the agent's knowledge source and is the intended business owner for
  Holiday Returns Helper.

- Riley Osei(Compliance & Risk Analyst)- Submitted the request to
  temporarily block Holiday helper agent pending a policy-language
  review, and will confirm when it's safe to unblock.

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

## **Exercise 1: Create a New Agent — Holiday Returns Helper**

Build the Holiday Returns Helper agent from scratch in Copilot Studio,
give it clear instructions and a knowledge source, and publish it so it
is ready for governance review. You are building this on behalf of
Jordan Blake's request, using the return-policy document supplied by
Priya Nair as the knowledge source.

1.  Open web browser and navigate to
    +++<https://copilotstudio.preview.microsoft.com/+++>

2.  Sign in with the lab credentials.  
    ![](./media/image1.png)

3.  Enter your password.  
    ![](./media/image2.png)

4.  Select **Agents** from the left navigation bar. Then select **New
    agent.**  
    ![](./media/image3.png)

5.  Enter the **Agent** **Name +++**Holiday Returns Helper+++.

6.  Paste the **Instructions** and Click Save.

+++You are Holiday Returns Helper for Zava Retail.  
Your role is to assist store associates with questions about holiday
returns, exchanges, and refunds.  
Always answer using information from the uploaded Holiday Return Policy
document.  
Keep responses concise, professional, and suitable for frontline
employees using a mobile device.  
If the information is not available in the knowledge source, state that
you couldn't find the answer rather than making assumptions.  
Do not answer unrelated questions.+++  
![](./media/image4.png)

7.  Select **knowledge** from the right navigation menu to add a
    knowledge source. Select **Upload File.**  
    ![](./media/image5.png)![](./media/image6.png)

8.  Upload **Holiday Return Policy.docx.** Select **Add to agent** to
    upload the document.

![](./media/image7.png)

9.  Preview the uploaded file.  
    ![](./media/image8.png)

10. Ensure that **Web Search** option is disabled.  
    ![](./media/image9.png)

11. Click **Publish** to publish the agent.  
    ![](./media/image10.png)

12. Navigate to the Channels section. Select **M365 and Microsoft
    Teams**.  
    ![](./media/image11.png)

13. Select Availability Options.  
    ![](./media/image12.png)

14. Select the **Test** tab to test the agent.

15. Paste the following prompt in the prompt field. Select the **Send**
    button.

+++What is the holiday return window?+++  
![](./media/image13.png)

16. The agent should explain the return window using the uploaded
    policy.  
    ![](./media/image14.png)

17. Enter the following prompt and select the **Send** button.

+++Can a customer exchange an item instead of requesting a refund?+++  
![](./media/image15.png)

18. The exchange policy should match the knowledge document.  
    ![](./media/image16.png)

## **Exercise 2: Explore the Agent Registry and Monitor Agent Activity**

Get a tenant-wide snapshot of Zava Retail's agent ecosystem — total
agents, active usage, open requests, and ownership gaps — before
drilling into individual agents

1.  Open a browser and navigate to
    +++<https://admin.cloud.microsoft/+++>

2.  In the left navigation pane, expand **Agents**, and then select
    **Overview**.  
    ![](./media/image17.png)

3.  On the **Agent Overview** page, locate the following metrics and
    note their current values:

    1.  **Agent Registry** — total count of agents in the tenant.

    2.  **Active users** — unique users who interacted with an agent in
        the last 30 days.

    3.  **Pending requests for agents** — open requests to add specific
        agents.

    4.  **Agents without owners** — agents whose owner has left the
        company.

    5.  **Agent analytics** — agents by creators, top platforms used to
        build agents, and active users in Copilot over time.  
        ![](./media/image18.png)

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
    agents**. Then select the **Requests** tab.  
    ![](./media/image19.png)

2.  In the agent list, locate **Holiday Returns Helper** agent and
    select the vertical **...** next to the name.  
    ![](./media/image20.png)

3.  From the two options, you can either **Reject submission** or
    **Publish to store**. For now, select **Publish to store**.  
    ![](./media/image21.png)

4.  On the **Publish new agent** flow, under **Select users or groups
    who can install the agent**, select **All users**. Under **Select
    users or groups who will have the agent pre-installed (optional)**,
    select All Users. Select Next.  
    ![](./media/image22.png)

5.  On **Apply template**, select **Next**.  
    ![](./media/image23.png)

6.  On **Review permissions**, select **Next**.  
    ![](./media/image24.png)

7.  On **Review and finish**, select **Publish**.  
    ![](./media/image25.png)

8.  The agent is now published and available in the Registry.  
    ![](./media/image26.png)

### **Task 2: Install the Agent in Microsoft Teams**

Install the published Holiday Returns Helper agent in Microsoft Teams so
it is available to frontline employees during customer interactions.

1.  Open **Microsoft Teams**. Navigate to
    +++<https://teams.cloud.microsoft/+++>

2.  In the left navigation pane, select **Apps**. And locate **Holiday
    Returns Helper**.  
    ![](./media/image27.png)

3.  Select **Add** to install the agent.  
    ![](./media/image28.png)

### **Task 3: Verify the Agent's Responses**

Test the Holiday Returns Helper agent by asking common customer service
questions and confirm that it provides accurate and relevant responses.

1.  Open the **Holiday Returns Helper** agent in Microsoft Teams.  
    ![](./media/image29.png)

2.  Paste the following prompt:

+++Can a customer exchange an item instead of requesting a refund?+++  
![](./media/image30.png)

3.  Review the response and verify that the exchange policy is explained
    correctly.  
    ![](./media/image31.png)

4.  Paste the following prompt:

+++What refund methods are supported?+++  
![](./media/image32.png)

5.  Review the response and verify that the supported refund methods are
    accurately described.  
    ![](./media/image33.png)

## **Exercise 4: Block and Unblock the Holiday helper agent**

Practice the emergency control every AI admin needs: immediately
stopping an agent tenant-wide, and safely restoring it once a concern
has been resolved. Riley Osei from Compliance & Risk has asked you to
pause Sam Torres's Holiday helper agent while a policy-wording issue is
reviewed.

### **Task 1: Block an Agent**

Use the Registry to halt the Holiday helper agent for all users and
record why it was blocked, per Riley Osei's request.

1.  On the **All agents** page, select the **Registry** tab, then search
    for and select Holiday helper agent in the agent list.  
    ![](./media/image34.png)

2.  On the details panel, select **Block**.  
    ![](./media/image35.png)

3.  On the **Block agent** pane, review the message confirming that
    blocking will prevent all users in the organisation from accessing
    the agent. Check the box next to **Block agent**. Also select the
    reason for block: Not approved for use. Select **Save**.  
    ![](./media/image36.png)

4.  Confirm that agent now displays a **Blocked** status.  
    ![](./media/image37.png)

### **Task 2: Unblock an Agent**

Restore the Agent to Active status once Riley Osei confirms the
policy-wording review is complete and the block is no longer needed.

1.  Select the block agent.

2.  On the **Unblock agent** pane, select the **Unblock agent**
    checkbox.  
    ![](./media/image38.png)

3.  Select the unblock agent checkbox. Select **Save**. Close the
    details panel.  
    ![](./media/image39.png)

4.  In the agent list, confirm that Agent now displays an **Active**
    status.  
    ![](./media/image40.png),∫µ˜v,u

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
