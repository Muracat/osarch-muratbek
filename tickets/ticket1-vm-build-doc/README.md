# Ticket 1 — VM build document

## 1. What was asked

Aigerim said: "Hi, we have someone starting on Monday and he needs a test computer set up. Nothing special, just so he can try things without breaking anything. Can you write down how to do it so I can do the next one myself? Thanks"

## 2. What was actually needed

Aigerym needs a VM set up with recovery capabilities to safely work with a project that allows experimentation without consequences. Aigerim did not use technical terms, so there could be many ways to solve her problem. What does "nothing special" actually mean for a developer? Which operating systems does he need?

## 3. What I did
I wrote a document detailing the steps to resolve Aigerym's problem.

## 4. Evidence
 - [evidence/01-new-vm-wizard-1.png](evidence/01-new-vm-wizard-1.png) - the hypervisor's new-VM wizard with choices
 - [evidence/01-new-vm-wizard-2.png](evidence/01-new-vm-wizard-2.png) - the hypervisor's new-VM wizard with choices
 - [evidence/02-disk-settings.png](evidence/02-disk-settings.png) - disk size and type (thin / dynamically allocated)
 - [evidence/03-network-adapter.png](evidence/03-network-adapter.png) - the network mode of a guest
 - [evidence/04-guest-uname.txt](evidence/04-guest-uname.txt) - output of `uname -a` (and `lsb_release -a`) inside the Linux guest, with the command line
 - [evidence/05-ping-between-guests.txt](evidence/05-ping-between-guests.txt) - ping Linux to Windows and Windows to Linux, plus each guest to the internet, unedited output
 - [evidence/06-snapshot-list.png](evidence/06-snapshot-list.png) - the snapshot list with clean snapshot
 
## 5. What I would do differently

I would like to clarify for what purpose exactly does the new guy need this dev environment for. What is he planning to "break"? What is his requirements?
