---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Skapa nytt objekt för .NET och COM-objekt"
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: 534e1a9a759d67cfc62ce658a7abddf02f767212
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="creating-net-and-com-objects-new-object"></a>Skapa .NET och COM-objekt (nya objekt)
Det är programkomponenter med .NET Framework och COM-gränssnitt som gör att du kan utföra administrationsuppgifter för många system. Windows PowerShell kan du använda de här komponenterna så att du inte är begränsad till de uppgifter som kan utföras med hjälp av cmdlet: ar. Många av cmdletar i den första versionen av Windows PowerShell fungerar inte mot fjärrdatorer. Visar vi hur du komma runt denna begränsning vid hantering av händelseloggar med hjälp av .NET Framework **system.Diagnostics.Eventlog och** klass direkt från Windows PowerShell.

### <a name="using-new-object-for-event-log-access"></a>Med nytt objekt för åtkomst till Loggboken
.NET Framework-Klassbiblioteket innehåller en klass som heter **system.Diagnostics.Eventlog och** som kan användas för att hantera händelseloggar. Du kan skapa en ny instans av en .NET Framework-klass med hjälp av den **New-Object** med den **TypeName** parameter. Till exempel skapar följande kommando en referens i händelseloggen:

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

Även om kommandot har skapat en instans av klassen EventLog, innehåller instansen inte några data. Det beror på att vi inte har angett en viss händelselogg. Hur skaffar du en verklig händelselogg

#### <a name="using-constructors-with-new-object"></a>Använda konstruktorer med nytt objekt
Refererar till en specifik händelselogg, måste du ange namnet på loggen. **Nytt objekt** har en **ArgumentList** parameter. Argument som du skickar som värden för den här parametern används av en särskild startmetoden för objektet. Metoden anropas en *konstruktorn* eftersom den används för att skapa objektet. Till exempel för att få en referens till programloggen kan ange du strängen ”program” som ett argument:

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> Eftersom de flesta av .NET Framework-kärnklasser finns i namnrymden System, försöker Windows PowerShell automatiskt hitta klasser som du anger i namnrymden System om den inte finns en matchning för typename som du anger. Det innebär att du kan ange Diagnostics.EventLog i stället för system.Diagnostics.Eventlog och.

#### <a name="storing-objects-in-variables"></a>Lagra objekt i variabler
Du kanske vill lagra en referens till ett objekt så att du kan använda den i den aktuella shell. Även om Windows PowerShell kan du göra mycket arbete med pipelines, inskränkning behovet av variabler, gör ibland spara referenser till objekt i variabler det enklare att hantera dessa objekt.

Windows PowerShell kan du skapa variabler som är i stort sett namngivna objekt. Utdata från alla giltiga Windows PowerShell-kommando kan lagras i en variabel. Variabelnamn börjar alltid med $. Om du vill lagra program loggreferens i en variabel med namnet $AppLog, skriver du namnet på variabeln, följt av ett likhetstecken och Skriv det kommando som används för att skapa loggfilen programobjektet:

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

#### <a name="accessing-a-remote-event-log-with-new-object"></a>Åtkomst till en fjärrhantering av händelseloggen med nya objekt
De kommandon som används i föregående avsnitt rikta den lokala datorn. den **Get-EventLog** cmdlet kan göra det. För att komma åt programloggen på en fjärrdator måste du ange både namnet på loggen och ett datornamn (eller IP-adress) som argument.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

Nu när vi har en referens till en händelselogg som lagras i variabeln $RemoteAppLog uppgifter kan vi utföra på den?

#### <a name="clearing-an-event-log-with-object-methods"></a>Rensa en händelselogg med objektmetoder
Objekt har ofta metoder som kan användas för att utföra uppgifter. Du kan använda **Get-medlemmen** att visa vilka metoder som associeras med ett objekt. Följande kommando och valda visar några metoder i klassen händelseloggen:

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

Den **Rensa()** metoden kan användas för att rensa händelseloggen. När du anropar en metod, måste du göra metodnamnet av parenteser, även om metoden som inte kräver argument. Detta gör att Windows PowerShell skilja mellan metoden och potentiella egenskap med samma namn. Skriv följande för att anropa den **Rensa** metoden:

```
PS> $RemoteAppLog.Clear()
```

Skriv följande för att visa loggen. Du ser att händelseloggen har rensats och nu har 0 poster i stället för 262:

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### <a name="creating-com-objects-with-new-object"></a>Skapa COM-objekt med nytt objekt
Du kan använda **New-Object** att arbeta med COM Component Object Model ()-komponenter. Komponenter mellan de olika biblioteken som inkluderas med Windows Script Host (WSH) att ActiveX-program, till exempel Internet Explorer som är installerade på de flesta datorer.

**Nytt objekt** använder .NET Framework Runtime-Callable Omslutningar för att skapa COM-objekt, så att den har samma begränsningar som .NET Framework vid anrop av COM-objekt. För att skapa ett COM-objekt, måste du ange den **ComObject** parameter med programmässiga identifierare eller *ProgId* av COM-klass som du vill använda. En fullständig beskrivning av begränsningarna i COM-användning och bestämma vilka ProgID är tillgängligt i ett system som ligger utanför omfånget för den här användarhandboken, men de flesta välkända objekt från miljöer, till exempel WSH kan användas i Windows PowerShell.

Du kan skapa WSH-objekt genom att ange dessa ProgID: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, och  **Scripting.FileSystemObject**. Dessa objekt skapar du följande kommandon:

