# Incident Response Process at Acme Corp

_Are you actively experiencing an incident and need support? Make a copy of the [incident template][wiki_incident_template_link] to use as a checklist and reduce cognitive overhead. The most important thing to focus on is remediating the incident. Page [incident on-call rotation][incident_oncall_rotation] for emergency assistance._

Building customer trust, acting as an owner in all we do, and continuously learning are critical values at Acme Corp. We reflect these values in how we build and deliver our products and in how we support our customers. We also reflect these values in how we approach software incidents.

This document outlines our organization-wide incident response process. It is designed to be a living document that captures best practices from our shared experience. This document will grow and change with us as we scale.

Email [concerned_responders@acme.com][concerned_responders_email] with questions, concerns, or proposed updates to this document.

## Incident response process outcomes

Stealing a page from agile’s story mapping methods, these are the intended outcomes of this incident response process:

As a responder, during an incident:

* I avoid troubleshooting on the customer's dime and prioritize remediation, even if that creates additional engineering work later.
* I know when to escalate and it’s clear how to do so.
* I understand who owns the services and processes involved in the incident.
* I have a clear understanding of business and customer expectations during and after an incident.

As an affected customer or customer-facing stakeholder, during an incident:

* I know that I will receive proactive communication about incidents.
* I know what functionality is impacted and how.
* I know when to expect updates or, if possible, remediation.
* I know about any potential workarounds.

As an organization, during an incident:

* We understand that when managing a complex system, avoiding all incidents is impossible.
* While we can’t entirely avoid incidents, we do our best to build resilient systems and ensure our response is as efficient and effective as possible.
* We strive to learn from and improve after every incident, focusing on systems and processes rather than blaming individuals or teams.
* We are pragmatic; this response process can’t account for all situations, so we support responders in using common sense when deviating from the process.

## Detailed process by milestone

While incidents are unpredictable by nature, almost all of them progress through a series of predictable phases or milestones. This section lays out the progression of an incident, the expectations and next steps for responders to follow during each phase, and some practical advice to help guide them.

### Decide

#### In the first 10 minutes of identifying a possible issue, the first responder will:

