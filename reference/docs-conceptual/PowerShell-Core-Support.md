---
title: Supportlängd för PowerShell Core
description: Policyer som reglerar stöd för PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 2e0ca1b9c133e6f316a40aff13365d0489059165
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587167"
---
# <a name="powershell-core-support-lifecycle"></a>Supportlängd för PowerShell Core

PowerShell Core är en specifik uppsättning verktyg och komponenter som har levererats, installeras och konfigureras separat från Windows PowerShell.
PowerShell Core är därför inte ingår i Licensavtal för Windows 7/8.1/10 eller Windows Server.

PowerShell Core stöds dock under traditionella Microsoft support-avtal, inklusive [Premier][], [Microsoft Enterprise-avtal][enterprise-agreement], och [Microsoft Software Assurance][assurance].
Du kan också betala för [assisterad support för][] för PowerShell Core genom att skicka in en begäran om ditt problem.

Vi erbjuder också [Community-support][] på GitHub där du kan lagra ett problem, buggar eller funktionsförfrågan.
Alternativt kan du hitta hjälp från andra medlemmar i communityn på allmänna [Microsoft Community][] eller Microsoft [PowerShell-Tech-Community][].
Vi erbjuder ingen garanti det att problemet ska åtgärdas eller löst i tid.
Om du har ett problem som kräver omedelbar åtgärd, bör du använda den traditionella avgiftsbelagda supportalternativ.

## <a name="lifecycle-of-powershell-core"></a>Livscykeln för PowerShell Core

PowerShell Core inför den [Microsoft moderna livscykelpolicy][modern].
Den här supportlängd är avsedd att hålla kunder uppdaterade med de senaste versionerna.

Den version 6.x-grenen av PowerShell Core kommer att uppdateras ungefär en gång var sjätte månad (t.ex. 6.0, 6.1, 6.2, osv.)

> [!IMPORTANT]
> Du måste uppdatera inom sex månader efter varje ny delversion viktig för att fortsätta att få support.

Till exempel om PowerShell Core 6.1 släpps den 1 juli 2018 börjar är du förväntat att uppdatera till PowerShell Core 6.1 med den 1 januari 2019 att underhålla support.

![PowerShell Core gren livscykel][lifecycle-chart]

Moderna livscykelpolicy kräver också att Microsoft ge kunderna 12 månader meddelande innan avslutade stöd för en produkt (d.v.s. PowerShell Core).

Så småningom vi förväntar oss PowerShell Core antar att ”långsiktig Service” metod där vi kräver bara underhåll och säkerhet som uppdaterar vara i stöd på en viss gren/version av 6.x.

## <a name="supported-platforms"></a>Plattformar som stöds

Se följande tabell för att se vilken plattform som versionen av PowerShell Core som du använder stöds officiellt.

Paket för vissa plattformar också har bidragit med vår community, men de officiellt stöds inte.
Dessa paket är märkta `Community` i tabellen.

Plattformar som anges som `Experimental` inte stöds officiellt, men är tillgängliga för experimentering och feedback.

|                                                   | 6.0         | 6.1         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 och 10                            | Stöds   | Stöds   |
| Windows Server 2008 R2, 2012 R2, 2016             | Stöds   | Stöds   |
| [Windows Server Halvårskanal][semi-annual] | Stöds   | Stöds   |
| Ubuntu 14.04 och 16.04                           | Stöds   | Stöds   |
| Ubuntu 18.04                                      |             | Stöds   |
| Ubuntu 18.10 (via Fäst paket)                   |             | Community   |
| Debian 8.7 + och 9                                | Stöds   | Stöds   |
| CentOS 7                                          | Stöds   | Stöds   |
| Red Hat Enterprise Linux 7                        | Stöds   | Stöds   |
| OpenSUSE 42.3                                     | Stöds   | Stöds   |
| Fedora 27                                         | Stöds   | Stöds   |
| Fedora 28                                         |             | Stöds   |
| macOS 10.12 +                                      | Stöds   | Stöds   |
| Arch                                              | Community   | Community   |
| Raspbian                                          | Experimentella| Community   |
| Kali                                              | Community   | Community   |
| AppImage (fungerar på flera Linux-plattformar)     | Community   | Community   |
| [Fäst paket](https://snapcraft.io/powershell)   | Se kommentar    | Se kommentar    |

> [!NOTE]
> Fäst paket kommer att experimentella under en period.  När du har är vi övertygade om att snapin inte innehåller några nya supportfrågor, support följer du kör paketet på distributionsplatsen.

## <a name="platform-which-are-out-of-support"></a>Plattformen som inte längre stöds

När en plattformsversion når slutet på sin livscykel som definieras av plattform ägaren, PowerShell Core också att upphöra att ge stöd för den plattform-versionen. Tidigare uppdateringar paket förblir tillgängliga för kunder som behöver åtkomst utan formella support och kommer inte längre att förses uppdateringar av något slag.

Därför stöd för följande versioner av ägare för distribution och stöds inte.

| Operativsystem       | Version | Livscykelns slut                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [Augusti 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [December 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Maj 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| OpenSUSE | 42.1    | [Maj 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| OpenSUSE | 42.2    | [Januari 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16,10   | [Juli 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | nr 17.04 från   | [Januari 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [Juli 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |

## <a name="notes-on-licensing"></a>Anmärkningar om licensiering

PowerShell Core är tillgängliga under den [MIT-licens][].
Under denna licens, och det inte finns i en betald support-avtal, användare är begränsade till [Community-support][].
Med community-support kan Microsoft inte garantera svarstider eller korrigeringar.

## <a name="windows-powershell-module"></a>Windows PowerShell-modulen

Stöd för PowerShell Core förlängs inte till andra produkt-moduler om du inte uttryckligen PowerShell Core stöd för dessa moduler.
Till exempel med hjälp av den `ActiveDirectory` -modulen som levereras som en del av Windows Server är ett scenario som inte stöds.

Moduler som inte uttryckligen har stöd för PowerShell Core kan dock vara kompatibla i vissa fall.
Genom att installera den [`WindowsPSModulePath`][] modulen, kan du lägga till Windows PowerShell `PSModulePath` till PowerShell Core `PSModulePath`.

Installera först den `WindowsPSModulePath` modul från PowerShell-galleriet:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

När du har installerat den här modulen, kör den `Add-WindowsPSModulePath` cmdlet för att lägga till Windows PowerShell `PSModulePath` till PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Community-support]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell-Tech-Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[assisterad support för]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT-licens]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
['WindowsPSModulePath']: https://www.powershellgallery.com/packages/WindowsPSModulePath/
