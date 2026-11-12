# Lab 7: **Build, Publish, and Share a Zava Retail App in Copilot Studio (Preview)**

Hands-on lab \| Zava Retail scenario \| 40 minutes

# **Lab overview**

Zava Retail store teams track urgent stock requests in scattered emails and spreadsheets. In this lab you act as a business maker and use the new **app creation experience** in Microsoft Copilot Studio to turn a plain-language description into a working app. You refine it through conversation, test it, publish it and share it with a colleague.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>Preview feature</strong></p>
<p>Apps in Copilot Studio are a preview feature. Preview features are not meant for production use, can have restricted functionality, and are rolling out gradually, so the <strong>App (Preview)</strong> tile might not be visible in every environment yet. Screen labels might differ slightly from this guide. Use the intent of each step if a label has changed.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## **Objectives**

- Confirm the prerequisites for app creation and explain how identity and governance apply.

- Describe an app in natural language and review the proposed approach and first draft.

- Navigate the authoring surface, including the **Data** and **Connections** views and the read-only code view.

- Refine the app through conversation, test it, then publish and share it.

## **Prerequisites**

| **Requirement**          | **Details**                                                                                                |
|--------------------------|------------------------------------------------------------------------------------------------------------|
| Copilot Studio access    | A work or school account with access to Microsoft Copilot Studio.                                          |
| New experience           | The **New experience** toggle is turned on, on the Copilot Studio **Home** page.                           |
| App tile                 | The **App (Preview)** tile appears. App creation is on by default, but your administrator can turn it off. |
| Billing                  | Building, previewing and testing apps can consume Copilot Credits under usage-based billing.               |
| Second person (optional) | A colleague or test account in your tenant to share the app with in Exercise 4.                            |

## **Lab timing**

| **Exercise**                                                      | **Time**       |
|-------------------------------------------------------------------|----------------|
| Exercise 1: Verify access and understand the governance model     | 5 minutes      |
| Exercise 2: Create the app from a description                     | 12 minutes     |
| Exercise 3: Refine the app and explore data, connections and code | 10 minutes     |
| Exercise 4: Test, publish and share the app                       | 13 minutes     |
| **Total**                                                         | **40 minutes** |

# **Exercise 1: Verify access and understand the governance model**

**Estimated time:** 5 minutes

## **Task 1: Confirm app creation is available**

1.  Go to <https://copilotstudio.microsoft.com> and sign in with your work or school account.

2.  On the **Home** page, make sure the **New experience** toggle is turned on.  
    ![](images/r_image27.png)

3.  Confirm that the **App (Preview)** tile is visible.

![](images/r_image28.png)

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>If the tile is missing</strong></p>
<p>Microsoft is rolling out apps gradually, and your administrator can turn off app creation. Ask your administrator to check, or follow along with a facilitator demonstration.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## **Task 2: Review the governance model**

Read the points below. You will test the last two in Exercise 4.

- **Environment:** Copilot Studio routes you to your personal environment automatically. You do not choose or manage an environment.

- **Hosting:** published apps use Microsoft-hosted infrastructure and approved application dependencies.

- **Identity:** when an app connects to organizational data, it uses the signed-in user's identity.

- **Sharing:** publishing or sharing an app does not give users permission to data they could not otherwise access.

# **Exercise 2: Create the app from a description**

**Estimated time:** 12 minutes

App creation begins as a conversation. Copilot Studio might ask clarifying questions and propose an approach before it generates an interactive preview.

## **Task 1: Start the app conversation**

1.  On the Copilot Studio **Home** page, select the **App (Preview)** tile.

2.  In the conversation area, paste the following prompt and send it.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>Prompt</strong></p>
<p>Build an app for Zava Retail store teams to track urgent stock requests.</p>
<p>Users: store managers and floor staff.</p>
<p>Each request has: Request ID, Store, Product name, Category, Quantity needed, Priority (Low, Medium, High), Status (New, In progress, Fulfilled), Requested by, and Requested date.</p>
<p>Screens: a dashboard showing open requests by priority, a list of requests with filters for Store, Category and Status, and a form to submit a new request.</p>
<p>Include 15 rows of realistic sample data across 3 stores.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![](images/r_image29.png)

## **Task 2: Create a SharePoint site with prompts**

1.  If asked the clarifying prompts, select “**Yes, save to SharePoint** to save the app data in SharePoint.![](images/r_image2a.png)

2.  Select “**Create a new site”.**  
    ![](images/r_image2b.png)

3.  Select Approve to approve the SharePoint site.  
    ![](images/r_image2c.png)

4.  **Approve** the Create lists prompt.  
    ![](images/r_image2d.png)

5.  Approve the prompt for **Create list items.**  
    ![](images/r_image2e.png)

