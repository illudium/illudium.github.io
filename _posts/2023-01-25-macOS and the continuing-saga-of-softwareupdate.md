## macOS and the continuing saga of softwareupdate (software update) being "frozen" or not working, no updates listed

There is a well-known issue with macOS in which a Mac does not show available software updates. This has been occurring since the time of macOS Big Sur - aka ["macOS '(this one) goes to' 11"](https://www.youtube.com/watch?v=KOO5S4vxi0o){:target="_blank" rel="noopener"}

---

### Investigating further
If you look at the running processes, you may see an existing ```softwareudpated``` process listed, which might have been active for some time.

Manually launching Software Update (in the GUI) or using the ```softwareudpate``` command, will simply sit without returning anything about available updates.

#### Remediation

To get past this, I have found the following helpful and the steps do not require a reboot:

Run the following via the Terminal (or remotely via ssh):
```sudo /bin/launchctl disable system/com.apple.softwareupdated```

Then wwait several seconds, and run:
```sudo /bin/launchctl enable system/com.apple.softwareupdated```

Wait several more seconds. Note, the following should be (technically spekaing) redundant and unnecessary, but think of it as one more "kick" to help get things working again:

```sudo /bin/launchctl kickstart -k system/com.apple.softwareupdated```

And - hopefully - you'll find the problem resolved, as I have so far.

#### Originally published by me, March 17th, 2022
