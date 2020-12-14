---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 6c19d1cbc7b7e4dc37e24c466f83efae688f3cec
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889477"
---
# <span data-ttu-id="3e9d6-102">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="3e9d6-102">Import-PackageProvider</span></span>

## <span data-ttu-id="3e9d6-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3e9d6-103">SYNOPSIS</span></span>
<span data-ttu-id="3e9d6-104">Lägger till leverantörer av paket hanterings paket i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-104">Adds Package Management package providers to the current session.</span></span>

## <span data-ttu-id="3e9d6-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3e9d6-105">SYNTAX</span></span>

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="3e9d6-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3e9d6-106">DESCRIPTION</span></span>

<span data-ttu-id="3e9d6-107">`Import-PackageProvider`Cmdleten lägger till en eller flera paket leverantörer i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-107">The `Import-PackageProvider` cmdlet adds one or more package providers to the current session.</span></span>
<span data-ttu-id="3e9d6-108">Leverantören som du importerar måste vara installerad på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-108">The provider that you import must be installed on the local computer.</span></span>

<span data-ttu-id="3e9d6-109">Kör om du vill hämta en lista över tillgängliga providers `Get-PackageProvider -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="3e9d6-109">To get a list of available providers, run `Get-PackageProvider -ListAvailable`.</span></span>
<span data-ttu-id="3e9d6-110">Observera att ett paket leverantörs namn kan skilja sig från dess modulnamn.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-110">Note that a package provider name can be different from its module name.</span></span>

<span data-ttu-id="3e9d6-111">På grund av säkerhets skäl kräver **PackageManagement** C#-baserade providers för att innehålla en `provider.manifest` .</span><span class="sxs-lookup"><span data-stu-id="3e9d6-111">Due to security reasons, **PackageManagement** requires C#-based providers to contain a `provider.manifest`.</span></span> <span data-ttu-id="3e9d6-112">Mer information om hur du skapar en Provider med `provider.manifest` inmatad finns i `.csproj` projektfilerna på [https://github.com/oneget/oneget](https://github.com/oneget/oneget) .</span><span class="sxs-lookup"><span data-stu-id="3e9d6-112">For more information on how to build a provider with `provider.manifest` injected, see the `.csproj` project files on [https://github.com/oneget/oneget](https://github.com/oneget/oneget).</span></span>

## <span data-ttu-id="3e9d6-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3e9d6-113">EXAMPLES</span></span>

### <span data-ttu-id="3e9d6-114">Exempel 1: importera en paket leverantör från den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="3e9d6-114">Example 1: Import a package provider from the local computer</span></span>

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

<span data-ttu-id="3e9d6-115">Det här kommandot importerar NuGet-providern när den har installerats på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-115">This command imports the Nuget provider after it has been installed on the local computer.</span></span>

### <span data-ttu-id="3e9d6-116">Exempel 2: importera en angiven version av en paket leverantör</span><span class="sxs-lookup"><span data-stu-id="3e9d6-116">Example 2: Import a specific version of a package provider</span></span>

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

<span data-ttu-id="3e9d6-117">Det här kommandot hittar, installerar och importerar en angiven version av NuGet-paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-117">This command finds, installs, and imports a specific version of the Nuget package provider.</span></span>

## <span data-ttu-id="3e9d6-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3e9d6-118">PARAMETERS</span></span>

### <span data-ttu-id="3e9d6-119">-Force</span><span class="sxs-lookup"><span data-stu-id="3e9d6-119">-Force</span></span>

<span data-ttu-id="3e9d6-120">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-120">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="3e9d6-121">Importerar en paket leverantör igen.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-121">Re-imports a package provider.</span></span>

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

### <span data-ttu-id="3e9d6-122">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="3e9d6-122">-ForceBootstrap</span></span>

<span data-ttu-id="3e9d6-123">Anger att den här cmdleten tvingar paket hantering att automatiskt installera paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-123">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="3e9d6-124">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="3e9d6-124">-MaximumVersion</span></span>

<span data-ttu-id="3e9d6-125">Anger den högsta tillåtna versionen av paket leverantören som du vill importera.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-125">Specifies the maximum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="3e9d6-126">Om du inte lägger till den här parametern `Import-PackageProvider` importeras den högsta tillgängliga versionen av providern.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-126">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider.</span></span>

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

### <span data-ttu-id="3e9d6-127">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="3e9d6-127">-MinimumVersion</span></span>

<span data-ttu-id="3e9d6-128">Anger den lägsta tillåtna versionen av paket leverantören som du vill importera.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-128">Specifies the minimum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="3e9d6-129">Om du inte lägger till den här parametern `Import-PackageProvider` importeras den högsta tillgängliga versionen av paketet som också uppfyller den högsta version som anges med parametern *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="3e9d6-129">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the package that also satisfies any maximum version that is specified using the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="3e9d6-130">-Name</span><span class="sxs-lookup"><span data-stu-id="3e9d6-130">-Name</span></span>

<span data-ttu-id="3e9d6-131">Anger ett eller flera paket leverantörs namn.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-131">Specifies one or more package provider names.</span></span> <span data-ttu-id="3e9d6-132">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-132">Wildcards are not permitted.</span></span>

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

### <span data-ttu-id="3e9d6-133">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="3e9d6-133">-RequiredVersion</span></span>

<span data-ttu-id="3e9d6-134">Anger den exakta versionen av paket leverantören som du vill importera.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-134">Specifies the exact version of the package provider that you want to import.</span></span> <span data-ttu-id="3e9d6-135">Om du inte lägger till den här parametern `Import-PackageProvider` importeras den högsta tillgängliga versionen av providern som också uppfyller den högsta version som anges med parametern **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="3e9d6-135">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider that also satisfies any maximum version specified using the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="3e9d6-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3e9d6-136">CommonParameters</span></span>

<span data-ttu-id="3e9d6-137">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3e9d6-138">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3e9d6-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3e9d6-139">INDATA</span><span class="sxs-lookup"><span data-stu-id="3e9d6-139">INPUTS</span></span>

### <span data-ttu-id="3e9d6-140">Microsoft. PackageManagement. implementation. PackageProvider</span><span class="sxs-lookup"><span data-stu-id="3e9d6-140">Microsoft.PackageManagement.Implementation.PackageProvider</span></span>

<span data-ttu-id="3e9d6-141">Du kan skicka vidare ett **PackageProvider** -objekt som returnerades av `Get-PackageProvider` till `Import-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="3e9d6-141">You can pipe a **PackageProvider** object returned by `Get-PackageProvider` into `Import-PackageProvider`.</span></span>

## <span data-ttu-id="3e9d6-142">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3e9d6-142">OUTPUTS</span></span>

## <span data-ttu-id="3e9d6-143">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3e9d6-143">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e9d6-144">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-144">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="3e9d6-145">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-145">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="3e9d6-146">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="3e9d6-146">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="3e9d6-147">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="3e9d6-147">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="3e9d6-148">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3e9d6-148">RELATED LINKS</span></span>

[<span data-ttu-id="3e9d6-149">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="3e9d6-149">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="3e9d6-150">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="3e9d6-150">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="3e9d6-151">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="3e9d6-151">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="3e9d6-152">Registrera – PackageSource</span><span class="sxs-lookup"><span data-stu-id="3e9d6-152">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="3e9d6-153">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="3e9d6-153">Get-PackageProvider</span></span>](Get-PackageProvider.md)
