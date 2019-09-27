---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Skapa .NET-och COM-objekt nytt objekt
ms.openlocfilehash: 6e98a159451bc7da4ba3b37eaeb813eb71590d2b
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325174"
---
# <a name="creating-net-and-com-objects-new-object"></a>Skapa .NET-och COM-objekt (nytt-objekt)

Det finns program komponenter med .NET Framework-och COM-gränssnitt som gör att du kan utföra många system administrations uppgifter. Med Windows PowerShell kan du använda dessa komponenter, så du är inte begränsad till de uppgifter som kan utföras med hjälp av cmdletar. Många av cmdletarna i den första versionen av Windows PowerShell fungerar inte mot fjärrdatorer. Vi visar hur du kommer runt den här begränsningen när du hanterar händelse loggar med hjälp av klassen .NET Framework **system. Diagnostics. EventLog** direkt från Windows PowerShell.

## <a name="using-new-object-for-event-log-access"></a>Använda nytt-objekt för händelse logg åtkomst

.NET Framework klass biblioteket innehåller en klass med namnet **system. Diagnostics. EventLog** som kan användas för att hantera händelse loggar. Du kan skapa en ny instans av en .NET Framework-klass med hjälp av cmdleten **New-Object** med parametern **TypeName** . Till exempel skapar följande kommando en händelse logg referens:

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

Även om kommandot har skapat en instans av klassen EventLog, innehåller instansen inga data. Det beror på att vi inte angav någon viss händelse logg. Hur får du en verklig händelse logg?

### <a name="using-constructors-with-new-object"></a>Använda konstruktorer med New-Object

Om du vill referera till en speciell händelse logg måste du ange namnet på loggen. **New-Object** har en **argument List** -parameter. De argument som du skickar som värden för den här parametern används av en särskild start metod för objektet. Metoden kallas en *konstruktor* eftersom den används för att konstruera objektet. Om du till exempel vill hämta en referens till program loggen anger du strängen ' Application ' som ett argument:

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> Eftersom de flesta .NET Framework Core-klasserna finns i system namn rymden försöker Windows PowerShell automatiskt hitta klasser som du anger i systemets namnrymd om det inte går att hitta en matchning för det TypeName som du anger. Det innebär att du kan ange Diagnostics. EventLog i stället för system. Diagnostics. EventLog.

### <a name="storing-objects-in-variables"></a>Lagra objekt i variabler

Du kanske vill lagra en referens till ett objekt, så att du kan använda den i det aktuella gränssnittet. Även om Windows PowerShell gör det möjligt att göra mycket arbete med pipelines, vilket minskar behovet av variabler, och ibland lagra referenser till objekt i variabler, gör det mer praktiskt att ändra dessa objekt.

Med Windows PowerShell kan du skapa variabler som är huvudsakligen namngivna objekt. Utdata från alla giltiga Windows PowerShell-kommandon kan lagras i en variabel. Variabel namn börjar alltid med $. Om du vill lagra program logg referensen i en variabel med namnet $AppLog, skriver du namnet på variabeln följt av ett likhets tecken och skriver sedan kommandot som används för att skapa programloggs objekt:

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

Om du sedan skriver $AppLog kan du se att den innehåller program loggen:

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

### <a name="accessing-a-remote-event-log-with-new-object"></a>Åtkomst till en fjärran sluten händelse logg med New-Object

Kommandona som används i föregående avsnitt riktar sig till den lokala datorn. cmdleten **Get-EventLog** kan göra det. För att få åtkomst till program loggen på en fjärrdator måste du ange både logg namnet och ett dator namn (eller en IP-adress) som argument.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

Nu när vi har en referens till en händelse logg som lagras i variabeln $RemoteAppLog, vilka uppgifter kan vi utföra på den?

### <a name="clearing-an-event-log-with-object-methods"></a>Rensa en händelse logg med objekt metoder

