---
description: Beskriver hur du använder metoder för att utföra åtgärder på objekt i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_methods?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Methods
ms.openlocfilehash: 25056ff8b3c0bc8828be1426463b2d087e23a131
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391008"
---
# <a name="about-methods"></a>Om metoder

## <a name="short-description"></a>Kort beskrivning
Beskriver hur du använder metoder för att utföra åtgärder på objekt i PowerShell.

## <a name="long-description"></a>Lång beskrivning

PowerShell använder objekt för att representera objekten i data lager eller datorns tillstånd. FileInfo-objekt representerar till exempel filerna i fil system enheter och ProcessInfo-objekt representerar processerna på datorn.

Objekt har egenskaper, som lagrar data om objektet och metoder som gör att du kan ändra objektet.

En "metod" är en uppsättning instruktioner som anger en åtgärd som du kan utföra på objektet. Objektet innehåller till exempel `FileInfo` `CopyTo` metoden som kopierar filen som `FileInfo` objektet representerar.

Använd cmdleten för att hämta metoder för ett objekt `Get-Member` . Använd dess **MemberType** -egenskap med värdet "Method". Följande kommando hämtar metoderna för process-objekt.

```powershell
Get-Process | Get-Member -MemberType Method
```

```Output
TypeName: System.Diagnostics.Process

Name                      MemberType Definition
----                      ---------- ----------
BeginErrorReadLine        Method     System.Void BeginErrorReadLine()
BeginOutputReadLine       Method     System.Void BeginOutputReadLine()
...
Kill                      Method     System.Void Kill()
Refresh                   Method     System.Void Refresh()
Start                     Method     bool Start()
ToString                  Method     string ToString()
WaitForExit               Method     bool WaitForExit(int milliseconds), ...
WaitForInputIdle          Method     bool WaitForInputIdle(int millisecon...
```

Om du vill utföra eller "anropa" en metod för ett objekt skriver du en punkt (.), metod namnet och en uppsättning parenteser (). Om metoden har argument, placerar du argument värden innanför parenteserna. Parenteserna krävs för varje metod anrop, även om det inte finns några argument. Om metoden tar flera argument ska de avgränsas med kommatecken.

Till exempel anropar följande kommando metoden Kill of processs för att avsluta Anteckningar-processen på datorn.

```powershell
$notepad = Get-Process notepad
$notepad.Kill()
```

Det här exemplet kan kortas ned genom att kombinera ovanstående instruktioner.

```powershell
(Get-Process Notepad).Kill()
```

`Get-Process`Kommandot omges av parenteser för att säkerställa att det körs innan Kill-metoden anropas. `Kill`Metoden anropas sedan på det returnerade `Process` objektet.

En annan mycket användbar metod är `Replace` metoden för strängar. `Replace`Metoden ersätter text i en sträng. I exemplet nedan kan punkt (.) placeras omedelbart efter slut citatet i strängen.

```powershell
'this is rocket science'.Replace('rocket', 'rock')
```

```Output
this is rock science
```

Som du ser i föregående exempel kan du anropa en metod för ett objekt som du får genom att använda ett kommando, ett objekt i en variabel eller något som resulterar i ett objekt (som en sträng i citat tecken).

Från och med PowerShell 4,0 stöds metod anrop med dynamiska metod namn.

### <a name="learning-about-methods"></a>Lär dig mer om metoder

