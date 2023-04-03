---
title: "How to compare file lengths with PowerShell"
datePublished: Thu Dec 01 2022 19:07:45 GMT+0000 (Coordinated Universal Time)
cuid: clb5g8rnr000408m9g57bdooz
slug: how-to-compare-file-lengths-with-powershell
cover: https://cdn.hashnode.com/res/hashnode/image/unsplash/Q9y3LRuuxmg/upload/v1669921595933/imUxuusM8.jpeg
tags: powershell

---

After a file copy is complete, how can you be sure the entire file was copied? This can be done with the file length command in PowerShell. This will compare the length in bytes of each file and, combined with an if statement, is a way to perform remediation on a failed file copy automatically.

First, store each file contents in memory using variables and the Get-Item command. Then compare them with an if statement using the file.Length command. The space in the else rackets can be used to take appropriate action if the file lengths do not match.

```
$file1 = Get-Item ‘C:\FilePath\File1.file’ -Verbose
$file2 = Get-Item ‘C:\FilePath\File2.file’ -Verbose
If ($file1.Length -eq $file2.Length)
{ Write-Host “File Sizes Match” }
else
{ Write-Host “File Sizes Do Not Match” }
``` 
