---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 04/29/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/set-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-DscLocalConfigurationManager
ms.openlocfilehash: 0d35aa56a52f0e6c17abd0e7b2707869e780324c
ms.sourcegitcommit: 0d4d3e47f6979876550591f62061096e7a568f7e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/11/2020
ms.locfileid: "93268047"
---
# <span data-ttu-id="9b035-103">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9b035-103">Set-DscLocalConfigurationManager</span></span>

## <span data-ttu-id="9b035-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9b035-104">SYNOPSIS</span></span>

<span data-ttu-id="9b035-105">Tillämpar lokala Configuration Manager-inställningar (LCM) på noder.</span><span class="sxs-lookup"><span data-stu-id="9b035-105">Applies Local Configuration Manager (LCM) settings to nodes.</span></span>

## <span data-ttu-id="9b035-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9b035-106">SYNTAX</span></span>

### <span data-ttu-id="9b035-107">ComputerNameSet (standard)</span><span class="sxs-lookup"><span data-stu-id="9b035-107">ComputerNameSet (Default)</span></span>

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9b035-108">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="9b035-108">CimSessionSet</span></span>

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9b035-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9b035-109">DESCRIPTION</span></span>

<span data-ttu-id="9b035-110">`Set-DscLocalConfigurationManager`Cmdleten tillämpar LCM-inställningar eller meta-konfiguration på noder.</span><span class="sxs-lookup"><span data-stu-id="9b035-110">The `Set-DscLocalConfigurationManager` cmdlet applies LCM settings, or meta-configuration, to nodes.</span></span> <span data-ttu-id="9b035-111">Ange datorer genom att ange dator namn eller använda Common Information Model CIM-sessioner.</span><span class="sxs-lookup"><span data-stu-id="9b035-111">Specify computers by specifying computer names or by using Common Information Model (CIM) sessions.</span></span> <span data-ttu-id="9b035-112">Om du inte anger en måldator, tillämpar cmdleten inställningar på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9b035-112">If you do not specify a target computer, the cmdlet applies settings to the local computer.</span></span>

## <span data-ttu-id="9b035-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9b035-113">EXAMPLES</span></span>

### <span data-ttu-id="9b035-114">Exempel 1: tillämpa inställningar för LCM</span><span class="sxs-lookup"><span data-stu-id="9b035-114">Example 1: Apply LCM settings</span></span>

```
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="9b035-115">Detta kommando tillämpar LCM-inställningarna från `C:\DSC\Configurations\` på de riktade noderna.</span><span class="sxs-lookup"><span data-stu-id="9b035-115">This command applies the LCM settings from `C:\DSC\Configurations\` to the targeted nodes.</span></span> <span data-ttu-id="9b035-116">När du har tagit emot inställningarna bearbetar LCM dem.</span><span class="sxs-lookup"><span data-stu-id="9b035-116">After receiving the settings, LCM processes them.</span></span>

> [!WARNING]
> <span data-ttu-id="9b035-117">Om det finns flera meta-MOF: ar för samma dator som lagras i den angivna mappen tillämpas bara den första meta MOF.</span><span class="sxs-lookup"><span data-stu-id="9b035-117">If there are multiple meta mofs for the same computer stored in the specified folder, only the first meta mof will be applied.</span></span>

### <span data-ttu-id="9b035-118">Exempel 2: tillämpa inställningar för LCM med hjälp av en CIM-session</span><span class="sxs-lookup"><span data-stu-id="9b035-118">Example 2: Apply LCM settings by using a CIM session</span></span>

```
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\" -CimSession $Session
```

<span data-ttu-id="9b035-119">Det här exemplet tillämpar LCM-inställningar på en dator och tillämpar inställningarna.</span><span class="sxs-lookup"><span data-stu-id="9b035-119">This example applies LCM settings to a computer and applies the settings.</span></span> <span data-ttu-id="9b035-120">I exemplet skapas en CIM-session för en dator med namnet Server01 för användning med cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9b035-120">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span> <span data-ttu-id="9b035-121">Du kan också skapa en matris med CIM-sessioner för att tillämpa cmdleten på flera angivna datorer.</span><span class="sxs-lookup"><span data-stu-id="9b035-121">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="9b035-122">Det första kommandot skapar en CIM-session med hjälp av `New-CimSession` cmdleten och lagrar sedan **CimSession** -objektet i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="9b035-122">The first command creates a CIM session by using the `New-CimSession` cmdlet, and then stores the **CimSession** object in the `$Session` variable.</span></span> <span data-ttu-id="9b035-123">I kommandot uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="9b035-123">The command prompts you for a password.</span></span> <span data-ttu-id="9b035-124">För mer information ange `Get-Help New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="9b035-124">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="9b035-125">Det andra kommandot tillämpar LCM-inställningar för den riktade noden från `C:\DSC\Configurations\` till datorn som identifieras av **CimSession** -objekten som lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="9b035-125">The second command applies LCM settings for the targeted node from `C:\DSC\Configurations\` to the computer identified by the **CimSession** objects stored in the `$Session` variable.</span></span> <span data-ttu-id="9b035-126">I det här exemplet `$Session` innehåller variabeln endast en CIM-session för datorn med namnet Server01.</span><span class="sxs-lookup"><span data-stu-id="9b035-126">In this example, the `$Session` variable contains a CIM session only for the computer named Server01.</span></span> <span data-ttu-id="9b035-127">Kommandot tillämpar inställningarna.</span><span class="sxs-lookup"><span data-stu-id="9b035-127">The command applies the settings.</span></span> <span data-ttu-id="9b035-128">När du har tagit emot inställningarna bearbetar LCM dem.</span><span class="sxs-lookup"><span data-stu-id="9b035-128">After receiving the settings, LCM processes them.</span></span>

## <span data-ttu-id="9b035-129">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9b035-129">PARAMETERS</span></span>

### <span data-ttu-id="9b035-130">– CimSession</span><span class="sxs-lookup"><span data-stu-id="9b035-130">-CimSession</span></span>

<span data-ttu-id="9b035-131">Kör cmdleten i en fjärran sluten session eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="9b035-131">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="9b035-132">Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en [New-CimSession-](/powershell/module/CimCmdlets/New-CimSession) eller [Get-CimSession-](/powershell/module/CimCmdlets/Get-CimSession) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9b035-132">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) or [Get-CimSession](/powershell/module/CimCmdlets/Get-CimSession) cmdlet.</span></span>
<span data-ttu-id="9b035-133">Standardvärdet är den aktuella sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9b035-133">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9b035-134">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="9b035-134">-ComputerName</span></span>

<span data-ttu-id="9b035-135">Anger en matris med dator namn.</span><span class="sxs-lookup"><span data-stu-id="9b035-135">Specifies an array of computer names.</span></span> <span data-ttu-id="9b035-136">Den här parametern begränsar de datorer som har meta-konfigurations dokument i parametern **Path** till de som anges i matrisen.</span><span class="sxs-lookup"><span data-stu-id="9b035-136">This parameter restricts the computers that have meta-configuration documents in the **Path** parameter to those specified in the array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9b035-137">-Credential</span><span class="sxs-lookup"><span data-stu-id="9b035-137">-Credential</span></span>

<span data-ttu-id="9b035-138">Anger ett användar namn och lösen ord, som ett **PSCredential** -objekt, för mål datorn.</span><span class="sxs-lookup"><span data-stu-id="9b035-138">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span> <span data-ttu-id="9b035-139">Om du vill hämta ett **PSCredential** -objekt använder du cmdleten Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="9b035-139">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span> <span data-ttu-id="9b035-140">För mer information ange `Get-Help Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="9b035-140">For more information, type `Get-Help Get-Credential`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b035-141">-Force</span><span class="sxs-lookup"><span data-stu-id="9b035-141">-Force</span></span>

