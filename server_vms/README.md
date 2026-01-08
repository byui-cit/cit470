## Task: Server VMs
Work with your team to deploy and apply an initial configuration to six virtual servers.

## Tools
<a href="/cit470/courseinfo/OpenShift" target="_blank" ref="noopener">CSE department OpenShift infrastructure</a>

## Requirements
Agree with your team partner(s) on a naming convention for your servers.
- All of your team's VM names should start with t##, where ## is your team's assigned number.
- you might choose a token that identifies a server's OS, such as:
  - "ws" or "windows" for a Windows Server
  - "ul" or "ubuntu" for an Ubuntu Linux server
- you might choose a token that identifies the zone in which the server resides, such as:
  - "d" or "dmz" for a server in the DMZ
  - "s" or "secure" for a server in the secure zone
- Examples (combining all of the above):
  - a Windows Server in Team 12's inside zone might be named something like:
    - t12-inside-windows
    - t12-ws-i
    - (depending on the team's chosen naming convention).
  - An AlmaLinux server in Team 11's DMZ earmarked for load balancing duty might be named something like:
    - t11-d-al2
    - t11-alma-dmz-loadbal
    - (depending on the team's chosen naming convention).

Agree with your team partner(s) on a secure way to share service account passwords with each other.
For example, you might want to use a cloud-based password manager that only members of your team can access.
(<a href="https://keepass.info/download.html" target="_blank" ref="noopener">KeePass</a> might be a good option for this,
with a shared password database stored in a cloud storage service such as
Microsoft OneDrive or Google Drive,
and shared to all team members, so that all can access it with their own copy of KeePass software.)

In each of your zones (secure,inside,DMZ) deploy a Windows Server and a Linux server, for a total of six servers.
*(This is a good starting point, but you may need to deploy additional servers in future assignments)*

Choose an appropriate password for the Administrator or root account on each server.
*(Of course, don't use a weak easily-guessable password like "password" or "123456."
On the other hand, do not use an overly complicated or lengthy random password either,
because sometimes you will not be able to merely copy/paste a password from your team's shared password manager,
but instead you will be forced to carefully type it successfully in order to log in or gain elevated privileges on a server.
Find an appropriate balance between security and convenience in your password selections.)*
Create additional accounts capable of administrator/root privilege on each server:
one for each team member, and another for your instructor.
(You'll need to find a secure way to inform your instructor of that account's initial password.)
Make sure every team member can successfully log into *and* exercise administrator privilege on all six VMs.

Find the private network address ranges assigned to your team's zones,
and configure the virtual network interface of each VM with an appropriate **static** IP address.
(*None* of these six servers should be configured to obtain an address via DHCP.)
Verify that each pair of servers in each zone can ping each other.
(*Hint:* a Windows Server will not respond to ICMP echo request "pings" by default.
You will need to enable an inbound rule in Windows Defender Firewall with Advanced Security to let this happen.)

Make sure each server is renamed to match its VM name, according to your team's machine naming convention.
(By default, your Windows Servers are assigned a random hostname such as WIN-A1B2C3D4E5 when they are first deployed,
so you'll want to change that.)

## Deliverable
Upload an illustrated tutorial, in which you explain what your team did and how you accomplished it.
- your document should be clear enough that one of your peers would be able to follow your instructions and accomplish the same tasks.
- identify any difficult or challenging parts of the project, and clearly explain how you diagnosed and overcame your obstacles.
- include a few cropped screen captures where appropriate.

## Scoring Rubric
- If your tutorial satisfies every requirement outlined above, you will earn a passing score (one point).
- If your tutorail does not satisfy any one of the above requirements, you will earn no points.
Your team must then address any deficiencies and re-upload corrected documents until you earn the passing score.

## Example
Here are some very detailed illustrated "how-to" tutorials that should help you create these servers in vSphere:
- <a href="https://byui-cit.atlassian.net/wiki/spaces/CDI/pages/24543233" target="_blank" ref="noopener">How to deploy an AlmaLinux OS server VM</a>
- <a href="https://byui-cit.atlassian.net/wiki/spaces/CDI/pages/24739841" target="_blank" ref="noopener">How to deploy an Ubuntu Linux server VM</a>
- <a href="https://byui-cit.atlassian.net/wiki/spaces/CDI/pages/24772609" target="_blank" ref="noopener">How to deploy a Windows Server 2022 VM</a>

Your team's delivered tutorial should be *much shorter* than these how-to articles! Nevertheless:
- It should show *evidence* that all of the task requirements are satisfied.
- A fellow student should be able to read, understand, and follow your tutorial to achieve the same results.
- Cite (or just link to) useful Internet articles your team found that helped you complete this task.
- Don't write too much content that just describes ordinary details.
Instead, spend more of your energy writing and illustrating content that shows specific troubles that you experienced,
and your explanations of how you figured out and solved those troubles.
