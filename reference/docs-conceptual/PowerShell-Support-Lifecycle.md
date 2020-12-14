---
title: Supportlängd för PowerShell Core
description: Information om principerna som styr support för PowerShell
ms.date: 11/11/2020
ms.openlocfilehash: f2a1df0fabdfb624db666d240172930dc60f1bfe
ms.sourcegitcommit: 2fc6ee49a70bda4c59135136bd5cc7782836a124
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94810393"
---
# <a name="powershell-support-lifecycle"></a>Support livs cykel för PowerShell

PowerShell är en distinkt uppsättning verktyg och komponenter som levereras, installeras och konfigureras separat från Windows PowerShell. PowerShell ingår inte i licens avtalen för Windows.

PowerShell stöds i traditionella Microsofts support avtal, inklusive [avgiftsbelagd support][], [Microsoft Enterprise Agreement][enterprise-agreement]och [Microsoft Software Assurance][assurance]. Du kan också betala för [assisterad support][] för PowerShell genom att skicka en support förfrågan om ditt problem.

## <a name="community-support"></a>Community-support

Vi erbjuder också [Community-support][] på GitHub där du kan skicka ett problem, en bugg eller en funktions förfrågan.
Du kan också få hjälp från andra medlemmar i communityn i Microsoft PowerShell- [Tech-communityn][] eller något av de forum som anges i avsnittet Community på sidan [PowerShell][pshub] -hubb. Vi erbjuder ingen garanti där communityn kommer att åtgärda problemet inom rimlig tid. Om du har ett problem som kräver omedelbar uppmärksamhet bör du använda de traditionella, avgiftsbelagda support alternativen.

## <a name="lifecycle-of-powershell-7"></a>Livs cykel för PowerShell 7

