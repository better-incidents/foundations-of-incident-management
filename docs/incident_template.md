# [inc-YY-MM-DD-SEV-X] {functionality} is {state} for {audience}

## Incident Commander Checklist

### Phase 0: Triage

- [ ] Evaluate the issue and choose a severity based on the [severity matrix][incident_documentation]
<!-- TODO: Figure out how to link to an anchor or header in another document where the base link is not known -->
- [ ] Check if anyone else is actively engaged or has been paged
- [ ] Spend no more than a few minutes writing up a customer impact summary to communicate to engaging responders and stakeholders

### Phase 1: Declare

- [ ] If not yet engaged, page the owning team of the impacted service or functionality
- [ ] [Create a copy][wiki_incident_template] of this doc
    * Name the incident using the format: [inc-YY-MM-DD-SEV-X] {functionality} is {state} for {audience}
    * Move it [here][wiki_incident_directory]
- [ ] Create communication channels
    * Name a chat channel using the format: inc-YY-MM-DD-SEV-X-{functionality} is {state} for {audience}
    * Create a video bridge
    * Invite any relevant responders to these channels/calls and post the links to the public channel.
    * Add links for all communication channels to the Incident Status: Responder section of this document
- [ ] From the triage phase, fill out the initial customer impact summary in the Incident Status: Stakeholder section of this document
    * Using this copy as a foundation, draft an email to internal stakeholders and send it to the [incident distro][incident_distro_email]
- [ ] For SEV1 and SEV2 incidents, update the [customer status page][status_page] following our [guidelines][incident_documentation]
    * Add the link under Incident Status: Responder > Previous Communication below

### Phase 2: Investigate, Coordinate, and Communicate
> Note: The parenthesis format “( )” is to indicate that the step is recurring and response times are severity dependent. Severities map as follows: (SEV1/SEV2/SEV3)

>Example: During a SEV1, emails to the incident distro should be sent on a 30-minute cadence.

- [ ] Record any relevant technical information or events during incident triage in the Timeline section of this document (ongoing)
    * See the Timeline section of this document for examples of relevant entries
- [ ] Monitor the incident chat and the video bridge (ongoing)
    * Listen for indicators that understanding of the impact is changing; if the impact is greater in severity than initially thought, update the severity and communicate to the incident disto and chat channel
    * If the responder team is struggling to make progress and you have exhausted your available options, consider escalating to technical leadership to aid in engaging responders with fresh eyes and/or deeper expertise
- [ ] Ten minutes before the next step check in with responders and compose a status update
- [ ] Every (30m/1h/3hr) send the update to the [incident distro][incident_distro_email] list by replying to all on the initial email thread
    * Add the update to the Latest Communication section of this doc, post the update to the incident chat channel.
- [ ] Every (1h/3h/- ) update the status page
    * Add the public link to the Previous Communication section of this document as an item in the timeline

### Phase 3: Mitigate and Resolve
Once the following conditions are met, the incident can be resolved:

- [ ] The changes made to mitigate customer impact are durable and will last until a long-term solution can be designed and implemented
- [ ] As the incident commander, I have reviewed this document and signed off that the current state of the document is as accurate as is reasonable at the time of resolution (pay specific attention to the Timeline and Incident Data sections of this document)
- [ ] A 45-minute initial retrospective for all responders has been scheduled within 24 to 48 business hours of mitigation
- [ ] A final update has been sent to the [incident distro][incident_distro_email] list that includes the following:
    * Date/time of the retrospective
    * Status of the incident and list of customers who were impacted
    * A brief overview of what next steps are (if any)
    * Kudos for responding teams

## Incident Status: Stakeholder
All stakeholder- and customer-centric communications with timestamps are logged here.
<table>
  <tr>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td><strong>Incident commander name:</strong></td>
    <td>Example Smith</td>
  </tr>
  <tr>
    <td><strong>Responding team name(s):</strong></td>
    <td>Team example</td>
  </tr>
  <tr>
    <td><strong>Summary of customer impact: </strong></td>
    <td>
      This should be a non-technical description of what customers are
      experiencing. Example: As of (date/time) all customers are unable to log
      in to the application.
    </td>
  </tr>
</table>

### Latest Communication

**Example: Stakeholder Communication**

