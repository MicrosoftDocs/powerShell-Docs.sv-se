---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageProvider
ms.openlocfilehash: fd8325f1a68755ee1b5c05719a04e71b22a7e9fd
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889491"
---
# <span data-ttu-id="853a5-102">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="853a5-102">Get-PackageProvider</span></span>

## <span data-ttu-id="853a5-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="853a5-103">SYNOPSIS</span></span>
<span data-ttu-id="853a5-104">Returnerar en lista med paket leverantörer som är anslutna till paket hantering.</span><span class="sxs-lookup"><span data-stu-id="853a5-104">Returns a list of package providers that are connected to Package Management.</span></span>

## <span data-ttu-id="853a5-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="853a5-105">SYNTAX</span></span>

```
Get-PackageProvider [[-Name] <String[]>] [-ListAvailable] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="853a5-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="853a5-106">DESCRIPTION</span></span>

<span data-ttu-id="853a5-107">Cmdlet **: en get-PackageProvider** returnerar en lista med paket leverantörer som är anslutna till paket hantering.</span><span class="sxs-lookup"><span data-stu-id="853a5-107">The **Get-PackageProvider** cmdlet returns a list of package providers that are connected to Package Management.</span></span>
<span data-ttu-id="853a5-108">Exempel på dessa leverantörer är PSModule, NuGet och choklad.</span><span class="sxs-lookup"><span data-stu-id="853a5-108">Examples of these providers include PSModule, NuGet, and Chocolatey.</span></span>
<span data-ttu-id="853a5-109">Du kan filtrera resultaten baserat på hela eller delar av ett eller flera providernamn.</span><span class="sxs-lookup"><span data-stu-id="853a5-109">You can filter the results based on all or part of one or more provider names.</span></span>

## <span data-ttu-id="853a5-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="853a5-110">EXAMPLES</span></span>

### <span data-ttu-id="853a5-111">Exempel 1: Hämta alla paket leverantörer som har lästs in</span><span class="sxs-lookup"><span data-stu-id="853a5-111">Example 1: Get all currently loaded package providers</span></span>

```
PS C:\> Get-PackageProvider
```

<span data-ttu-id="853a5-112">Det här kommandot hämtar en lista över alla paket leverantörer som för närvarande har lästs in på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="853a5-112">This command gets a list of all the package providers that are currently loaded on the local computer.</span></span>

### <span data-ttu-id="853a5-113">Exempel 2: Hämta alla tillgängliga paket leverantörer</span><span class="sxs-lookup"><span data-stu-id="853a5-113">Example 2: Get all available package providers</span></span>

```
PS C:\> Get-PackageProvider -ListAvailable
```

<span data-ttu-id="853a5-114">Det här kommandot hämtar en lista över alla paket leverantörer som är tillgängliga på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="853a5-114">This command gets a list of all package providers that are available on the local computer.</span></span>

### <span data-ttu-id="853a5-115">Exempel 3: Hämta en paket leverantör dynamiskt</span><span class="sxs-lookup"><span data-stu-id="853a5-115">Example 3: Dynamically get a package provider</span></span>

```
PS C:\> Get-PackageProvider -Name "Chocolatey" -ForceBootstrap
```

<span data-ttu-id="853a5-116">Med det här kommandot installeras choklad leverantören automatiskt om datorn inte har någon choklad-Provider installerad.</span><span class="sxs-lookup"><span data-stu-id="853a5-116">This command automatically installs the Chocolatey provider if your computer does not have the Chocolatey provider installed.</span></span>

## <span data-ttu-id="853a5-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="853a5-117">PARAMETERS</span></span>

### <span data-ttu-id="853a5-118">-Force</span><span class="sxs-lookup"><span data-stu-id="853a5-118">-Force</span></span>

<span data-ttu-id="853a5-119">Anger att denna cmdlet tvingar alla andra åtgärder med denna cmdlet som kan tvingas.</span><span class="sxs-lookup"><span data-stu-id="853a5-119">Indicates that this cmdlet forces all other actions with this cmdlet that can be forced.</span></span>
<span data-ttu-id="853a5-120">I **Get-PackageProvider** innebär detta att *Force* -parametern fungerar på samma sätt som parametern *ForceBootstrap* .</span><span class="sxs-lookup"><span data-stu-id="853a5-120">In **Get-PackageProvider**, this means the *Force* parameter acts the same as the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="853a5-121">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="853a5-121">-ForceBootstrap</span></span>

<span data-ttu-id="853a5-122">Anger att den här cmdleten tvingar paket hantering att automatiskt installera paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="853a5-122">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="853a5-123">– ListAvailable</span><span class="sxs-lookup"><span data-stu-id="853a5-123">-ListAvailable</span></span>

<span data-ttu-id="853a5-124">Hämtar alla installerade providrar.</span><span class="sxs-lookup"><span data-stu-id="853a5-124">Gets all installed providers.</span></span>
<span data-ttu-id="853a5-125">**Get-PackageProvider** hämtar providern i sökvägar som anges i miljövariabeln **PSModulePath** och paket providerns Assembly-mappar:</span><span class="sxs-lookup"><span data-stu-id="853a5-125">**Get-PackageProvider** gets provider in paths listed in the **PSModulePath** environment variable as well as the package provider assembly folders:</span></span>

<span data-ttu-id="853a5-126">**$env:P rogramFiles\PackageManagement\ProviderAssemblies \* \* \* \* $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies**</span><span class="sxs-lookup"><span data-stu-id="853a5-126">**$env:ProgramFiles\PackageManagement\ProviderAssemblies\*\*\*\*$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies**</span></span>

<span data-ttu-id="853a5-127">Utan den här parametern hämtar **Get-PackageProvider** bara de providrar som lästs in i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="853a5-127">Without this parameter, **Get-PackageProvider** gets only the providers loaded in the current session.</span></span>

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

### <span data-ttu-id="853a5-128">-Name</span><span class="sxs-lookup"><span data-stu-id="853a5-128">-Name</span></span>

<span data-ttu-id="853a5-129">Anger ett eller flera providernamn eller delar av leverantörs namn.</span><span class="sxs-lookup"><span data-stu-id="853a5-129">Specifies one or more provider names, or partial provider names.</span></span>
<span data-ttu-id="853a5-130">Separera flera providernamn med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="853a5-130">Separate multiple provider names with commas.</span></span>
<span data-ttu-id="853a5-131">Giltiga värden för den här parametern är namn på leverantörer som du har installerat med paket. PackageManagement levereras med en uppsättning standard leverantörer, inklusive **PSModule** -och **MSI** -providers.</span><span class="sxs-lookup"><span data-stu-id="853a5-131">Valid values for this parameter include names of providers that you have installed with packages; PackageManagement ships with a set of default providers, including the **PSModule** and **MSI** providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="853a5-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="853a5-132">CommonParameters</span></span>

<span data-ttu-id="853a5-133">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="853a5-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="853a5-134">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="853a5-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="853a5-135">INDATA</span><span class="sxs-lookup"><span data-stu-id="853a5-135">INPUTS</span></span>

## <span data-ttu-id="853a5-136">UTDATA</span><span class="sxs-lookup"><span data-stu-id="853a5-136">OUTPUTS</span></span>

### <span data-ttu-id="853a5-137">PackageProvider[]</span><span class="sxs-lookup"><span data-stu-id="853a5-137">PackageProvider[]</span></span>

## <span data-ttu-id="853a5-138">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="853a5-138">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="853a5-139">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="853a5-139">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="853a5-140">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="853a5-140">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="853a5-141">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="853a5-141">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="853a5-142">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="853a5-142">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="853a5-143">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="853a5-143">RELATED LINKS</span></span>

[<span data-ttu-id="853a5-144">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="853a5-144">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="853a5-145">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="853a5-145">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="853a5-146">Registrera – PackageSource</span><span class="sxs-lookup"><span data-stu-id="853a5-146">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="853a5-147">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="853a5-147">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
