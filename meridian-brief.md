# Meridian Energy: Requirements Engagement Brief
**Client:** Meridian Energy (energy supplier, Belgium & Netherlands)
**Issued to:** Functional Analysis team
**Version:** 1.0

---

## The engagement

Meridian Energy is a mid-sized energy supplier serving residential and business customers. They handle several thousand customer complaints per year across phone, email, web form, and walk-in channels.

Their current complaint handling process is manual: complaints tracked in a shared spreadsheet, resolution steps logged in free-text email threads, monthly reporting compiled by hand. They have received two regulatory warnings in the past eighteen months for late handling and insufficient documentation.

Meridian has asked Cegeka Professional Services to define the functional requirements for a new Complaint Management System (CMS). Your team is the FA team on this engagement. A previous vendor started an initial discovery pass but was let go after producing a requirements draft the compliance team rejected as "written from one stakeholder's opinion, not the actual regulation." You are picking this up from scratch.

The engagement lead will walk Meridian's steering committee through a first-look review of your work at the end of the day: not a final sign-off, a checkpoint.

---

## What your team is producing today

By 16:00, your team delivers a requirements package containing:

- **A user story backlog** for the core complaint handling flows, written in standard format with full, testable acceptance criteria
- **At least two process diagrams** in Mermaid syntax: the main complaint handling flow, and one exception flow of your choice
- **A glossary** of domain terms, resolving inconsistent terminology across the source material
- **An open-questions log**: every decision you made that the source material did not explicitly answer, and every real contradiction you found but did not resolve yourselves
- **A traceability note** for every story: where in the source material it came from

Use AI for as much of this as possible. The goal is a professional-quality requirements package in the time available, not proof that you can write user stories by hand. For diagrams, generate Mermaid syntax with AI and render it at mermaid.live to check it actually renders.

---

## Source material

The following is the raw input received from the client. It is messy, incomplete, and in places contradictory, because that is what real client input looks like. Six documents. Read all of them before you start prompting. The most important content is not in the first one.

---

### Document 1: Project initiation email from Sarah Belmans, Head of Customer Operations

*Received three weeks ago. This is what kicked off the engagement.*

> Hi,
>
> Following our call last week, here is a quick summary of what we need.
>
> We want a proper system to manage customer complaints end to end. Right now everything lives in spreadsheets and email and it is a mess. We are getting complaints about our complaints process, which is embarrassing.
>
> The basics: a customer submits a complaint (phone, email, web), it gets logged, someone picks it up, they investigate, they resolve it. We want to track all of that. Customers should be able to see where their complaint is. We want dashboards for management.
>
> The most important thing for us is the 5-working-day resolution target. That is our internal standard and we need the system to enforce it: reminders to handlers when they are approaching the deadline, escalation if they miss it.
>
> One thing I want specifically: if a customer does not respond to our requests for information within 7 days, the complaint should close automatically. We spend too much time chasing people. If they do not engage, we close it and they can resubmit if they want.
>
> Can we also build in some kind of customer satisfaction survey after resolution? Just a simple one: did we resolve your complaint, yes or no, any comments. We want to track that over time.
>
> Let me know if you need anything else.
>
> Sarah

---

### Document 2: Interview notes, Sarah Belmans, Head of Customer Operations

*Interview conducted on-site, 45 minutes. Paraphrased notes, not a transcript.*

Sarah is focused on operational efficiency and management visibility. Her main frustration is that she cannot currently see at a glance how many complaints are open, who owns them, and what stage they are at.

On complaint categories: she mentioned billing complaints, supply interruptions, contract disputes, and "general service complaints" as the main types. She was vague about whether different types need different handling: "they all go through the same process basically, some just take longer."

On roles: she described two roles: **complaints handlers** (investigate and resolve) and **team leaders** (oversee handlers, handle escalations). Team leaders can reassign complaints between handlers, but she was not clear on what else they can do differently.

On the web submission channel: "customers fill in a form, it goes into the system, same as everything else." She assumed the web form already exists. When pressed, she admitted it does not and said "IT will sort that out."

On reporting: she wants a monthly report showing volume, resolution times, and satisfaction scores by category. "Automated, not something someone has to compile manually."

On business customers: "they have an account manager, so usually complaints go through the account manager first. I am not sure how that works exactly. You would need to talk to the commercial team. It is probably out of scope for now."

---

### Document 3: Interview notes, Marc Devos, Senior Complaints Handler

*Interview conducted on-site, 30 minutes. Marc has handled complaints at Meridian for six years.*

Marc was cautious about the project. He has seen system implementations before that made his job harder rather than easier.

On the current process: "We get the complaint, we log it (in the spreadsheet), we send an acknowledgement to the customer within two working days, then we investigate. If we need more info from the customer we send a request and wait. If we need to involve another department (billing, network, whatever), we send an internal request and wait for them to come back. Then we write up the resolution and close it."

On the 5-day target: "Five days is the target but it is not realistic for anything involving another department. Those requests can take two weeks. We flag it to the team leader and they approve an extension. That happens probably thirty percent of the time. The system needs to support that: extensions with a reason, approved by the team leader."

On auto-closing complaints: "We cannot auto-close complaints. Full stop. We got a fine from the regulator two years ago partly because of something like that. If a customer does not respond, we send a reminder, then another reminder, then we send a letter telling them we are closing in 14 days unless we hear from them. Only then can we close. And even then it is manual sign-off, not automatic."

