---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Skapa och publicera ett objekt
ms.openlocfilehash: 3875c7ae8231f254e655f149c788503cb0b3077c
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655437"
---
# <a name="creating-and-publishing-an-item"></a>Skapa och publicera ett objekt

PowerShell-galleriet är platsen att publicera och dela stabil PowerShell-moduler, skript och DSC-resurser med bredare PowerShell-användargruppen.

Den här artikeln beskriver mechanics och viktiga steg för att förbereda ett skript eller en modul och publicera dem på PowerShell-galleriet.
Vi rekommenderar starkt att du läser igenom den [publiceringsriktlinjer](/powershell/gallery/concepts/publishing-guidelines) vill lära dig att se till att de objekt som du publicerar mer allmänt kommer att accepteras av användarna i PowerShell-galleriet.

Kraven för att publicera ett objekt till PowerShell-galleriet är:

- Har ett PowerShell-galleriet och som är associerade med den API-nyckel
- Kontrollera krävs Metadata finns i objektet
- Använda före verifiering verktyg för att se till att objektet är redo att publicera
- Publicera objektet till PowerShell-galleriet med hjälp av kommandona Publish-Module och Publish-Script
- Besvarat frågor om dina objekt

PowerShell-galleriet accepterar PowerShell-moduler och PowerShell-skript.
När vi refererar till skript menar vi ett PowerShell-skript som är en enda fil och inte en del av en större modul.

## <a name="powershell-gallery-account-and-api-key"></a>PowerShell-galleriet konto och API-nyckel

Se [skapar ett konto för PowerShell-galleriet](/powershell/gallery/how-to/publishing-packages/creating-an-account) för hur du konfigurerar ditt konto med PowerShell-galleriet.

När du har skapat ett konto kan få du API-nyckel som behövs för att publicera ett objekt.
När du har loggat in med kontot visas ditt användarnamn högst upp på sidorna PowerShell-galleriet i stället för att registrera dig.
När du klickar på ditt användarnamn tar dig till sidan mitt konto där du hittar API-nyckeln.

Obs! API-nyckel behandlas så säkert som ditt inloggningsnamn och lösenord.
Med den här nyckeln kan du eller någon annan, uppdatera ett objekt som du äger i PowerShell-galleriet.
Vi rekommenderar att du uppdaterar nyckeln regelbundet, som kan göras med återställning av nyckel på sidan med mitt konto.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>Nödvändiga Metadata för objekt som publicerats i PowerShell-galleriet

PowerShell-galleriet innehåller information till galleriet användare från metadatafält som ingår i manifestet skript eller en modul.
Skapa eller ändra artiklar för publikationen till PowerShell-galleriet har en liten uppsättning krav för information som tillhandahålls i manifestet objekt.
Vi rekommenderar starkt att du läser igenom avsnittet objektmetadata i den [publiceringsriktlinjer](/powershell/gallery/concepts/publishing-guidelines) att lära dig hur du ger den bästa informationen till användare med objekten.

Den [New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest) och [New ScriptFileInfo](/powershell/module/PowerShellGet/New-ScriptFileInfo) cmdletar skapar mallen manifest åt dig, med platshållare för alla manifest element.

Både manifest har två avsnitt som är viktiga för publicering, området primära nyckel Data och PSData PrivateData primära viktiga data i ett PowerShell-modulmanifest allt utanför PrivateData-avsnittet.
Uppsättningen med primärnycklar är knutna till versionen av PowerShell används och odefinierad stöds inte.
PrivateData har stöd för att lägga till nya nycklar så att de som är specifika för PowerShell-galleriet finns i PSData.


Manifest element som är viktigast att fylla i för objektet som du publicerar till PowerShell-galleriet är:

