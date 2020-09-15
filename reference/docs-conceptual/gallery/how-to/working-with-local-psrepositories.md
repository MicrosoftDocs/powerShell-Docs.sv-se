---
ms.date: 11/06/2018
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery, psget
title: Arbeta med lokala PSRepositories
ms.openlocfilehash: 421b73c141c7551224e2298f51464a19bc736d0e
ms.sourcegitcommit: 105c69ecedfe5180d8c12e8015d667c5f1a71579
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85837587"
---
# <a name="working-with-private-powershellget-repositories"></a>Arbeta med privata PowerShellGet-lagringsplatser

PowerShellGet-modulen stöder andra databaser än PowerShell-galleriet.
Dessa cmdletar möjliggör följande scenarier:

- Stöd för en betrodd, fördefinierad uppsättning PowerShell-moduler för användning i din miljö
- Testa en CI/CD-pipeline som bygger PowerShell-moduler eller-skript
- Leverera PowerShell-skript och moduler till system som inte har åtkomst till Internet
- Leverera PowerShell-skript och moduler som endast är tillgängliga för din organisation

Den här artikeln beskriver hur du konfigurerar en lokal PowerShell-lagringsplats. Artikeln beskriver också [OfflinePowerShellGetDeploy][] -modulen som är tillgänglig från PowerShell-galleriet. Den här modulen innehåller cmdlets för att installera den senaste versionen av PowerShellGet i din lokala lagrings plats.

## <a name="local-repository-types"></a>Typer av lokala databaser

Det finns två sätt att skapa en lokal PSRepository: NuGet-Server eller fil resurs. Varje typ har fördelar och nack delar:

### <a name="nuget-server"></a>NuGet-Server

| Fördelar| Nackdelar |
| --- | --- |
| Liknar PowerShellGallery-funktioner | En app med flera nivåer kräver åtgärder som planerar & |
| NuGet integreras med Visual Studio, andra verktyg | Autentiserings modell och NuGet Accounts Management krävs |
| NuGet stöder metadata i `.Nupkg` paket | Publicering kräver hantering av API-nyckel & underhåll |
| Tillhandahåller sökning, paket administration osv. | |

### <a name="file-share"></a>Filresurs

| Fördelar| Nackdelar |
| --- | --- |
| Enkelt att konfigurera, säkerhetskopiera och underhålla | Metadata som används av PowerShellGet är inte tillgängliga |
| Enkel säkerhets modell – användar behörigheter på resursen | Inget användar gränssnitt utöver grundläggande fil resurs |
| Inga begränsningar, som att ersätta befintliga objekt | Begränsad säkerhet och ingen inspelning av vem som uppdaterar vad |

PowerShellGet fungerar med antingen typ och har stöd för att hitta versioner och beroende installationer.
Men vissa funktioner som fungerar för PowerShell-galleriet är inte tillgängliga för bas-NuGet-servrar eller fil resurser.

- Allt är ett paket – ingen differentiering av skript, moduler, DSC-resurser eller roll funktioner.
- Fil resurs servrar kan inte se paketets metadata, inklusive taggar.

## <a name="creating-a-local-repository"></a>Skapa en lokal lagrings plats

I följande artikel visas stegen för att skapa en egen NuGet-Server.

- [NuGet. Server][]

