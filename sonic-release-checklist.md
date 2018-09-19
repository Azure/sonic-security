# SONiC release security checklist

The checklist below is expected to be worked through at least once per release.

Checklist items:
 
 -  Read through the security docs, meeting notes, issues reported and dependency track list, identify applicable items and perform them. 
 - Update SONiC (submodule, makefile) to retrieve newer upstream
   packages that fix security vulnerabilities.
 - Identify vulnerabilities that were caused by SONiC code and
   document them along with their mitigation.
 - Update the dependency track list with the security information such as CVEs the new release fixed.
 - Perform static code analysis for SONiC repos(This should be done during the code review process as well).
 - Perform security testing and generate a report attach to the release notes.
