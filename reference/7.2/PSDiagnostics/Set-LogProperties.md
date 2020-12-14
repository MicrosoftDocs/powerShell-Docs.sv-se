---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/set-logproperties?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LogProperties
ms.openlocfilehash: 51bb791e0633cf172252f5b0dca22373bb065fcc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710290"
---
# <span data-ttu-id="1de94-102">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="1de94-102">Set-LogProperties</span></span>

## <span data-ttu-id="1de94-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1de94-103">SYNOPSIS</span></span>
<span data-ttu-id="1de94-104">Ändrar egenskaperna för en händelse logg i Windows.</span><span class="sxs-lookup"><span data-stu-id="1de94-104">Changes the properties of a Windows event log.</span></span>

## <span data-ttu-id="1de94-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1de94-105">SYNTAX</span></span>

```
Set-LogProperties [-LogDetails] <LogDetails> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="1de94-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1de94-106">DESCRIPTION</span></span>

<span data-ttu-id="1de94-107">Den här cmdleten ändrar konfigurations inställningarna för en händelse logg i Windows.</span><span class="sxs-lookup"><span data-stu-id="1de94-107">This cmdlet changes the configuration settings of a Windows event log.</span></span> <span data-ttu-id="1de94-108">Denna cmdlet används av `Enable-PSTrace` `Disable-PSTrace` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="1de94-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

<span data-ttu-id="1de94-109">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="1de94-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="1de94-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1de94-110">EXAMPLES</span></span>

### <span data-ttu-id="1de94-111">Exempel 1: ändra inställningen kvarhållning för händelse loggen i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1de94-111">Example 1: Change the retention setting of the Windows PowerShell event log</span></span>

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

## <span data-ttu-id="1de94-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1de94-112">PARAMETERS</span></span>

### <span data-ttu-id="1de94-113">-Force</span><span class="sxs-lookup"><span data-stu-id="1de94-113">-Force</span></span>

<span data-ttu-id="1de94-114">Används för att framtvinga ändringen utan att du behöver göra något.</span><span class="sxs-lookup"><span data-stu-id="1de94-114">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="1de94-115">-LogDetails</span><span class="sxs-lookup"><span data-stu-id="1de94-115">-LogDetails</span></span>

<span data-ttu-id="1de94-116">De uppdaterade konfigurations inställningarna som ska tilldelas händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="1de94-116">The updated configuration settings to be assigned to the event log.</span></span>

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

### <span data-ttu-id="1de94-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1de94-117">CommonParameters</span></span>

<span data-ttu-id="1de94-118">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1de94-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1de94-119">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1de94-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1de94-120">INDATA</span><span class="sxs-lookup"><span data-stu-id="1de94-120">INPUTS</span></span>

### <span data-ttu-id="1de94-121">Microsoft. PowerShell. Diagnostics. LogDetails</span><span class="sxs-lookup"><span data-stu-id="1de94-121">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="1de94-122">Du måste skicka ett fullständigt konfigurerat **LogDetails** -objekt till `Set-LogProperties` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1de94-122">You must pass a fully configured **LogDetails** object to the `Set-LogProperties` cmdlet.</span></span>
<span data-ttu-id="1de94-123">Därför bör du använda `Get-LogProperties` för att hämta den aktuella konfigurationen om du vill ändra en inställning.</span><span class="sxs-lookup"><span data-stu-id="1de94-123">Therefore, to change one setting, you should use `Get-LogProperties` to retrieve the current configuration.</span></span>

## <span data-ttu-id="1de94-124">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1de94-124">OUTPUTS</span></span>

### <span data-ttu-id="1de94-125">Inga</span><span class="sxs-lookup"><span data-stu-id="1de94-125">None</span></span>

## <span data-ttu-id="1de94-126">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1de94-126">NOTES</span></span>

<span data-ttu-id="1de94-127">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="1de94-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="1de94-128">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1de94-128">RELATED LINKS</span></span>

[<span data-ttu-id="1de94-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="1de94-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="1de94-130">Aktivera – PSTrace</span><span class="sxs-lookup"><span data-stu-id="1de94-130">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="1de94-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="1de94-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)

