# SMBScan - Current Version 3.0.3

<pre>
 __      __        .__       .___         _________   _____ __________ 
/  \    /  \_____  |  |    __| _/____    /   _____/  /     \\______   \
\   \/\/   /\__  \ |  |   / __ |/  _ \   \_____  \  /  \ /  \|    |  _/
 \        /  / __ \|  |__/ /_/ (  <_> )  /        \/    Y    \    |   \
  \__/\  /  (____  /____/\____ |\____/  /_______  /\____|__  /______  /
       \/        \/           \/                \/         \/       \/ 
</pre>


Scans SMB for Vulnerabilities Assessment
<br />
<br />
Work in progress, looking to implement several things still.
Uses nmap but packages all the NSE scans in one script for quick assessment as well as enumerating shares/smb servers and banner grabbing.
Also does Enum4linux with -e flag and nbtscan with -n flag.

Please use responsibly and with permission only.  I do not condone unauthorized uses and will not be responsible for anything unethical commited with these.
<br />
<br />
Uses Nmap, Enum4linux, NBTSCAN, etc. in order to scan smb for vulnerabilities and enumerating shares and samba servers.  The script will check if you have these dependencies installed and offer to install them if you don't.
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
-sh or -sh='Share'            List and login to an SMB Share
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
-brute                        Brute force SMB
<br />
-i                            Do a full intensive scan of SMB on the machine
<br />
-v                            Verbose output
<br />
--update                      Updates WSMB
<br />
--version                     Displays current installed version and checkes for updates
<br />
<br />
# Usage Examples
<br />
<br />
It has the ability to check for ports 139,445 SMB.  You can search for all servers with these ports open by running:
<br />
<br />
EX: wsmb 192.168.1.* -qs
<br />
<br />
This does a quick scan in order to get an idea of every machine with ports 139,445 open on your subnet.  -s defaults to a full scan with hostname enumeration and -sb includes nmap banner grabbing as well.
<br />
<br />
Once you've decided on a target, you can run every smb nse script available on your system against the target with:
<br />
<br />
EX: wsmb 192.168.1.1
<br />
<br />
And if you'd like you can include enum4linux with -e and an NBTScan with -n.  An intensive scan can be run with -i, doing enum4linux, nbtscan, banner grabbing, and enumerating all samba shares (by checking if anon login is allowed) as well as running all NSE scripts against target.
<br />
<br />
EX: wsmb 192.168.1.1 -e -n (Runs NSE Scripts, enum4linux, and nbtscan)
<br />
<br />
EX: wsmb 192.168.1.1 -i (Does a full run SMB enumeration)
<br />
<br />
Everything you scan will be saved in a corresponding file with the scan name in a folder named (last 2 digits of IP)/hostname-SMBScan on your Desktop.
<br />
<br />
Several more features to come so a --update feature was added to automatically update your script from the github version.  Checks your current version against github version and if current version doesnt match, updates your file.

#Changelog
*3.0.3
<ul>
<li> Verbosity addition -vv</li>
</ul>

*3.0.2
<ul>
<li> Cleaned up dependency checks</li>
</ul>

*3.0.1
<ul>
<li> Folder naming fixes</li>
</ul>

*3.0
<ul>
<li> Added new intensive scan option (-i)</li>
<li> Added dependency checks, for best experience allows you to install all dependencies quickly</li>
<li> Removed constant Version check against the git, --update or --version must now be ran to check for and run updates.</li>
<li> When updating with --update you are now prompted before accepting the update</li>
<li> Minor Fixes</li>
</ul>

*2.0.2-2.0.3
<ul>
<li> Fixed help Menu</li>
<li> Minor Fixes</li>
</ul>

*2.0.1
<ul>
<li> Enhanced SMB Share login to accept a Share as an argument for an expedited login.  EX: wsmb 192.168.1.1 -sh="Admin"</li>
</ul>

*2.0.0
<ul>
<li> Complete restructure with functions to handle bulkwork. Further optimization planned to come.</li>
<li> Verbosity now works more effictively and as planned.  Continued plans to improve.</li>
<li> Minor bug fixes including SMB Brute force fix</li>
</ul>

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
<li> Added a verbosity level for more detailed output.  Plans to update the output significantly for detailed info.</li>
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
