# Review
## Info
Reviewer Name: Zhenghui Guo
Paper Title: Trust and Protection in the Illinois Browser Operating System
## Summary
With Ibos, web browsers and operating systems are codesigned in a way that makes browser abstractions first-class OS abstractions, while traditional system components and services are removed from the TCB.
### Problem and why we care
A single address space-based browser (monolithic browser) indicates that all your contents are crowded in one domain. If an attacker attacks only some parts of a computer system or software, the whole system or software can be compromised. Having access to a browser can allow an attacker to access a user's personal data on the user's computer system, which is damaging.
### Gap in current approaches
Most browsers back in the time when this paper was published, they only built on superficial Monolithic browsers running top on the operating system that isolates each web page by conditional loops, but it would be very easy to get into the browser and control everything. Decomposes the giant single system browser to much smaller subsystems to separate and reduce complexity between security logic and implements of the browser.
Browser like google chrome, even though an isolated computing base is an improvement over Monolithic Browser's untrusted computing base, it still has a huge amount of code in part of their trusted computing base. Regarding the gap in current approaches, the paper proposes using a system like Microkernel to isolate components, but all those components(like TCP, web App, and filesystem) are shared and limited by current O/S.
### Hypothesis, Key Idea, or Main Claim
Their key idea is to build a whole new OS to make the web browser more secure, to make browser abstractions as first-class OS abstractions, separate each web instance as a process and lift all components, and nest software to monitor interactions between them. If any of those components are broken, the user can still browse safely.
### Method for Proving the Claim
They use security invariants that are assertions on all interactions between subsystems that check basic security properties of each of the different components of our system
### Method for evaluating
This paper analyzes the security of IBOS by measuring the number of lines of code (LOC) in the IBOS TCB and comparing it with other systems like google chrome and by looking at recent bugs in comparable systems and counting vulnerabilities that IBOS is susceptible to
### Contributions: what we take away
The monolithic approach is really vulnerable. Using security invariants allows us to check the key security properties of each component without having to understand how they are implemented.
## Pros (3-6 bullets)
1, It can deal with the device driver by splitting driver architecture device logic and programming of the underline device and DMA underlying buffer, Even if somebody breaks into it.
2, It provides more security by identities are all visible to the kernel, so it’s the underlying kernel to making this security decision
3, They separate out the handling of the network from the webpage instance itself that provides clean separation for the system allow different policies to network
4， Provide page-level protection. Ibos encrypt data before storing it to prevent the severity invariance for substoring system.
5, Ibos have much fewer lines of code, which reduces the level of complexity compared to other browsers running on traditional commodity system kernels in TCB(Trust computing base).
6,
## Cons (3-6 bullets)
IBOS added little overhead when compared to today’s high-performance browsers
IBOS only pay attention to integrity and confidentiality. Attacks like denial-of-service(Dos) are still viable. So, they can still work with that.
Still vulnerable if the hardware has the bug. There is a specific device code that has one bug that IBos can't handle as the evaluation in the paper.
### What is your analysis of the proposed?
Make browser abstraction first class-OS provides high-security insurance by reducing TCB. This ensures that some part of the components is compromised, but the rest of the system is continued. I did not analyze what is the impact on the rest of other OS abstractions if we make browser abstraction first class-OS.
## Details Comments, Observations, Questions
What is the impact on the resting of other OS abstractions if we make browser abstraction first class-OS? Is this going to harshly reduce the performance of the overall OS?
I have questions regarding why IBos did not get popular. I mean, if I understand this correctly, I did not see we are using Ibos as the main web browser today. Is this main there is some really serious drawback there. Or community web browser has already absorbed that idea in their nowadays version
