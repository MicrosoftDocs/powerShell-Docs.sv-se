---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
contributor: jianyunt, quoctruong
title: Förbättringar av pakethantering i WMF 5.1
ms.openlocfilehash: 30ef59ed9dc0d56636d85cc6e53523a9a73963a4
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794288"
---
# <a name="improvements-to-package-management-in-wmf-51"></a>Förbättringar av pakethantering i WMF 5.1

## <a name="improvements-in-packagemanagement"></a>Förbättringar i PackageManagement

Följande är de korrigeringar som gjorts i WMF 5.1:

### <a name="version-alias"></a>Version Alias

**Scenario**: Om du har version 1.0 och 2.0 i ett paket, P1, som installeras på datorn, och du vill avinstallera version 1.0, kör du `Uninstall-Package -Name P1 -Version 1.0` och räknar med version 1.0 avinstalleras när du har kört cmdlet: en. Men resultatet är att version 2.0 avinstalleras.

Detta beror på att den `-Version` parametern är ett alias för den `-MinimumVersion` parametern. När PackageManagement är ute efter ett kvalificerat paket med den lägsta versionen av 1.0, returnerar den senaste versionen. Det här beteendet är förväntat i normala fall eftersom att söka efter den senaste versionen är vanligtvis det önskade resultatet. Det bör dock inte tillämpas på den `Uninstall-Package` fall.

**Lösningen**: bort `-Version` alias helt i PackageManagement (alias) OneGet) och PowerShellGet.

### <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>Flera prompter för start av NuGet-providern

**Scenario**: När du kör `Find-Module` eller `Install-Module` eller andra PackageManagement-cmdletar på din dator för första gången, PackageManagement försöker starta NuGet-providern. Detta sker eftersom providern PowerShellGet också NuGet-providern använder för att ladda ned PowerShell-moduler. PackageManagement sedan uppmanas användaren om behörighet att installera NuGet-providern. När användaren väljer ”Ja” för den startprogram, installeras den senaste versionen av NuGet-providern.

Men i vissa fall när du har en äldre version av NuGet-providern på datorn, den äldre versionen av NuGet som ibland hämtar läsas in först i PowerShell-sessionen (det vill säga konkurrenstillstånd i PackageManagement). PowerShellGet kräver dock den senare versionen av NuGet-providern fungerar, så PowerShellGet frågar PackageManagement ska kunna starta NuGet-providern igen. Detta resulterar i flera prompter för start av NuGet-providern.

**Lösningen**: Läser in den senaste versionen av NuGet-providern för att undvika flera prompter för start av NuGet-providern i WMF5.1, PackageManagement.

Du kan även undvika det här problemet genom att manuellt ta bort den gamla versionen av NuGet-providern (NuGet-Anycpu.exe) om det finns från $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies


### <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>Stöd för PackageManagement på datorer med endast intranät-åtkomst

**Scenario**: Enterprise-scenario, personer arbetar under en miljö där det finns ingen åtkomst till Internet men intranätet endast. PackageManagement inte stöd för det här fallet i WMF 5.0.

**Scenario**: I WMF 5.0 PackageManagement inte stöd för datorer som har endast intranät (men inte Internet) åtkomst.

**Lösningen**: Du kan följa stegen nedan för att Tillåt intranät-datorer använder PackageManagement i WMF 5.1:

1. Ladda ned NuGet-providern använder en annan dator som har en Internetanslutning med hjälp av `Install-PackageProvider -Name NuGet`.

2. Hitta NuGet-providern under `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` eller `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. Kopiera de binära filerna till en mapp eller plats som intranät-datorn kan komma åt och sedan installera NuGet-providern med `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


### <a name="event-logging-improvements"></a>Förbättringar av händelse-loggning

När du installerar paket, ändrar du tillståndet för datorn. I WMF 5.1 PackageManagement nu loggar händelser i Windows-händelseloggen för `Install-Package`, `Uninstall-Package`, och `Save-Package` aktiviteter. Händelseloggen är desamma som för PowerShell, det vill säga `Microsoft-Windows-PowerShell, Operational`.

### <a name="support-for-basic-authentication"></a>Stöd för grundläggande autentisering

I WMF 5.1 PackageManagement har stöd för att söka efter och installera paket från en lagringsplats som kräver grundläggande autentisering. Du kan ange dina autentiseringsuppgifter för att den `Find-Package` och `Install-Package` cmdletar. Till exempel:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

### <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Stöd för användning av PackageManagement bakom en proxyserver

I WMF 5.1 PackageManagement tar nu bara nya proxyparametrar `-ProxyCredential` och `-Proxy`. Med dessa parametrar kan ange du proxy-URL och autentiseringsuppgifter i PackageManagement-cmdletar. System-proxyinställningar används som standard. Till exempel:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
