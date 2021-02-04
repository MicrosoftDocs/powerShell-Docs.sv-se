---
title: Formatering, alias, leverantörer, jämförelse
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
description: I det här kapitlet beskrivs begreppen utdata, kommando-alias, providers och jämförelse åtgärder.
ms.openlocfilehash: 5573ca58601af0c6af15736b772a9792d8d77a79
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216167"
---
# <a name="chapter-5---formatting-aliases-providers-comparison"></a>Kapitel 5 – formatering, alias, providers, jämförelse

## <a name="requirements"></a>Krav

Den SQL Server PowerShell-modulen krävs av några av exemplen som visas i det här kapitlet. Modulen installeras som en del av [SQL Server Management Studio (Smss)][SMSS]. Den används också i efterföljande kapitel. Ladda ned och installera den på datorn med Windows 10 labb miljö.

## <a name="format-right"></a>Formatera höger

I kapitel 4 har du lärt dig att filtrera så långt till vänster som möjligt. Regeln för manuell formatering av ett kommandos utdata liknar den regeln, förutom att det måste inträffa så långt till höger som möjligt.

De vanligaste format kommandona är `Format-Table` och `Format-List` . `Format-Wide` och `Format-Custom` kan också användas, men är mindre vanliga.

Som anges i kapitel 3, ett kommando som returnerar fler än fyra egenskaper till en lista, om inte anpassad formatering används.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```Output
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

Använd `Format-Table` cmdleten för att manuellt åsidosätta formateringen och visa utdata i en tabell i stället för en lista.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can* |
Format-Table
```

```Output
 Status DisplayName  CanPauseAndContinue CanShutdown CanStop
 ------ -----------  ------------------- ----------- -------
Running Windows Time               False        True    True
```

Standardutdata för `Get-Service` är tre egenskaper i en tabell.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Använd `Format-List` cmdleten för att åsidosätta standardformateringen och returnera resultatet i en lista.

```powershell
Get-Service -Name w32time | Format-List
```

```Output
Name                : w32time
DisplayName         : Windows Time
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
ServiceType         : Win32ShareProcess
```

Observera att det bara rör `Get-Service` sig om att lämna `Format-List` tillbaka ytterligare egenskaper. Detta inträffar inte med varje kommando på grund av hur formateringen för det specifika kommandot har kon figurer ATS i bakgrunden.

Antalet som är ett sak att vara medveten om med format-cmdletar är att de producerar format objekt som skiljer sig från vanliga objekt i PowerShell.

```powershell
Get-Service -Name w32time | Format-List | Get-Member
```

```Output
   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
autosizeInfo                            Property   Microsoft.PowerShell.Commands.Inter...
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
pageFooterEntry                         Property   Microsoft.PowerShell.Commands.Inter...
pageHeaderEntry                         Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEntryData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
formatEntryInfo                         Property   Microsoft.PowerShell.Commands.Inter...
outOfBand                               Property   bool outOfBand {get;set;}
writeStream                             Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
```

Det innebär att format kommandon inte kan skickas till de flesta andra kommandon. De kan skickas till några av `Out-*` kommandona, men det är det. Detta är anledningen till varför du vill utföra formateringen i slutet av raden (format höger).

## <a name="aliases"></a>Alias

Ett alias i PowerShell är ett kortare namn för ett kommando. PowerShell innehåller en uppsättning inbyggda alias och du kan också definiera egna alias.

`Get-Alias`Cmdleten används för att hitta alias. Om du redan känner till aliaset för ett kommando används **namn** parametern för att avgöra vilket kommando som aliaset är associerat med.

```powershell
Get-Alias -Name gcm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
```

Du kan ange flera alias för värdet för **Name** -parametern.

```powershell
Get-Alias -Name gcm, gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

Du kan ofta se **namn** parametern som utelämnats eftersom det är en positions parameter.

```powershell
Get-Alias gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gm -> Get-Member
```

Om du vill söka efter alias för ett kommando måste du använda **definitions** parametern.

```powershell
Get-Alias -Definition Get-Command, Get-Member
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

