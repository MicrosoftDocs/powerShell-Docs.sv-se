---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-member?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Member
ms.openlocfilehash: 290d19cb2bf04e22bf7855cb88467ed26ad42fe7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265040"
---
# Get-Member

## SAMMANFATTNING
Hämtar egenskaper och metoder för objekt.

## SYNTAX

```
Get-Member [-InputObject <PSObject>] [[-Name] <String[]>] [-MemberType <PSMemberTypes>]
 [-View <PSMemberViewTypes>] [-Static] [-Force] [<CommonParameters>]
```

## BESKRIVNING

Cmdlet: en `Get-Member` hämtar medlemmar, egenskaper och metoder för objekt.

Om du vill ange objektet använder du parametern **InputObject** eller pipe ett objekt till `Get-Member` . Om du vill hämta information om statiska medlemmar, medlemmar i klassen, inte i instansen, använder du den **statiska** parametern. Om du bara vill ha vissa typer av medlemmar, till exempel **NoteProperties** , använder du parametern **MemberType** .

## EXEMPEL

### Exempel 1: Hämta medlemmar i process objekt

Det här kommandot visar egenskaper och metoder för de tjänst objekt som genereras av `Get-Service` cmdleten.

Eftersom `Get-Member` delen av kommandot inte har några parametrar används standardvärden för parametrarna. Som standard `Get-Member` får inte statiska eller inre medlemmar som standard.

```powershell
Get-Service | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, System.EventArgs)
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(type requestedType)
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.ServiceControllerSt...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] DependentServices {get;}
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle ServiceHandle {get;}
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] ServicesDependedOn {get;}
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType {get;}
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartType {get;}
Status                    Property      System.ServiceProcess.ServiceControllerStatus Status {get;}
ToString                  ScriptMethod  System.Object ToString();
```

### Exempel 2: Hämta medlemmar av tjänst objekt

Det här exemplet hämtar alla medlemmar (egenskaper och metoder) för de tjänst objekt som hämtas av `Get-Service` cmdleten, inklusive de inre medlemmarna, till exempel **PSBase** , **PSObject** och **get_** och **set_** metoder.

```powershell
Get-Service | Get-Member -Force
(Get-Service Schedule).PSBase
```

`Get-Member`Kommandot använder **Force** -parametern för att lägga till de inre medlemmarna och skapade medlemmar av de objekt som ska visas. Du kan använda dessa egenskaper och metoder på samma sätt som du använder en anpassad metod för objektet. Det andra kommandot visar hur du visar värdet för egenskapen PSBase för tjänsten Schedule.

### Exempel 3: Hämta utökade medlemmar av tjänst objekt

I det här exemplet hämtas metoder och egenskaper för tjänst objekt som har utökats med hjälp av en `Types.ps1xml` fil eller `Add-Member` cmdlet.

```powershell
Get-Service | Get-Member -View Extended
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name             MemberType    Definition
----             ----------    ----------
Name             AliasProperty Name = ServiceName
RequiredServices AliasProperty RequiredServices = ServicesDependedOn
ToString         ScriptMethod  System.Object ToString();
```

`Get-Member`Kommandot använder parametern **View** för att bara hämta utökade medlemmar av tjänst objekt. I det här fallet är den utökade medlemmen egenskapen **Name** , som är en aliasresurspost för egenskapen **ServiceName** .

### Exempel 4: Hämta skript egenskaper för händelse logg objekt

I det här exemplet hämtas skript egenskaperna för händelse loggs objekt i system loggen i Loggboken.

```powershell
Get-WinEvent -LogName System -MaxEvents 1 | Get-Member -MemberType NoteProperty
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.EventLogRecord

Name    MemberType   Definition
----    ----------   ----------
Message NoteProperty string Message=The machine-default permission settings do not grant Local ...
```

Parametern **MemberType** hämtar endast objekt med värdet `NoteProperty` för deras **MemberType** -egenskap.

Kommandot returnerar **meddelande** egenskapen för **EventLogRecord** -objektet.

### Exempel 5: Hämta objekt med en angiven egenskap

Det här exemplet hämtar objekt som har egenskapen **MachineName** i utdata från en lista med cmdletar.

`$list`Variabeln innehåller en lista över cmdletar som ska utvärderas. I **förgrunds** deklarationen anropas varje kommando och skickar resultatet till `Get-Member` . Parametern **Name** begränsar resultatet från `Get-Member` till medlemmar som har namnet **MachineName**.

```powershell
$list = "Get-Process", "Get-Service", "Get-Culture", "Get-PSDrive", "Get-ExecutionPolicy"
foreach ($cmdlet in $list) {& $cmdlet | Get-Member -Name MachineName}
```