Följ stegen upp till punkten för att lägga till paket. Stegen för att [publicera ett paket](#publishing-to-a-local-repository) beskrivs längre fram i den här artikeln.

Se till att användarna har behörighet att komma åt fil resursen för en fil resursbaserade lagrings plats.

## <a name="registering-a-local-repository"></a>Registrera en lokal lagrings plats

Innan du kan använda en lagrings plats måste du registrera den med hjälp av `Register-PSRepository` kommandot.
I exemplen nedan är **InstallationPolicy** inställt på *betrott*, enligt det antagande att du litar på din egen lagrings plats.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

Anteckna skillnaden mellan de två kommandona som hanterar **ScriptSourceLocation**. För en fil resursbaserade databaser måste **SourceLocation** och **ScriptSourceLocation** matcha. För en webbaserad lagrings plats måste de vara olika, så i det här exemplet läggs ett efterföljande "/" till i **SourceLocation**.

Om du vill att det nyligen skapade PSRepository ska vara standard lagrings platsen måste du avregistrera alla andra PSRepositories. Exempel:

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> Databas namnet "PSGallery" är reserverat för användning av PowerShell-galleriet. Du kan avregistrera PSGallery, men du kan inte återanvända namnet PSGallery för andra lagrings platser.

Om du behöver återställa PSGallery kör du följande kommando:

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Publicera till en lokal lagrings plats

När du har registrerat den lokala PSRepository kan du publicera den på din lokala PSRepository. Det finns två huvudsakliga publicerings scenarier: publicera en egen modul och publicera en modul från PSGallery.

### <a name="publishing-a-module-you-authored"></a>Publicera en modul som du har skapat

Använd `Publish-Module` och `Publish-Script` för att publicera modulen i din lokala PSRepository på samma sätt som du gör för PowerShell-galleriet.

- Ange plats för koden
- Ange en API-nyckel
- Ange namnet på databasen. Till exempel `-PSRepository LocalPSRepo`

> [!NOTE]
> Du måste skapa ett konto på NuGet-servern och sedan logga in för att generera och spara API-nyckeln.
> För en fil resurs använder du en icke-tom sträng för NuGetApiKey-värdet.

Exempel:

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey $nuGetApiKey
```

> [!IMPORTANT]
> För att säkerställa säkerheten bör API-nycklar inte hårdkodas i skript. Använd ett säkert nyckel hanterings system. När du kör ett kommando manuellt ska API-nycklar inte skickas som vanlig text för att undvika att den loggas. `Read-Host` cmdleten kan användas för att på ett säkert sätt skicka värdet för API-nyckeln.

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

### <a name="publishing-a-module-from-the-psgallery"></a>Publicera en modul från PSGallery

Om du vill publicera en modul från PSGallery till din lokala PSRepository kan du använda cmdleten "Save-Package".

- Ange paketets namn
- Ange "NuGet" som Provider
- Ange PSGallery-platsen som källa (https://www.powershellgallery.com/api/v2)
- Ange sökvägen till din lokala lagrings plats

Exempel:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider NuGet -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Om din lokala PSRepository är webbaserad kräver det ytterligare ett steg som använder nuget.exe för att publicera.

Se dokumentationen för att använda [nuget.exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>Installera PowerShellGet på ett frånkopplat system

Det är svårt att distribuera PowerShellGet i miljöer som kräver att system kopplas från Internet. PowerShellGet har en start process som installerar den senaste versionen första gången den används. OfflinePowerShellGetDeploy-modulen i PowerShell-galleriet tillhandahåller cmdlets som stöder den här start processen.

Om du vill starta en offline-distribution måste du:

- Hämta och installera OfflinePowerShellGetDeploy-datorn och dina frånkopplade system
- Ladda ned PowerShellGet och dess beroenden på det Internet-anslutna systemet med `Save-PowerShellGetForOffline` cmdleten
- Kopiera PowerShellGet och dess beroenden från det Internet-anslutna systemet till det frånkopplade systemet
- Använd `Install-PowerShellGetOffline` på det frånkopplade systemet för att placera PowerShellGet och dess beroenden i rätt mappar

Följande kommandon används `Save-PowerShellGetForOffline` för att skicka alla komponenter till en mapp `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

I det här läget måste du göra innehållet `F:\OfflinePowerShellGet` tillgängligt för de frånkopplade systemen. Kör `Install-PowerShellGetOffline` cmdleten för att installera PowerShellGet på det frånkopplade systemet.

> [!NOTE]
> Det är viktigt att du inte kör PowerShellGet i PowerShell-sessionen innan du kör de här kommandona. När PowerShellGet har lästs in i sessionen går det inte att uppdatera komponenterna. Om du startar PowerShellGet av misstag, avslutar du och startar om PowerShell.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

När du har kört dessa kommandon är du redo att publicera PowerShellGet till din lokala lagrings plats.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey $nuGetApiKey
```

> [!IMPORTANT]
> För att säkerställa säkerheten bör API-nycklar inte hårdkodas i skript. Använd ett säkert nyckel hanterings system. När du kör ett kommando manuellt ska API-nycklar inte skickas som vanlig text för att undvika att den loggas. `Read-Host` cmdleten kan användas för att på ett säkert sätt skicka värdet för API-nyckeln.

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

## <a name="use-packaging-solutions-to-host-powershellget-repositories"></a>Använda förpacknings lösningar för att vara värdar för PowerShellGet-databaser

Du kan också använda paket lösningar som Azure-artefakter som värdar för en privat eller offentlig PowerShellGet-lagringsplats. Mer information och instruktioner finns i dokumentationen för [Azure-artefakter](/azure/devops/artifacts/tutorials/private-powershell-library).

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[NuGet. Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