Det går inte att använda **definitions** parametern i stället för att den måste anges.

Alias kan spara några tangenttryckningar och de är bra när du skriver in kommandon i-konsolen.
De bör inte användas i skript eller någon kod som du sparar eller delar med andra. Som tidigare nämnts i den här boken, är det enkelt att förstå om du använder fullständig cmdlet och parameter namn.

Var försiktig när du skapar egna alias eftersom de bara finns i den aktuella PowerShell-sessionen på din dator.

## <a name="providers"></a>Leverantörer

En provider i PowerShell är ett gränssnitt som gör det möjligt att använda fil systemet till exempel åtkomst till ett data lager. Det finns ett antal inbyggda providrar i PowerShell.

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
Certificate          ShouldProcess                      {Cert}
WSMan                Credentials                        {WSMan}
```

Som du kan se i föregående resultat finns det inbyggda providers för registret, alias, miljövariabler, fil systemet, funktioner, variabler, certifikat och WSMan.

De faktiska enheterna som dessa leverantörer använder för att exponera sina data lager kan bestämmas med `Get-PSDrive` cmdleten. `Get-PSDrive`Cmdlet: en visar inte bara enheter som exponeras av providers, men visar även logiska Windows-enheter, inklusive enheter som är mappade till nätverks resurser.

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
Alias                                  Alias
C                  14.41        112.10 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
WSMan                                  WSMan
```

Moduler från tredje part, till exempel Active Directory PowerShell-modulen och SQLServer PowerShell-modulen, lägger både till sin egen PowerShell-Provider och PSDrive.

Importera Active Directory och SQL Server PowerShell-moduler.

```powershell
Import-Module -Name ActiveDirectory, SQLServer
```

Kontrol lera om ytterligare PowerShell-leverantörer har lagts till.

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
ActiveDirectory      Include, Exclude, Filter, Shoul... {AD}
SqlServer            Credentials                        {SQLSERVER}
```

Observera att två nya PowerShell-leverantörer nu finns i den föregående uppsättningen med resultat, en för Active Directory och en annan för SQL Server.

En PSDrive för var och en av dessa moduler har också lagts till.

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
AD                                     ActiveDire... //RootDSE/
Alias                                  Alias
C                  19.38        107.13 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
SQLSERVER                              SqlServer     SQLSERVER:\
Variable                               Variable
WSMan                                  WSMan
```

PSDrives kan nås precis som ett traditionellt fil system.

```powershell
Get-ChildItem -Path Cert:\LocalMachine\CA
```

```Output
   PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\CA

Thumbprint                                Subject
----------                                -------
FEE449EE0E3965A5246F000E87FDE2A065FD89D4  CN=Root Agency
D559A586669B08F46A30A133F8A9ED3D038E2EA8  OU=www.verisign.com/CPS Incorporated LIABI...
109F1CAED645BB78B3EA2B94C0697C740733031C  CN=Microsoft Windows Hardware Compatibility,...
```

## <a name="comparison-operators"></a>Jämförelseoperatorer

PowerShell innehåller ett antal jämförelse operatorer som används för att jämföra värden eller hitta värden som matchar vissa mönster. Tabell 5-1 innehåller en lista över jämförelse operatorer i PowerShell.

