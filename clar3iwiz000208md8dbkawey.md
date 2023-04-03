---
title: "How to remove duplicate files with PowerShell"
datePublished: Mon Nov 21 2022 18:02:56 GMT+0000 (Coordinated Universal Time)
cuid: clar3iwiz000208md8dbkawey
slug: how-to-remove-duplicate-files-with-powershell
cover: https://cdn.hashnode.com/res/hashnode/image/unsplash/fPxOowbR6ls/upload/v1669053759268/a_xTHtsX2.jpeg
tags: windows, powershell

---

So, you have a folder full of files, the names look similar, and you’re not sure what is in them. Storage space is tight, and you do not want to keep duplicate copies. How can you remove the duplicate files while avoiding the painstaking work of sorting through each one? With PowerShell and file hashes, the answer is, surprisingly easy. For files that are exact copies of each other, the file hash is the same, so the operation is to find the file hashes for a group of files and remove only one of the duplicates. Here is the complete operation to remove duplicate files with an explanation that follows.

```
Get-ChildItem “C:\FilePath\*FileName.file” | Get-FileHash | Group-Object -property hash | Where-Object { $_.count -gt 1 } | ForEach-Object { $_.group | Select-Object -skip 1 } | Remove-Item -Verbose
``` 
The first step is to get a list of the files that are duplicated, this is done with Get-ChildItem and the path and name of the files. This list is then sent to the Get-FileHash command which retrieves the file hash for each file in the list. The file hashes are then grouped by the hash number with Group-Object so the duplicate file hashes will be next to each other in the list. This is important for the next step.

The grouped list is then sent to Where-Object which counts the list for file hashes where the value is greater than one. This will identify only the duplicated files from the list. The grouped objects are then sent to ForEach-Object which creates a loop to run through each set of duplicate files. In each duplicate object set, one file is skipped and not retained in the list that is sent to Remove-Item to delete the file. Now duplicates should have been removed.
