---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: 20820d2d194f41d43048c9617b63b9acb3fbb4f8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709505"
---
# <span data-ttu-id="78fb4-102">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="78fb4-102">Get-PSProvider</span></span>

## <span data-ttu-id="78fb4-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="78fb4-103">SYNOPSIS</span></span>
<span data-ttu-id="78fb4-104">Hämtar information om den angivna PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="78fb4-104">Gets information about the specified PowerShell provider.</span></span>

## <span data-ttu-id="78fb4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="78fb4-105">SYNTAX</span></span>

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="78fb4-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="78fb4-106">DESCRIPTION</span></span>

<span data-ttu-id="78fb4-107">`Get-PSProvider`Cmdlet: en hämtar PowerShell-providern i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="78fb4-107">The `Get-PSProvider` cmdlet gets the PowerShell providers in the current session.</span></span>
<span data-ttu-id="78fb4-108">Du kan hämta en viss enhet eller alla enheter i sessionen.</span><span class="sxs-lookup"><span data-stu-id="78fb4-108">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="78fb4-109">Med PowerShell-providers kan du komma åt olika data lager som om de vore fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="78fb4-109">PowerShell providers let you access a variety of data stores as though they were file system drives.</span></span>
<span data-ttu-id="78fb4-110">Information om PowerShell-leverantörer finns [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="78fb4-110">For information about PowerShell providers, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="78fb4-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="78fb4-111">EXAMPLES</span></span>

### <span data-ttu-id="78fb4-112">Exempel 1: Visa en lista över alla tillgängliga providers</span><span class="sxs-lookup"><span data-stu-id="78fb4-112">Example 1: Display a list of all available providers</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="78fb4-113">Det här kommandot visar en lista över alla tillgängliga PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="78fb4-113">This command displays a list of all available PowerShell providers.</span></span>

### <span data-ttu-id="78fb4-114">Exempel 2: Visa en lista över alla PowerShell-leverantörer som börjar med angivna bokstäver</span><span class="sxs-lookup"><span data-stu-id="78fb4-114">Example 2: Display a list of all PowerShell providers that begin with specified letters</span></span>

```powershell
Get-PSProvider f*, r* | Format-List
```

<span data-ttu-id="78fb4-115">Det här kommandot visar en lista över alla PowerShell-leverantörer med namn som börjar med bokstaven f eller r.</span><span class="sxs-lookup"><span data-stu-id="78fb4-115">This command displays a list of all PowerShell providers with names that begin with the letter f or r.</span></span>

### <span data-ttu-id="78fb4-116">Exempel 3: Sök efter snapin-moduler eller moduler som har lagts till providers i sessionen</span><span class="sxs-lookup"><span data-stu-id="78fb4-116">Example 3: Find snap-ins or module that added providers to your session</span></span>

```powershell
Get-PSProvider | Format-Table name, module, pssnapin -auto
```

```Output
Name        Module       PSSnapIn
----        ------       --------
Test        TestModule
WSMan                    Microsoft.WSMan.Management
Alias                    Microsoft.PowerShell.Core
Environment              Microsoft.PowerShell.Core
FileSystem               Microsoft.PowerShell.Core
Function                 Microsoft.PowerShell.Core
Registry                 Microsoft.PowerShell.Core
Variable                 Microsoft.PowerShell.Core
Certificate              Microsoft.PowerShell.Security
```

```powershell
Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}
```

```Output
Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

<span data-ttu-id="78fb4-117">Kommandona hittar PowerShell-snapin-modulerna eller moduler som har lagt till providrar i sessionen.</span><span class="sxs-lookup"><span data-stu-id="78fb4-117">These commands find the PowerShell snap-ins or modules that added providers to your session.</span></span>
<span data-ttu-id="78fb4-118">Alla PowerShell-element, inklusive providers, har sitt ursprung i en snapin-modul eller i en modul.</span><span class="sxs-lookup"><span data-stu-id="78fb4-118">All PowerShell elements, including providers, originate in a snap-in or in a module.</span></span>

<span data-ttu-id="78fb4-119">Dessa kommandon använder egenskaperna PSSnapin och module för det **ProviderInfo** -objekt som `Get-PSProvider` returneras.</span><span class="sxs-lookup"><span data-stu-id="78fb4-119">These commands use the PSSnapin and Module properties of the **ProviderInfo** object that `Get-PSProvider` returns.</span></span>
<span data-ttu-id="78fb4-120">Värdena för dessa egenskaper innehåller namnet på snapin-modulen eller modulen som lägger till providern.</span><span class="sxs-lookup"><span data-stu-id="78fb4-120">The values of these properties contain the name of the snap-in or module that adds the provider.</span></span>

<span data-ttu-id="78fb4-121">Det första kommandot hämtar alla providers i sessionen och formaterar dem i en tabell med värdena för deras namn, modul och egenskaper för PSSnapin.</span><span class="sxs-lookup"><span data-stu-id="78fb4-121">The first command gets all of the providers in the session and formats them in a table with the values of their Name, Module, and PSSnapin properties.</span></span>

<span data-ttu-id="78fb4-122">Det andra kommandot använder `Where-Object` cmdleten för att hämta de providrar som kommer från snapin-modulen **Microsoft. PowerShell. Security** .</span><span class="sxs-lookup"><span data-stu-id="78fb4-122">The second command uses the `Where-Object` cmdlet to get the providers that come from the **Microsoft.PowerShell.Security** snap-in.</span></span>

### <span data-ttu-id="78fb4-123">Exempel 4: matcha sökvägen för fil system leverantörens start egenskap</span><span class="sxs-lookup"><span data-stu-id="78fb4-123">Example 4: Resolve the path of the Home property of the file system provider</span></span>

```powershell
C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

```powershell
PS C:\> (get-psprovider FileSystem).home
```

```Output
C:\Users\User01
```

<span data-ttu-id="78fb4-124">Det här exemplet visar att Tilde-symbolen (~) representerar värdet för fil systemets **Start** egenskap.</span><span class="sxs-lookup"><span data-stu-id="78fb4-124">This example shows that the tilde symbol (~) represents the value of the **Home** property of the FileSystem provider.</span></span>
<span data-ttu-id="78fb4-125">Värdet för **Start** egenskapen är valfritt, men för **fil Systems** leverantören definieras det som `$env:homedrive\$env:homepath` eller `$home` .</span><span class="sxs-lookup"><span data-stu-id="78fb4-125">The **Home** property value is optional, but for the **FileSystem** provider, it is defined as `$env:homedrive\$env:homepath` or `$home`.</span></span>

## <span data-ttu-id="78fb4-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="78fb4-126">PARAMETERS</span></span>

### <span data-ttu-id="78fb4-127">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="78fb4-127">-PSProvider</span></span>

<span data-ttu-id="78fb4-128">Anger namnet eller namnen på de PowerShell-leverantörer som denna cmdlet hämtar information om.</span><span class="sxs-lookup"><span data-stu-id="78fb4-128">Specifies the name or names of the PowerShell providers about which this cmdlet gets information.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="78fb4-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="78fb4-129">CommonParameters</span></span>

<span data-ttu-id="78fb4-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="78fb4-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="78fb4-131">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="78fb4-131">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="78fb4-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="78fb4-132">INPUTS</span></span>

### <span data-ttu-id="78fb4-133">Sträng []</span><span class="sxs-lookup"><span data-stu-id="78fb4-133">String[]</span></span>

<span data-ttu-id="78fb4-134">Du kan skicka en eller flera providers namn strängar till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="78fb4-134">You can pipe one or more provider name strings to this cmdlet.</span></span>

## <span data-ttu-id="78fb4-135">UTDATA</span><span class="sxs-lookup"><span data-stu-id="78fb4-135">OUTPUTS</span></span>

### <span data-ttu-id="78fb4-136">System. Management. Automation. ProviderInfo</span><span class="sxs-lookup"><span data-stu-id="78fb4-136">System.Management.Automation.ProviderInfo</span></span>

<span data-ttu-id="78fb4-137">Denna cmdlet returnerar objekt som representerar PowerShell-providern i sessionen.</span><span class="sxs-lookup"><span data-stu-id="78fb4-137">This cmdlet returns objects that represent the PowerShell providers in the session.</span></span>

## <span data-ttu-id="78fb4-138">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="78fb4-138">NOTES</span></span>

## <span data-ttu-id="78fb4-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="78fb4-139">RELATED LINKS</span></span>

