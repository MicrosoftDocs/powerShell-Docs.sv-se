---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/set-logproperties?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LogProperties
ms.openlocfilehash: baf737a649e96488aff10959e02b59a0323e3ac4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262106"
---
# <span data-ttu-id="8abfb-102">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="8abfb-102">Set-LogProperties</span></span>

## <span data-ttu-id="8abfb-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8abfb-103">SYNOPSIS</span></span>
<span data-ttu-id="8abfb-104">Ändrar egenskaperna för en händelse logg i Windows.</span><span class="sxs-lookup"><span data-stu-id="8abfb-104">Changes the properties of a Windows event log.</span></span>

## <span data-ttu-id="8abfb-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8abfb-105">SYNTAX</span></span>

```
Set-LogProperties [-LogDetails] <LogDetails> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="8abfb-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8abfb-106">DESCRIPTION</span></span>

<span data-ttu-id="8abfb-107">Den här cmdleten ändrar konfigurations inställningarna för en händelse logg i Windows.</span><span class="sxs-lookup"><span data-stu-id="8abfb-107">This cmdlet changes the configuration settings of a Windows event log.</span></span> <span data-ttu-id="8abfb-108">Denna cmdlet används av `Enable-PSTrace` `Disable-PSTrace` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="8abfb-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

<span data-ttu-id="8abfb-109">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="8abfb-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="8abfb-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8abfb-110">EXAMPLES</span></span>

### <span data-ttu-id="8abfb-111">Exempel 1: ändra inställningen kvarhållning för händelse loggen i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8abfb-111">Example 1: Change the retention setting of the Windows PowerShell event log</span></span>

```powershell
$logDetails = Get-LogProperties 'Windows PowerShell'
$logDetails.Retention = $True
Set-LogProperties -LogDetails $logDetails
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : True
AutoBackup : False
MaxLogSize : 15728640
```

## <span data-ttu-id="8abfb-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8abfb-112">PARAMETERS</span></span>

### <span data-ttu-id="8abfb-113">-Force</span><span class="sxs-lookup"><span data-stu-id="8abfb-113">-Force</span></span>

<span data-ttu-id="8abfb-114">Används för att framtvinga ändringen utan att du behöver göra något.</span><span class="sxs-lookup"><span data-stu-id="8abfb-114">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="8abfb-115">-LogDetails</span><span class="sxs-lookup"><span data-stu-id="8abfb-115">-LogDetails</span></span>

<span data-ttu-id="8abfb-116">De uppdaterade konfigurations inställningarna som ska tilldelas händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="8abfb-116">The updated configuration settings to be assigned to the event log.</span></span>

```yaml
Type: Microsoft.PowerShell.Diagnostics.LogDetails
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8abfb-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8abfb-117">CommonParameters</span></span>

<span data-ttu-id="8abfb-118">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8abfb-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8abfb-119">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8abfb-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8abfb-120">INDATA</span><span class="sxs-lookup"><span data-stu-id="8abfb-120">INPUTS</span></span>

### <span data-ttu-id="8abfb-121">Microsoft. PowerShell. Diagnostics. LogDetails</span><span class="sxs-lookup"><span data-stu-id="8abfb-121">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="8abfb-122">Du måste skicka ett fullständigt konfigurerat **LogDetails** -objekt till `Set-LogProperties` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8abfb-122">You must pass a fully configured **LogDetails** object to the `Set-LogProperties` cmdlet.</span></span>
<span data-ttu-id="8abfb-123">Därför bör du använda `Get-LogProperties` för att hämta den aktuella konfigurationen om du vill ändra en inställning.</span><span class="sxs-lookup"><span data-stu-id="8abfb-123">Therefore, to change one setting, you should use `Get-LogProperties` to retrieve the current configuration.</span></span>

## <span data-ttu-id="8abfb-124">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8abfb-124">OUTPUTS</span></span>

### <span data-ttu-id="8abfb-125">Inget</span><span class="sxs-lookup"><span data-stu-id="8abfb-125">None</span></span>

## <span data-ttu-id="8abfb-126">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8abfb-126">NOTES</span></span>

<span data-ttu-id="8abfb-127">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="8abfb-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="8abfb-128">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8abfb-128">RELATED LINKS</span></span>

[<span data-ttu-id="8abfb-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="8abfb-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="8abfb-130">Aktivera – PSTrace</span><span class="sxs-lookup"><span data-stu-id="8abfb-130">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="8abfb-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="8abfb-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)
