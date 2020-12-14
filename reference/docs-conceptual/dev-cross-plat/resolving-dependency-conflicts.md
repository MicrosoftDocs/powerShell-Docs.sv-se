---
title: Lösa beroende konflikter i PowerShell-modulens sammansättning
description: När du skriver en binär PowerShell-modul i C#, är det naturligt att ta beroenden på andra paket eller bibliotek för att tillhandahålla funktioner.
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 93bb39bdd440c7f97c27aa81e68f68331569b69e
ms.sourcegitcommit: 2fc6ee49a70bda4c59135136bd5cc7782836a124
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94810410"
---
# <a name="resolving-powershell-module-assembly-dependency-conflicts"></a>Lösa beroende konflikter i PowerShell-modulens sammansättning

När du skriver en binär PowerShell-modul i C#, är det naturligt att ta beroenden på andra paket eller bibliotek för att tillhandahålla funktioner. Att ta beroenden i andra bibliotek är önskvärt för åter användning av kod. PowerShell läser alltid in sammansättningar i samma kontext. Detta visar problem när en moduls beroenden står i konflikt med redan inlästa DLL-filer och kan förhindra att två i övrigt orelaterade moduler används i samma PowerShell-session.

Om du har fått det här problemet har du ett fel meddelande som liknar detta:

![Fel meddelande om sammansättnings läsnings konflikt](./media/resolving-dependency-conflicts/moduleconflict.png)

Den här artikeln beskriver några av de olika sätten att beroenden inträffar i PowerShell och metoder för att undvika problem som beror på beroende konflikter. Även om du inte är en moduls författare finns det några knep i här som kan hjälpa dig med beroende konflikter som inträffar i moduler som du använder.

## <a name="why-do-dependency-conflicts-occur"></a>Varför inträffar beroende konflikter?