I och med lanseringen av PowerShell 7 fortsätter PowerShell att stödjas enligt [Microsofts moderna livs cykel policy][modern], men support datum är länkade till [support livs cykeln för .net Core][Long-Term]. I den här underhålls metoden kan kunder välja långsiktiga support-versioner (LTS) eller aktuella versioner. PowerShell 7,0 är en LTS-version. Support upphör med supporten för .NET Core 3,1. Nästa LTS-utgåva följer nästa .NET Core LTS-version. Mer information finns i [PowerShell-versionerna av uttjänta-tabellen](#powershell-releases-end-of-life) för aktuella slut support datum. LTS versions uppdateringar innehåller bara kritiska säkerhets-och underhålls uppdateringar och korrigeringar som är utformade för att undvika eller minimera påverkan på befintliga arbets belastningar.

En aktuell version är en version som sker mellan LTS-versioner. Aktuella versioner kan innehålla viktiga korrigeringar, innovationer och nya funktioner. En aktuell version stöds i tre månader efter nästa aktuella eller LTS version.

> [!IMPORTANT]
> Du måste ha den senaste korrigerings uppdateringen installerad för att kunna användas. Om du till exempel kör PowerShell 7,0 och 7.0.1 har släppts, måste du uppdatera till 7.0.1 för att få support.

## <a name="supported-platforms"></a>Plattformar som stöds

För att bekräfta om din plattform och version av PowerShell Core stöds officiellt, se följande tabell.

Vår community har också bidragit med paket för vissa plattformar, men de stöds inte officiellt. Dessa paket är markerade som `Community` i tabellen.

Plattformar som anges som `Experimental` inte stöds officiellt, men som är tillgängliga för experimentering och feedback.

<!-- TODO: update OS list -->

|                     Plattform                      |      7.0      |      7.1      |
| ------------------------------------------------- | :-----------: | :-----------: |
| Windows 8,1 och 10                               |   Stöds   |   Stöds   |
| Windows Server 2012 R2, 2016, 2019                |   Stöds   |   Stöds   |
| [Windows Server Semi-Annual-kanal][semi-annual] |   Stöds   |   Stöds   |
| Ubuntu 16,04, 18,04                               |   Stöds   |   Stöds   |
| Ubuntu 20.04                                      | Stöds inte |   Stöds   |
| Ubuntu 19,10, 20,10 (via Snap-paket)            |   Community   |   Stöds   |
| Debian 9                                          |   Stöds   |   Stöds   |
| Debian 10                                         |   Stöds   |   Stöds   |
| CentOS 7                                          |   Stöds   |   Stöds   |
| CentOS 8                                          |   Stöds   |   Stöds   |
| Red Hat Enterprise Linux 7                        |   Stöds   |   Stöds   |
| Red Hat Enterprise Linux 8                        |   Stöds   |   Stöds   |
| Fedora 31 +                                        |   Stöds   | Stöds inte |
| Alpina 3,10                                       |   Se anmärkning 1  | Stöds inte |
| Alpine 3.11 +                                      |   Se anmärkning 1  |   Se anmärkning 1  |
| macOS 10.13 +                                      |   Stöds   |   Stöds   |
| Båge                                              |   Community   |   Community   |
| Raspbian                                          |   Community   |   Community   |
| Kali                                              |   Community   |   Community   |
| AppImage (fungerar på flera Linux-plattformar)      |   Community   |   Community   |
| [Snapin-paket](https://snapcraft.io/powershell)   |   Se anmärkning 2  |   Se Obs!    |

> [!NOTE]
> - 1 – CIM, PowerShell-fjärrkommunikation och DSC stöds inte på Alpina.
> - 2-Snap-paket stöds på samma sätt som den distribution som du kör paketet på.

## <a name="powershell-releases-end-of-life"></a>Slut på livs längd för PowerShell-versioner

I följande tabell visas de datum då olika versioner inte längre stöds, baserat på [livs cykeln för PowerShell](#lifecycle-of-powershell-7).

| Version |          Livs längd           |
| :-----: | ------------------------------ |
|   7.1   | mitten – februari 2022 (projicerad) |
|   7.0   | 3 december 2022               |
|   6,2   | 4 september 2020              |
|   6.1   | 28 september 2019             |
|   6.0   | 13 februari 2019              |

> [!NOTE]
> Det här dokumentet är om stöd för PowerShell Core. Windows PowerShell (1,0-5,1) är en del av Windows OS. Komponenterna får samma stöd som den överordnade produkten eller plattformen. Mer information finns i [livs cykel information om produkt och tjänster](/lifecycle/products/).

## <a name="unsupported-platforms"></a>Plattformar som inte stöds

När en plattforms version når livs längd som definieras av plattforms ägaren, kommer PowerShell-kärnan också upphöra att stödja den plattforms versionen. Tidigare utgivna paket är fortfarande tillgängliga för kunder som behöver åtkomst men formell support och uppdateringar av någon typ kommer inte längre att tillhandahållas.

Distributions ägarna avslutade därför stödet för följande versioner och stöds inte.

<!-- TODO: Update this table Jason-->

|    Plattform    | Version |                                                         Uttjänta                                                          |
| -------------- | :-----: | ---------------------------------------------------------------------------------------------------------------------------- |
| Debian         |    8    | [Juni 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)                                            |
| Fedora         |   24    | [Augusti 2017](https://fedoramagazine.org/fedora-24-eol/)                                                                     |
| Fedora         |   25    | [December 2017](https://fedoramagazine.org/fedora-25-end-life/)                                                              |
| Fedora         |   26    | [Maj 2018](https://fedoramagazine.org/fedora-26-end-life/)                                                                   |
| Fedora         |   27    | [November 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                                                           |
| Fedora         |   28    | [Maj 2019](https://fedoramagazine.org/fedora-28-end-of-life/)                                                                |
| openSUSE       |  42,1   | [Maj 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)                                      |
| openSUSE       |  42,2   | [Januari 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html)                                  |
| openSUSE       |  42,3   | [Juli 2019](https://lists.opensuse.org/opensuse-security-announce/2019-07/msg00000.html)                                     |
| Ubuntu         |  14,04  | [April 2019](https://wiki.ubuntu.com/Releases)                                                                               |
| Ubuntu         |  16,10  | [Juli 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)                                         |
| Ubuntu         |  17,04  | [Januari 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)                                           |
| Ubuntu         |  17,10  | [Juli 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)                                         |
| Windows        |    7    | [Januari 2020](https://support.microsoft.com/help/4057281/windows-7-support-ended-on-january-14-2020)                        |
| Windows Server | 2008 R2 | [Januari 2020](https://support.microsoft.com/help/4456235/end-of-support-for-windows-server-2008-and-windows-server-2008-r2) |

## <a name="notes-on-licensing"></a>Anteckningar om licensiering

PowerShell-kärnan släpps under [MIT-licensen][]. Under den här licensen och utan ett betalt support avtal är användare begränsade till [Community-support][]. Med community-support ger Microsoft inga garantier för svars tider eller korrigeringar.

## <a name="windows-powershell-compatibility"></a>Windows PowerShell-kompatibilitet

Support livs cykeln för PowerShell behandlar inte moduler som levereras utanför paketet med PowerShell 7-versionen. Exempelvis `ActiveDirectory` stöds den modul som levereras som en del av Windows Server under [Windows Support Lifecycle][].

PowerShell 7 förbättrar kompatibiliteten med befintliga PowerShell-moduler skrivna för Windows PowerShell.
Mer information finns i den [about_Windows_Compatibility][] artikeln och i [listan över kompatibla moduler][].

> [!NOTE]
> [**WindowsPSModulePath**](https://www.powershellgallery.com/packages/WindowsPSModulePath) -modulen behövs inte längre i PowerShell 7 och stöds inte.

## <a name="experimental-features"></a>Experimentella funktioner

[Experimentella funktioner][] är begränsade till [Community-support](#community-support).

## <a name="security-servicing-criteria"></a>Villkor för säkerhets underhåll

PowerShell följer [villkoren för Microsoft Security Servicing för Windows][].
I tabellen nedan beskrivs de funktioner som uppfyller underhålls villkoren och de som inte gör det.

| Funktion                          | Typ             |
|----------------------------------|------------------|
| Körnings princip                 | Skydd i djupet |
| System låsning – med AppLocker | Skydd i djupet |
| System låsning – med WDAC      | Säkerhetsfunktion |

## <a name="release-history"></a>Versions historik

Följande tabell innehåller en tids linje för de större versionerna av PowerShell. Den här tabellen tillhandahålls för historisk referens. Den är inte avsedd att användas för att fastställa support livs cykeln.

|         Version          | Utgivningsdatum |                                                                     Anteckning                                                                      |
| ------------------------ | :----------: | --------------------------------------------------------------------------------------------------------------------------------------------- |
| PowerShell 7,1 (aktuell) |   Nov-2020   | Bygger på .NET Core 5,0 (aktuell)                                                                                                              |
| PowerShell 7,0 (LTS)     |   Mar – 2020   | Bygger på .NET Core 3,1 (LTS)                                                                                                                  |
| PowerShell 6,0           |   Jan-2018   | Första versionen bygger på .NET Core 2,1. Kan installeras på Windows, Linux och macOS.                                                              |
| PowerShell 5.1           |   Aug-2016   | Lanseras i uppdatering för Windows 10-årsdag och Windows Server 2016                                                                             |
| PowerShell 5.0           |   Feb-2016   | Lanserad i Windows Management Framework (WMF) 5,0                                                                                            |
| PowerShell 4.0           |   Okt-2013   | Integrerad i Windows 8,1 och Windows Server 2012 R2. Kan installeras på Windows 7 SP1, Windows Server 2008 R2 SP1 och Windows Server 2012. |
| PowerShell 3.0           |   Okt-2012   | Integrerad i Windows 8 och Windows Server 2012. Kan installeras på Windows 7 SP1, Windows Server 2008 SP1 och Windows Server 2008 R2 SP1.  |
| PowerShell 2,0           |   Jul – 2009   | Integrerad i Windows 7 och Windows Server 2008 R2. Kan installeras på Windows XP SP3, Windows Server 2003 SP2 och Windows Vista SP1.            |
| PowerShell 1,0           |   Nov-2006   | Kan installeras på Windows XP SP2, Windows Server 2003 SP1 och Windows Vista. Valfri komponent i Windows Server 2008.                          |

<!-- hyperlink references -->
[avgiftsbelagd support]: https://support.microsoft.com/hub/4343728/support-for-business
[enterprise-agreement]: https://www.microsoft.com/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx
[Community-support]: /powershell/scripting/community/community-support
[pshub]: /powershell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[assisterad support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[Long-Term]: https://dotnet.microsoft.com/platform/support/policy/dotnet-core
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: /windows-server/get-started/semi-annual-channel-overview
[MIT-licens]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[about_Windows_Compatibility]: /powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility
[Support livs cykel för Windows]: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet
[kompatibilitetslista för modul]: /powershell/scripting/whats-new/module-compatibility
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Experimentella funktioner]: /powershell/module/microsoft.powershell.core/about/about_powershell_config#experimentalfeatures
[Microsoft Security Servicing-kriterier för Windows]: https://www.microsoft.com/msrc/windows-security-servicing-criteria
