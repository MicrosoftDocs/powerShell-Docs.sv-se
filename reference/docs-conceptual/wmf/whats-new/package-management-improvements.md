---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Förbättringar i pakethanteringen i WMF 5.1
ms.openlocfilehash: cb19c2d71391b5729ce9d73fc6b033270f8db307
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71325124"
---
# <a name="improvements-to-package-management-in-wmf-51"></a>Förbättringar i pakethanteringen i WMF 5.1

Följande är de korrigeringar som görs i WMF 5,1:

## <a name="version-alias"></a>Versions-alias

**Scenario**: om du har version 1,0 och 2,0 av ett paket, P1, installerat i systemet och du vill avinstallera version 1,0, kör du `Uninstall-Package -Name P1 -Version 1.0` och väntar på att version 1,0 ska avinstalleras efter att du kört cmdleten. Men resultatet är att version 2,0 avinstalleras.

Detta beror på att parametern `-Version` är ett alias för parametern `-MinimumVersion`. När PackageManagement söker efter ett kvalificerat paket med den lägsta versionen av 1,0 returneras den senaste versionen. Det här beteendet förväntas i normala fall eftersom det är vanligt att hitta den senaste versionen. Den bör dock inte gälla `Uninstall-Package` fallet.

**Lösning**: tar bort `-Version` alias helt i PackageManagement (kallas även OneGet) och PowerShellGet.

## <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>Du uppmanas att starta NuGet-providern med flera prompter

**Scenario**: när du kör `Find-Module` eller `Install-Module` eller andra PackageManagement-cmdlets på datorn för första gången försöker PackageManagement starta NuGet-providern. Detta beror på att PowerShellGet-providern även använder NuGet-providern för att hämta PowerShell-moduler.
PackageManagement uppmanas sedan användaren att ange behörighet för att installera NuGet-providern. När användaren har valt "Ja" för start sidan installeras den senaste versionen av NuGet-providern.

Men i vissa fall, när en gammal version av NuGet-providern är installerad på datorn, kommer den äldre versionen av NuGet ibland att läsas in först i PowerShell-sessionen (det är tävlings villkoret i PackageManagement). Men PowerShellGet kräver att den senare versionen av NuGet-providern fungerar, så PowerShellGet ber PackageManagement att starta NuGet-providern igen.
Detta resulterar i flera prompter för att starta NuGet-providern.

**Lösning**: i WMF 5.1 laddar PackageManagement den senaste versionen av NuGet-providern för att undvika flera prompter för att starta NuGet-providern.

Du kan också undvika det här problemet genom att manuellt ta bort den gamla versionen av NuGet-providern (NuGet-Anycpu. exe) om den finns från $env:P rogramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies

## <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>Stöd för PackageManagement på datorer med endast intranäts åtkomst

**Scenario**: för företags scenariot arbetar människor under en miljö där det inte finns någon Internet anslutning, men endast intranät. PackageManagement har inte stöd för det här fallet i WMF 5,0.

**Scenario**: i WMF 5,0 har PackageManagement inte stöd för datorer som endast har intranät åtkomst (men inte Internet).

**Lösning**: i WMF 5,1 kan du följa de här stegen för att låta intranät datorer använda PackageManagement:

1. Ladda ned NuGet-providern med en annan dator som har en Internet anslutning med hjälp av `Install-PackageProvider -Name NuGet`.

2. Hitta NuGet-providern under antingen `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` eller `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. Kopiera binärfilerna till en mapp eller en nätverks resurs som intranät datorn kan komma åt och installera sedan NuGet-providern med `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


## <a name="event-logging-improvements"></a>Förbättringar av händelse loggning

När du installerar paket ändrar du datorns tillstånd. I WMF 5,1 loggar PackageManagement nu händelser till händelse loggen i Windows för `Install-Package`, `Uninstall-Package`och `Save-Package` aktiviteter. Händelse loggen är samma som för PowerShell, det vill säga `Microsoft-Windows-PowerShell, Operational`.

## <a name="support-for-basic-authentication"></a>Stöd för grundläggande autentisering

I WMF 5,1 har PackageManagement stöd för att söka efter och installera paket från en lagrings plats som kräver grundläggande autentisering. Du kan ange dina autentiseringsuppgifter till `Find-Package` och `Install-Package`-cmdletar. Till exempel:

```powershell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

## <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Stöd för att använda PackageManagement bakom en proxy

I WMF 5,1 tar PackageManagement nu nya proxyadresser `-ProxyCredential` och `-Proxy`. Med dessa parametrar kan du ange proxy-URL och autentiseringsuppgifter till PackageManagement-cmdletar. Som standard används systemproxy-inställningar. Till exempel:

```powershell
Find-Package -Source https://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
