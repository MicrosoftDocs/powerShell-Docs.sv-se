---
external help file: Get-DSCLocalConfigurationManager.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscLocalConfigurationManager
ms.openlocfilehash: 162770d8eb3a8953dcfaeb31f30742a46353b33b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266048"
---
# <span data-ttu-id="6dfe3-103">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6dfe3-103">Get-DscLocalConfigurationManager</span></span>

## <span data-ttu-id="6dfe3-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6dfe3-104">SYNOPSIS</span></span>

<span data-ttu-id="6dfe3-105">Hämtar inställningar och tillstånd för lokala Configuration Manager (LCM) för noden.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-105">Gets Local Configuration Manager (LCM) settings and states for the node.</span></span>

## <span data-ttu-id="6dfe3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6dfe3-106">SYNTAX</span></span>

```
Get-DscLocalConfigurationManager [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## <span data-ttu-id="6dfe3-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6dfe3-107">DESCRIPTION</span></span>

<span data-ttu-id="6dfe3-108">`Get-DscLocalConfigurationManager`Cmdleten hämtar LCM-inställningar eller meta-konfiguration och LCM för noden.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-108">The `Get-DscLocalConfigurationManager` cmdlet gets LCM settings, or meta-configuration, and the states of LCM for the node.</span></span> <span data-ttu-id="6dfe3-109">Ange datorer med hjälp av Common Information Model (CIM)-sessioner.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-109">Specify computers by using Common Information Model (CIM) sessions.</span></span> <span data-ttu-id="6dfe3-110">Om du inte anger en måldator hämtar cmdleten konfigurations inställningarna från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-110">If you do not specify a target computer, the cmdlet gets the configuration settings from the local computer.</span></span>

## <span data-ttu-id="6dfe3-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6dfe3-111">EXAMPLES</span></span>

### <span data-ttu-id="6dfe3-112">Exempel 1: Hämta LCM-inställningar för den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="6dfe3-112">Example 1: Get LCM settings for the local computer</span></span>

```powershell
Get-DscLocalConfigurationManager
```

```Output
ActionAfterReboot              : ContinueConfiguration
AgentId                        : 47edd8c9-2798-4827-839a-b35cc87e69fb
AllowModuleOverWrite           : False
CertificateID                  :
ConfigurationDownloadManagers  : {}
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 15
Credential                     :
DebugMode                      : {NONE}
DownloadManagerCustomData      :
DownloadManagerName            :
LCMCompatibleVersions          : {1.0, 2.0}
LCMState                       : Idle
LCMStateDetail                 :
LCMVersion                     : 2.0
StatusRetentionTimeInDays      : 10
SignatureValidationPolicy      : NONE
SignatureValidations           : {}
MaximumDownloadSizeMB          : 500
PartialConfigurations          :
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 30
RefreshMode                    : PUSH
ReportManagers                 : {}
ResourceModuleManagers         : {}
PSComputerName
```

<span data-ttu-id="6dfe3-113">Detta kommando hämtar LCM-inställningar för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-113">This command gets LCM settings for the local computer.</span></span>

<span data-ttu-id="6dfe3-114">Mer information om de enskilda attributen för utdata finns i [Konfigurera den lokala Configuration Manager](../../docs-conceptual/dsc/managing-nodes/metaconfig.md#basic-settings) -dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-114">For more information on the individual attributes of the output, see the [Configuring the Local Configuration Manager](../../docs-conceptual/dsc/managing-nodes/metaconfig.md#basic-settings) documentation.</span></span>

### <span data-ttu-id="6dfe3-115">Exempel 2: Hämta LCM-inställningar för en angiven dator</span><span class="sxs-lookup"><span data-stu-id="6dfe3-115">Example 2: Get LCM settings for a specified computer</span></span>

```powershell
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Get-DscLocalConfigurationManager -CimSession $Session
```

```Output
ActionAfterReboot              : ContinueConfiguration
AgentId                        : 169dfa57-a7f9-43be-a7a5-9dd06587e052
AllowModuleOverWrite           : False
CertificateID                  :
ConfigurationDownloadManagers  : {}
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 15
Credential                     :
DebugMode                      : {NONE}
DownloadManagerCustomData      :
DownloadManagerName            :
LCMCompatibleVersions          : {1.0, 2.0}
LCMState                       : Idle
LCMStateDetail                 :
LCMVersion                     : 2.0
StatusRetentionTimeInDays      : 10
SignatureValidationPolicy      : NONE
SignatureValidations           : {}
MaximumDownloadSizeMB          : 500
PartialConfigurations          :
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 30
RefreshMode                    : PUSH
ReportManagers                 : {}
ResourceModuleManagers         : {}
PSComputerName                 : Server01
PSComputerName                 : Server01
```

<span data-ttu-id="6dfe3-116">Det här exemplet hämtar LCM-inställningar för en dator som anges av en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-116">This example gets LCM settings for a computer specified by a CIM session.</span></span>
<span data-ttu-id="6dfe3-117">I exemplet skapas en CIM-session för en dator med namnet Server01 för användning med cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-117">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="6dfe3-118">Du kan också skapa en matris med CIM-sessioner för att tillämpa cmdleten på flera angivna datorer.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-118">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="6dfe3-119">Det första kommandot skapar en CIM-session med hjälp av `New-CimSession` cmdleten och lagrar sedan **CimSession** -objektet i variabeln $session.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-119">The first command creates a CIM session by using the `New-CimSession` cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span> <span data-ttu-id="6dfe3-120">I kommandot uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-120">The command prompts you for a password.</span></span> <span data-ttu-id="6dfe3-121">För mer information ange `Get-Help New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-121">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="6dfe3-122">Det andra kommandot hämtar lokala Configuration Manager inställningar för de datorer som identifieras av de **CimSession** -objekt som lagras i $session-variabeln.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-122">The second command gets Local Configuration Manager settings for the computers identified by the **CimSession** objects stored in the $Session variable.</span></span> <span data-ttu-id="6dfe3-123">I det här fallet datorn med namnet Server01.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-123">In this case, the computer named Server01.</span></span>

