# Copilot Studio Agent Security & Governance

Lab duration- 30 minutes

## Lab Objective

Zava Retail\'s e-commerce team has started building Copilot Studio
agents to handle customer order lookups, returns, and internal inventory
questions --- without IT security involvement. This lab teaches
participants how to assess and govern those agents: reviewing an
agent\'s security posture, restricting what it can connect to and read
via DLP, controlling who can invoke it, and confirming its activity is
auditable --- so Zava can let store and e-commerce teams keep building
agents without losing control of customer or inventory data.

## Lab Overview

Citizen developers are shipping Copilot Studio agents faster than
security teams can review them --- and the biggest misconception is that
an agent adds a security boundary of its own. It doesn\'t. An agent
inherits whatever permissions its maker (or, for event-triggered agents,
its caller) already has, and it will faithfully expose whatever was
already left open.

This lab uses Zava Retail\'s agent --- a customer-facing agent built by
a business analyst, connected to a SharePoint order-records site,
published on an unauthenticated Web Channel, and wired to a
refund-issuing Power Automate flow --- as the case study for what
happens when an agent ships before security is looped in. You\'ll work
through the same review a governance lead would run today: reading an
agent\'s built-in security posture indicator, writing a DLP policy that
actually constrains it, comparing authentication modes and where
Conditional Access picks up, and locating the agent\'s audit trail ---
including the specific category of activity that Customer Lockbox does
not cover.

Along the way you\'ll also stand up a second, simpler agent (Zava
Inventory Watcher) to see agent creation and knowledge-grounding from
scratch, separate from the governance walkthrough on OrderBot.

## Scenario

Zava Retail\'s Customer Care team built a Copilot Studio agent called
"OrderBot" to let customers check order status and initiate returns via
the company website. To move fast, the maker (a business analyst, not an
IT admin) connected OrderBot to the SharePoint site holding customer
order records, enabled the Web Channel without requiring sign-in so
shoppers wouldn\'t need an account to use it, and gave it access to a
"Returns" Power Automate flow that can issue refunds.

Zava\'s security team has just been looped in --- after a routine review
flagged that OrderBot is publicly reachable, unauthenticated, and has
write access to a refund-issuing flow. Nobody currently knows what data
it\'s exposed, who\'s queried it, or whether the connectors it uses are
sanctioned. You\'re the security/governance lead brought in to assess
and lock this down before it goes further.

## Pre-requisites

Access required

- Power Platform admin center access (Environment Admin at minimum;
  System Administrator on any environment with a Dataverse database,
  which is required to scope environment-level DLP policies there)

- Copilot Studio maker access to at least one environment

- Microsoft Purview compliance portal access with Audit permissions, for
  Part 4

- A Microsoft 365 license assigned to your test/reviewer account ---
  required for Copilot Studio to record Purview audit events and
  transcripts in the first place

Licensing note

- If your tenant has Agent 365 provisioned and you want to explore the
  Agent Registry or ownerless-agent reassignment features referenced in
  the wrap-up discussion, Agent 365 requires Microsoft 365 E5, F5
  Defender and Purview, or Business Premium --- E3, Business Basic, and
  Business Standard are not eligible. This isn\'t required for the core
  lab, but flag it if participants ask why they can\'t see the Agent 365
  registry.

Environment setup (facilitator-provisioned)

- One test agent with an unauthenticated Web Channel enabled

- One connector identified in advance to block via DLP

## Learning Objectives

By the end of this lab, participants will be able to:

- Explain why an agent doesn\'t add a security layer of its own --- it
  inherits the maker\'s or caller\'s existing permissions, so
  oversharing upstream becomes agent exposure downstream.

- Review an agent\'s security posture (auth gaps, policy impacts) from
  the Copilot Studio authoring experience.

- Create a Power Platform DLP (data) policy that restricts connectors
  and knowledge sources for agents in an environment.

- Compare authenticated vs. unauthenticated agent access and know when
  to require Entra ID sign-in.

- Locate an agent\'s audit trail (invocation, tool calls, policy
  decisions) in Purview --- and know what Customer Lockbox does not
  cover.

- Use the Analytics Viewer role to give a non-editing stakeholder
  least-privilege visibility into an agent\'s usage and risk signals.

## Exercise 1 --- Creating the Zava Inventory Watcher Agent

Before the agent can act autonomously, you must first build and
configure it inside Copilot Studio.

### Task 1 --- Open Agent Builder

1.  Navigate to copilotstudio.microsoft.com in your browser.

2.  Sign in with your credentials.

3.  Enter your password.

