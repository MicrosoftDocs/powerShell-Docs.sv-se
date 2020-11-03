---
external help file: Get-DSCConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfiguration
ms.openlocfilehash: 42b24e72de4c4bcc9326d52861c08a05853b18e0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266078"
---
# <span data-ttu-id="65167-103">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="65167-103">Get-DscConfiguration</span></span>

## <span data-ttu-id="65167-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="65167-104">SYNOPSIS</span></span>
<span data-ttu-id="65167-105">Hämtar nodens aktuella konfiguration.</span><span class="sxs-lookup"><span data-stu-id="65167-105">Gets the current configuration of the nodes.</span></span>

## <span data-ttu-id="65167-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="65167-106">SYNTAX</span></span>

```
Get-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [<CommonParameters>]
```

## <span data-ttu-id="65167-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="65167-107">DESCRIPTION</span></span>
<span data-ttu-id="65167-108">Cmdlet: en **Get-DscConfiguration** hämtar den aktuella konfigurationen för noderna, om konfigurationen finns.</span><span class="sxs-lookup"><span data-stu-id="65167-108">The **Get-DscConfiguration** cmdlet gets the current configuration of the nodes, if the configuration exists.</span></span>
<span data-ttu-id="65167-109">Ange datorer med hjälp av Common Information Model (CIM)-sessioner.</span><span class="sxs-lookup"><span data-stu-id="65167-109">Specify computers by using Common Information Model (CIM) sessions.</span></span>
<span data-ttu-id="65167-110">Om du inte anger en måldator hämtar cmdleten konfigurationen från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="65167-110">If you do not specify a target computer, the cmdlet gets the configuration from the local computer.</span></span>

## <span data-ttu-id="65167-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="65167-111">EXAMPLES</span></span>

### <span data-ttu-id="65167-112">Exempel 1: Hämta konfigurationen för den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="65167-112">Example 1: Get the configuration for the local computer</span></span>

```
PS C:\> Get-DscConfiguration
```

<span data-ttu-id="65167-113">Det här kommandot hämtar det aktuella läget för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="65167-113">This command gets the current state for the local computer.</span></span>

### <span data-ttu-id="65167-114">Exempel 2: Hämta konfigurationen för en angiven dator</span><span class="sxs-lookup"><span data-stu-id="65167-114">Example 2: Get the configuration for a specified computer</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Get-DscConfiguration -CimSession $Session
```

<span data-ttu-id="65167-115">Det här exemplet hämtar det aktuella läget från en dator som anges av en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="65167-115">This example gets the current state from a computer specified by a CIM session.</span></span>
<span data-ttu-id="65167-116">I exemplet skapas en CIM-session för en dator med namnet Server01 för användning med cmdleten.</span><span class="sxs-lookup"><span data-stu-id="65167-116">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="65167-117">Du kan också skapa en matris med CIM-sessioner för att tillämpa cmdleten på flera angivna datorer.</span><span class="sxs-lookup"><span data-stu-id="65167-117">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="65167-118">Det första kommandot skapar en CIM-session med hjälp av cmdleten **New-CimSession** och lagrar sedan **CimSession** -objektet i variabeln **$session** .</span><span class="sxs-lookup"><span data-stu-id="65167-118">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the **$Session** variable.</span></span>
<span data-ttu-id="65167-119">I kommandot uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="65167-119">The command prompts you for a password.</span></span>
<span data-ttu-id="65167-120">För mer information ange `Get-Help New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="65167-120">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="65167-121">Det andra kommandot hämtar den aktuella konfigurationen för de datorer som identifieras av de **CimSession** -objekt som lagras i variabeln **$session** , i det här fallet datorn med namnet Server01.</span><span class="sxs-lookup"><span data-stu-id="65167-121">The second command gets the current configuration for the computers identified by the **CimSession** objects stored in the **$Session** variable, in this case, the computer named Server01.</span></span>

## <span data-ttu-id="65167-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="65167-122">PARAMETERS</span></span>

### <span data-ttu-id="65167-123">– AsJob</span><span class="sxs-lookup"><span data-stu-id="65167-123">-AsJob</span></span>
<span data-ttu-id="65167-124">Anger att denna cmdlet kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="65167-124">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="65167-125">– CimSession</span><span class="sxs-lookup"><span data-stu-id="65167-125">-CimSession</span></span>
<span data-ttu-id="65167-126">Kör cmdleten i en fjärran sluten session eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="65167-126">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="65167-127">Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en [New-CimSession-](/powershell/module/cimcmdlets/new-cimsession) eller [Get-CimSession-](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="65167-127">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="65167-128">Standardvärdet är den aktuella sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="65167-128">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="65167-129">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="65167-129">-ThrottleLimit</span></span>
<span data-ttu-id="65167-130">Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.</span><span class="sxs-lookup"><span data-stu-id="65167-130">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="65167-131">Om den här parametern utelämnas eller värdet `0` anges, beräknar Windows PowerShell en optimal begränsnings gräns för cmdleten baserat på antalet CIM-cmdletar som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="65167-131">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="65167-132">Begränsnings gränsen gäller endast för den aktuella cmdleten, inte sessionen eller till datorn.</span><span class="sxs-lookup"><span data-stu-id="65167-132">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="65167-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="65167-133">CommonParameters</span></span>
<span data-ttu-id="65167-134">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="65167-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="65167-135">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="65167-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="65167-136">INDATA</span><span class="sxs-lookup"><span data-stu-id="65167-136">INPUTS</span></span>

## <span data-ttu-id="65167-137">UTDATA</span><span class="sxs-lookup"><span data-stu-id="65167-137">OUTPUTS</span></span>

## <span data-ttu-id="65167-138">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="65167-138">NOTES</span></span>

## <span data-ttu-id="65167-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="65167-139">RELATED LINKS</span></span>

[<span data-ttu-id="65167-140">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="65167-140">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="65167-141">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="65167-141">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="65167-142">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="65167-142">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="65167-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="65167-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="65167-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="65167-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
