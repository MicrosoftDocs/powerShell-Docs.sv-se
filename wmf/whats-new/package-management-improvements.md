---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Förbättringar av pakethantering i WMF 5.1
ms.openlocfilehash: 24ff05d6bf5993826106f1a1d2cee6dad363d1e2
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856163"
---
# <a name="improvements-to-package-management-in-wmf-51"></a><span data-ttu-id="770d6-103">Förbättringar av pakethantering i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="770d6-103">Improvements to Package Management in WMF 5.1</span></span>

<span data-ttu-id="770d6-104">Följande är de korrigeringar som gjorts i WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="770d6-104">The following are the fixes made in the WMF 5.1:</span></span>

## <a name="version-alias"></a><span data-ttu-id="770d6-105">Version Alias</span><span class="sxs-lookup"><span data-stu-id="770d6-105">Version Alias</span></span>

<span data-ttu-id="770d6-106">**Scenario**: Om du har version 1.0 och 2.0 i ett paket, P1, som installeras på datorn, och du vill avinstallera version 1.0, kör du `Uninstall-Package -Name P1 -Version 1.0` och räknar med version 1.0 avinstalleras när du har kört cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="770d6-106">**Scenario**: If you have version 1.0 and 2.0 of a package, P1, installed on your system, and you want to uninstall version 1.0, you would run `Uninstall-Package -Name P1 -Version 1.0` and expect version 1.0 to be uninstalled after running the cmdlet.</span></span> <span data-ttu-id="770d6-107">Men resultatet är att version 2.0 avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="770d6-107">However the result is that version 2.0 gets uninstalled.</span></span>

<span data-ttu-id="770d6-108">Detta beror på att den `-Version` parametern är ett alias för den `-MinimumVersion` parametern.</span><span class="sxs-lookup"><span data-stu-id="770d6-108">This occurs because the `-Version` parameter is an alias of the `-MinimumVersion` parameter.</span></span> <span data-ttu-id="770d6-109">När PackageManagement är ute efter ett kvalificerat paket med den lägsta versionen av 1.0, returnerar den senaste versionen.</span><span class="sxs-lookup"><span data-stu-id="770d6-109">When PackageManagement is looking for a qualified package with the minimum version of 1.0, it returns the latest version.</span></span> <span data-ttu-id="770d6-110">Det här beteendet är förväntat i normala fall eftersom att söka efter den senaste versionen är vanligtvis det önskade resultatet.</span><span class="sxs-lookup"><span data-stu-id="770d6-110">This behavior is expected in normal cases because finding the latest version is usually the desired result.</span></span> <span data-ttu-id="770d6-111">Det bör dock inte tillämpas på den `Uninstall-Package` fall.</span><span class="sxs-lookup"><span data-stu-id="770d6-111">However, it should not apply to the `Uninstall-Package` case.</span></span>

<span data-ttu-id="770d6-112">**Lösningen**: bort `-Version` alias helt i PackageManagement (alias)</span><span class="sxs-lookup"><span data-stu-id="770d6-112">**Solution**:removed `-Version` alias entirely in PackageManagement (a.k.a.</span></span> <span data-ttu-id="770d6-113">OneGet) och PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="770d6-113">OneGet) and PowerShellGet.</span></span>

## <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a><span data-ttu-id="770d6-114">Flera prompter för start av NuGet-providern</span><span class="sxs-lookup"><span data-stu-id="770d6-114">Multiple prompts for bootstrapping the NuGet provider</span></span>

<span data-ttu-id="770d6-115">**Scenario**: När du kör `Find-Module` eller `Install-Module` eller andra PackageManagement-cmdletar på din dator för första gången, PackageManagement försöker starta NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="770d6-115">**Scenario**: When you run `Find-Module` or `Install-Module` or other PackageManagement cmdlets on your computer for the first time, PackageManagement tries to bootstrap the NuGet provider.</span></span> <span data-ttu-id="770d6-116">Detta sker eftersom providern PowerShellGet också NuGet-providern använder för att ladda ned PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="770d6-116">It does this because the PowerShellGet provider also uses the NuGet provider to download PowerShell modules.</span></span>
<span data-ttu-id="770d6-117">PackageManagement sedan uppmanas användaren om behörighet att installera NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="770d6-117">PackageManagement then prompts the user for permission to install the NuGet provider.</span></span> <span data-ttu-id="770d6-118">När användaren väljer ”Ja” för den startprogram, installeras den senaste versionen av NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="770d6-118">After the user selects "yes" for the bootstrapping, the latest version of the NuGet provider will be installed.</span></span>

