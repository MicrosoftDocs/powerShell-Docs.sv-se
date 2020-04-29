---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Skapa och publicera ett objekt
ms.openlocfilehash: 1aa9cc84f259869ca6f8b8e2f6952e43eaac14df
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328786"
---
# <a name="creating-and-publishing-an-item"></a>Skapa och publicera ett objekt

PowerShell-galleriet är den plats där du kan publicera och dela stabila PowerShell-moduler, skript och önskade tillstånds konfigurations resurser (DSC) med den bredare PowerShell-användaren community.

Den här artikeln beskriver Mechanics och viktiga steg för att förbereda ett skript eller en modul och publicera den till PowerShell-galleriet. Vi rekommenderar starkt att du läser igenom [publicerings rikt linjerna](../../concepts/publishing-guidelines.md) för att förstå hur du ser till att de objekt som du publicerar blir mer spridda av PowerShell-galleriet användare.

Minimi kraven för att publicera ett objekt till PowerShell-galleriet är:

- Ha ett PowerShell-galleriet konto och den API-nyckel som är kopplad till den
- Se till att nödvändiga metadata finns i ditt objekt
- Använd för validerings verktygen för att se till att ditt objekt är klart att publicera
- Publicera objektet till PowerShell-galleriet med kommandona publicera-modul och publicera-skript
- Svara på frågor eller problem om ditt objekt

PowerShell-galleriet accepterar PowerShell-moduler och PowerShell-skript. När vi refererar till skript, innebär det ett PowerShell-skript som är en enskild fil och inte en del av en större modul.

## <a name="powershell-gallery-account-and-api-key"></a>PowerShell-galleriet konto och API-nyckel

Mer information om hur du konfigurerar ditt PowerShell-galleriet-konto finns i [skapa ett PowerShell-galleriet konto](creating-an-account.md) .

När du har skapat ett konto kan du hämta den API-nyckel som behövs för att publicera ett objekt. När du har loggat in med kontot visas ditt användar namn längst upp på PowerShell-galleriet sidor i stället för registrera. När du klickar på ditt användar namn tas du till sidan mitt konto där du hittar API-nyckeln.

> [!IMPORTANT]
> API-nyckeln måste behandlas på ett säkert sätt som inloggning och lösen ord. Med den här nyckeln kan du eller någon annan uppdatera alla objekt som du äger i PowerShell-galleriet. Vi rekommenderar att du uppdaterar nyckeln regelbundet, som kan göras med hjälp av återställnings nyckeln på sidan mitt konto.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>Obligatoriska metadata för objekt som publicerats i PowerShell-galleriet

PowerShell-galleriet innehåller information till Galleri användare som har ritats från metadatafält som ingår i skriptet eller modul manifestet. Att skapa eller ändra objekt för publicering till PowerShell-galleriet har en liten uppsättning krav för information som anges i objekt manifestet. Vi rekommenderar starkt att du läser avsnittet objektmetadata i [publicerings rikt linjerna](../../concepts/publishing-guidelines.md) för att lära dig hur du ger den bästa informationen till användarna med dina objekt.

Cmdletarna [New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest) och [New-ScriptFileInfo](/powershell/module/PowerShellGet/New-ScriptFileInfo) kommer att skapa manifest mal len åt dig, med plats hållare för alla manifest element.

Båda manifesten har två avsnitt som är viktiga för publicering, primär nyckel data och PSData-arean för PrivateData. Primär nyckel data i PowerShell-modulens manifest är allt utanför PrivateData-avsnittet. Uppsättningen med primära nycklar är kopplad till den version av PowerShell som används och odefinierad stöds inte. PrivateData har stöd för att lägga till nya nycklar, så de element som är aktuella för PowerShell-galleriet finns i PSData.

Manifest element som är viktigast att fylla i för objekt som du publicerar till PowerShell-galleriet är:

