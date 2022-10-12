## Task: SNMP Network Monitor
Configure an SNMP poller, managed from your secure zone, that monitors your Internet-facing firewall's subinterfaces.
## Tools
- A VM in your team's **secure** zone.
- Your Internet-facing firewall.
- Your secure-facing firewall.

## Requirements
- Configure your Internet-facing firewall to accept SNMP poll requests from its secure-facing interface.
- Configure an SNMP poller on a VM in your **secure** zone, to collect bandwith-usage data from your Internet-facing firewall.
- Configure your secure-facing firewall to allow SNMP traffic *to and from* your poller and your Internet-facing firewall.
- Set up reporting and management for your SNMP poller
- To test your SNMP poller's reporting capability, produce high-bandwidth data transfers through your Inernet-facing firewall,
then produce a report from your poller that identifies the times during which the data transfer occurred.

## Deliverable
Upload an illustrated tutorial, in which you explain what your team did and how you accomplished it.
- Your document should be clear enough that one of your peers would be able to follow your instructions and accomplish the same tasks.
- Identify any difficult or challenging parts of the project, and clearly explain how you diagnosed and overcame your obstacles.
- Include a few cropped screen captures where appropriate. Also upload your updated and annotated network diagram.

## Scoring Rubric
- If your tutorial satisfies every requirement outlined above, you will earn a passing score (one point).
- If your tutorial does not satisfy any one of the above requirements, you will earn no points. Your team must then address any deficiencies and re-upload corrected documents until you earn the passing score.

## Hints
- By default, most firewalls communicate SNMP through a management interface.
However, your SNMP poller will be in your **secure** zone,
so you will need to change that default setting,
so that your Internet-facing firewall accepts SNMP poll requests through its secure-facing interface.
- There are many network monitoring software packages, available at no cost, that work nicely for this assignment.
  - A popular choice to install on a **secure** zone Windows Server is
<a href="https://www.paessler.com/prtg" target="_blank" rel="noopener">PRTG Network Monitor</a>,
a commercial product with a free trial option.
  - A couple of popular choices to install on a **secure** zone Linux Server are
<a href="https://www.zabbix.com/network_monitoring" target="_blank" rel="noopener">Zabbix</a> and 
<a href="https://www.cacti.net/" target="_blank" rel="noopener">Cacti</a>.
- There are lots of useful "bandwidth testing" web applications.
In general, these apps generate a large amount of discardable data,
to be downloaded to (and uploaded from) a web browser as fast as possible,
and then they measure how much bandwidth was used during those data transfers.
  - Some popular bandwitdh testers include <a href="https://speedof.me/" target="_blank" rel="noopener">SpeedOf.Me</a>,
<a href="https://www.bandwidthplace.com/" target="_blank" rel="noopener">Bandwidth Place</a>,
<a href="https://www.speedtest.net/" target="_blank" rel="noopener">Ookla Speedtest</a>, or
<a href="https://fiber.google.com/speedtest/" target="_blank" rel="noopener">Google Fiber Speed Test</a>.
  - Using any of these tools from a web browser in your **dmz** or **inside** zones
will temporarily produce a detectably large spike in bandwidth usage through your Internet-facing firewall.
  - Experiment! Most Internet service providers enforce their own data rate limits,
based on customer subscription plans and available infrastructure,
so results will certainly vary depending on your chosen bandwidth tester and its targeted servers.
Users commonly repeat tests, in order to observe consistency or variability among multiple tests,
or to compare tests performed at different times of day (such as during, and later after, customary business hours).
