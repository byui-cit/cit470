# CIT 470, Systems Security II
## Proxy servers

### Task
Work with your team to deploy proxy services in your inside zone that relay DNS and web protocols,
sufficient for your team's secure zone hosts to access the Internet and receive OS updates.

### Tools
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
  - Use a web browser, or curl or wget utility, to verify successful web traffic relay.
- Configure your secure VMs management-level web proxy settings to relay OS-updates through your web proxy.
  - On your Windows Server, use the netsh utility to configure the proxy used for Windows Updates.
  - On your Linux server, edit configuration files used by the package manager.
(This is probably **apt** for Debian/Ubuntu style Linux distributions,
or **dnf** for Red Hat style distributions.)

### Deliverable

### Scoring Rubric

### Hints
@@@ TBD
