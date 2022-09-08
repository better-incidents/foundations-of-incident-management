# Incident Response Process

This is our process for responding to incidents. Incident managers and responders use this process to declare, investigate, communicate about, and resolve incidents regardless of their severity.
## Declaration

Even if you aren’t certain that what’s occurring is actually an incident just yet or it’s a transient bug that only a few customers are experiencing, it’s best to err on the side of caution and declare an incident. Because mitigation is your first priority during an incident, the objective of the declaration phase is to set your team up for efficient and collaborative problem solving and streamlined communication.

When you need to declare an incident, follow these steps in order:

1. Check to see if some already declared the incident. Join their chat channel if they have.
2. Copy and use the [incident manager document](https://example.com) as the incident is mitigated.
3. Create a dedicated incident channel. Use the format `inc-dd-mm-yy-functionality-state-audience`
    ```
    inc-05-09-22-logging-in-is-broken-for-all-users
    ```



4. Post a short summary of the incident that is occurring and pin the message to the channel.

> Example \
> [inc-YY-MM-DD-SEV-X] {functionality} is {state} for {audience} \
>Impact summary: Customer support has received several tickets from customers complaining that they’re unable to log in. I’m also unable to log in to my sandbox account.



5. Notify the team that owns the impacted functionality. For most incidents, this can be via paging or a team chat channel notification, but **high severity incidents should always default to paging.**
    * In the notification, link to the channel that was created and include all pertinent information.
    * If you’re not sure which team owns the broken functionality, please refer to our [ownership database.](https://example.com)
6. Notify the #new-incidents channel about the newly declared incident.

> Example \
> I’ve declared an incident about customers unable to log in based on the reports customer support has received. The dedicated channel for the incident is #inc-05-09-22-logging-in-is-broken-for-all-users. The team that is currently responding is the Core Services team.



7. Create a video bridge and post it in the dedicated incident channel.

> Example \
> I’ve created a video bridge for this incident, if you’re responding to this incident, please join us in here: {link}


# Respond (Investigate, Coordinate, and Communicate)

**This phase of the incident is a recursive operation; it’s not linear.** The single most important thing is to mitigate impact and restore service to impacted customers. Apply durable changes later.

* **Take detailed notes in the incident manager document.** No action or discovery is too small to note. Write down current hypotheses, link to dashboards that have evidence, add relevant customer reports, etc.

Example

_9:34am - Emily found a metric for failing requests to a 3rd party that coincides with the reports our customers are telling us. Current hypothesis is that our logging in functionality has a single point of failure with the 3rd party.



* **Track potential Milestones **to help guide the communication and the future retrospective.

    Example
    10:42am - Possibly identified: Bad deploy causing logging in issues



* **Every 30 minutes** communicate the current status of the incident to internal stakeholders in plain english.
    * Post to the #new-incidents channel and the [new-incidents-grp@example.com](mailto:new-incidents-grp@example.com) email group.
    * Add the update to the Latest Communication section of the incident document as an item in the timeline

Example

```
UPDATE: {functionality} is {state} for {audience} is still experiencing a SEV1/SEV2/SEV3 incident.

The team is {milestone} the (issue).

A non-technical, realistic but confidence-inspiring description of the state of incidentNo additional resources are required at this time.

Please see the [incident document](http://www.google.com) for details.

Expect an update on the status of this incident in 30 minutes or sooner.

Responder Name>
```


* **Communicate with customers** and notify them of the scope of impact, workaround solutions (if available), and when to expect the next update.


Example “investigating” messaging
```
Our monitoring systems have detected a potential issue with requests to our API. Our engineering team has been alerted and is actively investigating. We will provide an update in 1 hour or as soon as more information is available.
```

Example “update” messaging
```
We continue to investigate an issue where requests to our API are returning an error. Customers may intermittently receive 500 internal server errors from all endpoints. We expect to provide another update in 1 hour or as soon as more information is available.
```
Example “resolved” messaging

```
All endpoints were degraded for 15 minutes between xx:xx am and xx:xx am Eastern Time on xx/xx/20xx. During this period, customers may have.
```


* **Calibrate the team toward mitigation**.
    * Watch for indicators that responders are stuck (they show signs of cognitive tunneling or tell you directly they feel stumped).
    * Intervene as necessary by introducing new subject matter experts, assigning quests with clear time limits to evaluate hypotheses, and asking directly if they’re seeing the big picture.
* **Escalate when it’s clear you need more assistance.**
    * Watch for indicators the team needs additional access or information to progress toward mitigation and proceed with escalations. Look for:
        * Limited knowledge about the impacted service
        * Access restrictions blocking the investigation
        * Missing historical context about how systems or tools work together
* **Redirect or deflect disruptions.**
    * Guard for distractions to maintain responder focus and ensure continuity of coverage. These might include:
        * Questions from non-responders that can be addressed through planned comms updates or after resolution
        * The responding team’s personal needs, like family responsibilities, hunger, etc.
        * Emotional spikes, such as frustration or fatigue
    * Should these disruptions arise, prioritize the care of your responders. Assign new responders and encourage breaks.


## Mitigation

An incident is mitigated when customers are no longer feeling its impact but only resolved when a durable resolution is in place. After mitigation, the  incident manager will drive the incident to resolution by working jointly with the responsible team to plan durable solutions. Notably, the action taken to mitigate an incident _can_ be durable enough for it to also be considered resolved.



* **Post a message** to the #new-incidents channel to notify internal stakeholders that the impact from the incident should no longer be occurring in plain english.

> Example

> We’ve applied a patch that should allow customers to login again. If customers are still unable to login, please notify the #inc-05-09-22-logging-in-is-broken-for-all-users channel. The team will be performing a retrospective on the incident and we’ll provide more information about the contributing factors soon. Thanks!



* Email [new-incidents-grp@example.com](mailto:new-incidents-grp@example.com) after the incident has been mitigated and confirmed.

Example

```
Mitigated: SEV1/SEV2/SEV3 {functionality} is {state} for {audience} is mitigated.

Describe how things are being leftImpact has been mitigated for all customers. The status page has been updated with a resolved status.
All adversely impacted customers have an in-app notification to communicate the extent of the impact they experienced and have had an email sent to their CSM.
A retrospective has been scheduled for {date}, please respond to this email if you would like more details.
A special thanks to all the responders of this incident including team and the customer support team, who really helped us resolve this issue.

Please see the incident document for details.
```


* **Communicate with customers** and notify them that impact is mitigated.
* **Schedule a prompt retrospective **with responders. For high severity incidents, consider paving calendars the next working day. For lower severity incidents, a 1- to 2-day gap between mitigating and retrospective is acceptable. Any gap longer than a week is <span style="text-decoration:underline;">unacceptable</span>.
* **Link the completed incident document** that you were filling in during the incident to the dedicated incident channel.


## Durable Resolution

Remember, the action taken to mitigate an incident _can_ be durable enough for it to also be considered resolved. If it’s not, continue following the process below until a durable solution is in place.

* **Audit for durability.** Potentially non-durable mitigation strategies include:
    * Cronjobs to restart pods every 15 minutes
    * Turning off caching because the caching layer is failing
    * Manual changes made to infrastructure that are not in the infrastructure-as-code repository
    * Code hotfixes that did not have test coverage added
* **Create tickets** and describe what work needs to be done to resolve the incident
* **Decide upon the implementation timeline (now or tomorrow).** Consider whether:
    * The mitigation is durable enough to persist until the next working day.
    * You’ll be easily notified by automated alerting if the mitigation somehow breaks.
    * Implementing a durable solution immediately creates unnecessary risks that could trigger another incident.
* **Mark the incident as resolved** when all tickets to implement a durable solution are complete.
