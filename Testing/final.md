# Offensive Security Engineering (CSEC 559/659)

### Final Project

# Tests

## Overview

The goal of these tests is to ensure that the client is working as expected, and is able to correctly fetch, run, and return all of its new (and old) tasking, as well as smoothly handle any errors. This test document will demonstrate the resolution of all warnings at the `W4` level, the successful implementation of the new `mimikatz` task, the use of encryption between the client and the server, the removal of a visible console window when the client is run, and any other miscellaneous improvements.

## Screenshots and Descriptions

### Resolution of Warnings

![Figure 1: Warning Level 4](final-images/warning-level.png)

**Figure 1: Warning Level 4** The first screenshot shows that the Client's warning level is set to `Level4 (/W4)`, and that it will halt the build process if any warnings are issued, treating them as if they were errors.***

![Figure 2: No Warnings](final-images/build-output.png)

**Figure 2: No Warnings** The second screenshot depicts a full rebuild completing successfully (and not being interrupted, as it would if there were a warning or error), as well as the Error List window, which shows the warning and error count both equal to `0`.***

### Mimikatz Task

![Figure 3: Mimikatz Commands](final-images/mimikatz.png)

**Figure 3: Mimikatz Commands**

![Figure 4: Mimikatz Tasks](final-images/mimikatz-tasks.png)

**Figure 4: Mimikatz Tasks**

![Figure 5: Mimikatz Standard Result](final-images/mimikatz-1.png)

**Figure 5: Mimikatz Standard Result**

![Figure 6: Mimikatz Logonpasswords Result](final-images/mimikatz-2.png)

**Figure 6: Mimikatz Logonpasswords Result**

***The first screenshot shows a mimikatz sequence of commands being issued, followed by the logonpasswords alias. Then, the task ID's and statuses are shown, followed by the result of each task.***

### Encryption Between Client and Server

![CLI Commands](final-images/random-CLI.png)

![Encrypted Registration](final-images/random-registration.png)

![Encrypted listprivs Task Result](final-images/random-listprivs.png)

***The first screenshot shows the CLI selecting an agent and then sending it the `listprivs` task (specifically chosen because of the large amount of data it causes the client to send back to the server).***

***The second screenshot displays a Wireshark packet capture that was running during the Client, Server, CLI interaction shown in the first screenshot. As you can see, the very first HTTP packet (the Client registering with the Server) contains only high entropy (encrypted) bytes in its data field. Only the HTTP headers and encapsulating structures are left unencrypted. Because the server was able to successfully register the Client, in order for it to be able to be selected in the CLI, it must have been able to successfully decrypt the encrypted registration data.***

***Similar to the second screenshot, the third screenshot highlights the data field in an HTTP packet only containing encrypted data. This time, however, the packet is delivering the results of the `listprivs` command, demonstrating that all types of requests are encrypted, not just registration requests. In addition, the HTTP stream is followed in the center window, showing successful communication between the Client and the Server, both encrypting their communication data before sending it.***

### Removal of Visible Console

![Windows Subsystem Configuration](final-images/windows-subsystem-configuration.png)

***This screenshot shows the correct configuration for removing the visible console window for Release builds***

![Running Without Window](final-images/running-without-window.png)

***Here, VisualStudio is shown to be actively running a Release build of the Client, and no corresponding console window is to be found.***

### Help Information

![help](final-images/help-command.png)

***In this screenshot, the improved `help` command's output is shown. Although all of the help messages and specific command examples couldn't be shown in this screenshot, they can easily be referenced [here](../Server/cli/ReadMe.md), in the CLI documentation.***

## Documented Re-Tests

![terminate](final-images/terminate.png)

***This screenshot shows the terminate functionality***

![history](final-images/history.png)

***This screenshot shows the history functionality***

![pwd](final-images/pwd.png)

***This screenshot shows the pwd functionality***

![cd](final-images/cd.png)

***This screenshot shows the cd functionality***

![whoami](final-images/whoami.png)

***This screenshot shows the whoami functionality***

![ps](final-images/ps.png)

![ps2](final-images/pscont.png)

***These screenshots show the ps functionality***


![Shell](final-images/shell.png)

![Shell](final-images/shell2.png)

***These screenshots shows the shell functionality***

![setpriv](final-images/setpriv.png)

***This screenshot shows the functionality of the setpriv command***

![listprivs](final-images/listprivs.png)

***This screenshot shows the functionality of the listprivs command, where you can see the priv that was set using the setpriv command above.***

![tasks](final-images/tasks.png)

![task](final-images/task.png)

***These screenshots show the functionality of the task command.***

![bypassuac](final-images/bypassuac.png)

***This screenshot shows the functionality of the bypassuac command***

![getsystem](final-images/getsystem.png)

***This screenshot shows the functionality of the getsystem command***

![sysinfo](final-images/sysinfo.png)

***This screenshot shows the functionality of the sysinfo command***

![Screenshot](final-images/screenshot.png)

***This screenshot shows the functionality of the screenshot command.***

![the screenshot that was taken](final-images/AGENT-TASK.png)

***This is the screenshot taken using the above command***

![Sleep](final-images/sleep.png)

***This screenshot shows the functionality of the sleep command***

# AAR

Date: 08/12/2024

Attendees: [Praj Shete, Michael Scalzetti, Michael Pothaczky, Amrit Sinha]

* what went well?
  * met most of the functionalities
  * completed in given time
* what didnt go well?
  * missed out on encrypotion and external IP part
* what should we change?
  * invest more time for the project


