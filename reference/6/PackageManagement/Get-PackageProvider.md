---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packageprovider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageProvider
ms.openlocfilehash: 85471e6f884d785ec8a5a253a57b1fb13b3a446b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265695"
---
# <span data-ttu-id="95585-103">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="95585-103">Get-PackageProvider</span></span>

## <span data-ttu-id="95585-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="95585-104">SYNOPSIS</span></span>
<span data-ttu-id="95585-105">Returnerar en lista med paket leverantörer som är anslutna till paket hantering.</span><span class="sxs-lookup"><span data-stu-id="95585-105">Returns a list of package providers that are connected to Package Management.</span></span>

## <span data-ttu-id="95585-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="95585-106">SYNTAX</span></span>

```
Get-PackageProvider [[-Name] <String[]>] [-ListAvailable] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="95585-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="95585-107">DESCRIPTION</span></span>

<span data-ttu-id="95585-108">Cmdlet **: en get-PackageProvider** returnerar en lista med paket leverantörer som är anslutna till paket hantering.</span><span class="sxs-lookup"><span data-stu-id="95585-108">The **Get-PackageProvider** cmdlet returns a list of package providers that are connected to Package Management.</span></span>
<span data-ttu-id="95585-109">Exempel på dessa leverantörer är PSModule, NuGet och choklad.</span><span class="sxs-lookup"><span data-stu-id="95585-109">Examples of these providers include PSModule, NuGet, and Chocolatey.</span></span>
<span data-ttu-id="95585-110">Du kan filtrera resultaten baserat på hela eller delar av ett eller flera providernamn.</span><span class="sxs-lookup"><span data-stu-id="95585-110">You can filter the results based on all or part of one or more provider names.</span></span>

## <span data-ttu-id="95585-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="95585-111">EXAMPLES</span></span>

### <span data-ttu-id="95585-112">Exempel 1: Hämta alla paket leverantörer som har lästs in</span><span class="sxs-lookup"><span data-stu-id="95585-112">Example 1: Get all currently loaded package providers</span></span>

```
PS C:\> Get-PackageProvider
```

<span data-ttu-id="95585-113">Det här kommandot hämtar en lista över alla paket leverantörer som för närvarande har lästs in på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="95585-113">This command gets a list of all the package providers that are currently loaded on the local computer.</span></span>

### <span data-ttu-id="95585-114">Exempel 2: Hämta alla tillgängliga paket leverantörer</span><span class="sxs-lookup"><span data-stu-id="95585-114">Example 2: Get all available package providers</span></span>

```
PS C:\> Get-PackageProvider -ListAvailable
```

<span data-ttu-id="95585-115">Det här kommandot hämtar en lista över alla paket leverantörer som är tillgängliga på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="95585-115">This command gets a list of all package providers that are available on the local computer.</span></span>

### <span data-ttu-id="95585-116">Exempel 3: Hämta en paket leverantör dynamiskt</span><span class="sxs-lookup"><span data-stu-id="95585-116">Example 3: Dynamically get a package provider</span></span>

```
PS C:\> Get-PackageProvider -Name "Chocolatey" -ForceBootstrap
```

<span data-ttu-id="95585-117">Med det här kommandot installeras choklad leverantören automatiskt om datorn inte har någon choklad-Provider installerad.</span><span class="sxs-lookup"><span data-stu-id="95585-117">This command automatically installs the Chocolatey provider if your computer does not have the Chocolatey provider installed.</span></span>

## <span data-ttu-id="95585-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="95585-118">PARAMETERS</span></span>

### <span data-ttu-id="95585-119">-Force</span><span class="sxs-lookup"><span data-stu-id="95585-119">-Force</span></span>

<span data-ttu-id="95585-120">Anger att denna cmdlet tvingar alla andra åtgärder med denna cmdlet som kan tvingas.</span><span class="sxs-lookup"><span data-stu-id="95585-120">Indicates that this cmdlet forces all other actions with this cmdlet that can be forced.</span></span>
<span data-ttu-id="95585-121">I **Get-PackageProvider** innebär detta att *Force* -parametern fungerar på samma sätt som parametern *ForceBootstrap* .</span><span class="sxs-lookup"><span data-stu-id="95585-121">In **Get-PackageProvider** , this means the *Force* parameter acts the same as the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="95585-122">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="95585-122">-ForceBootstrap</span></span>

<span data-ttu-id="95585-123">Anger att den här cmdleten tvingar paket hantering att automatiskt installera paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="95585-123">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="95585-124">– ListAvailable</span><span class="sxs-lookup"><span data-stu-id="95585-124">-ListAvailable</span></span>

<span data-ttu-id="95585-125">Hämtar alla installerade providrar.</span><span class="sxs-lookup"><span data-stu-id="95585-125">Gets all installed providers.</span></span>
<span data-ttu-id="95585-126">**Get-PackageProvider** hämtar providern i sökvägar som anges i miljövariabeln **PSModulePath** och paket providerns Assembly-mappar:</span><span class="sxs-lookup"><span data-stu-id="95585-126">**Get-PackageProvider** gets provider in paths listed in the **PSModulePath** environment variable as well as the package provider assembly folders:</span></span>

<span data-ttu-id="95585-127">**$env:P rogramFiles\PackageManagement\ProviderAssemblies \* \* \* \* $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies**</span><span class="sxs-lookup"><span data-stu-id="95585-127">**$env:ProgramFiles\PackageManagement\ProviderAssemblies\*\*\*\*$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies**</span></span>

<span data-ttu-id="95585-128">Utan den här parametern hämtar **Get-PackageProvider** bara de providrar som lästs in i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="95585-128">Without this parameter, **Get-PackageProvider** gets only the providers loaded in the current session.</span></span>

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

### <span data-ttu-id="95585-129">-Name</span><span class="sxs-lookup"><span data-stu-id="95585-129">-Name</span></span>

<span data-ttu-id="95585-130">Anger ett eller flera providernamn eller delar av leverantörs namn.</span><span class="sxs-lookup"><span data-stu-id="95585-130">Specifies one or more provider names, or partial provider names.</span></span>
<span data-ttu-id="95585-131">Separera flera providernamn med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="95585-131">Separate multiple provider names with commas.</span></span>
<span data-ttu-id="95585-132">Giltiga värden för den här parametern är namn på leverantörer som du har installerat med paket. PackageManagement levereras med en uppsättning standard leverantörer, inklusive **PSModule** -och **MSI** -providers.</span><span class="sxs-lookup"><span data-stu-id="95585-132">Valid values for this parameter include names of providers that you have installed with packages; PackageManagement ships with a set of default providers, including the **PSModule** and **MSI** providers.</span></span>

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

### <span data-ttu-id="95585-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="95585-133">CommonParameters</span></span>

<span data-ttu-id="95585-134">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="95585-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="95585-135">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="95585-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="95585-136">INDATA</span><span class="sxs-lookup"><span data-stu-id="95585-136">INPUTS</span></span>

## <span data-ttu-id="95585-137">UTDATA</span><span class="sxs-lookup"><span data-stu-id="95585-137">OUTPUTS</span></span>

### <span data-ttu-id="95585-138">PackageProvider[]</span><span class="sxs-lookup"><span data-stu-id="95585-138">PackageProvider[]</span></span>

## <span data-ttu-id="95585-139">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="95585-139">NOTES</span></span>

## <span data-ttu-id="95585-140">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="95585-140">RELATED LINKS</span></span>

[<span data-ttu-id="95585-141">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="95585-141">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="95585-142">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="95585-142">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="95585-143">Registrera – PackageSource</span><span class="sxs-lookup"><span data-stu-id="95585-143">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="95585-144">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="95585-144">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