Objekt har ofta metoder som kan anropas för att utföra uppgifter. Du kan använda **Get-Member** för att visa de metoder som är associerade med ett objekt. Följande kommando och valda utdata visar några metoder i klassen EventLog:

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

Metoden **Clear ()** kan användas för att rensa händelse loggen. När du anropar en metod måste du alltid följa metod namnet med parenteser, även om metoden inte kräver argument. Detta låter Windows PowerShell skilja mellan metoden och en möjlig egenskap med samma namn. Skriv följande för att anropa metoden **Clear** :

```
PS> $RemoteAppLog.Clear()
```

Skriv följande för att visa loggen. Du ser att händelse loggen har rensats och har nu 0 poster i stället för 262:

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

## <a name="creating-com-objects-with-new-object"></a>Skapa COM-objekt med New-Object
Du kan använda **nya-objekt** för att arbeta med Component Object Model (com)-komponenter. Komponenter sträcker sig från de olika bibliotek som ingår i Windows Script Host (WSH) till ActiveX-program, till exempel Internet Explorer som är installerade på de flesta system.

**New-Object** använder .NET Framework runtime-anropade omslutningar för att skapa com-objekt, så den har samma begränsningar som .NET Framework gör vid anrop till com-objekt. Om du vill skapa ett COM-objekt måste du ange parametern **ComObject** med program-ID eller *ProgID* för den com-klass som du vill använda. En fullständig beskrivning av begränsningarna med COM-användning och hur du avgör vilka ProgId som är tillgängliga på ett system ligger utanför den här användarens Användar handbok, men de mest välkända objekten från miljöer som WSH kan användas i Windows PowerShell.

Du kan skapa WSH-objekt genom att ange följande ProgID: **Wscript. Shell**, **wscript. Network**, **Scripting. Dictionary**och **Scripting. FileSystemObject**. Följande kommandon skapar följande objekt:

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

Även om de flesta av funktionerna i dessa klasser görs tillgängliga på andra sätt i Windows PowerShell, är det enklare att skapa några uppgifter som att skapa genvägar med hjälp av WSH-klasser.

## <a name="creating-a-desktop-shortcut-with-wscriptshell"></a>Skapa en Skriv bords gen väg med WScript. Shell

En uppgift som snabbt kan utföras med ett COM-objekt är att skapa en genväg. Anta att du vill skapa en genväg på Skriv bordet som länkar till hem-mappen för Windows PowerShell. Du måste först skapa en referens till **wscript. Shell**, som vi kommer att lagra i en variabel med namnet **$WshShell**:

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

Get-Member fungerar med COM-objekt, så att du kan utforska medlemmar i objektet genom att skriva:

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-Member** har en valfri **InputObject** -parameter som du kan använda i stället för rörledningar för att tillhandahålla inmatade **medlemmar**. Du får samma utdata som visas ovan om du i stället använde kommandot **Get-Member-InputObject $WshShell**. Om du använder **InputObject**behandlar den sitt argument som ett enda objekt. Det innebär att om du har flera objekt i en variabel behandlar **Get-Member** dem som en objekt mat ris. Exempel:

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

Metoden **wscript. Shell CreateShortcut** accepterar ett enda argument, sökvägen till gen vägs filen som ska skapas. Vi kan ange den fullständiga sökvägen till Skriv bordet, men det finns ett enklare sätt. Skriv bordet representeras vanligt vis av en mapp med namnet Desktop i den aktuella användarens hem mapp. Windows PowerShell har en variabel **$Home** som innehåller sökvägen till den här mappen. Vi kan ange sökvägen till arbetsmappen med hjälp av den här variabeln och sedan lägga till namnet på mappen Desktop och namnet på genvägen att skapa genom att skriva:

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

När du använder något som ser ut som ett variabel namn inuti dubbla citat tecken försöker Windows PowerShell ersätta ett matchande värde. Om du använder enkla citat tecken försöker inte det variabla värdet ersättas med Windows PowerShell. Försök till exempel att skriva följande kommandon:

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

