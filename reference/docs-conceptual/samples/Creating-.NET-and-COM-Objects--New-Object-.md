---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Skapa .NET- och COM-objekt nytt objekt
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: 1ffd8d4afa419ec0c24321e44aa4a2f41a9bee44
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406038"
---
# <a name="creating-net-and-com-objects-new-object"></a>Skapa .NET- och COM-objekt (New-Object)

Det finns programvarukomponenter med .NET Framework- och COM-gränssnitt som gör det möjligt att utföra många aktiviteter för administration av system. Windows PowerShell kan du använda de här komponenterna så att du inte är begränsad till de uppgifter som kan utföras med hjälp av cmdlet: ar. Många av i denna första version av Windows PowerShell-cmdlets fungerar inte mot fjärrdatorer. Vi visar hur du kan komma runt denna begränsning vid hantering av händelseloggar genom att använda .NET Framework **system.Diagnostics.Eventlog och** klass direkt från Windows PowerShell.

### <a name="using-new-object-for-event-log-access"></a>Med New-Object för händelseloggen åtkomst

.NET Framework Class-bibliotek innehåller en klass med namnet **system.Diagnostics.Eventlog och** som kan användas för att hantera händelseloggar. Du kan skapa en ny instans av en .NET Framework-klass med hjälp av den **New-Object** cmdlet med den **TypeName** parametern. Till exempel skapar följande kommando en referens i händelseloggen:

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

Även om kommandot har skapat en instans av klassen EventLog, innehåller instansen inte några data. Det beror på att vi inte har angett en viss händelselogg. Hur får du en verklig händelselogg?

#### <a name="using-constructors-with-new-object"></a>Med New-Object konstruktorer

Refererar till en specifik händelselogg, måste du ange namn på loggen. **New-Object** har en **ArgumentList** parametern. Argument som du skickar som värden för den här parametern används av en särskild startmetoden i-objektet. Metoden anropas en *konstruktorn* eftersom den används för att skapa objektet. Till exempel om du vill hämta en referens till programloggen anger du strängen ”program” som ett argument:

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> Eftersom de flesta .NET Framework core klasser finns i namnrymden System, försöker Windows PowerShell automatiskt hitta klasser som du anger i namnrymden System om den inte kan hitta en matchning för typename som du anger. Det innebär att du kan ange Diagnostics.EventLog i stället för system.Diagnostics.Eventlog och.

#### <a name="storing-objects-in-variables"></a>Lagra objekt i variabler

Du kanske vill spara en referens till ett objekt, så att du kan använda den i det nuvarande gränssnittet. Även om Windows PowerShell kan du göra mycket arbete med pipelines inskränkning behovet av variabler, är ibland lagra referenser till objekt i variabler det mer praktiskt att ändra dessa objekt.

Windows PowerShell kan du skapa variabler som är i stort sett namngivna objekt. Utdata från alla giltiga Windows PowerShell-kommandon kan lagras i en variabel. Variabelnamn börja alltid med $. Om du vill lagra Application log-referens i en variabel med namnet $AppLog, skriver du namnet på variabeln, följt av ett likhetstecken och skriv sedan kommandot används för att skapa log programobjektet:

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

Om du anger sedan $AppLog kan se du att den innehåller programloggen:

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### <a name="accessing-a-remote-event-log-with-new-object"></a>Åtkomst till en fjärrhantering av händelseloggen med New-Object

De kommandon som används i föregående avsnitt rikta den lokala datorn. den **Get-EventLog** cmdlet kan göra. För att komma åt programloggen på en fjärrdator, måste du ange både namnet på loggen och ett datornamn (eller IP-adress) som argument.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

Nu när vi har en referens till en händelselogg som lagras i variabeln $RemoteAppLog vilka uppgifter kan vi utföra på den?

#### <a name="clearing-an-event-log-with-object-methods"></a>Rensa en händelselogg med objektmetoder

