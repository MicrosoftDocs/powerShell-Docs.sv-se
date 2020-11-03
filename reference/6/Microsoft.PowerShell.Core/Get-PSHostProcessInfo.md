---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pshostprocessinfo?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSHostProcessInfo
ms.openlocfilehash: 24ebb507b2f9544115d6309b0a91d8b19b0745ec
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266643"
---
# <span data-ttu-id="56a3a-103">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="56a3a-103">Get-PSHostProcessInfo</span></span>

## <span data-ttu-id="56a3a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="56a3a-104">SYNOPSIS</span></span>
<span data-ttu-id="56a3a-105">Hämtar process information om PowerShell-värden.</span><span class="sxs-lookup"><span data-stu-id="56a3a-105">Gets process information about the PowerShell host.</span></span>

## <span data-ttu-id="56a3a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="56a3a-106">SYNTAX</span></span>

### <span data-ttu-id="56a3a-107">ProcessNameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="56a3a-107">ProcessNameParameterSet (Default)</span></span>

```
Get-PSHostProcessInfo [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="56a3a-108">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="56a3a-108">ProcessParameterSet</span></span>

```
Get-PSHostProcessInfo [-Process] <Process[]> [<CommonParameters>]
```

### <span data-ttu-id="56a3a-109">ProcessIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="56a3a-109">ProcessIdParameterSet</span></span>

```
Get-PSHostProcessInfo [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="56a3a-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="56a3a-110">DESCRIPTION</span></span>

<span data-ttu-id="56a3a-111">`Get-PSHostProcessInfo`Cmdleten hämtar information om PowerShell-värd processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="56a3a-111">The `Get-PSHostProcessInfo` cmdlet gets information about PowerShell host processes running on the local computer.</span></span>

<span data-ttu-id="56a3a-112">Från och med PowerShell 6,2 stöds denna cmdlet på plattformar som inte är Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="56a3a-112">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="56a3a-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="56a3a-113">EXAMPLES</span></span>

### <span data-ttu-id="56a3a-114">1: Hämta en lista över PowerShell-värdar som körs i systemet</span><span class="sxs-lookup"><span data-stu-id="56a3a-114">1: Get a list of PowerShell hosts running on the system</span></span>

```powershell
Get-PSHostProcessInfo
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell      11204 DefaultAppDomain
pwsh            13912 DefaultAppDomain
```

### <span data-ttu-id="56a3a-115">2: Hämta information om PowerShell-värden för ett enskilt process namn</span><span class="sxs-lookup"><span data-stu-id="56a3a-115">2: Get PowerShell host information for a specific process name</span></span>

```powershell
Get-PSHostProcessInfo -Name pwsh
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
pwsh            13912 DefaultAppDomain
```

## <span data-ttu-id="56a3a-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="56a3a-116">PARAMETERS</span></span>

### <span data-ttu-id="56a3a-117">-ID</span><span class="sxs-lookup"><span data-stu-id="56a3a-117">-Id</span></span>

<span data-ttu-id="56a3a-118">Anger en process med process-ID.</span><span class="sxs-lookup"><span data-stu-id="56a3a-118">Specifies a process by the process ID.</span></span> <span data-ttu-id="56a3a-119">Kör cmdleten för att hämta ett process-ID `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="56a3a-119">To get a process ID, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56a3a-120">-Name</span><span class="sxs-lookup"><span data-stu-id="56a3a-120">-Name</span></span>

<span data-ttu-id="56a3a-121">Anger en process efter process namnet.</span><span class="sxs-lookup"><span data-stu-id="56a3a-121">Specifies a process by the process name.</span></span> <span data-ttu-id="56a3a-122">Kör cmdleten för att få ett process namn `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="56a3a-122">To get a process name, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56a3a-123">– Process</span><span class="sxs-lookup"><span data-stu-id="56a3a-123">-Process</span></span>

<span data-ttu-id="56a3a-124">Anger en process av objektet process.</span><span class="sxs-lookup"><span data-stu-id="56a3a-124">Specifies a process by the process object.</span></span> <span data-ttu-id="56a3a-125">Det enklaste sättet att använda den här parametern är att spara resultatet av ett `Get-Process` kommando som returnerar en process som du vill ange i en variabel och sedan ange variabeln som värde för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="56a3a-125">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="56a3a-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="56a3a-126">CommonParameters</span></span>

<span data-ttu-id="56a3a-127">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="56a3a-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="56a3a-128">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="56a3a-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="56a3a-129">INDATA</span><span class="sxs-lookup"><span data-stu-id="56a3a-129">INPUTS</span></span>

### <span data-ttu-id="56a3a-130">System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="56a3a-130">System.Diagnostics.Process</span></span>

<span data-ttu-id="56a3a-131">Du kan skicka vidare ett **process** objekt från `Get-Process` till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="56a3a-131">You can pipe a **Process** object from `Get-Process` to this cmdlet.</span></span>

## <span data-ttu-id="56a3a-132">UTDATA</span><span class="sxs-lookup"><span data-stu-id="56a3a-132">OUTPUTS</span></span>

### <span data-ttu-id="56a3a-133">Microsoft. PowerShell. commands. PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="56a3a-133">Microsoft.PowerShell.Commands.PSHostProcessInfo</span></span>

## <span data-ttu-id="56a3a-134">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="56a3a-134">NOTES</span></span>

## <span data-ttu-id="56a3a-135">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="56a3a-135">RELATED LINKS</span></span>

[<span data-ttu-id="56a3a-136">Hämta process</span><span class="sxs-lookup"><span data-stu-id="56a3a-136">Get-Process</span></span>](../Microsoft.PowerShell.Management/get-process.md)