I .NET uppstår beroende konflikter när två versioner av samma sammansättning läses in i samma _sammansättning för sammansättnings belastning_. Den här termen innebär något annorlunda på olika .NET-plattformar, vilket beskrivs [senare](#powershell-and-net). Den här konflikten är ett vanligt problem som inträffar i program vara där versions beroenden används. Eftersom det inte finns några enkla lösningar, och eftersom många ramverk för beroende lösningar försöker lösa problemet på olika sätt, kallas den här situationen ofta "beroende Hell".

Konflikt problem sammanställs av det faktum att ett projekt nästan aldrig avsiktligt eller direkt är beroende av två versioner av samma beroende. I stället har projektet två eller flera beroenden som varje kräver en annan version av samma beroende.

Anta till exempel att ditt .NET-program, `DuckBuilder` , finns i två beroenden för att utföra delar av dess funktioner och ser ut så här:

![Två beroenden för DuckBuilder förlitar sig på olika versioner av Newtonsoft.Jspå](./media/resolving-dependency-conflicts/dep-conflict.jpg)

Eftersom `Contoso.ZipTools` `Fabrikam.FileHelpers` båda är beroende av olika versioner av `Newtonsoft.Json` , kan det finnas en beroende konflikt beroende på hur varje beroende har lästs in.

### <a name="conflicting-with-powershells-dependencies"></a>Konflikt med PowerShell-beroenden

I PowerShell förstoras det beroende konflikt problemet eftersom PowerShell-moduler och PowerShell: s egna beroenden läses in i samma delade kontext. Det innebär att PowerShell-motorn och alla inlästa PowerShell-moduler får inte ha motstridiga beroenden. Ett klassiskt exempel på detta är `Newtonsoft.Json` :

![FictionalTools-modulen är beroende av en nyare version av Newtonsoft.Jspå än PowerShell](./media/resolving-dependency-conflicts/engine-conflict.jpg)

I det här exemplet är modulen `FictionalTools` beroende av `Newtonsoft.Json` version `12.0.3` , som är en nyare version av `Newtonsoft.Json` än `11.0.2` de som levereras i PowerShell-exemplet.

> [!NOTE]
> Detta är ett exempel och PowerShell 7 levereras för närvarande med `Newtonsoft.Json 12.0.3` .

Eftersom modulen är beroende av en nyare version av sammansättningen, accepterar den inte versionen som redan har lästs in av PowerShell. Men eftersom PowerShell redan har läst in en version av sammansättningen kan modulen inte läsa in sin egen version med hjälp av den konventionella belastnings mekanismen.

### <a name="conflicting-with-another-modules-dependencies"></a>Konflikt med en annan moduls beroenden

Ett annat vanligt scenario i PowerShell är att en modul läses in som är beroende av en version av en sammansättning, och sedan läses en annan modul in senare som är beroende av en annan version av den sammansättningen.

Detta ser ofta ut så här:

![Två PowerShell-moduler kräver olika versioner av Microsoft. Extensions. logging-beroendet](./media/resolving-dependency-conflicts/mod-conflict.jpg)

I det här fallet `FictionalTools` kräver modulen en nyare version av `Microsoft.Extensions.Logging` än- `FilesystemManager` modulen.

Tänk dig att de här modulerna läser in sina beroenden genom att placera beroende sammansättningarna i samma katalog som rot modulens sammansättning. Detta gör att .NET kan läsa in dem implicit efter namn. Om vi kör PowerShell 7 (ovanpå .NET Core 3,1) kan vi läsa in och köra och `FictionalTools` sedan läsa in och köra `FilesystemManager` utan problem. Men om vi läser in och kör i en ny session, `FilesystemManager` `FictionalTools` hämtas vi `FileLoadException` från `FictionalTools` kommandot eftersom det kräver en nyare version av `Microsoft.Extensions.Logging` än den som lästs in.
`FictionalTools` Det går inte att läsa in den nödvändiga versionen eftersom en sammansättning med samma namn redan har lästs in.

## <a name="powershell-and-net"></a>PowerShell och .NET

PowerShell körs på .NET-plattformen. NET ansvarar för att lösa och läsa in sammansättnings beroenden, så vi måste förstå hur .NET fungerar här för att förstå beroende konflikter.

Vi måste också confront det faktum att olika versioner av PowerShell körs på olika .NET-implementeringar. I allmänhet körs PowerShell 5,1 och senare på .NET Framework, medan PowerShell 6 och senare körs på .NET Core. Dessa två implementeringar av .NET läser in och hanterar sammansättningar på olika sätt.
Det innebär att matchning av beroende konflikter kan variera beroende på den underliggande .NET-plattformen.

### <a name="assembly-load-contexts"></a>Sammansättnings inläsnings kontexter

I .NET är en _sammansättnings inläsnings kontext_ (ALC) som är ett körnings namn område där sammansättningar läses in. Sammansättningens namn måste vara unika. Det här konceptet gör att sammansättningar kan matchas unikt efter namn i varje ALC.

### <a name="assembly-reference-loading-in-net"></a>Sammansättnings referens inläsning i .NET

Semantiken vid sammansättnings inläsning är beroende av både .NET-implementeringen (.NET Core vs .NET Framework) och .NET-API: et som används för att läsa in en viss sammansättning. I stället för att gå in i detalj här finns det länkar i avsnittet [Ytterligare läsning](#further-reading) som går till detaljerad information om hur .net-sammansättnings inläsning fungerar i varje .net-implementering.

I den här artikeln kommer vi att se följande metoder:

- Implicit sammansättnings inläsning (effektivt `Assembly.Load(AssemblyName)` ) när .net försöker läsa in en sammansättning efter namn från en statisk sammansättnings referens i .NET-kod.
- `Assembly.LoadFrom()`, ett plugin-orienterat inläsnings-API som lägger till hanterare för att lösa beroenden för den inlästa DLL-filen. Den här metoden kan inte matcha beroenden på det sätt vi vill.
- `Assembly.LoadFile()`är ett grundläggande inläsnings-API avsett för att endast läsa in den sammansättning som är tillfrågad och hanterar inte några beroenden.

### <a name="differences-in-net-framework-vs-net-core"></a>Skillnader i .NET Framework vs .NET Core

Hur dessa API: er fungerar har ändrats på ett diskret sätt mellan .NET Core och .NET Framework, så det är värt att läsa igenom [länkarna](#further-reading)som ingår. Ett viktigt sätt är att sammansättnings inläsnings kontexter och andra metoder för sammansättnings upplösning har ändrats mellan .NET Framework och .NET Core.

I synnerhet har .NET Framework följande funktioner:

- Global Assembly Cache, för hela datorns sammansättnings upplösning
- Program domäner, som fungerar som aktiva sand boxar för sammansättnings isolering, men som även presenterar ett tävla med
- En begränsad sammansättnings modell för sammansättnings belastning, som beskrivs i djup [här](/dotnet/framework/deployment/best-practices-for-assembly-loading), som har en fast uppsättning sammansättnings inläsnings kontexter, var och en med sina egna beteenden:
  - Standard inläsnings kontexten, där sammansättningar läses in som standard
  - Inläsnings kontexten för inläsning av sammansättningar manuellt vid körning
  - Reflektions kontexten, för att på ett säkert sätt läsa in sammansättningar för att läsa deras metadata utan att köra dem
  - Mystiska annullerade att sammansättningar läses in med `Assembly.LoadFile(string path)` och `Assembly.Load(byte[] asmBytes)` bor i

.NET Core (och .NET 5 +) har ersatt denna komplexitet med en enklare modell:

- Ingen Global Assembly Cache. Programmen tar alla sina egna beroenden. Detta tar bort en extern faktor för beroende matchning i program, vilket gör att beroende matchning är mer skalbar.
  PowerShell, som plugin-värden, kan komplicera detta något för moduler. Dess beroenden i `$PSHOME` delas med alla moduler.
- Endast en program domän och ingen möjlighet att skapa nya. Tillämpnings programmets domän koncept underhålls i .NET Core rent för att vara det globala läget för .NET-processen.
- En ny, utöknings bar sammansättnings modell för sammansättning. Du kan få ett namn på sammansättnings matchning genom att placera den i en ny ALC. .NET Core-processer börjar med en enda standard-ALC där alla sammansättningar läses in. (förutom de som läses in med `Assembly.LoadFile(string)` och `Assembly.Load(byte[])` ), men processen kan skapa och definiera egna anpassade ALCs med en egen inläsnings logik. När en sammansättning läses in, läses den första ALC in i som ansvarar för att matcha dess beroenden. Detta skapar möjligheter att implementera kraftfulla .NET plugin-mekanismer.

I båda implementeringarna läses sammansättningar in Lazy. Det innebär att de läses in när en metod som kräver typen körs för första gången.

Här är till exempel två versioner av samma kod som läser in ett beroende vid olika tidpunkter.

Det första läser alltid in sitt beroende när `Program.GetRange()` anropas, eftersom beroende referensen finns i den här metoden:

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetRange(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library will be loaded when GetRange is run
                // because the dependency call occurs directly within the method
                DependencyApi.Use();
            }

            list.Add(i);
        }
        return list;
    }
}
```

Den andra kommer att ladda sitt beroende endast om `limit` parametern är 20 eller mer, på grund av intern indirigering via en metod:

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetNumbers(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library is only referenced within
                // the UseDependencyApi() method,
                // so will only be loaded when limit >= 20
                UseDependencyApi();
            }

            list.Add(i);
        }
        return list;
    }

    private static void UseDependencyApi()
    {
        // Once UseDependencyApi() is called, Dependency.Library is loaded
        DependencyApi.Use();
    }
}
```

Det här är en bra metod eftersom den minimerar minnet och fil systemet I/O och använder resurserna mer effektivt. Olycklig en sido effekt av detta är att vi inte vet att det inte går att läsa in sammansättningen förrän vi når kod Sök vägen som försöker läsa in sammansättningen.

Det kan också skapa ett tids villkor för inläsnings konflikter. Om två delar av samma program försöker läsa in olika versioner av samma sammansättning, beror den inlästa versionen på vilken kod Sök väg som körs först.

För PowerShell innebär detta att följande faktorer kan påverka en konflikt vid en sammansättnings belastning:

- Vilken modul lästes in först?
- Har kod Sök vägen som använder beroende biblioteket körts?
- Laddar PowerShell ett motstridigt beroende vid start eller bara under vissa kod Sök vägar?

## <a name="quick-fixes-and-their-limitations"></a>Snabb korrigeringar och deras begränsningar