Objekt har ofta metoder som kan anropas för att utföra uppgifter. Du kan använda **Get-Member** att visa de metoder som associeras med ett objekt. Följande kommando och valda utdata visar några metoder i klassen EventLog:

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

Den **Rensa()** metoden kan användas för att rensa händelseloggen. När du anropar en metod, måste du göra metodnamnet av parenteser, även om metoden som inte kräver argument. På så sätt kan Windows PowerShell skilja mellan metoden och en potentiell egenskap med samma namn. Skriv följande för att anropa den **Rensa** metoden:

```
PS> $RemoteAppLog.Clear()
```

Skriv följande om du vill visa loggen. Du ser att händelseloggen har rensats och nu har 0 poster i stället för 262:

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### <a name="creating-com-objects-with-new-object"></a>Skapa COM-objekt med New-Object
Du kan använda **New-Object** att arbeta med komponenter för COM Component Object Model (). Komponenter sträcker sig från de olika bibliotek som inkluderas med Windows Script Host (WSH) att ActiveX-program, till exempel Internet Explorer som är installerade på de flesta system.

**New-Object** använder .NET Framework Runtime-Anropningsbara Omslutningar för att skapa COM-objekt, så att den har samma begränsningar som .NET Framework när du anropar COM-objekt. Om du vill skapa ett COM-objekt, måste du ange den **ComObject** parameter med den programmässiga identifieraren eller *ProgId* av COM-klass som du vill använda. En fullständig beskrivning av begränsningar av COM-användning och bestämma vilka ProgID är tillgängligt i ett system är utanför omfattningen för den här användarhandboken, men mest välkända objekt från miljöer, till exempel WSH kan användas i Windows PowerShell.

Du kan skapa WSH-objekt genom att ange dessa ProgID: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, och **Scripting.FileSystemObject**. Följande kommandon kan skapa dessa objekt:

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

Även om de flesta av funktionerna i de här klasserna görs tillgänglig på andra sätt i Windows PowerShell, är några uppgifter som att skapa genväg fortfarande lättare att göra med hjälp av WSH-klasser.

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a>Skapa en genväg på skrivbordet med WScript.Shell

En aktivitet som kan utföras snabbt med ett COM-objekt är att skapa en genväg. Anta att du vill skapa en genväg på skrivbordet som länkar till arbetsmappen för Windows PowerShell. Du måste först skapa en referens till **WScript.Shell**, som vi lagrar i en variabel med namnet **$WshShell**:

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

Get-Member fungerar med COM-objekt, så du kan utforska medlemmarna i objektet genom att skriva:

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-Member** har en valfri **InputObject** parameter som du kan använda i stället för omdirigering som indata för **Get-Member**. Du skulle få samma utdata som ovan om du i stället använde kommandot **Get-Member - InputObject $WshShell**. Om du använder **InputObject**, den behandlar dess argument som ett enskilt objekt. Det innebär att om du har flera objekt i en variabel, **Get-Member** behandlar dem som en matris med objekt. Till exempel:

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

Den **WScript.Shell CreateShortcut** metoden godkänner ett argument, sökvägen till genvägsfilen för att skapa. Vi kan skriva i den fullständiga sökvägen till skrivbordet, men det finns ett enklare sätt. Skrivbordet är vanligtvis representeras av en mapp med namnet Desktop i arbetsmappen för den aktuella användaren. Windows PowerShell har en variabel **$Home** som innehåller sökvägen till den här mappen. Vi kan ange sökvägen till arbetsmappen med hjälp av den här variabeln och Lägg sedan till namnet på mappen Skrivbord och namnet på genvägen till skapa genom att skriva:

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

När du använder något som ser ut som ett variabelnamn inom dubbla citattecken, försöker Windows PowerShell att ersätta ett motsvarande värde. Om du använder en citattecken, försöker Windows PowerShell inte att ersätta variabelvärdet. Prova till exempel att skriva följande kommandon:

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

