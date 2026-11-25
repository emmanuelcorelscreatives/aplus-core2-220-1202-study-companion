# A+ Core 2: a repeatable study workflow

## A 35-minute review session

1. **Five minutes — retrieve:** choose one objective from the current official Core 2 list. Without notes, write its decision boundary: for example, file access versus encryption, or DNS versus application reachability.
2. **Ten minutes — investigate:** use an authorized lab or a sanitized fictional ticket. Write the symptom, the affected scope and the smallest observation that would distinguish two plausible causes.
3. **Ten minutes — verify:** open the relevant official reference. Identify what the tool or feature actually proves, its limitations and any edition/version prerequisite.
4. **Five minutes — explain:** summarize why the chosen next step is safer or more informative than a broader reset. Explain it as if handing the ticket to another technician.
5. **Five minutes — schedule:** record one follow-up and revisit the concept after a delay without rereading your answer first.

This is an optional learning routine, not a requirement to buy hardware, software or another course.

## A four-session rotation

| Session | Focus | Useful output |
|---|---|---|
| Operating systems | Deployment, accounts, disks, startup and recovery boundaries | A comparison of two recovery choices and the data each preserves |
| Security | Identity, authorization, elevation, encryption and incident handling | A diagram separating account, permission and key ownership |
| Troubleshooting | One reproducible application or connectivity fault | A test sequence with the expected result for each competing cause |
| Operations | Change, remote support, documentation and escalation | A sanitized ticket with a rollback plan and closure evidence |

Avoid spending every session on the easiest domain. Use the official domain weights to plan attention, then adjust for demonstrated weaknesses rather than guessing that your favorite tools will dominate an exam.

## Optional observation-only lab

On your own Windows device, record the OS build, inspect adapter settings with `ipconfig /all`, and inspect your current identity with `whoami`. On an authorized Linux lab, inspect the working directory with `pwd`, file permissions with `ls -l`, and file-system usage with `df -h`. Do not infer that these commands repair anything. Their learning purpose is to distinguish the information each observation supplies.

Record output only after removing identifying information. Do not collect a full environment dump: environment variables and configuration files may contain credentials. Do not change disk partitions, access controls or encryption settings as part of this observation-only activity.

## Personal review record

Copy this template into a private notebook:

```text
Date / objective / OS and build:
Symptom and affected scope:
Observation, not assumption:
Two plausible explanations:
Lowest-risk distinguishing test:
Expected result for each explanation:
Actual result, or "not performed":
Reference and relevant limitation:
Approved repair / rollback, or escalation:
Verification of the original task:
Confidence before / after:
Next review date:
```

Keep **not performed**, **failed**, **inconclusive** and **passed** separate. Reading a procedure is not executing it. A correct practice response with uncertain reasoning deserves review just like a wrong answer.

## When using practice tests

Attempt before reading explanations. For each uncertain or incorrect decision, record the missing distinction rather than copying the question. Revisit the principle later using a different symptom or platform context. Do not distribute assessment text or answer keys in a study group.

A percentage from independent practice is not a conversion to CompTIA's scaled score or a prediction of passing. Completion of this companion is not evidence of hands-on proficiency. Use the official objectives and permitted practical work to identify gaps beyond multiple-choice reasoning.
