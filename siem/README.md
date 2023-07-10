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
- One popular commercial SIEM software package is <a href="https://www.splunk.com/en_us/products/splunk-enterprise.html" target="_blank" ref="noopener">Splunk Enterprise</a>,
which you can install on either a Windows Server or a Linux Server.
  - If you choose to implement Splunk as your team's SIEM,
you should also implement <a href="https://www.splunk.com/en_us/download/universal-forwarder.html" target="_blank" ref="noopener">Splunk Universal Forwarder for Remote Data Collection</a>
as a "middleware" broker between your Splunk Enterprise server and the log/event data produced by your other various VMs.
  - Here's a simple and commonly used SIEM architecure:
    - After Splunk Enterprise is successfully installed and running on a secure-zone server,
configure it to _listen_ on port 9997/tcp for incoming security event data.
(You _can_ choose a different port, but 9997 is the default port for Splunk Universal Forwarder.)
    - Install Splunk Universal Forwarder on your other VMs.
    - Configure each Windows universal forwarder to _monitor_ Windows Events,
and configure each Linux universal forwarder to _monitor_ the `/var/log` directory.
    - Configure each forwarder to _send_ monitored data to the Splunk Enterprise server's IP address, port 9997.
    - You'll probably need new firewall rules that permit port 9997 traffic to reach the Splunk Enterprise server.
- One popular open-source SIEM software package is <a href="https://www.elastic.co/downloads/" target="_blank" ref="noopener">Elastic Stack Enterprise Search</a>.
  - If you choose to implement a new Elastic Stack instance,
you should download and integrate the core components of the Elastic "ELK" Stack (*ElasticSearch*, *Logstash*, and *Kibana*),
but you might find it helpful to integrate other data collectors into the stack, such as *Beats* or *Elastic Agent*.
  - A faster option might be to use and explore
the complete Elastic Stack docker instance that is provided and already configured
on your installed Security Onion sensor.
Study the <a href="https://docs.securityonion.net/" target="_blank" ref="noopener">documentation for Security Onion</a> if you want to pursue this choice.
  - You'll probably need new firewall rules that permit your ElasticSearch instance to receive log and event traffic from other VMs.
