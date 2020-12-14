---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Error
ms.openlocfilehash: 7e4f4adf60a4f6386c646d92ada0003f239f05f4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709445"
---
# <span data-ttu-id="76489-102">Get-Error</span><span class="sxs-lookup"><span data-stu-id="76489-102">Get-Error</span></span>

## <span data-ttu-id="76489-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="76489-103">SYNOPSIS</span></span>

<span data-ttu-id="76489-104">Hämtar och visar de senaste fel meddelandena från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="76489-104">Gets and displays the most recent error messages from the current session.</span></span>

## <span data-ttu-id="76489-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="76489-105">SYNTAX</span></span>

### <span data-ttu-id="76489-106">Nyaste (standard)</span><span class="sxs-lookup"><span data-stu-id="76489-106">Newest (Default)</span></span>

```
Get-Error [[-Newest] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="76489-107">Fel</span><span class="sxs-lookup"><span data-stu-id="76489-107">Error</span></span>

```
Get-Error [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="76489-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="76489-108">DESCRIPTION</span></span>

<span data-ttu-id="76489-109">`Get-Error`Cmdleten hämtar ett **PSExtendedError** -objekt som representerar den aktuella fel informationen från det senaste felet som inträffade i sessionen.</span><span class="sxs-lookup"><span data-stu-id="76489-109">The `Get-Error` cmdlet gets a **PSExtendedError** object that represents the current error details from the last error that occurred in the session.</span></span>

<span data-ttu-id="76489-110">Du kan använda `Get-Error` för att visa ett angivet antal fel som har inträffat i den aktuella sessionen med den **senaste** parametern.</span><span class="sxs-lookup"><span data-stu-id="76489-110">You can use `Get-Error` to display a specified number of errors that have occurred in the current session using the **Newest** parameter.</span></span>

<span data-ttu-id="76489-111">`Get-Error`Cmdleten tar även emot fel objekt från en samling, till exempel `$Error` för att visa flera fel från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="76489-111">The `Get-Error` cmdlet also receives error objects from a collection, such as `$Error`, to display multiple errors from the current session.</span></span>

## <span data-ttu-id="76489-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="76489-112">EXAMPLES</span></span>

### <span data-ttu-id="76489-113">Exempel 1: hämta den senaste fel informationen</span><span class="sxs-lookup"><span data-stu-id="76489-113">Example 1: Get the most recent error details</span></span>

<span data-ttu-id="76489-114">I det här exemplet `Get-Error` visas information om de senaste fel som inträffat i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="76489-114">In this example, `Get-Error` displays the details of the most recent error that occurred in the current session.</span></span>

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

### <span data-ttu-id="76489-115">Exempel 2: Hämta det angivna antalet fel meddelanden som inträffat under den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="76489-115">Example 2: Get the specified number of error messages that occurred in the current session</span></span>

<span data-ttu-id="76489-116">Det här exemplet visar hur du använder `Get-Error` med den **senaste** parametern.</span><span class="sxs-lookup"><span data-stu-id="76489-116">This example shows how to use `Get-Error` with the **Newest** parameter.</span></span> <span data-ttu-id="76489-117">I det här exemplet returnerar den **senaste** informationen om de tre senaste fel som inträffade i den här sessionen.</span><span class="sxs-lookup"><span data-stu-id="76489-117">In this example, **Newest** returns the details of the 3 newest errors that occurred in this session.</span></span>

```powershell
Get-Error -Newest 3
```

### <span data-ttu-id="76489-118">Exempel 3: skicka en samling fel för att få detaljerade meddelanden</span><span class="sxs-lookup"><span data-stu-id="76489-118">Example 3: Send a collection of errors to receive detailed messages</span></span>

<span data-ttu-id="76489-119">Den `$Error` automatiska variabeln innehåller en matris med fel objekt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="76489-119">The `$Error` automatic variable contains an array of error objects in the current session.</span></span> <span data-ttu-id="76489-120">Objekts mat ris kan vara skickas för `Get-Error` att få detaljerade fel meddelanden.</span><span class="sxs-lookup"><span data-stu-id="76489-120">The array of objects can be piped to `Get-Error` to receive detailed error messages.</span></span>

<span data-ttu-id="76489-121">I det här exemplet `$Error` är skickas till- `Get-Error` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="76489-121">In this example, `$Error` is piped to the `Get-Error` cmdlet.</span></span> <span data-ttu-id="76489-122">Resultatet är en lista med detaljerade fel meddelanden, liknande resultatet i exempel 1.</span><span class="sxs-lookup"><span data-stu-id="76489-122">the result is list of detailed error messages, similar to the result of Example 1.</span></span>

```powershell
$Error | Get-Error
```

## <span data-ttu-id="76489-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="76489-123">PARAMETERS</span></span>

### <span data-ttu-id="76489-124">– Nyaste</span><span class="sxs-lookup"><span data-stu-id="76489-124">-Newest</span></span>

<span data-ttu-id="76489-125">Anger antalet fel som ska visas i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="76489-125">Specifies the number of errors to display that have occurred in the current session.</span></span>

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

### <span data-ttu-id="76489-126">– InputObject</span><span class="sxs-lookup"><span data-stu-id="76489-126">-InputObject</span></span>

<span data-ttu-id="76489-127">Den här parametern används för pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="76489-127">This parameter is used for pipeline input.</span></span>

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

### <span data-ttu-id="76489-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="76489-128">CommonParameters</span></span>

<span data-ttu-id="76489-129">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="76489-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="76489-130">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="76489-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="76489-131">INDATA</span><span class="sxs-lookup"><span data-stu-id="76489-131">INPUTS</span></span>

### <span data-ttu-id="76489-132">PSObject</span><span class="sxs-lookup"><span data-stu-id="76489-132">PSObject</span></span>

<span data-ttu-id="76489-133">Har stöd för inmatade från alla **PSObject**, men resultaten varierar om varken ett **ErrorRecord** -eller **Exception** -objekt anges.</span><span class="sxs-lookup"><span data-stu-id="76489-133">Supports input from any **PSObject**, but results vary unless either an **ErrorRecord** or **Exception** object are supplied.</span></span>

## <span data-ttu-id="76489-134">UTDATA</span><span class="sxs-lookup"><span data-stu-id="76489-134">OUTPUTS</span></span>

### <span data-ttu-id="76489-135">System. Management. Automation. ErrorRecord # PSExtendedError</span><span class="sxs-lookup"><span data-stu-id="76489-135">System.Management.Automation.ErrorRecord#PSExtendedError</span></span>

<span data-ttu-id="76489-136">Utdata i ett **PSExtendedError** -objekt.</span><span class="sxs-lookup"><span data-stu-id="76489-136">Output in a **PSExtendedError** object.</span></span>

## <span data-ttu-id="76489-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="76489-137">NOTES</span></span>

<span data-ttu-id="76489-138">`Get-Error` accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="76489-138">`Get-Error` accepts pipeline input.</span></span> <span data-ttu-id="76489-139">Ett exempel är `$Error | Get-Error`.</span><span class="sxs-lookup"><span data-stu-id="76489-139">For example, `$Error | Get-Error`.</span></span>

## <span data-ttu-id="76489-140">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="76489-140">RELATED LINKS</span></span>

[<span data-ttu-id="76489-141">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="76489-141">about_Try_Catch_Finally</span></span>](../Microsoft.PowerShell.Core/About/about_Try_Catch_Finally.md)