Nu har vi en variabel med namnet **$lnk** som innehåller en ny gen vägs referens. Om du vill se dess medlemmar kan du lägga till den för att **bli medlem**. I följande utdata visas de medlemmar som vi behöver använda för att slutföra skapandet av vår genväg:

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

Vi måste ange **TargetPath**, som är programmappen för Windows PowerShell, och sedan spara genvägen **$lnk** genom att anropa metoden **Save** . Sökvägen till Windows PowerShell-programmappen lagras i variabeln **$PSHome**, så vi kan göra detta genom att skriva:

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

## <a name="using-internet-explorer-from-windows-powershell"></a>Använda Internet Explorer från Windows PowerShell

Många program (inklusive Microsoft Office serie program och Internet Explorer) kan automatiseras med hjälp av COM. Internet Explorer visar några typiska tekniker och problem som ingår i arbetet med COM-baserade program.

Du skapar en Internet Explorer-instans genom att ange Internet Explorer ProgId, **InternetExplorer. Application**:

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

Det här kommandot startar Internet Explorer, men gör det inte synligt. Om du skriver get-process kan du se att processen som heter iexplore körs. I själva verket fortsätter processen att köras om du avslutar Windows PowerShell. Du måste starta om datorn eller använda ett verktyg som aktivitets hanteraren för att avsluta iexplore-processen.

> [!NOTE]
> COM-objekt som startar som separata processer, vanligt vis kallade *ActiveX-körbara filer*, kan visa ett användar gränssnitts fönster när de startar. Om de skapar ett fönster men inte gör det synligt, t. ex. Internet Explorer, går fokus i allmänhet till Windows-skrivbordet och du måste göra fönstret synligt för att interagera med det.

Genom att skriva **$IE | Hämta medlem**kan du Visa egenskaper och metoder för Internet Explorer. Om du vill visa Internet Explorer-fönstret anger du egenskapen visible till $true genom att skriva:

```powershell
$ie.Visible = $true
```

Du kan sedan navigera till en speciell webb adress med hjälp av metoden navigera:

```powershell
$ie.Navigate("https://devblogs.microsoft.com/scripting/")
```

Med andra medlemmar i Internet Explorer-objektmodellen är det möjligt att hämta text innehåll från webb sidan. Följande kommando visar HTML-texten i bröd texten på den aktuella webb sidan:

```powershell
$ie.Document.Body.InnerText
```

För att stänga Internet Explorer inifrån PowerShell, anropa metoden quit ():

```powershell
$ie.Quit()
```

Detta kommer att tvinga den att stängas. Variabeln $ie inte längre innehåller en giltig referens trots att den fortfarande verkar vara ett COM-objekt. Om du försöker använda den får du ett Automation-fel:

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

Du kan antingen ta bort den återstående referensen med ett kommando som $ie = $null eller helt ta bort variabeln genom att skriva:

```powershell
Remove-Variable ie
```

> [!NOTE]
> Det finns ingen gemensam standard för om du avslutar ActiveX-körbara filer eller fortsätter att köra när du tar bort en referens till en. Beroende på omständigheterna, till exempel om programmet är synligt, om ett redigerat dokument körs i det och även om Windows PowerShell fortfarande körs, kan det hända att programmet inte avslutas. Därför bör du testa avslutnings beteendet för varje ActiveX-fil som du vill använda i Windows PowerShell.

## <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a>Få varningar om .NET Framework-figursatta COM-objekt

I vissa fall kan ett COM-objekt ha en associerad .NET Framework *runtime-anropad wrapper* eller RCW, och detta kommer att användas av **New-Object**. Eftersom beteendet för RCW kan skilja sig från det normala COM-objektets beteende, har **New-Object** en **strikt** parameter som VARNAr dig om RCW-åtkomst. Om du anger en **strikt** parameter och sedan skapar ett com-objekt som använder en RCW, får du ett varnings meddelande:

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

Även om objektet fortfarande har skapats visas en varning om att det inte är ett standard-COM-objekt.
