# CIT 470
## Systems Security II

Diagram

### Task:
Create and maintain a professional-quality network diagram that documents your team's security architecture.

### Software Tools:
*(Recommended)* Here are some links to web-based applications students have successfully used to create their diagrams:
- [Cacoo](https://cacoo.com/)
- [Lucidchart](https://www.lucidchart.com/pages)
- [app.diagrams.net](https://app.diagrams.net/)

*(Optional)* You may also use workstation software to create a network diagram. Examples:
- Microsoft Visio. This is the premier tool used in industry by network and security professionals. To obtain copy of Visio software at no cost, BYU-Idaho students may:
- - visit [Microsoft Azure Dev Tools for Teaching](https://azureforeducation.microsoft.com/devtools),
- - sign in with BYU-Idaho credentials,
- - select "Software" from the menu at the left of the Azure Education web page,
- - select one of the available editions of Visio Professional,
- - click **Download** to download the installer and **View Key** to obtain your product license activation key.
- [yEd](https://www.yworks.com/products/yed) (free download)
- [Dia](https://wiki.gnome.org/Apps/Dia) (free download)
- [OmniGraffle](https://www.omnigroup.com/omnigraffle). (This tool is for MacOS users only, and is pretty expensive, but has wide use among IT Professionals.)

*(Not Recommended)* It is possible to use general purpose drawing tools such as
Microsoft Paint, or Inkscape, or Adobe Illustrator, or GIMP, or the "Word Art" features in Microsoft Word/PowerPoint, or Cisco Packet Tracer.
Please don't use these for this task.

### Requirements:
- Include four security zones in your network diagram:
- - **"secure"** (*highest trust* - sensitive assets will be deployed in this zone)
- - **"inside"** (*ordinary trust* - assets such as regular user's machines will be deployed here)
- - **"dmz"** (*semi-trusted* - assets that must be Internet-accessible will be deployed here)
- - **"outside"** (*untrusted* - alas, the rest of the Internet is not yours to create nor control)
- Specify two firewalls as perimeter devices between your zones:
- - an *Internet-facing* firewall that will serve as the default router to the outside zone.
- - a *secure-facing* firewall that will be the default router from the inside zone to the secure zone.
- Specify at least two computer "end points" in the dmz, two in the inside zone, and two in the secure zone. Your firewalls will enforce network security policies for various endpoint machines, such as:
- - Internet-facing hosts in the DMZ for web, proxy, and load balancing services
- - Protected hosts in the secure zone for database and network monitoring services
- - Regular hosts in the inside zone for testing and operating the services deployed in the other zones
- *In future assignments, you will annotate your diagram to include OSI-model layer information:*
- - *Layer 2 information: VLAN tags*
- - *Layer 3 information: IP addresses, subnet masks, and network identifiers*
- - *Layer 4 information: port numbers*
- - *Layer 7 information: application identifiers*

### Examples:
Here are some example diagrams created using the tools mentioned above.
# TBD
