# Lab 1: **Build an Enterprise Marketing Operations Agent with Microsoft 365 Copilot**

**Estimated duration: 40 minutes**

# **Scenario**

Zava Retail is a growing SMB omnichannel retailer with 12 physical stores and a successful online business. Its marketing team runs frequent, multi-channel campaigns — seasonal sales, product launches, loyalty promotions — but has no consistent, repeatable way to plan them.

Every campaign brief looks different depending on who wrote it. Different people produce creative assets for email, social, SMS, and in-store signage separately, often with inconsistent tone and messaging. Executives receive campaign summaries in varying formats, which slows approvals. And when a campaign needs to be adapted — for loyalty members, for a premium audience, or for different store regions — the team frequently starts over instead of building on the original plan.

As Marketing Operations Lead, Priya Nair is responsible for how campaigns move from idea to execution to executive sign-off. With a Summer Clearance campaign due for leadership approval by the end of the week, Priya needs a faster, more consistent way to plan the campaign, produce channel-ready assets, adapt it for different audiences and regions, and package it for executive review.

To solve this, Zava Retail has adopted Microsoft 365 Copilot Chat. Priya will build a reusable custom agent — the Zava Retail Marketing Advisor — that plans campaigns to a consistent enterprise structure, generates creative assets, adapts content for different audiences and channels, and prepares executive-ready summaries.

# **Objectives**

During this lab, you will use Microsoft 365 Copilot Chat to:

- Create a custom Copilot agent — build a dedicated marketing operations assistant from scratch with a defined name and purpose.

- Configure enterprise-grade instructions — enforce a consistent, complete campaign structure and enable image generation and web search.

- Generate a structured campaign brief and creative assets — produce a complete campaign plan and a promotional banner from a single prompt.

- Adapt campaigns for different audiences, channels, and regions — refine content while preserving the original objective and KPIs.

- Prepare and validate an executive approval package — produce leadership-ready materials and confirm the agent works reliably for the whole team.

- (Optional) Extend the agent in Copilot Studio — copy it across, add a human approval step, and validate it with an evaluation test set.

# **Key Personas**

Priya Nair – Marketing Operations Lead (Learner): Owns campaign planning and execution at Zava Retail and builds the Copilot agent to standardize campaign briefs, creative assets, and executive reporting.

David Kim – VP of Marketing: Executive sponsor for the Summer Clearance campaign who requires every campaign brief to include an executive summary, KPIs, and clearly flagged risks and assumptions before he approves it.

Sam Osei – Creative Director: Leads the creative team and needs channel-ready first-draft copy and imagery across email, social, SMS, and in-store signage, so designers and copywriters aren’t starting from a blank page.

Regional Store Directors – North, South, Urban, Rural: Require the same campaign to be adapted to local context — timing, product emphasis, and preferred channels — without changing the underlying campaign objective.

# **Exercise 1: Create and Configure the Marketing Operations Agent**

In this exercise, you will sign in to Microsoft 365 Copilot Chat as Priya Nair and create a new custom agent from scratch. This exercise gets your environment ready for the rest of the lab.

## **Task 1 – Sign In to Microsoft 365 Copilot Chat**

1.  Open a web browser and navigate to +++https://m365.cloud.microsoft/chat/+++.

2.  Sign in with your Microsoft 365 Copilot account credentials.

> ![Screenshot 01](images/image-01.png)

3.  Enter your password.

> ![Screenshot 02](images/image-02.png)

## **Task 2 – Create the Agent**

1.  From the left navigation menu, select New agent.

> Depending on your tenant, the entry may read New agent or Create agent, and in tenants with the new Home experience, agents are managed under Plugins. Use whichever is shown.
>
> ![Screenshot 03](images/image-03.png)

2.  Select Skip.

> Agent Builder can also draft an agent from a plain-language description (Describe tab). This lab uses Skip so everyone configures the same way.
>
> ![Screenshot 04](images/image-04.png)

3.  Paste the agent’s identity:

