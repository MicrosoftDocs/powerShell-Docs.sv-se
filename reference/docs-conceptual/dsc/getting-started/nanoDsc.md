---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Använda DSC på Nano Server
ms.openlocfilehash: fb826455c21833ae4c8dc2ecd731ffce6bf7eaba
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941882"
---
# <a name="using-dsc-on-nano-server"></a>Använda DSC på Nano Server

> Gäller för: Windows PowerShell 5,0

**DSC på Nano Server** är ett valfritt paket i `NanoServer\Packages` mappen på Windows Server 2016-mediet. Paketet kan installeras när du skapar en virtuell hård disk för en Nano Server genom att ange **Microsoft-NanoServer-DSC-Package** som värdet för parametern **packages** för funktionen **New-NanoServerImage** . Om du till exempel skapar en virtuell hård disk för en virtuell dator ser kommandot ut så här:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Information om hur du installerar och använder Nano Server, samt hur du hanterar Nano Server med PowerShell-fjärrkommunikation, finns [komma igång med Nano Server](/windows-server/get-started/getting-started-with-nano-server).

## <a name="dsc-features-available-on-nano-server"></a>DSC-funktioner som är tillgängliga på Nano Server

Eftersom Nano Server bara stöder en begränsad uppsättning API: er jämfört med en fullständig version av Windows Server, har DSC på Nano Server inte fullt fungerande paritet med DSC som körs på fullständiga SKU: er under tiden. DSC på Nano Server är i aktiv utveckling och funktionen är inte slutförd ännu.

Följande DSC-funktioner är för närvarande tillgängliga på Nano Server:

Både push-och pull-lägen

- Alla DSC-cmdletar som finns i en fullständig version av Windows Server, inklusive följande:
- [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [Aktivera – DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [Publicera – DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [Uppdatera – DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [Restore-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [Invoke-Dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [Find-Dscresource Keyword Supports](/powershell/module/powershellget/find-dscresource?view=powershell-6)
- [Get-Dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- Kompilera konfigurationer (se [DSC-konfigurationer](../configurations/configurations.md))

  **Problem:** Lösen ords kryptering (se [skydda MOF-filen](../pull-server/secureMOF.md)) under konfigurations kompileringen fungerar inte.

- Kompilera metaconfigurations (se [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md))

- Köra en resurs under användar kontext (se [köra DSC med användarautentiseringsuppgifter (runas)](../configurations/runAsUser.md))

- Klassbaserade resurser (se [skriva en anpassad DSC-resurs med PowerShell-klasser](/previous-versions//dn948461(v=technet.10)))

- Fel sökning av DSC-resurser (se [fel sökning av DSC-resurser](../troubleshooting/debugResource.md))

  **Problem:** Fungerar inte om en resurs använder PsDscRunAsCredential (se [köra DSC med](../configurations/runAsUser.md)användarautentiseringsuppgifter)

- [Ange beroenden mellan noder](../configurations/crossNodeDependencies.md)

- [Resurs version](../configurations/sxsResource.md)

- Hämta klient (konfigurationer & resurser) (se [Konfigurera en pull-klient med hjälp av konfigurations namn](../pull-server/pullClientConfigNames.md))

- [Partiella konfigurationer (pull-& push)](../pull-server/partialConfigs.md)

- [Rapportering till hämtnings Server](../pull-server/reportServer.md)

- MOF-kryptering

- Händelse loggning

- Azure Automation DSC-rapportering

- Resurser som är helt funktionella

- **Arkiv**
- **Miljö**
- **Fil**
- **Kvorumloggen**
- **ProcessSet**
- **Registernyckeln**
- **Över**
- **WindowsPackageCab**
- **WindowsProcess**
- **WaitForAll** (se [ange beroenden mellan noder](../configurations/crossNodeDependencies.md))
- **WaitForAny** (se [ange beroenden mellan noder](../configurations/crossNodeDependencies.md))
- **WaitForSome** (se [ange beroenden mellan noder](../configurations/crossNodeDependencies.md))

- Resurser som är delvis funktionella
- **Grupp**
- **GroupSet**

  **Problem:** Över resurser fungerar inte om en speciell instans anropas två gånger (kör samma konfiguration två gånger)

- **Tjänst**
- **ServiceSet**

  **Problem:** Fungerar bara för att starta/stoppa tjänsten (status). Miss lyckas, om ett försök att ändra andra tjänsteattribut som startuptype tjänst, autentiseringsuppgifter, beskrivning osv. Det fel som har utlösts liknar:

  *Det går inte att hitta typen [Management. managementobject]: kontrol lera att sammansättningen som innehåller den här typen har lästs in.*

- Resurser som inte fungerar
- **Användare**

## <a name="dsc-features-not-available-on-nano-server"></a>DSC-funktioner är inte tillgängliga på Nano Server

Följande DSC-funktioner är för närvarande inte tillgängliga på Nano Server:

- Dekryptera MOF-dokument med krypterade lösen ord
- Pull-server – du kan för närvarande inte konfigurera en pull-server på Nano Server
- Allt som inte finns med i listan över funktioner fungerar

## <a name="using-custom-dsc-resources-on-nano-server"></a>Använda anpassade DSC-resurser på Nano Server

På grund av en begränsad uppsättning Windows-API: er och CLR-bibliotek som är tillgängliga på Nano Server, fungerar DSC-resurser som fungerar på den fullständiga CLR-versionen av Windows inte nödvändigt vis på Nano Server.
Slutför testet från slut punkt till slut punkt innan du distribuerar några anpassade DSC-resurser till en produktions miljö.

## <a name="see-also"></a>Se även

- [Komma igång med Nano Server](/windows-server/get-started/getting-started-with-nano-server)
