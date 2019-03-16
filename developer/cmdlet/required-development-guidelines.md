---
title: Riktlinjerna för utveckling | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: 3f6bcd2e4ef4d9c404b3a5deeaa9f25d3fa42ec1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056523"
---
# <a name="required-development-guidelines"></a>Obligatoriska riktlinjer för utveckling

Följande riktlinjer måste följas när du skriver dina cmdlets. De är indelade i riktlinjer för att utforma cmdlets och riktlinjer för att skriva cmdlet-kod. Om du inte följer dessa riktlinjer dina cmdlets kan misslyckas och användarna kan ha en dålig upplevelse när de använder dina cmdlets.

## <a name="in-this-topic"></a>I det här avsnittet

### <a name="design-guidelines"></a>Designriktlinjer

- [Använd endast godkända verb (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Cmdlet-namn: Tecken som inte får återanvändas (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Namn på parametrar som inte får återanvändas (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Bekräftelse supportärenden (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Stöd för parametern Force för interaktiva sessioner (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Utdata-Dokumentobjekt (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Riktlinjer för kod

- [Härledd från Cmdlet eller PSCmdlet klasser (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Ange Cmdlet-attribut (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Åsidosätt indata som bearbetar metod (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Ange OutputType-attributet (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Spara inte referenser till utdata-objekt (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Handle Errors Robustly (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Använda en Windows PowerShell-modul för att distribuera dina Cmdlets (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Designriktlinjer

Följande riktlinjer måste följas när du utformar cmdletar för att säkerställa en konsekvent användarupplevelse mellan att använda dina cmdlets och andra cmdlet: ar. När du har hittat en Design riktlinje som gäller för din situation bör du titta på koden riktlinjer för liknande riktlinjer.

### <a name="use-only-approved-verbs-rd01"></a>Använd endast godkända verb (RD01)

Verbet som har angetts i Cmdlet-attributet måste komma från en känd uppsättning verb som tillhandahålls av Windows PowerShell. Det får inte vara någon av otillåten synonymer. Använd konstant strängar som definieras av följande uppräkningar ange cmdlet verb:

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Läs mer om de godkända verb, [Cmdlet verb](./approved-verbs-for-windows-powershell-commands.md).

Användare behöver en uppsättning att upptäcka och förväntade cmdlet-namnen. Använd lämplig verbet så att användaren kan göra en snabb utvärdering av en cmdlet gör och för att enkelt utforska funktionerna i systemet. Till exempel följande kommandorad hämtar en lista över alla kommandon i systemet vars namn börjar med ”start”: `get-command start-*`. Använd substantiv i dina cmdlets för att skilja dina cmdletar från andra cmdlet: ar. Substantivet anger den resurs där åtgärden utförs. Själva funktionen representeras av verbet.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Cmdlet-namn: Tecken som inte får återanvändas (RD02)

När du namnger cmdletar, Använd inte någon av följande specialtecken.

|Tecken|Namn|
|---------------|----------|
|#|nummertecken|
|, |kommaavgränsad|
|()|parenteser|
|{}|klammerparenteser|
|[]|hakparenteser|
|&|et-tecken|
|-|bindestreck **Obs:**  Bindestreck som kan användas för att avgränsa verb från substantivet, men den kan inte användas inom substantivet eller verbet.|
|/|snedstreck|
|\|backslash|
|$|dollartecken|
|^|cirkumflex|
|;|semicolon|
|:|kolon|
|"|citattecken|
|'|enkelt citattecken|
|<>|vinkelparentes|
|&#124;|vertikalstreck|
|?|frågetecken|
|@|tecknet|
|' | tillbaka skalstreck (allvarligt accent)|
|*|asterisk|
|%|procenttecken|
|+|plustecken|
|=|likhetstecken|
|~|tilde|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Namn på parametrar som inte får återanvändas (RD03)

Windows PowerShell tillhandahåller en gemensam uppsättning en parametrar i alla cmdletar plus ytterligare parametrar som har lagts till i vissa situationer. När du utformar dina egna cmdletar kan inte du använda följande namn: Bekräfta, felsökning, ErrorAction, -ErrorVariable, OutBuffer OutVariable, WarningAction, WarningVariable, WhatIf, UseTransaction, och utförlig. Mer information om dessa parametrar finns i [vanliga parameternamn](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Bekräftelse supportärenden (RD04)

För cmdlet: ar som utför en åtgärd som ändrar systemet, ska de anropa den [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metod för att begära bekräftelse och i särskilda fall anropa den [ System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metod. (Den [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoden ska anropas förrän den [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metoden anropas.)

Att göra dessa anrop som cmdlet: en måste ange att den stöder begäranden om händelsebekräftelse genom att ange den `SupportsShouldProcess` nyckelord för attributet Cmdlet. Läs mer om att ställa in det här attributet [Cmdlet attributet deklarationen](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Om Cmdlet-attributet i cmdlet-klassen anger att cmdleten har stöd för anrop till den [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metod och cmdleten inte kan göra anrop till den [ System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metoden användaren kan ändra systemet oväntat.

Använd den [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metod för ändringar system. En användarinställning och `WhatIf` parameterkontroll den [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metod. Däremot den [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) anrop utför ytterligare en kontroll efter potentiellt skadliga ändringar. Den här metoden inte kontrolleras av alla ANVÄNDARPREFERENSER eller `WhatIf` parametern. Om cmdlet: anropar den [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metod, som den ska ha en `Force` parameter som förbigår anrop till dessa två metoder och som fortsätter med åtgärden. Detta är viktigt eftersom den tillåter din cmdlet som ska användas i icke-interaktivt skript och värdar.

Om dina cmdletar stöder dessa anrop, kan användaren avgöra om åtgärden faktiskt ska utföras. Till exempel den [Stop-Process](/powershell/module/microsoft.powershell.management/stop-process) cmdlet-anrop i [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoden innan den stoppar en uppsättning viktiga processer, inklusive System, Winlogon, och Spoolsv processer.

Läs mer om att stödja dessa metoder, [begär bekräftelse](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Stöd för parametern Force för interaktiva sessioner (RD05)

Om du använder cmdlet: interaktivt, alltid ange ett Force-parametern om du vill åsidosätta de interaktiva åtgärderna, till exempel anvisningarna eller läsa rader av indata). Detta är viktigt eftersom den tillåter din cmdlet som ska användas i icke-interaktivt skript och värdar. Följande metoder kan implementeras med en interaktiv värd.

- [System.Management.Automation.Host.PSHostUserInterface.Prompt*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection.PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForCredential*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLine*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLineAsSecureString*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Utdata-Dokumentobjekt (RD06)

Windows PowerShell använder objekt som har skrivits till pipelinen. För användare att dra nytta av de objekt som returneras av varje cmdlet, måste du dokumentera de objekt som returneras och måste du dokumentera medlemmarna i dessa returnerade objekt som används för.

## <a name="code-guidelines"></a>Riktlinjer för kod

Följande riktlinjer måste följas när du skriver kod för cmdlet. När du har hittat en kod riktlinje som gäller för din situation bör du titta på designriktlinjer för liknande riktlinjer.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Härledd från Cmdlet eller PSCmdlet klasser (RC01)

En cmdlet måste komma från antingen den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) eller [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) basklassen. Cmdlet: ar som härleds från den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klass inte beror på en Windows PowerShell. De kan anropas direkt från alla Microsoft .NET Framework-språk. Cmdlet: ar som härleds från den [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klass beror på en Windows PowerShell. Därför kan köras de inom ett körningsutrymme.

Alla cmdlet-klasser som du implementerar måste vara offentliga klasser. Mer information om dessa cmdlet-klasserna finns [cmdlet: en översikt över](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>Ange Cmdlet-attribut (RC02)

.NET Framework klass måste vara dekorerad med Cmdlet-attribut för en cmdlet ska kunna identifieras av Windows PowerShell. Det här attributet anger följande funktioner i cmdleten.

- Verb och substantiv-paret som identifierar cmdlet: en.

- Standarduppsättningen som används när flera parameteruppsättningar har angetts för parametern. Standard-parameteruppsättningen används när Windows PowerShell inte har tillräckligt med information för att fastställa vilka parametern inställd på att använda.

- Anger om cmdleten stöder anrop till den [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metod. Den här metoden visas en bekräftelse till användaren innan cmdleten gör en ändring i systemet. Läs mer om hur begäranden om händelsebekräftelse görs [begär bekräftelse](./requesting-confirmation-from-cmdlets.md).

- Ange den åtgärd som är associerade med bekräftelsemeddelandet effektnivå (eller allvarlighetsgrad). I de flesta fall bör du används standardvärdet medium. Läs mer om hur effektnivå påverkar bekräftelse-begäranden som visas för användaren, [begär bekräftelse](./requesting-confirmation-from-cmdlets.md).

Läs mer om hur du deklarera cmdlet-attributet [CmdletAttribute deklarationen](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Åsidosätt indata som bearbetar metod (RC03)

För cmdleten att delta i Windows PowerShell-miljö, måste den åsidosätter minst en av följande *inkommande bearbetningsmetoder*.

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) den här metoden anropas en gång och används för att tillhandahålla förväg bearbetnings funktioner.

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) den här metoden anropas flera gånger och används för att tillhandahålla post med funktioner.

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) den här metoden anropas en gång och används för att tillhandahålla efterbearbetning funktioner.

### <a name="specify-the-outputtype-attribute-rc04"></a>Ange OutputType-attributet (RC04)

OutputType-attributet (introducerades i Windows PowerShell 2.0) anger den typ av .NET Framework som din cmdlet returnerar till pipelinen. Genom att ange utdatatypen för dina cmdlets du objekten som returneras av cmdlet: mer synliga för andra cmdletar. Läs mer om att dekorera cmdlet-klassen med det här attributet [OutputType-attributet deklarationen](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Spara inte referenser till utdata-objekt (RC05)

Cmdlet: ska inte behålla alla referenser till objekt som skickas till den [System.Management.Automation.Cmdlet.WriteObject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metod. De här objekten skickas till cmdleten nästa i pipelinen, eller de används av ett skript. Om du behåller referenser till objekten som två entiteter äger varje objektet, vilket leder till fel.

### <a name="handle-errors-robustly-rc06"></a>Hantera fel kraftigare (RC06)

En miljö för administration identifierar sin natur och gör viktiga ändringar i systemet som du administrerar. Därför är det viktigt att cmdletar hantera fel på rätt sätt. Mer information om felposter finns i [felrapportering för Windows PowerShell](./error-reporting-concepts.md).

- När ett fel förhindrar att en cmdlet fortsätter att bearbeta några fler poster, är det ett avslutande fel. Cmdlet: en måste anropa den [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metod som refererar till en [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objekt. Om ett undantag inte påträffades av cmdlet: en, utlöser Windows PowerShell-runtime själva ett avslutande fel med mindre information.

- För ett icke-avslutande fel som inte hindrar igen vid nästa post som kommer från pipelinen (till exempel en post skapas av en annan process) cmdlet: en måste anropa den [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metod som refererar till en [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objekt. Ett exempel på ett icke-avslutande fel är fel som uppstår om en viss process som inte går att stoppa. Anropa den [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metoden kan användaren konsekvent utföra åtgärder som begärts och att lagra information för specifika åtgärder som misslyckas. Cmdlet: bör hantera varje post oberoende som möjligt.

- Den [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objekt som refererar till den [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) och [ System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metoder kräver ett undantag kärnpunkter. Följ riktlinjerna för .NET Framework-design när du bestämmer undantaget att använda. Om felet är från samma som ett befintligt undantag kan använda detta undantag eller härledd från detta undantag. Annars kan härleda ett nytt undantag eller undantag hierarki direkt från den [System.Exception](/dotnet/api/System.Exception) typen.

En [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objekt kräver också en felkategori som grupperar fel för användaren. Du kan visa fel baserat på kategori genom att ange värdet för den `$ErrorView` gränssnittsvariabeln till CategoryView. Möjliga grupper definieras av den [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) uppräkning.

- Om en cmdlet skapar en ny tråd, och om den kod som körs i den tråden kastar ett ohanterat undantag, kommer inte att fånga felet i Windows PowerShell och kommer att avsluta processen.

- Om ett objekt har kod i dess destruktorn som orsakar ett ohanterat undantag, kommer inte att fånga felet i Windows PowerShell och kommer att avsluta processen. Detta inträffar även om ett objekt anropar Dispose metoder som orsakar ett ohanterat undantag.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Använda en Windows PowerShell-modul för att distribuera dina Cmdlets (RC07)

Skapa en Windows PowerShell-modul för att paketera och distribuera dina cmdlets. Stöd för moduler som introducerades i Windows PowerShell 2.0. Du kan använda de paket som innehåller cmdlet-klasser direkt som modulen binära filer (detta är användbart när du testar dina cmdlets) eller du kan skapa ett modulmanifest som refererar till cmdlet-sammansättningar. (Du kan också lägga till befintliga snapin-modulen sammansättningar när du använder moduler.) Läs mer om moduler [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Se även

[Vi rekommenderar utveckling riktlinjer](./strongly-encouraged-development-guidelines.md)

[Riktlinjer för rådgivande utveckling](./advisory-development-guidelines.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
