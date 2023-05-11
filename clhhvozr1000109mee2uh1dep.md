---
title: "Catch and Store Error Messages in PowerShell"
datePublished: Wed May 10 2023 15:51:44 GMT+0000 (Coordinated Universal Time)
cuid: clhhvozr1000109mee2uh1dep
slug: catch-and-store-error-messages-in-powershell
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/heNwUmEtZzo/upload/5b8fc560a40dd8d28923c41cf8ae829f.jpeg
tags: powershell, try-and-catch

---

When you are in a flow, nothing is worse than having to stop to deal with a console error message. It would be great if the errors could be handled by the script and packaged into helpful messages. Happily, PowerShell offers this capability to catch, store, and take action on error messages when they happen in your code.

Like any good thing, catching and storing errors will require some planning upfront. What type of errors could your script encounter? Are there any actions the script could take when an error has happened? What do you want to do with the error after it has occurred?

Once you have answered these questions, you can begin coding a solution to catch and store any errors. The starting point for your script will be the PowerShell [try, catch](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_try_catch_finally?view=powershell-7.3) functionality. The try block will be the action taken in your script, and the catch block will be used if an error is encountered during the try action. Different error types can be specified and stored in variables in the catch block. The last error message that was encountered by the script is stored by default in $\_ and can be stored in a variable. The example below stores the error in the $LastException variable.

Additionally, you can include multiple catch blocks, to handle specific types of errors and then a general catch block for every other error. The example below looks for an ItemNotFoundException and stores the error in an $ItemNotFound variable.

```powershell
try
{
    Write-Host "Here are your action steps."
}
#This will catch an Item Not Found Exception
catch [System.Management.Automation.ItemNotFoundException] {
    $_.Exception.GetType().Name
    $ItemNotFound = $_.Exception.GetType().Name
}
catch
{
    Write-Host "Error: $($_)"
    $LastException = $_
}

if ($LastException)
{
    Write-Host "An error has occurred, the error text is $($LastException)."    
}
```

These examples should give you a good start toward handling errors in your PowerShell scripts. There are many options for additional handling and adding catch blocks to find and store additional error messages. Thank you for reading!