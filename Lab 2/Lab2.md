**COPILOT COWORK · LAB 3**

**AI-powered calendar optimisation**

  ------------------ ----------------------------------------------------
  **Estimated time** 20 minutes

  **Apps &           Copilot Cowork, Outlook Calendar, Microsoft Teams
  services**         

  **Objective**      Detect and resolve conflicts, schedule meetings
                     intelligently, and manage an executive-style
                     calendar with protected focus time.
  ------------------ ----------------------------------------------------

**How to read this guide**

+-----------------------+-----------------------+-----------------------+
| **PROMPT**            | **FOLLOW-UP**         | **CORRECTION**        |
|                       |                       |                       |
| Type or paste into    | A prompt sent in the  | A prompt that fixes   |
| Cowork.               | same task.            | something.            |
+-----------------------+-----------------------+-----------------------+
| **NOTE**              | **TIP**               | **IMPORTANT**         |
|                       |                       |                       |
| Useful context to     | An optional shortcut  | Do this to avoid an   |
| know.                 | or extra.             | error.                |
+-----------------------+-----------------------+-----------------------+

**Lab overview**

In this lab you use Microsoft 365 Copilot Cowork, an AI-powered agentic
workspace, to take control of your calendar. Rather than manually
hunting for scheduling conflicts or remembering which meetings need
agendas, you instruct Cowork in plain language and let it work across
Outlook Calendar and Microsoft Teams.

By the end of this lab you will have:

> • Detected and resolved real calendar conflicts using an AI-generated
> resolution plan.
>
> • Scheduled a meeting that satisfies multiple constraints at once: day
> preference, buffer times, a Teams link, and a context-aware agenda
> pulled from your email history.
>
> • Tested how a well-designed agent handles an impossible request,
> refusing gracefully and offering alternatives instead of silently
> breaking rules.
>
> • Applied executive-style standing rules to an entire week and
> reviewed every proposed change before it was applied.

