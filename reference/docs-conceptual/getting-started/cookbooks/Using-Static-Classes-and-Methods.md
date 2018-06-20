---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Använd statiska klasser och metoder
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: 0f2b02c3a40365ad0335118b057a4e548c9f6535
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951859"
---
# <a name="using-static-classes-and-methods"></a>Använd statiska klasser och metoder
Inte alla klasser i .NET Framework kan skapas med hjälp av **New-Object**. Om du försöker skapa till exempel en **System.Environment** eller en **System.Math** objekt med **New-Object**, du får följande felmeddelanden:

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

Dessa fel inträffa eftersom det inte går att skapa ett nytt objekt från dessa klasser. De här klasserna är referens bibliotek med metoder och egenskaper som inte ändrar tillståndet. Du behöver inte skapa dem kan du bara använda. Klasser och metoder som dessa kallas *statiska klasser* förstörs eftersom de inte har skapats eller ändrats. Om du vill göra detta klart ger vi exempel som använder statiska klasser.

### <a name="getting-environment-data-with-systemenvironment"></a>Hämta miljödata med System.Environment
Vanligtvis är det första steget i att arbeta med ett objekt i Windows PowerShell att använda Get-medlem för att ta reda på vilka medlemmar som den innehåller. Processen är något annorlunda med statiska klasser, eftersom den faktiska klassen inte är ett objekt.

#### <a name="referring-to-the-static-systemenvironment-class"></a>Refererar till den statiska System.Environment klassen
Du kan referera till en statisk klass av omgivande klassnamnet med hakparenteser. Du kan till exempel referera till **System.Environment** genom att skriva namnet inom hakparenteser. Då visas vissa allmän typinformation:

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> Som vi nämnt tidigare Windows PowerShell automatiskt läggs '**System.**' Ange namn när du använder **New-Object**. Samma sak händer när du använder ett inom hakparenteser typnamn så att du kan ange  **\[System.Environment]** som  **\[miljö]**.

Den **System.Environment** klassen innehåller allmän information om arbetsmiljö för den aktuella processen är powershell.exe när du arbetar i Windows PowerShell.

Om du vill visa detaljer för den här klassen genom att skriva  **\[System.Environment] | Get-medlemmen**, typen av objekt som har rapporterats som **System.RuntimeType** , inte **System.Environment**:

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

Om du vill visa statiska medlemmarna med Get-medlem, ange den **Statiska** parameter:

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

Vi kan nu välja Egenskaper för att visa från System.Environment.

#### <a name="displaying-static-properties-of-systemenvironment"></a>Visa statiska egenskaperna för System.Environment

Egenskaper för System.Environment också är statiska och måste anges på ett annat sätt än normal egenskaper. Vi använder **::** att indikera att Windows PowerShell som vi vill arbeta med en statisk metod eller egenskap. Om du vill se det kommando som användes för att starta Windows PowerShell, vi kontrollerar den **CommandLine** egenskapen genom att skriva:

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

Kontrollera Operativsystemversionen genom att visa OSVersion-egenskapen genom att skriva:

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

Vi kan kontrollera om datorn håller på att avslutas genom att visa den **HasShutdownStarted** egenskapen:

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a>Gör beräkningar med System.Math

Den statiska System.Math-klassen är användbart för att utföra vissa matematiska åtgärder. Viktiga medlemmarna i **System.Math** är främst metoder som vi visa genom att använda **Get-medlemmen**.

> [!NOTE]
> System.Math har flera metoder med samma namn, men de åtskiljs av typ av deras parametrar.

Skriv följande kommando för att lista metoder av den **System.Math** klass.

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