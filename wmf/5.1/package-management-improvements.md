---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
contributor: jianyunt, quoctruong
title: "Förbättringar av hantering av paketet i WMF 5.1"
ms.openlocfilehash: b55a1742530b7cd48d60d79b7d4866ebee80a3b6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="improvements-to-package-management-in-wmf-51"></a>Förbättringar av hantering av paketet i WMF 5.1#

## <a name="improvements-in-packagemanagement"></a>Förbättringar i PackageManagement ##
Följande är de korrigeringar som gjorts i WMF 5.1: 

### <a name="version-alias"></a>Version Alias

**Scenariot**: Om du har version 1.0 och 2.0 i ett paket, P1, som installeras på datorn, och du vill avinstallera version 1.0, kör du `Uninstall-Package -Name P1 -Version 1.0` och räknar version 1.0 avinstalleras när du kör cmdleten. Men resultatet är att version 2.0 hämtar avinstalleras.  
    
Detta beror på att den `-Version` parametern är ett alias för den `-MinimumVersion` parameter. När PackageManagement är ute efter ett kvalificerat paket med den lägsta versionen av 1.0, returnerar den senaste versionen. Det här beteendet är förväntat i vanliga fall eftersom söka efter den senaste versionen är vanligtvis det önskade resultatet. Det bör dock inte tillämpas på den `Uninstall-Package` fallet.
    
**Lösningen**: bort `-Version` alias helt i PackageManagement (kallas även OneGet) och PowerShellGet. 

### <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>Flera efterfrågas startprogram NuGet-provider

**Scenariot**: när du kör `Find-Module` eller `Install-Module` eller andra PackageManagement cmdlet: ar på din dator för första gången, PackageManagement försöker bootstrap NuGet-providern. Detta sker eftersom providern PowerShellGet också NuGet-providern använder för att ladda ned PowerShell-moduler. PackageManagement uppmanar sedan användaren att installera NuGet-providern. När användaren väljer ”Ja” för den startprogram, installeras den senaste versionen av NuGet-providern. 
    
Men i vissa fall, hämtar när du har en äldre version av NuGet-providern installerad på datorn, ibland den äldre versionen av NuGet laddas först i PowerShell-session (dvs konkurrenstillstånd i PackageManagement). Men PowerShellGet kräver en senare version av NuGet-providern fungerar, så PowerShellGet frågar PackageManagement att starta NuGet-providern igen. Detta resulterar i flera efterfrågas startprogram NuGet-providern.

**Lösningen**: I WMF5.1, PackageManagement laddas den senaste versionen av NuGet-providern för att undvika flera efterfrågas startprogram NuGet-providern.

Du kan även undvika det här problemet genom att manuellt ta bort den gamla versionen av NuGet-providern (NuGet-Anycpu.exe) om det finns från $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies


### <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>Stöd för PackageManagement på datorer med intranät-åtkomst

**Scenariot**: enterprise-scenariot personer arbetar i en miljö där det finns ingen tillgång till Internet men intranätet endast. PackageManagement stöder inte det här fallet i WMF 5.0.

**Scenariot**: WMF 5.0, PackageManagement hade inte stöd för datorer som har endast intranät (men inte Internet) åtkomst.

**Lösningen**: I WMF 5.1 följer du dessa steg för att tillåta intranät-datorer använder PackageManagement:

1. Hämta NuGet-providern använder en annan dator som har en Internetanslutning med hjälp av `Install-PackageProvider -Name NuGet`.

2. Hitta NuGet-providern under `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` eller `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. Kopiera de binära filerna till en mapp eller plats som intranätdatorn kan komma åt och installera NuGet-provider med `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


### <a name="event-logging-improvements"></a>Förbättringar av händelse loggning

När du installerar paket, ändrar du datorns tillstånd. I WMF 5.1 PackageManagement nu loggar händelser till händelseloggen för `Install-Package`, `Uninstall-Package`, och `Save-Package` aktiviteter. Händelseloggen är desamma som för PowerShell, d.v.s. `Microsoft-Windows-PowerShell, Operational`.

### <a name="support-for-basic-authentication"></a>Stöd för grundläggande autentisering

I WMF 5.1 stöder PackageManagement söka efter och installera paket från en databas som kräver grundläggande autentisering. Du kan ange dina autentiseringsuppgifter för den `Find-Package` och `Install-Package` cmdlets. Till exempel:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
### <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Stöd för användning av PackageManagement bakom en proxyserver

I WMF 5.1 tar PackageManagement nu nya proxyparametrar `-ProxyCredential` och `-Proxy`. Med dessa parametrar kan ange du proxy-URL och autentiseringsuppgifter till PackageManagement cmdletar. Som standard används systemets proxyinställningar. Till exempel:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```

