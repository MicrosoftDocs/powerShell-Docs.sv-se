---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/test-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-DscConfiguration
ms.openlocfilehash: 25c8bc61976ce3940e0b9bd949fa3ee60728450d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264759"
---
# <span data-ttu-id="08e18-103">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="08e18-103">Test-DscConfiguration</span></span>

## <span data-ttu-id="08e18-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="08e18-104">SYNOPSIS</span></span>
<span data-ttu-id="08e18-105">Testar om den faktiska konfigurationen på noderna matchar önskad konfiguration.</span><span class="sxs-lookup"><span data-stu-id="08e18-105">Tests whether the actual configuration on the nodes matches the desired configuration.</span></span>

## <span data-ttu-id="08e18-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="08e18-106">SYNTAX</span></span>

### <span data-ttu-id="08e18-107">ComputerNameSet (standard)</span><span class="sxs-lookup"><span data-stu-id="08e18-107">ComputerNameSet (Default)</span></span>

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Detailed] [<CommonParameters>]
```

### <span data-ttu-id="08e18-108">ComputerNameAndPathSet</span><span class="sxs-lookup"><span data-stu-id="08e18-108">ComputerNameAndPathSet</span></span>

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="08e18-109">ComputerNameAndReferenceConfigurationSet</span><span class="sxs-lookup"><span data-stu-id="08e18-109">ComputerNameAndReferenceConfigurationSet</span></span>

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] -ReferenceConfiguration <String> [<CommonParameters>]
```

### <span data-ttu-id="08e18-110">CimSessionAndPathSet</span><span class="sxs-lookup"><span data-stu-id="08e18-110">CimSessionAndPathSet</span></span>

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Path] <String>
 [<CommonParameters>]
```

### <span data-ttu-id="08e18-111">CimSessionAndReferenceConfigurationSet</span><span class="sxs-lookup"><span data-stu-id="08e18-111">CimSessionAndReferenceConfigurationSet</span></span>

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob]
 -ReferenceConfiguration <String> [<CommonParameters>]
```

### <span data-ttu-id="08e18-112">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="08e18-112">CimSessionSet</span></span>

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Detailed]
 [<CommonParameters>]
```

## <span data-ttu-id="08e18-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="08e18-113">DESCRIPTION</span></span>
<span data-ttu-id="08e18-114">**Test-DscConfiguration** -cmdleten testar om den faktiska konfigurationen på noderna matchar önskad konfiguration.</span><span class="sxs-lookup"><span data-stu-id="08e18-114">The **Test-DscConfiguration** cmdlet tests whether the actual configuration on the nodes matches the desired configuration.</span></span>
<span data-ttu-id="08e18-115">Ange vilka datorer som du vill testa konfigurationerna med hjälp av dator namn eller Common Information Model CIM-sessioner.</span><span class="sxs-lookup"><span data-stu-id="08e18-115">Specify which computers for which you want to test configurations by using computer names or Common Information Model (CIM) sessions.</span></span>
<span data-ttu-id="08e18-116">Om du inte anger en måldator testar cmdleten konfigurationen av den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="08e18-116">If you do not specify a target computer, the cmdlet tests configuration of the local computer.</span></span>

<span data-ttu-id="08e18-117">Om de önskade och de faktiska konfigurationerna matchar, returnerar cmdleten ett sträng värde för "true".</span><span class="sxs-lookup"><span data-stu-id="08e18-117">If the desired and actual configurations match, the cmdlet returns a string value of 'True'.</span></span>
<span data-ttu-id="08e18-118">Annars returnerar den ett sträng värde på ' false '.</span><span class="sxs-lookup"><span data-stu-id="08e18-118">Otherwise, it returns a string value of 'False'.</span></span>

## <span data-ttu-id="08e18-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="08e18-119">EXAMPLES</span></span>

### <span data-ttu-id="08e18-120">Exempel 1: testa konfigurationen för den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="08e18-120">Example 1: Test configuration for the local computer</span></span>

```
PS C:\> Test-DscConfiguration
```

<span data-ttu-id="08e18-121">Det här kommandot testar konfigurationen för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="08e18-121">This command tests configuration for the local computer.</span></span>

### <span data-ttu-id="08e18-122">Exempel 2: testa konfigurationen för en angiven dator</span><span class="sxs-lookup"><span data-stu-id="08e18-122">Example 2: Test configuration for a specified computer</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Test-DscConfiguration -CimSession $Session
```