Om du vill hitta definitioner för ett objekts metoder går du till hjälp avsnittet för objekt typen och letar efter dess metoder-sida. Till exempel beskriver följande sida metoder för process objekt [system. Diagnostics. process](/dotnet/api/system.diagnostics.process#methods).

Om du vill fastställa argumenten för en metod granskar du metod definitionen, som liknar syntax diagrammet för en PowerShell-cmdlet.

En metod definition kan ha en eller flera metod-signaturer, som liknar parameter uppsättningarna i PowerShell-cmdletar. Signaturerna visar alla giltiga format för kommandon för att anropa-metoden.

`CopyTo`Metoden för `FileInfo` klassen innehåller till exempel följande två signaturer för metoden:

```
    CopyTo(String destFileName)
    CopyTo(String destFileName, Boolean overwrite)
```

Den första metoden signaturen använder mål fil namnet (och en sökväg). I följande exempel används den första `CopyTo` metoden för att kopiera `Final.txt` filen till `C:\Bin` katalogen.

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt")
```

> [!NOTE]
> Till skillnad från PowerShell: s _argument_ läge körs objekt metoder i _uttrycks_ läge, som är ett pass-till-.NET Framework som PowerShell bygger på. I _uttrycks_ läge **bareword** argument (icke-citerade strängar) tillåts inte. Du kan se skillnaden när du använder en sökväg som parameter, jämfört med sökvägen som ett argument. Du kan läsa mer om tolknings lägen i [about_Parsing](about_Parsing.md)

Signaturen för den andra metoden tar ett mål fil namn och ett booleskt värde som avgör om mål filen ska skrivas över, om den redan finns.

I följande exempel används den andra `CopyTo` metoden för att kopiera `Final.txt` filen till `C:\Bin` katalogen och för att skriva över befintliga filer.

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt", $true)
```

### <a name="methods-of-scalar-objects-and-collections"></a>Metoder för skalära objekt och samlingar

Metoderna för ett ("skalär") objekt av en viss typ skiljer sig ofta från metoder för en samling objekt av samma typ.

Till exempel har varje process en `Kill` metod, men en samling processer har ingen Kill-metod.

Från och med PowerShell 3,0 försöker PowerShell förhindra skript fel som orsakas av olika metoder för skalära objekt och samlingar.

Om du skickar en samling, men begär en metod som bara finns på en("skalär") objekt, anropar PowerShell metoden på alla objekt i samlingen.

Om metoden finns på de enskilda objekten och i samlingen, anropas bara samlingens metod.

Den här funktionen fungerar också med egenskaper för skalära objekt och samlingar. Mer information finns i [about_Properties](about_Properties.md).

### <a name="examples"></a>Exempel

I följande exempel körs metoden **Kill** för enskilda process objekt i en objekt samling.

Det första kommandot startar tre instanser av anteckningar-processen. `Get-Process` hämtar alla tre instanserna av anteckningar-processen och sparar dem i `$p` variabeln.

```powershell
Notepad; Notepad; Notepad
$p = Get-Process Notepad
$p.Count
```

```Output
3
```

Nästa kommando kör metoden **Kill** på alla tre processerna i `$p` variabeln. Kommandot fungerar även om en samling processer inte har någon `Kill` metod.

```powershell
$p.Kill()
Get-Process Notepad
```

`Get-Process`Kommandot bekräftar att `Kill` metoden fungerade.

```Output
Get-Process : Cannot find a process with the name "notepad". Verify the proc
ess name and call the cmdlet again.
At line:1 char:12
+ Get-Process <<<<  notepad
    + CategoryInfo          : ObjectNotFound: (notepad:String) [Get-Process]
, ProcessCommandException
    + FullyQualifiedErrorId : NoProcessFoundForGivenName,Microsoft.PowerShel
l.Commands.GetProcessCommand
```

Det här exemplet är detsamma som att använda `Foreach-Object` cmdleten för att köra metoden på varje objekt i samlingen.

```powershell
$p | ForEach-Object {$_.Kill()}
```

### <a name="foreach-and-where-methods"></a>Förvars och var metoderna

Från och med PowerShell 4,0 stöds samlings filtrering med hjälp av metoden syntax. Detta gör att du kan använda två nya metoder när du hanterar samlingar `ForEach` och `Where` .

Du kan läsa mer om de här metoderna i [about_arrays](about_arrays.md)

### <a name="calling-a-specific-method-when-multiple-overloads-exist"></a>Anropa en speciell metod när det finns flera överlagringar

Tänk dig följande scenario när du anropar .NET-metoder. Om en metod tar ett objekt men har en överlagring via ett gränssnitt med en mer specifik typ, väljer PowerShell den metod som accepterar objektet om du inte uttryckligen skickar den till det gränssnittet.

```powershell
Add-Type -TypeDefinition @'

   // Interface
   public interface IFoo {
     string Bar(int p);
   }

   // Type that implements the interface
   public class Foo : IFoo {

   // Direct member method named 'Bar'
   public string Bar(object p) { return $"object: {p}"; }

   // *Explicit* implementation of IFoo's 'Bar' method().
   string IFoo.Bar(int p) {
       return $"int: {p}";
   }

}
'@
```

I det här exemplet `object` valdes mindre viss överbelastning för **stapel** -metoden.

```powershell
[Foo]::new().Bar(1)
```

```Output
object: 1
```

I det här exemplet har vi omvandlat-metoden till gränssnittet **IFoo** för att välja en mer detaljerad överlagring av **streckkods** metoden.

```powershell
([IFoo] [Foo]::new()).Bar(1)
```

```Output
int: 1
```

## <a name="see-also"></a>Se även

[about_Objects](about_Objects.md)

[about_Properties](about_Properties.md)

[Hämta medlem](xref:Microsoft.PowerShell.Utility.Get-Member)
