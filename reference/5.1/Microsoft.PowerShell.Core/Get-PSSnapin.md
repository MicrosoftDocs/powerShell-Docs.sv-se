---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSnapin
ms.openlocfilehash: 156cadecd87910e3c3312e84929b16709770641d
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388679"
---
# <span data-ttu-id="ebfef-103">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="ebfef-103">Get-PSSnapin</span></span>

## <span data-ttu-id="ebfef-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ebfef-104">SYNOPSIS</span></span>
<span data-ttu-id="ebfef-105">Hämtar snapin-moduler för Windows PowerShell på datorn.</span><span class="sxs-lookup"><span data-stu-id="ebfef-105">Gets the Windows PowerShell snap-ins on the computer.</span></span>

## <span data-ttu-id="ebfef-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ebfef-106">SYNTAX</span></span>

```
Get-PSSnapin [[-Name] <String[]>] [-Registered] [<CommonParameters>]
```

## <span data-ttu-id="ebfef-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ebfef-107">DESCRIPTION</span></span>

<span data-ttu-id="ebfef-108">`Get-PSSnapin`Cmdlet: en hämtar Windows PowerShell-snapin-modulerna som har lagts till i den aktuella sessionen eller som har registrerats i systemet.</span><span class="sxs-lookup"><span data-stu-id="ebfef-108">The `Get-PSSnapin` cmdlet gets the Windows PowerShell snap-ins that have been added to the current session or that have been registered on the system.</span></span> <span data-ttu-id="ebfef-109">Denna cmdlet listar snapin-modulerna i den ordning som de identifieras.</span><span class="sxs-lookup"><span data-stu-id="ebfef-109">This cmdlet lists the snap-ins in the order in which they are detected.</span></span>

<span data-ttu-id="ebfef-110">`Get-PSSnapin` hämtar endast registrerade snapin-moduler. Om du vill registrera en Windows PowerShell-snapin-modul använder du InstallUtil-verktyget som ingår i Microsoft .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="ebfef-110">`Get-PSSnapin` gets only registered snap-ins. To register a Windows PowerShell snap-in, use the InstallUtil tool included with the Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="ebfef-111">Mer information finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="ebfef-111">For more information, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

<span data-ttu-id="ebfef-112">Från och med Windows PowerShell 3,0 paketeras de grundläggande kommandon som ingår i Windows PowerShell i moduler.</span><span class="sxs-lookup"><span data-stu-id="ebfef-112">Starting in Windows PowerShell 3.0, the core commands that are included in Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="ebfef-113">Undantaget är **Microsoft. PowerShell. Core** , som är en snapin-modul (PSSnapin).</span><span class="sxs-lookup"><span data-stu-id="ebfef-113">The exception is **Microsoft.PowerShell.Core** , which is a snap-in (PSSnapin).</span></span>
<span data-ttu-id="ebfef-114">Som standard läggs bara snapin-modulen **Microsoft. PowerShell. Core** till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ebfef-114">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span> <span data-ttu-id="ebfef-115">Moduler importeras automatiskt vid första användningen och du kan använda `Import-Module` cmdleten för att importera dem.</span><span class="sxs-lookup"><span data-stu-id="ebfef-115">Modules are imported automatically on first use and you can use the `Import-Module` cmdlet to import them.</span></span>

## <span data-ttu-id="ebfef-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ebfef-116">EXAMPLES</span></span>

### <span data-ttu-id="ebfef-117">Exempel 1: Hämta snapin-moduler som är inlästa för tillfället</span><span class="sxs-lookup"><span data-stu-id="ebfef-117">Example 1: Get snap-ins that are currently loaded</span></span>

```
PS C:\> Get-PSSnapIn
```

<span data-ttu-id="ebfef-118">Det här kommandot hämtar Windows PowerShell-snapin-modulerna som för närvarande läses in i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ebfef-118">This command gets the Windows PowerShell snap-ins that are currently loaded in the session.</span></span> <span data-ttu-id="ebfef-119">Detta inkluderar snapin-modulerna som installeras med Windows PowerShell och de som har lagts till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ebfef-119">This includes the snap-ins that are installed with Windows PowerShell and those that have been added to the session.</span></span>

### <span data-ttu-id="ebfef-120">Exempel 2: Hämta snapin-moduler som har registrerats</span><span class="sxs-lookup"><span data-stu-id="ebfef-120">Example 2: Get snap-ins that have been registered</span></span>

```
PS C:\> get-PSSnapIn -Registered
```

<span data-ttu-id="ebfef-121">Det här kommandot hämtar Windows PowerShell-snapin-modulerna som har registrerats på datorn, inklusive de som redan har lagts till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ebfef-121">This command gets the Windows PowerShell snap-ins that have been registered on the computer, including those that have already been added to the session.</span></span> <span data-ttu-id="ebfef-122">Utdata inkluderar inte snapin-moduler som installeras med Windows PowerShell eller Windows PowerShell-snapin-modulen dll: er (Dynamic-Link Libraries) som ännu inte har registrerats i systemet.</span><span class="sxs-lookup"><span data-stu-id="ebfef-122">The output does not include snap-ins that are installed with Windows PowerShell or Windows PowerShell snap-in dynamic-link libraries (DLLs) that have not yet been registered on the system.</span></span>

