---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: Skapa och publicera en artikel
ms.openlocfilehash: 1640d35d684bbb399336eecef529e6efd8075da3
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2018
---
# <a name="creating-and-publishing-an-item"></a>Skapa och publicera en artikel

PowerShell-galleriet är plats att publicera och dela stabil PowerShell-moduler, skript och DSC-resurser med bredare PowerShell-användargruppen.

Den här artikeln täcker säkerhetsnivån och viktiga steg för att förbereda ett skript eller en modul och publicera den i PowerShell-galleriet.
Vi rekommenderar starkt att du läser den [publiceringsriktlinjer](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) att förstå hur du se till att de objekt som du publicerar mer ingående kommer att accepteras av PowerShell-galleriet användare.

Kraven för att publicera objekt på PowerShell-galleriet är:

- Har ett PowerShell-galleriet och API-nyckeln som associeras med den
- Kontrollera krävs Metadata är i objektet
- Använda före verifieringen verktyg för att se till att objektet är redo att publicera
- Publicera objektet till PowerShell-galleriet kommandona publicera modul och publicera-skript
- Svarar på frågor om objektet

PowerShell-galleriet accepterar PowerShell-moduler och PowerShell-skript.
När vi refererar till skript menar vi ett PowerShell-skript som är en enda fil och inte en del av en större modul.

## <a name="powershell-gallery-account-and-api-key"></a>PowerShell-galleriet konto och API-nyckel

Se [skapar ett PowerShell-galleriet konto](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_creating_an_account) för hur du konfigurerar kontot för PowerShell-galleriet.

När du har skapat ett konto kan hämta du API-nyckeln som behövs för att publicera objekt.
När du har loggat in med kontot visas ditt användarnamn längst upp i PowerShell-galleriet sidor i stället för att registrera.
Klicka på ditt användarnamn tar dig vidare till sidan mitt konto där du hittar API-nyckeln.

Obs: API-nyckeln måste behandlas så säkert som ditt inloggningsnamn och lösenord.
Med den här nyckeln kan du eller någon annan, uppdatera ett objekt som du äger i PowerShell-galleriet.
Vi rekommenderar att uppdatera nyckeln regelbundet, vilket kan göras med återställning av nyckel på sidan mitt konto.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>Nödvändiga Metadata för objekt som publicerats i PowerShell-galleriet

PowerShell-galleriet ger information till galleriet användare från metadatafält som ingår i manifestet skript eller modul.
Skapa eller ändra artiklar för publikationen till PowerShell-galleriet har en liten uppsättning krav för uppgifterna i manifestet för objektet.
Vi rekommenderar starkt att du läser avsnittet objektmetadata i den [publiceringsriktlinjer](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) information om hur du ger den bästa informationen till användare med objekten.

Den [ny ModuleManifest](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/ModuleManifest-Reference) och [ny ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_new-scriptfileinfo) cmdlets skapar mallen manifestet, med platshållare för alla manifest element.

Båda manifesten har två delar som är viktiga för att publicera, primära nyckel Data och PSData PrivateData primära viktiga data i ett PowerShell-modulmanifest är allt utanför avsnittet PrivateData.
Uppsättningen med primärnycklar är kopplade till versionen av PowerShell används och odefinierad stöds inte.
PrivateData har stöd för att lägga till nya nycklar så att element som är specifika för PowerShell-galleriet finns i PSData.


Manifestet element som är viktigast för att fylla i för objektet som du publicerar till PowerShell-galleriet är:

- Skript eller Modulnamn - de ritas från namnen på den. Ps1 för ett skript eller. PSD1 för en modul.
- Version - detta är en obligatorisk primärnyckel, format bör följa SemVer riktlinjer (Se metodtips för information)
- Skapad – detta är en obligatorisk primärnyckel och innehåller namnet som ska associeras med objektet (se författare och ägare, nedan)
- Beskrivning – det här är en obligatorisk primärnyckel används för att kortfattat förklara vad det här objektet har och eventuella krav för att använda den
- ProjectURI - detta är ett rekommenderas starkt URI i PSData som innehåller en länk till en Github-repo eller liknande plats där du kan göra utvecklingen i objektet

Författare och ägare av PowerShell-galleriet objekt är relaterade begrepp, men matchar inte alltid.
Objektet ägare är användare med PowerShell-galleriet konton som har behörighet att underhålla objektet. Det kan finnas flera ägare som kan uppdatera alla objekt.
Ägaren är endast tillgänglig från PowerShell-galleriet och förloras om objektet kopieras från ett system till ett annat.
Författare är en sträng som är inbyggd i manifestet data, så att det alltid är en del av objektet.
Rekommendationer för objekt från Microsoft-produkter är:

- Har flera ägare, med minst en är namnet på det team som producerar objektet;
- Ha författaren vara ett välkänt Teamnamn (till exempel Azure SDK Team) eller Microsoft Corporation.


## <a name="pre-validate-your-item"></a>Före Validera objektet

Det finns några verktyg som du behöver köra mot din kod innan du publicerar objektet till PowerShell-galleriet:

- [PowerShell-skriptet Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), vilket är i PowerShell-galleriet
- För moduler, Test-ModuleManifest som är en del av PowerShell
- För Test-ScriptFileInfo som medföljer PowerShell Get-skript

[PowerShell-skriptet Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) är ett analysverktyg för statisk kod som genomsöker din kod för att säkerställa att den uppfyller grundläggande PowerShell riktlinjer. Det här verktyget identifierar vanliga och viktiga problem i koden och bör köras regelbundet under utveckling för att få ditt objekt som är redo att publicera.
PowerShell-skriptet Analyzer ger lista över problem som identifieras som fel, varning och Information.
Alla fel måste åtgärdas innan du publicerar till PowerShell-galleriet. Varningar måste granskas och de flesta bör åtgärdas.
PowerShell-skriptet Analyzer körs varje gång ett objekt som är publicerade eller uppdateras i PowerShell-galleriet.
Galleriet Operations-teamet kommer att kontakta objektet ägare adress fel som påträffas.

Om manifestet informationen i objektet inte kan läsas av PowerShell-galleriet infrastruktur, kan du inte publicera.
[Testa ModuleManifest](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-modulemanifest) kommer att fånga upp vanliga problem som kan orsaka att modulen kan inte användas när den är installerad. Det måste köras för varje modul innan du publicerar till PowerShell-galleriet.

På samma sätt [Test ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_test-scriptfileinfo) validerar metadata i ett skript och måste köras på alla skript (publicerade separat från en modul) innan du publicerar till Powershell-galleriet.


## <a name="publishing-items"></a>Publicera objekt

Du måste använda den [publicera skript](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_publish-script) eller [publicera-modulen](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/psget_publish-module) att publicera objekt till PowerShell-galleriet.
Dessa kommandon som kräver båda

- Sökvägen till objektet som du vill publicera. Använd mappen för din modulen för en modul. Om du anger en mapp som innehåller flera versioner av samma modul, måste du ange RequiredVersion.
- En Nuget API-nyckel. Detta är API-nyckeln finns på sidan mitt konto på PowerShell-galleriet.

De flesta alternativen på kommandoraden ska vara i manifestet data för objektet som du publicerar, så du inte bör behöver ange dem i kommandot.

För att undvika fel bör du försöka kommandona med - Whatif-Verbose, innan du publicerar.
Detta sparar mycket tid eftersom varje gång du publicerar till PowerShell-galleriet, måste du uppdatera versionsnumret i manifestavsnittet av artikeln.

Exempel är: ' publicera modul-sökväg ”. \MyModule” - RequiredVersion ”0.0.1” - NugetAPIKey ”GUID” - Whatif-utförlig ' ' publicera skript-sökvägen ”.\MyScriptFile.PS1” - NugetAPIKey ”GUID” - Whatif-utförlig '

Granska utdata noggrant och upprepa kommandot utan - Whatif om inga fel eller varningar visas.

Alla objekt som publiceras till PowerShell-galleriet genomsöks efter virus och ska analyseras med hjälp av PowerShell-skript Analyzer.
Eventuella problem som uppstår vid den tiden skickas tillbaka till utgivaren för matchning.

När du har publicerat ett objekt i PowerShell-galleriet, behöver du titta på för feedback på objektet.

- Se till att du övervaka den e-postadress som är associerat med kontot som används för att publicera.
Användare och team PowerShell-galleriet-åtgärder ger feedback via det kontot, inklusive problem från PSSA eller virusgenomsökning.
Om e-postadressen är ogiltig, eller om allvarliga problem rapporteras till kontot och vänster olöst under lång tid objekt kan ses avbrutna och tas bort från PowerShell-galleriet som beskrivs i vår [användningsvillkoren](https://www.powershellgallery.com/policies/Terms).
- Vi rekommenderar att du prenumererar på kommentarer för varje objekt för PowerShell-galleriet som du publicerar.
På så sätt kan du få en avisering om alla kommentarer på objekten i PowerShell-galleriet.
Det här är valfritt, eftersom den kräver att skapa ett konto med LiveFyre.