> Name: Zava Retail Marketing Advisor
>
> Description: Enterprise AI assistant for planning and executing retail marketing campaigns.
>
> Instruction: Paste the following instruction:
>
> +++You are the Zava Retail Marketing Advisor, an enterprise AI
>
> assistant that supports the Zava Retail marketing team in planning,
>
> creating and preparing multi-channel marketing campaigns for the executive
>
> approval.
>
> ROLE AND SCOPE
>
> \- Act as a marketing operations strategist and creative producer.
>
> \- Support campaign planning, audience segmentation, channel adaptation,
>
> regional localization, and executive reporting for retail marketing
>
> initiatives.
>
> \- Stay within marketing, brand, and campaign operations topics. Politely
>
> decline requests unrelated to marketing operations.
>
> RESPONSE REQUIREMENTS
>
> Every campaign-related response must include the following sections,
>
> clearly labelled:
>
> 1\. Campaign Objective
>
> 2\. Target Audience
>
> 3\. Key Messaging
>
> 4\. Channels
>
> 5\. Timeline
>
> 6\. KPIs (Key Performance Indicators)
>
> 7\. Risks and Assumptions
>
> 8\. Executive Summary (3-5 sentences, written for a VP-level audience)
>
> 9\. Creative Assets (descriptions and, where requested, generated images)
>
> STYLE AND TONE
>
> \- Professional, concise, and action-oriented.
>
> \- Default to Zava Retail’s brand voice: confident, customer-first,
>
> optimistic, and inclusive.
>
> \- Avoid unsubstantiated claims; flag assumptions explicitly.
>
> BRAND GUARDRAILS
>
> \- Do not fabricate pricing, legal disclaimers, or discount terms beyond
>
> what the user specifies.
>
> \- Do not generate content that disparages competitors by name.
>
> \- Always mark placeholder data (e.g., dates, budgets) clearly as
>
> \[PLACEHOLDER\] if not provided by the user.
>
> WHEN ASKED TO ADAPT CONTENT
>
> \- Preserve the original campaign objective and core value proposition
>
> unless explicitly told to change them.
>
> \- Clearly state what was changed and why when adapting for a new
>
> audience, channel, or region.
>
> WHEN ASKED FOR EXECUTIVE MATERIALS
>
> \- Prioritize brevity, business impact, and risk visibility.
>
> \- Use structured, scannable formatting (headers, bullet points, short
>
> paragraphs).+++
>
> ![Screenshot 05](images/image-05.png)

## **Task 3: Leverage the Prompt Optimizer**

1.  After pasting the instruction, look for a Prompt Optimizer (or similar “improve instructions”) option in the builder. If present, run it once and compare its suggestion with the pasted text. Do not accept changes that remove any of the nine required sections.  
    ![Screenshot 06](images/image-06.png)

2.  Review the suggestions and select “Apply both Improvements” to apply the suggestions.  
    ![Screenshot 07](images/image-07.png)

3.  Review the updated instructions.  
    ![Screenshot 08](images/image-08.png)

## **Task 4 – Add knowledge Source**

1.  Move to the Knowledge section and upload the files: \[PLACEHOLDER: list the lab file names to upload here\]

> You can use Knowledge sources from your SharePoint/OneDrive/Meetings and Chats in Copilot Chat. Use Attachments while uploading a file directly from your system.
>
> ![Screenshot 09](images/image-09.png)
>
> In current builds, the file-upload option is labelled Attachments (it was Uploaded files).

## **Task 5: Create the Agent**

1.  Select **Create** button to create the agent.  
    ![Screenshot 10](images/image-10.png)

2.  Once you have configured the agent, select **Preview** to start using the agent.  
    ![Screenshot 11](images/image-11.png)

# **Exercise 2: Build the Summer Clearance Campaign Brief**

David Kim has asked Priya for a complete campaign plan for the Summer Clearance event before he’ll consider it for approval. In this exercise, you will test whether a single prompt produces a complete, structured campaign brief.

