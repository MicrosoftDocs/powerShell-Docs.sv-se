---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/13/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerrestorepoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerRestorePoint
ms.openlocfilehash: 73819aafee9ed1911354daf9af23eedff0a3e14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266169"
---
# <span data-ttu-id="cd3f5-103">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="cd3f5-103">Get-ComputerRestorePoint</span></span>

## <span data-ttu-id="cd3f5-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="cd3f5-104">SYNOPSIS</span></span>
<span data-ttu-id="cd3f5-105">Hämtar återställnings punkterna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-105">Gets the restore points on the local computer.</span></span>

## <span data-ttu-id="cd3f5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cd3f5-106">SYNTAX</span></span>

### <span data-ttu-id="cd3f5-107">ID (standard)</span><span class="sxs-lookup"><span data-stu-id="cd3f5-107">ID (Default)</span></span>

```
Get-ComputerRestorePoint [[-RestorePoint] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="cd3f5-108">LastStatus</span><span class="sxs-lookup"><span data-stu-id="cd3f5-108">LastStatus</span></span>

```
Get-ComputerRestorePoint -LastStatus [<CommonParameters>]
```

## <span data-ttu-id="cd3f5-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cd3f5-109">DESCRIPTION</span></span>

<span data-ttu-id="cd3f5-110">`Get-ComputerRestorePoint`Cmdlet: en hämtar system återställnings punkter för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-110">The `Get-ComputerRestorePoint` cmdlet gets the local computer's system restore points.</span></span> <span data-ttu-id="cd3f5-111">Och kan visa status för det senaste försöket att återställa datorn.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-111">And, it can display the status of the most recent attempt to restore the computer.</span></span>

<span data-ttu-id="cd3f5-112">Du kan använda informationen från `Get-ComputerRestorePoint` för att välja en återställnings punkt.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-112">You can use the information from `Get-ComputerRestorePoint` to select a restore point.</span></span> <span data-ttu-id="cd3f5-113">Du kan till exempel använda ett ordnings nummer för att identifiera en återställnings punkt för `Restore-Computer` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-113">For example, use a sequence number to identify a restore point for the `Restore-Computer` cmdlet.</span></span>

<span data-ttu-id="cd3f5-114">System återställnings punkter och `Get-ComputerRestorePoint` cmdlet stöds endast på klient operativ system som Windows 10, Windows 7, Windows Vista och Windows XP.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-114">System restore points and the `Get-ComputerRestorePoint` cmdlet are supported only on client operating systems such as Windows 10, Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="cd3f5-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="cd3f5-115">EXAMPLES</span></span>

### <span data-ttu-id="cd3f5-116">Exempel 1: Hämta alla system återställnings punkter</span><span class="sxs-lookup"><span data-stu-id="cd3f5-116">Example 1: Get all system restore points</span></span>

<span data-ttu-id="cd3f5-117">I det här exemplet `Get-ComputerRestorePoint` hämtar alla system återställnings punkter för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-117">In this example, `Get-ComputerRestorePoint` gets all the local computer's system restore points.</span></span>

```powershell
Get-ComputerRestorePoint
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
8/7/2019  12:56:45     Installed PowerShell 6-x64     6                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

### <span data-ttu-id="cd3f5-118">Exempel 2: hämta vissa ordnings nummer</span><span class="sxs-lookup"><span data-stu-id="cd3f5-118">Example 2: Get specific sequence numbers</span></span>

<span data-ttu-id="cd3f5-119">Det här exemplet hämtar system återställnings punkter för vissa sekvensnummer.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-119">This example gets system restore points for specific sequence numbers.</span></span>

