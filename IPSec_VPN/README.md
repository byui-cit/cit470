### Task (IPSec VPN)
Your instructor will specify another team in the class to work with for this milestone.

Configure a site-to-site VPN tunnel on your team's Internet-facing firewall,
which securely enables network traffic between your DMZ and the other team's DMZ.


### Tools
- Your team's Palo Alto firewall and DMZ VMs
- Another team's Palo Alto firewall and DMZ VMs

### Requirements
- Create a new user account on your team's DMZ Windows Server.
(The new account must belong to the "Remote Desktop Users" group.)
- Create a new user account on your team's DMZ Linux server.

Securely share the username/password credentials of these new accounts with the other team.

For each of the requirements below, application traffic between DMZs must traverse
a lan-to-lan (site-to-site) IPSec VPN tunnel.

- From their own DMZ Windows Server, students of the other team must be able to use
Microsoft Remote Desktop to log in and use the new account on your team's DMZ Windows Server.
- From your team's DMZ Windows Server, you must be able to use
Microsoft Remote Desktop to log in and use the new account provisioned by the other team on their DMZ Windows Server.
- From their own DMZ Linux server, students of the other team must be able to use SSH
to log in and use the new account on your team's DMZ Linux server.
- From your team's DMZ Linux server, you must be able to use SSH
to log in and use the new account provisioned by the other team on their DMZ Linux server.

### Deliverable
Upload an illustrated tutorial, in which you explain what your team did and how you accomplished it.
- Your document should be clear enough that one of your peers would be able to follow your instructions and accomplish the same tasks.
- Identify any difficult or challenging parts of the project, and clearly explain how you diagnosed and overcame your obstacles.
- Include a few cropped screen captures where appropriate. Also upload your updated and annotated network diagram.

### Scoring Rubric
- If your tutorial satisfies every requirement outlined above, you will earn a passing score (one point).
- If your tutorial does not satisfy any one of the above requirements, you will earn no points. Your team must then address any deficiencies and re-upload corrected documents until you earn the passing score.

### Hints
@@@ TBD
