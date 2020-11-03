---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/update-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-DscConfiguration
ms.openlocfilehash: 13365902ab317a3daa41b9a951d5e2fa6e4f1b37
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264758"
---
# <span data-ttu-id="74ebe-103">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="74ebe-103">Update-DscConfiguration</span></span>

## <span data-ttu-id="74ebe-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="74ebe-104">SYNOPSIS</span></span>
<span data-ttu-id="74ebe-105">Kontrollerar hämtnings servern för en uppdaterad konfiguration och tillämpar den.</span><span class="sxs-lookup"><span data-stu-id="74ebe-105">Checks the pull server for an updated configuration and applies it.</span></span>

## <span data-ttu-id="74ebe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="74ebe-106">SYNTAX</span></span>

### <span data-ttu-id="74ebe-107">ComputerNameSet (standard)</span><span class="sxs-lookup"><span data-stu-id="74ebe-107">ComputerNameSet (Default)</span></span>

```
Update-DscConfiguration [-Wait] [-JobName <String>] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="74ebe-108">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="74ebe-108">CimSessionSet</span></span>

```
Update-DscConfiguration [-Wait] [-JobName <String>] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="74ebe-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="74ebe-109">DESCRIPTION</span></span>
<span data-ttu-id="74ebe-110">`Update-DscConfiguration`Cmdleten ansluter till en pull-server, laddar ned konfigurationen om den skiljer sig från vad som är aktuellt på noden och tillämpar sedan konfigurationen på datorn.</span><span class="sxs-lookup"><span data-stu-id="74ebe-110">The `Update-DscConfiguration` cmdlet connects to a pull server, downloads the configuration if it differs from what is current on the node, and then applies the configuration to the computer.</span></span>

<span data-ttu-id="74ebe-111">Den här cmdleten är endast tillgänglig som en del av den [samlade uppdateringen November 2014 för Windows RT 8,1, Windows 8,1 och Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) från Microsoft Support-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="74ebe-111">This cmdlet is available only as part of the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) from the Microsoft Support library.</span></span>

## <span data-ttu-id="74ebe-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="74ebe-112">EXAMPLES</span></span>

### <span data-ttu-id="74ebe-113">Exempel 1: uppdatera en konfiguration</span><span class="sxs-lookup"><span data-stu-id="74ebe-113">Example 1: Update a configuration</span></span>

```
PS C:\> Update-DscConfiguration -Wait -Verbose
```

<span data-ttu-id="74ebe-114">När du har kört det här kommandot ansluter servern till den registrerade pull-tjänsten, laddar ned den senaste tilldelade konfigurationen och tillämpar den sedan.</span><span class="sxs-lookup"><span data-stu-id="74ebe-114">After running this command, the server will connect to the registered pull service, download the latest assigned configuration, and then apply it.</span></span>
<span data-ttu-id="74ebe-115">Parametrarna-wait och-verbose är valfria.</span><span class="sxs-lookup"><span data-stu-id="74ebe-115">The -Wait and -Verbose parameters are optional.</span></span>
<span data-ttu-id="74ebe-116">När du arbetar interaktivt aktiverar de här parametrarna real tids feedback om förlopp och framgång eller haveri vid tillämpning av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="74ebe-116">When working interactively, these parameters combined enable real-time feedback about progress and success or failure when applying the configuration.</span></span>

### <span data-ttu-id="74ebe-117">Exempel 2: uppdatera en konfiguration genom att ansluta via en CIM-session</span><span class="sxs-lookup"><span data-stu-id="74ebe-117">Example 2: Update a configuration by connecting over a CIM session</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Update-DscConfiguration -CimSession $Session -Wait
```

<span data-ttu-id="74ebe-118">Det första kommandot skapar en CIM-session med hjälp av cmdleten **New-CimSession** och lagrar sedan **CimSession** -objektet i variabeln $session.</span><span class="sxs-lookup"><span data-stu-id="74ebe-118">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="74ebe-119">I kommandot uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="74ebe-119">The command prompts you for a password.</span></span>
<span data-ttu-id="74ebe-120">För mer information ange `Get-Help New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="74ebe-120">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="74ebe-121">Det andra kommandot uppdaterar datorn som anges i **CimSession** som lagras i $session.</span><span class="sxs-lookup"><span data-stu-id="74ebe-121">The second command updates the computer specified in the **CimSession** stored in $Session.</span></span>
<span data-ttu-id="74ebe-122">Kommandot anger parametern *wait* .</span><span class="sxs-lookup"><span data-stu-id="74ebe-122">The command specifies the *Wait* parameter.</span></span>
<span data-ttu-id="74ebe-123">Konsolen accepterar inte ytterligare kommandon förrän det aktuella kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="74ebe-123">The console does not accept additional commands until the current command finishes.</span></span>

## <span data-ttu-id="74ebe-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="74ebe-124">PARAMETERS</span></span>

