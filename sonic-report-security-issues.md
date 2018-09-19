# How to report security issues on SONiC

This document describes how you can report SONiC security issues.

Two categories for security issues:

1. Security issues that you wanted to open publicly

 Please report issues to SONiC through github issue track:
[sonic-buildimage issues](https://github.com/Azure/sonic-buildimage/issues)
or other SONiC repos like
[sonic-swss issues](https://github.com/Azure/sonic-swss/issues)

 Please include **[security]** in the title, the issue should include **Description** which should includes SONiC version (sonic-buildimage commit id), CVE case number/link etc.

 Report issues with below information if applicable.
 * Steps to reproduce the issue
 * Describe the results you received
 * Describe the results you expected
 * Debug dumps etc

 Issues can be reported through:
[SONiC forum](https://groups.google.com/forum/#!forum/sonicproject)
or [SONiC Slack Workspace](sonicswitch.slack.com) as well.

2. Issues that you want to privately report to the community to address the problem before public disclosure. This might applicable for issuess that easy to reproduce and have high impact on the system.

 Please send emails to [sonic-security@googlegroups.com](sonic-security@googlegroups.com) with details about the security problem such as:
 
 * The SONiC version (sonic-buildimage commit-id)
 * How to reproduce the problem and the observered results.

 Note: Only the security team members can receive the emails.

 The SONiC security team will respond to you and coordinate community activity to address the problem:

  *  Engage community members to understand and address the problem
  *  Provide workarounds and fixes
  *  Keep problems private until announce
  *  Create a SONiC security advisory if needed
