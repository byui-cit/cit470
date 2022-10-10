## Task: SIEM
- Configure a log manager or SIEM to receive and process application logs and events.

## Tools
- A VM in your team's **secure** zone, running a SIEM (log management) software package.

## Requirements
- Configure your team's SIEM or log manager to receive and collect event data and/or event logs.
- Configure your team's firewalls to allow event and logging traffic to reach the SIEM server in the **secure** zone.
- Configure agents and/or event loggers on other VMs in your **dmz**, **inside**, and **secure** zones
to deliver logs to your SIEM server.
- After your SIEM server has collected and processed some events,
figure out how to search or query the collected logs to look for interesting events.

## Deliverable
Upload an illustrated tutorial, in which you explain what your team did and how you accomplished it.
- Your document should be clear enough that one of your peers would be able to follow your instructions and accomplish the same tasks.
- Identify any difficult or challenging parts of the project, and clearly explain how you diagnosed and overcame your obstacles.
- Include a few cropped screen captures where appropriate. Also upload your updated and annotated network diagram.

## Scoring Rubric
- If your tutorial satisfies every requirement outlined above, you will earn a passing score (one point).
- If your tutorial does not satisfy any one of the above requirements, you will earn no points. Your team must then address any deficiencies and re-upload corrected documents until you earn the passing score.

## Hints
- One popular open-source SIEM software package is [Elastic Stack Enterprise Search](https://www.elastic.co/downloads/).
  - If you choose to implement a new Elastic Stack instance,
you should download and integrate the core components of the Elastic "ELK" Stack (*ElasticSearch*, *Logstash*, and *Kibana*),
but you might find it helpful to integrate other data collectors into the stack, such as *Beats* or *Elastic Agent*.
  - A faster option might be to use and explore
the complete Elastic Stack docker instance that is provided and already configured
on your installed Security Onion sensor.
Study the [documentaition for Security Onion](https://docs.securityonion.net/) if you want to pursue this choice.
- One popular commercial SIEM software package is [Splunk Enterprise](https://www.splunk.com/en_us/products/splunk-enterprise.html),
which you can install on either a Windows Server or a Linux Server.
  - If you choose to implement Splunk as your team's SIEM,
you should also implement [Splunk Universal Forwarder for Remote Data Collection](https://www.splunk.com/en_us/download/universal-forwarder.html)
as a "middleware" broker between your Splunk Enterprise server and the log/event data sent by your other various VMs.
