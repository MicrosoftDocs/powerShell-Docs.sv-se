---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: 997d86460837946a2cf18fc78f058f21472dd909
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266109"
---
# <span data-ttu-id="ca979-103">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="ca979-103">Get-PSProvider</span></span>

## <span data-ttu-id="ca979-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ca979-104">SYNOPSIS</span></span>
<span data-ttu-id="ca979-105">Hämtar information om den angivna Windows PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="ca979-105">Gets information about the specified Windows PowerShell provider.</span></span>

## <span data-ttu-id="ca979-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ca979-106">SYNTAX</span></span>

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="ca979-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ca979-107">DESCRIPTION</span></span>
<span data-ttu-id="ca979-108">Cmdlet **: en get-PSProvider** hämtar Windows PowerShell-providers i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ca979-108">The **Get-PSProvider** cmdlet gets the Windows PowerShell providers in the current session.</span></span>
<span data-ttu-id="ca979-109">Du kan hämta en viss enhet eller alla enheter i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ca979-109">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="ca979-110">Med Windows PowerShell-providers kan du komma åt olika data lager som om de vore fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="ca979-110">Windows PowerShell providers let you access a variety of data stores as though they were file system drives.</span></span>
<span data-ttu-id="ca979-111">Information om Windows PowerShell-leverantörer finns about_Providers.</span><span class="sxs-lookup"><span data-stu-id="ca979-111">For information about Windows PowerShell providers, see about_Providers.</span></span>

## <span data-ttu-id="ca979-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ca979-112">EXAMPLES</span></span>

### <span data-ttu-id="ca979-113">Exempel 1: Visa en lista över alla tillgängliga providers</span><span class="sxs-lookup"><span data-stu-id="ca979-113">Example 1: Display a list of all available providers</span></span>

```
PS C:\> Get-PSProvider
```

<span data-ttu-id="ca979-114">Det här kommandot visar en lista över alla tillgängliga Windows PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="ca979-114">This command displays a list of all available Windows PowerShell providers.</span></span>

### <span data-ttu-id="ca979-115">Exempel 2: Visa en lista över alla Windows PowerShell-leverantörer som börjar med angivna bokstäver</span><span class="sxs-lookup"><span data-stu-id="ca979-115">Example 2: Display a list of all Windows PowerShell providers that begin with specified letters</span></span>

```
PS C:\> Get-PSProvider f*, r* | Format-List
```

<span data-ttu-id="ca979-116">Det här kommandot visar en lista över alla Windows PowerShell-leverantörer med namn som börjar med bokstaven f eller r.</span><span class="sxs-lookup"><span data-stu-id="ca979-116">This command displays a list of all Windows PowerShell providers with names that begin with the letter f or r.</span></span>

### <span data-ttu-id="ca979-117">Exempel 3: Sök efter snapin-moduler eller moduler som har lagts till providers i sessionen</span><span class="sxs-lookup"><span data-stu-id="ca979-117">Example 3: Find snap-ins or module that added providers to your session</span></span>

