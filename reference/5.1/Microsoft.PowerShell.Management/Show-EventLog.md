---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-EventLog
ms.openlocfilehash: e8dbcf1aa4280c0481714a8a9fb24f2e5ef79ffe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265371"
---
# <span data-ttu-id="15612-103">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="15612-103">Show-EventLog</span></span>

## <span data-ttu-id="15612-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="15612-104">SYNOPSIS</span></span>
<span data-ttu-id="15612-105">Visar händelse loggarna för den lokala datorn eller en fjärrdator i Loggboken.</span><span class="sxs-lookup"><span data-stu-id="15612-105">Displays the event logs of the local or a remote computer in Event Viewer.</span></span>

## <span data-ttu-id="15612-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="15612-106">SYNTAX</span></span>

```
Show-EventLog [[-ComputerName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="15612-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="15612-107">DESCRIPTION</span></span>
<span data-ttu-id="15612-108">Cmdleten **show-EventLog** öppnar Loggboken på den lokala datorn och visar den alla klassiska händelse loggar på den lokala datorn eller en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="15612-108">The **Show-EventLog** cmdlet opens Event Viewer on the local computer and displays in it all of the classic event logs on the local computer or a remote computer.</span></span>

<span data-ttu-id="15612-109">För att öppna Loggboken i Windows Vista och senare versioner av operativ systemet Windows måste den aktuella användaren vara medlem i gruppen Administratörer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="15612-109">To open Event Viewer on Windows Vista and later versions of the Windows operating system, the current user must be a member of the Administrators group on the local computer.</span></span>

<span data-ttu-id="15612-110">De cmdletar som innehåller **EventLog** -händelsen Substantiv ( **EventLog** -cmdletar) fungerar bara på klassiska händelse loggar.</span><span class="sxs-lookup"><span data-stu-id="15612-110">The cmdlets that contain the **EventLog** noun (the **EventLog** cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="15612-111">Om du vill hämta händelser från loggar som använder Windows händelse logg teknik i Windows Vista och senare versioner av Windows-operativsystemet, använder du Get-WinEvent-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="15612-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use the Get-WinEvent cmdlet.</span></span>

## <span data-ttu-id="15612-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="15612-112">EXAMPLES</span></span>

### <span data-ttu-id="15612-113">Exempel 1: Visa händelse loggar för den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="15612-113">Example 1: Display event logs for the local computer</span></span>

```
PS C:\> Show-EventLog
```

<span data-ttu-id="15612-114">Det här kommandot öppnar Loggboken och visar de klassiska händelse loggarna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="15612-114">This command opens Event Viewer and displays in it the classic event logs on the local computer.</span></span>

### <span data-ttu-id="15612-115">Exempel 2: Visa händelse loggar för en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="15612-115">Example 2: Display event logs for a remote computer</span></span>

```
PS C:\> Show-EventLog -ComputerName "Server01"
```

<span data-ttu-id="15612-116">Det här kommandot öppnar Loggboken och visar den klassiska händelse loggarna på den Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="15612-116">This command opens Event Viewer and displays in it the classic event logs on the Server01 computer.</span></span>

## <span data-ttu-id="15612-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="15612-117">PARAMETERS</span></span>

### <span data-ttu-id="15612-118">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="15612-118">-ComputerName</span></span>
<span data-ttu-id="15612-119">Anger en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="15612-119">Specifies a remote computer.</span></span>
<span data-ttu-id="15612-120">**Visa-EventLog** visar händelse loggarna från den angivna datorn i Loggboken på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="15612-120">**Show-EventLog** displays the event logs from the specified computer in Event Viewer on the local computer.</span></span>
<span data-ttu-id="15612-121">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="15612-121">The default is the local computer.</span></span>

<span data-ttu-id="15612-122">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="15612-122">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>

<span data-ttu-id="15612-123">Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="15612-123">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="15612-124">Du kan använda parametern *computername* även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="15612-124">You can use the *ComputerName* parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15612-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="15612-125">CommonParameters</span></span>
<span data-ttu-id="15612-126">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="15612-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="15612-127">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="15612-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="15612-128">INDATA</span><span class="sxs-lookup"><span data-stu-id="15612-128">INPUTS</span></span>

### <span data-ttu-id="15612-129">Inget</span><span class="sxs-lookup"><span data-stu-id="15612-129">None</span></span>
<span data-ttu-id="15612-130">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15612-130">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="15612-131">UTDATA</span><span class="sxs-lookup"><span data-stu-id="15612-131">OUTPUTS</span></span>

### <span data-ttu-id="15612-132">Inget</span><span class="sxs-lookup"><span data-stu-id="15612-132">None</span></span>
<span data-ttu-id="15612-133">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="15612-133">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="15612-134">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="15612-134">NOTES</span></span>

* <span data-ttu-id="15612-135">Kommando tolken för Windows PowerShell returneras så snart Loggboken öppnas.</span><span class="sxs-lookup"><span data-stu-id="15612-135">The Windows PowerShell command prompt returns as soon as Event Viewer opens.</span></span> <span data-ttu-id="15612-136">Du kan arbeta i den aktuella sessionen medan Loggboken är öppen.</span><span class="sxs-lookup"><span data-stu-id="15612-136">You can work in the current session while Event Viewer is open.</span></span>

  <span data-ttu-id="15612-137">Eftersom denna cmdlet kräver ett användar gränssnitt fungerar den inte på Server Core-installationer av Windows Server.</span><span class="sxs-lookup"><span data-stu-id="15612-137">Because this cmdlet requires a user interface, it does not work on Server Core installations of Windows Server.</span></span>

*

## <span data-ttu-id="15612-138">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="15612-138">RELATED LINKS</span></span>

[<span data-ttu-id="15612-139">Rensa-EventLog</span><span class="sxs-lookup"><span data-stu-id="15612-139">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="15612-140">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="15612-140">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="15612-141">Begränsning-EventLog</span><span class="sxs-lookup"><span data-stu-id="15612-141">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="15612-142">Ny-EventLog</span><span class="sxs-lookup"><span data-stu-id="15612-142">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="15612-143">Ta bort-EventLog</span><span class="sxs-lookup"><span data-stu-id="15612-143">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="15612-144">Skriv-EventLog</span><span class="sxs-lookup"><span data-stu-id="15612-144">Write-EventLog</span></span>](Write-EventLog.md)
