---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-experimentalfeature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ExperimentalFeature
ms.openlocfilehash: e35e164f3116304efd52c71c1715ba70711f6253
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709612"
---
# <span data-ttu-id="e148f-102">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="e148f-102">Disable-ExperimentalFeature</span></span>

## <span data-ttu-id="e148f-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e148f-103">SYNOPSIS</span></span>
<span data-ttu-id="e148f-104">Inaktivera en experimentell funktion när du startar en ny instans av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e148f-104">Disable an experimental feature on startup of new instance of PowerShell.</span></span>

## <span data-ttu-id="e148f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e148f-105">SYNTAX</span></span>

```
Disable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e148f-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e148f-106">DESCRIPTION</span></span>

<span data-ttu-id="e148f-107">`Disable-ExperimentalFeature`Cmdleten inaktiverar experimentella funktioner genom att ta bort de namngivna experimentella funktionerna från `powershell.config.json` inställnings filen Läs på PowerShell-start.</span><span class="sxs-lookup"><span data-stu-id="e148f-107">The `Disable-ExperimentalFeature` cmdlet disables experimental features by removing the named experimental features from the `powershell.config.json` settings file read on PowerShell startup.</span></span>

<span data-ttu-id="e148f-108">Denna cmdlet introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="e148f-108">This cmdlet was introduced in PowerShell 6.2.</span></span>

> [!NOTE]
> <span data-ttu-id="e148f-109">Alla ändringar av experiment funktions läget börjar bara gälla vid omstart av PowerShell</span><span class="sxs-lookup"><span data-stu-id="e148f-109">Any changes to experimental feature state only takes effect on restart of PowerShell</span></span>

## <span data-ttu-id="e148f-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e148f-110">EXAMPLES</span></span>

### <span data-ttu-id="e148f-111">Exempel 1: inaktivera en experimentell funktion</span><span class="sxs-lookup"><span data-stu-id="e148f-111">Example 1: Disable an experimental feature</span></span>

<span data-ttu-id="e148f-112">I det här exemplet, om den här experimentella funktionen tidigare har Aktiver ATS, `powershell.config.json` uppdateras filen så att användaren inte aktiverar funktionen när PowerShell startas om.</span><span class="sxs-lookup"><span data-stu-id="e148f-112">In this example, if this experimental feature was previously enabled, then the `powershell.config.json` file is updated for the user to not enable that feature once PowerShell is restarted.</span></span>
<span data-ttu-id="e148f-113">När inget är klart skickas utdata till pipelinen och endast ett varnings meddelande visas.</span><span class="sxs-lookup"><span data-stu-id="e148f-113">Upon success nothing is output to the pipeline and only a warning message is displayed.</span></span>

```powershell
PS C:\> Disable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## <span data-ttu-id="e148f-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e148f-114">PARAMETERS</span></span>

### <span data-ttu-id="e148f-115">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e148f-115">-Confirm</span></span>

<span data-ttu-id="e148f-116">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e148f-116">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e148f-117">-Name</span><span class="sxs-lookup"><span data-stu-id="e148f-117">-Name</span></span>

<span data-ttu-id="e148f-118">Namn eller namn på de experimentella funktioner som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="e148f-118">The name or names of the experimental features to disable.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e148f-119">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="e148f-119">-Scope</span></span>

<span data-ttu-id="e148f-120">Bestämmer vilka som `powershell.config.json` ska uppdateras om det påverkar alla användare eller bara den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="e148f-120">Determines which `powershell.config.json` to update whether it affects all users or just the current user.</span></span>

```yaml
Type: System.Management.Automation.Configuration.ConfigScope
Parameter Sets: (All)
Aliases:
Accepted values: AllUsers, CurrentUser

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e148f-121">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e148f-121">-WhatIf</span></span>

<span data-ttu-id="e148f-122">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="e148f-122">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e148f-123">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="e148f-123">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e148f-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e148f-124">CommonParameters</span></span>

<span data-ttu-id="e148f-125">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e148f-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e148f-126">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e148f-126">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e148f-127">INDATA</span><span class="sxs-lookup"><span data-stu-id="e148f-127">INPUTS</span></span>

### <span data-ttu-id="e148f-128">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="e148f-128">ExperimentalFeature</span></span>

<span data-ttu-id="e148f-129">Pipe-instanser av ExperimentalFeature från `Get-ExperimentalFeature` cmdlet för att inaktivera.</span><span class="sxs-lookup"><span data-stu-id="e148f-129">Pipe instances of ExperimentalFeature from `Get-ExperimentalFeature` cmdlet to disable.</span></span>

## <span data-ttu-id="e148f-130">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e148f-130">OUTPUTS</span></span>

### <span data-ttu-id="e148f-131">Inga</span><span class="sxs-lookup"><span data-stu-id="e148f-131">None</span></span>

<span data-ttu-id="e148f-132">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e148f-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="e148f-133">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e148f-133">NOTES</span></span>

<span data-ttu-id="e148f-134">Ändringar av status för en experimentell funktion börjar bara gälla vid omstart av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e148f-134">Changes to state of an experimental feature only take effect on restart of PowerShell.</span></span>

## <span data-ttu-id="e148f-135">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e148f-135">RELATED LINKS</span></span>

[<span data-ttu-id="e148f-136">Aktivera – ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="e148f-136">Enable-ExperimentalFeature</span></span>](Enable-ExperimentalFeature.md)

[<span data-ttu-id="e148f-137">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="e148f-137">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