I vissa fall är det möjligt att göra små justeringar i modulen och åtgärda saker med minimal ansträngning. Men dessa lösningar tenderar att komma med varningar. De kan användas för modulen, men de fungerar inte för alla moduler.

### <a name="change-your-dependency-version"></a>Ändra beroende version

Det enklaste sättet att undvika beroende konflikter är att samtycka till ett beroende. Detta kan vara möjligt när:

- Konflikten är ett direkt beroende av modulen och du styr versionen.
- Konflikten är med ett indirekt beroende, men du kan konfigurera dina direkta beroenden för att använda en fungerande indirekt beroende version.
- Du vet vilken version som är i konflikt och kan vara beroende av att den inte ändras.

`Newtonsoft.Json`Paketet är ett användbart exempel på det här förra scenariot. Detta är ett beroende av PowerShell 6 och senare och används inte i Windows PowerShell. Ett enkelt sätt att lösa versions konflikter är att ange den lägsta versionen av i `Newtonsoft.Json` de PowerShell-versioner som du vill använda som mål.

Till exempel PowerShell-6.2.6 och PowerShell 7.0.2 använder båda versioner för närvarande `Newtonsoft.Json` 12.0.3. För att skapa en modul som riktar in sig på Windows PowerShell, PowerShell 6 och PowerShell 7, riktar du till detta `Newtonsoft.Json 12.0.3` som ett beroende och inkluderar det i den inbyggda modulen. När modulen läses in i PowerShell 6 eller 7 har PowerShell- `Newtonsoft.Json` sammansättningen redan lästs in. Dessutom är det minst den version som krävs för din modul, så upplösningen lyckas. I Windows PowerShell finns inte sammansättningen redan i PowerShell. Därför läses den in från mappen module i stället.

När du riktar in ett konkret PowerShell-paket, till exempel `Microsoft.PowerShell.Sdk` eller `System.Management.Automation` , ska NuGet kunna lösa rätt beroende versioner som krävs. Det blir svårare att nå både Windows PowerShell och PowerShell 6 + eftersom du måste välja mellan att använda flera ramverk eller `PowerShellStandard.Library` .

Situationer där det inte går att fästa till en gemensam beroende version är:

- Konflikten är med ett indirekt beroende, och ingen av dina beroenden kan konfigureras för att använda en gemensam version.
- Den andra beroende versionen kommer förmodligen att ändras ofta, så det är bara en kortsiktig korrigering att lösa en gemensam version.

### <a name="add-an-assemblyresolve-event-handler-to-create-a-dynamic-binding-redirect"></a>Lägga till en händelse hanterare för AssemblyResolve för att skapa en dynamisk bindning för omdirigering

Ibland går det inte att ändra din egen beroende version eller så är den för svår. Ett annat alternativ är att konfigurera en dynamisk bindning för omdirigering genom att registrera en händelse hanterare för `AssemblyResolve` händelsen.

Som med en statisk omdirigering är punkten att tvinga alla konsumenter av ett beroende att använda samma faktiska sammansättning. Du kan avlyssna anrop för att läsa in beroendet och alltid omdirigera dem till den version som du vill använda.

Detta ser ut ungefär så här:

```csharp
// Register the event handler as early as you can in your code.
// A good option is to use the IModuleAssemblyInitializer interface
// that PowerShell provides to run code early on when your module is loaded.

// This class will be instantiated on module import and the OnImport() method run.
// Make sure that:
//  - the class is public
//  - the class has a public, parameterless constructor
//  - the class implements IModuleAssemblyInitializer
public class MyModuleInitializer : IModuleAssemblyInitializer
{
    public void OnImport()
    {
        AppDomain.CurrentDomain.AssemblyResolve += DependencyResolution.ResolveNewtonsoftJson;
    }
}

// Clean up the event handler when the the module is removed
// to prevent memory leaks.
//
// Like IModuleAssemblyInitializer, IModuleAssemblyCleanup allows
// you to register code to run when a module is removed (with Remove-Module).
// Make sure it is also public with a public parameterless contructor
// and implements IModuleAssemblyCleanup.
public class MyModuleCleanup : IModuleAssemblyCleanup
{
    public void OnRemove()
    {
        AppDomain.CurrentDomain.AssemblyResolve -= DependencyResolution.ResolveNewtonsoftJson;
    }
}

internal static class DependencyResolution
{
    private static readonly string s_modulePath = Path.GetDirectoryName(
        Assembly.GetExecutingAssembly().Location);

    public static Assembly ResolveNewtonsoftJson(object sender, ResolveEventArgs args)
    {
        // Parse the assembly name
        var assemblyName = new AssemblyName(args.Name);

        // We only want to handle the dependency we care about.
        // In this example it's Newtonsoft.Json.
        if (!assemblyName.Name.Equals("Newtonsoft.Json"))
        {
            return null;
        }

        // Generally the version of the dependency you want to load is the higher one,
        // since it's the most likely to be compatible with all dependent assemblies.
        // The logic here assumes our module always has the version we want to load.
        // Also note the use of Assembly.LoadFrom() here rather than Assembly.LoadFile().
        return Assembly.LoadFrom(Path.Combine(s_modulePath, "Newtonsoft.Json.dll"));
    }
}
```

Du kan tekniskt registrera en script block i PowerShell för att hantera en `AssemblyResolve` händelse, men:

- En `AssemblyResolve` händelse kan utlösas i en tråd, något som PowerShell inte kan hantera.
- Även om händelser hanteras i rätt tråd innebär PowerShell-koncepten att händelse hanterarens script block måste skrivas försiktigt för att inte vara beroende av variabler som definierats utanför den.

Det finns situationer där omdirigering till en gemensam version inte fungerar:

- När beroendet har gjort ändringar mellan versioner, eller när beroende kod är beroende av en funktion som annars inte är tillgänglig i den version som du omdirigerar till.
- När modulen inte har lästs in före det motstridiga beroendet. Om du registrerar en `AssemblyResolve` händelse hanterare efter att beroendet har lästs in utlöses den aldrig. Om du försöker förhindra beroende konflikter med en annan modul kan detta vara ett problem, eftersom den andra modulen kan läsas in först.