<span data-ttu-id="770d6-119">Men i vissa fall när du har en äldre version av NuGet-providern på datorn, den äldre versionen av NuGet som ibland hämtar läsas in först i PowerShell-sessionen (det vill säga konkurrenstillstånd i PackageManagement).</span><span class="sxs-lookup"><span data-stu-id="770d6-119">However, in some cases, when you have an old version of NuGet provider installed on your computer, the older version of NuGet sometimes gets loaded first into the PowerShell session (that's the race condition in PackageManagement).</span></span> <span data-ttu-id="770d6-120">PowerShellGet kräver dock den senare versionen av NuGet-providern fungerar, så PowerShellGet frågar PackageManagement ska kunna starta NuGet-providern igen.</span><span class="sxs-lookup"><span data-stu-id="770d6-120">However PowerShellGet requires the later version of the NuGet provider to work, so PowerShellGet asks PackageManagement to bootstrap the NuGet provider again.</span></span>
<span data-ttu-id="770d6-121">Detta resulterar i flera prompter för start av NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="770d6-121">This results in multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="770d6-122">**Lösningen**: Läser in den senaste versionen av NuGet-providern för att undvika flera prompter för start av NuGet-providern i WMF5.1, PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="770d6-122">**Solution**: In WMF5.1, PackageManagement loads the latest version of the NuGet provider to avoid multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="770d6-123">Du kan även undvika det här problemet genom att manuellt ta bort den gamla versionen av NuGet-providern (NuGet-Anycpu.exe) om det finns från $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies</span><span class="sxs-lookup"><span data-stu-id="770d6-123">You could also work around this issue by manually deleting the old version of the NuGet provider (NuGet-Anycpu.exe) if exists from $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies</span></span>

## <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a><span data-ttu-id="770d6-124">Stöd för PackageManagement på datorer med endast intranät-åtkomst</span><span class="sxs-lookup"><span data-stu-id="770d6-124">Support for PackageManagement on computers with Intranet access only</span></span>

<span data-ttu-id="770d6-125">**Scenario**: Enterprise-scenario, personer arbetar under en miljö där det finns ingen åtkomst till Internet men intranätet endast.</span><span class="sxs-lookup"><span data-stu-id="770d6-125">**Scenario**: For the enterprise scenario, people are working under an environment where there is no Internet access but Intranet only.</span></span> <span data-ttu-id="770d6-126">PackageManagement inte stöd för det här fallet i WMF 5.0.</span><span class="sxs-lookup"><span data-stu-id="770d6-126">PackageManagement did not support this case in WMF 5.0.</span></span>

<span data-ttu-id="770d6-127">**Scenario**: I WMF 5.0 PackageManagement inte stöd för datorer som har endast intranät (men inte Internet) åtkomst.</span><span class="sxs-lookup"><span data-stu-id="770d6-127">**Scenario**: In WMF 5.0, PackageManagement did not support computers that have only Intranet (but not Internet) access.</span></span>

<span data-ttu-id="770d6-128">**Lösningen**: Du kan följa stegen nedan för att Tillåt intranät-datorer använder PackageManagement i WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="770d6-128">**Solution**: In WMF 5.1, you can follow these steps to allow Intranet computers to use PackageManagement:</span></span>

1. <span data-ttu-id="770d6-129">Ladda ned NuGet-providern använder en annan dator som har en Internetanslutning med hjälp av `Install-PackageProvider -Name NuGet`.</span><span class="sxs-lookup"><span data-stu-id="770d6-129">Download the NuGet provider using another computer that has an Internet connection by using `Install-PackageProvider -Name NuGet`.</span></span>

2. <span data-ttu-id="770d6-130">Hitta NuGet-providern under `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` eller `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.</span><span class="sxs-lookup"><span data-stu-id="770d6-130">Find the NuGet provider under either `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` or `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.</span></span>

3. <span data-ttu-id="770d6-131">Kopiera de binära filerna till en mapp eller plats som intranät-datorn kan komma åt och sedan installera NuGet-providern med `Install-PackageProvider -Name NuGet -Source <Path to folder>`.</span><span class="sxs-lookup"><span data-stu-id="770d6-131">Copy the binaries to a folder or network share location that the Intranet computer can access, and then install the NuGet provider with `Install-PackageProvider -Name NuGet -Source <Path to folder>`.</span></span>


## <a name="event-logging-improvements"></a><span data-ttu-id="770d6-132">Förbättringar av händelse-loggning</span><span class="sxs-lookup"><span data-stu-id="770d6-132">Event logging improvements</span></span>

<span data-ttu-id="770d6-133">När du installerar paket, ändrar du tillståndet för datorn.</span><span class="sxs-lookup"><span data-stu-id="770d6-133">When you install packages, you are changing the state of the computer.</span></span> <span data-ttu-id="770d6-134">I WMF 5.1 PackageManagement nu loggar händelser i Windows-händelseloggen för `Install-Package`, `Uninstall-Package`, och `Save-Package` aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="770d6-134">In WMF 5.1, PackageManagement now logs events to the Windows event log for `Install-Package`, `Uninstall-Package`, and `Save-Package` activities.</span></span> <span data-ttu-id="770d6-135">Händelseloggen är desamma som för PowerShell, det vill säga `Microsoft-Windows-PowerShell, Operational`.</span><span class="sxs-lookup"><span data-stu-id="770d6-135">The Event log is the same as for PowerShell, that is, `Microsoft-Windows-PowerShell, Operational`.</span></span>

## <a name="support-for-basic-authentication"></a><span data-ttu-id="770d6-136">Stöd för grundläggande autentisering</span><span class="sxs-lookup"><span data-stu-id="770d6-136">Support for basic authentication</span></span>

<span data-ttu-id="770d6-137">I WMF 5.1 PackageManagement har stöd för att söka efter och installera paket från en lagringsplats som kräver grundläggande autentisering.</span><span class="sxs-lookup"><span data-stu-id="770d6-137">In WMF 5.1, PackageManagement supports finding and installing packages from a repository that requires basic authentication.</span></span> <span data-ttu-id="770d6-138">Du kan ange dina autentiseringsuppgifter för att den `Find-Package` och `Install-Package` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="770d6-138">You can supply your credentials to the `Find-Package` and `Install-Package` cmdlets.</span></span> <span data-ttu-id="770d6-139">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="770d6-139">For example:</span></span>

```powershell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

## <a name="support-for-using-packagemanagement-behind-a-proxy"></a><span data-ttu-id="770d6-140">Stöd för användning av PackageManagement bakom en proxyserver</span><span class="sxs-lookup"><span data-stu-id="770d6-140">Support for using PackageManagement behind a proxy</span></span>

<span data-ttu-id="770d6-141">I WMF 5.1 PackageManagement tar nu bara nya proxyparametrar `-ProxyCredential` och `-Proxy`.</span><span class="sxs-lookup"><span data-stu-id="770d6-141">In WMF 5.1, PackageManagement now takes new proxy parameters `-ProxyCredential` and `-Proxy`.</span></span> <span data-ttu-id="770d6-142">Med dessa parametrar kan ange du proxy-URL och autentiseringsuppgifter i PackageManagement-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="770d6-142">Using these parameters, you can specify the proxy URL and credentials to PackageManagement cmdlets.</span></span> <span data-ttu-id="770d6-143">System-proxyinställningar används som standard.</span><span class="sxs-lookup"><span data-stu-id="770d6-143">By default, system proxy settings are used.</span></span> <span data-ttu-id="770d6-144">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="770d6-144">For example:</span></span>

```powershell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
