# AzBluMon
Automate the deployment of Azure Monitor Diagnostic Settings for the integration with Blumira SIEM.

**This script assumes you are running this in Bash locally (with az cli installed) or in AZCLI within the Azure Portal, this will NOT work properly in ZSH**
**Make sure before running this you run chmod +x /path/to/file**

What's not working or needs changed:
Checks for unsupported resources, need to list out all of these and get case statements to get it working right.