|    Operator    |                          Definition                          |
| -------------- | ------------------------------------------------------------ |
| `-eq`          | Lika med                                                     |
| `-ne`          | Inte lika med                                                 |
| `-gt`          | Större än                                                 |
| `-ge`          | Större än eller lika med                                     |
| `-lt`          | Mindre än                                                    |
| `-le`          | Mindre än eller lika med                                        |
| `-Like`        | Matcha med `*` jokertecknet                       |
| `-NotLike`     | Överensstämmer inte med `*` jokertecknet              |
| `-Match`       | Matchar det angivna reguljära uttrycket                     |
| `-NotMatch`    | Matchar inte det angivna reguljära uttrycket              |
| `-Contains`    | Anger om en samling innehåller ett angivet värde        |
| `-NotContains` | Anger om en samling inte innehåller ett angivet värde |
| `-In`          | Anger om ett angivet värde finns i en samling           |
| `-NotIn`       | Anger om ett angivet värde inte finns i en samling       |
| `-Replace`     | Ersätter det angivna värdet                                 |

Alla operatorer som anges i tabell 5-1 är Skift läges känsliga. Placera en `c` framför operatorn som visas i tabell 5-1 för att göra den Skift läges känslig. Till exempel `-ceq` är den Skift läges känsliga versionen av `-eq` jämförelse operatorn.

Gemener "PowerShell" är lika med gemener "PowerShell" med hjälp av jämförelse operatorn Equals.

```powershell
'PowerShell' -eq 'powershell'
```

```Output
True
```

Den är inte lika med den Skift läges känsliga versionen av jämförelse operatorn Equals.

```powershell
'PowerShell' -ceq 'powershell'
```

```Output
False
```

Den icke-identiska jämförelse operatorn kastar om villkoret.

```powershell
'PowerShell' -ne 'powershell'
```

```Output
False
```

Större än, större än eller lika med, mindre än och mindre än eller lika med alla fungerar med sträng eller numeriska värden.

```powershell
5 -gt 5
```

```Output
False
```

Om du använder större än eller lika med i stället för större än med föregående exempel returneras det **booleska** värdet True eftersom fem är lika med fem.

```powershell
5 -ge 5
```

```Output
True
```

Baserat på resultaten från de föregående två exemplen kan du förmodligen gissa dig att både mindre än och mindre än eller lika med fungerar.

```powershell
5 -lt 10
```

```Output
True
```

`-Like` `-Match` Operatorerna och kan vara förvirrande, även för erfarna PowerShell-användare. `-Like` används med jokertecken för tecknen `*` och `?` för att utföra "Like"-matchningar.

```powershell
'PowerShell' -like '*shell'
```

```Output
True
```

`-Match` använder ett reguljärt uttryck för att utföra matchningen.

```powershell
'PowerShell' -match '^*.shell$'
```

```Output
True
```

Använd operatorn Range för att lagra talen 1 till och med 10 i en variabel.

```powershell
$Numbers = 1..10
```

```Output
```

Ta reda på om `$Numbers` variabeln innehåller 15.

```powershell
$Numbers -contains 15
```

```Output
False
```

Kontrol lera om det innehåller numret 10.

```powershell
$Numbers -contains 10
```

```Output
True
```

`-NotContains` kastar om logiken för att se om `$Numbers` variabeln inte innehåller något värde.

```powershell
$Numbers -notcontains 15
```

```Output
True
```

Föregående exempel returnerar det **booleska** värdet sant eftersom det är sant att `$Numbers` variabeln inte innehåller 15. Den innehåller dock talet 10 så det är falskt när det testas.

```powershell
$Numbers -notcontains 10
```

```Output
False
```

Jämförelse operatorn "i" introducerades först i PowerShell version 3,0. Den används för att avgöra om ett värde är "i" en matris. `$Numbers`Variabeln är en matris eftersom den innehåller flera värden.

```powershell
15 -in $Numbers
```

```Output
False
```

Med andra ord `-in` utförs samma test som innehåller jämförelse operatorn, förutom motsatt riktning.

```powershell
10 -in $Numbers
```

```Output
True
```

15 finns inte i `$Numbers` matrisen så false returneras i följande exempel.

```powershell
15 -in $Numbers
```

```Output
False
```

Precis som `-contains` operatorn `not` vänder sig `-in` operatorn för operatorn.