```powershell
Get-ComputerRestorePoint -RestorePoint 4, 5
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

<span data-ttu-id="cd3f5-120">`Get-ComputerRestorePoint` använder parametern **RestorePoint** för att ange en kommaavgränsad matris med sekvensnummer.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-120">`Get-ComputerRestorePoint` uses the **RestorePoint** parameter to specify a comma-separated array of sequence numbers.</span></span>

### <span data-ttu-id="cd3f5-121">Exempel 3: Visa status för en system återställning</span><span class="sxs-lookup"><span data-stu-id="cd3f5-121">Example 3: Display the status of a system restore</span></span>

<span data-ttu-id="cd3f5-122">I det här exemplet visas statusen för den senaste system återställningen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-122">This example displays the status of the most recent system restore on the local computer.</span></span>

```powershell
Get-ComputerRestorePoint -LastStatus
```

```Output
The last attempt to restore the computer failed.
```

<span data-ttu-id="cd3f5-123">`Get-ComputerRestorePoint` använder parametern **LastStatus** för att visa resultatet av den senaste system återställningen.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-123">`Get-ComputerRestorePoint` uses the **LastStatus** parameter to display the result of the most recent system restore.</span></span>

### <span data-ttu-id="cd3f5-124">Exempel 4: Använd ett uttryck för att konvertera CreationTime</span><span class="sxs-lookup"><span data-stu-id="cd3f5-124">Example 4: Use an expression to convert the CreationTime</span></span>

<span data-ttu-id="cd3f5-125">`Get-ComputerRestorePoint` matar ut **CreationTime** som en Windows Management INSTRUMENTATION (WMI)-datum-och tids sträng.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-125">`Get-ComputerRestorePoint` outputs the **CreationTime** as a Windows Management Instrumentation (WMI) date and time string.</span></span>

<span data-ttu-id="cd3f5-126">I det här exemplet lagrar en variabel ett uttryck som konverterar **CreationTime** -strängen till ett **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-126">In this example, a variable stores an expression that converts the **CreationTime** string to a **DateTime** object.</span></span> <span data-ttu-id="cd3f5-127">Om du vill visa **CreationTime** -strängar innan de konverteras, använder du ett kommando som `((Get-ComputerRestorePoint).CreationTime)` .</span><span class="sxs-lookup"><span data-stu-id="cd3f5-127">To view **CreationTime** strings before they're converted, use a command such as `((Get-ComputerRestorePoint).CreationTime)`.</span></span> <span data-ttu-id="cd3f5-128">Mer information om WMI-datum och tids sträng finns [CIM_DATETIME](/windows/win32/wmisdk/cim-datetime).</span><span class="sxs-lookup"><span data-stu-id="cd3f5-128">For more information about the WMI date and time string, see [CIM_DATETIME](/windows/win32/wmisdk/cim-datetime).</span></span>

```powershell
$date = @{Label="Date"; Expression={$_.ConvertToDateTime($_.CreationTime)}}
Get-ComputerRestorePoint | Select-Object -Property SequenceNumber, $date, Description
```

```Output
SequenceNumber   Date                 Description
--------------   ----                 -----------
             4   7/30/2019 09:17:24   Windows Update
             5   8/5/2019  08:15:37   Installed PowerShell 7-preview-x64
             6   8/7/2019  12:56:45   Installed PowerShell 6-x64
