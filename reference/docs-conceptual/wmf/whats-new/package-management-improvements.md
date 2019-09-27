---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Förbättringar i pakethanteringen i WMF 5.1
ms.openlocfilehash: cb19c2d71391b5729ce9d73fc6b033270f8db307
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325124"
---
# <a name="improvements-to-package-management-in-wmf-51"></a><span data-ttu-id="62480-103">Förbättringar i pakethanteringen i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="62480-103">Improvements to Package Management in WMF 5.1</span></span>

<span data-ttu-id="62480-104">Följande är de korrigeringar som görs i WMF 5,1:</span><span class="sxs-lookup"><span data-stu-id="62480-104">The following are the fixes made in the WMF 5.1:</span></span>

## <a name="version-alias"></a><span data-ttu-id="62480-105">Versions-alias</span><span class="sxs-lookup"><span data-stu-id="62480-105">Version Alias</span></span>

<span data-ttu-id="62480-106">**Scenario**: Om du har version 1,0 och 2,0 av ett paket, P1, installerat i systemet och du vill avinstallera version 1,0, kör `Uninstall-Package -Name P1 -Version 1.0` du och förväntar dig att version 1,0 ska avinstalleras efter att du kört cmdleten.</span><span class="sxs-lookup"><span data-stu-id="62480-106">**Scenario**: If you have version 1.0 and 2.0 of a package, P1, installed on your system, and you want to uninstall version 1.0, you would run `Uninstall-Package -Name P1 -Version 1.0` and expect version 1.0 to be uninstalled after running the cmdlet.</span></span> <span data-ttu-id="62480-107">Men resultatet är att version 2,0 avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="62480-107">However the result is that version 2.0 gets uninstalled.</span></span>

<span data-ttu-id="62480-108">Detta beror på `-Version` att parametern är ett alias `-MinimumVersion` för parametern.</span><span class="sxs-lookup"><span data-stu-id="62480-108">This occurs because the `-Version` parameter is an alias of the `-MinimumVersion` parameter.</span></span> <span data-ttu-id="62480-109">När PackageManagement söker efter ett kvalificerat paket med den lägsta versionen av 1,0 returneras den senaste versionen.</span><span class="sxs-lookup"><span data-stu-id="62480-109">When PackageManagement is looking for a qualified package with the minimum version of 1.0, it returns the latest version.</span></span> <span data-ttu-id="62480-110">Det här beteendet förväntas i normala fall eftersom det är vanligt att hitta den senaste versionen.</span><span class="sxs-lookup"><span data-stu-id="62480-110">This behavior is expected in normal cases because finding the latest version is usually the desired result.</span></span> <span data-ttu-id="62480-111">Det bör dock inte gälla för `Uninstall-Package` fallet.</span><span class="sxs-lookup"><span data-stu-id="62480-111">However, it should not apply to the `Uninstall-Package` case.</span></span>

<span data-ttu-id="62480-112">**Lösning**: borttaget `-Version` alias helt i PackageManagement (kallas även</span><span class="sxs-lookup"><span data-stu-id="62480-112">**Solution**:removed `-Version` alias entirely in PackageManagement (a.k.a.</span></span> <span data-ttu-id="62480-113">OneGet) och PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="62480-113">OneGet) and PowerShellGet.</span></span>

## <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a><span data-ttu-id="62480-114">Du uppmanas att starta NuGet-providern med flera prompter</span><span class="sxs-lookup"><span data-stu-id="62480-114">Multiple prompts for bootstrapping the NuGet provider</span></span>

<span data-ttu-id="62480-115">**Scenario**: När du kör `Find-Module` eller `Install-Module` eller andra PackageManagement-cmdlet: ar på datorn för första gången försöker PackageManagement starta NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="62480-115">**Scenario**: When you run `Find-Module` or `Install-Module` or other PackageManagement cmdlets on your computer for the first time, PackageManagement tries to bootstrap the NuGet provider.</span></span> <span data-ttu-id="62480-116">Detta beror på att PowerShellGet-providern även använder NuGet-providern för att hämta PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="62480-116">It does this because the PowerShellGet provider also uses the NuGet provider to download PowerShell modules.</span></span>
<span data-ttu-id="62480-117">PackageManagement uppmanas sedan användaren att ange behörighet för att installera NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="62480-117">PackageManagement then prompts the user for permission to install the NuGet provider.</span></span> <span data-ttu-id="62480-118">När användaren har valt "Ja" för start sidan installeras den senaste versionen av NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="62480-118">After the user selects "yes" for the bootstrapping, the latest version of the NuGet provider will be installed.</span></span>

