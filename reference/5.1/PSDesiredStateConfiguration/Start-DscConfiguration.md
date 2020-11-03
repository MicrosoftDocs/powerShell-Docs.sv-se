---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/start-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-DscConfiguration
ms.openlocfilehash: c34754aeb7fce99030cf4ddb235e3e7e8161f3eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266025"
---
# <span data-ttu-id="85df0-103">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="85df0-103">Start-DscConfiguration</span></span>

## <span data-ttu-id="85df0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="85df0-104">SYNOPSIS</span></span>
<span data-ttu-id="85df0-105">Tillämpar konfiguration på noder.</span><span class="sxs-lookup"><span data-stu-id="85df0-105">Applies configuration to nodes.</span></span>

## <span data-ttu-id="85df0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="85df0-106">SYNTAX</span></span>

### <span data-ttu-id="85df0-107">ComputerNameAndPathSet (standard)</span><span class="sxs-lookup"><span data-stu-id="85df0-107">ComputerNameAndPathSet (Default)</span></span>

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="85df0-108">CimSessionAndPathSet</span><span class="sxs-lookup"><span data-stu-id="85df0-108">CimSessionAndPathSet</span></span>

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] -CimSession <CimSession[]> [-ThrottleLimit <Int32>]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="85df0-109">ComputerNameAndUseExistingSet</span><span class="sxs-lookup"><span data-stu-id="85df0-109">ComputerNameAndUseExistingSet</span></span>

```
Start-DscConfiguration [-Wait] [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-UseExisting] [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="85df0-110">CimSessionAndUseExistingSet</span><span class="sxs-lookup"><span data-stu-id="85df0-110">CimSessionAndUseExistingSet</span></span>

```
Start-DscConfiguration [-Wait] [-Force] -CimSession <CimSession[]> [-ThrottleLimit <Int32>] [-UseExisting]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="85df0-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="85df0-111">DESCRIPTION</span></span>
<span data-ttu-id="85df0-112">Cmdleten **Start-DscConfiguration** tillämpar konfigurationen på noderna.</span><span class="sxs-lookup"><span data-stu-id="85df0-112">The **Start-DscConfiguration** cmdlet applies configuration to nodes.</span></span>
<span data-ttu-id="85df0-113">När den används med parametern *UseExisting* tillämpas den befintliga konfigurationen på mål datorn.</span><span class="sxs-lookup"><span data-stu-id="85df0-113">When used with the *UseExisting* parameter, the existing configuration on the target computer is applied.</span></span>
<span data-ttu-id="85df0-114">Ange vilka datorer som du vill tillämpa konfigurationen på genom att ange dator namn eller använda Common Information Model CIM-sessioner.</span><span class="sxs-lookup"><span data-stu-id="85df0-114">Specify which computers that you want to apply configuration to by specifying computer names or by using Common Information Model (CIM) sessions.</span></span>

<span data-ttu-id="85df0-115">Som standard skapar denna cmdlet ett jobb och returnerar ett **jobb** objekt.</span><span class="sxs-lookup"><span data-stu-id="85df0-115">By default, this cmdlet creates a job and returns a **Job** object.</span></span>
<span data-ttu-id="85df0-116">Om du vill ha mer information om bakgrunds jobb skriver du `Get-Help about_Jobs` .</span><span class="sxs-lookup"><span data-stu-id="85df0-116">For more information about background jobs, type `Get-Help about_Jobs`.</span></span>
<span data-ttu-id="85df0-117">Om du vill använda den här cmdleten interaktivt anger du parametern *wait* .</span><span class="sxs-lookup"><span data-stu-id="85df0-117">To use this cmdlet interactively, specify the *Wait* parameter.</span></span>

<span data-ttu-id="85df0-118">Ange *utförlig* parameter om du vill se information om vad cmdleten gör när konfigurations inställningarna tillämpas.</span><span class="sxs-lookup"><span data-stu-id="85df0-118">Specify the *Verbose* parameter to see details of what the cmdlet does when it applies configuration settings.</span></span>

## <span data-ttu-id="85df0-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="85df0-119">EXAMPLES</span></span>

### <span data-ttu-id="85df0-120">Exempel 1: Använd konfigurations inställningar</span><span class="sxs-lookup"><span data-stu-id="85df0-120">Example 1: Apply configuration settings</span></span>

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="85df0-121">Detta kommando tillämpar konfigurations inställningarna från C:\DSC\Configurations\ till alla datorer som har inställningar i den mappen.</span><span class="sxs-lookup"><span data-stu-id="85df0-121">This command applies the configuration settings from C:\DSC\Configurations\ to the every computer that has settings in that folder.</span></span>
<span data-ttu-id="85df0-122">Kommandot returnerar **jobb** objekt för varje målnod som distribueras till.</span><span class="sxs-lookup"><span data-stu-id="85df0-122">The command returns **Job** objects for each target node deployed to.</span></span>

