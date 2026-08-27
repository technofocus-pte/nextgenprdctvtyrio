# Lab 3-Build a Workforce Upskilling Agent with Microsoft 365 Copilot

Duration: 30 minutes

## Lab Objective 

By the end of this lab, you will be able to:

- Build a custom Workforce Upskilling Agent using Microsoft 365 Copilot
  Agent Builder

- Configure agent instructions aligned to retail workforce
  transformation goals

- Ground the agent in organizational context using Work IQ principles

- Add enterprise knowledge sources to improve agent relevance

- Diagnose employee skill gaps using operational behavior signals

- Generate personalized learning plans for multiple workforce personas

- Use the agent to simulate coaching conversations and leadership
  role-play

- Produce workforce readiness briefings for executive stakeholders

## Lab Scenario

You are Jordan Mercer, Chief Operating Officer of Zava Retail --- a
mid-sized retail chain specializing in consumer electronics and home
goods, operating across four regional store clusters in the Midwest.

Zava Retail is eighteen months into a digital transformation initiative:

- A new Retail Management System (RMS) is being rolled out company-wide

- AI-powered inventory forecasting is active in two regional store
  clusters

- Customer behavior analytics tools are being adopted by store
  supervisors

- ERP migration completes next quarter

Technology adoption is accelerating faster than employee readiness.

To address this challenge, you will build and deploy a Workforce
Upskilling Agent that helps identify skill gaps, personalize employee
learning journeys, and improve workforce readiness across operations.

## Key Personas

1.  Jordan Mercer (COO -- Primary Persona): Leads digital transformation
    strategy and oversees workforce capability planning

2.  Alex Chen (Store Operations Supervisor)- Frequently overrides AI
    inventory alerts without reviewing them

3.  Maria Santos (Supply Chain Analyst)- Leaving in 60 days with
    undocumented critical supplier knowledge

4.  Derek Okonkwo (Operations Coordinator)- Low RMS adoption despite
    extensive legacy systems experience

## Exercise 1: Creating the Workforce Upskilling Agent

Before the agent can support workforce development, you must first build
and configure it inside Microsoft 365 Copilot.

### Task 1: Open Agent Builder

