---
title: "How to check for multiple files with PowerShell"
datePublished: Wed Nov 16 2022 18:06:30 GMT+0000 (Coordinated Universal Time)
cuid: clajyg8al000208lb4cj1a7t3
slug: how-to-check-for-multiple-files-with-powershell
cover: https://cdn.hashnode.com/res/hashnode/image/unsplash/d9ILr-dbEdg/upload/v1669053866543/0cVArPKjo.jpeg
tags: powershell

---

In PowerShell, checking for a file is as simple as using the Test-Path command with the file path. Followed by an if statement, this is a great tool to check when a file exists. If the result of Test-Path is stored in a variable, this can be used to evaluate the result and proceed, as necessary.

But what if multiple files are needed before acting? The Test-Path command can accept an array with each path being separated by commas. While checking the result for a single file is a simple True/False statement, checking the result of a Test-Path array is more difficult. When the result of a Test-Path array is stored in a variable, it stores the result of each file path check. All the file paths may evaluate to True, False, or a combination of both. This means, when checking the result, it is necessary to accept one desired outcome and discard all others.

For example, to accept only an outcome where all file paths evaluate to True, the -notcontains $false modifier can be used on Test-Path. This will ignore any outcomes that are false meaning the whole Test-Path statement will only be True when all file paths in the array are True. The same logic can be used in reverse if the desired outcome is for all of the paths to be False.

Here is an example of how to use an array with Test-Path. In this example the $result variable will only be true if all paths in the array exist.


```
$filecheck = “File Path 1”, “File Path 2”, “File Path 3”
$result = ($filecheck | Test-Path) -notcontains $false
``` 