### <a name="use-the-dependency-out-of-process"></a>Använd beroendet av processen

Den här lösningen är mer för modul användare än för modulens författare. Detta är en lösning som ska användas när den är framgångs intensiv med en modul som inte fungerar på grund av en befintlig beroende konflikt.

Beroende konflikter inträffar eftersom två versioner av samma sammansättning läses in i samma .NET-process. En enkel lösning är att läsa in dem i olika processer, så länge du fortfarande kan använda funktionerna från båda.

I PowerShell finns det flera sätt att åstadkomma detta:

- Anropa PowerShell som under process

  Ett enkelt sätt att köra ett PowerShell-kommando från den aktuella processen är att bara starta en ny PowerShell-process direkt med kommando anropet:

  ```powershell
  pwsh -c 'Invoke-ConflictingCommand'
  ```

  Den huvudsakliga begränsningen här är att omstrukturering av resultatet kan vara ett trickier eller fler fel som är mer känsliga än andra alternativ.

- PowerShell-jobbet

  PowerShell-jobbet kör även kommandon som är utanför processen, genom att skicka kommandon till en ny PowerShell-process och returnera resultaten:

  ```powershell
  $result = Start-Job { Invoke-ConflictingCommand } | Receive-Job -Wait
  ```

  I det här fallet behöver du bara vara säker på att alla variabler och tillstånd skickas korrekt.

  Jobb systemet kan också vara något besvärligt när du kör små kommandon.

- PowerShell-fjärranvändning

  När det är tillgängligt kan PowerShell-fjärrkommunikation vara ett användbart sätt att köra kommandon från processen. Med fjärr kommunikation kan du skapa en ny **PSSession** i en ny process, anropa dess kommandon via PowerShell-fjärrkommunikation och sedan använda resultaten lokalt med de andra modulerna som innehåller de motstridiga beroendena.

  Ett exempel kan se ut så här:

  ```powershell
  # Create a local PowerShell session
  # where the module with conflicting assemblies will be loaded
  $s = New-PSSession

  # Import the module with the conflicting dependency via remoting,
  # exposing the commands locally
  Import-Module -PSSession $s -Name ConflictingModule

  # Run a command from the module with the conflicting dependencies
  Invoke-ConflictingCommand
  ```

- Implicit fjärr kommunikation till Windows PowerShell

  Ett annat alternativ i PowerShell 7 är att använda `-UseWindowsPowerShell` flaggan på `Import-Module` . Detta kommer att importera modulen via en lokal Remoting-session till Windows PowerShell:

  ```powershell
  Import-Module -Name ConflictingModule -UseWindowsPowerShell
  ```

  Tänk på att moduler kanske inte fungerar med eller fungerar annorlunda med Windows PowerShell.

#### <a name="when-out-of-process-invocation-should-not-be-used"></a>När en out-of-process-anrop inte ska användas

Som en modul skapar är kommando anrop utanför processen svårt att ta sig in i en modul och kan ha Edge-fall som orsakar problem. I synnerhet kanske fjärr kommunikation och jobb inte är tillgängliga i alla miljöer där modulen behöver fungera. Den allmänna principen för att flytta implementeringen utanför processen och tillåta PowerShell-modulen att vara en tunnare klient kan dock fortfarande användas.

Som en module-användare finns det fall där inaktiva anrop inte fungerar:

- När PowerShell-fjärrkommunikation inte är tillgängligt eftersom du inte har behörighet att använda den eller inte är aktive rad.
- När en viss .NET-typ krävs från utdata som indata till en metod eller ett annat kommando.
  Kommandon som körs via PowerShell-fjärrkommunikation genererar avserialiserade objekt i stället för .NET-objekt med starkt skriven. Det innebär att metod anrop och starkt skrivna API: er inte fungerar med utdata från kommandon som importer ATS via fjärr kommunikation.

## <a name="more-robust-solutions"></a>Robusta lösningar

De tidigare lösningarna hade alla scenarier och moduler som inte fungerar. De har dock också en relativt enkel att implementera på rätt sätt. Följande lösningar är mer robusta, men kräver mer ansträngning att implementera korrekt och kan införa diskreta buggar om de inte skrivs försiktigt.

### <a name="loading-through-net-core-assembly-load-contexts"></a>Inläsning via .NET Core Assembly load-kontexter

[Sammansättnings inläsnings kontexter](/dotnet/api/system.runtime.loader.assemblyloadcontext) (ALCs) som ett implementerat API introducerades i .net core 1,0 för att specifikt åtgärda behovet av att läsa in flera versioner av samma sammansättning i samma körnings miljö.

I .NET Core och .NET 5 erbjuder de den mest robusta lösningen till problem med att läsa in versioner av en sammansättning i konflikt. Anpassade ALCs är dock inte tillgängliga i .NET Framework. Det innebär att den här lösningen endast fungerar i PowerShell 6 och senare.

