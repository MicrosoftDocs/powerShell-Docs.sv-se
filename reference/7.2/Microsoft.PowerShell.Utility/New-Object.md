---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Object
ms.openlocfilehash: 3b2db400c5a8a1c61ec30ecee07f91d29b5eb3c1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710795"
---
# New-Object

## SAMMANFATTNING
Skapar en instans av ett Microsoft .NET Framework-eller COM-objekt.

## SYNTAX

### NET (standard)

```
New-Object [-TypeName] <String> [[-ArgumentList] <Object[]>] [-Property <IDictionary>] [<CommonParameters>]
```

### Com

```
New-Object [-ComObject] <String> [-Strict] [-Property <IDictionary>] [<CommonParameters>]
```

## BESKRIVNING

`New-Object`Cmdleten skapar en instans av ett .NET Framework-eller COM-objekt.

Du kan ange antingen typen av en .NET Framework klass eller ett ProgID för ett COM-objekt. Som standard skriver du det fullständigt kvalificerade namnet för en .NET Framework-klass och cmdleten returnerar en referens till en instans av klassen. Om du vill skapa en instans av ett COM-objekt använder du parametern **ComObject** och anger objektets ProgID som värde.

## EXEMPEL

### Exempel 1: skapa ett system. version-objekt

I det här exemplet skapas ett **system. version** -objekt med hjälp av "1.2.3.4"-strängen som konstruktorn.

```powershell
New-Object -TypeName System.Version -ArgumentList "1.2.3.4"
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
1      2      3      4
```

### Exempel 2: skapa ett Internet Explorer COM-objekt

I det här exemplet skapas två instanser av COM-objektet som representerar Internet Explorer-programmet. Den första instansen använder hash-tabellen för **egenskaps** parametern för att anropa **Navigate2** -metoden och ange egenskapen **Visible** för objektet för `$True` att göra programmet synligt.
Den andra instansen får samma resultat med enskilda kommandon.

```powershell
$IE1 = New-Object -COMObject InternetExplorer.Application -Property @{Navigate2="www.microsoft.com"; Visible = $True}

# The following command gets the same results as the example above.
$IE2 = New-Object -COMObject InternetExplorer.Application`
$IE2.Navigate2("www.microsoft.com")`
$IE2.Visible = $True`
```

### Exempel 3: Använd den strikta parametern för att generera ett icke-avslutande fel

Det här exemplet visar att om du lägger till en **strikt** parameter `New-Object` genererar cmdleten ett icke-avslutande fel när com-objektet använder en interop-sammansättning.

```powershell
$A = New-Object -COMObject Word.Application -Strict -Property @{Visible = $True}
```

```Output
New-Object : The object written to the pipeline is an instance of the type
"Microsoft.Office.Interop.Word.ApplicationClass" from the component's primary interop assembly. If
this type exposes different members than the IDispatch members, scripts written to work with this
object might not work if the primary interop assembly is not installed.

At line:1 char:14
+ $A = New-Object  <<<< -COM Word.Application -Strict; $a.visible=$true
```

### Exempel 4: skapa ett COM-objekt för att hantera Windows-skrivbordet

Det här exemplet visar hur du skapar och använder ett COM-objekt för att hantera Windows-skrivbordet.

Det första kommandot använder **ComObject** -parametern för `New-Object` cmdleten för att skapa ett com-objekt med **Shell. Application** ProgID. Det lagrar det resulterande objektet i `$ObjShell` variabeln. Det andra kommandot rör `$ObjShell` variabeln till `Get-Member` cmdleten, som visar egenskaper och metoder för com-objektet. Metoden **ToggleDesktop** är mellan metoderna. Det tredje kommandot anropar **ToggleDesktop** -metoden för objektet för att minimera öppna fönster på Skriv bordet.

```powershell
$Objshell = New-Object -COMObject "Shell.Application"
$objshell | Get-Member
$objshell.ToggleDesktop()
```

```Output
   TypeName: System.__ComObject#{866738b9-6cf2-4de8-8767-f794ebe74f4e}

