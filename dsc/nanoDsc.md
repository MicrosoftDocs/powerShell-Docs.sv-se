---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Använda DSC på Nano Server
ms.openlocfilehash: 9ebc1f046893c360538009b5ecbcfb6456f92bbb
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="using-dsc-on-nano-server"></a>Använda DSC på Nano Server

> Gäller för: Windows PowerShell 5.0

**DSC på Nano Server** är ett valfritt paket i den `NanoServer\Packages` mapp på Windows Server 2016-mediet. Paketet kan installeras när du skapar en virtuell Hårddisk för en Nano Server genom att ange **Microsoft-NanoServer-DSC-Package** som värde för den **paket** parameter för den **ny NanoServerImage**  funktion. Till exempel om du skapar en virtuell Hårddisk för en virtuell dator, skulle kommandot se ut så här:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Mer information om hur du installerar och använder Nano Server, samt hur du hanterar Nano Server med PowerShell-fjärrkommunikation finns [komma igång med Nano Server](https://technet.microsoft.com/library/mt126167.aspx).


## <a name="dsc-features-available-on-nano-server"></a>DSC-funktioner som är tillgängliga på Nano Server

 Eftersom Nano Server stöder endast en begränsad uppsättning API: er jämfört med en fullständig version av Windows Server, har DSC på Nano Server inte fullständig jämlika med DSC som körs på fullständig SKU: er för närvarande. DSC på Nano Server är i aktiv utveckling och ännu inte är funktionen som är klar.

 Följande DSC-funktioner är tillgängliga på Nano Server:


* Både sändning och mottagning lägen

* Alla DSC-cmdletar som finns på en fullständig version av Windows Server, inklusive följande:
  * [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx)
  * [Set-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn521621.aspx)
  * [Aktivera DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [Inaktivera DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx)
  * [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [Stoppa DscConfiguration](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [Testa DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)
  * [Publish-DscConfiguraiton](https://technet.microsoft.com/en-us/library/mt517875.aspx)
  * [Uppdatera DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [Återställ DscConfiguration](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [Remove-DscConfigurationDocument](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [Hitta DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [Ny DscChecksum](https://technet.microsoft.com/en-us/library/dn521622.aspx)

* Kompilera konfigurationer (se [DSC-konfigurationer](configurations.md))

  **Problem:** lösenordskryptering (se [skydda MOF-filen](securemof.md)) under konfigurationen kompilering fungerar inte.

* Kompilera metaconfigurations (se [konfigurera den lokala Configuration Manager](metaConfig.md))

* Kör en resurs under användarkontext (se [kör DSC med autentiseringsuppgifterna för användaren (RunAs)](runAsUser.md))

* Klass-baserade resurser (se [skriva en anpassad DSC-resurs med PowerShell klasser](authoringResourceClass.md))

* Felsökning av DSC-resurser (se [felsökning DSC resurser](debugresource.md))

  **Problem:** fungerar inte om en resurs använder PsDscRunAsCredential (se [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md))

* [Ange beroenden mellan noder](crossNodeDependencies.md)

* [Resursen versionshantering](sxsResource.md)

* Pull-klienten (konfigurationer och resurser) (se [ställa in en pull-klient som använder konfigurationsnamn](pullClientConfigNames.md))

* [Partiell konfigurationer (pull och push)](partialConfigs.md)

* [Rapporterar till pull-server](reportServer.md)

* MOF-kryptering

* Händelseloggning

* Azure Automation DSC-rapportering

* Resurser som är helt funktionella
  * [Arkiv](archiveResource.md)
  * [Miljö](environmentResource.md)
  * [Filen](fileResource.md)
  * [Logg](logResource.md)
  * ProcessSet
  * [Registret](registryResource.md)
  * [Skriptet](scriptResource.md)
  * WindowsPackageCab
  * [WindowsProcess](windowsProcessResource.md)
  * WaitForAll (se [angett beroenden mellan noder](crossNodeDependencies.md))
  * WaitForAny (se [angett beroenden mellan noder](crossNodeDependencies.md))
  * WaitForSome (se [angett beroenden mellan noder](crossNodeDependencies.md))

* Resurser som delvis fungerar
  * [Grupp](groupResource.md)
  * GroupSet

  **Problem:** ovan resurser misslyckas om specifika instansen anropas två gånger (körs två gånger i samma konfiguration)

  * [Tjänsten](serviceResource.md)
  * ServiceSet

  **Problem:** fungerar bara för Starta/Stoppa tjänst (status). Misslyckas om någon försöker ändra andra attribut som startuptype, autentiseringsuppgifter, beskrivning etc... Felet uppstod liknar:

  *Det går inte att hitta typen [management.managementobject]: Kontrollera att sammansättningen som innehåller den här typen är inläst.*

* Resurser som inte fungerar
  * [Användaren](userResource.md)


## <a name="dsc-features-not-available-on-nano-server"></a>DSC-funktioner som inte finns på Nano Server

Följande DSC-funktioner är inte tillgängliga på Nano Server:

* Dekryptera MOF-dokument med krypterade password(s)
* Pull-Server – du kan inte just nu konfigurera en pull-server på Nano Server
* Något som inte finns med i listan över funktionen fungerar

## <a name="using-custom-dsc-resources-on-nano-server"></a>Med hjälp av anpassade DSC-resurser på Nano Server

På grund av en begränsade uppsättningar av Windows API: er och CLR-bibliotek som är tillgängliga på Nano Server fungerar DSC-resurser som kan användas i den fullständiga CLR-versionen av Windows inte nödvändigtvis på Nano Server.
Slutföra slutpunkt till slutpunkt testning innan du distribuerar några anpassade DSC-resurser i en produktionsmiljö.

## <a name="see-also"></a>Se även
- [Komma igång med Nano Server](https://technet.microsoft.com/library/mt126167.aspx)