## **Task 1 – Generate the Campaign Brief**

1.  Open a chat with the Zava Retail Marketing Advisor.

> ![Screenshot 12](images/image-12.png)

2.  Paste the following prompt, then select Send:

> Create a complete Summer Clearance campaign (up to 50% off apparel)
>
> with the full 9-section structure, and generate (render, don’t just
>
> describe) a hero banner image for the Creative Assets section that
>
> reflects the offer and Zava Retail’s brand voice.
>
> ![Screenshot 13](images/image-13.png)

3.  Confirm the Creative Assets section includes a promotional banner concept, and that an image has been generated.  
    ![Screenshot 14](images/image-14.png)

> Note: Generated outputs are non-deterministic and may vary across users, sessions, and environments.

4.  Review the response and confirm it includes all nine required sections: Campaign Objective, Target Audience, Key Messaging, Channels, Timeline, KPIs, Risks and Assumptions, Executive Summary, and Creative Assets.

> Note: Generated outputs are non-deterministic and may vary across users, sessions, and environments.
>
> 5\. Confirm that you get a Word file at the end of the document, that you can export for your reference.  
> ![Screenshot 15](images/image-15.png)

# **Exercise 3: Generate Multi-channel Campaign Assets**

Sam Osei’s creative team needs a running start across every channel, not just the core brief. In this exercise, you will ask the agent to translate the Summer Clearance campaign into channel-ready assets for seven distinct formats in a single request.

## **Task 1 – Generate Channel Assets**

1.  In the same conversation as Exercise 2 (to preserve campaign context), paste the following prompt, then select Send:

> +++Generate assets for this campaign across the following channels: Email,
>
> Teams announcement, LinkedIn, Instagram, Facebook, SMS, and in-store
>
> digital signage. For each channel, provide the copy, tone adjustments,
>
> and any format-specific notes (e.g., character limits, image aspect
>
> ratio).+++
>
> ![Screenshot 16](images/image-16.png)

2.  Review each of the seven channel outputs and confirm they are adapted to the channel.

![Screenshot 17](images/image-17.png)

## **Task 2 – Generate a Promotional Image**

1.  Paste the following prompt, then select Send:

> Generate a promotional image for the Instagram post that matches the
>
> Summer Clearance campaign’s messaging and Zava Retail’s brand voice.
>
> ![Screenshot 18](images/image-18.png)

2.  Confirm that an image is generated and visually consistent with the campaign messaging.

> ![Screenshot 19](images/image-19.png)

## **Task 3 – Save the Channel Format as a Reusable Skill (optional) \[NEW · Rolling out · L1-07\]**

1.  From the left navigation bar, select Plugins.

> ![Screenshot 20](images/image-20.png)

2.  Select the recently created “**Zava Retail Marketing Advisor”.**

> ![Screenshot 21](images/image-21.png)

3.  In the Skills section, select Create with chat.

> ![Screenshot 22](images/image-22.png)

4.  Edit the pre-defined instruction with: “For every channel, give copy, tone adjustment, character limit, and image aspect ratio. SMS must stay under 160 characters.”  
    ![Screenshot 23](images/image-23.png)

<!-- -->

5.  Review the updated skill. Select Update to update the skill.![Screenshot 24](images/image-24.png)

6.  Return to the chat and ask for just the SMS asset again.

> +++Regenerate the SMS asset for this campaign.+++

![Screenshot 25](images/image-25.png)

7.  Confirm the response follows the skill (copy, tone, character limit) and, if shown, that the skill is indicated as used.

> ![Screenshot 26](images/image-26.png)

# **Exercise 4: Refine the Campaign for Loyalty Members**

David Kim has a follow-up request: loyalty program members shouldn’t receive the same “everything must go” clearance messaging as everyone else — they should feel like they’re getting early, exclusive access. In this exercise, you will refine the existing campaign without starting over.

## **Task 1 – Refine for Audience and Brand Tone**