**Key concepts**

  -----------------------------------------------------------------------
  **Concept**          **What it means**
  -------------------- --------------------------------------------------
  Skills & Plugins     Pre-built or custom capabilities Cowork can
                       invoke. Calendar work uses the built-in Calendar
                       Management skill, which understands buffer time,
                       focus blocks, and attendee availability.

  Plan view            Before executing, Cowork shows its proposed
                       multi-step plan in the right-hand Workspace panel.
                       You can read, approve, or cancel.

  Human-in-the-loop    Cowork proposes changes and waits for approval
                       before applying them, especially for bulk calendar
                       edits.

  Scheduling skill     Queries Outlook Calendar for you and other
                       attendees, finds open slots, and generates an
                       invite including a Teams link.

  Constraint handling  When you give rules ("not Monday," "prefer
                       mornings"), Cowork applies them rigorously and
                       reports back if they cannot all be met.
  -----------------------------------------------------------------------

**Prerequisites**

> •You are signed in to Microsoft 365 with your lab account and have a
> Copilot license assigned.
>
> • You have seeded your calendar with 5--6 events across the next three
> business days, including at least one deliberate conflict (two
> meetings at the same time).
>
> •Copilot Cowork is accessible via the Microsoft 365 app launcher or
> the Cowork tab in the Copilot app.
>
> •Outlook Calendar is listed as a connected app in the Cowork
> connections panel.

+-----------------------------------------------------------------------+
| **● NOTE**                                                            |
|                                                                       |
| If you have not seeded your calendar yet, do it now. Without real     |
| data, Cowork cannot find conflicts or check availability. In Outlook  |
| Calendar, create at least two meetings that overlap, for example      |
| "Team Stand-up" and "Client Review" both at 2:00 PM tomorrow.         |
+-----------------------------------------------------------------------+

**Exercise 1: Conflict detection and resolution**

Instruct Cowork to scan your calendar, identify every conflict and
back-to-back run, and propose a specific resolution for each, including
a suggested reschedule time and a ready-to-send message.

This exercise demonstrates two capabilities:

> •**Calendar Management skill** --- Cowork reads Outlook Calendar
> across a date range, compares event times, and identifies overlaps and
> tight transitions.
>
> •**Plan-view transparency** --- the Workspace panel shows the exact
> steps Cowork intends to run before it changes anything.

**Step 1 --- Open Copilot Cowork**

> **1.**Open your browser and go to **m365.cloud.microsoft**, or click
> the Microsoft 365 app launcher (the grid icon, top-left of any M365
> app) and select Copilot.
>
> ![](media/media/image25.png "A screenshot of a computer
>
> AI-generated content may be incorrect."){width="6.5in"
> height="3.84375in"}
>
> ![](media/media/image26.png "A screenshot of a login box
>
> AI-generated content may be incorrect."){width="6.5in"
> height="4.135416666666667in"}
>
> ![](media/media/image27.png "A screenshot of a login screen
>
> AI-generated content may be incorrect."){width="6.5in"
> height="4.5625in"}

- Click Yes to stay signed in.

> ![](media/media/image28.png "A screenshot of a computer screen
>
> AI-generated content may be incorrect."){width="6.5in"
> height="5.5625in"}
>
> **2.**In the Copilot app, find the two tabs at the top of the left
> sidebar, **Chat** and **Cowork**. Click **Cowork**.

![](media/media/5fc20ff790018831d9de0e55f077f2ccfff2af32.png){width="5.604166666666667in"
height="3.7083333333333335in"}

*The Copilot app with the Cowork tab selected.*

> **3.**The Cowork home screen shows a prompt bar in the centre, a left
> sidebar of recent tasks, and a **+ New task** button at the top-left.
> This is your starting point for every exercise.

![](media/media/c4427f563de63a50767a4816b56a8f8de6a087da.png){width="5.604166666666667in"
height="2.59375in"}

*The Cowork home screen: prompt bar, recent tasks, and + New task.*

+-----------------------------------------------------------------------+
| **● NOTE**                                                            |
|                                                                       |
| Notice the Cowork tab is selected, not Chat. Cowork can take actions, |
| while Chat only answers questions.                                    |
+-----------------------------------------------------------------------+

**Step 2 --- Enter the conflict-detection prompt**

> **4.** Click inside the prompt bar.
>
> **5.**Type or paste the prompt below exactly. Replace nothing, Cowork
> uses your actual calendar dates automatically.

+-----------------------------------------------------------------------+
| **PROMPT · CONFLICT DETECTION**                                       |
+-----------------------------------------------------------------------+
| Scan my calendar for the next 5 business days. List every conflict or |
|                                                                       |
| back-to-back run of 3+ meetings. For each conflict, propose a         |
| resolution:                                                           |
|                                                                       |
| which meeting to move, the best alternative slot for all attendees,   |
| and a                                                                 |
|                                                                       |
| polite reschedule message.                                            |
+-----------------------------------------------------------------------+

> **6.**Click the blue arrow (or press **Enter**) to submit.

![](media/media/552299461af195601ebe1f6a04756f4792fbf31e.png){width="5.604166666666667in"
height="2.4791666666666665in"}

*Cowork names the task "Calendar Conflict Analysis" and begins working.*

Cowork immediately begins: it names the task in the left sidebar, and
the Workspace panel shows the Calendar Management skill loading with the
status "Preparing to work with your calendar."

**Step 3 --- Watch the plan execute**

> **7.**As Cowork runs, watch the Workspace panel on the right. It shows
> a live list of steps being completed.
>
> **8.** The step counter updates (for example **1/3**, **2/3**,
> **3/3**) as each phase finishes.
>
> **9.**The visible steps tell you exactly what Cowork is doing, this
> plan transparency is what makes it safe for calendar changes.

![](media/media/1817eb18a837f9fcaea9baa5f5a6f51f35b74de5.png){width="5.604166666666667in"
height="2.5625in"}

*The Workspace panel mid-execution, with all three steps complete.*

The plan reads: gather context (identity, timezone, preferences) → scan
the calendar for the date range → propose resolutions for conflicts and
back-to-back runs. In the main view you can see Cowork gathering your
profile, checking your timezone, and looking up manager context in
parallel.

**Step 4 --- Review the conflict report**

> **10.**When the task completes, Cowork displays a structured report in
> the main conversation area.
>
> **11.** Read it carefully. It should include a conflicts section, a
> back-to-back runs section, a Calendar Health summary, and suggested
> next actions.
>
> **12.** Look for the deliberate conflict you seeded during setup. If
> you created two overlapping meetings tomorrow, they should appear
> here.
>
> **13.** If Cowork did not find your seeded conflict, type a follow-up:

  -----------------------------------------------------------------------
  **FOLLOW-UP**

  Are any of my meetings tomorrow overlapping?
  -----------------------------------------------------------------------

![](media/media/7ef13d40185050b790602ddf6bcf83d711db6ec3.png){width="5.604166666666667in"
height="2.5729166666666665in"}

*The completed conflict-analysis report (part 1).*

![](media/media/b58add6dccb0c70fc12439554ddacf3cfcced462.png){width="5.604166666666667in"
height="2.4895833333333335in"}

*The completed conflict-analysis report (part 2).*

The report includes a Back-to-Back Runs section, a Calendar Health
summary with a meeting-load figure, and a "Would you like me to..."
section offering follow-up actions (add focus blocks, scan a longer
window, or set scheduling preferences). All 3/3 steps show green
checkmarks.

**Step 5 --- Approve a resolution**

+-----------------------------------------------------------------------+
| **● NOTE**                                                            |
|                                                                       |
| A sandbox tenant may report no conflicts. If Cowork found a conflict  |
| and proposed a resolution, read the reschedule carefully, it should   |
| include the new suggested time and a draft message to attendees.      |
+-----------------------------------------------------------------------+

> • To approve, click **Approve** (or the thumbs-up) next to the
> proposal, or type a follow-up such as:

  -----------------------------------------------------------------------
  **FOLLOW-UP**

  Go ahead and send the reschedule request for the 2 PM conflict.
  -----------------------------------------------------------------------

> • Open Outlook Calendar to verify the meeting moved to the new slot.

+-----------------------------------------------------------------------+
| **◆ TIP**                                                             |
|                                                                       |
| To draft the message instead of sending it, add "save as draft, do    |
| not send" to your follow-up instruction.                              |
+-----------------------------------------------------------------------+

**Exercise 2: Intelligent meeting scheduling**

Ask Cowork to schedule a real meeting while satisfying multiple
constraints at once, a task that would normally mean cross-checking two
calendars, composing an agenda, and setting up a Teams link. Cowork
handles all of it from one instruction. You\'ll then give it an
impossible request to see how it fails gracefully.

Capabilities used:

> • **Scheduling skill** --- queries both calendars, finds slots,
> applies your constraints, and creates the event.
>
> • **Email-context grounding** --- searches recent threads to generate
> a context-aware agenda instead of generic talking points.
>
> • **Teams link generation** --- automatically adds a Microsoft Teams
> link to the invite.
>
> • **Constraint refusal** --- when constraints cannot all be met,
> Cowork explains why and offers the closest alternatives; it never
> silently drops a rule.

**Step 1 --- Start a new task**

> **14.**Click the **+ New task** button at the top-left of the Cowork
> sidebar. This starts a fresh conversation so the previous scan
> doesn\'t interfere. You are returned to the home screen with a blank
> prompt bar.

+-----------------------------------------------------------------------+
| **▲ IMPORTANT**                                                       |
|                                                                       |
| The button is labeled **+ New task** and sits at the top-left of the  |
| sidebar. It is not green, so look for the label and position rather   |
| than a colour.                                                        |
+-----------------------------------------------------------------------+

![](media/media/226d25ac850010c8fb61de247014e6c001ffe991.png){width="5.604166666666667in"
height="3.71875in"}

*The home screen after clicking + New task, ready for a new prompt.*

**Step 2 --- Enter the meeting-scheduling prompt**

> **15.**Click inside the prompt bar and type or paste the prompt below.
> Replace \<colleague\> with the display name or email of a lab partner
> or a colleague in your tenant.

+-----------------------------------------------------------------------+
| **PROMPT · SCHEDULE A MEETING**                                       |
+-----------------------------------------------------------------------+
| Schedule a 45-minute \"Project Sync\" with \<colleague\> next week.   |
|                                                                       |
| Constraints: not Monday, not within 30 minutes of either of our       |
| existing                                                              |
|                                                                       |
| meetings, prefer mornings, and add a Teams link and a draft agenda    |
| with                                                                  |
|                                                                       |
| 3 talking points based on our recent email thread about the project.  |
+-----------------------------------------------------------------------+

> **16.**Submit with the blue send button or **Enter**.

![](media/media/f59de2f7083531ad045e0feb061350edbaedf39d.png){width="5.604166666666667in"
height="2.5833333333333335in"}

*The scheduling prompt entered, with the Exercise 1 result still visible
above.*

**Step 3 --- Watch the multi-step plan**

> **17.**As soon as you submit, the Workspace panel updates with a new
> plan. Expect steps such as: gather context, scan both calendars for
> the date range, resolve the attendee, find the best morning slot, and
> create the event with agenda and Teams link.

+-----------------------------------------------------------------------+
| **▲ IMPORTANT**                                                       |
|                                                                       |
| The scheduling plan for this task covers attendee resolution,         |
| slot-finding, and event creation only. If a step called "propose      |
| resolutions for conflicts" appears, it has carried over from Exercise |
| 1 and does not apply here.                                            |
+-----------------------------------------------------------------------+

> •This plan shows Cowork checking BOTH calendars, yours and your
> colleague\'s, before picking a slot.
>
> • The Skills & Plugins section now lists two skills: **Calendar
> Management** and **Scheduling**, confirming two skills working
> together.

![](media/media/c5a0255deefaa3fa3ffe5eaa7c28390f5e24912a.png){width="5.604166666666667in"
height="2.5729166666666665in"}

*The scheduling plan in the Workspace panel (part 1).*

![](media/media/f18ddd40fe809f6b54547133589af90580b60e89.png){width="5.604166666666667in"
height="2.6041666666666665in"}

*The scheduling plan in progress (part 2).*

![](media/media/1ae3dedf623aaad652f5f5bb55560bf3e11be023.png){width="5.604166666666667in"
height="2.6145833333333335in"}

*Both Calendar Management and Scheduling skills active (part 3).*

Steps 1--4 complete (context, calendar scan, attendee resolution), while
steps 5--6, finding the morning slot and creating the event, are still
pending. Both skills are listed, showing how Cowork composes
capabilities for one complex request.

**Step 4 --- Respond to the attendee-input prompt**

> **18.**Cowork may pause and show an Attendee dialog asking you to
> confirm your colleague\'s details. This happens when their calendar is
> not automatically accessible.
>
> •You\'ll see two options: **Enter their email in Other** (type it
> manually) or **Just block time for myself** (create a solo event).
> Choose the one that fits.
>
> •Click **Next** to continue. Cowork resumes scheduling.