### <span data-ttu-id="85df0-123">Exempel 2: tillämpa konfigurations inställningar och vänta tills konfigurationen är klar</span><span class="sxs-lookup"><span data-stu-id="85df0-123">Example 2: Apply configuration settings and wait for configuration to complete</span></span>

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -Wait -Verbose
```

<span data-ttu-id="85df0-124">Detta kommando tillämpar konfigurationen från C:\DSC\Configurations\ till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="85df0-124">This command applies the configuration from C:\DSC\Configurations\ to the local computer.</span></span>
<span data-ttu-id="85df0-125">Kommandot returnerar **jobb** objekt för varje målnod som distribueras till, i det här fallet bara den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="85df0-125">The command returns **Job** objects for each target node deployed to, in this case, just the local computer.</span></span>
<span data-ttu-id="85df0-126">I det här exemplet anges *utförlig* parameter.</span><span class="sxs-lookup"><span data-stu-id="85df0-126">This example specifies the *Verbose* parameter.</span></span>
<span data-ttu-id="85df0-127">Därför skickar kommandot meddelanden till-konsolen när de fortsätter.</span><span class="sxs-lookup"><span data-stu-id="85df0-127">Therefore, the command sends messages to the console as it proceeds.</span></span>
<span data-ttu-id="85df0-128">Kommandot innehåller parametern *wait* .</span><span class="sxs-lookup"><span data-stu-id="85df0-128">The command includes the *Wait* parameter.</span></span>
<span data-ttu-id="85df0-129">Därför kan du inte använda-konsolen förrän kommandot har slutfört alla konfigurations åtgärder.</span><span class="sxs-lookup"><span data-stu-id="85df0-129">Therefore, you cannot use the console until the command finishes all configuration tasks.</span></span>

### <span data-ttu-id="85df0-130">Exempel 3: tillämpa konfigurations inställningar med en CIM-session</span><span class="sxs-lookup"><span data-stu-id="85df0-130">Example 3: Apply configuration settings by using a CIM session</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -CimSession $Session
```

<span data-ttu-id="85df0-131">I det här exemplet används konfigurations inställningar på en angiven dator.</span><span class="sxs-lookup"><span data-stu-id="85df0-131">This example applies configuration settings to a specified computer.</span></span>
<span data-ttu-id="85df0-132">I exemplet skapas en CIM-session för en dator med namnet Server01 för användning med cmdleten.</span><span class="sxs-lookup"><span data-stu-id="85df0-132">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="85df0-133">Du kan också skapa en matris med CIM-sessioner för att tillämpa cmdleten på flera angivna datorer.</span><span class="sxs-lookup"><span data-stu-id="85df0-133">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="85df0-134">Det första kommandot skapar en CIM-session med hjälp av cmdleten **New-CimSession** och lagrar sedan **CimSession** -objektet i variabeln $session.</span><span class="sxs-lookup"><span data-stu-id="85df0-134">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="85df0-135">I kommandot uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="85df0-135">The command prompts you for a password.</span></span>
<span data-ttu-id="85df0-136">För mer information ange `Get-Help NewCimSession`.</span><span class="sxs-lookup"><span data-stu-id="85df0-136">For more information, type `Get-Help NewCimSession`.</span></span>

<span data-ttu-id="85df0-137">Det andra kommandot tillämpar konfigurations inställningarna från C:\DSC\Configurations\ på de datorer som identifieras av de **CimSession** -objekt som lagras i variabeln $session.</span><span class="sxs-lookup"><span data-stu-id="85df0-137">The second command applies the configuration settings from C:\DSC\Configurations\ to the computers identified by the **CimSession** objects stored in the $Session variable.</span></span>
<span data-ttu-id="85df0-138">I det här exemplet innehåller variabeln $Session endast en CIM-session för datorn med namnet Server01.</span><span class="sxs-lookup"><span data-stu-id="85df0-138">In this example, the $Session variable contains a CIM session only for the computer named Server01.</span></span>
<span data-ttu-id="85df0-139">Kommandot tillämpar konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="85df0-139">The command applies the configuration.</span></span>
<span data-ttu-id="85df0-140">Kommandot skapar **jobb** objekt för varje konfigurerad dator.</span><span class="sxs-lookup"><span data-stu-id="85df0-140">The command creates **Job** objects for each configured computer.</span></span>