On the acknowledgement: "The two-working-day acknowledgement is a regulatory requirement, not just our policy. The system needs to flag immediately if an acknowledgement has not been sent within two working days. That is non-negotiable."

On complaint categories: "Billing is the biggest one by far. Supply issues are rare but serious. Those always need to involve the network team. Contract disputes are usually straightforward. There is also a fourth category that Sarah probably did not mention: regulatory complaints. Those are complaints where the customer has already been to the regulator or says they are going to. Those have completely different handling rules and I would want to make sure the system supports that properly."

---

### Document 4: Interview notes, Priya Nair, Compliance Officer

*Interview conducted by phone, 20 minutes. Priya joined the call late and had limited time.*

Priya's perspective was almost entirely focused on regulatory obligations. She was surprised nobody had briefed her more thoroughly before the project started.

On regulatory timeframes: "The five-day target Sarah mentioned is internal. The regulatory requirement is different. For standard complaints we must acknowledge within two working days. Marc is right about that. For resolution, the regulation says we must make reasonable efforts to resolve within eight weeks. If we cannot resolve within eight weeks, we must write to the customer explaining why and what their options are including escalation to the ombudsman."

On regulatory complaints specifically: "If a customer mentions the energy ombudsman or a regulatory body, that complaint is immediately classified as regulatory and must be escalated to me or my team within two working days of receipt. Not five days. Two days. The handling process is different and I manage those personally. This is not optional."

On auto-closing: "I agree with Marc. Auto-closing is not acceptable from a compliance standpoint. I want to be very clear about that."

On data retention: "All complaint records must be retained for five years. That includes every communication, every internal note, every status change. If the system deletes or archives anything before five years I will block the go-live."

On business customers: "Business customers above a certain contract value have a dedicated escalation path. I do not know the threshold off the top of my head. You would need to check with the commercial team. But it is not out of scope. If we build this system without it we will have to retrofit it and that will be painful."

---

### Document 5: Email from Tom Geerts, IT Manager

*Received this week, in response to a question about existing systems.*

> Hi,
>
> To answer your questions about the current landscape:
>
> 1. Customer data lives in our CRM system (Salesforce). Any new complaint system needs to integrate with Salesforce or at minimum look up customer records by account number or email address. We cannot have two separate customer databases.
>
> 2. The customer portal is being replaced. We signed a contract with a new vendor last month. Go-live is expected in about 14 months. I would strongly recommend not building the customer-facing complaint tracking on top of the current portal. It will be thrown away. If you want customer-facing functionality, design it so it can be dropped into the new portal when it is ready.
>
> 3. Email handling: our current inbound email goes to a shared mailbox. Complaints that arrive by email are manually copied into the spreadsheet. If the new system can pull from that mailbox automatically that would be great but it is not a hard requirement from my side.
>
> 4. We have an internal ticketing system (ServiceNow) for IT issues. Please do not use ServiceNow for complaints. It has been suggested before and it is a bad idea. They are different processes with different audiences.
>
> Tom

---

### Document 6: Current state process description

*Provided by Marc as a written summary of how complaints are currently handled.*

1. Complaint received via phone, email, or walk-in
2. Handler logs complaint in shared spreadsheet: date, customer name, account number, channel, brief description, category, assigned handler
3. Acknowledgement email sent to customer (target: within 2 working days)
4. Handler investigates. If additional information needed from customer, handler sends request email and updates spreadsheet with "awaiting customer info" status
5. If another department is involved, handler sends internal email to that department and updates spreadsheet with "awaiting internal input" status
6. Once information received, handler resolves complaint and sends resolution email to customer
7. Spreadsheet updated with resolution date and brief resolution summary
8. Monthly: team leader exports spreadsheet, produces report for management

*What is not in this description: what happens when a handler is absent and their complaints are unattended, what happens to complaints received outside business hours, what triggers escalation to the team leader beyond the extension approval, how duplicate complaints from the same customer about the same issue are identified and handled.*

---

## Technical constraints

- No authentication design required today. Assume Meridian's existing SSO handles login; focus on the complaint domain
- The system must be designed to integrate with Salesforce for customer lookup (do not design a second customer database)
- The system must be designed so customer-facing functionality can be handed to the new portal team when it goes live in ~14 months. Do not couple requirements to the current portal
- All complaint records, including every communication, internal note, and status change, must be retained for five years

---

## What is out of scope for today

- The commercial/account-manager complaint path for business customers (until the open question about it is resolved; see below)
- Detailed Salesforce integration field mapping
- Visual/UI design: you are producing functional requirements, not mockups
- The customer satisfaction survey question design (note it as a story, do not design the survey itself)

---

## Definition of done for today

You will not produce a complete requirements package. The goal is a package you can defend.

At the end of the day, each team presents:

1. **At least three user stories, walked through in full**: the core submission and acknowledgement flow, one story involving escalation or extension, and one of your choice. For each: point to where in the source material it came from, and name one thing AI produced that you had to correct or question.
2. **One process diagram**, walked through live: name one flow or exception that was missing from what AI first generated.
3. **Your top three open questions**: the things from the source material you could not resolve, that would block a development team from starting work if left silent.

*Meridian steering committee framing, from the engagement kickoff call:*
> "We don't need you to have all the answers today. We need to trust that you know which questions you haven't answered yet. The last vendor didn't. That's why they're not here anymore."
