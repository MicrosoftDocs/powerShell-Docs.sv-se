---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 428cb3afa574345ef5cb4b79b76b31cf9bfb2e7b
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890087"
---
# <span data-ttu-id="92264-103">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="92264-103">Import-PackageProvider</span></span>

## <span data-ttu-id="92264-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="92264-104">SYNOPSIS</span></span>
<span data-ttu-id="92264-105">Lägger till leverantörer av paket hanterings paket i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="92264-105">Adds Package Management package providers to the current session.</span></span>

## <span data-ttu-id="92264-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="92264-106">SYNTAX</span></span>

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="92264-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="92264-107">DESCRIPTION</span></span>

<span data-ttu-id="92264-108">`Import-PackageProvider`Cmdleten lägger till en eller flera paket leverantörer i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="92264-108">The `Import-PackageProvider` cmdlet adds one or more package providers to the current session.</span></span>
<span data-ttu-id="92264-109">Leverantören som du importerar måste vara installerad på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="92264-109">The provider that you import must be installed on the local computer.</span></span>

<span data-ttu-id="92264-110">Kör om du vill hämta en lista över tillgängliga providers `Get-PackageProvider -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="92264-110">To get a list of available providers, run `Get-PackageProvider -ListAvailable`.</span></span>
<span data-ttu-id="92264-111">Observera att ett paket leverantörs namn kan skilja sig från dess modulnamn.</span><span class="sxs-lookup"><span data-stu-id="92264-111">Note that a package provider name can be different from its module name.</span></span>

<span data-ttu-id="92264-112">På grund av säkerhets skäl kräver **PackageManagement** C#-baserade providers för att innehålla en `provider.manifest` .</span><span class="sxs-lookup"><span data-stu-id="92264-112">Due to security reasons, **PackageManagement** requires C#-based providers to contain a `provider.manifest`.</span></span> <span data-ttu-id="92264-113">Mer information om hur du skapar en Provider med `provider.manifest` inmatad finns i `.csproj` projektfilerna på [https://github.com/oneget/oneget](https://github.com/oneget/oneget) .</span><span class="sxs-lookup"><span data-stu-id="92264-113">For more information on how to build a provider with `provider.manifest` injected, see the `.csproj` project files on [https://github.com/oneget/oneget](https://github.com/oneget/oneget).</span></span>

## <span data-ttu-id="92264-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="92264-114">EXAMPLES</span></span>

### <span data-ttu-id="92264-115">Exempel 1: importera en paket leverantör från den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="92264-115">Example 1: Import a package provider from the local computer</span></span>

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

<span data-ttu-id="92264-116">Det här kommandot importerar NuGet-providern när den har installerats på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="92264-116">This command imports the Nuget provider after it has been installed on the local computer.</span></span>

### <span data-ttu-id="92264-117">Exempel 2: importera en angiven version av en paket leverantör</span><span class="sxs-lookup"><span data-stu-id="92264-117">Example 2: Import a specific version of a package provider</span></span>

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

<span data-ttu-id="92264-118">Det här kommandot hittar, installerar och importerar en angiven version av NuGet-paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="92264-118">This command finds, installs, and imports a specific version of the Nuget package provider.</span></span>

## <span data-ttu-id="92264-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="92264-119">PARAMETERS</span></span>

### <span data-ttu-id="92264-120">-Force</span><span class="sxs-lookup"><span data-stu-id="92264-120">-Force</span></span>

<span data-ttu-id="92264-121">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="92264-121">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="92264-122">Importerar en paket leverantör igen.</span><span class="sxs-lookup"><span data-stu-id="92264-122">Re-imports a package provider.</span></span>

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

### <span data-ttu-id="92264-123">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="92264-123">-ForceBootstrap</span></span>

<span data-ttu-id="92264-124">Anger att den här cmdleten tvingar paket hantering att automatiskt installera paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="92264-124">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="92264-125">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="92264-125">-MaximumVersion</span></span>

<span data-ttu-id="92264-126">Anger den högsta tillåtna versionen av paket leverantören som du vill importera.</span><span class="sxs-lookup"><span data-stu-id="92264-126">Specifies the maximum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="92264-127">Om du inte lägger till den här parametern `Import-PackageProvider` importeras den högsta tillgängliga versionen av providern.</span><span class="sxs-lookup"><span data-stu-id="92264-127">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="92264-128">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="92264-128">-MinimumVersion</span></span>

<span data-ttu-id="92264-129">Anger den lägsta tillåtna versionen av paket leverantören som du vill importera.</span><span class="sxs-lookup"><span data-stu-id="92264-129">Specifies the minimum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="92264-130">Om du inte lägger till den här parametern `Import-PackageProvider` importeras den högsta tillgängliga versionen av paketet som också uppfyller den högsta version som anges med parametern *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="92264-130">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the package that also satisfies any maximum version that is specified using the *MaximumVersion* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="92264-131">-Name</span><span class="sxs-lookup"><span data-stu-id="92264-131">-Name</span></span>

<span data-ttu-id="92264-132">Anger ett eller flera paket leverantörs namn.</span><span class="sxs-lookup"><span data-stu-id="92264-132">Specifies one or more package provider names.</span></span> <span data-ttu-id="92264-133">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="92264-133">Wildcards are not permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="92264-134">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="92264-134">-RequiredVersion</span></span>

<span data-ttu-id="92264-135">Anger den exakta versionen av paket leverantören som du vill importera.</span><span class="sxs-lookup"><span data-stu-id="92264-135">Specifies the exact version of the package provider that you want to import.</span></span> <span data-ttu-id="92264-136">Om du inte lägger till den här parametern `Import-PackageProvider` importeras den högsta tillgängliga versionen av providern som också uppfyller den högsta version som anges med parametern **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="92264-136">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider that also satisfies any maximum version specified using the **MaximumVersion** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="92264-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="92264-137">CommonParameters</span></span>

<span data-ttu-id="92264-138">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="92264-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="92264-139">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="92264-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="92264-140">INDATA</span><span class="sxs-lookup"><span data-stu-id="92264-140">INPUTS</span></span>

### <span data-ttu-id="92264-141">Microsoft. PackageManagement. implementation. PackageProvider</span><span class="sxs-lookup"><span data-stu-id="92264-141">Microsoft.PackageManagement.Implementation.PackageProvider</span></span>

<span data-ttu-id="92264-142">Du kan skicka vidare ett **PackageProvider** -objekt som returnerades av `Get-PackageProvider` till `Import-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="92264-142">You can pipe a **PackageProvider** object returned by `Get-PackageProvider` into `Import-PackageProvider`.</span></span>

## <span data-ttu-id="92264-143">UTDATA</span><span class="sxs-lookup"><span data-stu-id="92264-143">OUTPUTS</span></span>

## <span data-ttu-id="92264-144">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="92264-144">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="92264-145">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="92264-145">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="92264-146">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="92264-146">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="92264-147">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="92264-147">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="92264-148">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="92264-148">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="92264-149">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="92264-149">RELATED LINKS</span></span>

[<span data-ttu-id="92264-150">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="92264-150">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="92264-151">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="92264-151">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="92264-152">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="92264-152">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="92264-153">Registrera – PackageSource</span><span class="sxs-lookup"><span data-stu-id="92264-153">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="92264-154">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="92264-154">Get-PackageProvider</span></span>](Get-PackageProvider.md)