- Skript-eller Modulnamn – de hämtas från namnet på. PS1 för ett skript eller. PSD1 för en modul.
- Version – det här är en nödvändig primär nyckel. formatet bör följa rikt linjer för SemVer. Se metod tips för mer information.
- Author – det här är en primär nyckel som krävs och innehåller det namn som ska associeras med objektet. Se författare och ägare nedan.
- Beskrivning – Det här är en nödvändig primär nyckel som används för att kortfattat förklara vad det här objektet gör och eventuella krav för att använda det
- ProjectURI – det här är ett starkt rekommenderat URI-fält i PSData som innehåller en länk till en GitHub-lagrings platsen eller en liknande plats där du utvecklar objektet
- Taggar – det är en stark rekommendation att tagga ditt paket baserat på dess kompatibilitet med PSEditions och plattformar. Mer information finns i [publicerings rikt linjerna](../../concepts/publishing-guidelines.md#tag-your-package-with-the-compatible-pseditions-and-platforms).

Författare och ägare av PowerShell-galleriet objekt är relaterade begrepp, men matchar inte alltid. Objekt ägare är användare med PowerShell-galleriet konton som har behörighet att underhålla objektet. Det kan finnas många ägare som kan uppdatera alla objekt. Ägaren är bara tillgänglig från PowerShell-galleriet och går förlorad om objektet kopieras från ett system till ett annat. Author är en sträng som är inbyggd i manifest data, så den är alltid en del av objektet. Rekommendationerna för objekt från Microsoft-produkter är:

- Ha flera ägare, med minst ett som namn på teamet som skapar objektet
- Låt författaren vara ett välkänt team namn (t. ex. Azure SDK-team) eller Microsoft Corporation

## <a name="pre-validate-your-item"></a>Validera ditt objekt i förväg

Det finns några verktyg som du behöver köra mot din kod innan du publicerar ditt objekt till PowerShell-galleriet:

- [PowerShell-skript analys](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), som finns i PowerShell-galleriet
- För moduler, test-ModuleManifest som är en del av PowerShell
- För skript, test-ScriptFileInfo som medföljer PowerShell Hämta

[PowerShell script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) är ett statiskt kod analys verktyg som söker igenom koden för att säkerställa att den uppfyller Basics rikt linjer för PowerShell-kodning. Det här verktyget identifierar vanliga och kritiska problem i koden och bör köras regelbundet under utvecklingen för att hjälpa dig att få ditt objekt att publicera. PowerShell script Analyzer visar en lista över problem som identifieras som fel, varning och information. Alla fel måste åtgärdas innan du publicerar till PowerShell-galleriet. Varningar måste granskas och de flesta bör åtgärdas. PowerShell skript analys körs varje gång ett objekt publiceras eller uppdateras i PowerShell-galleriet. Galleri drifts teamet kontaktar objekt ägare för att åtgärda fel som hittas.

Om manifest informationen i objektet inte kan läsas av PowerShell-galleriet-infrastrukturen kommer du inte att kunna publicera. [Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest) kommer att fånga vanliga problem som kan leda till att modulen inte kan användas när den är installerad. Den måste köras för varje modul innan den kan publiceras på PowerShell-galleriet.

På samma sätt verifierar [test-ScriptFileInfo](/powershell/module/PowerShellGet/test-scriptfileinfo) metadata i ett skript och måste köras på alla skript (publicerade separat från en modul) innan de publiceras till PowerShell-galleriet.

## <a name="publishing-items"></a>Publicera objekt

Du måste använda [publicerings skriptet](/powershell/module/PowerShellGet/publish-script) eller [Publish-modulen](/powershell/module/PowerShellGet/publish-module) för att publicera objekt till PowerShell-galleriet. Dessa kommandon kräver båda:

- Sökvägen till det objekt som du vill publicera. För en modul använder du mappen med namnet för din modul. Om du anger en mapp som innehåller flera versioner av samma modul måste du ange RequiredVersion.
- En NuGet API-nyckel. Detta är API-nyckeln som finns på sidan mitt konto på PowerShell-galleriet.

De flesta andra alternativ på kommando raden ska finnas i manifest data för det objekt som du publicerar, så du behöver inte ange dem i kommandot.

För att undvika fel rekommenderar vi starkt att du provar kommandona med-WhatIf-verbose innan du publicerar. Detta sparar avsevärd tid, eftersom du varje gång du publicerar till PowerShell-galleriet måste uppdatera versions numret i manifest avsnittet av objektet.

Exempel:

* `Publish-Module -Path ".\MyModule" -NugetAPIKey "GUID" -WhatIf -Verbose`
* `Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -WhatIf -Verbose`

Granska utdata noggrant och om du inte ser några fel eller varningar upprepar du kommandot utan-WhatIf.

Alla objekt som publiceras till PowerShell-galleriet genomsöks efter virus och analyseras med hjälp av PowerShell-skript analys. Eventuella problem som uppstår vid denna tidpunkt skickas tillbaka till utgivaren för lösning.

När du har publicerat ett objekt till PowerShell-galleriet måste du titta efter feedback om ditt objekt.

- Se till att du övervakar den e-postadress som är kopplad till det konto som används för att publicera. Användare och PowerShell-galleriet drifts teamet ger feedback via kontot, inklusive problem från PSSA eller antivirus genomsökningar. Om e-postkontot är ogiltigt, eller om allvarliga problem rapporteras till kontot och lämnas olöst under en längre tid, kan objekt anses vara övergivna och tas bort från PowerShell-galleriet enligt beskrivningen i våra [användnings villkor](https://www.powershellgallery.com/policies/Terms).
- Vi rekommenderar att du prenumererar på kommentarer för varje PowerShell-galleriet objekt som du publicerar. På så sätt kan du få ett meddelande om alla kommentarer om dina objekt i PowerShell-galleriet. Detta är valfritt, eftersom det krävs att du skapar ett konto med LiveFyre.
