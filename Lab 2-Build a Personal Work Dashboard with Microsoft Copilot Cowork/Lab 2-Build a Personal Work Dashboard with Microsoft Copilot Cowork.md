**Build a Personal Work Dashboard with Microsoft Copilot Cowork**

**Estimated duration: 40 minutes**

# **Overview**

Modern workdays suffer from app-switching overload. You start in
Outlook, jump to Teams, check your calendar, hop into OneDrive — and
before long, an hour has passed without meaningful work.

In this lab you will use Microsoft Copilot Cowork to build a single HTML
page that answers one question every morning: ***"What deserves my
attention right now?"***

# **What the Dashboard includes:**

- Header — today's date, last-refresh timestamp, and a hint that
  everything is clickable

- KPI Strip — six at-a-glance tiles: overdue actions, unread emails,
  meetings tomorrow, Teams unread, active projects, and out-of-office
  teammates

- Urgent Banner — red-bordered block surfacing items needing attention
  today

- Tomorrow's Schedule — every event with time, response status, and
  conflict markers

- Prep Notes — short crib sheets for meetings that need preparation

- Top Projects — your 5–8 active projects with an inferred 'Next' action
  each

- Week Calendar Load — a pure CSS bar chart showing meeting density per
  day

- Time Allocation — a CSS doughnut chart breaking the week by category

- Emails Needing a Reply — filtered to only messages that need a
  response

- OOF Radar — teammates out of office this week and next

- Unread Teams Chats — top chats with one-line previews

- Recent Files in Flight — most recently modified OneDrive folders

# **Prerequisites**

Before starting the lab, confirm each item below. If any item is
missing, contact your Microsoft 365 administrator.

| Requirement | How to Verify |
|---|---|
| **Microsoft 365 Account** | You can sign in at microsoft365.com with your work or school account |
| **Copilot Cowork Access** | You see a 'Cowork' option or tab when you open Microsoft Copilot |
| **Outlook Enabled** | You can open Outlook and see your inbox |
| **Calendar Enabled** | You can open the M365 Calendar and see your meetings |
| **Teams Enabled** | You can open Microsoft Teams and see your chats |
| **OneDrive Enabled** | You can access OneDrive and see recent files |
| **At Least 5 Upcoming Events** | You have meetings on your calendar so the dashboard has real data to show |

# **Exercise 1: Open Copilot Cowork**

1.  Open your browser and navigate to <https://microsoft365.com> and
    Click Sign In.

2.  Enter your Username and password and complete any multi-factor
    authentication (MFA) prompt.  
    ![](./media/image1.png)

> ![](./media/image2.png)

3.  Confirm you land on the Microsoft 365 home page.  
    ![](./media/image3.png)

4.  Inside Copilot, look for tabs or sections near the top of the panel
    — you should see options such as 'Chat' and 'Cowork' (or 'Tasks').

![](./media/image4.png)

5.  You should see a 'New Task' button and possibly a list of any
    previous tasks.  
    ![](./media/image5.png)

**Note:** If your Copilot interface only shows a chat box and no Cowork
tab, your tenant may not yet have Cowork enabled. Check with your
administrator.

# **Exercise 2: Build the Dashboard**

1.  In the Cowork tab, click New Task (or the + button).  
    ![](./media/image5.png)

2.  A text input area will appear for you to describe the task.  
    ![](./media/image6.png)

Below is the complete Prompt 1. You will copy everything between the
dashed lines and paste it into the Cowork task input.

[TABLE]

![](./media/image7.png)

After submitting, Cowork will begin working. You will see it:

- Fan out parallel queries to your calendar, inbox, Teams, and OneDrive

- Infer your active projects from recurring meeting and email patterns

- Generate the HTML file and save it to output/dashboard.html

**Note:** The first run typically takes 5-10 minutes.

![](./media/image8.png)

3.  When the task finishes, Cowork will display a completion message.  
    ![](./media/image9.png)

4.  If a preview link or download button appears, click it to open the
    dashboard.

![](./media/image10.png)

# **Exercise 3: Schedule the Hourly Refresh**

Use Prompt 2 to create a scheduled task that regenerates the dashboard
every hour on weekdays and emails it to your inbox at 9 AM. With the
dashboard built, you now want it to stay fresh automatically — without
you having to re-run anything manually. Prompt 2 sets up a recurring
scheduled task inside Cowork.

1.  In the Cowork tab, click **New Task** again.  
    ![](./media/image11.png)

