---
title: "How to remove files by last write time with PowerShell"
datePublished: Tue Nov 29 2022 17:42:39 GMT+0000 (Coordinated Universal Time)
cuid: clb2ibmjg000g08kuh24g3iyu
slug: how-to-remove-files-by-last-write-time-with-powershell
cover: https://cdn.hashnode.com/res/hashnode/image/unsplash/7EwWeNyzSwQ/upload/v1669743465377/8zJJBNxw6.jpeg
tags: powershell

---

Drive space is a finite resource, ask any server administrator. No one wants to see the message, “No space on disk”, when you are trying to save that last document. How can you clean up files that you don’t need? As always, PowerShell makes it simple.

This script will remove files by last write time, which is the last date and time the file was modified.

```
$Now=Get-Date
Get-Childitem C:\FilePath\*.* | Where-Object { $_.LastWriteTime -lt $Now.AddDays(-30) } | Remove-Item -Verbose
``` 
The first step is to get the time you want to use as the baseline for the delete, this is what you will compare against when telling the script what files to remove. In the example, this date and time is stored in the variable $Now. The Get-Date command will retrieve the date and time when the script is run.

The next step is to get a list of files that are candidates for removal. This is done with the Get-ChildItem command and the file path. This information is sent to the Where-Object command which determines which files meet the criteria. In the example, last write time is used along with $Now.AddDays(-30) which subtracts 30 days from the current date. Any files where the last write time is more than 30 days old are then sent to the Remove-Item command and deleted.