```
PS C:\> Get-PSProvider | Format-Table name, module, pssnapin -auto

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

PS C:\> Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}

Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

<span data-ttu-id="ca979-118">Kommandona hittar de Windows PowerShell-snapin-moduler eller moduler som har lagt till providrar i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ca979-118">These commands find the Windows PowerShell snap-ins or modules that added providers to your session.</span></span>
<span data-ttu-id="ca979-119">Alla Windows PowerShell-element, inklusive providers, har sitt ursprung i en snapin-modul eller i en modul.</span><span class="sxs-lookup"><span data-stu-id="ca979-119">All Windows PowerShell elements, including providers, originate in a snap-in or in a module.</span></span>

<span data-ttu-id="ca979-120">Dessa kommandon använder egenskaperna PSSnapin och module för **ProviderInfo** -objektet som returnerar **-PSProvider** returnerar.</span><span class="sxs-lookup"><span data-stu-id="ca979-120">These commands use the PSSnapin and Module properties of the **ProviderInfo** object that **Get-PSProvider** returns.</span></span>
<span data-ttu-id="ca979-121">Värdena för dessa egenskaper innehåller namnet på snapin-modulen eller modulen som lägger till providern.</span><span class="sxs-lookup"><span data-stu-id="ca979-121">The values of these properties contain the name of the snap-in or module that adds the provider.</span></span>

<span data-ttu-id="ca979-122">Det första kommandot hämtar alla providers i sessionen och formaterar dem i en tabell med värdena för deras namn, modul och egenskaper för PSSnapin.</span><span class="sxs-lookup"><span data-stu-id="ca979-122">The first command gets all of the providers in the session and formats them in a table with the values of their Name, Module, and PSSnapin properties.</span></span>

<span data-ttu-id="ca979-123">Det andra kommandot använder cmdleten Where-Object för att hämta de leverantörer som kommer från snapin-modulen **Microsoft. PowerShell. Security** .</span><span class="sxs-lookup"><span data-stu-id="ca979-123">The second command uses the Where-Object cmdlet to get the providers that come from the **Microsoft.PowerShell.Security** snap-in.</span></span>

### <span data-ttu-id="ca979-124">Exempel 4: matcha sökvägen för fil system leverantörens start egenskap</span><span class="sxs-lookup"><span data-stu-id="ca979-124">Example 4: Resolve the path of the Home property of the file system provider</span></span>

```
PS C:\> Resolve-Path ~

Path
----
C:\Users\User01

PS C:\> (get-psprovider FileSystem).home
C:\Users\User01
```

<span data-ttu-id="ca979-125">Det här exemplet visar att Tilde-symbolen (~) representerar värdet för fil systemets start egenskap.</span><span class="sxs-lookup"><span data-stu-id="ca979-125">This example shows that the tilde symbol (~) represents the value of the Home property of the FileSystem provider.</span></span>
<span data-ttu-id="ca979-126">Värdet för start egenskapen är valfritt, men för fil Systems leverantören definieras det som $env: HOMEDRIVE \$ miljö: HOMEPATH eller $Home.</span><span class="sxs-lookup"><span data-stu-id="ca979-126">The Home property value is optional, but for the FileSystem provider, it is defined as $env:homedrive\$env:homepath or $home.</span></span>

## <span data-ttu-id="ca979-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ca979-127">PARAMETERS</span></span>

### <span data-ttu-id="ca979-128">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="ca979-128">-PSProvider</span></span>
<span data-ttu-id="ca979-129">Anger namn eller namn på de Windows PowerShell-leverantörer som den här cmdlet: en hämtar information om.</span><span class="sxs-lookup"><span data-stu-id="ca979-129">Specifies the name or names of the Windows PowerShell providers about which this cmdlet gets information.</span></span>

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

### <span data-ttu-id="ca979-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ca979-130">CommonParameters</span></span>
<span data-ttu-id="ca979-131">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ca979-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ca979-132">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ca979-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ca979-133">INDATA</span><span class="sxs-lookup"><span data-stu-id="ca979-133">INPUTS</span></span>

### <span data-ttu-id="ca979-134">Sträng []</span><span class="sxs-lookup"><span data-stu-id="ca979-134">String[]</span></span>

<span data-ttu-id="ca979-135">Du kan skicka en eller flera providers namn strängar till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ca979-135">You can pipe one or more provider name strings to this cmdlet.</span></span>

## <span data-ttu-id="ca979-136">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ca979-136">OUTPUTS</span></span>

### <span data-ttu-id="ca979-137">System. Management. Automation. ProviderInfo</span><span class="sxs-lookup"><span data-stu-id="ca979-137">System.Management.Automation.ProviderInfo</span></span>
<span data-ttu-id="ca979-138">Denna cmdlet returnerar objekt som representerar Windows PowerShell-providers i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ca979-138">This cmdlet returns objects that represent the Windows PowerShell providers in the session.</span></span>

## <span data-ttu-id="ca979-139">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ca979-139">NOTES</span></span>

## <span data-ttu-id="ca979-140">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ca979-140">RELATED LINKS</span></span>

## <span data-ttu-id="ca979-141">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ca979-141">RELATED LINKS</span></span>