### <span data-ttu-id="74ebe-125">– CimSession</span><span class="sxs-lookup"><span data-stu-id="74ebe-125">-CimSession</span></span>
<span data-ttu-id="74ebe-126">Kör cmdleten i en fjärran sluten session eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="74ebe-126">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="74ebe-127">Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en [New-CimSession-](/powershell/module/cimcmdlets/new-cimsession) eller [Get-CimSession-](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="74ebe-127">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="74ebe-128">Standardvärdet är den aktuella sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="74ebe-128">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="74ebe-129">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="74ebe-129">-ComputerName</span></span>
<span data-ttu-id="74ebe-130">Anger en matris med dator namn.</span><span class="sxs-lookup"><span data-stu-id="74ebe-130">Specifies an array of computer names.</span></span>
<span data-ttu-id="74ebe-131">Cmdleten tillämpar konfigurations inställningarna på de datorer som parametern anger.</span><span class="sxs-lookup"><span data-stu-id="74ebe-131">The cmdlet applies the configuration settings to the computers that this parameter specifies.</span></span>

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

### <span data-ttu-id="74ebe-132">-Credential</span><span class="sxs-lookup"><span data-stu-id="74ebe-132">-Credential</span></span>
<span data-ttu-id="74ebe-133">Anger ett användar namn och lösen ord, som ett **PSCredential** -objekt, för mål datorn.</span><span class="sxs-lookup"><span data-stu-id="74ebe-133">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span>
<span data-ttu-id="74ebe-134">Om du vill hämta ett **PSCredential** -objekt använder du cmdleten Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="74ebe-134">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span>
<span data-ttu-id="74ebe-135">För mer information ange `Get-Help Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="74ebe-135">For more information, type `Get-Help Get-Credential`.</span></span>

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

### <span data-ttu-id="74ebe-136">– JobName</span><span class="sxs-lookup"><span data-stu-id="74ebe-136">-JobName</span></span>
<span data-ttu-id="74ebe-137">Anger ett eget namn för ett jobb.</span><span class="sxs-lookup"><span data-stu-id="74ebe-137">Specifies a friendly name for a job.</span></span>
<span data-ttu-id="74ebe-138">Om du anger den här parametern körs cmdleten som ett jobb och den returnerar ett **jobb** objekt.</span><span class="sxs-lookup"><span data-stu-id="74ebe-138">If you specify this parameter, the cmdlet runs as a job, and it returns a **Job** object.</span></span>

<span data-ttu-id="74ebe-139">Som standard tilldelar Windows PowerShell namnet JobN där N är ett heltal.</span><span class="sxs-lookup"><span data-stu-id="74ebe-139">By default, Windows PowerShell assigns the name JobN where N is an integer.</span></span>

<span data-ttu-id="74ebe-140">Ange inte den här parametern om du anger parametern *wait* .</span><span class="sxs-lookup"><span data-stu-id="74ebe-140">If you specify the *Wait* parameter, do not specify this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74ebe-141">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="74ebe-141">-ThrottleLimit</span></span>
<span data-ttu-id="74ebe-142">Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.</span><span class="sxs-lookup"><span data-stu-id="74ebe-142">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="74ebe-143">Om den här parametern utelämnas eller värdet `0` anges, beräknar Windows PowerShell en optimal begränsnings gräns för cmdleten baserat på antalet CIM-cmdletar som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="74ebe-143">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="74ebe-144">Begränsnings gränsen gäller endast för den aktuella cmdleten, inte sessionen eller till datorn.</span><span class="sxs-lookup"><span data-stu-id="74ebe-144">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="74ebe-145">– Vänta</span><span class="sxs-lookup"><span data-stu-id="74ebe-145">-Wait</span></span>
<span data-ttu-id="74ebe-146">Anger att cmdleten blockerar konsolen tills den Slutför alla konfigurations åtgärder.</span><span class="sxs-lookup"><span data-stu-id="74ebe-146">Indicates that the cmdlet blocks the console until it finishes all configuration tasks.</span></span>

<span data-ttu-id="74ebe-147">Om du anger den här parametern ska du inte ange parametern *JobName* .</span><span class="sxs-lookup"><span data-stu-id="74ebe-147">If you specify this parameter, do not specify the *JobName* parameter.</span></span>

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

### <span data-ttu-id="74ebe-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="74ebe-148">-Confirm</span></span>
<span data-ttu-id="74ebe-149">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="74ebe-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="74ebe-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="74ebe-150">-WhatIf</span></span>
<span data-ttu-id="74ebe-151">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="74ebe-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="74ebe-152">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="74ebe-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="74ebe-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="74ebe-153">CommonParameters</span></span>
<span data-ttu-id="74ebe-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="74ebe-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="74ebe-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="74ebe-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="74ebe-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="74ebe-156">INPUTS</span></span>

## <span data-ttu-id="74ebe-157">UTDATA</span><span class="sxs-lookup"><span data-stu-id="74ebe-157">OUTPUTS</span></span>

## <span data-ttu-id="74ebe-158">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="74ebe-158">NOTES</span></span>

## <span data-ttu-id="74ebe-159">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="74ebe-159">RELATED LINKS</span></span>

[<span data-ttu-id="74ebe-160">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="74ebe-160">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="74ebe-161">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="74ebe-161">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="74ebe-162">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="74ebe-162">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="74ebe-163">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="74ebe-163">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="74ebe-164">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="74ebe-164">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="74ebe-165">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="74ebe-165">Stop-DscConfiguration</span></span>](Stop-DscConfiguration.md)

[<span data-ttu-id="74ebe-166">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="74ebe-166">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
