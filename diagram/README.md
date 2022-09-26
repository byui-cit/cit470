### Task
Create and maintain a professional-quality network diagram that documents your team's security architecture.

### Software Tools
*(Recommended)* Here are some links to web-based applications students have successfully used to create their diagrams:
- [Cacoo](https://cacoo.com/)
- [Lucidchart](https://www.lucidchart.com/pages)
- [diagrams.net](https://app.diagrams.net/)

*(Optional)* You may also install and use desktop workstation software to create a network diagram. Examples:
- Microsoft Visio. This is the premier diagramming tool used by industry network and security professionals.
It's a little challenging to learn, so Visio proficiency looks attractive on a job-seeker's résumé.
It is also expensive, but BYU-Idaho students may obtain a copy of Visio software at no cost:
  - visit [Microsoft Azure Dev Tools for Teaching](https://azureforeducation.microsoft.com/devtools),
  - sign in with BYU-Idaho credentials,
  - select "Software" from the menu at the left of the Azure Education web page,
  - select one of the available editions of Visio Professional,
  - click **[Download]** to download the installer and **[View Key]** to obtain your product license activation key.
- [yEd](https://www.yworks.com/products/yed) (free download)
- [Dia](https://wiki.gnome.org/Apps/Dia) (free download)
- [OmniGraffle](https://www.omnigroup.com/omnigraffle). (This tool is for MacOS users only, and is expensive, but has wide use among IT Professionals.)

*(Not Recommended)* It is possible to make network diagrams using general purpose drawing tools such as
Microsoft Paint, or Inkscape, or Adobe Illustrator, or GIMP, or the "Word Art" features in Microsoft Word/PowerPoint, or printing a Cisco Packet Tracer diagram.
Please don't use any of these for this task.

### Requirements
- Include four security zones in your network diagram:
  - **"secure"** (*highest trust* - sensitive assets will be deployed in this zone)
  - **"inside"** (*ordinary trust* - assets such as regular user's machines will be deployed here)
  - **"dmz"** (*semi-trusted* - assets that must be Internet-accessible will be deployed here)
  - **"outside"** (*untrusted* - alas, the rest of the Internet is not yours to create nor control)
- Specify two firewalls as perimeter devices between your zones:
  - an *Internet-facing* firewall that will serve as the default router to the outside zone from both dmz and inside.
  - a *secure-facing* firewall that will be the default router from the inside zone to the secure zone.
- Specify at least two computer "end points" in the dmz, two in the inside zone, and two in the secure zone.
Your firewalls will enforce network security policies for various endpoint machines, such as:
  - Internet-facing hosts in the DMZ for web, proxy, and load balancing services
  - Protected hosts in the secure zone for database and network monitoring services
  - Regular hosts in the inside zone for testing and operating the services deployed in the other zones
- *Leave room in your diagram to add some annotations later. In future assignments, you will annotate your diagram to include OSI-model layer information:*
  - *Layer 2 information: VLAN tags*
  - *Layer 3 information: IP addresses, subnet masks, and network identifiers*
  - *Layer 4 information: port numbers*
  - *Layer 7 information: application identifiers*

### Deliverable
Upload an image, in either PDF or PNG file format, of your completed diagram.

### Scores
- If your diagram satisfies every requirement outlined above, you will earn a passing score (one point).
- If your diagram does not satisfy any one of the above requirements, you will earn earn no points.
You must then address any deficiencies and re-upload corrected diagrams until you earn the passing score.

### Examples
Here are some example diagrams that were created using some of the tools mentioned above.

Example drawn using Cacoo:
![Cacoo example](CIT470-cacoo-x.png)

Example drawn using diagrams.net:
![diagrams.net example](CIT470-drawio-x.png)

Example drawn using Lucidchart:
![Lucidchart example](CIT470-lucid-x.png)

Example drawn using Microsoft Visio:
![Visio example](CIT470-visio-x.png)
