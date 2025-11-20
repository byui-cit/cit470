## Task: Above-and-Beyond 5
Implement an **802.1x** "Remote-Access Dial-in User Service" (RADIUS) authenticator,
then configure your team's Remote Access VPN service to use that RADIUS server to authenticate remote access clients.

## Tools
- Your Internet-facing firewall
- Recommended:
<a href="https://freeradius.org/" target="_blank" ref="noopener">FreeRADIUS</a> software.
(Note: FreeRADIUS is already available in most Linux distributions' software repositories.
Use `apt search freeradius` to find it in a Debian-based distribution, or
`dnf search freeradius` to look for it in a Red Hat-based distribution.)
  - FreeRadius is quite simple to set up, but there are other no-cost Radius solutions out there.
If you find one that your team would rather try out, message your instructor and propose your alternative RADIUS software.

## Requirements

- Deploy FreeRADIUS on a Linux server in your team's **secure** zone.
  - implement local usernames and passwords, one each for you and your team-mate(s), as part of your FreeRADIUS configuration.
- Configure your secure-facing firewall to allow RADIUS protocol traffic *from* your Internet-facing firewall *toward* your RADIUS server.
(In other words, your Internet-facing firewall is your RADIUS client host.)
- Configure your Internet-facing firewall's Remote-Access VPN service to authenticate users using your new RADIUS server.
- Test it; verify that it works!

## Deliverable
Upload an illustrated tutorial, in which you explain what your team did and how you accomplished it.

- Your document should be clear enough that one of your peers would be able to follow your instructions and accomplish the same tasks.
- Identify any difficult or challenging parts of the project, and clearly explain how you diagnosed and overcame your obstacles.
- Include a few cropped screen captures where appropriate. Also upload your updated and annotated network diagram.

## Scoring Rubric
- If your tutorial satisfies every requirement outlined above, you will earn a passing score (one point).
- If your tutorial does not satisfy any one of the above requirements, you will earn no points. Your team must then address any deficiencies and re-upload corrected documents until you earn the passing score.

## Hints
- For this lab task, just keep your RADIUS configuration simple.
Let your local user database be a plaintext configuration file that contains usernames and passwords.
  - *(Note: in an enterprise deployment, a plaintext username/password data table would **not** be acceptable.
Competent IT security professionals would look for a way to encrypt the username/password configuration, rather than just leave it in plaintext.
In fact, most professionals would instead configure the RADIUS server to act as a proxy to some other secure authentication service,
such as a Microsoft Active Directory domain controller, or an LDAP authenticator, or a TACACS server.
That way there would be no need to store confidential username/password credentials on the RADIUS server itself.)*
- The current standard default ports for RADIUS protocol traffic are 1812/udp and 1813/udp.
However, you may find RADIUS implementations that use the older legacy ports 1645/udp and 1646/udp.
Make sure you know whether the RADIUS client on your firewall expects to use current or legacy ports for its RADIUS messages,
and that you configure your secure-facing firewall and your RADIUS server to use the expected port numbers.
- There is a `radius-test` command-line client you can use to test your RADIUS server; use it as a local troubleshooting tool.
- *Note for those familiar with AAA jargon:
In general, RADIUS servers don't differentiate between authentication ("AuthN") and authorization ("AuthZ").
As far as RADIUS is concerned, a successful username/password both authenticates and authorizes.
It's up to the RADIUS **client** (in this case, the Internet-facing firewall)
to determine whether a properly authenticated user is authorized to use a service (in this case, the Remote-Access VPN service).*