### <span data-ttu-id="ebfef-123">Exempel 3: hämta aktuella snapin-moduler som matchar en sträng</span><span class="sxs-lookup"><span data-stu-id="ebfef-123">Example 3: Get current snap-ins that match a string</span></span>

```
PS C:\> Get-PSSnapIn -Name smp*
```

<span data-ttu-id="ebfef-124">Det här kommandot hämtar Windows PowerShell-snapin-modulerna i den aktuella sessionen med namn som börjar med SMP.</span><span class="sxs-lookup"><span data-stu-id="ebfef-124">This command gets the Windows PowerShell snap-ins in the current session that have names that begin with smp.</span></span>

## <span data-ttu-id="ebfef-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ebfef-125">PARAMETERS</span></span>

### <span data-ttu-id="ebfef-126">-Name</span><span class="sxs-lookup"><span data-stu-id="ebfef-126">-Name</span></span>

<span data-ttu-id="ebfef-127">Anger en matris med namn på snapin-modulen.</span><span class="sxs-lookup"><span data-stu-id="ebfef-127">Specifies an array of snap-in names.</span></span> <span data-ttu-id="ebfef-128">Denna cmdlet hämtar bara de angivna Windows PowerShell-snapin-modulerna. Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="ebfef-128">This cmdlet gets only the specified Windows PowerShell snap-ins. Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ebfef-129">-Registrerad</span><span class="sxs-lookup"><span data-stu-id="ebfef-129">-Registered</span></span>

<span data-ttu-id="ebfef-130">Anger att den här cmdlet: en hämtar Windows PowerShell-snapin-modulerna som har registrerats i systemet även om de ännu inte har lagts till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ebfef-130">Indicates that this cmdlet gets the Windows PowerShell snap-ins that have been registered on the system even if they have not yet been added to the session.</span></span>

<span data-ttu-id="ebfef-131">Snapin-modulerna som installeras med Windows PowerShell visas inte i den här listan.</span><span class="sxs-lookup"><span data-stu-id="ebfef-131">The snap-ins that are installed with Windows PowerShell do not appear in this list.</span></span>

<span data-ttu-id="ebfef-132">Utan den här parametern `Get-PSSnapin` hämtar Windows PowerShell-snapin-modulerna som har lagts till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ebfef-132">Without this parameter, `Get-PSSnapin` gets the Windows PowerShell snap-ins that have been added to the session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ebfef-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ebfef-133">CommonParameters</span></span>

<span data-ttu-id="ebfef-134">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ebfef-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ebfef-135">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ebfef-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ebfef-136">INDATA</span><span class="sxs-lookup"><span data-stu-id="ebfef-136">INPUTS</span></span>

### <span data-ttu-id="ebfef-137">Inget</span><span class="sxs-lookup"><span data-stu-id="ebfef-137">None</span></span>
<span data-ttu-id="ebfef-138">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ebfef-138">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="ebfef-139">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ebfef-139">OUTPUTS</span></span>

### <span data-ttu-id="ebfef-140">System. Management. Automation. PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="ebfef-140">System.Management.Automation.PSSnapInInfo</span></span>

<span data-ttu-id="ebfef-141">`Get-PSSnapin` Returnerar ett objekt för varje snapin-modul som det får.</span><span class="sxs-lookup"><span data-stu-id="ebfef-141">`Get-PSSnapin` returns an object for each snap-in that it gets.</span></span>

## <span data-ttu-id="ebfef-142">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ebfef-142">NOTES</span></span>

<span data-ttu-id="ebfef-143">Från och med Windows PowerShell 3,0 paketeras de grundläggande kommandon som installeras med Windows PowerShell i moduler.</span><span class="sxs-lookup"><span data-stu-id="ebfef-143">Starting in Windows PowerShell 3.0, the core commands that are installed with Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="ebfef-144">I Windows PowerShell 2,0 och i värd program som skapar äldre sessioner i senare versioner av Windows PowerShell är huvud kommandona förpackade i snapin-moduler ( **PSSnapin** ).</span><span class="sxs-lookup"><span data-stu-id="ebfef-144">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of Windows PowerShell, the core commands are packaged in snap-ins ( **PSSnapin** ).</span></span> <span data-ttu-id="ebfef-145">Undantaget är **Microsoft. PowerShell. Core** , som alltid är en snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="ebfef-145">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="ebfef-146">Fjärrsessioner, till exempel de som startas av `New-PSSession` cmdleten, är äldre sessioner som inkluderar grundläggande snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="ebfef-146">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

 <span data-ttu-id="ebfef-147">Information om **CreateDefault2** -metoden som skapar nyare sessioner med Core-moduler finns i CreateDefault2- [metoden](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2).</span><span class="sxs-lookup"><span data-stu-id="ebfef-147">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2).</span></span>

## <span data-ttu-id="ebfef-148">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ebfef-148">RELATED LINKS</span></span>

[<span data-ttu-id="ebfef-149">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="ebfef-149">Add-PSSnapin</span></span>](Add-PSSnapin.md)

[<span data-ttu-id="ebfef-150">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="ebfef-150">Remove-PSSnapin</span></span>](Remove-PSSnapin.md)
