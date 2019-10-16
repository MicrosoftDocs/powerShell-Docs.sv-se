---
title: Starkt uppmuntrande utvecklings rikt linjer | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 0906d0d37c66b8c1538a0b2e9e0f1ff2fba12ac0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359193"
---
# <a name="strongly-encouraged-development-guidelines"></a>Starkt rekommenderade riktlinjer för utveckling

I det här avsnittet beskrivs rikt linjer som du bör följa när du skriver dina cmdlets. De är indelade i rikt linjer för att utforma cmdlets och rikt linjer för att skriva din cmdlet-kod. Du kanske upptäcker att dessa rikt linjer inte gäller för varje scenario. Men om de tillämpas och du inte följer dessa rikt linjer, kan användarna ha en dålig upplevelse när de använder dina cmdletar.

## <a name="design-guidelines"></a>Design rikt linjer

- [Använd ett angivet Substantiv för ett cmdlet-namn (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Använd Pascal-fall för cmdlet-namn (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Rikt linjer för parameter design (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [Ge feedback till användaren (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Skapa en hjälp fil för cmdlet (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Kod rikt linjer

- [Kodnings parametrar (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [Support bra definierade pipeline-inmatare (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Skriv enskilda poster till pipelinen (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Gör cmdletar Skift läges okänsliga och Skift läges bevarande (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Design rikt linjer

Följande rikt linjer bör följas när du utformar cmdlets för att säkerställa en konsekvent användar upplevelse mellan att använda dina cmdletar och andra cmdletar. När du hittar en design rikt linje som gäller din situation bör du titta närmare på kod rikt linjerna för liknande rikt linjer.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Använd ett angivet Substantiv för ett cmdlet-namn (SD01)

Substantiv som används i cmdlet-namn måste vara särskilt så att användaren kan identifiera dina cmdletar. Prefix för generiska substantiv som "Server" med en förkortad version av produkt namnet. Om t. ex. ett substantiv refererar till en server som kör en instans av Microsoft SQL Server, använder du ett substantiv som "SQLServer". Kombinationen av vissa Substantiv och den korta listan över godkända verb gör det möjligt för användaren att snabbt upptäcka och förutse funktioner samtidigt som du undviker duplicering mellan cmdlet-namn.

För att förbättra användar upplevelsen ska det substantiv som du väljer för ett cmdlet-namn vara singular. Använd till exempel namnet `Get-Process` i stället för **Get-Processes**. Det är bäst att följa den här regeln för alla cmdlet-namn, även om en cmdlet förmodligen fungerar på mer än ett objekt.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Använd Pascal-fall för cmdlet-namn (SD02)

Använd Pascal-fall för parameter namn. Med andra ord skriver du in den första bokstaven i verbet och alla termer som används i substantivet. Till exempel "`Clear-ItemProperty`".

### <a name="parameter-design-guidelines-sd03"></a>Rikt linjer för parameter design (SD03)

En cmdlet behöver parametrar som tar emot data som den måste fungera på och parametrar som anger information som används för att fastställa egenskaperna för åtgärden. En cmdlet kan till exempel ha en `Name`-parameter som tar emot data från pipelinen, och cmdleten kan ha en `Force`-parameter för att ange att cmdleten kan tvingas utföra åtgärden. Det finns ingen gräns för antalet parametrar som en cmdlet kan definiera.

#### <a name="use-standard-parameter-names"></a>Använd standard parameter namn

Din cmdlet ska använda standard parameter namn så att användaren snabbt kan fastställa vad en viss parameter innebär. Om ett mer särskilt namn krävs, Använd ett standard parameter namn och ange sedan ett mer särskilt namn som alias. Till exempel har cmdleten `Get-Service` en parameter som har ett generiskt namn (`Name`) och ett mer särskilt alias (`ServiceName`). Båda villkoren kan användas för att ange parametern.

Mer information om parameter namn och deras data typer finns i [rikt linjer för cmdlet-parameter namn och funktioner](./standard-cmdlet-parameter-names-and-types.md).

#### <a name="use-singular-parameter-names"></a>Använd singular parameter namn

Undvik att använda plural-namn för parametrar vars värde är ett enda element. Detta inkluderar parametrar som tar matriser eller listor eftersom användaren kan ange en matris eller lista med endast ett-element.

Plural-parameter namn ska endast användas i de fall där parameterns värde alltid är ett värde för flera element. I dessa fall bör cmdleten verifiera att flera element anges och cmdleten ska visa en varning till användaren om flera element inte anges.

#### <a name="use-pascal-case-for-parameter-names"></a>Använd Pascal-fall för parameter namn

Använd Pascal-fall för parameter namn. Med andra ord skriver du in den första bokstaven i varje ord i parameter namnet, inklusive den första bokstaven i namnet. Parameter namnet `ErrorAction` använder till exempel rätt Skift läge. Följande parameter namn använder felaktig kapitalisering:

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Parametrar som tar en lista med alternativ

Det finns två sätt att skapa en parameter vars värde kan väljas från en uppsättning alternativ.

- Definiera en uppräknings typ (eller Använd en befintlig uppräknings typ) som anger giltiga värden. Använd sedan uppräknings typen för att skapa en parameter av den typen.

- Lägg till attributet **ValidateSet** i parameter deklarationen. Mer information om det här attributet finns i [ValidateSet Attribute-deklaration](./validateset-attribute-declaration.md).

#### <a name="use-standard-types-for-parameters"></a>Använd standard typer för parametrar

Använd standard typer för parametrar där det är möjligt för att säkerställa konsekvens med andra cmdletar. Mer information om vilka typer som ska användas för olika parametrar finns i [standard parameter namn och typer](./standard-cmdlet-parameter-names-and-types.md). Det här avsnittet innehåller länkar till flera avsnitt som beskriver namn och .NET Framework typer för grupper med standard parametrar, t. ex. "aktivitets parametrar".

#### <a name="use-strongly-typed-net-framework-types"></a>Använd typer av starkt skrivna .NET Framework

Parametrar ska definieras som .NET Framework typer för att ge bättre parameter validering. Till exempel ska parametrar som är begränsade till ett värde från en uppsättning värden definieras som en uppräknings typ. För att stödja ett Uniform Resource Identifier (URI)-värde definierar du parametern som en [system. URI](/dotnet/api/System.Uri) -typ. Undvik grundläggande sträng parametrar för alla fält med fri Forms egenskaper.

#### <a name="use-consistent-parameter-types"></a>Använd konsekventa parameter typer

Använd alltid samma parameter typ när samma parameter används av flera cmdletar.  Om till exempel parametern `Process` är en [system. Int16](/dotnet/api/System.Int16) -typ för en cmdlet ska du inte göra parametern `Process` för en annan cmdlet: en [system. Uint16](/dotnet/api/System.UInt16) -typ.

#### <a name="parameters-that-take-true-and-false"></a>Parametrar som tar sant och falskt

Om parametern bara tar `true` och `false` definierar du parametern som Type [system. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter). En växel parameter behandlas som `true` när den anges i ett kommando. Om parametern inte ingår i ett kommando, anser Windows PowerShell värdet för parametern som ska `false`. Definiera inte booleska parametrar.

Om parametern behöver särskilja mellan tre värden: $true, $false och "ospecificerad", definierar du en parameter av typen Nullable @ no__t-0bool >.  Behovet av ett tredje, "Ospecificerat" värde inträffar vanligt vis när cmdleten kan ändra en Boolean-egenskap för ett objekt. I det här fallet "Ospecificerat" innebär att egenskapens aktuella värde inte ändras.

#### <a name="support-arrays-for-parameters"></a>Stöd mat ris för parametrar

Användare måste ofta utföra samma åtgärd mot flera argument. För dessa användare ska en cmdlet acceptera en matris som parameter indata så att en användare kan skicka argumenten till parametern som en Windows PowerShell-variabel. Till exempel använder cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) en matris för strängarna som identifierar namnen på de processer som ska hämtas.

#### <a name="support-the-passthru-parameter"></a>Stöd för parametern PassThru

Som standard fungerar många cmdlets som ändrar systemet, till exempel cmdleten [Stop process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) , som "Sinks" för objekt och returnerar inte ett resultat. Denna cmdlet ska implementera parametern `PassThru` för att tvinga cmdleten att returnera ett objekt. När parametern `PassThru` anges, returnerar cmdleten ett objekt genom att använda ett anrop till metoden [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Följande kommando stoppar till exempel processen Calc och skickar den resulterande processen till pipelinen.

```powershell
Stop-Process calc -passthru
```

I de flesta fall ska Lägg till, ange och nya cmdletar ha stöd för en `PassThru`-parameter.

#### <a name="support-parameter-sets"></a>Stöd parameter uppsättningar

En cmdlet är avsedd att utföra ett enda syfte. Det finns dock ofta mer än ett sätt att beskriva åtgärden eller åtgärds målet. En process kan till exempel identifieras med sitt namn, med dess identifierare eller av ett process objekt. Cmdleten ska ha stöd för alla rimliga representationer av sina mål. Normalt uppfyller cmdleten detta krav genom att ange uppsättningar med parametrar (kallas parameter uppsättningar) som fungerar tillsammans. En enskild parameter kan tillhöra valfritt antal parameter uppsättningar. Mer information om parameter uppsättningar finns i [cmdlet parameter Sets](./cmdlet-parameter-sets.md).

När du anger parameter uppsättningar anger du endast en parameter i uppsättningen till ValueFromPipeline. Mer information om hur du deklarerar attributet **parameter** finns i [ParameterAttribute-deklaration](./parameter-attribute-declaration.md).

När parameter uppsättningar används definieras standard parameter uppsättningen av **cmdlet** -attributet. Standard parameter uppsättningen bör innehålla de parametrar som troligen används i en interaktiv Windows PowerShell-session. Mer information om hur du deklarerar **cmdlet** -attributet finns i [CmdletAttribute-deklaration](./cmdlet-attribute-declaration.md).

### <a name="provide-feedback-to-the-user-sd04"></a>Ge feedback till användaren (SD04)

Använd rikt linjerna i det här avsnittet för att ge feedback till användaren. Den här feedbacken gör att användaren kan vara medveten om vad som händer i systemet och fatta bättre administrativa beslut.

Med Windows PowerShell-körningsmiljön kan en användare ange hur utdata ska hanteras från varje anrop till metoden `Write` genom att ange en inställnings variabel. Användaren kan ange flera variabler, inklusive en variabel som avgör om systemet ska visa information och en variabel som avgör om systemet ska fråga användaren innan ytterligare åtgärder vidtas.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>Stöd för metoderna WriteWarning, WriteVerbose och WriteDebug

En cmdlet ska anropa metoden [system. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) när cmdleten är på väg att utföra en åtgärd som kan ha ett oavsiktligt resultat. Till exempel ska en cmdlet anropa den här metoden om cmdleten är på väg att skriva över en skrivskyddad fil.

En cmdlet ska anropa metoden [system. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) när användaren behöver information om vad cmdleten gör. Till exempel ska en-cmdlet anropa den här informationen om cmdlet-författaren anser att det finns scenarier som kan kräva mer information om vad cmdleten gör.

Cmdleten ska anropa metoden [system. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) när en utvecklare eller en produkt support tekniker måste förstå vad som har skadat cmdlet-åtgärden. Det är inte nödvändigt att cmdleten anropar metoden [system. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) i samma kod som anropar metoden [system. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) eftersom parametern `Debug` visar både informations uppsättningar.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>Stöd för WriteProgress för åtgärder som tar lång tid

Cmdlet-åtgärder som tar lång tid att slutföra och som inte kan köras i bakgrunden bör ha stöd för förlopps rapportering via periodiska anrop till metoden [system. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .

#### <a name="use-the-host-interfaces"></a>Använd värd gränssnitten

Ibland måste en cmdlet kommunicera direkt med användaren i stället för genom att använda de olika Skriv-eller-metoderna som stöds av klassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . I det här fallet ska cmdleten härledas från klassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) och använda egenskapen [system. Management. Automation. PSCmdlet. Host *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) . Den här egenskapen stöder olika kommunikations typer, inklusive typerna PromptForChoice, prompt och WriteLine/ReadLine. På den mest specifika nivån ger det också olika sätt att läsa och skriva enskilda nycklar och att hantera buffertar.

Såvida inte en cmdlet är särskilt utformad för att generera ett grafiskt användar gränssnitt (GUI) bör den inte kringgå värden med hjälp av egenskapen [system. Management. Automation. PSCmdlet. Host *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) . Ett exempel på en cmdlet som är utformad för att generera ett grafiskt användar gränssnitt är cmdleten [out-GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) .

> [!NOTE]
> Cmdletar ska inte använda [system. Console](/dotnet/api/System.Console) -API: et.

### <a name="create-a-cmdlet-help-file-sd05"></a>Skapa en hjälp fil för cmdlet (SD05)

Skapa en Help. XML-fil som innehåller information om cmdleten för varje cmdlet-sammansättning. Den här informationen innehåller en beskrivning av cmdleten, beskrivningar av cmdletens parametrar, exempel på cmdlet: en, med mera.

## <a name="code-guidelines"></a>Kod rikt linjer

Följande rikt linjer bör följas när du kodar cmdletar för att säkerställa en konsekvent användar upplevelse mellan att använda dina cmdletar och andra cmdletar. När du hittar en kod rikt linje som gäller för din situation bör du läsa rikt linjerna för utformning av liknande rikt linjer.

### <a name="coding-parameters-sc01"></a>Kodnings parametrar (SC01)

Definiera en parameter genom att deklarera en offentlig egenskap för cmdlet-klassen som är dekorerad med attributet **parameter** . Parametrarna behöver inte vara statiska medlemmar i den härledda .NET Frameworks klassen för cmdleten. Mer information om hur du deklarerar attributet **parameter** finns i [deklaration av parameter attribut](./parameter-attribute-declaration.md).

#### <a name="support-windows-powershell-paths"></a>Stöd för Windows PowerShell-sökvägar

Windows PowerShell-sökvägen är mekanismen för att normalisera åtkomst till namn områden. När du tilldelar en Windows PowerShell-sökväg till en parameter i cmdleten kan användaren definiera en anpassad "enhet" som fungerar som en genväg till en angiven sökväg. När en användare anger en sådan enhet, kan lagrade data, till exempel data i registret, användas på ett konsekvent sätt.

Om din cmdlet gör det möjligt för användaren att ange en fil eller en data källa, bör den definiera en parameter av typen [system. String](/dotnet/api/System.String). Om mer än en enhet stöds måste typen vara en matris. Namnet på parametern ska vara `Path`, med ett alias för `PSPath`. Dessutom ska parametern `Path` ha stöd för jokertecken. Om stöd för jokertecken inte är obligatoriskt definierar du en `LiteralPath`-parameter.

Om data som cmdleten läser eller skriver måste vara en fil, ska cmdleten acceptera Windows PowerShell Path-indata och cmdleten ska använda egenskapen [system. Management. Automation. sessionState. Path](/dotnet/api/System.Management.Automation.SessionState.Path) för att översätta Windows PowerShell-sökvägar till sökvägar som fil systemet känner igen. De olika mekanismerna omfattar följande metoder:

- [System. Management. Automation. PSCmdlet. GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System. Management. Automation. PSCmdlet. GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System. Management. Automation. PathIntrinsics. GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System. Management. Automation. PathIntrinsics. GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Om data som cmdleten läser eller skriver bara är en uppsättning strängar i stället för en fil, ska cmdleten använda providerns innehålls information (`Content` medlem) för att läsa och skriva. Den här informationen hämtas från egenskapen [system. Management. Automation. Provider. CmdletProvider. InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) . Dessa metoder gör det möjligt för andra data lager att delta i läsning och skrivning av data.

#### <a name="support-wildcard-characters"></a>Stöd för jokertecken

En cmdlet måste ha stöd för jokertecken om det är möjligt. Stöd för jokertecken förekommer på många platser i en cmdlet (särskilt när en parameter tar en sträng för att identifiera ett objekt från en uppsättning objekt). Exempel: **Stop-proc-** cmdleten från StopProc- [självstudien](./stopproc-tutorial.md) definierar till exempel en `Name`-parameter för att hantera strängar som representerar process namn. Den här parametern stöder jokertecken så att användaren enkelt kan ange vilka processer som ska stoppas.

När stöd för jokertecken är tillgängligt skapar en cmdlet-åtgärd vanligt vis en matris. Ibland är det inte meningsfullt att stödja en matris eftersom användaren bara kan använda ett enda objekt i taget. Till exempel behöver cmdleten [set-location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) inte stöd för en matris eftersom användaren bara anger en enda plats. I den här instansen stöder cmdlet: en fortfarande jokertecken, men den framtvingar matchning till en enda plats.

Mer information om mönster med jokertecken finns i [stödjande jokertecken i cmdlet-parametrar](./supporting-wildcard-characters-in-cmdlet-parameters.md).

#### <a name="defining-objects"></a>Definiera objekt

Det här avsnittet innehåller rikt linjer för att definiera objekt för cmdlets och för att utöka befintliga objekt.

##### <a name="define-standard-members"></a>Definiera standard medlemmar

Definiera standard medlemmar för att utöka en objekt typ i en anpassad typ. ps1xml-fil (Använd Windows PowerShell-typerna. ps1xml-filen som en mall). Standard medlemmar definieras av en nod med namnet PSStandardMembers. Dessa definitioner gör det möjligt för andra cmdletar och Windows PowerShell-körningsmiljön att arbeta med ditt objekt på ett konsekvent sätt.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>Definiera ObjectMembers som ska användas som parametrar

Om du skapar ett objekt för en cmdlet bör du se till att dess medlemmar mappar direkt till parametrarna för de cmdletar som ska använda den. Med den här mappningen kan objektet enkelt skickas till pipelinen och skickas från en-cmdlet till en annan.

Befintliga .NET Framework objekt som returneras av cmdlets ofta saknar vissa viktiga eller praktiska medlemmar som krävs av skript utvecklaren eller användaren. De medlemmar som saknas kan vara särskilt viktiga för att visa och för att skapa rätt medlems namn så att objektet kan skickas korrekt till pipelinen. Skapa en anpassad types. ps1xml-fil för att dokumentera de nödvändiga medlemmarna. När du skapar den här filen rekommenderar vi följande namngivnings konvention: *< Your_Product_Name >* . Types. ps1xml.

Du kan till exempel lägga till en skript egenskap `Mode` till typen [system. io. fileinfo](/dotnet/api/System.IO.FileInfo) för att visa attributen för en fil tydligare. Dessutom kan du lägga till egenskapen `Count` alias till [system. mat ris](/dotnet/api/System.Array) typen för att tillåta en konsekvent användning av egenskaps namnet (i stället för `Length`).

##### <a name="implement-the-icomparable-interface"></a>Implementera IComparable-gränssnittet

Implementera ett [system. IComparable](/dotnet/api/System.IComparable) -gränssnitt på alla utgående objekt. Detta gör att utmatnings objekt enkelt kan skickas till olika sorterings-och analys-cmdletar.

##### <a name="update-display-information"></a>Uppdatera visnings information

Om visningen för ett objekt inte ger det förväntade resultatet skapar du en anpassad *\<YourProductName >* . Format. ps1xml-fil för objektet.

### <a name="support-well-defined-pipeline-input-sc02"></a>Support bra definierade pipeline-inmatare (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>Implementera mitt i en pipeline

Implementera en cmdlet förutsatt att den kommer att anropas från mitten av en pipeline (det vill säga andra cmdlets skapar indata eller förbrukar utdata). Du kan till exempel anta att cmdleten `Get-Process`, eftersom den genererar data, endast används som första cmdlet i en pipeline. Men eftersom den här cmdleten är avsedd för mitten av en pipeline, tillåter den här cmdleten tidigare cmdletar eller data i pipelinen att ange vilka processer som ska hämtas.

#### <a name="support-input-from-the-pipeline"></a>Stöd för ininformation från pipelinen

I varje parameter uppsättning för en cmdlet inkluderar du minst en parameter som stöder indatamängden från pipelinen. Stöd för pipeline-indata gör att användaren kan hämta data eller objekt, skicka dem till rätt parameter uppsättning och skicka resultaten direkt till en-cmdlet.

En parameter accepterar ininformation från pipelinen om attributet **parameter** innehåller nyckelordet `ValueFromPipeline`, nyckelordet `ValueFromPipelineByPropertyName` eller båda nyckelorden i dess deklaration. Om ingen av parametrarna i en parameter uppsättning stöder `ValueFromPipeline`-eller `ValueFromPipelineByPropertyName`-nyckelorden, kan cmdleten inte meningsfullt placeras efter en annan cmdlet eftersom den kommer att ignorera eventuella pipeline-inflöden.

#### <a name="support-the-processrecord-method"></a>Stöd för metoden ProcessRecord

Om du vill acceptera alla poster från föregående cmdlet i pipelinen måste din cmdlet implementera metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . Windows PowerShell anropar den här metoden flera gånger, en gång för varje post som skickas till din cmdlet.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Skriv enskilda poster till pipelinen (SC03)

När en cmdlet returnerar objekt ska cmdleten skriva objekten direkt när de genereras. Cmdleten bör inte innehålla dem för att buffra dem i en kombinerad matris. De cmdletar som tar emot objekten som indata kommer sedan att kunna bearbeta, Visa eller bearbeta och visa utdata utan fördröjning. En cmdlet som genererar utdata en i taget bör anropa metoden [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . En cmdlet som genererar utdata i batchar (till exempel eftersom ett underliggande API returnerar en matris med utgående objekt) bör anropa metoden [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) med den andra parametern inställd på `true`.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Gör cmdletar Skift läges okänsliga och Skift läges bevarande (SC04)

Som standard är Windows PowerShell inte Skift läges känsligt. Men eftersom det behandlar flera befintliga system, bevarar Windows PowerShell Skift läge för enkel drift och kompatibilitet. Om ett tecken i versaler anges med versaler, så behåller Windows PowerShell det med versala bokstäver. För att system ska fungera bra måste en cmdlet följa denna konvention. Om möjligt bör det köras på ett skift läges okänsligt sätt. Det bör dock behålla det ursprungliga fallet för cmdletar som sker senare i ett kommando eller i pipelinen.

## <a name="see-also"></a>Se även

[Nödvändiga utvecklings rikt linjer](./required-development-guidelines.md)

[Rikt linjer för utveckling av råd](./advisory-development-guidelines.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
