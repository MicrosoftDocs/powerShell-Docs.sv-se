---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/get-logproperties?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LogProperties
ms.openlocfilehash: f532dd3ff46f14348437de531e80e94b192b13e8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709307"
---
# <span data-ttu-id="4fc48-102">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="4fc48-102">Get-LogProperties</span></span>

## <span data-ttu-id="4fc48-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4fc48-103">SYNOPSIS</span></span>
<span data-ttu-id="4fc48-104">Hämtar egenskaperna för en händelse logg i Windows.</span><span class="sxs-lookup"><span data-stu-id="4fc48-104">Retrieves the properties of a Windows event log.</span></span>

## <span data-ttu-id="4fc48-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4fc48-105">SYNTAX</span></span>

```
Get-LogProperties [-Name] <Object> [<CommonParameters>]
```

## <span data-ttu-id="4fc48-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4fc48-106">DESCRIPTION</span></span>

<span data-ttu-id="4fc48-107">Den här cmdleten hämtar konfigurations inställningarna för en händelse logg i Windows.</span><span class="sxs-lookup"><span data-stu-id="4fc48-107">This cmdlet gets the configuration settings of a Windows event log.</span></span> <span data-ttu-id="4fc48-108">Denna cmdlet används av `Enable-PSTrace` `Disable-PSTrace` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="4fc48-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

## <span data-ttu-id="4fc48-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4fc48-109">EXAMPLES</span></span>

### <span data-ttu-id="4fc48-110">Exempel 1: hämta konfigurations inställningarna för händelse loggen i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4fc48-110">Example 1: Get the configuration settings of the Windows PowerShell event log</span></span>

```powershell
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : False
AutoBackup : False
MaxLogSize : 15728640
```

## <span data-ttu-id="4fc48-111">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4fc48-111">PARAMETERS</span></span>

### <span data-ttu-id="4fc48-112">-Name</span><span class="sxs-lookup"><span data-stu-id="4fc48-112">-Name</span></span>

<span data-ttu-id="4fc48-113">Namnet på händelse leverantören.</span><span class="sxs-lookup"><span data-stu-id="4fc48-113">The name of the event provider.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4fc48-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4fc48-114">CommonParameters</span></span>

<span data-ttu-id="4fc48-115">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4fc48-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4fc48-116">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4fc48-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4fc48-117">INDATA</span><span class="sxs-lookup"><span data-stu-id="4fc48-117">INPUTS</span></span>

### <span data-ttu-id="4fc48-118">System. String</span><span class="sxs-lookup"><span data-stu-id="4fc48-118">System.String</span></span>

## <span data-ttu-id="4fc48-119">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4fc48-119">OUTPUTS</span></span>

### <span data-ttu-id="4fc48-120">Microsoft. PowerShell. Diagnostics. LogDetails</span><span class="sxs-lookup"><span data-stu-id="4fc48-120">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="4fc48-121">**PSDiagnostics** -modulen lägger till **LogDetails** -klassen i `Microsoft.PowerShell.Diagnostics` namn området.</span><span class="sxs-lookup"><span data-stu-id="4fc48-121">The **PSDiagnostics** module adds the **LogDetails** class to the `Microsoft.PowerShell.Diagnostics` namespace.</span></span>

## <span data-ttu-id="4fc48-122">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4fc48-122">NOTES</span></span>

## <span data-ttu-id="4fc48-123">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4fc48-123">RELATED LINKS</span></span>

[<span data-ttu-id="4fc48-124">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="4fc48-124">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="4fc48-125">Aktivera – PSTrace</span><span class="sxs-lookup"><span data-stu-id="4fc48-125">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="4fc48-126">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="4fc48-126">Disable-PSTrace</span></span>](Disable-PSTrace.md)