- Skript eller Modulnamn – de som hämtas från namnen på den. Ps1 för ett skript eller. PSD1 för en modul.
- Version – det här är en obligatorisk primärnyckel, format bör följa SemVer riktlinjer. Mer information finns i metodtips.
- Författare – detta är en obligatorisk primärnyckel och innehåller namnet som ska associeras med objektet. Se författare och ägare nedan.
- Beskrivning – det här är en obligatorisk primär nyckel som används för att kortfattat beskriver vad som gör det här objektet och alla krav för att använda den
- ProjectURI – detta är ett rekommenderas starkt URI-fält i PSData som innehåller en länk till en Github-lagringsplats eller liknande plats där du utför utveckling på objektet
- -Taggar – det är en stark rekommendation att tagga ditt paket baserat på dess kompatibilitet med PSEditions och plattformar. Se [publiceringsriktlinjerna](/powershell/gallery/concepts/publishing-guidelines.md#tag-your-package-with-the-compatible-pseditions-and-platforms) mer information.

Författare och ägare av PowerShell-galleriet är relaterade begrepp, men matchar inte alltid.
Objektägare är användare med PowerShell-galleriet konton som har behörighet att behålla objektet. Det kan finnas många ägare som kan uppdatera ett objekt.
Ägaren är endast tillgänglig från PowerShell-galleriet och förloras om objektet kopieras från ett system till ett annat.
Författare är en sträng som är inbyggd i manifestet data, så att det alltid är en del av artikeln.
Rekommendationer för objekt från Microsoft-produkter är:

- Har flera ägare, med minst en som namnet på det team som skapar objektet;
- Ha en författare vara namnet på en välkänd grupp (till exempel Azure SDK-teamet) eller Microsoft Corporation.


## <a name="pre-validate-your-item"></a>Kontrollera din objekt

Det finns några verktyg som du behöver för att köra mot din kod innan du publicerar dina objekt i PowerShell-galleriet:

- [PowerShell-skript Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), vilket är i PowerShell-galleriet
- För Test-ModuleManifest som är en del av PowerShell-moduler
- För skript, Test-ScriptFileInfo som medföljer PowerShell hämta

[PowerShell-skript Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) är ett analysverktyg för statisk kod som söker igenom din kod för att kontrollera att den uppfyller grundläggande PowerShell riktlinjer för kod. Det här verktyget identifierar vanliga och viktiga problem i din kod som ska köras regelbundet under utvecklingen för att få dina objekt som är redo att publicera.
PowerShell-skript Analyzer ger lista över problem som identifieras som fel, varning och Information.
Alla fel måste åtgärdas innan du publicerar PowerShell-galleriet. Varningar som behöver granskas och de flesta bör åtgärdas.
PowerShell-skript Analyzer körs varje gång som ett objekt är publicerade eller uppdateras i PowerShell-galleriet.
Galleriet driftsteamet kommer att kontakta objektägare adress fel som påträffas.

Om manifestet informationen i dina objekt inte kan läsas av infrastrukturen som PowerShell-galleriet, kan du inte publicera.
[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest) ska fånga upp vanliga problem som skulle orsaka att modulen kan inte användas när den är installerad. Det måste köras för varje modul innan du publicerar den PowerShell-galleriet.

På samma sätt [Test ScriptFileInfo](/powershell/module/PowerShellGet/test-scriptfileinfo) validerar metadata i ett skript och måste köras på varje skript (publicerade separat från en modul) innan du publicerar den Powershell-galleriet.


## <a name="publishing-items"></a>Publicera objekt

Du måste använda den [Publish-Script](/powershell/module/PowerShellGet/publish-script) eller [Publish-Module](/powershell/module/PowerShellGet/publish-module) att publicera objekt till PowerShell-galleriet.
De här kommandona kräver båda

- Sökvägen till objektet som ska publiceras. Använd mappen med namnet för din modul för en modul. Om du anger en mapp som innehåller flera versioner av samma modul, måste du ange RequiredVersion.
- Ett Nuget-API-nyckel. Det här är API-nyckel som återfinns i mitt konto-sidan på PowerShell-galleriet.

De flesta av de andra alternativen i kommandoraden måste vara i manifestet data för det objekt som du publicerar, så du inte bör behöver ange dem i kommandot.

Om du vill undvika fel bör du försöka kommandon med hjälp av – Whatif-Verbose, innan du publicerar.
Detta sparar ganska lång tid sedan varje gång du publicerar till PowerShell-galleriet, måste du uppdatera versionsnumret i manifest-delen av artikeln.

Exempel är: ”Publicera-Module-sökvägen”. \MyModule ”- RequiredVersion” 0.0.1 ”- NugetAPIKey” GUID ”- Whatif-utförlig” ”publicera skript-sökvägen”.\MyScriptFile.PS1 ”- NugetAPIKey” GUID ”- Whatif-utförlig”

Granska utdata noggrant och om du ser några fel eller varningar, upprepa kommandot utan - Whatif.

Alla artiklar som publiceras till PowerShell-galleriet ska genomsökas efter virus och ska analyseras med hjälp av PowerShell-skript analysatorn.
Eventuella problem som uppstår vid den tiden skickas tillbaka till utgivaren för matchning.

När du har publicerat ett objekt i PowerShell-galleriet, måste du titta på för feedback för ditt objekt.

- Se till att du övervaka den e-postadress som är kopplade till kontot som används för att publicera.
Användare och PowerShell-galleriet driftsteamet ska tillhandahålla feedback via kontot, inklusive problem från PSSA eller virusgenomsökning.
Om e-postkontot är ogiltig, eller om allvarliga problem rapporteras till kontot och vänster olöst under en längre tid, objekt kan betraktas som övergivna och tas bort från PowerShell-galleriet enligt beskrivningen i vår [användningsvillkor](https://www.powershellgallery.com/policies/Terms).
- Vi rekommenderar att du prenumererar på kommentarer för varje objekt för PowerShell-galleriet som du publicerar.
På så sätt kan du få ett meddelande om vem som helst kommentarer på objekten i PowerShell-galleriet.
Detta är valfritt, eftersom det måste du skapa ett konto med LiveFyre.
