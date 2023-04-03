---
title: "Evaluating (s)ftp exit codes"
datePublished: Thu Nov 17 2022 17:15:43 GMT+0000 (Coordinated Universal Time)
cuid: clalc2rhk000108iifgqsazl5
slug: evaluating-sftp-exit-codes
cover: https://cdn.hashnode.com/res/hashnode/image/unsplash/f77Bh3inUpE/upload/v1669053827562/ACjlfJnAE.jpeg
tags: windows-server, sftp

---

By design, ftp interfaces are simple. Connect to a server, get or put and file and disconnect. This has advantages, it is simple to learn and to use, the barrier to entry is low and changes to syntax are few. This is ideal for ad hoc transfers to and from a server, but for automated transfers this can pose challenges.

When performing an ad hoc transfer, it is easy to see when a transfer fails and take action to correct it. But when using automation for file transfers, this becomes difficult. How do you know when a transfer fails and how it should be corrected? A first step toward this is evaluating the exit code of the ftp script. This would indicate if the script completed all steps successfully or not. It will not indicate exactly what failed, this will require further investigation. The exit codes are zero for success and one for failure. There is some variation in exit codes between ftp clients but zero is always success and one is always a type of failure. Evaluating the exit code for non-zero values would indicate whether a script failed and needs further review.

To evaluate the exit code, add the following line to the end of a shell script in Windows after the ftp commands have completed.


```
IF %ERRORLEVEL% EQU 0 Echo Success > “Path to File”
``` 

This line will check if the exit code is zero and write the word “Success” to a defined file. Evaluating the exit code is not limited to this type of interaction, using the if statement above, any number of actions can be performed after the exit code is evaluated. For instance, if the exit code is not equal to zero a message could be sent to indicate further review is needed. The exit code could also be consumed by another monitoring tool which would allow for automated alerting in cases where many transfers need to be evaluated. The options are only limited to your imagination but evaluating the exit code is the entry point for knowing if a file transfer was successful.