![](media/media/73fb609a4828d09c0dea98f86ee77213c34f432a.png){width="5.604166666666667in"
height="2.5416666666666665in"}

*The interactive Attendee dialog ("1 of 2" unknowns to resolve).*

This is an example of Cowork asking for clarification rather than
guessing, a key behaviour of a well-designed agent.

**Step 5 --- Review the proposed slot and agenda**

> **19.**When Cowork finishes, it displays the proposed meeting: date,
> time, duration, attendees, Teams link, and an AI-generated agenda with
> three talking points. Read the agenda, the points should come from
> your recent email thread, not generic filler.
>
> •Verify every constraint was honoured: no Monday, a morning slot, and
> at least 30 minutes from any existing meeting.
>
> • Click **Approve** to create the meeting, or type adjust the time to
> \[alternative\] for a different slot.

![](media/media/990a325c8e042ff55648bc4296767ba81a258092.png){width="5.604166666666667in"
height="2.6041666666666665in"}

*The proposed meeting details (part 1).*

![](media/media/7e75363d3dad833c4cc07721f670549ae1c47dea.png){width="5.604166666666667in"
height="2.6458333333333335in"}

*The meeting-creation flow (part 2).*

![](media/media/697ea6aef24ac510abc693df217c478d21bd4912.png){width="5.604166666666667in"
height="2.625in"}