6.  Wait for the interactive app preview to appear.

![](images/r_image2f.png)

## **Task 3: Tour the authoring surface**

| **\#** | **Area**                         | **What you use it for**                                                                |
|--------|----------------------------------|----------------------------------------------------------------------------------------|
| 1      | Conversation area                | Answer questions, request app changes and attach files for context.                    |
| 2      | Dropdown menu                    | View the app's metadata and settings, and open the **Data** and **Connections** views. |
| 3      | Interactive preview              | Validate features, behaviour and connected data.                                       |
| 4      | Preview and code switch          | Switch between the app preview and the underlying code.                                |
| 5      | **Play**, **Share**, **Publish** | Run, share and publish the app.                                                        |

1.  Find each area on your screen, then try the dashboard, the list and the new request form in the preview. Do not submit anything yet.

# **Exercise 3: Refine the app and explore data, connections and code**

**Estimated time:** 10 minutes

Generated layouts, fields and calculations might be incomplete or incorrect. Make one change at a time and review the preview after each one.

## **Task 1: Refine the app through conversation**

1.  Send the first change request below and review the preview.

> **Prompt**
>
> Change 1: Add a "Days open" column to the request list that shows the number of days since the Requested date. Highlight High priority requests that have been open for more than 3 days.  
> ![](images/r_image30.png)
>
> ![](images/r_image31.png)

2.  Send the second change request and review the preview again.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>Prompt</strong></p>
<p>Change 2: Add summary cards at the top of the dashboard showing total open requests and High priority open requests.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![](images/r_image32.png)

![](images/r_image33.png)

## **Task 2: Explore the Data and Connections views**

1.  Select the dropdown menu next to the app name and review the metadata and settings.

2.  Open the **Data** view.  
    ![](images/r_image34.png)

3.  Note the tables or lists the app uses.  
    ![](images/r_image35.png)

4.  Open the **Connections** view.  
    ![](images/r_image36.png)

5.  Note whether any connections exist.  
    ![](images/r_image37.png)

6.  Switch to the code view and try to edit a line of code. Note what happens, then switch back to the preview.  
    ![](images/r_image38.png)

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>Key point</strong></p>
<p>The code view is <strong>read-only</strong>. To change the app, describe what you want in the conversation area. You can also use <strong>Ask for follow-up changes</strong> in the preview.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

# **Exercise 4: Test, publish and share the app**

**Estimated time:** 13 minutes

Publish only after the main scenarios work as expected. **Publishing** makes the latest version available to the people the app has been shared with. **Sharing** controls who can open and use the app, subject to your organization's policies.

## **Task 1: Test the main scenarios**

1.  Use the preview to test the scenarios.

2.  Paste the following prompt:  
      
    ***“Submit a new request with valid values.”***  
    ![](images/r_image39.png)

> Note: Approve the prompt requests.  
> 4. Review the output:  
> ![](images/r_image3a.png)

5\. Paste the following prompt:  
  
“***Filter the list by Store, then Category, then Status. “***  
![](images/r_image3b.png)  
6***.*** Review the output:  
![](images/r_image3c.png)

## **Task 2:: Publish and share**

1.  Select **Play** to run the app as an end user and submit one valid request.  
    ![](images/r_image3d.png)

2.  Approve the SharePoint request.Select **Allow.**![](images/r_image3e.png)

3.  Select **Publish** and wait for the confirmation.  
    ![](images/r_image3f.png)

4.  Select **Share** and add one colleague or test account from your tenant (for example, Marie Brown in the Zava Retail scenario). Share only with people who should be able to open and use the app.  
    ![](images/r_image40.png)

> ![](images/r_image41.png)

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>Remember</strong></p>
<p>Sharing an app might not automatically share its underlying data. If the app uses connected data such as SharePoint or Dataverse, users might need separate permission to it. The app uses each signed-in user's identity, so it never grants more access than that user already has.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

# **Summary**

You created an app from a plain-language description, refined it through conversation, inspected its data, connections and read-only code, tested it, published it and shared it.

| **Skill**         | **Key takeaway**                                                     |
|-------------------|----------------------------------------------------------------------|
| Describe          | State the purpose, users, data, fields, actions and rules clearly.   |
| Refine            | Work in small steps and review the preview each time.                |
| Test              | Run the main scenarios before publishing, using representative data. |
| Publish and share | Separate actions. Share only with the right people.                  |
| Govern            | Identity, permissions and organizational policies still apply.       |

## **Preview limitations to keep in mind**

- Generated layouts, fields, calculations or sample data might be incomplete or incorrect.

- Complex apps with many roles or integrations need more iteration. Build in smaller steps.

- Available data sources and connectors depend on your environment and organizational policies.

- Preview features and limits can change before general availability.