```powershell
10 -notin $Numbers
```

```Output
False
```

Det tidigare exemplet returnerar false eftersom `$Numbers` matrisen innehåller 10 och villkoret kunde testas för att avgöra om det inte innehöll 10.

15 är "inte i" `$Numbers` matrisen så att den returnerar det **booleska** värdet true.

```powershell
15 -notin $Numbers
```

```Output
True
```

`-replace`Operatören vill bara tänka dig. Den används för att ersätta något. Om du anger ett värde ersätts värdet med Nothing. I följande exempel ersätter jag "Shell" med Nothing.

```powershell
'PowerShell' -replace 'Shell'
```

```Output
Power
```

Om du vill ersätta ett värde med ett annat värde anger du det nya värdet efter det mönster som du vill ersätta. SQL lördag i Baton Rouge är en händelse som jag försöker tala om varje år. I följande exempel ersätter jag ordet "lördag" med förkortningen "söt".

```powershell
'SQL Saturday - Baton Rouge' -Replace 'saturday','Sat'
```

```Output
SQL Sat - Baton Rouge
```

Det finns också metoder som **Ersätt ()** som kan användas för att ersätta saker som liknar hur ersättnings operatorn fungerar. `-Replace`Operatorn är dock Skift läges känslig som standard och metoden **replace ()** är Skift läges känslig.

```powershell
'SQL Saturday - Baton Rouge'.Replace('saturday','Sat')
```

```Output
SQL Saturday - Baton Rouge
```

Observera att ordet "lördag" inte ersattes i föregående exempel. Detta beror på att den angavs i ett annat fall än originalet. När ordet "lördag" anges i samma fall som den ursprungliga, ersätter metoden **replace ()** det som förväntat.

```powershell
'SQL Saturday - Baton Rouge'.Replace('Saturday','Sat')
```

```Output
SQL Sat - Baton Rouge
```

Var försiktig när du använder metoder för att transformera data eftersom du kan köra oväntade problem, t. ex. om du inte gör ett _kalkon test_. Ett exempel finns i blogg artikeln om [att använda pester för att testa PowerShell-kod med andra kulturer][]. Min rekommendation är att använda en operatör i stället för en metod när det är möjligt att undvika dessa typer av problem.

Även om jämförelse operatorerna kan användas som du ser i föregående exempel, kan jag normalt hitta själv med hjälp av `Where-Object` cmdleten för att utföra viss typ av filtrering.

## <a name="summary"></a>Sammanfattning

I det här kapitlet har du lärt dig ett antal olika ämnen för att ta med formatering höger, alias, providers och jämförelse operatorer.

## <a name="review"></a>Genomgång

1. Varför är det nödvändigt att göra formateringen så långt till höger som möjligt?
1. Hur avgör du vad den faktiska cmdleten är för `%` aliaset?
1. Varför ska du inte använda alias i skript som du sparar eller kodar som du delar med andra?
1. Utföra en katalog lista på de enheter som är associerade med en av register leverantörerna.
1. Vad är en av de största fördelarna med att använda ersättnings operatorn i stället för ersättnings metoden?

## <a name="recommended-reading"></a>Rekommenderad läsning

- [Format-Table][]
- [Format-List][]
- [Format-Wide][]
- [about_Aliases][]
- [about_Providers][]
- [about_Comparison_Operators][]
- [about_Arrays][]

<!-- link references -->
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
[Format-Table]: /powershell/module/microsoft.powershell.utility/format-table
[Format-List]: /powershell/module/microsoft.powershell.utility/format-list
[Format-Wide]: /powershell/module/microsoft.powershell.utility/format-wide
[about_Aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[about_Providers]: /powershell/module/microsoft.powershell.core/about/about_providers
[about_Comparison_Operators]: /powershell/module/microsoft.powershell.core/about/about_comparison_operators
[about_Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Använda pester för att testa PowerShell-kod med andra kulturer]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
