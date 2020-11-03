---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/publish-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-DscConfiguration
ms.openlocfilehash: 139de2bfdb88c443e7bc48d36e37e95644556bf5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266037"
---
# <span data-ttu-id="d84fe-103">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d84fe-103">Publish-DscConfiguration</span></span>

## <span data-ttu-id="d84fe-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d84fe-104">SYNOPSIS</span></span>
<span data-ttu-id="d84fe-105">Publicerar en DSC-konfiguration till en uppsättning datorer.</span><span class="sxs-lookup"><span data-stu-id="d84fe-105">Publishes a DSC configuration to a set of computers.</span></span>

## <span data-ttu-id="d84fe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d84fe-106">SYNTAX</span></span>

### <span data-ttu-id="d84fe-107">ComputerNameSet (standard)</span><span class="sxs-lookup"><span data-stu-id="d84fe-107">ComputerNameSet (Default)</span></span>

```
Publish-DscConfiguration [-Path] <String> [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d84fe-108">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="d84fe-108">CimSessionSet</span></span>

```
Publish-DscConfiguration [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d84fe-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d84fe-109">DESCRIPTION</span></span>
<span data-ttu-id="d84fe-110">Cmdleten **Publish-DscConfiguration** publicerar ett konfigurations dokument för Windows PowerShell Desired State Configuration (DSC) på en uppsättning datorer.</span><span class="sxs-lookup"><span data-stu-id="d84fe-110">The **Publish-DscConfiguration** cmdlet publishes a Windows PowerShell Desired State Configuration (DSC) configuration document on set of computers.</span></span>
<span data-ttu-id="d84fe-111">Den här cmdleten tillämpar inte konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d84fe-111">This cmdlet does not apply the configuration.</span></span>
<span data-ttu-id="d84fe-112">Konfigurationer tillämpas antingen av Start-DscConfiguration-cmdleten när den används med parametern *UseExisting* eller när DSC-motorn kör sin konsekvens cykel.</span><span class="sxs-lookup"><span data-stu-id="d84fe-112">Configurations are applied by either the Start-DscConfiguration cmdlet when it is used with the *UseExisting* parameter or when the DSC engine runs its consistency cycle.</span></span>
<span data-ttu-id="d84fe-113">DSC-motorn kallas även lokal Configuration Manager (LCM).</span><span class="sxs-lookup"><span data-stu-id="d84fe-113">The DSC engine is also known as the Local Configuration Manager (LCM).</span></span>

<span data-ttu-id="d84fe-114">Denna cmdlet är särskilt användbar när fragment av flera konfigurations dokument levereras.</span><span class="sxs-lookup"><span data-stu-id="d84fe-114">This cmdlet is especially useful when fragments of multiple configuration documents are delivered.</span></span>
<span data-ttu-id="d84fe-115">När flera fragment för konfigurations dokument levereras skrivs de äldre fragmenten för konfigurations dokument över.</span><span class="sxs-lookup"><span data-stu-id="d84fe-115">When multiple configuration documents fragments are delivered, they overwrite the older configuration document fragments.</span></span>

## <span data-ttu-id="d84fe-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d84fe-116">EXAMPLES</span></span>

### <span data-ttu-id="d84fe-117">Exempel 1: publicera en konfiguration på en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="d84fe-117">Example 1: Publish a configuration to a remote computer</span></span>

```
PS C:\> Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

<span data-ttu-id="d84fe-118">Det här kommandot publicerar en konfiguration till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="d84fe-118">This command publishes a configuration to a remote computer.</span></span>
<span data-ttu-id="d84fe-119">Den användare som kör cmdleten ska vara administratör på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="d84fe-119">The user who runs the cmdlet should be administrator on the remote computer.</span></span>

## <span data-ttu-id="d84fe-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d84fe-120">PARAMETERS</span></span>

### <span data-ttu-id="d84fe-121">– CimSession</span><span class="sxs-lookup"><span data-stu-id="d84fe-121">-CimSession</span></span>
<span data-ttu-id="d84fe-122">Kör cmdleten i en fjärran sluten session eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="d84fe-122">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="d84fe-123">Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en [New-CimSession-](/powershell/module/cimcmdlets/new-cimsession) eller [Get-CimSession-](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d84fe-123">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="d84fe-124">Standardvärdet är den aktuella sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="d84fe-124">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="d84fe-125">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="d84fe-125">-ComputerName</span></span>
<span data-ttu-id="d84fe-126">Anger en eller flera datorer där denna cmdlet publicerar konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d84fe-126">Specifies one or more computers on which this cmdlet publishes the configuration.</span></span>

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

### <span data-ttu-id="d84fe-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="d84fe-127">-Credential</span></span>
<span data-ttu-id="d84fe-128">Anger autentiseringsuppgifter som används för att få åtkomst till mål enheten.</span><span class="sxs-lookup"><span data-stu-id="d84fe-128">Specifies credentials that are used to access the target device.</span></span>

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

### <span data-ttu-id="d84fe-129">-Force</span><span class="sxs-lookup"><span data-stu-id="d84fe-129">-Force</span></span>
<span data-ttu-id="d84fe-130">Tvingar cmdleten att slutföras.</span><span class="sxs-lookup"><span data-stu-id="d84fe-130">Forces the cmdlet to finish.</span></span>
<span data-ttu-id="d84fe-131">Om det lokala Configuration Manager uppdaterings läget är inställt på Hämta, ändras användningen av den här parametern till PUSH och möjliggör publicering av DSC-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d84fe-131">If the Local Configuration Manager refresh mode is set to PULL, usage of this parameter changes it to PUSH and enables publication of the DSC configuration.</span></span>
<span data-ttu-id="d84fe-132">Även om det finns en väntande DSC-konfiguration skriver den här parametern över den väntande konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d84fe-132">Also, if a pending DSC configuration exists, usage of this parameter overwrites that pending configuration.</span></span>

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

### <span data-ttu-id="d84fe-133">-Path</span><span class="sxs-lookup"><span data-stu-id="d84fe-133">-Path</span></span>
<span data-ttu-id="d84fe-134">Anger en sökväg som innehåller konfigurationer som ska publiceras på mål datorerna.</span><span class="sxs-lookup"><span data-stu-id="d84fe-134">Specifies a path that contains configurations to publish to target computers.</span></span>

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

### <span data-ttu-id="d84fe-135">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="d84fe-135">-ThrottleLimit</span></span>
<span data-ttu-id="d84fe-136">Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d84fe-136">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="d84fe-137">Om den här parametern utelämnas eller värdet `0` anges, beräknar Windows PowerShell en optimal begränsnings gräns för cmdleten baserat på antalet CIM-cmdletar som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="d84fe-137">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="d84fe-138">Begränsnings gränsen gäller endast för den aktuella cmdleten, inte sessionen eller till datorn.</span><span class="sxs-lookup"><span data-stu-id="d84fe-138">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="d84fe-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d84fe-139">-Confirm</span></span>
<span data-ttu-id="d84fe-140">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d84fe-140">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d84fe-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d84fe-141">-WhatIf</span></span>
<span data-ttu-id="d84fe-142">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="d84fe-142">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d84fe-143">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="d84fe-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d84fe-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d84fe-144">CommonParameters</span></span>
<span data-ttu-id="d84fe-145">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d84fe-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d84fe-146">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d84fe-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d84fe-147">INDATA</span><span class="sxs-lookup"><span data-stu-id="d84fe-147">INPUTS</span></span>

## <span data-ttu-id="d84fe-148">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d84fe-148">OUTPUTS</span></span>

## <span data-ttu-id="d84fe-149">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d84fe-149">NOTES</span></span>

## <span data-ttu-id="d84fe-150">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d84fe-150">RELATED LINKS</span></span>

[<span data-ttu-id="d84fe-151">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d84fe-151">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="d84fe-152">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d84fe-152">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="d84fe-153">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="d84fe-153">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="d84fe-154">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d84fe-154">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="d84fe-155">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d84fe-155">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="d84fe-156">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d84fe-156">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