<span data-ttu-id="62480-119">Men i vissa fall, när en gammal version av NuGet-providern är installerad på datorn, kommer den äldre versionen av NuGet ibland att läsas in först i PowerShell-sessionen (det är tävlings villkoret i PackageManagement).</span><span class="sxs-lookup"><span data-stu-id="62480-119">However, in some cases, when you have an old version of NuGet provider installed on your computer, the older version of NuGet sometimes gets loaded first into the PowerShell session (that's the race condition in PackageManagement).</span></span> <span data-ttu-id="62480-120">Men PowerShellGet kräver att den senare versionen av NuGet-providern fungerar, så PowerShellGet ber PackageManagement att starta NuGet-providern igen.</span><span class="sxs-lookup"><span data-stu-id="62480-120">However PowerShellGet requires the later version of the NuGet provider to work, so PowerShellGet asks PackageManagement to bootstrap the NuGet provider again.</span></span>
<span data-ttu-id="62480-121">Detta resulterar i flera prompter för att starta NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="62480-121">This results in multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="62480-122">**Lösning**: I WMF 5.1 laddar PackageManagement den senaste versionen av NuGet-providern för att undvika flera prompter för att starta NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="62480-122">**Solution**: In WMF5.1, PackageManagement loads the latest version of the NuGet provider to avoid multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="62480-123">Du kan också undvika det här problemet genom att manuellt ta bort den gamla versionen av NuGet-providern (NuGet-Anycpu. exe) om den finns från $env:P rogramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies</span><span class="sxs-lookup"><span data-stu-id="62480-123">You could also work around this issue by manually deleting the old version of the NuGet provider (NuGet-Anycpu.exe) if exists from $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies</span></span>

## <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a><span data-ttu-id="62480-124">Stöd för PackageManagement på datorer med endast intranäts åtkomst</span><span class="sxs-lookup"><span data-stu-id="62480-124">Support for PackageManagement on computers with Intranet access only</span></span>

<span data-ttu-id="62480-125">**Scenario**: För företags scenariot arbetar människor under en miljö där det inte finns någon Internet anslutning, men endast intranät.</span><span class="sxs-lookup"><span data-stu-id="62480-125">**Scenario**: For the enterprise scenario, people are working under an environment where there is no Internet access but Intranet only.</span></span> <span data-ttu-id="62480-126">PackageManagement har inte stöd för det här fallet i WMF 5,0.</span><span class="sxs-lookup"><span data-stu-id="62480-126">PackageManagement did not support this case in WMF 5.0.</span></span>

<span data-ttu-id="62480-127">**Scenario**: I WMF 5,0 har PackageManagement inte stöd för datorer som endast har intranät åtkomst (men inte Internet).</span><span class="sxs-lookup"><span data-stu-id="62480-127">**Scenario**: In WMF 5.0, PackageManagement did not support computers that have only Intranet (but not Internet) access.</span></span>

<span data-ttu-id="62480-128">**Lösning**: I WMF 5,1 kan du följa de här stegen för att låta intranät datorer använda PackageManagement:</span><span class="sxs-lookup"><span data-stu-id="62480-128">**Solution**: In WMF 5.1, you can follow these steps to allow Intranet computers to use PackageManagement:</span></span>

1. <span data-ttu-id="62480-129">Ladda ned NuGet-providern med en annan dator som har en Internet `Install-PackageProvider -Name NuGet`anslutning med hjälp av.</span><span class="sxs-lookup"><span data-stu-id="62480-129">Download the NuGet provider using another computer that has an Internet connection by using `Install-PackageProvider -Name NuGet`.</span></span>

2. <span data-ttu-id="62480-130">Hitta NuGet-providern under `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` antingen `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`eller.</span><span class="sxs-lookup"><span data-stu-id="62480-130">Find the NuGet provider under either `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` or `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.</span></span>

3. <span data-ttu-id="62480-131">Kopiera binärfilerna till en mapp eller nätverks resurs plats som intranät datorn kan komma åt och installera sedan NuGet-providern med `Install-PackageProvider -Name NuGet -Source <Path to folder>`.</span><span class="sxs-lookup"><span data-stu-id="62480-131">Copy the binaries to a folder or network share location that the Intranet computer can access, and then install the NuGet provider with `Install-PackageProvider -Name NuGet -Source <Path to folder>`.</span></span>


## <a name="event-logging-improvements"></a><span data-ttu-id="62480-132">Förbättringar av händelse loggning</span><span class="sxs-lookup"><span data-stu-id="62480-132">Event logging improvements</span></span>

<span data-ttu-id="62480-133">När du installerar paket ändrar du datorns tillstånd.</span><span class="sxs-lookup"><span data-stu-id="62480-133">When you install packages, you are changing the state of the computer.</span></span> <span data-ttu-id="62480-134">I WMF 5,1 loggar PackageManagement nu händelser till händelse loggen i Windows för `Install-Package`- `Uninstall-Package`,- `Save-Package` och-aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="62480-134">In WMF 5.1, PackageManagement now logs events to the Windows event log for `Install-Package`, `Uninstall-Package`, and `Save-Package` activities.</span></span> <span data-ttu-id="62480-135">Händelse loggen är samma som för PowerShell, det `Microsoft-Windows-PowerShell, Operational`vill säga.</span><span class="sxs-lookup"><span data-stu-id="62480-135">The Event log is the same as for PowerShell, that is, `Microsoft-Windows-PowerShell, Operational`.</span></span>

## <a name="support-for-basic-authentication"></a><span data-ttu-id="62480-136">Stöd för grundläggande autentisering</span><span class="sxs-lookup"><span data-stu-id="62480-136">Support for basic authentication</span></span>

<span data-ttu-id="62480-137">I WMF 5,1 har PackageManagement stöd för att söka efter och installera paket från en lagrings plats som kräver grundläggande autentisering.</span><span class="sxs-lookup"><span data-stu-id="62480-137">In WMF 5.1, PackageManagement supports finding and installing packages from a repository that requires basic authentication.</span></span> <span data-ttu-id="62480-138">Du kan ange dina autentiseringsuppgifter till `Find-Package` -och `Install-Package` -cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="62480-138">You can supply your credentials to the `Find-Package` and `Install-Package` cmdlets.</span></span> <span data-ttu-id="62480-139">Exempel:</span><span class="sxs-lookup"><span data-stu-id="62480-139">For example:</span></span>

```powershell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

## <a name="support-for-using-packagemanagement-behind-a-proxy"></a><span data-ttu-id="62480-140">Stöd för att använda PackageManagement bakom en proxy</span><span class="sxs-lookup"><span data-stu-id="62480-140">Support for using PackageManagement behind a proxy</span></span>

<span data-ttu-id="62480-141">I WMF 5,1 tar PackageManagement nu nya proxyadresser `-ProxyCredential` och. `-Proxy`</span><span class="sxs-lookup"><span data-stu-id="62480-141">In WMF 5.1, PackageManagement now takes new proxy parameters `-ProxyCredential` and `-Proxy`.</span></span> <span data-ttu-id="62480-142">Med dessa parametrar kan du ange proxy-URL och autentiseringsuppgifter till PackageManagement-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="62480-142">Using these parameters, you can specify the proxy URL and credentials to PackageManagement cmdlets.</span></span> <span data-ttu-id="62480-143">Som standard används systemproxy-inställningar.</span><span class="sxs-lookup"><span data-stu-id="62480-143">By default, system proxy settings are used.</span></span> <span data-ttu-id="62480-144">Exempel:</span><span class="sxs-lookup"><span data-stu-id="62480-144">For example:</span></span>

```powershell
Find-Package -Source https://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