*Confirmation that the event was created in Outlook (part 3).*

Cowork found a valid morning slot that satisfies all constraints and
generated an agenda grounded in your email context. The Workspace panel
shows all six steps complete.

**Step 6 --- Test the impossible request**

> **20.**Now deliberately give Cowork a request that cannot be
> fulfilled. Click **+ New task** and enter the prompt below.

+-----------------------------------------------------------------------+
| **PROMPT · IMPOSSIBLE REQUEST**                                       |
+-----------------------------------------------------------------------+
| Review my calendar and the calendar of my account lead. Schedule a    |
| 4-hour                                                                |
|                                                                       |
| Project Planning Workshop tomorrow at a time when we are both         |
| completely free.                                                      |
|                                                                       |
| Constraints:                                                          |
|                                                                       |
| \- Must be tomorrow.                                                  |
|                                                                       |
| \- Must be a continuous 4-hour block.                                 |
|                                                                       |
| \- Must start before 10:00 AM.                                        |
|                                                                       |
| \- Must not overlap with any existing meetings.                       |
|                                                                       |
| \- Must include a Teams meeting link.                                 |
|                                                                       |
| If no time slot satisfies all constraints, explain why the request    |
| cannot be                                                             |
|                                                                       |
| completed and provide the three closest alternative options.          |
+-----------------------------------------------------------------------+