2.  A fresh input area will appear. Copy and Paste Prompt 2.

[TABLE]

![](./media/image12.png)

3.  Once you have pasted the prompt. Click Submit to confirm the
    scheduled task.

4.  Wait for Cowork to confirm the task was created. You should see a
    task appear in the Cowork task list named: 'Refresh work dashboard
    (hourly at :55, email at 6:55 AM)'.

![](./media/image13.png)

5.  Click **Next.**

![](./media/image14.png)

6.  Click **Schedule**.

![](./media/image15.png)

7.  Review the output:

![](./media/image16.png)

8.  Click on the task name in the Cowork task list to open its details
    and verify the scheduled task.  
    ![](./media/image17.png)

9.  Confirm the schedule shows weekdays, :55 past the hour, 6:55 AM–5:55
    PM Pacific.  
    ![](./media/image18.png)

10. Confirm the task status shows Active or Running (not Paused).  
    ![](./media/image19.png)

**Warning:** Editing a scheduled task automatically pauses it. If you
ever modify the task, remember to resume it from the Cowork task list
afterward.

# **Exploring the Dashboard**

Now that the dashboard is built and scheduled, take a few minutes to
explore each section. Use the guide below to understand what you are
looking at.

#################### Header & KPI Strip

- The header shows your name, today's date, and the last-refreshed
  timestamp (with a pulsing dot). Click any item in any section — they
  all open the original source.

- The KPI strip has six tiles. Red tiles indicate urgency, amber
  indicates a warning, green means healthy.

![](./media/image20.png)

#################### Tomorrow's Schedule & Prep Notes

- Each meeting row has a color-coded badge: green = Accepted, amber =
  Tentative, red = No Response or Needs Action.

- If Cowork detects that a meeting needs preparation (customer demo,
  manager 1:1), a Prep Notes card appears with a short crib sheet.

- Click any meeting to open it directly in Outlook Calendar.

![](./media/image21.png)

![](./media/image22.png)

![](./media/image23.png)

#################### Week Calendar Load & Time Allocation Charts

- The bar chart shows how many meetings fall on each day of the upcoming
  week. Heavy days (7+ meetings) appear in red.

- The doughnut chart splits your week by category: customer-facing,
  training, internal syncs, focus time, and admin.

- Both charts are built from pure CSS — they work even in email viewers
  and locked-down browsers.

![](./media/image24.png)

![](./media/image25.png)

![](./media/image26.png)

#################### Dark Mode Toggle

- Look for the sun/moon pill button in the top-right corner of the
  dashboard header.

- Click it to switch between light and dark modes. Your preference is
  saved in the browser.

![](./media/image27.png)

![](./media/image28.png)

########## Troubleshooting Common Issues

[TABLE]

########## Customization Tips

Once you are comfortable with the base dashboard, try these
customizations:

#################### Task 1: Lock the Layout

1.  After the dashboard looks exactly how you want it, tell Cowork:

> ***"Lock this dashboard format in for all future ones."***

This updates the scheduled task so every hourly refresh preserves the
approved layout, CSS, and premium visual touches.

![](./media/image29.png)

![](./media/image30.png)

![](./media/image31.png)

## **Task 2: Check Schedules** 

1.  Navigate to Automations tab. Here you can view the Scheduled
    automations.

![](./media/image32.png)

#################### Change the Refresh Frequency

1.  Open the scheduled task in Cowork.  
    ![](./media/image32.png)

2.  Edit the schedule to your preferred interval (e.g., every 30
    minutes, or only once at 7 AM).  
    ![](./media/image33.png)

3.  Remember to Resume the task after editing.  
    ![](./media/image34.png)

[TABLE]

########## Summary & Next Steps

#################### What You Accomplished

- Navigated to Copilot Cowork and created a new task

- Used Prompt 1 to generate a fully functional personal work dashboard
  from live Microsoft 365 data

- Used Prompt 2 to schedule the dashboard to refresh every hour on
  weekdays and email it to your inbox each morning

- Explored all sections of the dashboard and understood what each tile
  and chart represents

- Learned how to troubleshoot common issues and customize the dashboard

#################### Next Steps

- Run the dashboard for a full week and note which sections you use most

- Lock the layout once you are happy with the design

- Share the recipe with a colleague and have them build their own

- Explore other Copilot Cowork use cases — the same pattern works for
  project status reports, client briefings, and team digests