Name                 MemberType Definition
----                 ---------- ----------
AddToRecent          Method     void AddToRecent (Variant, string)
BrowseForFolder      Method     Folder BrowseForFolder (int, string, int, Variant)
CanStartStopService  Method     Variant CanStartStopService (string)
CascadeWindows       Method     void CascadeWindows ()
ControlPanelItem     Method     void ControlPanelItem (string)
EjectPC              Method     void EjectPC ()
Explore              Method     void Explore (Variant)
ExplorerPolicy       Method     Variant ExplorerPolicy (string)
FileRun              Method     void FileRun ()
FindComputer         Method     void FindComputer ()
FindFiles            Method     void FindFiles ()
FindPrinter          Method     void FindPrinter (string, string, string)
GetSetting           Method     bool GetSetting (int)
GetSystemInformation Method     Variant GetSystemInformation (string)
Help                 Method     void Help ()
IsRestricted         Method     int IsRestricted (string, string)
IsServiceRunning     Method     Variant IsServiceRunning (string)
MinimizeAll          Method     void MinimizeAll ()
NameSpace            Method     Folder NameSpace (Variant)
Open                 Method     void Open (Variant)
RefreshMenu          Method     void RefreshMenu ()
ServiceStart         Method     Variant ServiceStart (string, Variant)
ServiceStop          Method     Variant ServiceStop (string, Variant)
SetTime              Method     void SetTime ()
ShellExecute         Method     void ShellExecute (string, Variant, Variant, Variant, Variant)
ShowBrowserBar       Method     Variant ShowBrowserBar (string, Variant)
ShutdownWindows      Method     void ShutdownWindows ()
Suspend              Method     void Suspend ()
TileHorizontally     Method     void TileHorizontally ()
TileVertically       Method     void TileVertically ()
ToggleDesktop        Method     void ToggleDesktop ()
TrayProperties       Method     void TrayProperties ()
UndoMinimizeALL      Method     void UndoMinimizeALL ()
Windows              Method     IDispatch Windows ()
WindowsSecurity      Method     void WindowsSecurity ()
WindowSwitcher       Method     void WindowSwitcher ()
Application          Property   IDispatch Application () {get}
Parent               Property   IDispatch Parent () {get}
```

### Exempel 5: skicka flera argument till en konstruktor

Det här exemplet visar hur du skapar ett objekt med en konstruktor som tar flera parametrar. Parametrarna måste placeras i en matris när parametern **argument List** används.

```powershell
$array = @('One', 'Two', 'Three')
$parameters = @{
    TypeName = 'System.Collections.Generic.HashSet[string]'
    ArgumentList = ([string[]]$array, [System.StringComparer]::OrdinalIgnoreCase)
}
$set = New-Object @parameters
```

PowerShell binder varje medlem i matrisen till en parameter i konstruktorn.

> [!NOTE]
> I det här exemplet används parametern ihopbuntning för läsbarhet. Mer information finns i [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).

### Exempel 6: anropa en konstruktor som tar en matris som en enda parameter

Det här exemplet visar hur du skapar ett objekt med en konstruktor som tar en parameter som är en matris eller samling. Mat ris parametern måste placeras i en omsluten rad inuti en annan matris.

```powershell
$array = @('One', 'Two', 'Three')
# This command throws an exception.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList $array
# This command succeeds.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList (,[string[]]$array)
$set
```

```Output
New-Object : Cannot find an overload for "HashSet`1" and the argument count: "3".
At line:1 char:8
+ $set = New-Object -TypeName 'System.Collections.Generic.HashSet[strin ...
+        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidOperation: (:) [New-Object], MethodException
+ FullyQualifiedErrorId : ConstructorInvokedThrowException,Microsoft.PowerShell.Commands.NewObjectCommand

One
Two
Three
```

Det första försöket att skapa objektet i det här exemplet misslyckades. PowerShell försökte binda de tre medlemmarna av till- `$array` parametrarna för konstruktorn, men konstruktorn tar inte tre parametrar. `$array`Genom att figursätta i en annan matris förhindrar du att PowerShell försöker binda de tre medlemmarna av `$array` till-parametrarna för konstruktorn.

## PARAMETRAR

### – Argument List

Anger en matris med argument som ska skickas till konstruktorn för klassen .NET Framework. Om konstruktorn använder en enda parameter som är en matris måste du figursätta den parametern inuti en annan matris. Exempel:

`$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate -ArgumentList (,$bytes)`

Mer information om beteendet för **argument List** finns [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).

Aliaset för **argument List** är **argument**.

```yaml
Type: System.Object[]
Parameter Sets: Net
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComObject

Anger program-ID: n (ProgID) för COM-objektet.

```yaml
Type: System.String
Parameter Sets: Com
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Egenskap

Anger egenskaps värden och anropar metoder för det nya objektet.

Ange en hash-tabell där nycklarna är namnen på egenskaper eller metoder och värdena är egenskaps värden eller metod argument. `New-Object` skapar objektet och anger varje egenskaps värde och anropar varje metod i den ordning som de visas i hash-tabellen.

Om det nya objektet härleds från **PSObject** -klassen och du anger en egenskap som inte finns på objektet, `New-Object` lägger till den angivna egenskapen i objektet som en NoteProperty. Om objektet inte är ett **PSObject** genererar kommandot ett icke-avslutande fel.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Strikt

Anger att cmdleten genererar ett icke-avslutande fel när ett COM-objekt som du försöker skapa använder en interop-sammansättning. Den här funktionen särskiljer faktiska COM-objekt från .NET Framework objekt med COM-anropade omslutningar.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Com
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

Anger det fullständigt kvalificerade namnet på .NET Framework-klassen. Du kan inte ange både parametern **TypeName** och parametern **ComObject** .

```yaml
Type: System.String
Parameter Sets: Net
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inga

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Objekt

`New-Object` Returnerar det objekt som har skapats.

## ANTECKNINGAR

- `New-Object` innehåller de vanligaste funktionerna i funktionen VBScript CreateObject. En instruktion som `Set objShell = CreateObject("Shell.Application")` i VBScript kan översättas till `$objShell = New-Object -COMObject "Shell.Application"` i PowerShell.
- `New-Object` expanderar på de funktioner som är tillgängliga i Windows Script Host-miljön genom att göra det enkelt att arbeta med .NET Framework objekt från kommando raden och inom skript.

## RELATERADE LÄNKAR

[about_Object_Creation](../Microsoft.PowerShell.Core/About/about_Object_Creation.md)

[Jämför objekt](Compare-Object.md)

[Gruppera objekt](Group-Object.md)

[Mått – objekt](Measure-Object.md)

[Select-Object](Select-Object.md)

[Sortera objekt](Sort-Object.md)

[Tee – objekt](Tee-Object.md)

