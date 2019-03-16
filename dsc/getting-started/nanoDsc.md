---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Använda DSC på Nano Server
ms.openlocfilehash: ac5eaf3885788f40e12e4f0a0f19025668280f7e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054670"
---
# <a name="using-dsc-on-nano-server"></a>Använda DSC på Nano Server

> Gäller för: Windows PowerShell 5.0

**DSC på Nano Server** är ett valfritt paket i den `NanoServer\Packages` mappen för Windows Server 2016 media. Paketet kan installeras när du skapar en virtuell Hårddisk för Nano Server genom att ange **Microsoft-NanoServer-DSC-Package** som värde för den **paket** -parametern för den **New-NanoServerImage**  funktion. Om du skapar en virtuell Hårddisk för en virtuell dator, till exempel se kommandot ut så här:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Information om installation och användning av Nano Server, samt hur du hanterar Nano Server med PowerShell-fjärrkommunikation finns i [komma igång med Nano Server](/windows-server/get-started/getting-started-with-nano-server).

## <a name="dsc-features-available-on-nano-server"></a>DSC-funktioner som är tillgängliga på Nano Server

Eftersom Nano Server stöder endast en begränsad uppsättning API: er jämfört med en fullständig version av Windows Server, har DSC på Nano Server inte fullständiga funktioner i paritet med DSC som körs på fullständiga SKU: er för tillfället. DSC på Nano Server är i aktivt med utveckling och ännu inte är funktionen som är klar.

Följande DSC-funktioner är tillgängliga på Nano Server:

Både sändnings- och mottagningsläge

- Alla DSC-cmdletar som finns på en fullständig version av Windows Server, inklusive följande:
- [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [Restore-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- Kompilera konfigurationer (se [DSC-konfigurationer](../configurations/configurations.md))

  **Problem:** Lösenordskryptering (se [skydda MOF-filen](../pull-server/secureMOF.md)) under konfigurationen kompilering fungerar inte.

- Kompilera metaconfigurations (se [konfigurerar den lokala Konfigurationshanteraren](../managing-nodes/metaConfig.md))

- Kör en resurs under användarkontext (se [kör DSC med autentiseringsuppgifterna för användaren (kör)](../configurations/runAsUser.md))

- MOF-baserade resurser (se [skriva en anpassad DSC-resurs med PowerShell-klasser](../resources/authoringResourceClass.md))

- Felsökning av DSC-resurser (se [felsökning DSC-resurser](../troubleshooting/debugResource.md))

  **Problem:** Fungerar inte om en resurs använder PsDscRunAsCredential (se [kör DSC med autentiseringsuppgifterna för användaren](../configurations/runAsUser.md))

- [Ange beroenden mellan noder](../configurations/crossNodeDependencies.md)

- [Resurs-versionshantering](../configurations/sxsResource.md)

- Pullklient (konfigurationer och resurser) (se [konfigurera en hämtningsklient med konfigurationsnamn](../pull-server/pullClientConfigNames.md))

- [Partiella konfigurationer (pull och push)](../pull-server/partialConfigs.md)

- [Rapporterar till hämtningsserver](../pull-server/reportServer.md)

- MOF-kryptering

- Händelseloggning

- Azure Automation DSC-rapportering

- Resurser som är helt funktionella

- **Arkiv**
- **Miljö**
- **Fil**
- **log**
- **ProcessSet**
- **Registret**
- **skriptet**
- **WindowsPackageCab**
- **WindowsProcess**
- **WaitForAll** (se [att ange beroenden mellan noder](../configurations/crossNodeDependencies.md))
- **WaitForAny** (se [att ange beroenden mellan noder](../configurations/crossNodeDependencies.md))
- **WaitForSome** (se [att ange beroenden mellan noder](../configurations/crossNodeDependencies.md))

- Resurser som delvis fungerar
- **Grupp**
- **GroupSet**

  **Problem:** Ovan resurser misslyckas om specifika instans kallas två gånger (som kör samma konfiguration för två gånger)

- **Tjänst**
- **ServiceSet**

  **Problem:** Fungerar bara för Starta/Stoppa tjänst (status). Misslyckas om någon försöker ändra andra attribut som startuptype för, autentiseringsuppgifter, beskrivning osv... Felet uppstod är ungefär:

  *Det går inte att hitta typen [management.managementobject]: Kontrollera att sammansättningen som innehåller den här typen har lästs in.*

- Resurser som inte fungerar
- **Användaren**

## <a name="dsc-features-not-available-on-nano-server"></a>DSC-funktioner som inte är tillgängliga på Nano Server

Följande DSC-funktioner är inte tillgängliga på Nano Server:

- Dekryptera MOF-dokument med krypterade password(s)
- Hämtningsservern – du kan inte för närvarande konfigurera en pull-server på Nano Server
- Något som inte är i listan över funktionen fungerar

## <a name="using-custom-dsc-resources-on-nano-server"></a>Använda anpassade DSC-resurser på Nano Server

På grund av en begränsad uppsättning Windows API: er och CLR-bibliotek som är tillgängliga på Nano Server fungerar DSC-resurser som arbetar med den fullständiga CLR-versionen av Windows inte nödvändigtvis på Nano Server.
Slutför slutpunkt till slutpunkt testning innan du distribuerar eventuella anpassade DSC-resurser till en produktionsmiljö.

## <a name="see-also"></a>Se även

- [Komma igång med Nano Server](/windows-server/get-started/getting-started-with-nano-server)