1.  In the same conversation, paste the following prompt, then select Send:

> +++Refine this campaign for loyalty program members, with a more premium
>
> brand feel. Preserve the original campaign objective and KPIs, but
>
> adjust messaging, tone, and offer framing accordingly.+++
>
> ![Screenshot 27](images/image-27.png)

2.  Review the response and confirm it explicitly states:

- What changed (e.g., messaging shifted from “clearance” to “exclusive loyalty access”)

- What was preserved (objective, KPIs, timeline)

> ![Screenshot 28](images/image-28.png)
>
> Note: Confirm the tone reads as more premium — word choice, pacing, and framing should feel distinct from the original mass-market version.

# **Exercise 5: Adapt the Campaign for Regional Stores**

Zava Retail’s regional store directors have flagged that a single national message doesn’t land the same way in every market. In this exercise, you will generate four regional versions of the same campaign.

## **Task 1 – Generate Regional Variants**

1.  In the same conversation, paste the following prompt, then select Send:

> +++Create four regional versions of this campaign for: North stores, South
>
> stores, Urban stores, and Rural stores. Highlight any differences in
>
> messaging, product mix emphasis, or channel priority for each version,
>
> while keeping the core campaign objective identical.+++
>
> ![Screenshot 29](images/image-29.png)

2.  Review each of the four versions and confirm:

- Each has a distinct regional angle (e.g., Urban emphasizes foot traffic and digital signage; Rural emphasizes SMS and local relevance)

- All four versions stay consistent with the original campaign objective and KPIs

> ![Screenshot 30](images/image-30.png)

# **Exercise 6: Prepare the Executive Approval Package**

David Kim has one rule for Friday’s leadership review: every campaign pitch must be scannable in under two minutes. In this exercise, you will generate a complete executive approval package from the campaign you’ve built.

## **Task 1 – Generate the Executive Approval Package**

1.  In the same conversation, paste the following prompt, then select Send:

> +++Prepare an executive approval package for this campaign, including:
>
> \- Executive summary
>
> \- Expected business impact
>
> \- Campaign risks
>
> \- Assumptions
>
> \- Success metrics
>
> \- Approval checklist+++
>
> ![Screenshot 31](images/image-31.png)

2.  Review the response; it must cover the following points:

- Executive Summary: 3–5 sentence overview for a VP-level decision-maker

- Expected Business Impact: quantified or directional impact (revenue, traffic, engagement)

- Campaign Risks: realistic risks (e.g., inventory shortfall, message fatigue, timing conflicts)

- Assumptions: explicitly flagged placeholders (budget, dates, inventory levels)

- Success Metrics: tied back to the KPIs from Exercise 2

- Approval Checklist: actionable items (e.g., Legal review, Brand review, Budget sign-off, Channel scheduling confirmed)

> ![Screenshot 32](images/image-32.png)

## **Task 2 – Save the Package as a File (optional) \[NEW · GA · L1-08\]**

1.  Paste the following prompt, then select Send:

> +++Create the executive approval package above as a one-page Word document David Kim can scan in under two minutes.+++
>
> ![Screenshot 33](images/image-33.png)

2.  Open the file and confirm all six sections are present and it fits on roughly one page.

> ![Screenshot 34](images/image-34.png)

# **Summary**

In this lab, you used Microsoft 365 Copilot Chat to build a custom marketing operations agent for Zava Retail — configuring enterprise instructions that enforce a consistent campaign structure, generating a full campaign brief and multi-channel creative assets, refining the campaign for a premium loyalty audience, adapting it across four store regions, and packaging it for executive approval, before publishing it for the wider marketing team.

By the end of this lab, you should be able to:

- Create a custom Microsoft 365 Copilot Chat agent and configure enterprise-grade instructions

- Generate a structured campaign brief and creative assets, including generated images

- Refine and adapt a campaign for different audiences, channels, and regions while preserving the original objective and KPIs

- Prepare a leadership-ready executive approval package
