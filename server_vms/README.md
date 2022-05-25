# CIT 470, Systems Security II
## Server VMs

Agree with your team partner(s) on a naming convention for your servers.
- All of your team's VM names should start with T##, where ## is your team's assigned number.
- you might choose a token that identifies a server's OS, such as:
  - "WS" or "Windows" for a Windows Server
  - "UL" or "Ubuntu" for an Ubuntu Linux server
- you might choose a token that identifies the zone in which the server resides, such as:
  - "D" or "dmz" for a server in the DMZ
  - "S" or "secure" for a server in the secure zone
- Examples (combining all of the above):
  - a Windows Server in Team 12's inside zone might be named something like:
    - T12-inside-windows
    - T12-WS-I
  depending on the team's chosen naming convention.
  - a CentOS Linux server in Team 11's DMZ earmarked for load balancing duty might be named something like:
    - T11-D-CL2
    - T11-centos-dmz-loadbal
  depending on the team's chosen naming convention.

Agree with your team partner(s) on a secure way to share service account passwords with each other.
For example, you might want to use a cloud-based password manager that only members of your team can access.
(KeePass might be a good option for this,
with a shared password database stored in a cloud storage service such as
Microsoft OneDrive or Google Drive,
and shared to all team members, so that all can access it with their own copy of KeePass software.)

In each of your zones (secure,inside,DMZ) deploy a Windows Server and a Linux server, for a total of six servers.
*(This is a good starting point, but you may need to deploy additional servers for future assignments)*

Choose an appropriate password for the Administrator or root account on each server.
(Of course, don't use a weak easily-guessable password like "password" or "123456."
On the other hand, do not use an overly complicated or lengthy random password either,
because sometimes you will not be able to merely copy/paste a password from your team's shared password manager,
but instead you will be forced to carefully type it successfully in order to log in or gain elevated privileges on a server.
Find an appropriate balance between security and convenience in your password selections.)
Create additional accounts capable of administrator/root privilege on each server:
one for each team member, and another for your instructor.
(You'll need to find a secure way to inform your instructor of that account's initial password.)
Make sure every team member can successfully log into *and* exercise administrator privilege on all six VMs.

Find the private network address ranges assigned to your team's zones,
and configure the virtual network interface of each VM with an appropriate static IP address.
(*None* of these six servers should be configured to obtain an address via DHCP.)
Verify that each pair of servers in each zone can ping each other.
(*Hint:* a Windows Server will not respond to ICMP echo request "pings" by default.
You will need to enable an inbound rule in Windows Defender Firewall with Advanced Security to let this happen.)

Make sure each server is renamed to match its VM name, according to your team's machine naming convention.
(By default, your Windows Servers are assigned a random hostname such as WIN-A1B2C3D4E5 when they are first deployed,
so you'll want to change that.)
