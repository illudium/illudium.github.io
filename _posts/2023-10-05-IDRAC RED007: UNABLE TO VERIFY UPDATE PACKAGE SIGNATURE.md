## IDRAC RED007: UNABLE TO VERIFY UPDATE PACKAGE SIGNATURE

Dell servers provide an iDRAC ("Integrated Dell Remote Access Controller") card for remote management of the unit. Note that this feature is a default (with some limited functionality in the "express" version) in Dell's most entry-level tower server options.

There are a number of options for managing updates for Dell servers, including direct access to an iDRAC card, which is configured with a specifed network configuration during initial setup of a/the server in question. Of course, please observe standard best-practices and never provide public accessibility to any such device, keep it behind your perimeter firewall where it (the iDRAC interface) can only be accessed via VPN.
Once configured the iDRAC card is readily accessible at its assigned IP address, via a web-browser.

While there may be a tendency to "set it and forget it" with regards to something like this, there is an expectation to keep the iDRAC updated, and generally within a certain range (for reasons of compatibility if not official support) of associated system BIOS versions.
If you are tasked with maintaining a Dell server that's fallen behind in terms of updates, you can encounter an error when attempting to update an iDRAC when jumping up too many versions:

idrac RED007: Unable to verify Update Package signature

### Remediation

This is most probably due to the existing iDRAC setup lacking required information about newer security (certificate) information for the much newer update installer.

**A confirmed fix** is to apply earlier updates to/for the iDRAC in a more step-wise manner:
For example, if the card is listed at version 2.3x.(etc), apply the update to 2.40.40.40 then 2.5x, etc. up the latest update. It is often possible to skip one version, but as always, proceed with due care & caution.

#### Originally published by me, January 29, 2019