```
Subject: SEV1/SEV2/SEV3 Incident - {functionality} is {state} for {audience}

<Functionality> is currently experiencing a SEV1/SEV2/SEV3 incident. The required teams are being engaged and are actively triaging the issue.

Identified time: 23:xx est
Description of customer impact: Customers can not log in after clearing cookies
Quantity of customers impacted: Unknown/All/Some/Few
Known customers impacted:
* Customer 1
* Customer 2

Please see the incident document for additional details. For additional questions, respond to this email thread.

Expect an update on the status of this incident in (30 minutes | 1 hour | 3 hours) or sooner.

<Responder Name>
```

### Previous Communication (chronological order from most to least recent)
> All times are eastern time EST or EDT.

**Example: Stakeholder Email**

    yyyy-MM-dd HH:mm est

    <Functionality> is still experiencing a SEV1/SEV2/SEV3 incident. The issue is related to a failed deploy.

    Identified time: 23:xx est
    Description of customer impact:
    Quantity of customers impacted: Unknown/All/Some/Few
    Known customers impacted:
    * Customer 1
    * Customer 2

**Example: Status Page**

    yyyy-MM-dd HH:mm est
    https://status.acme.com/8675309

## Incident Status: Responder

<table>
  <tr>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Chat channel link</td>
    <td><a href="https://zoom.com/8675309">https://zoom.com/8675309</a></td>
  </tr>
  <tr>
    <td>Video bridge link</td>
    <td></td>
  </tr>
  <tr>
    <td>Status page link</td>
    <td></td>
  </tr>
  <tr>
    <td>Internal engineering ticket link(s)</td>
    <td></td>
  </tr>
  <tr>
    <td>Associated customer ticket link(s)</td>
    <td></td>
  </tr>
  <tr>
    <td>Incident summary</td>
    <td></td>
  </tr>
</table>

### Timeline

The timeline with events in chronological order from most to least recent should include any technical event (deploy, rollback, etc.), action taken (reaching out other teams or vendors, handing off a responsibility etc.), or discovery that could be relevant to the incident. Logs, chat messages, and screen grabs are valid for inclusion.

Example:

    yyyy-MM-dd HH:mm est - Deploy has been successfully rolled back by Jane Doe

### Incident Data
<table>
  <tr>
    <td><strong>Event</strong></td>
    <td><strong>DateTime</strong></td>
  </tr>
  <tr>
    <td>Impact start time</td>
    <td>yyyy-MM-dd HH:mm est</td>
  </tr>
  <tr>
    <td>Issue detection time</td>
    <td></td>
  </tr>
  <tr>
    <td>Investigation start time</td>
    <td></td>
  </tr>
  <tr>
    <td>Mitigation time</td>
    <td></td>
  </tr>
  <tr>
    <td>Resolution time</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <strong>Customer impact duration</strong>
      <strong>(Impact start time - mitigation time)</strong>
    </td>
    <td><strong>XXm</strong></td>
  </tr>
  <tr>
    <td>
      <strong>Response duration</strong>
      <strong>(Investigation start time - resolution time)</strong>
    </td>
    <td><strong>XXm</strong></td>
  </tr>
  <tr>
    <td>
      <strong>Total incident duration</strong>
      <strong>(Impact start time - resolution time)</strong>
    </td>
    <td><strong>XXm</strong></td>
  </tr>
</table>

## Retrospective

See the Incident Management Process [documentation][incident_documentation] for guidance on running a retrospective.

### Prompts


    What was the final assessment of customer impact?

    What went well?

    What could be improved?

    Where did we get lucky?

    What were we wrong about?

    Links to action items
    * https://ticketing_provider/com/8675309

<!-- Link Index -->

[wiki_incident_template]: https://example.com
[incident_oncall_rotation]: https://example.com
[concerned_responders_email]: mailto:concerned_responders@acme.com
[service_ownership_resource]: https://example.com
[wiki_incident_directory]: https://example.com
[general_incidents_chat_channel]: https://example.com
[incident_documentation#severity_matrix]: incident_doc#severity_matrix
[incident_distro_email]: example_incidident_distoro_email@exmple.com
[incident_documentation]: <link to your copy of the incident documentation>
[status_page]: https://your-status-page.com