> **21.**Submit the prompt and wait for the response. A well-designed
> agent explains why the request cannot be met and offers alternatives,
> it does NOT silently create a meeting that violates your rules.

![](media/media/d4a69262bf76a042c8ba5bceecb56cb1e1031546.png){width="5.604166666666667in"
height="2.6354166666666665in"}

*Cowork processes the impossible request (part 1).*

![](media/media/a9229d89ee21b3e10944d95c07064c4f86567c5c.png){width="5.604166666666667in"
height="2.6145833333333335in"}

*Checking both calendars and available blocks (part 2).*

![](media/media/a10f2fd9d6038cf7247263770364e3f2541043f3.png){width="5.604166666666667in"
height="2.625in"}

*Evaluating all constraints (part 3).*

![](media/media/eea0b79f86929e309b60d3740ae9878c18b2da0d.png){width="5.604166666666667in"
height="2.6041666666666665in"}

*Concluding the request cannot be fulfilled (part 4).*

![](media/media/02a6904fe58be27bc5453f5e10340b15f4636ca9.png){width="5.604166666666667in"
height="2.5416666666666665in"}

*The three nearest alternative options offered (part 5).*

Cowork still runs a multi-step plan, it checks both calendars, scans for
open blocks, and evaluates every constraint before concluding the
request cannot be met. The final response names the failing constraint
and lists three alternatives. This "graceful refusal" is a critical
safety behaviour in enterprise agents.

**Exercise 3: Executive calendar management**

Act as your own executive assistant by giving Cowork a set of standing
rules for an entire week. Cowork analyses your schedule, proposes all
required changes as a batch, and waits for your review before applying
anything. This is the clearest demonstration of the human-in-the-loop
principle.

Capabilities used:

> •**Standing-rules processing** --- Cowork interprets multi-part
> instructions and applies them systematically across a week.
>
> •**Batch-change review** --- all proposed changes are collected into a
> single review package before any are applied. You approve and reject
> individually.
>
> •**Calendar-load summarisation** --- Cowork calculates meeting hours,
> focus hours, and free-block sizes per day.

**Step 1 --- Enter the executive-assistant prompt**

> **22.** Click **+ New task** to start a fresh conversation.

![](media/media/226d25ac850010c8fb61de247014e6c001ffe991.png){width="5.604166666666667in"
height="3.71875in"}

*A fresh conversation on the home screen.*

> **23.** Type or paste the following prompt:

