---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pshostprocessinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSHostProcessInfo
ms.openlocfilehash: 6528d25ea706ac63927ef3d23cf661489caae8aa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709175"
---
# <span data-ttu-id="b7ab2-102">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="b7ab2-102">Get-PSHostProcessInfo</span></span>

## <span data-ttu-id="b7ab2-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b7ab2-103">SYNOPSIS</span></span>
<span data-ttu-id="b7ab2-104">Hämtar process information om PowerShell-värden.</span><span class="sxs-lookup"><span data-stu-id="b7ab2-104">Gets process information about the PowerShell host.</span></span>

## <span data-ttu-id="b7ab2-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b7ab2-105">SYNTAX</span></span>

### <span data-ttu-id="b7ab2-106">ProcessNameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="b7ab2-106">ProcessNameParameterSet (Default)</span></span>

```
Get-PSHostProcessInfo [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="b7ab2-107">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="b7ab2-107">ProcessParameterSet</span></span>

```
Get-PSHostProcessInfo [-Process] <Process[]> [<CommonParameters>]
```

### <span data-ttu-id="b7ab2-108">ProcessIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="b7ab2-108">ProcessIdParameterSet</span></span>

```
Get-PSHostProcessInfo [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="b7ab2-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b7ab2-109">DESCRIPTION</span></span>

<span data-ttu-id="b7ab2-110">`Get-PSHostProcessInfo`Cmdleten hämtar information om PowerShell-värd processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="b7ab2-110">The `Get-PSHostProcessInfo` cmdlet gets information about PowerShell host processes running on the local computer.</span></span>

<span data-ttu-id="b7ab2-111">Från och med PowerShell 6,2 stöds denna cmdlet på plattformar som inte är Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="b7ab2-111">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="b7ab2-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b7ab2-112">EXAMPLES</span></span>

### <span data-ttu-id="b7ab2-113">1: Hämta en lista över PowerShell-värdar som körs i systemet</span><span class="sxs-lookup"><span data-stu-id="b7ab2-113">1: Get a list of PowerShell hosts running on the system</span></span>

```powershell
Get-PSHostProcessInfo
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell      11204 DefaultAppDomain
pwsh            13912 DefaultAppDomain
```

### <span data-ttu-id="b7ab2-114">2: Hämta information om PowerShell-värden för ett enskilt process namn</span><span class="sxs-lookup"><span data-stu-id="b7ab2-114">2: Get PowerShell host information for a specific process name</span></span>

```powershell
Get-PSHostProcessInfo -Name pwsh
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
pwsh            13912 DefaultAppDomain
```

## <span data-ttu-id="b7ab2-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b7ab2-115">PARAMETERS</span></span>

### <span data-ttu-id="b7ab2-116">-ID</span><span class="sxs-lookup"><span data-stu-id="b7ab2-116">-Id</span></span>

<span data-ttu-id="b7ab2-117">Anger en process med process-ID.</span><span class="sxs-lookup"><span data-stu-id="b7ab2-117">Specifies a process by the process ID.</span></span> <span data-ttu-id="b7ab2-118">Kör cmdleten för att hämta ett process-ID `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="b7ab2-118">To get a process ID, run the `Get-Process` cmdlet.</span></span>

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

### <span data-ttu-id="b7ab2-119">-Name</span><span class="sxs-lookup"><span data-stu-id="b7ab2-119">-Name</span></span>

<span data-ttu-id="b7ab2-120">Anger en process efter process namnet.</span><span class="sxs-lookup"><span data-stu-id="b7ab2-120">Specifies a process by the process name.</span></span> <span data-ttu-id="b7ab2-121">Kör cmdleten för att få ett process namn `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="b7ab2-121">To get a process name, run the `Get-Process` cmdlet.</span></span>

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

### <span data-ttu-id="b7ab2-122">– Process</span><span class="sxs-lookup"><span data-stu-id="b7ab2-122">-Process</span></span>

<span data-ttu-id="b7ab2-123">Anger en process av objektet process.</span><span class="sxs-lookup"><span data-stu-id="b7ab2-123">Specifies a process by the process object.</span></span> <span data-ttu-id="b7ab2-124">Det enklaste sättet att använda den här parametern är att spara resultatet av ett `Get-Process` kommando som returnerar en process som du vill ange i en variabel och sedan ange variabeln som värde för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="b7ab2-124">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

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

### <span data-ttu-id="b7ab2-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b7ab2-125">CommonParameters</span></span>

<span data-ttu-id="b7ab2-126">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b7ab2-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b7ab2-127">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b7ab2-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b7ab2-128">INDATA</span><span class="sxs-lookup"><span data-stu-id="b7ab2-128">INPUTS</span></span>

### <span data-ttu-id="b7ab2-129">System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="b7ab2-129">System.Diagnostics.Process</span></span>

<span data-ttu-id="b7ab2-130">Du kan skicka vidare ett **process** objekt från `Get-Process` till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b7ab2-130">You can pipe a **Process** object from `Get-Process` to this cmdlet.</span></span>

## <span data-ttu-id="b7ab2-131">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b7ab2-131">OUTPUTS</span></span>

### <span data-ttu-id="b7ab2-132">Microsoft. PowerShell. commands. PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="b7ab2-132">Microsoft.PowerShell.Commands.PSHostProcessInfo</span></span>

## <span data-ttu-id="b7ab2-133">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b7ab2-133">NOTES</span></span>

## <span data-ttu-id="b7ab2-134">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b7ab2-134">RELATED LINKS</span></span>

[<span data-ttu-id="b7ab2-135">Hämta process</span><span class="sxs-lookup"><span data-stu-id="b7ab2-135">Get-Process</span></span>](../Microsoft.PowerShell.Management/get-process.md)

