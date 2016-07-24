# SMBScan
Scans SMB for Vulnerabilities Assessment

Work in progress, looking to implement several things still
Uses nmap but packages all the NSE scans in one script for quick assessment instead of having to pop each NSE one by one!
Also does Enum4linux with -e flag and nbtscan with -n flag.

Uses Nmap, Enum4linux, NBTSCAN, etc. in order to scan smb for vulnerabilities and enumerating shares and samba servers.

It can scan a subrange since it just uses nmap for the heavy lifting.

if [ -z "$1" ]; then
[*] SMB Nmap NSE Scanner
[*] Runs all available SMB NSE Scripts gainst victim target
 Usage: wsmb <target> [options]
options:"
-h, --help                    Show Brief Help
-l                            List SMB NSE Scripts
-n                            Include NBTScan
-e                            Include Enum4Linux Scan
-map                          Enumerate with smbmap
-sh                           List and login to an SMB Share
-s                            Run a full subnet SMB Scan without Banner Grabbing
-qs                           Run a quick SMB Scan
-sb                           Run a full subnet SMB Scan with Banner Grabbing (slow scan)
-c                            Run scan and empty directory
-cx                           Empty dir without scan
--update                      Updates WSMB

Current Version 1.0.3

# Usage Examples
It has the ability to check for ports 139,445 SMB.  You can search for all servers with these ports open by running:

wsmb 192.168.1.* -qs

This does a quick scan in order to get an idea of every machine with ports 139,445 open on your subnet.  -s defaults to a full scan with hostname enumeration and -sb includes nmap banner grabbing as well.

Once you've decided on a target, you can run every smb nse script available on your system against the target with:

wsmb 192.168.1.1

And if you'd like you can include enum4linux with -e and an NBTScan with -n

Everything you scan will be saved in a corresponding file with the scan name in a folder named (last 2 digits of IP)/hostname-SMBScan on your Desktop.

Several more features to come so a --update feature was added to automatically update your script from the github version.  Checks your current version against github version and if current version doesnt match, updates your file.