+-----------------------------------------------------------------------+
| **PROMPT · STANDING RULES**                                           |
+-----------------------------------------------------------------------+
| Act as my executive assistant. Apply these standing rules to next     |
| week:                                                                 |
|                                                                       |
| block two 90-minute focus blocks before noon; decline meetings with   |
| no                                                                    |
|                                                                       |
| agenda after asking the organiser for one; keep Friday afternoons     |
| free;                                                                 |
|                                                                       |
| and summarise every change you make for my approval before applying   |
| it.                                                                   |
+-----------------------------------------------------------------------+

> **24.**Submit the prompt. This is a complex multi-rule instruction,
> watch the Workspace panel break it into individual steps.

![](media/media/33f2a7526b9a6728fbc192dc2b3b0c613d4c931e.png){width="5.604166666666667in"
height="2.65625in"}

*Cowork begins the executive calendar task (part 1).*

![](media/media/9494315fc2659cb5473034b1fcb8c6d9b619967c.png){width="5.604166666666667in"
height="2.6458333333333335in"}

*A structured plan covering all four standing rules (part 2).*

Cowork first gathers context (profile, working hours, timezone), then
scans next week to find where focus blocks fit, which meetings lack
agendas, and whether Friday afternoons are already protected.

**Step 2 --- Review the batch-change proposal**

> **25.**When analysis finishes, Cowork displays a list of ALL proposed
> changes for review, not applied yet (for example, "Block focus time
> Monday 9:00--10:30 AM," "Send agenda request to \[organiser\],"
> "Decline \[meeting\] Friday afternoon").
>
> • Read every item. You do not have to accept all of them.
>
> • Approve the ones you want by clicking **Approve** (or typing
> "approve all" / "approve items 1, 2, 3").
>
> •Deliberately reject at least one item to see that Cowork respects
> partial approvals. For example:

  -----------------------------------------------------------------------
  **FOLLOW-UP**

  Skip the Friday afternoon decline, keep that meeting.
  -----------------------------------------------------------------------

![](media/media/17dbcbc48f605e00003aee6347a95a128ff71a8a.png){width="5.604166666666667in"
height="2.625in"}

*The batch-review list before any change is applied (part 1).*

![](media/media/ce18b7f23c1210989625704a388c6e7a1793e063.png){width="5.604166666666667in"
height="2.6145833333333335in"}

*Approving selected changes (part 2).*

![](media/media/9b79ec2bfd1f1a46193350908260b00cdfcfda92.png){width="5.604166666666667in"
height="2.5625in"}

*Approved changes written to the calendar (part 3).*

![](media/media/929f00d07f5ed29fbb3a021e901075a20b985a4b.png){width="5.604166666666667in"
height="2.6145833333333335in"}

*Rejected items left unchanged (part 4).*

The approve-before-apply pattern is the human-in-the-loop mechanism that
distinguishes Cowork from a fully autonomous agent. Items you reject
remain unchanged.

**Step 3 --- Request the weekly load summary**

> **26.** After approving your changes, type the follow-up prompt below
> in the message bar:

+-----------------------------------------------------------------------+
| **FOLLOW-UP · LOAD SUMMARY**                                          |
+-----------------------------------------------------------------------+
| Show me next week as a load summary: total meeting hours, focus       |
| hours,                                                                |
|                                                                       |
| and largest free block per day.                                       |
+-----------------------------------------------------------------------+

> **27.**Submit it. Cowork re-reads your calendar (now including the
> approved changes) and calculates a structured summary.
>
> **28.** Read the summary. It should show per-day meeting hours,
> focus-block hours, and the largest contiguous free period each day.

![](media/media/edade7169595cfdb392f1604e590b33e7820fa39.png){width="5.604166666666667in"
height="2.65625in"}

*The weekly load summary (part 1).*

![](media/media/b8b90896dae8e93b31df5eed0970ce4ef9db9145.png){width="5.604166666666667in"
height="2.6145833333333335in"}

*Per-day meeting and focus hours (part 2).*

![](media/media/d2d030add0f82d4875936a44d9652767bdfb1dd6.png){width="5.604166666666667in"
height="2.625in"}

*Largest free block per day (part 3).*

![](media/media/1ca70137c252e75f74215aa459c02d3ef279c2b5.png){width="5.604166666666667in"
height="2.3229166666666665in"}

