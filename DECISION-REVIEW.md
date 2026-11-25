# A+ Core 2: decision and troubleshooting review

## Start with the support contract

Before choosing a tool, establish the affected user, device, application, impact, recent change and permission to investigate. Record what works as carefully as what fails. A single user's sign-in problem, a machine-wide startup failure and a shared service outage are different scopes.

Use this decision chain:

**Confirm scope → collect relevant evidence → form a testable explanation → choose the least disruptive authorized test → evaluate the result → repair with rollback available → verify the user's task → document.**

Do not confuse a proposed cause with a proven cause. If the evidence points to a security incident or a failing disk, the next step may be escalation and preservation rather than an ordinary software repair.

## 1. Operating system and deployment choices

| Decision | Evidence to obtain | Boundary that matters |
|---|---|---|
| Upgrade or clean installation | Supported source/target edition, hardware requirements, application compatibility, data backup and licensing | An upgrade path is not automatically supported between every edition or architecture. A clean installation may erase the intended data location. |
| Local or organization-managed account | Device enrollment, domain membership, identity source and intended resource | A local account's success does not prove a domain identity is healthy or authorized. |
| File-system selection | Required permissions, file sizes, portability, encryption and target OS support | A file system that transfers files conveniently may not supply the security features required for the working copy. |
| Disk extension | Disk/partition layout, supported file system, available space and recovery state | Free space somewhere on a disk is not proof that a particular basic volume can extend into it. |
| Startup management | Startup entry, publisher, resource impact, user need and management policy | Disable an identified unnecessary entry through an approved change; do not remove every service because startup is slow. |

Capture the installed OS edition and build before applying instructions. Do not treat an old screenshot as the current menu path or assume that every consumer edition supports the same management features.

### A controlled investigation of slow sign-in

Compare one affected user with another authorized test user on the same device, then compare the affected user's experience on another permitted device if available. This separates user/profile scope from machine scope without immediately deleting a profile. Correlate startup programs, disk pressure, policy processing and event timestamps with the delay. One high CPU reading is a lead, not proof of the persistent bottleneck.

If an approved clean-boot investigation is appropriate, follow the vendor procedure and record how to restore the prior startup configuration. A diagnostic startup state is not the final production configuration.

## 2. Access, elevation and encryption

Treat these as separate checks:

- **Identity:** which account actually signed in or authenticated?
- **Authorization:** which group memberships, effective permissions and applicable policies control the requested operation?
- **Elevation:** does the approved operation require a different execution token or administrative consent?
- **Encryption:** can the authorized principal access the key needed to decrypt the data?

A UAC prompt is not proof that a downloaded program is trustworthy. Conversely, suppressing UAC is not a good repair for an application with an incorrectly designed privilege requirement. Obtain the approved package, verify the requested operation and use the organization's elevation process.

For a Windows file-share denial, identify the actual user, share permission, NTFS permission and inheritance/deny context. A share-level change alone may not fix an NTFS denial. Making everyone an administrator hides the boundary rather than diagnosing it.

### BitLocker recovery without destroying the evidence

Confirm the device identity and the displayed recovery-key identifier. Follow the approved recovery process and retrieve the matching key through an authorized channel. A recovery prompt can follow a platform or boot configuration change; it is not proof that the encrypted data is corrupt. Do not clear the TPM, format the volume or publish a recovery key as an exploratory step. If the key is unavailable, stop and escalate before taking an irreversible action.

## 3. Connectivity versus name resolution

A useful observation ladder on an authorized Windows device is:

| Observation | What it helps establish | What it does not establish |
|---|---|---|
| `ipconfig /all` | Adapter configuration, addressing, gateway and configured DNS servers | Whether the requested application is permitted and working |
| `nslookup example.com` | A DNS query result using the selected resolver | Browser proxy, certificate or application authorization correctness |
| `ping <approved-address>` | ICMP reachability if permitted along that path | Service availability when ICMP is filtered, or application success when ICMP works |
| `tracert <approved-address>` | Visible path responses and possible scope clues | Proof that every nonresponding hop drops the application's traffic |

Replace example targets with approved lab endpoints. Avoid repeated probes of an employer's systems without authorization. An IP address working while a name fails suggests investigating DNS, but verify the application's actual destination and any proxy behavior before declaring the cause.

Do not start with `ipconfig /release` on a remotely managed machine: it changes connectivity and may end the only support session. Read-only observations should precede a deliberate reset.

## 4. Application, update and system-file failures

Correlate the first failure with the actual update, driver, configuration or application change. Distinguish a failed installation, an application crash and an OS startup problem. Match the repair to that layer.

- A driver regression may justify an approved rollback of that driver; reinstalling the entire OS is a much broader intervention.
- System File Checker and DISM address particular Windows component/system-file conditions. They are not universal repairs for third-party application bugs, account denials or a physically failing storage device. Follow the vendor's prerequisites and ordering when repair is justified.
- A restore point, a user-file backup and an image backup have different coverage. Verify what the selected recovery option retains, removes and requires before committing.
- An application that works for an administrator but not a standard user needs a permissions/configuration investigation, not a permanent administrator assignment by default.

Recovery confidence comes from confirming usable backups and required credentials, not just seeing a backup job labeled successful. After repair, repeat the original user task and check adjacent functions that the change could affect.

## 5. Suspected malware and sensitive evidence

Treat unusual behavior as an observation until investigated; do not label every slow device infected. If credible signs of compromise appear, follow the incident process: establish authority, contain through the approved method, notify the responsible team and preserve required evidence. Scanning, rebooting or deleting files can alter evidence, so coordinate those actions when preservation is required.

An alert being dismissed is not remediation. Document the affected scope, approved eradication/recovery actions, subsequent verification and user guidance. Do not request passwords over chat or send suspicious attachments to an unapproved external analysis service. Never disable protection globally merely to make an application install.

## 6. Operational procedures complete the fix

For a change, record purpose, risk, approval, affected assets, maintenance window, backup/rollback plan and success criterion. For a ticket, separate the user's description, observed facts, tests, conclusions and actions. Include timestamps and time zones when correlating multiple systems.

Remote assistance should use the approved tool and the required consent. Explain what you need to access and avoid viewing unrelated personal content. Redact logs before sharing; a harmless-looking screenshot can expose a username, token or recovery key.

If a script is involved, identify its inputs, privilege, side effects and failure handling before execution. Read-only discovery is not permission to run a downloaded repair script. If the change could affect safety, compliance or data retention, use the organization's escalation path rather than improvising policy.

**Close only after verification:** the user's original task works, the intended controls still apply, the temporary diagnostic state is removed and the ticket records a reproducible explanation of the outcome.
