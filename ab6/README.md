## Task: HIDS Sensor
Now that your team is working on (or has successfully deployed) a Network Intrustion Detection sensor,
deploy and test a Host-based Intrustion Detection System as an individual above-and-beyond task.

## Tools
Choose a HIDS platform.
- Recommended: deploy an [OSSEC](https://www.ossec.net/) HIDS server on a **secure** zone Linux VM.
- Other options:
  - use the [Wazuh](https://wazuh.com/) service already installed on your Security Onion VM.
  - deploy a standalone Wazuh HIDS server on one of your other **secure** zone Linux VMs.
  - (There are other no-cost HIDS solutions. If you know of one and want to try it, message your instructor and ask if you can implement it for this task.)

## Requirements
- Configure and activate a HIDS server.
- Deploy a corresponding HIDS agent on at least one of your team's Windows Server VMs.
- Deploy a corresponding HIDS agent on at least one of your team's Linuz Server VMs.
- Establish communication between your HIDS agents and your HIDS server. ("Register" your agents.)
- Find a way to test your HIDS setup.
  - Example: make a dangerous registry or configuration change on an agent-registered VM, something that the agent should detect.
Then verify that the agent sent an alert to the HIDS server.
  - Example: (NOT recommended!) Find a mild malware specimen that the HIDS agent will detect, download it to your agent-registered VM, and "detonate" it (that is, execute the malware program). Then verify that the agent sent an alert to the HIDS server.

## Deliverable
Upload an illustrated tutorial, in which you explain what you did and how you accomplished it.
- Your document should be clear enough that one of your peers would be able to follow your instructions and accomplish the same tasks.
- Identify any difficult or challenging parts of the project, and clearly explain how you diagnosed and overcame your obstacles.
- Include a few cropped screen captures where appropriate. Also upload your updated and annotated network diagram.

## Scoring Rubric
- If your tutorial satisfies every requirement outlined above, you will earn a passing score (one point).
- If your tutorial does not satisfy any one of the above requirements, you will earn no points. Your team must then address any deficiencies and re-upload corrected documents until you earn the passing score.

## Hints
- It may be difficult to actually coax your new HIDS system into actually generating an alert.
However, do your best in your tutorial document to demonstrate that you at least made a good-faith effort to do so,
without taking any "unreasonable" security risks.
