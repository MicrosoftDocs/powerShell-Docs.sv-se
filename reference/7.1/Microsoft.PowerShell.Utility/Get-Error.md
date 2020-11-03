---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Error
ms.openlocfilehash: c29115a65b46d38039d78b10eee293e6944cede5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264410"
---
# <span data-ttu-id="064b4-103">Get-Error</span><span class="sxs-lookup"><span data-stu-id="064b4-103">Get-Error</span></span>

## <span data-ttu-id="064b4-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="064b4-104">SYNOPSIS</span></span>

<span data-ttu-id="064b4-105">Hämtar och visar de senaste fel meddelandena från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="064b4-105">Gets and displays the most recent error messages from the current session.</span></span>

## <span data-ttu-id="064b4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="064b4-106">SYNTAX</span></span>

### <span data-ttu-id="064b4-107">Nyaste (standard)</span><span class="sxs-lookup"><span data-stu-id="064b4-107">Newest (Default)</span></span>

```
Get-Error [[-Newest] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="064b4-108">Fel</span><span class="sxs-lookup"><span data-stu-id="064b4-108">Error</span></span>

```
Get-Error [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="064b4-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="064b4-109">DESCRIPTION</span></span>

<span data-ttu-id="064b4-110">`Get-Error`Cmdleten hämtar ett **PSExtendedError** -objekt som representerar den aktuella fel informationen från det senaste felet som inträffade i sessionen.</span><span class="sxs-lookup"><span data-stu-id="064b4-110">The `Get-Error` cmdlet gets a **PSExtendedError** object that represents the current error details from the last error that occurred in the session.</span></span>

<span data-ttu-id="064b4-111">Du kan använda `Get-Error` för att visa ett angivet antal fel som har inträffat i den aktuella sessionen med den **senaste** parametern.</span><span class="sxs-lookup"><span data-stu-id="064b4-111">You can use `Get-Error` to display a specified number of errors that have occurred in the current session using the **Newest** parameter.</span></span>

<span data-ttu-id="064b4-112">`Get-Error`Cmdleten tar även emot fel objekt från en samling, till exempel `$Error` för att visa flera fel från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="064b4-112">The `Get-Error` cmdlet also receives error objects from a collection, such as `$Error`, to display multiple errors from the current session.</span></span>

## <span data-ttu-id="064b4-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="064b4-113">EXAMPLES</span></span>

### <span data-ttu-id="064b4-114">Exempel 1: hämta den senaste fel informationen</span><span class="sxs-lookup"><span data-stu-id="064b4-114">Example 1: Get the most recent error details</span></span>

<span data-ttu-id="064b4-115">I det här exemplet `Get-Error` visas information om de senaste fel som inträffat i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="064b4-115">In this example, `Get-Error` displays the details of the most recent error that occurred in the current session.</span></span>

```powershell
Get-Childitem -path /NoRealDirectory
Get-Error
```

```
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.

Exception             :
    ErrorRecord          :
        Exception             :
            Message : Cannot find path 'C:\NoRealDirectory' because it does not exist.
            HResult : -2146233087
        TargetObject          : C:\NoRealDirectory
        CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [], ParentContainsErrorRecordException
        FullyQualifiedErrorId : PathNotFound
    ItemName             : C:\NoRealDirectory
    SessionStateCategory : Drive
    TargetSite           :
        Name          : GetChildItems
        DeclaringType : System.Management.Automation.SessionStateInternal
        MemberType    : Method
        Module        : System.Management.Automation.dll
    StackTrace           :
   at System.Management.Automation.SessionStateInternal.GetChildItems(String path, Boolean recurse, UInt32 depth,
CmdletProviderContext context)
   at System.Management.Automation.ChildItemCmdletProviderIntrinsics.Get(String path, Boolean recurse, UInt32
depth, CmdletProviderContext context)
   at Microsoft.PowerShell.Commands.GetChildItemCommand.ProcessRecord()
    Message              : Cannot find path 'C:\NoRealDirectory' because it does not exist.
    Source               : System.Management.Automation
    HResult              : -2146233087
TargetObject          : C:\NoRealDirectory
CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [Get-ChildItem], ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
InvocationInfo        :
    MyCommand        : Get-ChildItem
    ScriptLineNumber : 1
    OffsetInLine     : 1
    HistoryId        : 57
    Line             : Get-Childitem -path c:\NoRealDirectory
    PositionMessage  : At line:1 char:1
                       + Get-Childitem -path c:\NoRealDirectory
                       + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    InvocationName   : Get-Childitem
    CommandOrigin    : Internal
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo :
```

### <span data-ttu-id="064b4-116">Exempel 2: Hämta det angivna antalet fel meddelanden som inträffat under den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="064b4-116">Example 2: Get the specified number of error messages that occurred in the current session</span></span>

<span data-ttu-id="064b4-117">Det här exemplet visar hur du använder `Get-Error` med den **senaste** parametern.</span><span class="sxs-lookup"><span data-stu-id="064b4-117">This example shows how to use `Get-Error` with the **Newest** parameter.</span></span> <span data-ttu-id="064b4-118">I det här exemplet returnerar den **senaste** informationen om de tre senaste fel som inträffade i den här sessionen.</span><span class="sxs-lookup"><span data-stu-id="064b4-118">In this example, **Newest** returns the details of the 3 newest errors that occurred in this session.</span></span>

```powershell
Get-Error -Newest 3
```

### <span data-ttu-id="064b4-119">Exempel 3: skicka en samling fel för att få detaljerade meddelanden</span><span class="sxs-lookup"><span data-stu-id="064b4-119">Example 3: Send a collection of errors to receive detailed messages</span></span>

<span data-ttu-id="064b4-120">Den `$Error` automatiska variabeln innehåller en matris med fel objekt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="064b4-120">The `$Error` automatic variable contains an array of error objects in the current session.</span></span> <span data-ttu-id="064b4-121">Objekts mat ris kan vara skickas för `Get-Error` att få detaljerade fel meddelanden.</span><span class="sxs-lookup"><span data-stu-id="064b4-121">The array of objects can be piped to `Get-Error` to receive detailed error messages.</span></span>

<span data-ttu-id="064b4-122">I det här exemplet `$Error` är skickas till- `Get-Error` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="064b4-122">In this example, `$Error` is piped to the `Get-Error` cmdlet.</span></span> <span data-ttu-id="064b4-123">Resultatet är en lista med detaljerade fel meddelanden, liknande resultatet i exempel 1.</span><span class="sxs-lookup"><span data-stu-id="064b4-123">the result is list of detailed error messages, similar to the result of Example 1.</span></span>

```powershell
$Error | Get-Error
```

## <span data-ttu-id="064b4-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="064b4-124">PARAMETERS</span></span>

### <span data-ttu-id="064b4-125">– Nyaste</span><span class="sxs-lookup"><span data-stu-id="064b4-125">-Newest</span></span>

<span data-ttu-id="064b4-126">Anger antalet fel som ska visas i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="064b4-126">Specifies the number of errors to display that have occurred in the current session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Newest
Aliases: Last

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="064b4-127">– InputObject</span><span class="sxs-lookup"><span data-stu-id="064b4-127">-InputObject</span></span>

<span data-ttu-id="064b4-128">Den här parametern används för pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="064b4-128">This parameter is used for pipeline input.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Error
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="064b4-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="064b4-129">CommonParameters</span></span>

<span data-ttu-id="064b4-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="064b4-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="064b4-131">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="064b4-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="064b4-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="064b4-132">INPUTS</span></span>

### <span data-ttu-id="064b4-133">PSObject</span><span class="sxs-lookup"><span data-stu-id="064b4-133">PSObject</span></span>

<span data-ttu-id="064b4-134">Har stöd för inmatade från alla **PSObject** , men resultaten varierar om varken ett **ErrorRecord** -eller **Exception** -objekt anges.</span><span class="sxs-lookup"><span data-stu-id="064b4-134">Supports input from any **PSObject** , but results vary unless either an **ErrorRecord** or **Exception** object are supplied.</span></span>

## <span data-ttu-id="064b4-135">UTDATA</span><span class="sxs-lookup"><span data-stu-id="064b4-135">OUTPUTS</span></span>

### <span data-ttu-id="064b4-136">System. Management. Automation. ErrorRecord # PSExtendedError</span><span class="sxs-lookup"><span data-stu-id="064b4-136">System.Management.Automation.ErrorRecord#PSExtendedError</span></span>

<span data-ttu-id="064b4-137">Utdata i ett **PSExtendedError** -objekt.</span><span class="sxs-lookup"><span data-stu-id="064b4-137">Output in a **PSExtendedError** object.</span></span>

## <span data-ttu-id="064b4-138">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="064b4-138">NOTES</span></span>

<span data-ttu-id="064b4-139">`Get-Error` accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="064b4-139">`Get-Error` accepts pipeline input.</span></span> <span data-ttu-id="064b4-140">Till exempel `$Error | Get-Error`.</span><span class="sxs-lookup"><span data-stu-id="064b4-140">For example, `$Error | Get-Error`.</span></span>

## <span data-ttu-id="064b4-141">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="064b4-141">RELATED LINKS</span></span>

[<span data-ttu-id="064b4-142">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="064b4-142">about_Try_Catch_Finally</span></span>](../Microsoft.PowerShell.Core/About/about_Try_Catch_Finally.md)