## <span data-ttu-id="85df0-141">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="85df0-141">PARAMETERS</span></span>

### <span data-ttu-id="85df0-142">– CimSession</span><span class="sxs-lookup"><span data-stu-id="85df0-142">-CimSession</span></span>
<span data-ttu-id="85df0-143">Kör cmdleten i en fjärran sluten session eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="85df0-143">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="85df0-144">Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en [New-CimSession-](/powershell/module/cimcmdlets/new-cimsession) eller [Get-CimSession-](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="85df0-144">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="85df0-145">Standardvärdet är den aktuella sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="85df0-145">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="85df0-146">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="85df0-146">-ComputerName</span></span>
<span data-ttu-id="85df0-147">Anger en matris med dator namn.</span><span class="sxs-lookup"><span data-stu-id="85df0-147">Specifies an array of computer names.</span></span>
<span data-ttu-id="85df0-148">Den här parametern begränsar de datorer som har konfigurations dokument i parametern *Path* till de som anges i matrisen.</span><span class="sxs-lookup"><span data-stu-id="85df0-148">This parameter restricts the computers that have configuration documents in the *Path* parameter to those specified in the array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="85df0-149">-Credential</span><span class="sxs-lookup"><span data-stu-id="85df0-149">-Credential</span></span>
<span data-ttu-id="85df0-150">Anger ett användar namn och lösen ord, som ett **PSCredential** -objekt, för mål datorn.</span><span class="sxs-lookup"><span data-stu-id="85df0-150">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span>
<span data-ttu-id="85df0-151">Om du vill hämta ett **PSCredential** -objekt använder du cmdleten Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="85df0-151">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span>
<span data-ttu-id="85df0-152">För mer information ange `Get-Help Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="85df0-152">For more information, type `Get-Help Get-Credential`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85df0-153">-Force</span><span class="sxs-lookup"><span data-stu-id="85df0-153">-Force</span></span>
<span data-ttu-id="85df0-154">Stoppar den konfigurations åtgärd som körs på mål datorn och påbörjar den nya Start-Configuration åtgärden.</span><span class="sxs-lookup"><span data-stu-id="85df0-154">Stops the configuration operation currently running on the target computer and begins the new Start-Configuration operation.</span></span>
<span data-ttu-id="85df0-155">Om egenskapen **RefreshMode** för den lokala Configuration Manager är inställd på **Hämta** , ändrar den här parametern den till **push**.</span><span class="sxs-lookup"><span data-stu-id="85df0-155">If the **RefreshMode** property of the Local Configuration Manager is set to **Pull** , specifying this parameter changes it to **Push**.</span></span>

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

### <span data-ttu-id="85df0-156">– JobName</span><span class="sxs-lookup"><span data-stu-id="85df0-156">-JobName</span></span>
<span data-ttu-id="85df0-157">Anger ett eget namn för ett jobb.</span><span class="sxs-lookup"><span data-stu-id="85df0-157">Specifies a friendly name for a job.</span></span>
<span data-ttu-id="85df0-158">Om du anger den här parametern körs cmdleten som ett jobb och den returnerar ett **jobb** objekt.</span><span class="sxs-lookup"><span data-stu-id="85df0-158">If you specify this parameter, the cmdlet runs as a job, and it returns a **Job** object.</span></span>

<span data-ttu-id="85df0-159">Som standard tilldelar Windows PowerShell namnet JobN där N är ett heltal.</span><span class="sxs-lookup"><span data-stu-id="85df0-159">By default, Windows PowerShell assigns the name JobN where N is an integer.</span></span>

<span data-ttu-id="85df0-160">Ange inte den här parametern om du anger parametern *wait* .</span><span class="sxs-lookup"><span data-stu-id="85df0-160">If you specify the *Wait* parameter, do not specify this parameter.</span></span>

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

### <span data-ttu-id="85df0-161">-Path</span><span class="sxs-lookup"><span data-stu-id="85df0-161">-Path</span></span>
<span data-ttu-id="85df0-162">Anger en fil Sök väg till en mapp som innehåller filer för konfigurations inställningar.</span><span class="sxs-lookup"><span data-stu-id="85df0-162">Specifies a file path of a folder that contains configuration settings files.</span></span>
<span data-ttu-id="85df0-163">Denna cmdlet publicerar och tillämpar dessa konfigurations inställningar på datorer som har installationsfiler på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="85df0-163">This cmdlet publishes and applies these configuration settings to computers that have settings files in the specified path.</span></span>
<span data-ttu-id="85df0-164">Varje målnod måste ha en inställnings fil med följande format: NetBIOS-namn. mof.</span><span class="sxs-lookup"><span data-stu-id="85df0-164">Each target node must have a settings file of the following format: NetBIOS Name.mof.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85df0-165">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="85df0-165">-ThrottleLimit</span></span>
<span data-ttu-id="85df0-166">Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.</span><span class="sxs-lookup"><span data-stu-id="85df0-166">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="85df0-167">Om den här parametern utelämnas eller värdet `0` anges, beräknar Windows PowerShell en optimal begränsnings gräns för cmdleten baserat på antalet CIM-cmdletar som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="85df0-167">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="85df0-168">Begränsnings gränsen gäller endast för den aktuella cmdleten, inte sessionen eller till datorn.</span><span class="sxs-lookup"><span data-stu-id="85df0-168">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="85df0-169">-UseExisting</span><span class="sxs-lookup"><span data-stu-id="85df0-169">-UseExisting</span></span>
<span data-ttu-id="85df0-170">Anger att den här cmdleten tillämpar den befintliga konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="85df0-170">Indicates that this cmdlet applies the existing configuration.</span></span>
<span data-ttu-id="85df0-171">Konfigurationen kan finnas på mål datorn av HITECH med hjälp av **Start-DscConfiguration** eller genom att publicera med hjälp av cmdleten Publish-DscConfiguration.</span><span class="sxs-lookup"><span data-stu-id="85df0-171">The configuration can exist on the target computer by enactment using **Start-DscConfiguration** or by publication using the Publish-DscConfiguration cmdlet.</span></span>

<span data-ttu-id="85df0-172">Innan du anger den här parametern för denna cmdlet bör du läsa informationen i [Nyheter i Windows PowerShell 5,0](/powershell/scripting/whats-new/what-s-new-in-windows-powershell-50)</span><span class="sxs-lookup"><span data-stu-id="85df0-172">Before you specify this parameter for this cmdlet, review the information in [What's New in Windows PowerShell 5.0](/powershell/scripting/whats-new/what-s-new-in-windows-powershell-50)</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameAndUseExistingSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85df0-173">– Vänta</span><span class="sxs-lookup"><span data-stu-id="85df0-173">-Wait</span></span>
<span data-ttu-id="85df0-174">Anger att cmdleten blockerar konsolen tills den Slutför alla konfigurations åtgärder.</span><span class="sxs-lookup"><span data-stu-id="85df0-174">Indicates that the cmdlet blocks the console until it finishes all configuration tasks.</span></span>

<span data-ttu-id="85df0-175">Om du anger den här parametern ska du inte ange parametern *JobName* .</span><span class="sxs-lookup"><span data-stu-id="85df0-175">If you specify this parameter, do not specify the *JobName* parameter.</span></span>

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

### <span data-ttu-id="85df0-176">-Confirm</span><span class="sxs-lookup"><span data-stu-id="85df0-176">-Confirm</span></span>
<span data-ttu-id="85df0-177">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="85df0-177">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="85df0-178">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="85df0-178">-WhatIf</span></span>
<span data-ttu-id="85df0-179">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="85df0-179">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="85df0-180">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="85df0-180">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="85df0-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="85df0-181">CommonParameters</span></span>
<span data-ttu-id="85df0-182">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="85df0-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="85df0-183">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="85df0-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="85df0-184">INDATA</span><span class="sxs-lookup"><span data-stu-id="85df0-184">INPUTS</span></span>

## <span data-ttu-id="85df0-185">UTDATA</span><span class="sxs-lookup"><span data-stu-id="85df0-185">OUTPUTS</span></span>

## <span data-ttu-id="85df0-186">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="85df0-186">NOTES</span></span>

## <span data-ttu-id="85df0-187">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="85df0-187">RELATED LINKS</span></span>

[<span data-ttu-id="85df0-188">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="85df0-188">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="85df0-189">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="85df0-189">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="85df0-190">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="85df0-190">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="85df0-191">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="85df0-191">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="85df0-192">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="85df0-192">Stop-DscConfiguration</span></span>](Stop-DscConfiguration.md)

[<span data-ttu-id="85df0-193">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="85df0-193">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

[<span data-ttu-id="85df0-194">Uppdatera – DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="85df0-194">Update-DscConfiguration</span></span>](Update-DscConfiguration.md)
