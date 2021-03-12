---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-experimentalfeature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ExperimentalFeature
ms.openlocfilehash: 47cae5d0c3ddd1800e5a8ae33282677773dc50d5
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195162"
---
# <span data-ttu-id="175ff-102">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="175ff-102">Disable-ExperimentalFeature</span></span>

## <span data-ttu-id="175ff-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="175ff-103">SYNOPSIS</span></span>
<span data-ttu-id="175ff-104">Inaktivera en experimentell funktion när du startar en ny instans av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="175ff-104">Disable an experimental feature on startup of new instance of PowerShell.</span></span>

## <span data-ttu-id="175ff-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="175ff-105">SYNTAX</span></span>

```
Disable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="175ff-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="175ff-106">DESCRIPTION</span></span>

<span data-ttu-id="175ff-107">`Disable-ExperimentalFeature`Cmdleten inaktiverar experimentella funktioner genom att ta bort de namngivna experimentella funktionerna från `powershell.config.json` inställnings filen Läs på PowerShell-start.</span><span class="sxs-lookup"><span data-stu-id="175ff-107">The `Disable-ExperimentalFeature` cmdlet disables experimental features by removing the named experimental features from the `powershell.config.json` settings file read on PowerShell startup.</span></span>

<span data-ttu-id="175ff-108">Denna cmdlet introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="175ff-108">This cmdlet was introduced in PowerShell 6.2.</span></span>

> [!NOTE]
> <span data-ttu-id="175ff-109">Alla ändringar av experiment funktions läget börjar bara gälla vid omstart av PowerShell</span><span class="sxs-lookup"><span data-stu-id="175ff-109">Any changes to experimental feature state only takes effect on restart of PowerShell</span></span>

## <span data-ttu-id="175ff-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="175ff-110">EXAMPLES</span></span>

### <span data-ttu-id="175ff-111">Exempel 1: inaktivera en experimentell funktion</span><span class="sxs-lookup"><span data-stu-id="175ff-111">Example 1: Disable an experimental feature</span></span>

<span data-ttu-id="175ff-112">I det här exemplet, om den här experimentella funktionen tidigare har Aktiver ATS, `powershell.config.json` uppdateras filen så att användaren inte aktiverar funktionen när PowerShell startas om.</span><span class="sxs-lookup"><span data-stu-id="175ff-112">In this example, if this experimental feature was previously enabled, then the `powershell.config.json` file is updated for the user to not enable that feature once PowerShell is restarted.</span></span>
<span data-ttu-id="175ff-113">När inget är klart skickas utdata till pipelinen och endast ett varnings meddelande visas.</span><span class="sxs-lookup"><span data-stu-id="175ff-113">Upon success nothing is output to the pipeline and only a warning message is displayed.</span></span>

```powershell
PS C:\> Disable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## <span data-ttu-id="175ff-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="175ff-114">PARAMETERS</span></span>

### <span data-ttu-id="175ff-115">-Confirm</span><span class="sxs-lookup"><span data-stu-id="175ff-115">-Confirm</span></span>

<span data-ttu-id="175ff-116">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="175ff-116">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="175ff-117">-Name</span><span class="sxs-lookup"><span data-stu-id="175ff-117">-Name</span></span>

<span data-ttu-id="175ff-118">Namn eller namn på de experimentella funktioner som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="175ff-118">The name or names of the experimental features to disable.</span></span>

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

### <span data-ttu-id="175ff-119">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="175ff-119">-Scope</span></span>

<span data-ttu-id="175ff-120">Bestämmer vilka som `powershell.config.json` ska uppdateras om det påverkar alla användare eller bara den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="175ff-120">Determines which `powershell.config.json` to update whether it affects all users or just the current user.</span></span>

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

### <span data-ttu-id="175ff-121">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="175ff-121">-WhatIf</span></span>

<span data-ttu-id="175ff-122">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="175ff-122">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="175ff-123">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="175ff-123">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="175ff-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="175ff-124">CommonParameters</span></span>

<span data-ttu-id="175ff-125">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="175ff-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="175ff-126">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="175ff-126">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="175ff-127">INDATA</span><span class="sxs-lookup"><span data-stu-id="175ff-127">INPUTS</span></span>

### <span data-ttu-id="175ff-128">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="175ff-128">ExperimentalFeature</span></span>

<span data-ttu-id="175ff-129">Pipe-instanser av ExperimentalFeature från `Get-ExperimentalFeature` cmdlet för att inaktivera.</span><span class="sxs-lookup"><span data-stu-id="175ff-129">Pipe instances of ExperimentalFeature from `Get-ExperimentalFeature` cmdlet to disable.</span></span>

## <span data-ttu-id="175ff-130">UTDATA</span><span class="sxs-lookup"><span data-stu-id="175ff-130">OUTPUTS</span></span>

### <span data-ttu-id="175ff-131">Inget</span><span class="sxs-lookup"><span data-stu-id="175ff-131">None</span></span>

<span data-ttu-id="175ff-132">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="175ff-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="175ff-133">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="175ff-133">NOTES</span></span>

<span data-ttu-id="175ff-134">Ändringar av status för en experimentell funktion börjar bara gälla vid omstart av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="175ff-134">Changes to state of an experimental feature only take effect on restart of PowerShell.</span></span>

## <span data-ttu-id="175ff-135">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="175ff-135">RELATED LINKS</span></span>

[<span data-ttu-id="175ff-136">Aktivera – ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="175ff-136">Enable-ExperimentalFeature</span></span>](Enable-ExperimentalFeature.md)

[<span data-ttu-id="175ff-137">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="175ff-137">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