<span data-ttu-id="9b035-142">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="9b035-142">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="9b035-143">-Path</span><span class="sxs-lookup"><span data-stu-id="9b035-143">-Path</span></span>

<span data-ttu-id="9b035-144">Anger en fil Sök väg till en mapp som innehåller filer för konfigurations inställningar.</span><span class="sxs-lookup"><span data-stu-id="9b035-144">Specifies a file path of a folder that contains configuration settings files.</span></span> <span data-ttu-id="9b035-145">Cmdleten publicerar och tillämpar dessa LCM-inställningar på datorer som har installationsfiler på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="9b035-145">The cmdlet publishes and applies these LCM settings to computers that have settings files in the specified path.</span></span> <span data-ttu-id="9b035-146">Varje målnod måste ha en inställnings fil med följande format: `NetBIOS Name.meta.mof` .</span><span class="sxs-lookup"><span data-stu-id="9b035-146">Each target node must have a settings file of the following format: `NetBIOS Name.meta.mof`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b035-147">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="9b035-147">-ThrottleLimit</span></span>

<span data-ttu-id="9b035-148">Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9b035-148">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span> <span data-ttu-id="9b035-149">Om den här parametern utelämnas eller värdet `0` anges, beräknar Windows PowerShell en optimal begränsnings gräns för cmdleten baserat på antalet CIM-cmdletar som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="9b035-149">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span> <span data-ttu-id="9b035-150">Begränsnings gränsen gäller endast för den aktuella cmdleten, inte sessionen eller till datorn.</span><span class="sxs-lookup"><span data-stu-id="9b035-150">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="9b035-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9b035-151">-Confirm</span></span>

<span data-ttu-id="9b035-152">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9b035-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9b035-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9b035-153">-WhatIf</span></span>

<span data-ttu-id="9b035-154">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="9b035-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9b035-155">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="9b035-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9b035-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9b035-156">CommonParameters</span></span>

<span data-ttu-id="9b035-157">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9b035-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9b035-158">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9b035-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9b035-159">INDATA</span><span class="sxs-lookup"><span data-stu-id="9b035-159">INPUTS</span></span>

## <span data-ttu-id="9b035-160">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9b035-160">OUTPUTS</span></span>

## <span data-ttu-id="9b035-161">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9b035-161">NOTES</span></span>

## <span data-ttu-id="9b035-162">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9b035-162">RELATED LINKS</span></span>

[<span data-ttu-id="9b035-163">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9b035-163">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="9b035-164">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9b035-164">Get-DscLocalConfigurationManager</span></span>](Get-DscLocalConfigurationManager.md)