```

<span data-ttu-id="cd3f5-129">`$date`Variabeln lagrar en hash-tabell med uttrycket som använder metoden **ConvertToDateTime** .</span><span class="sxs-lookup"><span data-stu-id="cd3f5-129">The `$date` variable stores a hash table with the expression that uses the **ConvertToDateTime** method.</span></span> <span data-ttu-id="cd3f5-130">Uttrycket konverterar **CreationTime** -egenskapens värde från en WMI-sträng till ett **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-130">The expression converts the **CreationTime** property's value from a WMI string to a **DateTime** object.</span></span>

<span data-ttu-id="cd3f5-131">`Get-ComputerRestorePoint` skickar system återställnings punkts objekt nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-131">`Get-ComputerRestorePoint` sends the system restore point objects down the pipeline.</span></span> <span data-ttu-id="cd3f5-132">`Select-Object` använder **egenskaps** parametern för att ange vilka egenskaper som ska visas.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-132">`Select-Object` uses the **Property** parameter to specify the properties to display.</span></span> <span data-ttu-id="cd3f5-133">För varje objekt i pipelinen konverterar uttrycket i `$date` **CreationTime** och matar ut resultatet i egenskapen **date** .</span><span class="sxs-lookup"><span data-stu-id="cd3f5-133">For each object in the pipeline, the expression in `$date` converts the **CreationTime** and outputs the result in the **Date** property.</span></span>

### <span data-ttu-id="cd3f5-134">Exempel 5: Använd en egenskap för att hämta ett sekvensnummer</span><span class="sxs-lookup"><span data-stu-id="cd3f5-134">Example 5: Use a property to get a sequence number</span></span>

<span data-ttu-id="cd3f5-135">Det här exemplet hämtar ett sekvensnummer med hjälp av egenskapen **SequenceNumber** och ett mat ris index.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-135">This example gets a sequence number by using the **SequenceNumber** property and an array index.</span></span> <span data-ttu-id="cd3f5-136">Utdata innehåller bara sekvensnumret.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-136">The output only contains the sequence number.</span></span>

```powershell
((Get-ComputerRestorePoint).SequenceNumber)[-1]
```

```Output
6
```

<span data-ttu-id="cd3f5-137">`Get-ComputerRestorePoint` använder egenskapen **SequenceNumber** med ett mat ris index.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-137">`Get-ComputerRestorePoint` uses the **SequenceNumber** property with an array index.</span></span> <span data-ttu-id="cd3f5-138">Mat ris indexet för `-1` hämtar det senaste sekvensnumret i matrisen.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-138">The array index of `-1` gets the most recent sequence number in the array.</span></span>

## <span data-ttu-id="cd3f5-139">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="cd3f5-139">PARAMETERS</span></span>

### <span data-ttu-id="cd3f5-140">-LastStatus</span><span class="sxs-lookup"><span data-stu-id="cd3f5-140">-LastStatus</span></span>

<span data-ttu-id="cd3f5-141">Anger att `Get-ComputerRestorePoint` hämtar status för den senaste system återställnings åtgärden.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-141">Indicates that `Get-ComputerRestorePoint` gets the status of the most recent system restore operation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LastStatus
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd3f5-142">-RestorePoint</span><span class="sxs-lookup"><span data-stu-id="cd3f5-142">-RestorePoint</span></span>

<span data-ttu-id="cd3f5-143">Anger system återställnings punkternas ordnings nummer.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-143">Specifies the sequence numbers of the system restore points.</span></span> <span data-ttu-id="cd3f5-144">Du kan ange antingen ett enda sekvensnummer eller en kommaavgränsad matris med sekvensnummer.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-144">You can specify either a single sequence number or a comma-separated array of sequence numbers.</span></span>

<span data-ttu-id="cd3f5-145">Om parametern **RestorePoint** inte anges `Get-ComputerRestorePoint` returnerar alla system återställnings punkter för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-145">If the **RestorePoint** parameter isn't specified, `Get-ComputerRestorePoint` returns all the local computer's system restore points.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: ID
Aliases:

Required: False
Position: 0
Default value: All restore points
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd3f5-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cd3f5-146">CommonParameters</span></span>

<span data-ttu-id="cd3f5-147">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cd3f5-148">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cd3f5-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cd3f5-149">INDATA</span><span class="sxs-lookup"><span data-stu-id="cd3f5-149">INPUTS</span></span>

### <span data-ttu-id="cd3f5-150">Inget</span><span class="sxs-lookup"><span data-stu-id="cd3f5-150">None</span></span>

<span data-ttu-id="cd3f5-151">Du kan inte skicka objekt nedåt i pipelinen till `Get-ComputerRestorePoint` .</span><span class="sxs-lookup"><span data-stu-id="cd3f5-151">You can't send objects down the pipeline to `Get-ComputerRestorePoint`.</span></span>

## <span data-ttu-id="cd3f5-152">UTDATA</span><span class="sxs-lookup"><span data-stu-id="cd3f5-152">OUTPUTS</span></span>

### <span data-ttu-id="cd3f5-153">System. Management. ManagementObject # root\default\SystemRestore eller string</span><span class="sxs-lookup"><span data-stu-id="cd3f5-153">System.Management.ManagementObject#root\default\SystemRestore or String</span></span>

<span data-ttu-id="cd3f5-154">`Get-ComputerRestorePoint` Returnerar ett **SystemRestore** -objekt, som är en instans av **SystemRestore** -klassen (Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="cd3f5-154">`Get-ComputerRestorePoint` returns a **SystemRestore** object, which is an instance of the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

<span data-ttu-id="cd3f5-155">När du använder parametern **LastStatus** `Get-ComputerRestorePoint` returneras en sträng.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-155">When you use the **LastStatus** parameter, `Get-ComputerRestorePoint` returns a string.</span></span>

## <span data-ttu-id="cd3f5-156">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="cd3f5-156">NOTES</span></span>

<span data-ttu-id="cd3f5-157">Om du vill köra ett `Get-ComputerRestorePoint` kommando i Windows Vista och senare versioner av Windows öppnar du PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="cd3f5-157">To run a `Get-ComputerRestorePoint` command on Windows Vista and later versions of Windows, open PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="cd3f5-158">`Get-ComputerRestorePoint` använder WMI- **SystemRestore** -klassen.</span><span class="sxs-lookup"><span data-stu-id="cd3f5-158">`Get-ComputerRestorePoint` uses the WMI **SystemRestore** class.</span></span>

## <span data-ttu-id="cd3f5-159">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="cd3f5-159">RELATED LINKS</span></span>

[<span data-ttu-id="cd3f5-160">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="cd3f5-160">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="cd3f5-161">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="cd3f5-161">about_Arrays</span></span>](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[<span data-ttu-id="cd3f5-162">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="cd3f5-162">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="cd3f5-163">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="cd3f5-163">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="cd3f5-164">Aktivera – ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="cd3f5-164">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="cd3f5-165">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="cd3f5-165">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="cd3f5-166">Återställa-dator</span><span class="sxs-lookup"><span data-stu-id="cd3f5-166">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="cd3f5-167">SystemRestore</span><span class="sxs-lookup"><span data-stu-id="cd3f5-167">SystemRestore</span></span>](/windows/win32/sr/systemrestore)
