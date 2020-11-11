---
description: Beskriver hur variabler lagrar värden som kan användas i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Variables
ms.openlocfilehash: e1eee80740d1f59ab9a96122c09ba81ef99d35cc
ms.sourcegitcommit: 768816a5c05cc2d07ffd84bed95b0499f4b49f2d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483045"
---
# <a name="about-variables"></a>Om variabler

## <a name="short-description"></a>Kort beskrivning

Beskriver hur variabler lagrar värden som kan användas i PowerShell.

## <a name="long-description"></a>Lång beskrivning

Du kan lagra alla typer av värden i PowerShell-variabler. Du kan till exempel lagra resultatet av kommandon och lagra element som används i kommandon och uttryck, till exempel namn, sökvägar, inställningar och värden.

En variabel är en enhet i minnet där värden lagras. I PowerShell representeras variabler av text strängar som börjar med ett dollar tecken ( `$` ), till exempel,, `$a` `$process` eller `$my_var` .

Variabel namn är inte Skift läges känsliga och kan innehålla blank steg och specialtecken. Men variabel namn som innehåller specialtecken och blank steg är svåra att använda och bör undvikas. Mer information finns i [variabel namn som innehåller specialtecken](#variable-names-that-include-special-characters).

Det finns flera olika typer av variabler i PowerShell.

- Användardefinierade variabler: variabler som skapats av användaren skapas och underhålls av användaren. Som standard finns variabler som du skapar på PowerShell-kommandoraden bara när PowerShell-fönstret är öppet. När PowerShell-fönstren stängs tas variablerna bort. Om du vill spara en variabel lägger du till den i din PowerShell-profil. Du kan också skapa variabler i skript med globalt skript eller lokalt definitions område.

- Automatiska variabler: automatiska variabler lagrar status för PowerShell. De här variablerna skapas av PowerShell, och PowerShell ändrar värdena efter behov för att upprätthålla deras noggrannhet. Användare kan inte ändra värdet för dessa variabler. `$PSHOME`Variabeln lagrar till exempel sökvägen till installations katalogen för PowerShell.

  Mer information, en lista och en beskrivning av de automatiska variablerna finns [about_Automatic_Variables](about_Automatic_Variables.md).

- Inställningar variabler: Preferences-variabler lagrar användar inställningar för PowerShell. Dessa variabler skapas av PowerShell och fylls i med standardvärden. Användare kan ändra värdena för variablerna. Variabeln kan till exempel `$MaximumHistoryCount` bestämma det maximala antalet poster i tidigare sessioner.

  Mer information, en lista och en beskrivning av Preferences-variablerna finns [about_Preference_Variables](about_Preference_Variables.md).

## <a name="working-with-variables"></a>Arbeta med variabler

Om du vill skapa en ny variabel använder du ett tilldelnings uttryck för att tilldela variabeln ett värde. Du behöver inte deklarera variabeln innan du använder den. Standardvärdet för alla variabler är `$null` .

Om du vill hämta en lista över alla variabler i PowerShell-sessionen skriver du `Get-Variable` . Variabel namnen visas utan föregående dollar `$` tecken () som används för att referera till variabler.

Exempel:

```powershell
$MyVariable = 1, 2, 3

$Path = "C:\Windows\System32"
```

Variabler är användbara för att lagra resultatet av kommandon.

Exempel:

```powershell
$Processes = Get-Process

$Today = (Get-Date).DateTime
```

Om du vill visa värdet för en variabel skriver du variabelns namn, föregånget av ett dollar tecken ( `$` ).

Exempel:

```powershell
$MyVariable
```

```Output
1
2
3
```

```powershell
$Today
```

```Output
Tuesday, September 3, 2019 09:46:46
```

Om du vill ändra värdet för en variabel tilldelar du ett nytt värde till variabeln.

Följande exempel visar värdet för `$MyVariable` variabeln, ändrar värdet för variabeln och visar sedan det nya värdet.

```powershell
$MyVariable = 1, 2, 3
$MyVariable
```

```Output
1
2
3
```

```powershell
$MyVariable = "The green cat."
$MyVariable
```

```Output
The green cat.
```

Om du vill ta bort värdet för en variabel använder du `Clear-Variable` cmdleten eller ändrar värdet till `$null` .

```powershell
Clear-Variable -Name MyVariable
```

```powershell
$MyVariable = $null
```

Ta bort variabeln genom att använda [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) eller [Remove-item](xref:Microsoft.PowerShell.Management.Remove-Item).

```powershell
Remove-Variable -Name MyVariable
```

```powershell
Remove-Item -Path Variable:\MyVariable
```

## <a name="types-of-variables"></a>Typer av variabler

Du kan lagra alla typer av objekt i en variabel, inklusive heltal, strängar, matriser och hash-tabeller. Och objekt som representerar processer, tjänster, händelse loggar och datorer.

PowerShell-variabler skrivs fritt, vilket innebär att de inte är begränsade till en viss typ av objekt. En enskild variabel kan till och med innehålla en samling, eller matris, av olika typer av objekt på samma gång.

Data typen för en variabel fastställs av .NET-typerna för variabelns värden. Om du vill visa en variabels objekt typ använder du [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member).

Exempel:

```powershell
$a = 12                         # System.Int32
$a = "Word"                     # System.String
$a = 12, "Word"                 # array of System.Int32, System.String
$a = Get-ChildItem C:\Windows   # FileInfo and DirectoryInfo types
```

Du kan använda ett Type-attribut och Cast notation för att säkerställa att en variabel endast kan innehålla vissa objekt typer eller objekt som kan konverteras till den typen. Om du försöker tilldela ett värde av en annan typ försöker PowerShell konvertera värdet till dess typ. Om typen inte kan konverteras Miss lyckas tilldelnings instruktionen.

Om du vill använda Cast notation anger du ett typnamn som omges av hakparenteser, före variabel namnet (till vänster i tilldelnings instruktionen). I följande exempel skapas en `$number` variabel som bara kan innehålla heltal, en `$words` variabel som bara kan innehålla strängar och en `$dates` variabel som endast kan innehålla **datetime** -objekt.

```powershell
[int]$number = 8
$number = "12345"  # The string is converted to an integer.
$number = "Hello"
```

```Output
Cannot convert value "Hello" to type "System.Int32". Error: "Input string was
 not in a correct format."
At line:1 char:1
+ $number = "Hello"
+ ~~~~~~~~~~~~~~~~~
+ CategoryInfo          : MetadataError: (:) [],
    ArgumentTransformationMetadataException
+ FullyQualifiedErrorId : RuntimeException
```

```powershell
[string]$words = "Hello"
$words = 2       # The integer is converted to a string.
$words += 10     # The plus (+) sign concatenates the strings.
$words
```

```Output
210
```

```powershell
[datetime] $dates = "09/12/91"  # The string is converted to a DateTime object.
$dates
```

```Output
Thursday, September 12, 1991 00:00:00
```

```powershell
$dates = 10    # The integer is converted to a DateTime object.
$dates
```

```Output
Monday, January 1, 0001 00:00:00
```

## <a name="using-variables-in-commands-and-expressions"></a>Använda variabler i kommandon och uttryck

Om du vill använda en variabel i ett kommando eller uttryck skriver du variabelns namn, föregånget av dollar `$` tecknet ().

Om variabel namn och dollar tecken inte omges av citat tecken, eller om de omges av dubbla citat tecken ( `"` ), används värdet för variabeln i kommandot eller uttrycket.

Om variabel namn och dollar tecken omges av enkla citat `'` tecken () används variabel namnet i uttrycket.

Mer information om hur du använder citat tecken i PowerShell finns [about_Quoting_Rules](about_Quoting_Rules.md).

Det här exemplet hämtar värdet för `$PROFILE` variabeln, som är sökvägen till PowerShell-filen för användar profiler i PowerShell-konsolen.

```powershell
$PROFILE
```

```Output
C:\Users\User01\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
```

I det här exemplet visas två kommandon som kan öppna PowerShell-profilen i **notepad.exe**. Exemplet med dubbla citat `"` tecken () använder variabelns värde.

```powershell
notepad $PROFILE

notepad "$PROFILE"
```

I följande exempel används ett enkelt citat `'` tecken () som behandlar variabeln som en literal text.

```powershell
'$PROFILE'
```

```Output
$PROFILE
```

```powershell
'Use the $PROFILE variable.'
```

```Output
Use the $PROFILE variable.
```

## <a name="variable-names-that-include-special-characters"></a>Variabel namn som innehåller specialtecken

Variabel namn börjar med ett dollar tecken ( `$` ) och får innehålla alfanumeriska tecken och specialtecken. Variabel namnets längd begränsas bara av tillgängligt minne.

Det bästa tillvägagångs sättet är att variabel namn bara innehåller alfanumeriska tecken och under streck ( `_` )-tecknet. Variabel namn som innehåller blank steg och andra specialtecken är svåra att använda och bör undvikas.

Alfanumeriska variabel namn kan innehålla följande tecken:

- Unicode-tecken från dessa kategorier: **Lu** , **lla** , **lt** , **LM** , **Lo** eller **nd**.
- Under streck ( `_` )-tecken.
- Frågetecken ( `?` )-tecken.

I följande lista finns beskrivningar av Unicode-kategorier. Mer information finns i [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory).

- **Lu** -UppercaseLetter
- **Lla** – LowercaseLetter
- **Lt** -TitlecaseLetter
- **LM** -ModifierLetter
- **Lo** -OtherLetter
- **Nd** – DecimalDigitNumber

Om du vill skapa eller visa ett variabel namn som innehåller blank steg eller specialtecken, omger du variabel namnet med klammerparenteser ( `{}` )-tecknen.
Klammerparenteserna Direct PowerShell för att tolka variabel namnets tecken som litteraler.

Variabel namn för specialtecken kan innehålla följande tecken:

- Valfritt Unicode-tecken, med följande undantag:
  - Avslutande klammer ( `}` )-tecken (U + 007D).
  - "Bakticket"-( `` ` `` )-symbolen (U + 0060). Bakticket används för att undanta Unicode-tecken så att de behandlas som litteraler.

PowerShell har reserverade variabler som `$$` ,, `$?` `$^` och `$_` som innehåller alfanumeriska tecken och specialtecken. Mer information finns i [about_Automatic_Variables](about_automatic_variables.md).

Till exempel skapar följande kommando variabeln med namnet `save-items` . Klammerparenteser ( `{}` ) behövs eftersom variabel namnet innehåller ett bindestreck ( `-` )-specialtecken.

```powershell
${save-items} = "a", "b", "c"
${save-items}
```

```Output
a
b
c
```

Följande kommando hämtar de underordnade objekten i katalogen som representeras av `ProgramFiles(x86)` miljö variabeln.

```powershell
Get-ChildItem ${env:ProgramFiles(x86)}
```

Om du vill referera till ett variabel namn som innehåller klammerparenteser, omger du variabel namnet inom klammerparenteser och använder Baknings tecknet för att undanta klammerparenteserna. Om du till exempel vill skapa en variabel med namnet `this{value}is` Typ:

```powershell
${this`{value`}is} = "This variable name uses braces and backticks."
${this`{value`}is}
```

```Output
This variable name uses braces and backticks.
```

## <a name="variables-and-scope"></a>Variabler och omfång

Som standard är variabler bara tillgängliga i den omfattning som de har skapats i.

En variabel som du skapar i en funktion är till exempel bara tillgänglig i funktionen. En variabel som du skapar i ett skript är bara tillgänglig i skriptet. Om du använder skriptet i punkt-källa läggs variabeln till i det aktuella omfånget. Mer information finns i [about_Scopes](about_Scopes.md).

Du kan använda en omfattnings modifierare för att ändra standard omfånget för variabeln. Följande uttryck skapar en variabel med namnet `Computers` . Variabeln har en global omfattning, även när den skapas i ett skript eller en funktion.

```powershell
$Global:Computers = "Server01"
```

För alla skript eller kommandon som körs utanför sessionen behöver du `Using` omfångs modifieraren för att bädda in variabel värden från scopet för den anropande sessionen, så att det går att komma åt dem.

Mer information finns i [about_Remote_Variables](about_Remote_Variables.md).

## <a name="saving-variables"></a>Sparar variabler

Variabler som du skapar är bara tillgängliga i den session där du skapar dem. De går förlorade när du stänger sessionen.

Om du vill skapa variabeln i varje PowerShell-session som du startar lägger du till variabeln i din PowerShell-profil.

Om du till exempel vill ändra värdet för `$VerbosePreference` variabeln i varje PowerShell-session lägger du till följande kommando i din PowerShell-profil.

```powershell
$VerbosePreference = "Continue"
```

Du kan lägga till det här kommandot i din PowerShell-profil genom att öppna `$PROFILE` filen i en text redigerare, t. ex. **notepad.exe**. Mer information om PowerShell-profiler finns [about_Profiles](about_Profiles.md).

## <a name="the-variable-drive"></a>Variabeln: enhet

PowerShell-variabeln Provider skapar en `Variable:` enhet som ser ut och fungerar som en fil systemen het, men den innehåller variablerna i sessionen och deras värden.

Om du vill ändra till `Variable:` enheten använder du följande kommando:

```powershell
Set-Location Variable:
```

Om du vill visa en lista över objekten och variablerna i `Variable:` enheten använder du `Get-Item` `Get-ChildItem` cmdletarna eller.

```powershell
Get-ChildItem Variable:
```

Om du vill hämta värdet för en viss variabel använder du fil system notation för att ange namnet på enheten och namnet på variabeln. Använd till exempel följande kommando för att hämta den `$PSCulture` automatiska variabeln.

```powershell
Get-Item Variable:\PSCulture
```

```Output
Name                           Value
----                           -----
PSCulture                      en-US
```

Om du vill visa mer information om `Variable:` enheten och PowerShell-variabeln Provider skriver du:

```powershell
Get-Help Variable
```

## <a name="variable-syntax-with-provider-paths"></a>Variabel syntax med Provider-sökvägar

Du kan använda en provider-sökväg med dollar ( `$` )-tecknet och få åtkomst till innehållet i alla providrar som implementerar [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) -gränssnittet.

Följande inbyggda PowerShell-leverantörer stöder den här notationen:

- [about_Environment_Provider](about_Environment_Provider.md)
- [about_Variable_Provider](about_Variable_Provider.md)
- [about_Function_Provider](about_Function_Provider.md)
- [about_Alias_Provider](about_Alias_Provider.md)

## <a name="the-variable-cmdlets"></a>Variabel-cmdletar

PowerShell innehåller en uppsättning cmdletar som är utformade för att hantera variabler.

Om du vill visa en lista med cmdletar skriver du:

```powershell
Get-Command -Noun Variable
```

Om du vill ha hjälp med en angiven cmdlet skriver du:

```powershell
Get-Help <cmdlet-name>
```

| Cmdlet-namn       | Beskrivning                                |
| ---------------   | ------------------------------------------ |
| `Clear-Variable`  | Tar bort värdet för en variabel.           |
| `Get-Variable`    | Hämtar variablerna i den aktuella konsolen. |
| `New-Variable`    | Skapar en ny variabel.                    |
| `Remove-Variable` | Tar bort en variabel och dess värde.          |
| `Set-Variable`    | Ändrar värdet för en variabel.           |

## <a name="see-also"></a>Se även

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Scopes](about_Scopes.md)

[about_Remote_Variables](about_Remote_Variables.md)