För närvarande är det bästa exemplet på att använda en ALC för beroende isolering i PowerShell i PowerShell-redigeraren, språk servern för PowerShell-tillägget för Visual Studio Code. En [ALC används](https://github.com/PowerShell/PowerShellEditorServices/blob/master/src/PowerShellEditorServices.Hosting/Internal/PsesLoadContext.cs) för att förhindra att PowerShell Editor-tjänsternas egna beroenden kolliderar med dem i PowerShell-moduler.

Implementering av underavsnitts beroende isolering med en ALC är konceptuellt svårt, men vi kommer att arbeta med ett minimalt exempel. Föreställ dig att vi har en enkel modul som endast är avsedd att fungera i PowerShell 7.
Käll koden organiseras på följande sätt:

```
+ AlcModule.psd1
+ src/
    + TestAlcModuleCommand.cs
    + AlcModule.csproj
```

Cmdlet-implementeringen ser ut så här:

```csharp
using Shared.Dependency;

namespace AlcModule
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            // Here's where our dependency gets used
            Dependency.Use();
            // Something trivial to make our cmdlet do *something*
            WriteObject("done!");
        }
    }
}
```

(Kraftigt förenklat) manifestet ser ut så här:

```powershell
@{
    Author = 'Me'
    ModuleVersion = '0.0.1'
    RootModule = 'AlcModule.dll'
    CmdletsToExport = @('Test-AlcModule')
    PowerShellVersion = '7.0'
}
```

Och `csproj` ser ut så här:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

När vi skapar den här modulen har genererade utdata följande layout:

```
AlcModule/
  + AlcModule.psd1
  + AlcModule.dll
  + Shared.Dependency.dll
```

I det här exemplet finns vårt problem i `Shared.Dependency.dll` sammansättningen, som är vår imaginära konflikt beroende. Detta är det beroende som vi behöver för att kunna placeras bakom en ALC så att vi kan använda den moduler-/regionsspecifika versionen.

Vi måste skapa en ny tekniker för modulen så att:

- Modulens beroenden läses bara in i vår anpassade ALC och inte till PowerShell: s ALC, så det kan finnas ingen konflikt. När vi lägger till fler beroenden i vårt projekt behöver vi dessutom inte lägga till mer kod kontinuerligt för att hålla inläsningen igång. I stället vill vi ha en återanvändbar, generisk lösning för matchning av beroenden.
- Inläsning av modulen fungerar fortfarande som normalt i PowerShell. -Cmdletar och andra typer som PowerShell-modulens system behöver definieras i PowerShell: s egna ALC.

För att tjänstassisterad de här två kraven måste vi dela upp vår modul i två sammansättningar:

- En cmdlets-sammansättning, `AlcModule.Cmdlets.dll` som innehåller definitioner av alla typer som PowerShell-Modulsystemet behöver för att läsa in vår modul korrekt. Nämligen alla implementeringar av `Cmdlet` Bask-klassen och den klass som implementerar `IModuleAssemblyInitializer` , som konfigurerar händelse hanteraren för `AssemblyLoadContext.Default.Resolving` att läsas in korrekt `AlcModule.Engine.dll` via vår anpassade ALC. Eftersom PowerShell 7 avsiktligt döljer typer som definierats i sammansättningar som lästs in i andra ALCs, måste alla typer som är avsedda att vara allmänt exponerade för PowerShell definieras här. Slutligen måste vår anpassade ALC-definition definieras i den här sammansättningen. Utöver det, så så liten kod som möjligt bör finnas i denna sammansättning.
- En motor sammansättning, `AlcModule.Engine.dll` som hanterar den faktiska implementeringen av modulen.
  Typer från detta är tillgängliga i PowerShell-ALC, men den läses in från början via vår anpassade ALC. Dess beroenden läses bara in i den anpassade ALC. Detta blir effektivt en _bro_ mellan de två ALCs.

Med det här bro fallet ser vårt nya sammansättnings scenario ut så här:

![Diagram som representerar AlcModule.Engine.dll bryggning av de två ALCs](./media/resolving-dependency-conflicts/alc-diagram.jpg)

För att se till att standard ALC för beroendet avsöknings logik inte löser beroenden som ska läsas in i den anpassade ALC, måste vi separera dessa två delar av modulen i olika kataloger. Den nya modulen layout har följande struktur:

```
AlcModule/
  AlcModule.Cmdlets.dll
  AlcModule.psd1
  Dependencies/
  | + AlcModule.Engine.dll
  | + Shared.Dependency.dll
```

För att se hur implementeringen ändras börjar vi med implementeringen av `AlcModule.Engine.dll` :

```csharp
using Shared.Dependency;

namespace AlcModule.Engine
{
    public class AlcEngine
    {
        public static void Use()
        {
            Dependency.Use();
        }
    }
}
```

Det här är en enkel behållare för beroendet, `Shared.Dependency.dll` men du bör tänka på det som .NET API för dina funktioner som cmdletarna i den andra sammansättnings omslutning för PowerShell.

Cmdleten `AlcModule.Cmdlets.dll` ser ut så här:

```csharp
// Reference our module's Engine implementation here
using AlcModule.Engine;

namespace AlcModule.Cmdlets
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            AlcEngine.Use();
            WriteObject("done!");
        }
    }
}
```

Om vi nu skulle läsa in **AlcModule** och köra `Test-AlcModule` , får vi en `FileNotFoundException` när standard-ALC försöker läsa in `Alc.Engine.dll` för att köra `EndProcessing()` . Detta är bra eftersom det innebär att standard-ALC inte kan hitta de beroenden som vi vill dölja.

Nu måste vi lägga till kod till `AlcModule.Cmdlets.dll` så att den vet hur man kan lösa det `AlcModule.Engine.dll` . Först måste vi definiera vår anpassade ALC som kommer att lösa sammansättningar från vår katalog för modulen `Dependencies` :

```csharp
namespace AlcModule.Cmdlets
{
    internal class AlcModuleAssemblyLoadContext : AssemblyLoadContext
    {
        private readonly string _dependencyDirPath;

        public AlcModuleAssemblyLoadContext(string dependencyDirPath)
        {
            _dependencyDirPath = dependencyDirPath;
        }

        protected override Assembly Load(AssemblyName assemblyName)
        {
            // We do the simple logic here of
            // looking for an assembly of the given name
            // in the configured dependency directory
            string assemblyPath = Path.Combine(
                _dependencyDirPath,
                $"{assemblyName.Name}.dll");

            // The ALC must use inherited methods to load assemblies
            // Assembly.Load*() won't work here
            return LoadFromAssemblyPath(assemblyPath);
        }
    }
}
```

Sedan måste vi koppla upp vår anpassade ALC till standard händelsen för ALC `Resolving` , vilket är ALC-versionen av `AssemblyResolve` händelsen i program domäner. Den här händelsen utlöses för att hitta `AlcModule.Engine.dll` när `EndProcessing()` anropas.

```csharp
namespace AlcModule.Cmdlets
{
    public class AlcModuleResolveEventHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // Get the path of the dependency directory.
        // In this case we find it relative to the AlcModule.Cmdlets.dll location
        private static readonly string s_dependencyDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        private static readonly AlcModuleAssemblyLoadContext s_dependencyAlc = new AlcModuleAssemblyLoadContext(s_dependencyDirPath);

        public void OnImport()
        {
            // Add the Resolving event handler here
            AssemblyLoadContext.Default.Resolving += ResolveAlcEngine;
        }

        public void OnRemove()
        {
          // Remove the Resolving event handler here
          AssemblyLoadContext.Default.Resolving -= ResolveAlcEngine;
        }

        private static Assembly ResolveAlcEngine(
            AssemblyLoadContext defaultAlc,
            AssemblyName assemblyToResolve)
        {
            // We only want to resolve the Alc.Engine.dll assembly here.
            // Because this will be loaded into the custom ALC,
            // all of *its* dependencies will be resolved
            // by the logic we defined for that ALC's implementation.
            //
            // Note that we are safe in our assumption that the name is enough
            // to distinguish our assembly here,
            // since it's unique to our module.
            // There should be no other AlcModule.Engine.dll on the system.
            if (!assemblyToResolve.Name.Equals("AlcModule.Engine"))
            {
                return null;
            }

            // Allow our ALC to handle the directory discovery concept
            //
            // This is where Alc.Engine.dll is loaded into our custom ALC
            // and then passed through into PowerShell's ALC,
            // becoming the bridge between both
            return s_dependencyAlc.LoadFromAssemblyName(assemblyToResolve);
        }
    }
}
```

Med den nya implementeringen tar du en titt på sekvensen av anrop som inträffar när modulen läses in och `Test-AlcModule` körs:

![Sekvens diagram över anrop med hjälp av den anpassade ALC för att läsa in beroenden](./media/resolving-dependency-conflicts/alc-sequence.png)

Några intressanta punkter är:

- `IModuleAssemblyInitializer`Körs först när modulen läser in och anger `Resolving` händelsen.
- Vi läser inte in beroenden förrän körs `Test-AlcModule` och dess `EndProcessing()` metod anropas.
- När `EndProcessing()` anropas, kan inte standard-ALC hitta `AlcModule.Engine.dll` och Utlös `Resolving` händelsen.
- Vår händelse hanterare kopplar upp den anpassade ALC till standardvärdet för ALC och inläsningar `AlcModule.Engine.dll` .
- När `AlcEngine.Use()` anropas i används `AlcModule.Engine.dll` den anpassade ALC igen för att lösa problemet `Shared.Dependency.dll` . Mer specifikt laddar den alltid  `Shared.Dependency.dll` ut eftersom den aldrig står i konflikt med något i standard-ALC och bara ser ut i vår `Dependencies` katalog.

Genom att sätta samman implementeringen ser vår nya källkod ut så här:

```
+ AlcModule.psd1
+ src/
  + AlcModule.Cmdlets/
  | + AlcModule.Cmdlets.csproj
  | + TestAlcModuleCommand.cs
  | + AlcModuleAssemblyLoadContext.cs
  | + AlcModuleInitializer.cs
  |
  + AlcModule.Engine/
  | + AlcModule.Engine.csproj
  | + AlcEngine.cs
```

AlcModule. cmdlets. CSPROJ ser ut så här:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <ProjectReference Include="..\AlcModule.Engine\AlcModule.Engine.csproj" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

AlcModule. Engine. CSPROJ ser ut så här:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
  </ItemGroup>
</Project>
```

Så när vi bygger modulen är vår strategi:

- Konstruktion `AlcModule.Engine`
- Konstruktion `AlcModule.Cmdlets`
- Kopiera allt från `AlcModule.Engine` till `Dependencies` katalogen och kom ihåg vad vi kopierade
- Kopiera allt från `AlcModule.Cmdlets` det som inte fanns i `AlcModule.Engine` Bask module-katalogen

Eftersom modulens layout här är så viktigt att beroendet skiljs åt är det ett build-skript som ska användas från käll roten:

```powershell
param(
    # The .NET build configuration
    [ValidateSet('Debug', 'Release')]
    [string]
    $Configuration = 'Debug'
)

# Convenient reusable constants
$mod = "AlcModule"
$netcore = "netcoreapp3.1"
$copyExtensions = @('.dll', '.pdb')

# Source code locations
$src = "$PSScriptRoot/src"
$engineSrc = "$src/$mod.Engine"
$cmdletsSrc = "$src/$mod.Cmdlets"

# Generated output locations
$outDir = "$PSScriptRoot/out/$mod"
$outDeps = "$outDir/Dependencies"

# Build AlcModule.Engine
Push-Location $engineSrc
dotnet publish -c $Configuration
Pop-Location

# Build AlcModule.Cmdlets
Push-Location $cmdletsSrc
dotnet publish -c $Configuration
Pop-Location

# Ensure out directory exists and is clean
Remove-Item -Path $outDir -Recurse -ErrorAction Ignore
New-Item -Path $outDir -ItemType Directory
New-Item -Path $outDeps -ItemType Directory

# Copy manifest
Copy-Item -Path "$PSScriptRoot/$mod.psd1"

# Copy each Engine asset and remember it
$deps = [System.Collections.Generic.Hashtable[string]]::new()
Get-ChildItem -Path "$engineSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { $_.Extension -in $copyExtensions } |
    ForEach-Object { [void]$deps.Add($_.Name); Copy-Item -Path $_.FullName -Destination $outDeps }

# Now copy each Cmdlets asset, not taking any found in Engine
Get-ChildItem -Path "$cmdletsSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { -not $deps.Contains($_.Name) -and $_.Extension -in $copyExtensions } |
    ForEach-Object { Copy-Item -Path $_.FullName -Destination $outDir }
```

Slutligen har vi ett allmänt sätt att använda en sammansättnings inläsnings kontext för att isolera vår moduls beroenden som är stabila med tiden när fler beroenden läggs till.

För ett mer detaljerat exempel går du till den här [GitHub-lagringsplatsen](https://github.com/rjmholt/ModuleDependencyIsolationExample). Det här exemplet visar hur du migrerar en modul för att använda en ALC, samtidigt som modulen fungerar i .NET Framework. Det visar också hur du använder .NET standard och PowerShell standard för att förenkla kärn implementeringen.

### <a name="assembly-resolve-handler-for-side-by-side-loading-with-assemblyloadfile"></a>Sammansättnings lösa hanterare för inläsning sida vid sida med `Assembly.LoadFile()`

En annan, eventuellt enklare, metod för att få en sammansättning sida vid sida är att koppla upp en `AssemblyResolve` händelse till `Assembly.LoadFile()` . Användningen `Assembly.LoadFile()` av har fördelen att vara den enklaste lösningen att implementera och fungerar med både .net Core och .NET Framework.

För att kunna visa detta tar vi en titt på ett snabbt exempel på en implementering som kombinerar idéer från vårt dynamiska bindnings exempel för omdirigering och sammansättnings exemplet för sammansättnings inläsning ovan.

Vi anropar den här modulen **LoadFileModule**, som har ett trivial-kommando `Test-LoadFile [-Path] <path>` . Den här modulen tar ett beroende på `CsvHelper` sammansättningen (version 15.0.5).

Precis som med ALC-modulen måste vi först dela upp modulen i två delar.

Den första delen utför den faktiska implementeringen `LoadFileModule.Engine` :

```csharp
using CsvHelper;

namespace LoadFileModule.Engine
{
    public class Runner
    {
        public void Use(string path)
        {
            // Here's where we use the CsvHelper dependency
            using (var reader = new StreamReader(path))
            using (var csvReader = new CsvReader(reader, CultureInfo.InvariantCulture))
            {
                // Imagine we do something useful here...
            }
        }
    }
}
```

Den andra delen är vad PowerShell läser in direkt `LoadFileModule.Cmdlets` . Vi använder en strategi som liknar ALC-modulen, där vi isolerar beroenden i en separat katalog. Men den här gången läser vi in alla sammansättningar i med en lös händelse i stället för bara `LoadFileModule.Engine.dll` .

```csharp
using LoadFileModule.Engine;

namespace LoadFileModule.Cmdlets
{
    // Actual cmdlet definition
    [Cmdlet(VerbsDiagnostic.Test, "LoadFile")]
    public class TestLoadFileCommand : Cmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        protected override void EndProcessing()
        {
            // Here's where we use LoadFileModule.Engine
            new Runner().Use(Path);
        }
    }

    // This class controls our dependency resolution
    public class ModuleContextHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // We catalog our dependencies here to ensure we don't load anything else
        private static IReadOnlyDictionary<string, int> s_dependencies = new Dictionary<string, int>
        {
            { "CsvHelper", 15 },
        };

        // Set up the path to our dependency directory within the module
        private static string s_dependenciesDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        // This makes sure we only try to resolve dependencies when the module is loaded
        private static bool s_engineLoaded = false;

        public void OnImport()
          {
            // Set up our event when the module is loaded
            AppDomain.CurrentDomain.AssemblyResolve += HandleResolveEvent;
        }

        public void OnRemove(PSModuleInfo psModuleInfo)
        {
            // Unset the event when the module is unloaded
            AppDomain.CurrentDomain.AssemblyResolve -= HandleResolveEvent;
        }

        private static Assembly HandleResolveEvent(object sender, ResolveEventArgs args)
        {
            var asmName = new AssemblyName(args.Name);

            // First we want to know if this is the top-level assembly
            if (asmName.Name.Equals("LoadFileModule.Engine"))
            {
                s_engineLoaded = true;
                return Assembly.LoadFile(Path.Combine(s_dependenciesDirPath, "Unrelated.Engine.dll"));
            }

            // Otherwise, if that assembly has been loaded, we must try to resolve its dependencies too
            if (s_engineLoaded
                && s_dependencies.TryGetValue(asmName.Name, out int requiredMajorVersion)
                && asmName.Version.Major == requiredMajorVersion)
            {
                string asmPath = Path.Combine(s_dependenciesDirPath, $"{asmName.Name}.dll");
                return Assembly.LoadFile(asmPath);
            }

            return null;
        }
    }
}
```

Slutligen liknar layouten för modulen också ALC-modulen:

```
LoadFileModule/
  + LoadFileModule.Cmdlets.dll
  + LoadFileModule.psd1
  + Dependencies/
  |  + LoadFileModule.Engine.dll
  |  + CsvHelper.dll
