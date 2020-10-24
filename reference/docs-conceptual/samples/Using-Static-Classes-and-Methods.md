---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Använd statiska klasser och metoder
description: Den här artikeln förklarar hur du identifierar och använder egenskaper och metoder för statiska .NET-klasser.
ms.openlocfilehash: 2e83fe442f7b3fdf62ceaab587450251ac4e7958
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501260"
---
# <a name="using-static-classes-and-methods"></a>Använd statiska klasser och metoder

Det går inte att skapa alla .NET Framework klasser med **New-Object**. Om du till exempel försöker skapa ett **system. Environment** -eller **system. math** -objekt med **New-Object**får du följande fel meddelanden:

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment

PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

Felen beror på att det inte finns något sätt att skapa ett nytt objekt från dessa klasser. Dessa klasser är referens bibliotek av metoder och egenskaper som inte ändrar tillstånd. Du behöver inte skapa dem. du använder dem bara. Klasser och metoder som dessa kallas *statiska klasser* eftersom de inte har skapats, förstörts eller ändrats. För att göra det här tydligt kommer vi att tillhandahålla exempel som använder statiska klasser.

## <a name="getting-environment-data-with-systemenvironment"></a>Hämta miljö data med system. Environment

Det första steget i att arbeta med ett objekt i Windows PowerShell är vanligt vis att använda Get-Member för att ta reda på vilka medlemmar det innehåller. Med statiska klasser är processen lite annorlunda eftersom den faktiska klassen inte är ett objekt.

### <a name="referring-to-the-static-systemenvironment-class"></a>Referera till den statiska system. Environment-klassen

Du kan referera till en statisk klass genom att omge klass namnet med hakparenteser. Du kan till exempel referera till **system. Environment** genom att skriva namnet inom hakparenteser. Då visas viss allmän typ information:

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> Som vi nämnt tidigare prepends "system" automatiskt i Windows PowerShell **.** för att skriva namn när du använder **nytt-objekt**. Samma sak händer när du använder ett namn för hakparenteser, så du kan ange ** \[ system. Environment]** som ** \[ miljö]**.

Klassen **system. Environment** innehåller allmän information om arbets miljön för den aktuella processen, vilket är powershell.exe när du arbetar i Windows PowerShell.

Om du försöker visa information om den här klassen genom att skriva ** \[ system. Environment] | Hämta medlem**, objekt typen rapporteras som **system. RuntimeType** , inte **system. Environment**:

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

Om du vill visa statiska medlemmar med Get-Member anger du den **statiska** parametern:

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

Nu kan vi välja egenskaper att visa från system. Environment.

### <a name="displaying-static-properties-of-systemenvironment"></a>Visar statiska egenskaper för system. Environment

Egenskaperna för system. Environment är också statiska och måste anges på ett annat sätt än för normala egenskaper. Vi använder **::** för att indikera för Windows PowerShell att vi vill arbeta med en statisk metod eller egenskap. För att se kommandot som användes för att starta Windows PowerShell, kontrollerar vi egenskapen **CommandLine** genom att skriva:

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

Kontrol lera operativ system versionen genom att visa egenskapen OSVersion genom att skriva:

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

Vi kan kontrol lera om datorn håller på att stängas av genom att visa egenskapen **HasShutdownStarted** :

```
PS> [System.Environment]::HasShutdownStarted
False
```

## <a name="doing-math-with-systemmath"></a>Gör matematik med system. math

Den statiska klassen system. math är användbar för att utföra vissa matematiska åtgärder. De viktiga medlemmarna i **system. matematik** är huvudsakligen metoder som vi kan visa med hjälp av **Get-Member**.

> [!NOTE]
> System. matematik har flera metoder med samma namn, men de åtskiljs av typen av parametrar.

Skriv följande kommando för att lista metoderna i klassen **system. math** .

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

Detta visar flera matematiska metoder. Här är en lista med kommandon som visar hur några av de vanliga metoderna fungerar:

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```
