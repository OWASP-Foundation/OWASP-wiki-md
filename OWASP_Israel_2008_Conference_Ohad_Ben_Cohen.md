## Korset: Code-based Intrusion Detection System for Linux, Ohad Ben-Cohen

Presented at BlackHat

Host-based Intrusion Detection Systems traditionally compare observable
data to pre-constructed models of normal behavior. Such models can
either be automatically learnt during a training session, or manually
written by the user. Alas, the former technique suffers from false
positives, and therefore repeatedly requires user intervention, while
the latter technique is tedious and demanding.

In this talk we discuss how static analysis can be used to automatically
construct a model of application behavior. We call this methodology
"Code-based Intrusion Detection", and show that its derived model can
prevent future or unknown code injection attacks (such as Buffer
Overflows) with guaranteed zero false alarms. We will then present
Korset, a Linux prototype that implements this approach with negligible
runtime overheads.

## Bio

Ohad Ben-Cohen is a Linux Kernel developer and consultant, bringing
years of Information Security expertise and Free and Open Source
Software know how. His recent Open Source work includes writing Texas
Instruments' Bluelink Linux driver, Bluetooth power management support
for the kernel and the Linux port of TI's FM stack. He teaches System
Programming at Tel-Aviv University, where he conducts his research and
develops Korset.

In collaboration with Avishai Wool, Tel-Aviv University