Nu har vi en variabel med namnet **$lnk** som innehåller en ny genväg referens. Om du vill visa medlemmarna kan du skicka det till **Get-Member**. Utdata nedan visar medlemmarna som vi behöver använda skapa vår genväg:

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

Vi måste du ange den **TargetPath**, vilket är programmappen för Windows PowerShell och sedan spara genvägen **$lnk** genom att anropa den **spara** metod. Mappsökväg för Windows PowerShell-programmet lagras i variabeln **$PSHome**, så vi kan göra detta genom att skriva:

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a>Med hjälp av Internet Explorer från Windows PowerShell

Många program (inklusive i Microsoft Office-familjen av program och Internet Explorer) kan automatiseras med hjälp av COM. Internet Explorer visar några av de vanliga metoder och problem som ingår i att arbeta med COM-baserade program.

Du skapar en instans av Internet Explorer genom att ange den Internet Explorer ProgId, **InternetExplorer.Application**:

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

Det här kommandot startar Internet Explorer, men gör inte det synligt. Om du skriver Get-Process, kan du se att en process som kallas iexplore körs. Om du avslutar Windows PowerShell i själva verket fortsätter processen att köras. Du måste starta om datorn eller använda ett verktyg som Aktivitetshanteraren för att avsluta processen iexplore.

> [!NOTE]
> COM-objekt som börjar som separata processer kallas *ActiveX körbara filer*, kanske eller kanske inte visas ett fönster för user interface när de startas. Om de skapa ett fönster, men inte gör det visas, till exempel Internet Explorer, kommer vanligtvis att flytta fokus på Windows-skrivbordet och du måste göra fönstret synlig för att interagera med den.

Genom att skriva **$ie | Get-Member**, du kan visa egenskaper och metoder för Internet Explorer. Om du vill se i Internet Explorer-fönstret visas egenskapen värdet $true genom att skriva:

```powershell
$ie.Visible = $true
```

Du kan sedan navigera till en specifik webbadress med hjälp av metoden analysera:

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

Med andra medlemmar i Internet Explorer: objektmodell, är det möjligt att hämta textinnehållet från webbsidan. Följande kommando visar HTML-texten i brödtexten i den aktuella webbsidan:

```powershell
$ie.Document.Body.InnerText
```

Stäng Internet Explorer från PowerShell genom att anropa dess Quit()-metoden:

```powershell
$ie.Quit()
```

Detta kommer att tvinga den att Stäng. $Ie variabeln innehåller inte längre en giltig referens trots att den fortfarande verkar vara ett COM-objekt. Om du försöker använda den, får du ett automationfel:

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

Du kan antingen ta bort de återstående referera med ett kommando som $ie = $null eller helt ta bort variabeln genom att skriva:

```powershell
Remove-Variable ie
```

> [!NOTE]
> Det finns ingen gemensam standard för huruvida ActiveX körbara filer avsluta eller fortsätta att köras när du tar bort en referens till en. Beroende på omständigheterna som huruvida programmet är synliga, om ett redigerat dokument körs i den och även om Windows PowerShell fortfarande körs programmet kan eller kan inte avslutas. Därför bör du testa avslutning beteendet för varje ActiveX körbara du vill använda i Windows PowerShell.

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a>Få varningar om .NET Framework-omslutna COM-objekt

I vissa fall kan en COM-objektet kan ha en associerad .NET Framework *Runtime-Anropningsbara omslutning* eller RCW och det här kommer att användas av **New-Object**. Eftersom RCW beteende kan skilja sig från beteendet för normal COM-objektet **New-Object** har en **Strict** parameter för att varna dig om RCW åtkomst. Om du anger den **Strict** parametern och sedan skapa ett COM-objekt som använder en RCW, du får ett varningsmeddelande:

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

Även om objektet fortfarande har skapats, ett meddelande om att det inte är ett standard COM-objekt.