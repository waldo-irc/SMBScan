# SMBScan - Current Version 1.0.62
Scans SMB for Vulnerabilities Assessment
<br />
<br />
Work in progress, looking to implement several things still.
Uses nmap but packages all the NSE scans in one script for quick assessment instead of having to pop each NSE one by one!
Also does Enum4linux with -e flag and nbtscan with -n flag.

Please use responsibly and with permission only.  I do not condone unauthorized uses and will not be responsible for anything unethical commited with these.
<br />
<br />
Uses Nmap, Enum4linux, NBTSCAN, etc. in order to scan smb for vulnerabilities and enumerating shares and samba servers.
<br />
<br />
It can scan a subrange since it just uses nmap for the heavy lifting.
<br />
<br />
Usage: wsmb <target> [options]
<br />
options:
<br />
-h, --help                    Show Brief Help
<br />
-l                            List SMB NSE Scripts
<br />
-n                            Include NBTScan
<br />
-e                            Include Enum4Linux Scan
<br />
-map                          Enumerate with smbmap
<br />
-sh                           List and login to an SMB Share
<br />
-s                            Run a full subnet SMB Scan without Banner Grabbing
<br />
-qs                           Run a quick SMB Scan
<br />
-sb                           Run a full subnet SMB Scan with Banner Grabbing (slow scan)
<br />
-c                            Run scan and empty directory
<br />
-cx                           Empty dir without scan
<br />
--update                      Updates WSMB
<br />
<br />
# Usage Examples
<br />
<br />
It has the ability to check for ports 139,445 SMB.  You can search for all servers with these ports open by running:
<br />
<br />
wsmb 192.168.1.* -qs
<br />
<br />
This does a quick scan in order to get an idea of every machine with ports 139,445 open on your subnet.  -s defaults to a full scan with hostname enumeration and -sb includes nmap banner grabbing as well.
<br />
<br />
Once you've decided on a target, you can run every smb nse script available on your system against the target with:
<br />
<br />
wsmb 192.168.1.1
<br />
<br />
And if you'd like you can include enum4linux with -e and an NBTScan with -n
<br />
<br />
Everything you scan will be saved in a corresponding file with the scan name in a folder named (last 2 digits of IP)/hostname-SMBScan on your Desktop.
<br />
<br />
Several more features to come so a --update feature was added to automatically update your script from the github version.  Checks your current version against github version and if current version doesnt match, updates your file.

#Changelog
** Plans to reduce output down to importance only to keep screen clear.  -v will show full output.

*1.0.62
<ul>
<li> New ASCII intro.</li>
</ul>

*1.0.61
<ul>
<li> Minor fixes.</li>
</ul>

*1.0.6
<ul>
<li> Added a verbosity level for more detailed output.  Plans to update thie output significantly for detailed info.</li>
</ul>

*1.0.51
<ul>
<li> Minor Bug Fixes</li>
</ul>

*1.0.5
<ul>
<li> SMB Brute Forcing Capabilities have been added using Kali built in acccheck</li>
</ul>

*1.0.4 
<ul>
<li>Added Automatic Version checking (updates are done manually in case you'd like to wait for whatever reason)</li>
<li>Fixed folder naming system for certain hosts</li>
<li>Now set to properly update Locate DB</li>
</ul>
