---
title: "How to cast a string value as an integer in PowerShell"
datePublished: Mon Nov 28 2022 15:24:13 GMT+0000 (Coordinated Universal Time)
cuid: clb0xxr7u000808mihfnh0rlz
slug: how-to-cast-a-string-value-as-an-integer-in-powershell
cover: https://cdn.hashnode.com/res/hashnode/image/unsplash/mdADGzyXCVE/upload/v1669649032805/ZdFOaWCKF.jpeg
tags: powershell, string, integer

---

When numbers are stored as a string in a database, it is difficult to sort them, so they are readable to human users. PowerShell makes this operation simple, to take a string value, cast it as an integer, sort it by numeric value and create an output file with the sorted values.

To perform this operation, use the code here.

```
$SortValues = Get-Content -Path C:\FilePath\FileName.file | ForEach-Object -Process {[int]$_} | Sort-Object
$SortValues | ForEach-Object {$_.ToString(“0000000000000000”)} | Out-File -FilePath C:\FilePath\SortedFileName.file
``` 
The code assumes that the values are stored in a file, with the first command retrieving the data from the file. This data is then sent to the ForEach-Object command which casts the string values as integers and then sorts each value in ascending order. This data is stored in the variable $SortValues which can then be used to create an output file in the second command.

The second command takes the data stored in the $SortValues variable and makes sure each value is 16 characters, meaning it will add leading zeroes where necessary. Please note, that this step is not necessary, if you want to simply output the values as they are to a file, this section can be removed, leaving the Out-File command. The Out-File command then creates an output file with the values sorted by number. 