4.  From the left navigation panel, select + Create, then New agent.\
    ![](media/media/image.png){width="6.25in"
    height="2.0416666666666665in"}

### Task 2 --- Define and Configure the Agent

1.  Paste the following agent details:

> **Agent Name**: +++Zava Inventory Watcher+++

**Agent Description:** +++Watches Zava Retail\'s product inventory and
automatically emails procurement when stock drops below the reorder
threshold.+++

**Agent Instructions:**

+++You are Zava Retail\'s inventory assistant. When a product\'s stock
level falls below its reorder threshold, generate a concise restock
request email to the procurement contact.

Include the product name, SKU, current stock level, reorder threshold,
and a suggested reorder quantity (assume 2x at the threshold unless told
otherwise). Keep the tone efficient and professional.

If the SKU, stock level, or procurement contact email is missing, do not
send the email --- instead flag the record for manual review.+++\
![](media/media/image2.png){width="6.5in" height="3.6354166666666665in"}

2.  Select Publish to create the agent.\
    ![](media/media/image3.png){width="6.25in"
    height="1.4895833333333333in"}

### Task 3 --- Add Knowledge

Autonomous agents rely heavily on clear instructions and grounded
knowledge, since there is no human steering the conversation
turn-by-turn.

1.  Go to the Knowledge tab and select Add knowledge.\
    ![](media/media/image4.png){width="6.25in"
    height="3.5104166666666665in"}

2.  Upload the Zava Inventory file.\
    ![](media/media/image5.png){width="6.25in"
    height="4.479166666666667in"}

3.  Save your changes.\
    ![](media/media/image6.png){width="6.25in"
    height="2.8645833333333335in"}

## Exercise 2- Build a Power Platform DLP Policy for Agents

### Task 1- Build the DLP policy

1.  Go to the Power Platform admin center.\
    ![](media/media/image7.png){width="6.25in"
    height="2.6354166666666665in"}

2.  On the left navigation bar, select Security \> Data and privacy \>
    Data Policy![](media/media/image8.png){width="6.25in"
    height="1.75in"}

3.  Select Create New Policy.\
    ![](media/media/image9.png){width="6.25in" height="3.46875in"}

4.  Configure the policy by entering the required information at each
    step. Paste the policy name- +++New_Policy+++. Click Next.\
    ![](media/media/imagea.png){width="6.25in"
    height="4.145833333333333in"}

5.  Select the env in which you have built your Zava Inventory Watcher
    agent. Select Next.\
    \
    ![](media/media/imageb.png){width="6.25in"
    height="4.135416666666667in"}

6.  Assign the connectors to the policy that will be available in your
    agent env. To test the DLP policy, block the available Sharepoint
    connectors. For your agent, you primarily want to block- "Knowledge
    source with SharePoint and OneDrive in Copilot Studio." Select
    Next.\
    ![](media/media/imagec.png){width="6.25in"
    height="4.208333333333333in"}

7.  Review the changes. Select Create
    policy.![](media/media/imaged.png){width="6.25in"
    height="4.15625in"}

8.  Save and publish the policy, then return to your Zava agent.

### Task 2- Testing the DLP policy

1.  Navigate to your Zava Inventory Watcher agent.\
    ![](media/media/imagee.png){width="6.25in"
    height="1.5416666666666667in"}

2.  Navigate to Knowledge section. Select +Add knowledge.\
    ![](media/media/imagef.png){width="6.25in"
    height="4.541666666666667in"}

3.  Select SharePoint knowledge connector.\
    \
    ![](media/media/image10.png){width="6.25in" height="4.625in"}

4.  Select the knowledge source you wish to add through SharePoint.
    Select Add to agent.\
    ![](media/media/image11.png){width="6.25in" height="4.46875in"}

5.  As we have blocked the SharePoint connector in our DLP policy, you
    wont be able to connect any knowledge source through SharePoint. The
    knowledge source will appear as blocked.\
    ![](media/media/image12.png){width="6.25in" height="5.1875in"}

6.  Hence, the DLP policy is in place.

## Exercise 3 - Review an Agent\'s Security Posture

1.  In the authoring experience, locate the agent status / security and
    protection posture indicator.\
    ![](media/media/image13.png){width="6.25in" height="5.375in"}

2.  Identify any flagged issues --- e.g., authentication gaps, DLP
    policy impacts on connectors/knowledge sources the agent uses.\
    ![](media/media/image14.png){width="6.25in"
    height="3.0729166666666665in"}

