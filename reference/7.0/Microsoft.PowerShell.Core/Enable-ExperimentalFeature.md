---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-experimentalfeature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ExperimentalFeature
ms.openlocfilehash: 79884c73bc6e010eb218f1b722d26e0aaa05ef53
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262851"
---
# <span data-ttu-id="88c7a-102">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="88c7a-102">Enable-ExperimentalFeature</span></span>

## <span data-ttu-id="88c7a-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="88c7a-103">SYNOPSIS</span></span>
<span data-ttu-id="88c7a-104">Aktivera en experimentell funktion när du startar en ny instans av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88c7a-104">Enable an experimental feature on startup of new instance of PowerShell.</span></span>

## <span data-ttu-id="88c7a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="88c7a-105">SYNTAX</span></span>

```
Enable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="88c7a-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="88c7a-106">DESCRIPTION</span></span>

<span data-ttu-id="88c7a-107">`Enable-ExperimentalFeature`Cmdleten aktiverar experimentella funktioner genom att lägga till de namngivna experimentella funktionerna i `powershell.config.json` inställnings filen Läs på PowerShell-start.</span><span class="sxs-lookup"><span data-stu-id="88c7a-107">The `Enable-ExperimentalFeature` cmdlet enables experimental features by adding the named experimental features to the `powershell.config.json` settings file read on PowerShell startup.</span></span>

<span data-ttu-id="88c7a-108">Denna cmdlet introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="88c7a-108">This cmdlet was introduced in PowerShell 6.2.</span></span>

> [!NOTE]
> <span data-ttu-id="88c7a-109">Alla ändringar av experiment funktions läget börjar bara gälla vid omstart av PowerShell</span><span class="sxs-lookup"><span data-stu-id="88c7a-109">Any changes to experimental feature state only takes effect on restart of PowerShell</span></span>

## <span data-ttu-id="88c7a-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="88c7a-110">EXAMPLES</span></span>

### <span data-ttu-id="88c7a-111">Exempel 1: Aktivera en experimentell funktion</span><span class="sxs-lookup"><span data-stu-id="88c7a-111">Example 1: Enable an experimental feature</span></span>

<span data-ttu-id="88c7a-112">I det här exemplet, om den här experimentella funktionen tidigare har inaktiverats, `powershell.config.json` uppdateras filen för att användaren ska kunna aktivera funktionen när PowerShell startas om.</span><span class="sxs-lookup"><span data-stu-id="88c7a-112">In this example, if this experimental feature was previously disabled, then the `powershell.config.json` file is updated for the user to enable that feature once PowerShell is restarted.</span></span>
<span data-ttu-id="88c7a-113">När inget är klart skickas utdata till pipelinen och endast ett varnings meddelande visas.</span><span class="sxs-lookup"><span data-stu-id="88c7a-113">Upon success nothing is output to the pipeline and only a warning message is displayed.</span></span>

```powershell
Enable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## <span data-ttu-id="88c7a-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="88c7a-114">PARAMETERS</span></span>

### <span data-ttu-id="88c7a-115">-Confirm</span><span class="sxs-lookup"><span data-stu-id="88c7a-115">-Confirm</span></span>

<span data-ttu-id="88c7a-116">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="88c7a-116">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="88c7a-117">-Name</span><span class="sxs-lookup"><span data-stu-id="88c7a-117">-Name</span></span>

<span data-ttu-id="88c7a-118">Namn eller namn på de experimentella funktioner som ska aktive ras.</span><span class="sxs-lookup"><span data-stu-id="88c7a-118">The name or names of the experimental features to enable.</span></span>

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

### <span data-ttu-id="88c7a-119">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="88c7a-119">-Scope</span></span>

<span data-ttu-id="88c7a-120">Bestämmer vilka som `powershell.config.json` ska uppdateras om det påverkar alla användare eller bara den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="88c7a-120">Determines which `powershell.config.json` to update whether it affects all users or just the current user.</span></span>

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

### <span data-ttu-id="88c7a-121">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="88c7a-121">-WhatIf</span></span>

<span data-ttu-id="88c7a-122">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="88c7a-122">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="88c7a-123">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="88c7a-123">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="88c7a-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="88c7a-124">CommonParameters</span></span>

<span data-ttu-id="88c7a-125">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="88c7a-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="88c7a-126">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="88c7a-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="88c7a-127">INDATA</span><span class="sxs-lookup"><span data-stu-id="88c7a-127">INPUTS</span></span>

### <span data-ttu-id="88c7a-128">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="88c7a-128">ExperimentalFeature</span></span>

<span data-ttu-id="88c7a-129">Pipe-instanser av ExperimentalFeature från `Get-ExperimentalFeature` cmdlet för att aktivera.</span><span class="sxs-lookup"><span data-stu-id="88c7a-129">Pipe instances of ExperimentalFeature from `Get-ExperimentalFeature` cmdlet to enable.</span></span>

## <span data-ttu-id="88c7a-130">UTDATA</span><span class="sxs-lookup"><span data-stu-id="88c7a-130">OUTPUTS</span></span>

### <span data-ttu-id="88c7a-131">Inget</span><span class="sxs-lookup"><span data-stu-id="88c7a-131">None</span></span>

<span data-ttu-id="88c7a-132">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="88c7a-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="88c7a-133">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="88c7a-133">NOTES</span></span>

<span data-ttu-id="88c7a-134">Ändringar av status för en experimentell funktion börjar bara gälla vid omstart av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88c7a-134">Changes to state of an experimental feature only take effect on restart of PowerShell.</span></span>

## <span data-ttu-id="88c7a-135">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="88c7a-135">RELATED LINKS</span></span>

[<span data-ttu-id="88c7a-136">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="88c7a-136">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="88c7a-137">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="88c7a-137">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)