*Load summary continued (part 4).*

![](media/media/0b3445d7f4bde1ea3cb80dbc84a749a663832dbf.png){width="5.604166666666667in"
height="2.5520833333333335in"}

*Load summary continued (part 5).*

![](media/media/bd7592ca41b0e72c327f5064c38687d66ec3bf22.png){width="5.604166666666667in"
height="2.6458333333333335in"}

*The completed day-by-day load analysis (part 6).*

![](media/media/7f74fb5a9bbf7a1e453e0236387fab125c4cd992.png){width="5.604166666666667in"
height="2.625in"}

*Load-summary output detail (part 7).*

![](media/media/e63127ae1e7ca54c6aa103a335e1cae03926387e.png){width="5.604166666666667in"
height="2.6041666666666665in"}

*Load-summary output detail (part 8).*

![](media/media/999922e7f1c5d8c91d35d77418edb3892c26ac70.png){width="5.604166666666667in"
height="2.4583333333333335in"}

*Load-summary output detail (part 9).*

![](media/media/82f43d5ae8f24e85bc93e078480c5a631933b8c6.png){width="5.604166666666667in"
height="2.5833333333333335in"}

*Final load-summary view (part 10).*

Cowork presents a day-by-day analysis, quantifying meeting load,
protected focus time, and free blocks. This is only possible because
Cowork reads your calendar as data, not just as appointments.

**Validation checklist**

Confirm every item before moving to the next lab. If any item fails,
re-run the relevant step and check the troubleshooting tips.

> ☐ Exercise 1 --- All seeded conflicts were detected, and at least one
> conflict was resolved on your Outlook Calendar (the meeting moved to a
> new slot).
>
> ☐Exercise 2 --- The scheduled "Project Sync" honours every constraint
> (not Monday, morning slot, 30-minute buffer) and the agenda contains
> real email context, not placeholders.
>
> ☐Exercise 2 --- The impossible 4-hour request was refused with a clear
> explanation and three alternatives. Cowork did NOT create a
> rule-breaking meeting.
>
> ☐Exercise 3 --- The batch proposal was reviewed and only approved
> items were applied. Rejected items remain unchanged.
>
> ☐ Exercise 3 --- The weekly load summary shows per-day meeting hours,
> focus hours, and largest free block.

**Troubleshooting**

  -----------------------------------------------------------------------
  **Symptom**                **Resolution**
  -------------------------- --------------------------------------------
  "Cowork cannot access my   Open the Cowork connections panel (plug
  calendar."                 icon, or Settings \> Connections) and
                             confirm Outlook Calendar shows as Connected.
                             If Disconnected, click it and
                             re-authenticate.

  "The conflict I seeded was Both events may be in different accounts.
  not found."                Confirm both are in the Primary calendar of
                             your lab account, then type: "Check if any
                             of my meetings tomorrow overlap."

  "Cowork picked a slot that Vague constraints like "prefer mornings" are
  violates my constraints."  treated as preferences. For a hard rule, say
                             "must be before 12 PM," then re-run.

  "The agenda is generic,    Cowork can only ground the agenda in emails
  not email context."        that exist. If there\'s no real thread,
                             type: "Generate the agenda based on the
                             general goals of a project sync instead."
  -----------------------------------------------------------------------

**Key prompting patterns used in this lab**

> • **State rules, not vibes** --- "not Monday, not within 30 minutes of
> existing meetings, prefer mornings" gives measurable criteria. "Find a
> good time" does not.
>
> •**Preview before action** --- for calendar changes, always include
> "summarise every change for my approval before applying it."
>
> •**Test refusal** --- the impossible request in Exercise 2, Step 6 is
> deliberate. Include one request that should be refused; if the agent
> complies, your constraints aren\'t strong enough.
>
> • **Correct in-loop** --- if the wrong meeting is flagged, type a
> correction in the same conversation ("The 3 PM meeting was already
> rescheduled, ignore it") rather than starting over.
>
> •**Scope tightly** --- name the date range ("next 5 business days")
> and the apps ("Outlook Calendar only") to stop Cowork searching too
> broadly.
