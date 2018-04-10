# <a name="powershell-core-support-lifecycle"></a>Supportlängd för PowerShell Core

PowerShell Core är en specifik uppsättning verktyg och komponenter som har levererats, installeras och konfigureras separat från Windows PowerShell.
Därför ingår PowerShell Core inte i Licensavtal för Windows 7/8.1/10 eller Windows Server.

PowerShell Core stöds dock under traditionell Microsoft support-avtalet, inklusive [Premier][], [Microsoft Enterprise-avtal][enterprise-agreement], och [Microsoft Software Assurance][assurance].
Du kan också betala för [stödd stöd][] för PowerShell Core arkivera en supportförfrågan för ditt problem.

Vi erbjuder även [communitysupport][] på GitHub där du kan lagra ett problem, fel eller funktionsbegäran.
Alternativt kan du hitta hjälp från andra medlemmar i gruppen på allmänna [Microsoft Community][] eller Microsoft [PowerShell teknisk Community][].
Vi erbjuder ingen garanti det att problemet ska åtgärdas eller matchas i rimlig tid.
Om du har problem som kräver omedelbara åtgärder, bör du använda den traditionella betald supportalternativ.

## <a name="lifecycle-of-powershell-core"></a>Livscykeln för PowerShell Core

PowerShell Core inför den [Microsoft moderna livscykel princip][modern].
Den här livscykeln för support är avsedd att hålla kunder uppdaterad med de senaste versionerna.

Version 6.x grenen av PowerShell Core uppdateras ungefär en gång var sjätte månad (t.ex. 6.0, 6.1, 6.2, etc.)

> [!IMPORTANT]
> Du måste uppdatera i sex månader efter varje ny delversion släpper för att fortsätta att få support.

Till exempel om PowerShell Core 6.1 släpps på 1 juli 2018, är du förväntat att uppdatera till PowerShell Core 6.1 med 1 januari 2019 att underhålla support.

![PowerShell Core gren livscykel][lifecycle-chart]

Moderna livscykel principen kräver också att Microsoft ger kunder 12 månader meddelande innan avslutade stöd för en produkt (d.v.s. PowerShell Core).

Så småningom kommer vi räknar med PowerShell Core antar ”långsiktiga behandlingen” metod där vi kräver endast underhåll och säkerhet uppdateras för att hålla stöd på en viss gren/version av 6.x.

## <a name="supported-platforms"></a>Plattformar som stöds

PowerShell Core stöds officiellt på följande plattformar:

* Windows 7, 8.1 och 10
* Windows Server 2008 R2, 2012 R2, 2016
* [Windows Server semikolon mellan årligt kanal][semi-annual]
* Ubuntu 14.04 16.04 och nr 17.04 från
* Debian 8.7 + och 9
* CentOS 7
* Red Hat Enterprise Linux 7
* OpenSUSE 42.2
* Fedora 25, 26
* macOS 10.12+

Gruppen har också bidragit paket för följande plattformar, men de är inte officiellt stöds:

* Arkitektur Linux
* Kali Linux
* AppImage (fungerar på flera plattformar för Linux)

## <a name="notes-on-licensing"></a>Information om licensiering

PowerShell Core släpps den [MIT-licensen][].
Under denna licens och saknas en betald supportavtal användare är begränsade till [communitysupport][].
Microsoft ger inga garantier för tillgänglighet eller korrigeringar med community-support.

## <a name="windows-powershell-module"></a>Windows PowerShell-modulen

Stöd för PowerShell Core inte utökar till andra moduler för produkten om de modulerna som uttryckligen har stöd för PowerShell Core.
Till exempel med hjälp av den `ActiveDirectory` modulen som levereras som en del av Windows Server är ett scenario som inte stöds.

Moduler som inte uttryckligen har stöd för PowerShell Core kan dock vara kompatibla i vissa fall.
Genom att installera den [`WindowsPSModulePath`][] modulen, kan du lägga till Windows PowerShell `PSModulePath` till PowerShell-kärna `PSModulePath`.

Installera först den `WindowsPSModulePath` modul från PowerShell-galleriet:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

När du installerar den här modulen, kör du den `Add-WindowsPSModulePath` för att lägga till Windows PowerShell `PSModulePath` till PowerShell kärnor:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[communitysupport]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell teknisk Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[stödd stöd]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT-licensen]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/