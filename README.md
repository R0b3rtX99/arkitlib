# arkitlib
Automatically exported from code.google.com/p/arkitlib
Introduction
ARKit is an open-source rootkit detection library for Microsoft Windows. ARKit has two components:

ARKitLib.lib - A Win32/C++ static library that exposes various methods to scan system and detect rootkits
ARKitDrv.sys - A device driver that actually implements methods to scan and detect rootkits
Features
Currently, ARKit library has following features:

Process scanning – Detect all running processes (hidden and visible)
DLL scanning – Detect DLLs loaded in a process
Driver scanning – Detect all loaded drivers (hidden and visible)
SSDT hook detection and restoration
Sysenter hook detection
Kernel inline hook detection and restoration
Supported Operating Systems
ARKit works on 32-bit flavors of Windows 2000, XP, 2003 and Vista. It has not been tested on Windows 2008 and Windows 7 yet. 
Summary of detection techniques in ARKit
Process detection methods:

PID brute force (PsLookupProcessByProcessId)
TID brute force (PsLookupThreadByThreadId)
Handle table traversing (NtQuerySystemInformation)
DLL detection methods:

InMemoryOrderModuleList traversal in process' PEB
VAD tree walking
Process termination methods:

NtTerminateProcess/ZwTerminateProcess
NtTerminateThread/ZwTerminateThread for all threads of a process
Driver detection methods:

PsLoadedModuleList traversing
\Driver\ directory traversing in Object Manager
\Device\ directory traversing in Object Manager
Source Code
ARKitLib.lib: ARKitLib directory in Source section
ARKitDrv.sys: ARKitDrv directory in Source section
ARKitTester.exe: ARKitTester directory in Source section. An executable is available in Downloads section
Use SVN tools such as TortoiseSVN to checkout/download source code.

Using ARKit
Using ARKit library is quite simple:

Include ARKitLib.h and ARKitDefines.h header files in your application source
Link to ARKitLib.lib and Psapi.lib
Instantiate an object of ARKitLib class and use various member functions to gather system data
While running your application, make sure that ARKitDrv.sys driver is in the same directory where application is present
Take a look at ARKitTester, an example application that shows how to make use of ARKit. 
Todo list
Methods to disable drivers
Boot sector rootkit detection
Note
Windows DDK or WDK is needed to compile and build ARKitDrv.sys. You can get it here.
ARKitLib.lib component uses few Psapi APIs. So, applications using ARKitLib.lib should link with Psapi.lib
ARKit uses open-source XDE disassembling engine. More information about XDE can be found here.