```

Med den här strukturen har **LoadFileModule** nu stöd för att läsas in tillsammans med andra moduler med ett beroende av **CsvHelper**.

Eftersom vår hanterare gäller för **alla** `AssemblyResolve` händelser i program domänen måste vi göra några specifika design alternativ här:

- För att begränsa fönstret där vår händelse kan störa annan inläsning börjar vi bara hantera allmän beroende inläsning efter `LoadFileModule.Engine.dll` har lästs in.
- Vi push `LoadFileModule.Engine.dll` -överför till katalogen med beroenden, så att den läses in av ett `LoadFile()` samtal i stället för PowerShell. Det innebär att den egna beroende inläsningen alltid höjer en `AssemblyResolve` händelse, även om ett annat `CsvHelper.dll` (till exempel) läses in i PowerShell.
  Det ger oss möjlighet att hitta rätt beroende.
- Eftersom vi bara måste matcha de olika beroendena för vår modul tvingas vi att koda en ord lista med beroende namn och versioner till vår hanterare. I vårt särskilda fall skulle det vara möjligt att använda `ResolveEventArgs.RequestingAssembly` egenskapen för att ta reda på om den `CsvHelper` begärs av vår modul. Men det fungerar inte för beroenden av beroenden. till exempel om `CsvHelper` en händelse aktive ras `AssemblyResolve` . Det finns andra, svårare sätt att göra detta, till exempel jämföra begärda sammansättningar med metadata för sammansättningar i `Dependencies` katalogen. I det här exemplet har vi gjort den här kontrollen mer utförligt för att både Markera problemet och förenkla exemplet.

Detta är den viktigaste skillnaden mellan `LoadFile()` strategin och ALC-strategin: `AssemblyResolve` händelsen måste betjäna alla belastningar i program domänen, vilket gör det mycket svårare att hålla vår beroende lösning att trasslar med andra moduler. Men bristen på ALCs i .NET Framework gör det här alternativet värdefullt att förstå.

### <a name="custom-application-domains"></a>Anpassade program domäner

Det sista och mest extrema alternativet för sammansättnings isolering är att använda anpassade program domäner.
Program domäner (används i plural) är endast tillgängliga i .NET Framework. De används för att tillhandahålla isolering i processen mellan delar av ett .NET-program. En av användnings områdena är att isolera sammansättnings belastningar från varandra i samma process.

Program domäner är dock gränser för serialisering. Objekt i en program domän kan inte refereras och användas direkt av objekt i en annan program domän. Du kan undvika detta genom att implementera `MarshalByRefObject` . Men när du inte styr typerna, vilket ofta är fallet med beroenden, är det inte möjligt att tvinga fram en implementering här. Den enda lösningen är att göra stora arkitektoniska ändringar. Serialiseringens gränser har också allvarliga prestanda konsekvenser.

Eftersom program domäner har denna allvarliga begränsning, är komplicerade att implementera och bara fungerar i .NET Framework, ger vi inget exempel på hur du kan använda dem här. Även om de är värda att nämnas som en möjlighet, är de inte rekommenderade.

Om du är intresse rad av att försöka använda en anpassad program domän kan följande länkar hjälpa dig:

- [Konceptuell dokumentation om program domäner](/dotnet/framework/app-domains/application-domains)
- [Exempel på användning av program domäner](/dotnet/framework/app-domains/use)

## <a name="solutions-for-dependency-conflicts-that-dont-work-for-powershell"></a>Lösningar för beroende konflikter som inte fungerar för PowerShell

Slutligen kommer vi att ta itu med några möjligheter som inträffar när du genomsöker .NET-beroende konflikter i .NET som kan se löfte, men vanligt vis inte fungerar för PowerShell.

Dessa lösningar har ett gemensamt tema som de är ändringar i distributions konfigurationen för en miljö där du styr programmet och eventuellt hela datorn. Dessa lösningar är riktade mot scenarier som webb servrar och andra program som distribueras till Server miljöer, där miljön är avsedd att vara värd för programmet och är kostnads fritt att konfigureras av distributions användaren. De brukar också vara mycket .NET Framework orienterade, vilket innebär att de inte fungerar med PowerShell 6 eller senare.

Om du vet att modulen endast används i Windows PowerShell 5,1-miljöer som du har total kontroll över, kan vissa av dessa alternativ vara. I allmänhet **bör moduler inte ändra globalt dator tillstånd som detta**. Den kan avbryta konfigurationer som orsakar problem i `powershell.exe` , andra moduler eller andra beroende program som orsakar att modulen kraschar på oväntade sätt.

### <a name="static-binding-redirect-with-appconfig-to-force-using-the-same-dependency-version"></a>Statisk bindning omdirigera med app.config för att framtvinga användning av samma beroende version

.NET Framework program kan dra nytta av en `app.config` fil för att konfigurera vissa av programmets beteenden i deklarativ form. Det går att skriva en `app.config` post som konfigurerar sammansättnings bindning för att omdirigera sammansättnings inläsning till en viss version.

Två problem med detta för PowerShell är:

- .NET Core stöder inte `app.config` , så den här lösningen gäller endast för `powershell.exe` .
- `powershell.exe` är ett delat program som finns i `System32` katalogen. Det är troligt att modulen inte kan ändra innehållet på många system. Även om det kan ändra det kan det `app.config` bryta en befintlig konfiguration eller påverka inläsningen av andra moduler.

### <a name="setting-codebase-with-appconfig"></a>Ange `codebase` med app.config

Av samma skäl kommer att försöka konfigurera `codebase` inställningen i `app.config` inte att fungera i PowerShell-moduler.

### <a name="installing-dependencies-to-the-global-assembly-cache-gac"></a>Installera beroenden i GAC (Global Assembly Cache)

Ett annat sätt att lösa beroende versions konflikter i .NET Framework är att installera beroenden till GAC, så att olika versioner kan läsas in sida vid sida från GAC.

För PowerShell-moduler är problemen här:

- Den globala sammansättningscachen gäller endast .NET Framework, så det här är inte hjälp i PowerShell 6 och senare.
- Att installera sammansättningar i GAC är en ändring av global dator status och kan orsaka sido effekter i andra program eller i andra moduler. Det kan också vara svårt att göra korrekt, även om modulen har de behörigheter som krävs. Att få IT-fel kan orsaka allvarliga, datorövergripande problem i andra .NET-program.

## <a name="further-reading"></a>Ytterligare läsning

Det finns mycket mer att läsa på .NET-sammansättning versions beroende konflikter. Här är några saker som är bra att säga:

- [.NET: sammansättningar i .NET](/dotnet/standard/assembly/)
- [.NET Core: algoritmen för inläsning av hanterad sammansättning](/dotnet/core/dependency-loading/loading-managed)
- [.NET Core: förstå system. Runtime. Loader. AssemblyLoadContext](/dotnet/core/dependency-loading/understanding-assemblyloadcontext)
- [.NET Core: diskussion om inläsnings lösningar sida vid sida](https://github.com/dotnet/runtime/issues/13471)
- [.NET Framework: omdirigering av sammansättnings versioner](/dotnet/framework/configure-apps/redirect-assembly-versions)
- [.NET Framework: metod tips för sammansättnings inläsning](/dotnet/framework/deployment/best-practices-for-assembly-loading)
- [.NET Framework: hur körningen hittar sammansättningar](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [.NET Framework: lös sammansättnings belastningar](/dotnet/standard/assembly/resolve-loads)
- [StackOverflow: sammansättnings bindning omdirigera, hur och varför?](https://stackoverflow.com/questions/43365736/assembly-binding-redirect-how-and-why)
- [PowerShell: diskussion om att implementera AssemblyLoadContexts](https://github.com/PowerShell/PowerShell/issues/11571)
- [PowerShell: `Assembly.LoadFile()` läses inte in i standard AssemblyLoadContext](https://github.com/PowerShell/PowerShell/issues/12052)
- [Rick-Strahl: när ett .NET-sammansättnings beroende hämtas läses in?](https://weblog.west-wind.com/posts/2012/Nov/03/Back-to-Basics-When-does-a-NET-Assembly-Dependency-get-loaded)
- [Jon Skeet: Sammanfattning av versions hantering i .NET](https://codeblog.jonskeet.uk/2019/06/30/versioning-limitations-in-net/)
- [Nate McMaster: djupgående att gå in i .NET Core-primitiver](https://natemcmaster.com/blog/2017/12/21/netcore-primitives/)
