---
ms.date: 11/06/2018
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery, psget
title: Arbeta med lokala PSRepositories
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619267"
---
# <a name="working-with-local-powershellget-repositories"></a>Arbeta med lokala PowerShellGet-databaser

PowerShellGet-modul support lagringsplatser än PowerShell-galleriet.
Dessa cmdletar aktivera följande scenarier:

- Stöd för en betrodd, före validerade uppsättning PowerShell-moduler för användning i din miljö
- Testa en CI/CD-pipeline som bygger på PowerShell-moduler eller skript
- Leverera PowerShell-skript och moduler för system där det går inte att få åtkomst till internet

Den här artikeln beskriver hur du ställer in en lokal PowerShell-lagringsplats. Den här artikeln beskriver också den [OfflinePowerShellGetDeploy][] modul som är tillgängliga från PowerShell-galleriet. Den här modulen innehåller cmdlets för att installera den senaste versionen av PowerShellGet i din lokala lagringsplats.

## <a name="local-repository-types"></a>Lagringsplats-typer

Det finns två sätt att skapa en lokal PSRepository: NuGet server eller filresurs. Varje typ har fördelar och nackdelar:

NuGet-Server

| Fördelar| Nackdelar |
| --- | --- |
| Nära efterliknar PowerShellGallery-funktioner | Flerskiktat program kräver åtgärder planering och support |
| NuGet kan integreras med andra verktyg för Visual Studio | Autentisering och hantering av NuGet-konton som behövs |
| NuGet har stöd för metadata i `.Nupkg` paket | Publicering kräver att API-nyckel för hantering och underhåll |
| Innehåller Sök, Paketadministration osv. | |

Filresurs

| Fördelar| Nackdelar |
| --- | --- |
| Enkelt att ställa in, säkerhetskopiera och underhålla | Metadata som används av PowerShellGet är inte tillgänglig |
| Enkel säkerhetsmodell - användarbehörigheter för resursen | Något användargränssnitt bortom grundläggande filresurs |
| Utan begränsningar, till exempel ersätta befintliga objekt | Begränsad säkerhet och ingen registrering av som uppdaterar vad |

PowerShellGet fungerar med typen och har stöd för att hitta versioner och installationen av beroenden.
Vissa funktioner som fungerar för PowerShell-galleriet är dock inte tillgängliga för grundläggande NuGet-servrar eller filresurser.

- Allt är ett paket - ingen skillnad i skript, moduler, DSC-resurser eller rollfunktioner.
- Dela filservrar kan inte se paketmetadata, inklusive taggar.

## <a name="creating-a-local-repository"></a>Skapa en lokal databas

I följande artikel innehåller stegen för att konfigurera din egen NuGet-Server.

- [NuGet.Server][]

Följ stegen i det läget för att lägga till paket. Stegen för att [publicerar ett paket](#publishing-to-a-local-repository) beskrivs senare i den här artikeln.

För en fil filresursbaserade lagringsplats, se till att dina användare har behörighet att komma åt filresursen.

## <a name="registering-a-local-repository"></a>Registrera en lokal databas

Innan en databas kan användas, måste den vara registrerad med hjälp av den `Register-PSRepository` kommando.
I exemplen nedan, den **InstallationPolicy** är inställd på *betrodda*, på antagandet att du har förtroende för en egen databas.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

Anteckna skillnaden mellan hur de två kommandona hanterar **ScriptSourceLocation**. För en fil filresursbaserade lagringsplatser, den **SourceLocation** och **ScriptSourceLocation** måste matcha. För en webbaserad lagringsplats, och de måste vara olika, så i det här exemplet som en avslutande ”/” har lagts till i den **SourceLocation**.

Om du vill att den nyligen skapade PSRepository vara standard-databasen måste du avregistrera alla andra PSRepositories. Till exempel:

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> Namnet på lagringsplatsen ”PSGallery” är reserverade för användning av PowerShell-galleriet. Du kan avregistrera PSGallery, men du kan inte återanvända namnet PSGallery för en annan lagringsplats.

Om du vill återställa PSGallery kör du följande kommando:

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Publicering till en lokal databas

När du har registrerat den lokala PSRepository, kan du publicera dina lokala PSRepository. Det finns två huvudscenarier för publicering: publicera en egen modul och publicera en modul från PSGallery.

### <a name="publishing-a-module-you-authored"></a>Publicera en modul som du skapat

Använd `Publish-Module` och `Publish-Script` att publicera din modul till din lokala PSRepository på samma sätt som du gör med PowerShell-galleriet.

- Ange platsen för din kod
- Ange en API-nyckel
- Ange namnet på lagringsplatsen. Till exempel `-PSRepository LocalPSRepo`

> [!NOTE]
> Du måste skapa ett konto på NuGet-servern och sedan logga in att generera och spara API-nyckeln.
> Använd alla icke-tomma strängar för NuGetApiKey värdet för en filresurs.

Exempel:

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> För att garantera säkerheten, får API-nycklar inte vara hårdkodade i skript. Använd en säker nyckelhanteringssystem.

### <a name="publishing-a-module-from-the-psgallery"></a>Publicera en modul från PSGallery

Om du vill publicera en modul från PSGallery till din lokala PSRepository, kan du använda cmdleten Save-Package.

- Ange namnet på paketet
- Ange ”NuGet-providern
- Ange PSGallery platsen som källa (https://www.powershellgallery.com/api/v2)
- Ange sökvägen till din lokala lagringsplats

Exempel:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Om din lokala PSRepository är webbaserade, krävs ytterligare ett steg där nuget.exe används för att publicera.

Finns i dokumentationen för att använda [nuget.exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>Installera PowerShellGet på en frånkopplad system

Distribuera PowerShellGet är svårt i miljöer som kräver att vara ansluten till internet. PowerShellGet har en bootstrap process som installerar den senaste versionen första gången den används. Modulen OfflinePowerShellGetDeploy i PowerShell-galleriet innehåller cmdletar som stöder bootstrap processen.

För att kunna starta en offline-distribution, måste du:

- Hämta och installera OfflinePowerShellGetDeploy din internet-anslutna system och dina frånkopplade system
- Hämta PowerShellGet och dess beroenden på internet-anslutna system med den `Save-PowerShellGetForOffline` cmdlet
- Kopiera PowerShellGet och dess beroenden från internet-anslutna systemet till det frånkopplade systemet
- Använd den `Install-PowerShellGetOffline` på det frånkopplade systemet placera PowerShellGet och dess beroenden i rätt mappar

Följande kommandon används `Save-PowerShellGetForOffline` att placera alla komponenter i en mapp `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Nu måste du se innehållet i `F:\OfflinePowerShellGet` tillgänglig för dina frånkopplade system. Kör den `Install-PowerShellGetOffline` cmdlet för att installera PowerShellGet på det frånkopplade systemet.

> [!NOTE]
> Det är viktigt att du inte kör PowerShellGet i PowerShell-sessionen innan du kör dessa kommandon. När PowerShellGet har lästs in i sessionen, kan inte komponenterna uppdateras. Om du ska börja PowerShellGet av misstag, avsluta och starta om PowerShell.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

När du har kört dessa kommandon är du redo att publicera PowerShellGet till din lokala lagringsplats.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> För att garantera säkerheten, får API-nycklar inte vara hårdkodade i skript. Använd en säker nyckelhanteringssystem.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