## <span data-ttu-id="6dfe3-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6dfe3-124">PARAMETERS</span></span>

### <span data-ttu-id="6dfe3-125">– AsJob</span><span class="sxs-lookup"><span data-stu-id="6dfe3-125">-AsJob</span></span>

<span data-ttu-id="6dfe3-126">Anger att denna cmdlet kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-126">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="6dfe3-127">– CimSession</span><span class="sxs-lookup"><span data-stu-id="6dfe3-127">-CimSession</span></span>

<span data-ttu-id="6dfe3-128">Kör cmdleten i en fjärran sluten session eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-128">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="6dfe3-129">Ange ett dator namn eller ett sessionsobjekt, till exempel utdata för en- `New-CimSession` eller- `Get-CimSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-129">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span>

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

### <span data-ttu-id="6dfe3-130">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6dfe3-130">-ThrottleLimit</span></span>

<span data-ttu-id="6dfe3-131">Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-131">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>

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

### <span data-ttu-id="6dfe3-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6dfe3-132">CommonParameters</span></span>

<span data-ttu-id="6dfe3-133">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6dfe3-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6dfe3-134">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6dfe3-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6dfe3-135">INDATA</span><span class="sxs-lookup"><span data-stu-id="6dfe3-135">INPUTS</span></span>

## <span data-ttu-id="6dfe3-136">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6dfe3-136">OUTPUTS</span></span>

## <span data-ttu-id="6dfe3-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6dfe3-137">NOTES</span></span>

## <span data-ttu-id="6dfe3-138">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6dfe3-138">RELATED LINKS</span></span>

[<span data-ttu-id="6dfe3-139">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6dfe3-139">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="6dfe3-140">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6dfe3-140">Set-DscLocalConfigurationManager</span></span>](Set-DscLocalConfigurationManager.md)