```
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

Även om de flesta av funktionerna i de här klasserna görs tillgänglig på andra sätt i Windows PowerShell är några uppgifter som att skapa genväg fortfarande lättare att göra med hjälp av WSH-klasser.

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a>Skapa en genväg på skrivbordet med WScript.Shell
En uppgift som kan utföras snabbt med ett COM-objekt är att skapa en genväg. Anta att du vill skapa en genväg på skrivbordet som länkar till arbetsmappen för Windows PowerShell. Först måste du skapa en referens till **WScript.Shell**, som vi lagrar i en variabel med namnet **$WshShell**:

```
$WshShell = New-Object -ComObject WScript.Shell
```

Get-medlem fungerar med COM-objekt, så du kan utforska medlemmarna i objektet genom att skriva:

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-medlemmen** har en valfri **InputObject** parameter som används i stället för omdirigering för att ange indata för **Get-medlemmen**. Du skulle få samma utdata som visas ovan om du i stället använde kommandot **Get-medlem - InputObject $WshShell**. Om du använder **InputObject**, det behandlar argument som ett enskilt objekt. Detta innebär att om du har flera objekt i en variabel **Get-medlemmen** behandlar dem som en matris med objekt. Till exempel:


```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

Den **WScript.Shell CreateShortcut** metoden godkänner ett argument, sökvägen till genvägsfilen för att skapa. Vi kan ange den fullständiga sökvägen till skrivbordet, men det finns ett enklare sätt. Skrivbordet representeras normalt av en mapp med namnet skrivbordet i arbetsmappen för den aktuella användaren. Windows PowerShell har en variabel **$Home** som innehåller sökvägen till den här mappen. Vi kan ange sökvägen till arbetsmappen med hjälp av den här variabeln och Lägg sedan till namnet på mappen Skrivbord och namnet på genvägen till skapa genom att skriva:

```
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

När du använder något som ser ut som ett variabelnamn inom citattecken, försöker Windows PowerShell i stället använda ett motsvarande värde. Om du använder en citattecken, försöker Windows PowerShell inte ersätta variabelvärdet. Skriv till exempel följande kommandon:

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

Nu har vi en variabel med namnet **$lnk** som innehåller en ny genväg referens. Om du vill visa dess medlemmar kan du skicka det till **Get-medlemmen**. Utdata nedan visas medlemmarna som vi behöver använda för att skapa våra genvägen:

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

Vi behöver ange den **TargetPath**, vilket är programmappen för Windows PowerShell och sedan spara genvägen **$lnk** genom att anropa den **spara** metod. Sökvägen till Windows PowerShell programmet lagras i variabeln **$PSHome**, så vi kan göra detta genom att skriva:

```
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a>Med hjälp av Internet Explorer från Windows PowerShell
Många program (inklusive Microsoft Office-familjen av program och Internet Explorer) kan automatiseras med hjälp av COM. Internet Explorer visar några av de vanliga tekniker och problem som ingår i att arbeta med COM-baserade program.

Du skapar en instans av Internet Explorer genom att ange den Internet Explorer ProgId, **InternetExplorer.Application**:

```
$ie = New-Object -ComObject InternetExplorer.Application
```

Detta kommando startar Internet Explorer, men göra inte den synlig. Om du skriver Get-Process, kan du se att en process som kallas iexplore körs. Om du avslutar Windows PowerShell i själva verket fortsätter processen att köras. Du måste starta om datorn eller använda ett verktyg som Aktivitetshanteraren för att avsluta processen iexplore.

> [!NOTE]
> COM-objekt som startar som separata processer kallas ofta *ActiveX körbara filer*, kanske eller kanske inte visas ett fönster för gränssnittet användare när de startas. Om de skapa ett fönster utan att göra den synlig som Internet Explorer, fokus flyttas vanligtvis till Windows-skrivbordet och måste du göra fönstret synlig kan interagera med den.

Genom att skriva **$ie | Get-medlemmen**, du kan visa egenskaper och metoder för Internet Explorer. Visa Internet Explorer-fönstret genom att ange egenskapen Visible till $true genom att skriva:

```
$ie.Visible = $true
```

Sedan kan du gå till en specifik webbadress med hjälp av metoden analysera:

```
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

Med andra medlemmar i objektmodellen i Internet Explorer är det möjligt att hämta textinnehåll från webbsidan. Följande kommando visar HTML-texten i brödtexten för den aktuella webbsidan:

```
$ie.Document.Body.InnerText
```

Stäng Internet Explorer från PowerShell genom att anropa dess Quit()-metoden:

```
$ie.Quit()
```

Detta kräver att den stängs. $Ie variabeln innehåller inte längre en giltig referens till trots att den fortfarande kan vara ett COM-objekt. Om du försöker använda den får du ett automationfel:

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

Du kan antingen ta bort de återstående referera med ett kommando som $ie = $null eller ta bort variabeln helt genom att skriva:

```
Remove-Variable ie
```

> [!NOTE]
> Det finns ingen gemensam standard för om ActiveX körbara filer avsluta eller fortsätta att köras när du tar bort en referens till en. Beroende på omständigheter som anger om programmet är synliga, om ett redigerat dokument körs i den och även om Windows PowerShell fortfarande körs programmet kan eller kan inte avslutas. Därför bör du testa avslutning beteendet för varje ActiveX körbara du vill använda i Windows PowerShell.

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a>Visa varningar om .NET Framework radbrutet COM-objekt
I vissa fall kan ett COM-objekt kan ha en associerad .NET Framework *Runtime-Callable Wrapper* eller RCW och det här kan användas av **New-Object**. Eftersom beteendet för RCW kan skilja sig från beteendet för normal COM-objektet **New-Object** har en **strikt** parametern för att varna dig om RCW åtkomst. Om du anger den **strikt** parameter och sedan skapa ett COM-objekt som använder en RCW, du får ett varningsmeddelande:

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

Även om det fortfarande skapas, varnas du att det inte är ett standard COM-objekt.