```Output
   TypeName: System.Diagnostics.Process

Name        MemberType Definition
----        ---------- ----------
MachineName Property   string MachineName {get;}

   TypeName: System.ServiceProcess.ServiceController

Name        MemberType Definition
----        ---------- ----------
MachineName Property   string MachineName {get;set;}
```

Resultaten visar att endast process objekt och tjänst objekt har egenskapen **MachineName** .

### Exempel 6: Hämta medlemmar för en matris

Det här exemplet visar hur du hittar medlemmarna i en objekt mat ris. När du rör och objekts mat ris till `Get-Member` , returnerar cmdleten en medlems lista för varje unik objekt typ i matrisen.
Om du skickar matrisen med parametern **InputObject** behandlas matrisen som ett enda objekt.

```powershell
$array = @(1,'hello')
$array | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType Definition
----        ---------- ----------
CompareTo   Method     int CompareTo(System.Object value), int CompareTo(int value), int ICompar...
Equals      Method     bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int...
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
GetTypeCode Method     System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method     bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method     byte IConvertible.ToByte(System.IFormatProvider provider)
...

   TypeName: System.String

Name                 MemberType            Definition
----                 ----------            ----------
Clone                Method                System.Object Clone(), System.Object ICloneable.Clone()
CompareTo            Method                int CompareTo(System.Object value), int CompareTo(str...
Contains             Method                bool Contains(string value), bool Contains(string val...
CopyTo               Method                void CopyTo(int sourceIndex, char[] destination, int ...
EndsWith             Method                bool EndsWith(string value), bool EndsWith(string val...
EnumerateRunes       Method                System.Text.StringRuneEnumerator EnumerateRunes()
Equals               Method                bool Equals(System.Object obj), bool Equals(string va...
GetEnumerator        Method                System.CharEnumerator GetEnumerator(), System.Collect...
GetHashCode          Method                int GetHashCode(), int GetHashCode(System.StringCompa...
...
```

```powershell
Get-Member -InputObject $array
```

```Output
   TypeName: System.Object[]

Name           MemberType            Definition
----           ----------            ----------
Add            Method                int IList.Add(System.Object value)
Address        Method                System.Object&, System.Private.CoreLib, Version=4.0.0.0, Cu...
Clear          Method                void IList.Clear()
Clone          Method                System.Object Clone(), System.Object ICloneable.Clone()
CompareTo      Method                int IStructuralComparable.CompareTo(System.Object other, Sy...
...
```

`$array`Variabeln innehåller ett **Int32** -objekt och ett **String** -objekt, som visas när matrisen är skickas `Get-Member` . När skickas `$array` med parametern **InputObject** `Get-Member` returnerar medlemmarna av typen **objekt []** .

### Exempel 7: Bestäm vilka objekt egenskaper du kan ange

Det här exemplet visar hur du avgör vilka egenskaper för ett objekt som kan ändras.

```powershell
$File = Get-Item c:\test\textFile.txt
$File.PSObject.Properties | Where-Object isSettable | Select-Object -Property Name
```

```Output
Name
----
PSPath
PSParentPath
PSChildName
PSDrive
PSProvider
PSIsContainer
IsReadOnly
CreationTime
CreationTimeUtc
LastAccessTime
LastAccessTimeUtc
LastWriteTime
LastWriteTimeUtc
Attributes
```

## PARAMETRAR

### -Force

Lägger till de inre medlemmarna och de kompilerade **get_** och **set_** metoder till visningen.
I följande lista beskrivs de egenskaper som läggs till när du använder parametern **Force** :

- **PSBase** : de ursprungliga egenskaperna för .net-objektet utan tillägg eller anpassning. Detta är de egenskaper som definierats för objekt klassen.
- **PSAdapted**. De egenskaper och metoder som definierats i PowerShell-systemet för utökad typ.
- **PSExtended**. De egenskaper och metoder som har lagts till i `Types.ps1xml` filerna eller med hjälp av `Add-Member` cmdleten.
- **PSObject**. Det kort som konverterar basobjektet till ett PowerShell **PSObject** -objekt.
- **PSTypeNames**. En lista med objekt typer som beskriver objektet, i angiven ordning. När du formaterar objektet söker PowerShell efter typerna i `Format.ps1xml` filerna i installations katalogen för PowerShell ( `$PSHOME` ). Format definitionen används för den första typ som hittas.

Som standard `Get-Member` hämtar dessa egenskaper i alla vyer förutom **bas** och **anpassade** , men de visas inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger det objekt vars medlemmar hämtas.

Att använda parametern **InputObject** är inte samma sak som att skicka ett objekt till `Get-Member` . Skillnader:

