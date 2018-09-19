# Security code review and code priority definitions
This document provides criteria to consider when prioritizing code for a security review and guidance on how to define priority for your project. It is not an exhaustive list and should not be treated as one.

## Code Priority Definitions
Use the information below during security code reviews to help determine which components are most at risk and set project priorities.  
High-risk items—Priority 1—should be reviewed the earliest and most in depth. 

Any code or component that has a high number of frequently-discovered security bugs is considered to be Priority 1 code, even if it otherwise maps to Priority 2 or Priority 3 per the definitions in the documents referenced above. While the definition of high rates of security bugs is subjective within the team, it is important to examine the portions of code that have experienced the highest rates of security issues with extra scrutiny.

Don't forget to include and prioritize all sample code shipped with the product. Consider how customers will be using the samples. Samples that are expected to be compiled and used with little modification in production environments should be considered Priority 1. 

Code priority definitions are provided in the following sections.
### Priority 1 Code
Priority 1 code is considered the most sensitive from a security standpoint. The following examples of Priority 1 code are not a definitive list, but are a starting point and provide a general overview of the types of code that should be given extra scrutiny:

-	All Internet or network-facing code.
-	Code in the Trusted Computing Base (TCB) (for example, kernel or SYSTEM code).
-	Code running as Administrator or Local System.
-	Code running as an elevated user (including LocalService and NetworkService).
-	Features with a history of vulnerability, regardless of version.
-	Any code that handles secret data, such as encryption keys and passwords.
-	Any unverifiable managed code (any code that the standard PEVerify.exe tool reports as not verified).
-	All code supporting functionality exposed on the maximum attack surface.

### Priority 2 Code
Priority 2 code is optionally installed code that runs with user privilege, or code that is installed by default that does not meet the Priority 1 criteria.

### Priority 3 Code
Priority 3 code is rarely used code and setup code.

NOTE: Setup code that handles secret data, such as encryption keys and passwords, is always considered Priority 1 code.
