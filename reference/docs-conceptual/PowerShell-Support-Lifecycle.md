---
title: Supportlängd för PowerShell Core
description: Policyer som reglerar stöd för PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: b8dd4891ecf245b87c3fe2fa61cd241a12209b57
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854379"
---
# <a name="powershell-core-support-lifecycle"></a>Supportlängd för PowerShell Core

PowerShell Core är en specifik uppsättning verktyg och komponenter som har levererats, installeras och konfigureras separat från Windows PowerShell.
PowerShell Core är därför inte ingår i Licensavtal för Windows 7/8.1/10 eller Windows Server.

PowerShell Core stöds dock under traditionella Microsoft support-avtal, inklusive [Premier][], [Microsoft Enterprise-avtal][enterprise-agreement], och [Microsoft Software Assurance][assurance].
Du kan också betala för [assisterad support för][] för PowerShell Core genom att skicka in en begäran om ditt problem.

## <a name="community-support"></a>Community-Support

Vi erbjuder också [Community-support][] på GitHub där du kan lagra ett problem, buggar eller funktionsförfrågan.
Dessutom kan du hitta hjälp från andra medlemmar i communityn på allmänna [Microsoft Community][] eller Microsoft [PowerShell-Tech-Community][].
Vi erbjuder ingen garanti det att communityn ska åtgärda eller lösa problemet i tid.
Om du har ett problem som kräver omedelbar åtgärd, bör du använda den traditionella avgiftsbelagda supportalternativ.

## <a name="lifecycle-of-powershell-core"></a>Livscykeln för PowerShell Core

PowerShell Core inför den [Microsoft moderna livscykelpolicy][modern].
Den här supportlängd är avsedd att hålla kunder uppdaterade med de senaste versionerna.

Den version 6.x-grenen av PowerShell Core kommer att uppdateras ungefär en gång var sjätte månad (exempel: 6.0, 6.1, 6.2, osv.)

> [!IMPORTANT]
> Du måste uppdatera inom sex månader efter varje ny delversion viktig för att fortsätta att få support.

Till exempel om PowerShell Core 6.1 släpps den 1 juli 2018 är du förväntat att uppdatera till PowerShell Core 6.1 med 1 januari 2019 att underhålla support.

> [!IMPORTANT]
> Du måste uppdatera inom 30 dagar efter varje ny Uppdateringsversion viktig för att fortsätta att få support.

Till exempel om du kör PowerShell Core 6.1 och 6.1.3 gavs ut den 19 februari 2019 är du förväntat att uppdatera till PowerShell Core 6.1.3 genom den 21 mars 2019 som är 30 dagar efter att upprätthålla support.
Om det finns några korrigeringar krävs släpps om korrigeringarna i vårt nästa kumulativ uppdatering.

Moderna livscykelpolicy kräver också att Microsoft ge kunderna 12 månader meddelande innan avslutade stöd för en produkt (det vill säga PowerShell Core).

Så småningom vi förväntar oss PowerShell Core antar att ”långsiktig Service” metod.
I den här serviceplanen metoden skulle vi kräver bara Underhåll uppdateringar och säkerhetsuppdateringar vara i stöd på en viss gren/version av 6.x.

## <a name="supported-platforms"></a>Plattformar som stöds

Följande tabell för att se vilken version av PowerShell Core som du använder för vilken plattform stöds officiellt.

Paket för vissa plattformar också har bidragit med vår community, men de officiellt stöds inte.
Dessa paket är märkta `Community` i tabellen.

Plattformar som anges som `Experimental` inte stöds officiellt, men är tillgängliga för experimentering och feedback.

|                                                   | 6.1         | 6.2         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 och 10                            | Stöds   | Stöds   |
| Windows Server 2008 R2, 2012 R2, 2016             | Stöds   | Stöds   |
| [Windows Server Halvårskanal][semi-annual] | Stöds   | Stöds   |
| Ubuntu 16.04 och 18.04                            | Stöds   | Stöds   |
| Ubuntu 18.10 (via Fäst paket)                   | Community   | Community   |
| Debian 9                                          | Stöds   | Stöds   |
| CentOS 7                                          | Stöds   | Stöds   |
| Red Hat Enterprise Linux 7                        | Stöds   | Stöds   |
| openSUSE 42.3                                     | Stöds   | Stöds   |
| Fedora 28                                         | Stöds   | Stöds   |
| macOS 10.12+                                      | Stöds   | Stöds   |
| Arch                                              | Community   | Community   |
| Raspbian                                          | Community   | Community   |
| Kali                                              | Community   | Community   |
| AppImage (fungerar på flera Linux-plattformar)     | Community   | Community   |
| [Fäst paket](https://snapcraft.io/powershell)   | Se kommentar    | Se kommentar    |

> [!NOTE]
> Fäst paket som stöds samma som distributionsplatsen du använder paketet på.

## <a name="powershell-release-end-of-life"></a>PowerShell version slutet på sin livscykel

Baserat på [livscykel PowerShell Core](#lifecycle-of-powershell-core), i följande tabell visas de datum när olika versionen inte längre att stödjas.

| Version | Livscykelns slut                   |
|---------|-------------------------------|
| 6.0     | Den 13 februari 2019             |
| 6.1     | 28 september 2019            |
| 6.2     | 6 månader efter 7 versioner     |

## <a name="platforms-which-are-out-of-support"></a>Plattformar som inte längre stöds

När en plattformsversion når slutet på sin livscykel som definieras av plattform ägaren, upphör också PowerShell Core som stöd för den plattform-versionen.
Tidigare uppdateringar paket förblir tillgängliga för kunder som behöver åtkomst utan formella support och kommer inte längre att förses uppdateringar av något slag.

Därför distribution ägare avslutades stöd för följande versioner och stöds inte.

| Operativsystem       | Version | Livscykelns slut                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [Augusti 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [December 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Maj 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| openSUSE | 42.1    | [Maj 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| openSUSE | 42.2    | [Januari 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16.10   | [Juli 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17.04   | [Januari 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [Juli 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| Debian   | 8       | [Juni 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [November 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14.04   | [April 2019](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>Anmärkningar om licensiering

PowerShell Core är tillgängliga under den [MIT-licens][].
Under denna licens, och utan en betald support-avtal, användare är begränsade till [Community-support][].
Med community-support kan Microsoft inte garantera svarstider eller korrigeringar.

## <a name="windows-powershell-module"></a>Windows PowerShell-modulen

Stöd för PowerShell Core omfattar inte produkten moduler, såvida inte dessa moduler uttryckligen stöd för PowerShell Core.
Till exempel med hjälp av den `ActiveDirectory` -modulen som levereras som en del av Windows Server är ett scenario som inte stöds.

Moduler som inte uttryckligen har stöd för PowerShell Core kan dock vara kompatibla i vissa fall.
Genom att installera den [ `WindowsPSModulePath` ][] modulen, du kan lägga till Windows PowerShell `PSModulePath` till PowerShell Core `PSModulePath`.

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

## <a name="experimental-features"></a>Experimentella funktioner

[Experimentella funktioner][] är begränsade till [communitysupport](#community-support).

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
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Experimentella funktioner]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