- När du rör en samling objekt till `Get-Member` `Get-Member` hämtar medlemmarna i de enskilda objekten i samlingen, till exempel egenskaperna för varje sträng i en sträng mat ris.
- När du använder **InputObject** för att skicka en samling objekt `Get-Member` hämtar medlemmarna i samlingen, till exempel egenskaperna för matrisen i en sträng mat ris.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – MemberType

Anger den medlems typ som denna cmdlet hämtar. Standardvärdet är **alla**.

De acceptabla värdena för den här parametern är:

- AliasProperty
- CodeProperty
- Egenskap
- NoteProperty
- ScriptProperty
- Egenskaper
- PropertySet
- Metod
- CodeMethod
- ScriptMethod
- Metoder
- ParameterizedProperty
- Mängd
- Händelse
- Dynamisk
- Alla

Information om dessa värden finns i [PSMemberTypes-uppräkning](/dotnet/api/system.management.automation.psmembertypes).

Alla objekt har inte alla typer av medlemmar. Om du anger en medlems typ som objektet inte har, returnerar PowerShell ett null-värde.

Om du vill hämta relaterade typer av medlemmar, till exempel alla utökade medlemmar, använder du parametern **View** . Om du använder parametern **MemberType** med parametrarna **static** eller **View** , `Get-Member` hämtar de medlemmar som tillhör båda uppsättningarna.

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger namnen på en eller flera egenskaper eller metoder för objektet. `Get-Member` hämtar endast de angivna egenskaperna och metoderna.

Om du använder parametern **Name** med parametern **MemberType** , **View** eller **static** `Get-Member` får bara de medlemmar som uppfyller kriterierna för alla parametrar.

Om du vill hämta en statisk medlem efter namn använder du den **statiska** parametern med parametern **Name** .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Static

Anger att denna cmdlet endast hämtar statiska egenskaper och metoder för objektet. Statiska egenskaper och metoder definieras i objekt klassen, inte på någon särskild instans av klassen.

Om du använder den **statiska** parametern med parametern **View** ignoreras parametern **View** .
Om du använder den **statiska** parametern med parametern **MemberType** `Get-Member` hämtar bara de medlemmar som tillhör båda uppsättningarna.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Visa

Anger att denna cmdlet endast hämtar egenskaper och metoder för vissa typer. Ange ett eller flera värden. Standardvärdet är **anpassad** och **utökad**.

De acceptabla värdena för den här parametern är:

- Grund. Hämtar endast ursprungliga egenskaper och metoder för .NET-objektet (utan tillägg eller anpassning).
- Justera. Hämtar endast de egenskaper och metoder som definierats i PowerShell-systemet för utökad typ.
- Extratextrad. Hämtar bara de egenskaper och metoder som har lagts till i en `Types.ps1xml` fil eller med hjälp av `Add-Member` cmdleten.
- Vissa. Hämtar medlemmarna i de grundläggande, anpassade och utökade vyerna.

Parametern **View** avgör vilka medlemmar som hämtas, inte bara visningen av dessa medlemmar.

Om du vill hämta särskilda medlems typer, till exempel skript egenskaper, använder du parametern **MemberType** . Om du använder parametrarna **MemberType** och **View** i samma kommando `Get-Member` hämtar de medlemmar som tillhör båda uppsättningarna. Om du använder parametrarna **static** och **View** i samma kommando ignoreras parametern **View** .

```yaml
Type: System.Management.Automation.PSMemberViewTypes
Parameter Sets: (All)
Aliases:
Accepted values: Extended, Adapted, Base, All

Required: False
Position: Named
Default value: Adapted, Extended
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka vidare alla objekt till `Get-Member` .

## UTDATA

### Microsoft. PowerShell. commands. MemberDefinition

`Get-Member` Returnerar ett objekt för varje egenskap eller metod som hämtas av.

## ANTECKNINGAR

Du kan hämta information om ett samlings objekt antingen med hjälp av parametern **InputObject** eller genom att skicka objektet, föregånget av ett komma, till `Get-Member` .

Du kan använda den `$This` automatiska variabeln i skript block som definierar värdena för nya egenskaper och metoder. `$This`Variabeln refererar till den instans av objektet som egenskaper och metoder läggs till i. Mer information om `$This` variabeln finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

Om du skickar ett objekt som representerar en _typ_ , t. ex. en typ sträng, till exempel `[int]` , `Get-Member` returnerar du information om `[System.RuntimeType]` typen. När du använder den **statiska** parametern `Get-Member` returnerar dock de statiska medlemmarna av den speciella typ som representeras av `System.RuntimeType` instansen.

## RELATERADE LÄNKAR

[Lägg till medlem](Add-Member.md)
