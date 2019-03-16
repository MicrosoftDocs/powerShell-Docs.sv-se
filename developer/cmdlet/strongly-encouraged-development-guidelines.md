---
title: Uppmuntras utveckling riktlinjer | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 0906d0d37c66b8c1538a0b2e9e0f1ff2fba12ac0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057730"
---
# <a name="strongly-encouraged-development-guidelines"></a>Starkt rekommenderade riktlinjer för utveckling

Det här avsnittet beskriver riktlinjer som du bör följa när du skriver dina cmdlets. De är indelade i riktlinjer för att utforma cmdlets och riktlinjer för att skriva cmdlet-kod. Du kanske upptäcker att riktlinjerna inte kan användas för alla scenarier. Men om de gäller och du inte följer dessa riktlinjer kan kan dina användare ha en dålig upplevelse när de använder dina cmdlets.

## <a name="design-guidelines"></a>Designriktlinjer

- [Använda en specifik substantiv för en Cmdlet-namn (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Använd Pascalnotation för Cmdlet-namnen (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Designriktlinjer för parametern (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [Ge Feedback till användaren (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Skapa en Cmdlet-hjälpavsnitten-fil (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Riktlinjer för kod

- [Koda parametrar (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [Stöd för väldefinierade Pipeline-indata (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Skriva enskild poster till pipelinen (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Kontrollera cmdletarna skiftlägeskänsliga och bevara (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Designriktlinjer

Följande riktlinjer ska följas när du utformar cmdletar för att säkerställa en konsekvent användarupplevelse mellan att använda dina cmdlets och andra cmdlet: ar. När du har hittat en Design riktlinje som gäller för din situation bör du titta på koden riktlinjer för liknande riktlinjer.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Använda en specifik substantiv för en Cmdlet-namn (SD01)

Substantiv som används i namngivning av cmdlet: en måste vara mycket specifik så att användaren kan identifiera dina cmdlets. Prefixet allmän substantiv, till exempel ”server” med en förkortad version av produktens namn. Till exempel om ett substantiv refererar till en server som kör en instans av Microsoft SQL Server, använda ett substantiv, till exempel ”SQLServer”. Kombinationen av specifika substantiv och en kort lista över godkända verb gör att användaren kan snabbt identifiera och förutse funktioner samtidigt som du undviker duplicering bland cmdlet-namnen.

För att förbättra användarupplevelsen, ska substantiv som du väljer för en cmdlet-namn rapportanvändare. Till exempel använda namnet `Get-Process` i stället för **Get-processer**. Det är bäst att följa den här regeln för alla cmdlet-namn, även när en cmdlet kommer troligen att agera på mer än ett objekt.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Använd Pascalnotation för Cmdlet-namnen (SD02)

Använd pascalnotation för parameternamn. Med andra ord med versal verb och alla termer som används i substantivet. Till exempel ”`Clear-ItemProperty`”.

### <a name="parameter-design-guidelines-sd03"></a>Designriktlinjer för parametern (SD03)

En cmdlet måste parametrarna som tar emot data måste köra och parametrar som visar information som används för att fastställa egenskaperna för åtgärden. En cmdlet kan till exempel ha en `Name` parameter som tar emot data från pipelinen och cmdleten kan ha en `Force` parameter som anger att cmdleten kan tvingas att utföra åtgärden. Det finns ingen gräns för antalet parametrar som en cmdlet kan definiera.

#### <a name="use-standard-parameter-names"></a>Använd Standard parameternamn

Cmdlet: bör använda standard parameternamn, så att du snabbt kan fastställa vad en viss parameter innebär. Om en mer specifik namn måste anges, använda ett standard parameternamn och anger sedan ett mer specifika namn som ett alias. Till exempel den `Get-Service` cmdleten har en parameter som har ett allmänt namn (`Name`) och en mer specifik alias (`ServiceName`). Båda termerna kan användas för att ange parametern.

Läs mer om parameternamn och datatyperna [Cmdlet parameternamnet och funktioner riktlinjer](./standard-cmdlet-parameter-names-and-types.md).

#### <a name="use-singular-parameter-names"></a>Använd rapportanvändare parameternamn

Undvik att använda plural namn för parametrar som vars värde är ett enda element. Detta omfattar parametrar som tar matriser eller listar eftersom användaren kan ange en matris eller en lista med bara ett element.

Plural parameternamn ska användas endast i de fall där värdet för parametern är alltid ett värde för flera element. I dessa fall bör du kontrollera att flera element distribueras utan att cmdleten ska visa en varning till användaren om flera element inte levereras cmdlet: en.

#### <a name="use-pascal-case-for-parameter-names"></a>Använd Pascalnotation för parameternamn

Använd pascalnotation för parameternamn. Med andra ord med versal i varje ord i parameternamn, inklusive den första bokstaven i namnet. Till exempel parameternamnet `ErrorAction` använder Korrigera versaler. I följande parameternamnen Använd felaktiga versaler:

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Parametrar som tar en lista med alternativ

Det finns två sätt att skapa en parameter vars värde kan väljas från en uppsättning med alternativ.

- Definiera en uppräkningstyp (eller använda en befintlig uppräkningstyp) som anger de giltiga värdena. Sedan Använd uppräkningstypen för att skapa en parameter av den typen.

- Lägg till den **ValidateSet** attributet Parameterdeklarationen. Läs mer om det här attributet [ValidateSet attributet deklarationen](./validateset-attribute-declaration.md).

#### <a name="use-standard-types-for-parameters"></a>Använd Standard typer för parametrar

Använda standard typer för parametrar för att säkerställa konsekvens med andra cmdlet: ar, där ända möjligt. Läs mer om vilka typer som ska användas för olika parametern [Standard Cmdlet parameternamn och typer](./standard-cmdlet-parameter-names-and-types.md). Det här avsnittet innehåller länkar till flera avsnitt som beskriver namn och .NET Framework-typer för grupper av standard parametrar, till exempel ”aktivitetsparametrar”.

#### <a name="use-strongly-typed-net-framework-types"></a>Använda starkt typifierade .NET Framework-typer

Parametrar ska definieras som .NET Framework-typer för att ge bättre parameterverifieringen. Till exempel ska parametrar som är begränsad till ett värde från en uppsättning värden vara definierat som en uppräkningstyp. För ett värde för ID: T URI (Uniform Resource) måste definiera parametern som ett [System.Uri](/dotnet/api/System.Uri) typen. Undvik grundläggande strängparametrar för allt utom friformsarbetsyta textegenskaper.

#### <a name="use-consistent-parameter-types"></a>Använd konsekvent parametertyper

När samma parameter används av flera cmdlets, Använd alltid samma parametertypen.  Till exempel om den `Process` parametern är en [System.Int16](/dotnet/api/System.Int16) skriver för en cmdlet, ska du inte göra den `Process` parameter för en annan cmdlet en [System.Uint16](/dotnet/api/System.UInt16) typen.

#### <a name="parameters-that-take-true-and-false"></a>Parametrar som tar värdet är True och False

Om parametern tar endast `true` och `false`, definiera parametern som typen [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter). En växlingsparametern behandlas som `true` när det anges i ett kommando. Om parametern inte ingår i ett kommando, Windows PowerShell tar hänsyn till värdet för parametern ska vara `false`. Definiera inte booleskt parametrar.

Om parametern måste skilja mellan 3 värden: $true, $false och ”okänt”, sedan definierar en parameter av typen kan ha värdet null\<bool >.  Behovet av en 3, ”okänt” värde uppstår vanligen när cmdlet: en kan ändra en boolesk egenskap för ett objekt. I det här fallet ”okänt” innebär att inte ändra det aktuella värdet för egenskapen.

#### <a name="support-arrays-for-parameters"></a>Stöd för matriser för parametrar

Användare måste ofta kan utföra samma åtgärd mot flera argument. Dessa användare bör en cmdlet accepterar en matris som parameter som indata så att en användare kan skicka argumenten till parametern som en Windows PowerShell-variabel. Till exempel den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet: en använder en matris för strängar som identifierar namnen på processerna som ska hämtas.

#### <a name="support-the-passthru-parameter"></a>Stöd för PassThru-parametern

Som standard många cmdletar som ändrar systemet, till exempel den [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet, fungerar som ”mottagare” för objekt och inte returnerar ett resultat. Dessa cmdlet: en ska implementera den `PassThru` parameter för att tvinga cmdlet för att returnera ett-objekt. När den `PassThru` parameter har angetts, cmdleten returnerar ett objekt med hjälp av ett anrop till den [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metod. Följande kommando stoppar Calc-processen och skickar den resulterande processen till transportledningen.

```powershell
Stop-Process calc -passthru
```

I de flesta fall Lägg till, uppsättning och nya cmdlets ska ha stöd för en `PassThru` parametern.

#### <a name="support-parameter-sets"></a>Stöd för parameteruppsättningar

En cmdlet är avsedd att göra ett enda syfte. Det finns dock ofta flera olika sätt att beskriva det eller åtgärdsmål. Till exempel kan en process identifieras av dess namn, dess identifierare eller ett processobjekt. Cmdlet: en ska ha stöd för alla rimliga framställningar av dess mål. Normalt sett uppfyller det här kravet genom att ange uppsättningar med parametrar som (kallas parameteruppsättningar) som fungerar tillsammans med cmdlet: en. En parameter kan höra till valfritt antal parameteruppsättningar. Läs mer om parameteruppsättningar [cmdlet: en Parameter anger](./cmdlet-parameter-sets.md).

När du anger parameteruppsättningar, ange endast en parameter i inställt ValueFromPipeline. Mer information om hur du deklarera den **parametern** attributet, se [ParameterAttribute deklarationen](./parameter-attribute-declaration.md).

När parameteruppsättningar används standard-parameteruppsättningen definieras av den **Cmdlet** attribut. Standard-parameteruppsättningen ska innehålla parametrarna som sannolikt kommer att användas i en interaktiv Windows PowerShell-session. Mer information om hur du deklarera den **Cmdlet** attributet, se [CmdletAttribute deklarationen](./cmdlet-attribute-declaration.md).

### <a name="provide-feedback-to-the-user-sd04"></a>Ge Feedback till användaren (SD04)

Använd riktlinjer i det här avsnittet för att ge feedback till användaren. Denna feedback gör att användaren ska vara medveten om vad som händer i systemet och fatta bättre administrativ.

Windows PowerShell-runtime gör att användaren kan ange hur du hanterar utdata från varje anrop till den `Write` metoden genom att ange en inställningsvariabeln. Användaren kan ange flera inställningsvariabler, inklusive en variabel som avgör om systemet ska visa information och en variabel som avgör huruvida systemet ska fråga användaren innan du vidtar ytterligare åtgärder.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>Stöd för WriteWarning, WriteVerbose och WriteDebug metoder

En cmdlet ska anropa den [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metod när cmdleten ska utföra en åtgärd som kan ha ett oönskade resultat. En cmdlet ska anropa den här metoden om cmdlet: en är att skriva över en skrivskyddad fil.

En cmdlet ska anropa den [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metod när användaren kräver detalj diskutera vad cmdleten gör. En cmdlet ska anropa den här informationen om cmdleten författaren anser att det finns scenarier som kan kräva mer information om vad cmdleten gör.

Cmdlet: en ska anropa den [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metod när en utvecklare eller produkten supporttekniker måste förstå vad har skadat cmdlet igen. Det är inte nödvändigt för cmdleten att anropa den [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) -metod i samma kod som anropar den [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metod eftersom den `Debug` parametern anger båda uppsättningarna information.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>Stöd för WriteProgress för åtgärder som tar lång tid

Cmdlet-åtgärder som tar lång tid att slutföra och som inte kan köras i bakgrunden ska ha stöd för statusrapportering via periodiska anrop till den [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) metod.

#### <a name="use-the-host-interfaces"></a>Använd värd-gränssnitt

Ibland kan en cmdlet måste kommunicera direkt med användare i stället för med hjälp av de olika skriva eller bör metoder som stöds av den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klass. I så fall cmdlet: en måste härledas från den [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klassen och använda den [System.Management.Automation.PSCmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) egenskapen. Den här egenskapen stöder olika nivåer av typen av kommunikation, inklusive PromptForChoice, fråga och WriteLine/ReadLine-typer. Högst viss nivå finns även sätt att läsa och skriva enskilda nycklar och hantera buffertar.

Om inte en cmdlet är speciellt utformad för att generera ett grafiskt användargränssnitt (GUI), bör det inte kringgå värden med hjälp av den [System.Management.Automation.PSCmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) egenskapen. Ett exempel på en cmdlet som har utformats för att generera ett grafiskt användargränssnitt är den [Out GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) cmdlet.

> [!NOTE]
> Cmdlet: ar bör inte använda den [System.Console](/dotnet/api/System.Console) API.

### <a name="create-a-cmdlet-help-file-sd05"></a>Skapa en Cmdlet-hjälpavsnitten-fil (SD05)

Skapa en Help.xml-fil som innehåller information om cmdlet: en för varje cmdlet-sammansättningen. Denna information innehåller en beskrivning av cmdlet, beskrivningar av cmdletens parametrar, exempel på cmdletens användning och mycket mer.

## <a name="code-guidelines"></a>Riktlinjer för kod

Följande riktlinjer ska följas när kodning cmdletar för att säkerställa en konsekvent användarupplevelse mellan att använda dina cmdlets och andra cmdlet: ar. När du har hittat en kod riktlinje som gäller för din situation bör du titta på designriktlinjer för liknande riktlinjer.

### <a name="coding-parameters-sc01"></a>Koda parametrar (SC01)

Definiera en parameter genom att deklarera en offentlig egenskap för cmdlet-klassen som innehåller den **parametern** attribut. Parametrar behöver inte vara statiska medlemmar i den härledda klassen för .NET Framework för cmdleten. Mer information om hur du deklarera den **parametern** attributet, se [parameterdeklaration för attributet](./parameter-attribute-declaration.md).

#### <a name="support-windows-powershell-paths"></a>Stöd för Windows PowerShell-sökvägar

Windows PowerShell-sökvägen är en mekanism för normaliserar åtkomst till namnområden. När du tilldelar en Windows PowerShell-sökväg till en parameter i cmdleten, kan användaren definiera en anpassad ”enhet” som fungerar som en genväg till en specifik sökväg. När en användare anger enheten, kan du använda lagrade data, till exempel data i registret på ett konsekvent sätt.

Om cmdlet: tillåter att användaren anger en fil eller en datakälla kan den bör definiera en parameter av typen [System.String](/dotnet/api/System.String). Om flera enheter stöds, ska typen vara en matris. Namnet på parametern bör vara `Path`, med ett alias för `PSPath`. Dessutom kan den `Path` parametern ska ha stöd för jokertecken. Om stöd för jokertecken inte är obligatoriskt, definiera en `LiteralPath` parametern.

Om de data som cmdleten läser eller skriver måste vara en fil, cmdleten ska ta emot indata för Windows PowerShell-sökväg och cmdlet: en ska använda den [System.Management.Automation.Sessionstate.Path](/dotnet/api/System.Management.Automation.SessionState.Path) egenskapen att översätta i Windows PowerShell-sökvägar till sökvägar som filsystemet känner igen. Specifika mekanismer är följande:

- [System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Om de data som cmdleten läser eller skriver är endast en uppsättning strängar i stället för en fil, cmdleten ska använda providern innehållsinformationen (`Content` medlem) att läsa och skriva. Den här informationen hämtas från den [System.Management.Automation.Provider.CmdletProvider.InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) egenskapen. Dessa mekanismer kan andra datalager att delta i läsning och skrivning av data.

#### <a name="support-wildcard-characters"></a>Stöd för jokertecken

En cmdlet ska ha stöd för jokertecken om möjligt. Stöd för jokertecken inträffar på olika ställen i en cmdlet (särskilt när en parameter tar en sträng att identifiera ett objekt från en uppsättning objekt). Till exempel exemplet **stoppa Proc** cmdlet från den [StopProc självstudien](./stopproc-tutorial.md) definierar en `Name` parameter för att hantera strängar som representerar processnamn. Den här parametern har stöd för jokertecken så att du enkelt kan ange processer för att stoppa.

Om har stöd för jokertecken tecken är tillgänglig, en cmdlet-åtgärd ger vanligtvis en matris. Ibland kan det inte meningsfullt att stödja en matris eftersom användaren kan använda endast en post i taget. Till exempel den [Set-Location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) cmdlet inte behöver stöd för en matris eftersom användaren kan du ställa en enda plats. Cmdlet: en har fortfarande stöd för jokertecken i den här instansen, men tvingas av lösningen till en enda plats.

Läs mer om jokertecknet mönster [stöd för jokertecken i Cmdlet-parametrarna](./supporting-wildcard-characters-in-cmdlet-parameters.md).

#### <a name="defining-objects"></a>Hur du definierar objekt

Det här avsnittet innehåller riktlinjer för att definiera objekt för cmdletar och för att utöka befintliga objekt.

##### <a name="define-standard-members"></a>Definiera standardmedlemmar

Definiera standard medlemmar för att utöka en objekttyp i en anpassad Types.ps1xml-fil (Använd Windows PowerShell Types.ps1xml-filen som en mall). Standardmedlemmar definieras av en nod med namnet PSStandardMembers. Dessa definitioner kan andra cmdlet: ar och Windows PowerShell-körning för att arbeta med dina objekt i ett konsekvent sätt.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>Definiera ObjectMembers som ska användas som parametrar

Om du designar ett objekt för en cmdlet, kontrollerar du att medlemmarna mappas direkt till parametrarna för cmdletarna som kommer att använda den. Den här mappningen innebär att objektet enkelt skickas till pipelinen och som ska skickas från en cmdlet till en annan.

Redan befintliga .NET Framework-objekt som returneras av cmdlet: ar saknar ofta vissa viktiga eller praktiskt medlemmar som krävs av skriptutvecklare eller användare. Dessa saknas medlemmar kan vara särskilt viktigt för visning och för att skapa rätt medlemmen namn så att objektet korrekt kan skickas till pipelinen. Skapa en anpassad Types.ps1xml-fil för att dokumentera dessa tillämpliga medlemmar. När du skapar den här filen, rekommenderar vi följande namngivningskonvention: *< Your_Product_Name >*. Types.ps1xml.

Exempelvis kan du lägga till en `Mode` skript som den [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) Skriv för att visa attribut för en fil tydligare. Dessutom kan du lägga till en `Count` alias-egenskap enligt den [System.Array](/dotnet/api/System.Array) typ som tillåter konsekvent användning av det egenskapsnamnet (i stället för `Length`).

##### <a name="implement-the-icomparable-interface"></a>Implementera gränssnittet IComparable

Implementera en [System.IComparable](/dotnet/api/System.IComparable) gränssnittet på alla objekt som utdata. På så sätt kan utdata objekt som ska skickas enkelt olika cmdletar för sortering och analys.

##### <a name="update-display-information"></a>Uppdatera visningsinformation

Om visningen för ett objekt inte tillhandahåller de förväntade resultaten, skapa en anpassad  *\<YourProductName >*. Format.ps1xml fil för objektet.

### <a name="support-well-defined-pipeline-input-sc02"></a>Stöd för väldefinierade Pipeline-indata (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>Implementera för mitten av en Pipeline

Implementera en cmdlet förutsatt att den anropas från mitten av en pipeline (det vill säga andra cmdletar kommer producerar indata eller använda dess utdata). Du kan till exempel förutsätts att den `Get-Process` cmdlet, eftersom den genererar data, används endast som den första cmdlet: i en pipeline. Eftersom denna cmdlet är utformat för mitten av en pipeline, kan denna cmdlet dock tidigare cmdletar eller data i pipeline för att ange processerna som ska hämtas.

#### <a name="support-input-from-the-pipeline"></a>Stöd för indata från Pipeline

På varje parameter som angetts för en cmdlet, innehåller minst en parameter som har stöd för indata från pipeline. Stöd för pipeline-indata används att hämta data eller objekt att skicka dem till rätt parameteruppsättningen och skickar resultaten direkt till en cmdlet.

En parameter godkänner indata från pipelinen om den **parametern** attribut innehåller den `ValueFromPipeline` nyckelord, den `ValueFromPipelineByPropertyName` nyckelordet attributet eller båda nyckelord i dess deklaration. Om ingen av parametrarna i en parameter anger stöd i `ValueFromPipeline` eller `ValueFromPipelineByPropertyName` nyckelord, cmdleten meningsfullt kan inte placeras efter en annan cmdlet eftersom det kommer att ignorera alla indata från pipeline.

#### <a name="support-the-processrecord-method"></a>Stöd för metoden ProcessRecord

För att godkänna alla poster från den föregående cmdleten i pipelinen, din cmdlet måste implementera de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod. Windows PowerShell anropar den här metoden flera gånger, en gång för varje post som skickas till din cmdlet.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Skriva enskild poster till pipelinen (SC03)

När en cmdlet returnerar objekt, cmdleten ska skriva objekten direkt när de skapas. Cmdlet: en ska inte innehålla dem för att buffra dem till en kombinerad matris. De cmdletar som tar emot objekt som indata kommer sedan att kunna bearbeta, visa, eller bearbeta och visa utdata-objekt utan fördröjning. En cmdlet som genererar utdata objekt i taget ska anropa den [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metod. En cmdlet som genererar utdata-objekt i batchar (till exempel eftersom en underliggande API: T returnerar en matris med objekt i utdata) ska anropa den [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metoden med dess andra parameter ange att `true`.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Kontrollera cmdletarna skiftlägeskänsliga och bevara (SC04)

Som standard inte själva Windows PowerShell är skiftlägeskänslig. Men eftersom den behandlar många befintliga system, bevarar Windows PowerShell fall för att underlätta av åtgärden och kompatibilitet. Med andra ord, om ett tecken anges med versaler håller Windows PowerShell den med versaler. För system för att fungera, måste en cmdlet följer denna konvention. Den bör om möjligt att fungera på ett skiftlägesokänsligt sätt. Det bör dock bevara det ursprungliga skiftläget för cmdletar som inträffar senare i ett kommando eller i pipelinen.

## <a name="see-also"></a>Se även

[Riktlinjer för nödvändiga utveckling](./required-development-guidelines.md)

[Riktlinjer för rådgivande utveckling](./advisory-development-guidelines.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
