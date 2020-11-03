---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
Locale: en-US
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/get-logproperties?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LogProperties
ms.openlocfilehash: 08638749b7a5bb57bee804fccf9de17f50fd6736
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262641"
---
# <span data-ttu-id="f2a12-102">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="f2a12-102">Get-LogProperties</span></span>

## <span data-ttu-id="f2a12-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f2a12-103">SYNOPSIS</span></span>
<span data-ttu-id="f2a12-104">Hämtar egenskaperna för en händelse logg i Windows.</span><span class="sxs-lookup"><span data-stu-id="f2a12-104">Retrieves the properties of a Windows event log.</span></span>

## <span data-ttu-id="f2a12-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f2a12-105">SYNTAX</span></span>

```
Get-LogProperties [-Name] <Object> [<CommonParameters>]
```

## <span data-ttu-id="f2a12-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f2a12-106">DESCRIPTION</span></span>

<span data-ttu-id="f2a12-107">Den här cmdleten hämtar konfigurations inställningarna för en händelse logg i Windows.</span><span class="sxs-lookup"><span data-stu-id="f2a12-107">This cmdlet gets the configuration settings of a Windows event log.</span></span> <span data-ttu-id="f2a12-108">Denna cmdlet används av `Enable-PSTrace` `Disable-PSTrace` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="f2a12-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

## <span data-ttu-id="f2a12-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f2a12-109">EXAMPLES</span></span>

### <span data-ttu-id="f2a12-110">Exempel 1: hämta konfigurations inställningarna för händelse loggen i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2a12-110">Example 1: Get the configuration settings of the Windows PowerShell event log</span></span>

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

## <span data-ttu-id="f2a12-111">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f2a12-111">PARAMETERS</span></span>

### <span data-ttu-id="f2a12-112">-Name</span><span class="sxs-lookup"><span data-stu-id="f2a12-112">-Name</span></span>

<span data-ttu-id="f2a12-113">Namnet på händelse leverantören.</span><span class="sxs-lookup"><span data-stu-id="f2a12-113">The name of the event provider.</span></span>

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

### <span data-ttu-id="f2a12-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f2a12-114">CommonParameters</span></span>

<span data-ttu-id="f2a12-115">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f2a12-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f2a12-116">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f2a12-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f2a12-117">INDATA</span><span class="sxs-lookup"><span data-stu-id="f2a12-117">INPUTS</span></span>

### <span data-ttu-id="f2a12-118">System. String</span><span class="sxs-lookup"><span data-stu-id="f2a12-118">System.String</span></span>

## <span data-ttu-id="f2a12-119">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f2a12-119">OUTPUTS</span></span>

### <span data-ttu-id="f2a12-120">Microsoft. PowerShell. Diagnostics. LogDetails</span><span class="sxs-lookup"><span data-stu-id="f2a12-120">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="f2a12-121">**PSDiagnostics** -modulen lägger till **LogDetails** -klassen i `Microsoft.PowerShell.Diagnostics` namn området.</span><span class="sxs-lookup"><span data-stu-id="f2a12-121">The **PSDiagnostics** module adds the **LogDetails** class to the `Microsoft.PowerShell.Diagnostics` namespace.</span></span>

## <span data-ttu-id="f2a12-122">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f2a12-122">NOTES</span></span>

## <span data-ttu-id="f2a12-123">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f2a12-123">RELATED LINKS</span></span>

[<span data-ttu-id="f2a12-124">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="f2a12-124">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="f2a12-125">Aktivera – PSTrace</span><span class="sxs-lookup"><span data-stu-id="f2a12-125">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="f2a12-126">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="f2a12-126">Disable-PSTrace</span></span>](Disable-PSTrace.md)
