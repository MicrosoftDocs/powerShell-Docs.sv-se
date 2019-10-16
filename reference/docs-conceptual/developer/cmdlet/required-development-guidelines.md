---
title: Nödvändiga utvecklings rikt linjer | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: e68e43a91f9139e8d3dc636b5740121515aab2e6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359293"
---
# <a name="required-development-guidelines"></a>Obligatoriska riktlinjer för utveckling

Följande rikt linjer måste följas när du skriver dina cmdletar. De är indelade i rikt linjer för att utforma cmdlets och rikt linjer för att skriva din cmdlet-kod. Om du inte följer de här rikt linjerna kan dina cmdlets missin fungera och användarna kan ha en låg upplevelse när de använder dina cmdletar.

## <a name="in-this-topic"></a>I det här avsnittet

### <a name="design-guidelines"></a>Design rikt linjer

- [Använd endast godkända verb (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Cmdlet-namn: tecken som inte kan användas (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Parameter namn som inte kan användas (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Support bekräftelse förfrågningar (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Support Force-parameter för interaktiva sessioner (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Dokument utmatnings objekt (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Kod rikt linjer

- [Härled från cmdlet eller PSCmdlet-klasser (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Ange cmdlet-attributet (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Åsidosätt en metod för bearbetning av indata (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Ange attributet OutputType (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Behåll inte referenser till utgående objekt (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Hantera fel stabilt (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Använd en Windows PowerShell-modul för att distribuera dina cmdlets (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Design rikt linjer

Följande rikt linjer måste följas när du utformar cmdlets för att säkerställa en konsekvent användar upplevelse mellan att använda dina cmdletar och andra cmdletar. När du hittar en design rikt linje som gäller din situation bör du titta närmare på kod rikt linjerna för liknande rikt linjer.

### <a name="use-only-approved-verbs-rd01"></a>Använd endast godkända verb (RD01)

Verbet som anges i cmdlet-attributet måste komma från den identifierade uppsättningen verb som tillhandahålls av Windows PowerShell. Det får inte vara en av de förbjudna synonymerna. Använd de konstanta strängarna som definieras av följande uppräkningar för att ange cmdlet-verb:

- [System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Mer information om godkända verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).

Användare behöver en uppsättning som identifierar och förväntade cmdlet-namn. Använd lämpligt verb så att användaren kan göra en snabb bedömning av vad en cmdlet gör och för att enkelt identifiera funktionerna i systemet. Följande kommando rads kommando hämtar till exempel en lista över alla kommandon i systemet vars namn börjar med "Start": `get-command start-*`. Använd Substantiv i dina cmdlets för att skilja dina cmdletar från andra cmdletar. Substantivet anger den resurs som åtgärden ska utföras på. Själva åtgärden representeras av verbet.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Cmdlet-namn: tecken som inte kan användas (RD02)

Använd inte något av följande specialtecken när du namnger cmdletar.

|Jokerteck|Namn|
|---------------|----------|
|#|nummer tecken|
|,|Kommaseparerade|
|()|Parenteser|
|{}|klammerparenteser|
|[]|hakparenteser|
|&|Et|
|-|bindestrecks **anteckning:** bindestrecket kan användas för att avgränsa verbet från substantiv, men det kan inte användas i Substantiv eller i verbet.|
|/|Snedstreck|
|\\ | omvänt snedstreck|
|$|dollar tecken|
|^|tecken|
|;|Skilj|
|:|Kolon|
|"|dubbla citat tecken|
|'|enkelt citat tecken|
|<>|vinkelparenteser|
|&#124;|lodrätt streck|
|?|frågetecken|
|@|vid tecken|
|`|ryggs kal streck (grav accent)|
|*|läggs|
|%|procent tecken|
|+|Plus tecken|
|=|likhets tecken|
|~|Tecknen|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Parameter namn som inte kan användas (RD03)

Windows PowerShell tillhandahåller en gemensam uppsättning parametrar för alla cmdletar plus ytterligare parametrar som läggs till i vissa situationer. När du skapar egna cmdlet: ar kan du inte använda följande namn: Confirm, debug, ErrorAction, ErrorVariable, utbuffer, disvariable, WarningAction, WarningVariable, WhatIf, UseTransaction och verbose. Mer information om dessa parametrar finns i [vanliga parameter namn](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Support bekräftelse förfrågningar (RD04)

För cmdletar som utför en åtgärd som ändrar systemet ska de anropa metoden [system. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) för att begära bekräftelse, och i särskilda fall anropar du [ Metoden system. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . (Metoden [system. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) får bara anropas efter att metoden [system. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anropas.)

För att göra dessa anrop måste cmdleten ange att den stöder bekräftelse begär Anden genom att ange nyckelordet `SupportsShouldProcess` för cmdlet-attributet. Mer information om hur du anger det här attributet finns i [deklaration av cmdlet-attribut](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Om cmdlet-attributet för cmdlet-klassen anger att cmdleten stöder anrop till metoden [system. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , och cmdleten inte kan ringa till [ System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -metoden, användaren kan ändra systemet utan förvarning.

Använd metoden [system. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) för alla system ändringar. En användar inställning och parametern `WhatIf` styr metoden [system. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Däremot utför anropet [system. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) ytterligare en kontroll för potentiellt skadliga ändringar. Den här metoden styrs inte av någon användar inställning eller parametern `WhatIf`. Om cmdleten anropar metoden [system. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) ska den ha en `Force`-parameter som kringgår anropen till dessa två metoder och som fortsätter med åtgärden. Detta är viktigt eftersom det gör att din cmdlet kan användas i icke-interaktiva skript och värdar.

Om dina cmdlets stöder dessa anrop kan användaren avgöra om åtgärden ska utföras. Till exempel anropar cmdleten [Stop-process](/powershell/module/microsoft.powershell.management/stop-process) metoden [system. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) innan en uppsättning kritiska processer stoppas, inklusive system-, Winlogon-och Spoolsv-processer.

Mer information om hur du stöder dessa metoder finns i [begära bekräftelse](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Support Force-parameter för interaktiva sessioner (RD05)

Om cmdleten används interaktivt ska du alltid ange en Force-parameter för att åsidosätta de interaktiva åtgärderna, t. ex. prompter eller Läs rader med inaktuella ingångar. Detta är viktigt eftersom det gör att din cmdlet kan användas i icke-interaktiva skript och värdar. Följande metoder kan implementeras av en interaktiv värd.

- [System. Management. Automation. Host. PSHostUserInterface. prompt *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System. Management. Automation. Host. Pshostuserinterface. PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System. Management. Automation. Host. Ihostuisupportsmultiplechoiceselection. PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System. Management. Automation. Host. Pshostuserinterface. PromptForCredential *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System. Management. Automation. Host. Pshostuserinterface. ReadLine *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System. Management. Automation. Host. Pshostuserinterface. ReadLineAsSecureString *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Dokument utmatnings objekt (RD06)

Windows PowerShell använder de objekt som skrivs till pipelinen. För att användarna ska kunna dra nytta av de objekt som returneras av varje cmdlet måste du dokumentera de objekt som returneras och du måste dokumentera vad medlemmarna av de returnerade objekten används för.

## <a name="code-guidelines"></a>Kod rikt linjer

Följande rikt linjer måste följas när du skriver cmdlet-kod. När du hittar en kod rikt linje som gäller för din situation bör du läsa rikt linjerna för utformning av liknande rikt linjer.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Härled från cmdlet eller PSCmdlet-klasser (RC01)

En cmdlet måste vara härledd från antingen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) eller [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Base Class. Cmdletar som är härledda från klassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) är inte beroende av Windows PowerShell-körningsmiljön. De kan anropas direkt från ett Microsoft .NET Ramverks språk. -Cmdlet: ar som härleds från klassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) är beroende av Windows PowerShell-körningsmiljön. De körs därför inom en körnings utrymme.

Alla cmdlet-klasser som du implementerar måste vara offentliga klasser. Mer information om dessa cmdlet-klasser finns i [cmdlet-översikt](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>Ange cmdlet-attributet (RC02)

För att en cmdlet ska kunna identifieras av Windows PowerShell måste dess .NET Framework klass vara dekorerat med cmdlet-attributet. Det här attributet anger följande funktioner för cmdleten.

- Verb-och-Substantiv-paret som identifierar cmdleten.

- Standard parameter uppsättningen som används när flera parameter uppsättningar anges. Standard parameter uppsättningen används när Windows PowerShell inte har tillräckligt med information för att avgöra vilken parameter som ska användas.

- Anger om cmdleten stöder anrop till metoden [system. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Den här metoden visar ett bekräftelse meddelande till användaren innan cmdleten gör en ändring i systemet. Mer information om hur bekräftelse begär Anden görs finns i [begära bekräftelse](./requesting-confirmation-from-cmdlets.md).

- Ange effekt nivån (eller allvarlighets grad) för åtgärden som är associerad med bekräftelse meddelandet. I de flesta fall ska standardvärdet medium användas. Mer information om hur effekt nivån påverkar de bekräftelse förfrågningar som visas för användaren finns i [begära bekräftelse](./requesting-confirmation-from-cmdlets.md).

Mer information om hur du deklarerar cmdlet-attributet finns i [CmdletAttribute-deklaration](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Åsidosätt en metod för bearbetning av indata (RC03)

För att cmdleten ska delta i Windows PowerShell-miljön, måste den åsidosätta minst en av följande *metoder för bearbetning av indata*.

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) den här metoden kallas en gång och används för att tillhandahålla för bearbetnings funktioner.

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) den här metoden anropas flera gånger och används för att tillhandahålla post-för-post-funktioner.

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) den här metoden kallas en gång och används för att tillhandahålla funktioner för efter bearbetning.

### <a name="specify-the-outputtype-attribute-rc04"></a>Ange attributet OutputType (RC04)

Attributet OutputType (som introducerades i Windows PowerShell 2,0) anger .NET Framework typ som cmdleten returnerar till pipelinen. Genom att ange utdatatypen för dina cmdlets, blir de objekt som returneras av cmdleten mer synliga av andra cmdletar. Mer information om dekorera cmdlet-klassen med det här attributet finns i [deklarationen för OutputType-attribut](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Behåll inte referenser till utgående objekt (RC05)

Cmdleten ska inte behålla några referenser till de objekt som skickas till metoden [system. Management. Automation. cmdlet. WriteObject *](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . De här objekten skickas till nästa cmdlet i pipelinen eller används av ett skript. Om du behåller handtagen till objekten, kommer två entiteter att äga varje objekt, vilket orsakar fel.

### <a name="handle-errors-robustly-rc06"></a>Hantera fel stabilt (RC06)

En administrations miljö identifierar och gör viktiga ändringar i systemet som du administrerar. Därför är det viktigt att cmdlets hanterar fel korrekt. Mer information om fel poster finns i [fel rapportering för Windows PowerShell](./error-reporting-concepts.md).

- När ett fel förhindrar att en cmdlet fortsätter att bearbeta fler poster är det ett avslutande fel. Cmdleten måste anropa metoden [system. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) som refererar till ett [system. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -objekt. Om ett undantag inte fångas av cmdleten, genererar Windows PowerShell-körningsmiljön ett avslutande fel som innehåller mindre information.

- För ett icke-avslutande fel som inte stoppar åtgärden på Nästa post som kommer från pipelinen (till exempel en post som skapats av en annan process) måste cmdleten anropa metoden [system. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) som refererar till ett [system. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -objekt. Ett exempel på ett icke-avslutande fel är ett fel som inträffar om en viss process inte kan stoppas. Genom att anropa metoden [system. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) kan användaren konsekvent utföra de begärda åtgärderna och spara informationen för särskilda åtgärder som inte fungerar. Din cmdlet ska hantera varje post så oberoende som möjligt.

- Objektet [system. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) som refereras av objektet [system. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) och [system. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metoder kräver en undantag vid dess kärna. Följ rikt linjerna för .NET Framework design när du bestämmer vilket undantag som ska användas. Om felet är semantiskt på samma sätt som ett befintligt undantag, använder du detta undantag eller härleds från det undantaget. Annars härleds en ny undantags-eller undantags hierarki direkt från [system. Exception](/dotnet/api/System.Exception) -typen.

Ett [system. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -objekt kräver också en fel kategori som grupperar fel för användaren. Användaren kan visa fel baserat på kategorin genom att ange värdet för skal variabeln `$ErrorView` till CategoryView. Möjliga kategorier definieras av uppräkningen [system. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) .

- Om en cmdlet skapar en ny tråd, och om den kod som körs i den tråden ger upphov till ett ohanterat undantag, kommer Windows PowerShell inte att fånga fel meddelandet och kommer att avsluta processen.

- Om ett objekt har kod i sin destruktorn som orsakar ett ohanterat undantag, kommer Windows PowerShell inte att fånga fel meddelandet och kommer att avsluta processen. Detta inträffar även om ett objekt anropar en dispose-metod som orsakar ett ohanterat undantag.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Använd en Windows PowerShell-modul för att distribuera dina cmdlets (RC07)

Skapa en Windows PowerShell-modul för att paketera och distribuera dina cmdletar. Stöd för moduler introduceras i Windows PowerShell 2,0. Du kan använda sammansättningarna som innehåller dina cmdlet-klasser direkt som binära modulblad (detta är användbart när du testar dina cmdlets) eller så kan du skapa ett modul manifest som refererar till cmdlet-sammansättningarna. (Du kan också lägga till befintliga snapin-sammansättningar när du använder moduler.) Mer information om moduler finns i [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Se även

[Rekommendationer för starkt uppmuntrande utveckling](./strongly-encouraged-development-guidelines.md)

[Rikt linjer för utveckling av råd](./advisory-development-guidelines.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
