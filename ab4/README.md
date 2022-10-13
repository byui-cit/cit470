## Task: Above-and-beyond 4
Deploy an extra proxy server, using a different technology than you used for your team Proxy Server task.
- For example, if your team deployed *Acrylic* and *Privoxy* on a Windows Server,
redo that milestone, but instead deploy *unbound* and *squid* on a Linux server.

## Tools
CIT VMware infrastructure

## Requirements
If necessary, prepare (create or clone) an additional VM to run your new proxy services.

After you deploy your new proxy services:
- Reconfigure one of your secure VMs' network interfaces to use your new DNS proxy as its primary DNS server.
  - Use the nslookup utility to verify successful DNS resolution.
- Reconfigure one of your secure VMs' proxy settings to relay web traffic through your new web proxy.
  - Use a web browser, or command-line utilities such as curl or wget, to verify successful web traffic relay.
- Reconfigure one of your secure VMs management-level web proxy settings to relay OS-updates through your web proxy.
  - Verify that you can get updates through yur new web proxy.

## Deliverable
Upload an illustrated tutorial, in which you explain what you did and how you accomplished it.
- Your document should be clear enough that one of your peers would be able to follow your instructions and accomplish the same tasks.
- Identify any difficult or challenging parts of the project, and clearly explain how you diagnosed and overcame your obstacles.
- Include a few cropped screen captures where appropriate. Also upload your updated and annotated network diagram.

## Scoring Rubric
- If your tutorial satisfies every requirement outlined above, you will earn a passing score (one point).
- If your tutorial does not satisfy any one of the above requirements, you will earn no points. Your team must then address any deficiencies and re-upload corrected documents until you earn the passing score.

## Hints
@@@ [Hints will be added by the Course Lead]
