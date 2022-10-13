## Task: Above-and-beyond 5
Successfully deploy some other multiple-tier web application of your choice across your security zones.

## Tools
- Use either MariaDB or MySQL as the back-end database. Very likely, this will be easy to install using your Linux distribution's package manager.
- Use either Apache HTTP Server or nginx as your web server. Very likely, these will be easy to install using your Linux distribution's package manager.
- A multiple-tier web application of your choice

## Requirements
Phase I:

- Do a search for a multiple-tier web application that you are interested in learning about and then download the application package.
- Install your database server on your secure Linux host.
- Find, read, and follow your multiple-tier web application installation instructions. (Those instructions anticipate that the database and web servers reside on the same machine, so be careful to adjust them so that you implement your tiered app archecture instead.)
- You'll certainly need to configure new firewall policies on your secure-facing firewall to allow the dmz web middleware to communicate with the secure database service.
- Notice that there are some additional pre-requisites that aren't listed above, such as a PHP engine, that you may need to find and install.
- For troubleshooting, it may be helpful to install a database client on your dmz web host, and use that to test connectivity through the secure-facing firewall to the secure database host.
- After you finish installing your multiple-tier web application and have set up the app's administrator account, you should be ready to make the app accessible to clients out on the outside (untrusted) Internet zone.
- Just in case, before you allow untrusted clients to connect, please install a copy of the University's managed security sensor software on your dmz web host.
- Configure your Internet-facing firewall with static NAT (IP address translation) and security policies (access rules) that allow untrusted Internet clients connect to your web application via (unencrypted) HTTP protocol.
- Verify that it works by asking and answering a question; this will begin to populate your database with application data.

Phase II:

- Clone your web server. 
- Configure this second instance of your web server with its own fixed IP address in the same subnet as your original web server. 
- If necessary, re-install the University's security sensor software on the clone. 
- Change your Internet-facing firewall's NAT configuration to direct outside clients to the clone, and verify that the web app still works correctly with this new web server.
- Deploy a new load balancing service in the dmz, also with its own fixed IP address in the same subnet as your web servers. 
- Configure the load balancer to be able to direct clients' Question2Answer web requests to whichever of the two webservers is running and not down.
- Change your Internet-facing firewall's NAT configuration to direct outside clients to the load balancer. 
- Verify that your multiple-tier web application still works correctly when the original server is running but the clone is stopped, when the clone is running and the original is stopped, and when both web servers are running.

## Deliverable
Upload an illustrated tutorial, in which you explain what your team did and how you accomplished it.

- Your document should be clear enough that one of your peers would be able to follow your instructions and accomplish the same tasks.
- Identify any difficult or challenging parts of the project, and clearly explain how you diagnosed and overcame your obstacles.
- Include a few cropped screen captures where appropriate. Also upload your updated and annotated network diagram.

## Scoring Rubric
- If your tutorial satisfies every requirement outlined above, you will earn a passing score (one point).
- If your tutorial does not satisfy any one of the above requirements, you will earn no points. Your team must then address any deficiencies and re-upload corrected documents until you earn the passing score.
