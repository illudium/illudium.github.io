---
# title: "Managing Adobe updates remotely via Jamf or other MDM"
Original Publication Date: 2024-10-20
---

## Managing Adobe updates remotely via Jamf or other MDM

Adobe provides their Remote Update Manager tool, which [you can read more about from Adobe](https://helpx.adobe.com/enterprise/using/using-remote-update-manager.html)

There is an excellent script for using Adobe RUM via Jamf, from John Mahlman, here:
https://github.com/jmahlman/Mac-Admin-Scripts/blob/master/Adobe-RUMWithProgress-jamfhelper.sh

One problem you will encounter with RUM, is that it will download available updates but fail to apply them, when an Adobe app is still running.

To handle that gracefully, I suggest the following script snippet [(also listed here)](https://github.com/illudium/shell-scripts-for-Mac-mgmt/blob/main/quit_all_adobe_apps.sh), which will invoke AppleScript and ask the user quit all running Adobe apps, and prompt them to save any unsaved changes.

```shell
#!/bin/sh

#other code here

quit_all_adobe_apps ()
{
osascript <<EOF
tell application "System Events"
	set adobeApps to displayed name of (every process whose background only is false and (name starts with "Adobe" or name is "Distiller")) as list
end tell

repeat with appName in adobeApps
	set end of adobeApps to appName
end repeat

try
	if adobeApps is not {} then
		repeat with currentApp in adobeApps
			if application currentApp is running then
				try
					tell application currentApp to activate
					tell application currentApp to quit
				end try
			end if
		end repeat
	end if
end try
EOF
}

# other code here

quit_all_adobe_apps
```