1.  Navigate to
    +++(https://copilotstudio.microsoft.com/)+++ in your
    browser. Sign in with your credentials.\
    ![](media/media/image.png){width="6.25in" height="4.5in"}

2.  Enter your password.\
    ![](media/media/image1b.png){width="5.468017279090113in"
    height="4.985008748906386in"}

3.  From the left navigation panel, click **+New Agent**.

![](media/media/image1c.png){width="6.5in" height="2.0625in"}

### Task 2: Define and Configure Agent 

1.  Paste the following agent details:

> **Agent Name**: +++Zava Retail Workforce Coach+++\
> \
> **Agent Description:** +++
>
> **Agent Instructions:**
>
> *+++You are Zava Retail's Workforce Coach.*
>
> *Your purpose is to help leaders identify workforce capability gaps,
> generate personalized learning plans, support coaching simulations,
> and recommend interventions during digital transformation.*
>
> *Focus on:*

- *RMS adoption*

- *AI inventory forecasting literacy*

- *Customer analytics interpretation*

- *Supply chain risk management*

- *Change adoption coaching*

> *Always tailor recommendations based on:*

- *Employee role*

- *Operational urgency*

- *Experience level+++*

![](media/media/image1d.png){width="6.5in" height="4.4375in"}

2.  In the Knowledge Sources upload these documents:

- RMS onboarding guide

- AI inventory forecasting SOP

- Store operations handbook

- Supply chain transition playbook

- ERP migration training documentation\
  ![](media/media/image1e.png){width="6.25in" height="5.65625in"}\
  ![](media/media/image1f.png){width="4.511970691163604in"
  height="4.083333333333333in"}

3.  Click **Create** to create the agent.

4.  Once the agent is created, go to **Start Chat** to start the chat
    with the agent.

![](media/media/image20.png){width="6.5in"
height="3.0520833333333335in"}

## Exercise 2: Grounding the Agent in Organizational Context

Now that your agent is built, provide it with Zava Retail's
transformation context.

### Task 1: Initialize Agent Context

1.  Paste the following prompt:

> *+++I am the COO of Zava Retail, a mid-sized retail chain specializing
> in consumer electronics and home goods, with 4 regional store clusters
> and approximately 600 employees across store operations, supply chain,
> customer experience, and merchandising.*\
> \
> *We are currently migrating to a new Retail Management System (RMS)
> and deploying AI-powered inventory forecasting and customer analytics
> tools.*\
> \
> *Our key upskilling priorities are:*\
> *1. RMS system adoption*\
> *2. AI inventory and analytics supervisory skills*\
> *3. Supply chain risk management for mid-career analysts+++*
>
> ![](media/media/image21.png){width="6.5in"
> height="2.7916666666666665in"}
>
> ![](media/media/image22.png){width="6.5in"
> height="4.291666666666667in"}

### Task 2: Validate Agent Understanding

1.  To test the agent, paste the following prompt:\
    \
    *+++What are the most critical workforce skill domains I should
    prioritize during this retail digital transformation?+++*

![](media/media/image23.png){width="6.5in" height="4.333333333333333in"}

![](media/media/image24.png){width="6.5in" height="4.322916666666667in"}

## Exercise 3: Diagnosing Workforce Skill Gaps

### Task 1: Diagnose Alex Chen

1\. Paste the following prompt to diagnose workforce skills gaps:\
\
*+++I have a Store Operations Supervisor named Alex who is consistently
overriding AI-powered inventory replenishment alerts without reviewing
them --- approximately 3 times per week over the past month.*\
*Based on this behavioral signal, what skill gaps should I hypothesize,
and what targeted learning plan should I create?+++*

![](media/media/image25.png){width="6.5in"
height="4.354166666666667in"}![](media/media/image26.png){width="6.5in"
height="4.3125in"}

### Task 2: Diagnose Maria Santos

1.  Paste the following prompt to diagnose workforce skills gaps:\
    \
    *+++One of our supply chain analysts, Maria, is leaving in 60 days.
    She owns four sole-source supplier relationships with no documented
    handover process.*\
    *What urgent learning and knowledge transfer plan should I
    implement?+++*\
    ![](media/media/image27.png){width="6.25in"
    height="4.208333333333333in"}

![](media/media/image28.png){width="6.5in" height="4.385416666666667in"}

### Task 3: Diagnose Derek Okonkwo

1.  Paste the following prompt to diagnose workforce skills gaps:\
    \
    *+++Our RMS went live 6 months ago. Derek is at 31% system
    utilization --- lowest on his team.*\
    *He has 11 years of legacy system experience.*\
    *What resistance patterns and skill gaps should I address?+++*\
    \
    ![](media/media/image29.png){width="5.3125in"
    height="3.5770833333333334in"}

2.  Review the output:\
    ![](media/media/image2a.png){width="5.25in"
    height="3.5168274278215224in"}

## Exercise 4: Generating Personalized Learning Plans

### Task 1: Generate Alex's 6-Week Plan

1.  To generate plan for Alex, enter the following prompt:\
    \
    *+++Generate a structured 6-week learning plan for Alex with:*\
    *- Learning objectives*\
    *- Weekly activities*\
    *- Resources*\
    *- Checkpoints*\
    *- Success metrics+++*

![](media/media/image2b.png){width="6.5in" height="4.34375in"}

2.  Review the output:\
    \
    ![](media/media/image2c.png){width="6.25in"
    height="4.156650262467192in"}

### Task 2: Maria's 60-Day Transition Plan

1.  To generate plan for Maria,paste the following prompt:\
    \
    *+++Generate a 60-day knowledge transfer and upskilling plan for
    Maria's transition scenario.*\
    *Include parallel tracks for:*\
    *1. Knowledge transfer*\
    *2. Analyst upskilling+++*

![](media/media/image2d.png){width="6.5in"
height="4.34375in"}![](media/media/image2e.png){width="6.5in"
height="4.572916666666667in"}

### Task 3: Derek's RMS Adoption Plan

1.  To generate plan for Derek, enter the following prompt:\
    \
    *Create an 8-week adoption-focused learning plan for Derek that
    positions RMS mastery as a career growth opportunity.*

![](media/media/image15.png){width="5.145919728783902in"
height="3.5104254155730534in"}![](media/media/image16.png){width="6.009064960629921in"
height="4.0833552055993in"}

# Lab Summary

In this lab, you built a custom Workforce Upskilling Agent in Microsoft
365 Copilot designed to support retail workforce transformation. You
configured the agent's behavior to align with workforce development
goals, grounded it in organizational context for more relevant and
accurate responses, and used operational signals to diagnose workforce
skill gaps. The lab also guided you through generating personalized
learning plans tailored to employee needs, refining agent responses
through prompt engineering for improved effectiveness, and producing
workforce readiness briefings to support decision-making and training
strategy.
