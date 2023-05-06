## New items on a fileserver (network fileshare) from one user are missing (don't show up) for other users:

A common occurrence with clients/users on Macs working with a fileserver (network shares)
is that when someone else adds new items (files, folders) to network (server-based) sharepoint/folder/drive, 
other Mac users don't see those new items, they appear to be missing or "hidden," but they're not.

(This is actually a longstanding issue with macOS and the Finder).

--

## An available workaround as remediation:

This is a long-standing issue with (shortcoming of the macOS Finder, in that it's not very good at picking up changes or auto-refreshing in response to underlying changes in a network-based volume. It can happen with OS X Server-based AFP, and various vendors' AFP or SMB server-based shares/network folders.
One thing we can easily do is create an AppleScript to prompt/prod the Finder to refresh. 
Save it as an application, store it somewhere safe from accidential deletion (eg: /Library/CompanySupport) and then add it (drag and drop) to the top of a Finder window. Users can click on it to cause a Finder refresh.
Optionally, you can add a dialog stating that a refresh is happening.

The AppleScript content is below:

```try
``` tell application "Finder" to update items of front window
```end try

And with a dialog:

```try
``` tell application "Finder" to update items of front window
``` display dialog "Refreshing the Finder" default button "OK" giving up after 1
```end try
