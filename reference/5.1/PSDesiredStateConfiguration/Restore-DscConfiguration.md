---
external help file: Restore-DSCConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/restore-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-DscConfiguration
ms.openlocfilehash: 823032f7665d9ec83faa59c37560510e049efdd2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266031"
---
# <span data-ttu-id="30377-103">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="30377-103">Restore-DscConfiguration</span></span>

## <span data-ttu-id="30377-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="30377-104">SYNOPSIS</span></span>
<span data-ttu-id="30377-105">Återanvänder den tidigare konfigurationen för noden.</span><span class="sxs-lookup"><span data-stu-id="30377-105">Reapplies the previous configuration for the node.</span></span>

## <span data-ttu-id="30377-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="30377-106">SYNTAX</span></span>

```
Restore-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="30377-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="30377-107">DESCRIPTION</span></span>
<span data-ttu-id="30377-108">**Restore-DscConfiguration-** cmdleten tillämpar den tidigare konfigurationen för noden, om det finns en tidigare konfiguration.</span><span class="sxs-lookup"><span data-stu-id="30377-108">The **Restore-DscConfiguration** cmdlet reapplies the previous configuration for the node, if a previous configuration exists.</span></span>
<span data-ttu-id="30377-109">Ange datorer med hjälp av Common Information Model (CIM)-sessioner.</span><span class="sxs-lookup"><span data-stu-id="30377-109">Specify computers by using Common Information Model (CIM) sessions.</span></span>
<span data-ttu-id="30377-110">Om du inte anger en måldator återställer cmdleten konfigurationen av den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="30377-110">If you do not specify a target computer, the cmdlet restores the configuration of the local computer.</span></span>
<span data-ttu-id="30377-111">Om det inte finns någon tidigare konfiguration för en viss nod, returnerar denna cmdlet ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="30377-111">If there is no previous configuration for a particular node, this cmdlet returns an error message.</span></span>

<span data-ttu-id="30377-112">Denna cmdlet stöder inte **Confirm** -parametern.</span><span class="sxs-lookup"><span data-stu-id="30377-112">This cmdlet does not support the **Confirm** parameter.</span></span>

## <span data-ttu-id="30377-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="30377-113">EXAMPLES</span></span>

### <span data-ttu-id="30377-114">Exempel 1: Återställ konfigurationen för den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="30377-114">Example 1: Restore the configuration for the local computer</span></span>

```
PS C:\> Restore-DscConfiguration
```

<span data-ttu-id="30377-115">Det här kommandot återställer konfigurationen för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="30377-115">This command restores the configuration for the local computer.</span></span>

### <span data-ttu-id="30377-116">Exempel 2: Återställa konfigurationen för en angiven dator</span><span class="sxs-lookup"><span data-stu-id="30377-116">Example 2: Restore configuration for a specified computer</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Restore-DscConfiguration -CimSession $Session
```

<span data-ttu-id="30377-117">I det här exemplet återställs konfigurationen på en dator som anges av en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="30377-117">This example restores configuration on a computer specified by a CIM session.</span></span>
<span data-ttu-id="30377-118">I exemplet skapas en CIM-session för en dator med namnet Server01 för användning med cmdleten.</span><span class="sxs-lookup"><span data-stu-id="30377-118">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="30377-119">Du kan också skapa en matris med CIM-sessioner för att tillämpa cmdleten på flera angivna datorer.</span><span class="sxs-lookup"><span data-stu-id="30377-119">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="30377-120">Det första kommandot skapar en CIM-session med hjälp av cmdleten **New-CimSession** och lagrar sedan **CimSession** -objektet i variabeln $session.</span><span class="sxs-lookup"><span data-stu-id="30377-120">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="30377-121">I kommandot uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="30377-121">The command prompts you for a password.</span></span>
<span data-ttu-id="30377-122">För mer information ange `Get-Help New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="30377-122">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="30377-123">Det andra kommandot återställer konfigurationen för de datorer som identifieras av de **CimSession** -objekt som lagras i variabeln $session, i det här fallet datorn med namnet Server01.</span><span class="sxs-lookup"><span data-stu-id="30377-123">The second command restores the configuration for the computers identified by the **CimSession** objects stored in the $Session variable, in this case, the computer named Server01.</span></span>

## <span data-ttu-id="30377-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="30377-124">PARAMETERS</span></span>

### <span data-ttu-id="30377-125">– AsJob</span><span class="sxs-lookup"><span data-stu-id="30377-125">-AsJob</span></span>
<span data-ttu-id="30377-126">Anger att denna cmdlet kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="30377-126">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="30377-127">– CimSession</span><span class="sxs-lookup"><span data-stu-id="30377-127">-CimSession</span></span>
<span data-ttu-id="30377-128">Kör cmdleten i en fjärran sluten session eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="30377-128">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="30377-129">Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en **New-CimSession-** eller **Get-CimSession-** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30377-129">Enter a computer name or a session object, such as the output of a **New-CimSession** or **Get-CimSession** cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="30377-130">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="30377-130">-ThrottleLimit</span></span>
<span data-ttu-id="30377-131">Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.</span><span class="sxs-lookup"><span data-stu-id="30377-131">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="30377-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="30377-132">-Confirm</span></span>
<span data-ttu-id="30377-133">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="30377-133">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="30377-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="30377-134">-WhatIf</span></span>
<span data-ttu-id="30377-135">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="30377-135">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="30377-136">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="30377-136">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="30377-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="30377-137">CommonParameters</span></span>
<span data-ttu-id="30377-138">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="30377-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="30377-139">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="30377-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="30377-140">INDATA</span><span class="sxs-lookup"><span data-stu-id="30377-140">INPUTS</span></span>

## <span data-ttu-id="30377-141">UTDATA</span><span class="sxs-lookup"><span data-stu-id="30377-141">OUTPUTS</span></span>

## <span data-ttu-id="30377-142">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="30377-142">NOTES</span></span>

## <span data-ttu-id="30377-143">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="30377-143">RELATED LINKS</span></span>

[<span data-ttu-id="30377-144">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="30377-144">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="30377-145">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="30377-145">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="30377-146">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="30377-146">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="30377-147">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="30377-147">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="30377-148">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="30377-148">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
