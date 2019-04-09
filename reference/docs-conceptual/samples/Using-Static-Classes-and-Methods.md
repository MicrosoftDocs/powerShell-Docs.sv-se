---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Använd statiska klasser och metoder
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: e4caff63a1ec7295b6fe450c2915baf0cc7e31af
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293120"
---
# <a name="using-static-classes-and-methods"></a>Använd statiska klasser och metoder

Inte alla .NET Framework-klasser som kan skapas med hjälp av **New-Object**. Exempel: Om du försöker skapa en **System.Environment** eller en **System.Math** objekt med **New-Object**, får du följande felmeddelanden:

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

Dessa fel inträffa eftersom det finns inget sätt att skapa ett nytt objekt från de här klasserna. De här klasserna är referensbibliotek av metoder och egenskaper som inte ändrar tillstånd. Du behöver inte skapa dem, du helt enkelt använda dem för. Klasser och metoder som dessa kallas *statiska klasser* eftersom de inte har skapats raderats eller ändrats. Om du vill göra detta tydligt ger vi exempel som använder statiska klasser.

## <a name="getting-environment-data-with-systemenvironment"></a>Hämta miljödata med System.Environment

Det första steget i att arbeta med ett objekt i Windows PowerShell är vanligtvis att använda Get-Member för att ta reda på vilka medlemmar som den innehåller. Processen skiljer sig något med statiska klasser, eftersom den faktiska klassen inte är ett objekt.

### <a name="referring-to-the-static-systemenvironment-class"></a>Refererar till den statiska System.Environment-klassen

Du kan referera till en statisk klass om klassnamnet med hakparenteser. Exempel: du kan referera till **System.Environment** genom att skriva namnet inom hakparenteser. Detta visar vissa allmänna typen information:

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> Som vi nämnde tidigare Windows PowerShell automatiskt läggs '**System.**' Ange namn när du använder **New-Object**. Samma sak som händer när du använder en inom hakparenteser namn, så att du kan ange  **\[System.Environment]** som  **\[miljö]**.

Den **System.Environment** klassen innehåller allmän information om arbetsmiljö för den aktuella processen, vilket är powershell.exe när du arbetar i Windows PowerShell.

Om du vill visa detaljer för den här klassen genom att skriva  **\[System.Environment] | Get-Member**, typen av objekt som ska rapporteras som **System.RuntimeType** , inte **System.Environment**:

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

Om du vill visa statiska medlemmar med Get-Member, ange den **Statiska** parameter:

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

Nu kan vi välja Egenskaper för att visa från System.Environment.

### <a name="displaying-static-properties-of-systemenvironment"></a>Visa statiska egenskaperna för System.Environment

Egenskaperna för System.Environment också är statiska och måste anges på ett annat sätt än normala egenskaper. Vi använder **::** som anger att Windows PowerShell som vi vill arbeta med en statisk metod eller egenskap. Om du vill se det kommando som användes för att starta Windows PowerShell, kontrollerar vi den **CommandLine** egenskapen genom att skriva:

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

Om du vill kontrollera operativsystemets version, visa egenskapen OSVersion genom att skriva:

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

Vi kan kontrollera om datorn är håller på att avslutas genom att visa den **HasShutdownStarted** egenskapen:

```
PS> [System.Environment]::HasShutdownStarted
False
```

## <a name="doing-math-with-systemmath"></a>Gör beräkningar med System.Math

Den statiska System.Math-klassen är användbart för att utföra vissa matematiska operationer. Viktiga medlemmarna i **System.Math** är främst metoder, som vi kan visas med hjälp av **Get-Member**.

> [!NOTE]
> System.Math har flera metoder med samma namn, men de åtskiljs av typ av deras parametrar.

Skriv följande kommando för att listas metoderna för den **System.Math** klass.

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

Då visas flera matematiska metoder. Här är en lista över kommandon som visar hur några av de vanliga metoderna fungerar:

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