3.  You wont be able to publish the agent unless you resolve and remove
    the SharePoint knowledge source from the agent.\
    ![](media/media/image15.png){width="6.25in"
    height="2.5208333333333335in"}

## Exercise 4 --- Compare Authenticated vs. Unauthenticated Access

### Task 1- Reviewing the No Authentication settings

1\. In your test agent, select the **three dots (...)** in the authoring
toolbar → **Settings** .\
![](media/media/image16.png){width="6.5in"
height="3.6145833333333335in"}

2\. Navigate to **Security** tab → **Authentication.**\
![](media/media/image17.png){width="6.5in" height="2.5625in"}

3\. Select No authentication. Click
Save.![](media/media/image18.png){width="6.5in" height="2.53125in"}

4\. Go to the **Publish** page and check that you wont be able to
publish the agent because there is no authentication.\
![](media/media/image19.png){width="6.5in"
height="3.3333333333333335in"}

### Task 2- Switch to Authenticate with Microsoft

1.  In Authentication, change the mode to **Authenticate with
    Microsoft**. **Save**, then **publish** the agent.

![](media/media/image1a.png){width="6.5in"
height="2.6145833333333335in"}

2.  The Agent Status will show as Ready.\
    ![](media/media/image1b.png){width="6.25in" height="1.96875in"}

3.  Navigate to the Channel section. Here you can view the channels
    available through the current authentication settings.\
    ![](media/media/image1c.png){width="6.25in" height="5.3125in"}

4\. Go back to the **Publish** page and confirm Teams/SharePoint/M365
Copilot channels are **now available** to select --- this is the
concrete, visible proof the mode actually changed something, not just a
setting that says something different.

### Task 3- Switch to Authenticate manually

1.  Change the mode to **Authenticate manually**, and walk through
    what\'s now required that wasn\'t before: **Service provider**,
    **Client ID**, **Client secret or federated credential**, **Redirect
    URI**.\
    ![](media/media/image1d.png){width="6.25in" height="3.46875in"}

2.  Enter the required sample information in the required fields.

![](media/media/image1e.png){width="6.5in" height="4.635416666666667in"}

3.  The agent requires you to sign in manually before testing the
    agent.\
    ![](media/media/image1f.png){width="6.25in"
    height="3.4895833333333335in"}

## Lab Summary --- What This Lab Teaches

This lab is built around one central idea: **an agent doesn\'t add a
security layer --- it inherits whatever permissions and exposure already
exist**, and everything else in the lab is about learning where that
inherited risk becomes visible and how to close it.

**Building an agent shows you how little friction stands between
\"idea\" and \"production.\"** Exercise 1 has you stand up Zava
Inventory Watcher in minutes, with no admin involvement --- mirroring
exactly how OrderBot got built in the scenario. This is deliberate: the
lab wants you to feel how easy it is to ship an agent before governance
catches up.

**Reading an agent\'s posture is the diagnostic skill, not a one-time
check.** Exercise 2 teaches you to find and interpret Copilot Studio\'s
built-in security/protection indicator directly in the authoring canvas
--- the same signal a maker sees, not just what an admin sees from the
Power Platform admin center. You learn to distinguish an actual flagged
risk (an auth gap, a blocked connector) from the absence of one, and to
tie each flag to a concrete reason it matters, not just \"it\'s red.\"

**DLP policy is where governance becomes enforceable, not just
visible.** Part 2 moves you from *seeing* a gap to *closing* it ---
scoping a policy to an environment, restricting connectors/knowledge
sources/channels, and confirming the policy-impact warning actually
shows up where you expected. This is also where you learn the
environment-scoping mechanics (Environment Admin vs. System
Administrator, tenant-level vs. environment-level policies) that trip
people up in real tenants.

**Authentication is the gate everything else depends on.** Exercise 4 is
the practical proof of this: you don\'t just read about the three auth
modes, you toggle between them and *watch the consequences* --- a
sign-in prompt appears, M365 channels unlock, an admin-level policy can
lock the maker\'s choices entirely. The lab makes you verify each change
instead of trusting that a setting did what it says, and it draws the
line between what Copilot Studio itself enforces (auth mode) versus what
only Entra Conditional Access can add on top (MFA, device compliance)
--- a boundary that\'s easy to blur in discussion but obvious once
you\'ve tried to find it in the UI.

**Audit visibility closes the loop.** Part 4 shows you where an agent\'s
activity actually lives --- Purview\'s audit pipeline, not Copilot
Studio itself --- and forces you to articulate a boundary people often
assume incorrectly: Customer Lockbox protects against Microsoft engineer
access, not against your own blind spots in your own tenant\'s audit
trail.
