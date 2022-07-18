# CIT 470, Systems Security II
## Above-and-beyond 1
### Task
Complete an optional project that creatively goes "above and beyond" the tasks you and your partner(s) are working on in your team projects.

Students that achieve a passing grade with each of their team tasks and peer evaluations will pass the course with a C grade.
Above-and-beyond tasks are projects that individual students may accomplish individually
There are eight Above-and-beyond opportunities in this course.

### Tools
- Sign up for a free gns3.com account: [https://www.gns3.com/account/login](https://www.gns3.com/account/login)
- A desktop or laptop computer with at least 16GB RAM
- A Type-II Hypervisor, suitable to running the GNS3 VM that accompanies the GNS3 application:
  - Oracle VirtualBox
  - VMware Workstation or Fusion
- GNS3 software components:
  - The GNS3 application: [https://www.gns3.com/software/download] (https://www.gns3.com/software/download)
  - The GNS3 VM: [https://www.gns3.com/software/download-vm] (https://www.gns3.com/software/download-vm)

### Requirements
- Install the GNS3 VM, and verify that it has KVM support available.
- Install the GNS3 application, and configure it to use the GNS3 VM for appliance images.
- Create a working mock-up of your network diagram, including the following nodes:
  - Deploy a "NAT" cloud endpoint node as your **outside** security zone.
  - Deploy three "Ethernet Switch" nodes, with one of each as the central node of your **dmz**, **inside**, and **secure** zones.
  - Deploy an "Internet-facing" firewall node with three connections:
one to your *outside* NAT node, another to your **dmz** switch node, and the third to your **inside** switch node.
    - configure this firewall to automatically get a DHCP address from the **outside** "NAT" cloud,
but configure your selected static gateway IP addresses on its **dmz** and **inside** interfaces.
  - Deploy a "Secure-facing" firewall node with two connections, to your **inside** and **secure** switches.
    - configure your selected static gateway IP addresses on its **inside** and **secure** interfaces.
    - on the Internet-facing firewall, configure an additional static route to the secure zone via the secure-facing firewall.
  - Deploy two "VPCS" (virtual PC stub) endpoints, one each connected to the switches in your **dmz** and **secure** zones.
    - configure appropriate static IP addresses on each VPCS.
  - Download and deploy a "webterm" endpoint device, and connect it to your **inside** switch.
    - configure an appropriate static IP address on the webterm,
with a default route through the Internet-facing firewall
and an additional static route to the secure zone through the secure-facing firewall.
  - configure appropriate policy rules on each firewall, such that:
    - the endpoint devices in the **dmz**, **inside**, and **secure** zones can ping each other (using ICMP Ping protocol)
    - the endpoint devices in the **dmz** and **inside** zones can successfully ping Google's public DNS server 8.8.8.8,
and the webterm in the **inside** zone can access web sites such as www.google.com and www.bing.com
    - the endpoint device in the secure zone cannot ping or otherwise connect to any Internet host in the **outside** zone.

### Deliverable

### Scoring Rubric

### Hints