Using the [incident severity definition/matrix](#severity), decide if the issue at hand qualifies as an incident. If it’s unclear if the issue warrants incident status based upon our definitions, but evidence indicates something is wrong, err on the side of declaring an incident. Engaging a broader group can help confirm whether or not the  suspect occurrence  is an issue and determine what next steps should be taken.

It’s better to declare an incident, then quickly downgrade it to a bug than to let an issue simmer and potentially have a negative impact on our customer experience.

If it’s determined that an issue is not at “incident” level, please create a bug in the appropriate team's backlog using the [service ownership table][service_ownership_resource].

If it’s determined that the issue is an incident, the first thing to do is name an incident commander. Ideally, a member of the team most closely related to the issue will assume the role of incident commander for the duration of that incident. If it’s unclear what teams are related or there is a delay in the team's engagement, these duties should be carried out by someone in the initial incident declarer group who is less critical for the technical triage effort.

### Declare

#### In the first 20 minutes, the incident commander will:

* Page the owning team of the impacted service or functionality based on [this document][service_ownership_resource]. If it’s unclear who owns the impacted service, page the [incident on-call rotation][incident_oncall_rotation] for assistance
* Create a new incident document from the [incident document template][wiki_incident_template_link]
    * Name it using the format: [inc-YY-MM-DD-SEV-X] {functionality} is {state} for {audience}
    * Move it [here][wiki_incident_directory]
* Fill out the initial incident description and format for initial communication in the incident document. Here’s an example:

        Subject: SEV1/SEV2/SEV3 Incident - {functionality} is {state} for {audience}

        <Functionality> is currently experiencing a SEV1/SEV2/SEV3 incident. The required teams are being engaged and are actively triaging the issue.

        Identified time: 23:xx est

        Description of customer impact: Customers can not log in after clearing cookies

        Quantity of customers impacted: Unknown/All/Some/Few

        Known customers impacted:
        * Customer 1
        * Customer 2

        Please see the [incident document](http://dummy-link-to-incident-doc.com) for additional details. For additional questions, respond to this email thread.

        Expect an update on the status of this incident in (30 minutes | 1 hour | 3 hours) or sooner.

        &lt;Responder Name>

* Send the created message to the [incident distro][incident_distro_email] email distribution list and post it in the [#incidents][general_incidents_chat_channel] chat channel.
* Create a dedicated chat channel using the format using the format: inc-YY-MM-DD-SEV-X-{functionality} is {state} for {audience} and post a link to the incident document in the channel and bookmark the file.
* Create and join a video bridge &lt;link to create a video bridge>
    * Add the link to the incident document

#### General advice for the declare phase:

* Try to remain calm when declaring an incident.
* Incidents are a team sport. Engage other members of your team, dedicated subject matter experts (SMEs), and your broader leadership group to get the support you need to remediate the incident successfully.
* It is important from the start of the incident until the end of the first hour to strike a balance between communicating and working to remediate the incident. Too much focus on one or the other can lead to a longer incident or missed communication expectations for stakeholders and customers.
* Slow down. Take a handful of minutes to accurately summarize what is currently happening and what steps have been taken in your initial communication. It’s better to take an extra minute or two to craft initial communications in the format and with the details that will be expected by the rest of the organization than to send something hastily and leave room for concern. It is also okay to share unknowns when they are present.

### Triage, Coordinate, and Communicate

At this stage in the incident response process, the goal is to ensure that responders have what they need to begin remediating the incident at hand, and that stakeholders and customers (when deemed necessary) are receiving regular status updates. Basically, here’s when you want to keep everything moving forward at a steady pace and proactively relieve fears from affected or interested parties outside the incident.

At this point, everyone who is needed to remediate the incident should be in the incident channel, and you should be starting to understand the incident better. Maybe you’re even starting to crystalize how you’ll remediate the incident.

#### General advice for the triage, coordinate and communicate phase:

Remember, the main priority in this phase is remediation — focus on mitigating customer impact and not on digging deeply into the “why” of the matter (unless, of course, that’s required to mitigate the impact). At this stage in the response process, it can be easy to go down tangents, get distracted by red herrings, and dig into technical issues that, again, don’t directly relate to mitigating the impact to customers.

#### Until incident resolution, the incident commander will:

    Note: The parenthesis format “( )” is to indicate that the step is recurring and response times are severity dependent. Severities map as follows: (SEV1/SEV2/SEV3)

    Example: During a SEV1, emails to the incident distro should be sent on a 30-minute cadence.

* Record any relevant technical information or events during incident triage in the Timeline section of this document (ongoing)
    * See the Timeline section of this document for examples of relevant entries
* Monitor the incident chat and the video bridge (ongoing)
    * Listen for indicators that understanding of the impact is changing; if the impact is greater in severity than initially thought, update the severity and communicate to the incident disto and chat channel
    * If the responder team is struggling to make progress and you have exhausted your available options, consider escalating to technical leadership to aid in engaging responders with fresh eyes and/or deeper expertise
* Every (20m/50m/2h50m) check in with responders and compose a status update
* Every (30m/1h/3hr) send the update to the [incident distro][incident_distro_email] list by replying to all on the initial email thread. Add the update to the Latest Communication section of the incident document and post the update to the incident chat channel.

Example "update" messaging:

        UPDATE: {functionality} is {state} for {audience} is still experiencing a SEV1/SEV2/SEV3 incident.

        The team is investigating/has identified/has mitigated the (issue).

        <A non-technical, realistic but confidence-inspiring description of the state of incident> No additional resources are required at this time.

Please see the [incident document](http://dummy-link-to-incident-doc.com) for details.


            Expect an update on the status of this incident in (30 minutes | 1 hour | 3 hours) or sooner.

            <Responder Name>

* Every (1h/3h/- ) update the status page
    * Add the public link to Add the update to the Latest Communication section of the incident document as an item in the timeline

Example “investigating” messaging:

    Our monitoring systems have detected a potential issue with requests to our API. Our engineering team has been alerted and is actively investigating. We will provide an update in 1 hour or as soon as more information is available.

Example “update” messaging:

    We continue to investigate an issue where requests to our API are returning an error. Customers may intermittently receive 500 internal server errors from all endpoints. We expect to provide another update in 1 hour or as soon as more information is available.

Example “resolved” messaging:

    All endpoints were degraded for 15 minutes between xx:xx am and xx:xx am Eastern Time on xx/xx/20xx. During this period, customers may have intermittently received 500 internal server errors. The issue has now been resolved.

### Mitigate and Resolve

An incident is resolved when the following conditions are met:

* The changes made to mitigate customer impact are durable and will last until a long-term solution can be designed and implemented
* As the incident commander, I have reviewed this document and signed off that the current state of the document is as accurate as is reasonable at the time of resolution (pay specific attention to the Timeline and Incident Data sections of this document)
* A 45-minute initial retrospective for all responders has been scheduled within 24 to 48 business hours of mitigation
* A final update has been sent to the incident distro list that includes the following:
    * Date/time of the retrospective
    * Status of the incident and list of customers who were impacted
    * A brief overview of what next steps are (if any)
    * Kudos for responding teams

    Example stakeholder email:

        Subject: Resolution: SEV1/SEV2/SEV3 {functionality} is {state} for {audience} is resolved.

        <Describe how things are being left> Impact has been mitigated for all customers. The status page has been updated with a resolved status.

        All adversely impacted customers have an in-app notification to communicate the extent of the impact they experienced and have had an email sent to their CSM.

        A retrospective has been scheduled for {date}, please respond to this email if you would like more details.

        A special thanks to all the responders of this incident including team x and the customer support team, who really helped us resolve this issue.

        Please see the [incident document](http://dummy-link-to-incident-doc.com) for details.

### Blameless retrospective

Retrospectives are used to close out an incident experience. These are a psychologically safe spaces where responders reflect on the incident, capture valuable insight, and determine any action items needed. We prefer the term ‘retrospective’ over other popular terms (aherm, postmortem), because no one has died.

Run well, these meetings can create positive feedback loops for the incident management program, ensuring learning from the incident get piped back into the broader organization and the incident process itself. We value outcomes from retros that include greater insight into systems (both social and technical), deeper understanding of the experience of all responders and their actions taken during an incident. Action items are another possible outcome of an effective retrospective, but should not be considered a requirement.

* When
    * Hold a retrospective within 24 to 48 business hours after the resolution of the incident for maximum retention of the experience by participants.
* Who
    * Invite all responders, regardless of department. This includes non-engineers like customer-facing team members, for example. Inclusion of all responders drives opportunities to improve processes, build customer empathy, and provide insights that might otherwise be missed.
* How
    * How to encourage healthy and productive retrospectives:
    * Don’t assign blame to individuals.
    * Pay attention for changes to our systems and processes that support the humans running them.
    * Stick to a standard agenda:
        * What was the final assessment of customer impact?
        * What went well?
        * What could be improved?
        * Where did we get lucky?
        * What were we wrong about?
        * Links to action items

# Appendix

## Definitions

### Incident

* An unexpected degradation or interruption of functionality in our product to a degree that is noticeable to our customers or internal stakeholders. The extent of the impact and our response to any given incident is delineated by the severities defined below.

### Incident document

* The incident document is the source of truth for the incident. An incident can be run entirely with the incident document’s guidance. It also serves as the collection point for all information relating to the incident during triage and after resolution.
* The incident commander is accountable for ensuring this document is up to date and will often serve as the document’s primary scribe, although others should feel free to contribute and comment. Similarly, in a sufficiently complicated incident, scribing can be delegated to another, more available responder.
* Training the organization to review the document before engaging responders directly helps ensure everyone is on the same page and minimizes unneeded disruptions to the response effort.

### Severity

* SEV1: Major incident
    * Breached customer SLA or any condition that will lead to the imminent breach of a customer SLA
    * Core functionality of the product is unavailable
    * Customer data is being lost or appears to the customer to be lost
* SEV2: Minor incident
    * Conditions exist that will cause the breach of a customer SLA before the next business day
    * Application is available, but performance is degraded or non-critical functionality is unavailable
* SEV3: Investigation
    * Non-critical product functionality is broken but not significantly detrimental to the customer experience

### Owned services

* Ownership document or architecture diagram outlining all services and functionalities in the product(s) and list owners and contact information for each. This should include critical vendors and contact information for their support organizations and status pages.

Example CSV headers:

	functionality, service, owning team, paging schedule link
	vendor, product, owning team/owner of relationship, link to vendor support portal, vendor status page

### Responder roles

* Triage engineer
    * A service owner who is on call and paged for interruptions to a service
* SME
    * Subject matter expert of adjacent services or domains (DBAs, cloud engineers, operations, etc.)
* Incident commander (engineering manager as default)
    * Director and coordinator of overall response, ensuring that work is tracked
    * Acts as a sounding board for prioritization of efforts
    * Assists in data collection and troubleshooting efforts
* Stakeholders
    * A broad group of roles whose expectations of the incident response process require management
    * Receive information about the status of current incidents and updates on expectations set by the incident response process

### Responding team

* All responders who are hands-on and engaged to successfully manage an incident, technical or otherwise.
* This includes support and customer success if the interactions are bi-directional.

### Milestones

* Declare
    * Started: When the affected system began having problems.
    * Detected: When a monitoring system or human noticed that a system was having problems.
    * Acknowledged: When the person responsible for responding to incidents within the affected system acknowledged the monitoring system's alert.
* Triage
    * Investigating: When the first concrete step toward identifying a fix or resolving the problems with the affected system occurred.
    * Mitigating: When the system is no longer exhibiting problems to users.
* Resolve
    * Retrospective prep: Time to prepare and gather additional data about the incident.
    * Retrospective done: Retrospective document is complete, any additional follow on retrospectives or other meetings are done and any follow on items have been identified.

## Prerequisites
> note: for ease of use, all links created can be input into the link index at the bottom of this document and of the incident template document.

* Incident email distribution list (example: incident_updates@company.com)
    * To broadcast incident status updates to internal stakeholders. This list will receive high-level overviews of incidents, as well as updates to incident processes. Typically, this is a mix of leadership (customer facing and technical) and customer-facing teams. Product and engineering teams can be added if desired.
* Create a “[concerned_responders@company.com](mailto:concerned_responders@company.com)” email alias to collect feedback on the incident management process.
* Severity levels based on your organization’s specific business needs
    * This severity matrix should be a living document that grows as you learn more about responding to incidents in the context of your business.
    * In defining your highest severity, 10-20% more conservative than your customer agreed upon SLAs are a great starting point.
    * Update the definition of “severity” under the definitions section in this document with rules that line up with your businesses use cases as gathered above.
    * General rules seem to work better than specifics, as specific rules will require more maintenance over the long run.
* Service ownership document
    * This document outlines the owners of services and functionalities.
    * To get started, this can be as basic as a high-level architecture diagram with team owners overlaid.
    * Expect this document to evolve into something like a table with the following headers: Functionality, Service, Owning Team.
* A functional on-call schedule
* Monitoring that will trigger based on states that require immediate attention, often customer impacting
* An engineering leadership on-call schedule to enable escalations
* A basic status page capable of displaying public facing incident communications
* Copy the [incident template](https://github.com/better-incidents/foundations-of-incident-management/blob/main/docs/incident_template.md) into your wiki or company note taking system and create a template
    * Documentation for importing markdown documents:
        * [Gdocs template creation](https://support.google.com/a/users/answer/9308885?hl=en)
        * [Gdocs markdown import](https://support.google.com/docs/answer/12014036?hl=en#:~:text=You%20can%20use%20Markdown%20to,Bold)
        * [Confluence template creation](https://support.atlassian.com/confluence-cloud/docs/create-a-template/)
        * [Confluence markdown import](https://community.atlassian.com/t5/Confluence-questions/How-to-import-pages-with-markdown-format-into-Confluence/qaq-p/1886974)
        * Notion

<!-- Link Index -->

[wiki_incident_template_link]: https://example.com
[incident_oncall_rotation]: https://example.com
[concerned_responders_email]: mailto:concerned_responders@acme.com
[service_ownership_resource]: https://example.com
[wiki_incident_directory]: https://example.com
[general_incidents_chat_channel]: https://example.com
[incident_documentation#severity_matrix]: incident_doc#severity_matrix
[incident_distro_email]: example_incidident_distoro_email@exmple.com
[incident_documentation#retrospectives]: incident_doc#retrospectives