# Ticket 1 — VM build document

## 1. What was asked

Aigerim said: "Hi, we have someone starting on Monday and he needs a test computer set up. Nothing special, just so he can try things without breaking anything. Can you write down how to do it so I can do the next one myself? Thanks"

## 2. What was actually needed

Aigerim's request has two deliverables: a safe test environment for the new starter (one he can break and get back quickly) and a document she can follow herself for the next person. "Test computer" for someone who will "try things" points to virtual machines with snapshots, not a spare physical PC: a VM can be reset in a minute and costs no hardware.

### What the request left out:
| Gap | Why it matters |
|---|---|
| Host resources: whose machine runs the VMs, how much RAM / CPU / free disk? | Decides how big the VMs can be and whether both can run at once. Windows 11 alone needs 4 GB RAM and 64 GB disk. |
| Which operating systems does he need? | "Nothing special" doesn't say Linux, Windows or both. |
| Network: should the VMs reach the internet? Each other? Must they stay off the office network? | Decides the VirtualBox network mode, and whether anything he breaks can reach company systems. |
| Licences: is there a Windows key for him, and for how long does he need it? | A real key costs money; the free evaluation expires after 90 days. |
| The reader: Aigerim is not technical. | The document has to say what to click and what she should see, explain the jargon, and cover what goes wrong. |
| Deadline: he starts on Monday. | The build must be done and tested before then, with time to fix problems. |

### Questions I would send Aigerim:

1. Which computer will he use, and roughly how much memory does it have (8 GB, 16 GB, more)?
2. Will he work on Windows, Linux, or both?
3. Should his test machines be able to reach the internet and/or the office network (shared drives, printers, internal sites)?
4. Do we have a Windows licence for him, or is a free 90-day trial OK?
5. How long does he need this: a few weeks of onboarding, or permanently?

### Assumptions I made (because the answers weren't available before Monday)

1. The host is a laptop like mine: ≈15 GB RAM, 16 logical CPUs (read from the VirtualBox wizard).
2. He needs both a Linux server (Ubuntu Server 26.04 LTS) and a Windows desktop (Windows 11 Enterprise), the two systems most company work touches.
3. The VMs need internet and each other, but must not appear on the office network → NAT Network.
4. No licence budget → Windows 11 Enterprise Evaluation (free, 90 days, then rebuild or buy a key).
5. He needs it for onboarding (weeks, not years), so a 90-day Windows is acceptable.

## 3. What I did
- Built both VMs in VirtualBox on one NAT Network, with a clean snapshot of each.
- Calculated the VM sizes from my host's resources (6 GB of 15 GB RAM, 3 of 16 CPUs with both running).
- Wrote BUILD.md: step-by-step build for Aigerim, a table of every non-default setting with the reason, a comparison of network modes, rollback instructions and a troubleshooting table.

## 4. Evidence
 - [evidence/01-new-vm-wizard-1.png](evidence/01-new-vm-wizard-1.png) - the hypervisor's new-VM wizard with choices
 - [evidence/01-new-vm-wizard-2.png](evidence/01-new-vm-wizard-2.png) - the hypervisor's new-VM wizard with choices
 - [evidence/02-disk-settings.png](evidence/02-disk-settings.png) - disk size and type (thin / dynamically allocated)
 - [evidence/03-network-adapter.png](evidence/03-network-adapter.png) - the network mode of a guest
 - [evidence/04-guest-uname.txt](evidence/04-guest-uname.txt) - output of `uname -a` (and `lsb_release -a`) inside the Linux guest, with the command line
 - [evidence/05-ping-between-guests.txt](evidence/05-ping-between-guests.txt) - ping Linux to Windows and Windows to Linux, plus each guest to the internet, unedited output
 - [evidence/06-snapshot-list.png](evidence/06-snapshot-list.png) - the snapshot list with clean snapshot
 
## 5. What I would do differently

I would send Aigerim the questions in section 2 before building, instead of building on assumptions. In particular: what he plans to "break" (OS settings? software installs? network experiments?) decides whether one VM is enough or he needs both, and whether the VMs must be cut off from the internet as well.
