## Task: Proxy servers
Work with your team to deploy proxy services in your inside zone that relay DNS and web protocols,
sufficient for your team's secure zone hosts to access the Internet and receive OS updates.

## Tools
The VMs you deployed to your inside and secure zones.

### Requirements
- Deploy a DNS proxy service.
  - recommended: Acrylic DNS Proxy on Windows Server
  - other good options: unbound or dnsmasq on Linux server.
- Deploy a Web proxy service.
  - recommended: Squid proxy on Linux server.
  - other good options: Privoxy or TinyProxy on Windows Server.
- Configure your secure VMs' network interfaces to use your DNS proxy as their primary DNS server.
  - Use the nslookup utility to verify successful DNS resolution.
- Configure your secure VMs proxy settings to manually relay web traffic through your web proxy.
  - Use a web browser, or command-line utilities such as curl or wget, to verify successful web traffic relay.
- Configure your secure VMs management-level web proxy settings to relay OS-updates through your web proxy.
  - On your Windows Server, use the netsh utility to configure the proxy used for Windows Updates.
  - On your Linux server, edit the configuration files used by the package manager.
(The manager is probably **apt** for Debian/Ubuntu style Linux distributions,
or **dnf** for Red Hat style distributions.)

### Deliverable
Upload an illustrated tutorial, in which you explain what your team did and how you accomplished it.
- Your document should be clear enough that one of your peers would be able to follow your instructions and accomplish the same tasks.
- Identify any difficult or challenging parts of the project, and clearly explain how you diagnosed and overcame your obstacles.
- Include a few cropped screen captures where appropriate. Also upload your updated and annotated network diagram.

### Scoring Rubric
- If your tutorial satisfies every requirement outlined above, you will earn a passing score (one point).
- If your tutorial does not satisfy any one of the above requirements, you will earn no points.
Your team must then address any deficiencies and re-upload corrected documents until you earn the passing score.

### Hints
@@@ [Hints will be added by the Course Lead]
