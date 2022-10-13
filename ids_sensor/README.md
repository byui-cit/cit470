## Task: IDS Sensor
- Configure a Network Intrusion Detection System (NIDS) sensor, managed from your secure zone, that monitors DMZ network traffic, and alerts when it notices potentially malicious traffic.

## Tools
- Recommended: deploy a <a href="https://securityonionsolutions.com/" target="_blank" ref="noopener">Security Onion</a> sensor VM with two virtual interfaces: an analyst's *management* interface in your **secure** zone, and a promiscuous *sensor* interface in your **dmz**.
  - Optional: not recommended, but if you prefer, you may also roll your own sensor, as follows:
deploy a new Linux or Windows Server in your **secure** zone,
add another virtual network interface in your **dmz** (intended to collect or *sniff* **dmz** network traffic as a *sensor*),
download, install, and configure <a href="https://suricata.io/" target="_blank" ref="noopener">Suricata</a> or <a href="https://www.snort.org/" target="_blank" ref="noopener">Snort</a>, and implement a NIDS ruleset from a reputable threat-intelligence source, such as <a href="https://rules.emergingthreats.net/open/" target="_blank" ref="noopener">Emerging Threats Open Rules</a>.

## Requirements
- Your team's NIDS sensor monitors all **dmz** network traffic
- Your team's NIDS sensor produces alerts when it detects potentially malicious **dmz** network traffic
- Your team has begun to *tune* your NIDS sensor, starting with the following modification:
  - The periodic "health check" connections from your load balancer to your web servers each produce "false positive" alerts.
Modify your ruleset so that your NIDS sensor does not alert when it detects these health check connections.

## Deliverable
Upload an illustrated tutorial, in which you explain what your team did and how you accomplished it.
- Your document should be clear enough that one of your peers would be able to follow your instructions and accomplish the same tasks.
- Identify any difficult or challenging parts of the project, and clearly explain how you diagnosed and overcame your obstacles.
- Include a few cropped screen captures where appropriate. Also upload your updated and annotated network diagram.

## Scoring Rubric
- If your tutorial satisfies every requirement outlined above, you will earn a passing score (one point).
- If your tutorial does not satisfy any one of the above requirements, you will earn no points. Your team must then address any deficiencies and re-upload corrected documents until you earn the passing score.

## Hints
These hints assume you will follow the recommendation to deploy a Security Onion VM.
- Spend some time studying the <a href="https://docs.securityonion.net/" target="_blank" ref="noopener">Security Onion documentation</a>.
Get acquainted with its architectures, its many components and its "containerized" organization.
  - Do NOT deploy a Security Onion with a minimal IMPORT architecture.
Although that's what the documentation's "First Time Users" section recommends,
that configuration is, unfortunately, NOT suitable for your sensor.
Instead, plan for an EVALUATION, or better yet, a STANDALONE architecture for your installation.
  - Heed the recommendations in the "Hardware Requirements" section.
Your sensor will need a lot more CPU cores, RAM, and storage space than any of your other servers.
If your selected architecture requires 4 CPU cores,
it's okay to configure it with five or six,
just to be safe.
If your selected architecture requires 16GB RAM,
it's okay to give it 17 or 18GB,
just to be safe.
(As for storage, the minimum recommended 200GB of thin-provisioned storage should
be plenty for this project.)
- Deploy your Security Onion VM using the Security Onion ISO image.
  - Annoyingly, if you make a configuration mistake during the installation,
you may need to reboot and start your installation over again.
So be careful to type your inputs carefully during the installation.
  - After installation is complete, follow the instructions found in the
documentation's "After Installation" section. In particular, practice using
the `sudo so-status` command to see how long it takes for your new sensor
to spin up all of its service processes.
  - It might be a good idea to manually use `so-allow` to specify
the IP address of your **secure** Windows Server or **secure** Linux server.
Then you can use a web browser on that server to interact with
your sensor's "Security Onion Console."
- The key NIDS software package in your sensor is <a href="https://suricata.io/" target="_blank" ref="noopener">Suricata</a>.
in the Security Onion documentation, find the "Network Visibility"
section and its "Suricata" subsection.
Just quickly skim through the suggestions you find there, to get a rough feel
for some of the things Suricata on Security Onion can do, and some of the
troubleshooting tips you might need to consult in case something doesn't work as expected.
  - You should not need to reconfigure Suricata; Security Onion's default configuration should work just fine.
- *The power and effectiveness of any Suricata IDS sensor lies in its ruleset*.
  - Go to <a href="https://suricata.readthedocs.io/" target="_blank" ref="noopener">Suricata's online documentation</a>,
find the "Suricata Rules" section and its "Rules Format" subsection,
and study it carefully to become acquainted with the manner in which a
Suricata-style or Snort-style "NIDS rule"
(commonly called a *signature*) is organized.
Try to get comfortable enough with the syntax that, when you are presented
with a new rule, you will be able to quickly distinguish its
action, header, and options.
  - Go back to the <a href="https://docs.securityonion.net/" target="_blank" ref="noopener">Security Onion documentation</a>,
find the "Tuning" section of the documentation,
and study its "Managing Rules," "Adding Local Rules," and "Managing Alerts" subsections.
  - Your Security Onion sensor will come preconfigured to download and use
the <a href="https://rules.emergingthreats.net/open/" target="_blank" ref="noopener">Emerging Threats Open</a> threat intelligence feed. 
  - In the "Adding Local Rules" subsection, find the example for adding a local
rule to the ruleset.
Do you recognize the action in that rule? *(Answer: it's an alert.)*
Do you recognize the header in that rule? *(Answer: it's "ip any any -> any any.")*
Do you recognize any options in that rule? *(Answer: there are five options: msg, content, classtype, sid, and rev.)*
  - Follow the instructions to try out that example local rule!
The last step is to use the CLI web client `curl` to invoke a "practice" attack from <a href="http://testmynids.org/" target="_blank" ref="noopener">testmynids.org</a>.
To see if it worked, switch to your Security Onion Console, select Alerts, and see if you notice an alert produced by this new rule.
(The text of the alert should match the text in the rule's `msg:` option.)
- To begin to tune your ruleset, look for a "false positive" alert in your Security Onion Console.
(A false positive is an alert that a rule author thought might be hostile,
but which you, as a security analyst, have determined to have alerted on normal or expected network traffic.)
  - Should you disable that rule on your Security Onion VM, by commenting out that rule in the `/opt/so/rules/nids/all.rules` file?
Or will the salt system overwrite your change next time it's activated?
  - Maybe you can add one or two local rules,
which are copies of the "false positive" rule except with careful changes to the action and header sections,
crafted to "pass" instead of "alert" on the traffic you know to be benign.
  - There's a short 15-minute video linked in the "Managing Alerts" subsection that may give more helpful tuning hints.