<span data-ttu-id="08e18-123">Det här exemplet testar konfigurationen från en dator som anges av en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="08e18-123">This example test configuration from a computer specified by a CIM session.</span></span>
<span data-ttu-id="08e18-124">I exemplet skapas en CIM-session för en dator med namnet Server01 för användning med cmdleten.</span><span class="sxs-lookup"><span data-stu-id="08e18-124">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="08e18-125">Du kan också skapa en matris med CIM-sessioner för att tillämpa cmdleten på flera angivna datorer.</span><span class="sxs-lookup"><span data-stu-id="08e18-125">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="08e18-126">Det första kommandot skapar en CIM-session med hjälp av cmdleten **New-CimSession** och lagrar sedan **CimSession** -objektet i variabeln $session.</span><span class="sxs-lookup"><span data-stu-id="08e18-126">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="08e18-127">I kommandot uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="08e18-127">The command prompts you for a password.</span></span>
<span data-ttu-id="08e18-128">För mer information ange `Get-Help New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="08e18-128">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="08e18-129">Det andra kommandot testar konfigurationen för de datorer som identifieras av de **CimSession** -objekt som lagras i variabeln $session, i det här fallet datorn med namnet Server01.</span><span class="sxs-lookup"><span data-stu-id="08e18-129">The second command tests configuration for the computers identified by the **CimSession** objects stored in the $Session variable, in this case, the computer named Server01.</span></span>

### <span data-ttu-id="08e18-130">Exempel 3: testa konfigurationer med detaljerade resultat</span><span class="sxs-lookup"><span data-stu-id="08e18-130">Example 3: Test configurations with detailed results</span></span>

```
PS C:\> Test-DscConfiguration -ComputerName "Server01", "Server02", "Server03" -Detailed
```

<span data-ttu-id="08e18-131">Det här kommandot testar konfigurationer för en uppsättning datorer som anges av parametern *computername* och returnerar detaljerad information som innehåller det övergripande läget, resurser som är i önskat tillstånd, resurser som inte är i önskat tillstånd och dator namn.</span><span class="sxs-lookup"><span data-stu-id="08e18-131">This command tests configurations for a set of computers specified by the *ComputerName* parameter and returns detailed information that includes the overall state, resources that are in the desired state, resources that are not in the desired state and computer name.</span></span>

### <span data-ttu-id="08e18-132">Exempel 4: testa konfigurationer som anges i en mapp</span><span class="sxs-lookup"><span data-stu-id="08e18-132">Example 4: Test configurations specified in a folder</span></span>

```
PS C:\> Test-DscConfiguration -Path "C:\Dsc\Configurations"
```

<span data-ttu-id="08e18-133">Det här kommandot testar konfigurationer som definieras i en mapp som anges av parametern *Path* .</span><span class="sxs-lookup"><span data-stu-id="08e18-133">This command tests configurations that are defined in a folder specified by the *Path* parameter.</span></span>
<span data-ttu-id="08e18-134">Konfigurationerna testas mot en uppsättning datorer, som identifieras av konfigurations filens fil namn.</span><span class="sxs-lookup"><span data-stu-id="08e18-134">The configurations are tested against a set of computers, each identified by the file name of the configuration file.</span></span>

### <span data-ttu-id="08e18-135">Exempel 5: testa konfigurationer som anges i en fil</span><span class="sxs-lookup"><span data-stu-id="08e18-135">Example 5: Test configurations specified in a file</span></span>

```
PS C:\> Test-DscConfiguration -ReferenceConfiguration "C:\Dsc\Configurations\WebServer.mof" -ComputerName "Server01", "Server02", "Server03"
```

<span data-ttu-id="08e18-136">Det här kommandot testar en konfiguration som definierats i en fil mot en uppsättning datorer som anges av parametern *computername* .</span><span class="sxs-lookup"><span data-stu-id="08e18-136">This command tests a configuration defined in a file against a set of computers specified by the *ComputerName* parameter.</span></span>

## <span data-ttu-id="08e18-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="08e18-137">PARAMETERS</span></span>

### <span data-ttu-id="08e18-138">– AsJob</span><span class="sxs-lookup"><span data-stu-id="08e18-138">-AsJob</span></span>
<span data-ttu-id="08e18-139">Anger att denna cmdlet kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="08e18-139">Indicates that this cmdlet runs the command as a background job.</span></span>

<span data-ttu-id="08e18-140">Om du anger parametern *AsJob* , returnerar kommandot ett objekt som representerar jobbet och visar sedan kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="08e18-140">If you specify the *AsJob* parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span>
<span data-ttu-id="08e18-141">Du kan fortsätta att arbeta i sessionen tills jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="08e18-141">You can continue to work in the session until the job finishes.</span></span>
<span data-ttu-id="08e18-142">Jobbet skapas på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="08e18-142">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="08e18-143">Använd jobb-cmdletar för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="08e18-143">To manage the job, use the Job cmdlets.</span></span>
<span data-ttu-id="08e18-144">Använd Receive-Job-cmdleten för att hämta jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="08e18-144">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="08e18-145">Om du vill använda den här parametern måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation och i Windows Vista och senare versioner av Windows operativ system måste du öppna Windows PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="08e18-145">To use this parameter, the local and remote computers must be configured for remoting, and on Windows Vista and later versions of the Windows operating system, you must open Windows PowerShell with the Run as administrator option.</span></span>
<span data-ttu-id="08e18-146">Mer information finns i [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08e18-146">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="08e18-147">Mer information om bakgrunds jobb i Windows PowerShell finns i [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) och [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="08e18-147">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

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

### <span data-ttu-id="08e18-148">– CimSession</span><span class="sxs-lookup"><span data-stu-id="08e18-148">-CimSession</span></span>
<span data-ttu-id="08e18-149">Kör cmdleten i en fjärran sluten session eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="08e18-149">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="08e18-150">Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en [New-CimSession-](/powershell/module/cimcmdlets/new-cimsession) eller [Get-CimSession-](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="08e18-150">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="08e18-151">Standardvärdet är den aktuella sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="08e18-151">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndReferenceConfigurationSet, CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="08e18-152">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="08e18-152">-ComputerName</span></span>
<span data-ttu-id="08e18-153">Anger en matris med dator namn som denna cmdlet testar konfigurationen på.</span><span class="sxs-lookup"><span data-stu-id="08e18-153">Specifies an array of computer names on which this cmdlet tests the configuration.</span></span>
<span data-ttu-id="08e18-154">Cmdleten testar konfigurations dokumentet på den plats som anges av *Sök vägs* parametern till de här datorerna.</span><span class="sxs-lookup"><span data-stu-id="08e18-154">The cmdlet tests the configuration document in the location specified by the *Path* parameter to these computers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="08e18-155">-Credential</span><span class="sxs-lookup"><span data-stu-id="08e18-155">-Credential</span></span>
<span data-ttu-id="08e18-156">Anger ett användar namn och lösen ord, som ett **PSCredential** -objekt, för mål datorn.</span><span class="sxs-lookup"><span data-stu-id="08e18-156">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span>
<span data-ttu-id="08e18-157">Om du vill hämta ett **PSCredential** -objekt använder du cmdleten Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="08e18-157">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span>
<span data-ttu-id="08e18-158">För mer information ange `Get-Help Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="08e18-158">For more information, type `Get-Help Get-Credential`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="08e18-159">-Detaljerad</span><span class="sxs-lookup"><span data-stu-id="08e18-159">-Detailed</span></span>
<span data-ttu-id="08e18-160">Anger att denna cmdlet returnerar ett detaljerat resultat vid jämförelse av konfigurations dokumentet med det önskade läget för noderna.</span><span class="sxs-lookup"><span data-stu-id="08e18-160">Indicates that this cmdlet returns a detailed result of comparing the configuration document with the desired state of the nodes.</span></span>
<span data-ttu-id="08e18-161">Resultatet innehåller information, till exempel övergripande tillstånd, resurser som är i önskat tillstånd, resurser som inte är i önskat tillstånd och dator namn.</span><span class="sxs-lookup"><span data-stu-id="08e18-161">The result includes information such as overall state, resources that are in the desired state, resources that are not in desired state, and computer name.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameSet, CimSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="08e18-162">-Path</span><span class="sxs-lookup"><span data-stu-id="08e18-162">-Path</span></span>
<span data-ttu-id="08e18-163">Anger sökvägen till en mapp som innehåller konfigurationsfiler för filer.</span><span class="sxs-lookup"><span data-stu-id="08e18-163">Specifies the path of a folder that contains configuration document files.</span></span>
<span data-ttu-id="08e18-164">Cmdleten testar konfigurationen mot önskat tillstånd för datorer som anges av parametern *computername* eller *CimSession* .</span><span class="sxs-lookup"><span data-stu-id="08e18-164">The cmdlet tests the configuration against the desired state of computers specified by the *ComputerName* or *CimSession* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="08e18-165">-ReferenceConfiguration</span><span class="sxs-lookup"><span data-stu-id="08e18-165">-ReferenceConfiguration</span></span>
<span data-ttu-id="08e18-166">Anger sökvägen till konfigurations dokument filen.</span><span class="sxs-lookup"><span data-stu-id="08e18-166">Specifies the path of the configuration document file.</span></span>
<span data-ttu-id="08e18-167">Den här cmdleten testar konfigurationen mot det aktuella läget för datorer som anges av parametern *computername* eller *CimSession* .</span><span class="sxs-lookup"><span data-stu-id="08e18-167">This cmdlet tests the configuration against the actual state of computers specified by the *ComputerName* or *CimSession* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameAndReferenceConfigurationSet, CimSessionAndReferenceConfigurationSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="08e18-168">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="08e18-168">-ThrottleLimit</span></span>
<span data-ttu-id="08e18-169">Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.</span><span class="sxs-lookup"><span data-stu-id="08e18-169">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="08e18-170">Om den här parametern utelämnas eller värdet `0` anges, beräknar Windows PowerShell en optimal begränsnings gräns för cmdleten baserat på antalet CIM-cmdletar som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="08e18-170">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="08e18-171">Begränsnings gränsen gäller endast för den aktuella cmdleten, inte sessionen eller till datorn.</span><span class="sxs-lookup"><span data-stu-id="08e18-171">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="08e18-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="08e18-172">CommonParameters</span></span>
<span data-ttu-id="08e18-173">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="08e18-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="08e18-174">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="08e18-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="08e18-175">INDATA</span><span class="sxs-lookup"><span data-stu-id="08e18-175">INPUTS</span></span>

## <span data-ttu-id="08e18-176">UTDATA</span><span class="sxs-lookup"><span data-stu-id="08e18-176">OUTPUTS</span></span>

## <span data-ttu-id="08e18-177">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="08e18-177">NOTES</span></span>

## <span data-ttu-id="08e18-178">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="08e18-178">RELATED LINKS</span></span>

[<span data-ttu-id="08e18-179">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="08e18-179">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="08e18-180">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="08e18-180">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="08e18-181">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="08e18-181">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="08e18-182">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="08e18-182">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="08e18-183">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="08e18-183">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)
