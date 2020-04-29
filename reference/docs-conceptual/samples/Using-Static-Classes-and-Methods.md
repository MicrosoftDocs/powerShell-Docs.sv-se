---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Använd statiska klasser och metoder
ms.openlocfilehash: 437e7b430f37224de7c617e120e37c3efcd7787a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030745"
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="c5d60-103">Använd statiska klasser och metoder</span><span class="sxs-lookup"><span data-stu-id="c5d60-103">Using Static Classes and Methods</span></span>

<span data-ttu-id="c5d60-104">Det går inte att skapa alla .NET Framework klasser med **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="c5d60-104">Not all .NET Framework classes can be created by using **New-Object**.</span></span> <span data-ttu-id="c5d60-105">Om du till exempel försöker skapa ett **system. Environment** -eller **system. math** -objekt med **New-Object**får du följande fel meddelanden:</span><span class="sxs-lookup"><span data-stu-id="c5d60-105">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object**, you will get the following error messages:</span></span>

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

<span data-ttu-id="c5d60-106">Felen beror på att det inte finns något sätt att skapa ett nytt objekt från dessa klasser.</span><span class="sxs-lookup"><span data-stu-id="c5d60-106">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="c5d60-107">Dessa klasser är referens bibliotek av metoder och egenskaper som inte ändrar tillstånd.</span><span class="sxs-lookup"><span data-stu-id="c5d60-107">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="c5d60-108">Du behöver inte skapa dem. du använder dem bara.</span><span class="sxs-lookup"><span data-stu-id="c5d60-108">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="c5d60-109">Klasser och metoder som dessa kallas *statiska klasser* eftersom de inte har skapats, förstörts eller ändrats.</span><span class="sxs-lookup"><span data-stu-id="c5d60-109">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="c5d60-110">För att göra det här tydligt kommer vi att tillhandahålla exempel som använder statiska klasser.</span><span class="sxs-lookup"><span data-stu-id="c5d60-110">To make this clear we will provide examples that use static classes.</span></span>

## <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="c5d60-111">Hämta miljö data med system. Environment</span><span class="sxs-lookup"><span data-stu-id="c5d60-111">Getting Environment Data with System.Environment</span></span>

<span data-ttu-id="c5d60-112">Det första steget i att arbeta med ett objekt i Windows PowerShell är vanligt vis att använda Get-Member för att ta reda på vilka medlemmar det innehåller.</span><span class="sxs-lookup"><span data-stu-id="c5d60-112">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="c5d60-113">Med statiska klasser är processen lite annorlunda eftersom den faktiska klassen inte är ett objekt.</span><span class="sxs-lookup"><span data-stu-id="c5d60-113">With static classes, the process is a little different because the actual class is not an object.</span></span>

### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="c5d60-114">Referera till den statiska system. Environment-klassen</span><span class="sxs-lookup"><span data-stu-id="c5d60-114">Referring to the Static System.Environment Class</span></span>

<span data-ttu-id="c5d60-115">Du kan referera till en statisk klass genom att omge klass namnet med hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="c5d60-115">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="c5d60-116">Du kan till exempel referera till **system. Environment** genom att skriva namnet inom hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="c5d60-116">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="c5d60-117">Då visas viss allmän typ information:</span><span class="sxs-lookup"><span data-stu-id="c5d60-117">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="c5d60-118">Som vi nämnt tidigare prepends "system" automatiskt i Windows PowerShell **.**</span><span class="sxs-lookup"><span data-stu-id="c5d60-118">As we mentioned previously, Windows PowerShell automatically prepends '**System.**'</span></span> <span data-ttu-id="c5d60-119">för att skriva namn när du använder **nytt-objekt**.</span><span class="sxs-lookup"><span data-stu-id="c5d60-119">to type names when you use **New-Object**.</span></span> <span data-ttu-id="c5d60-120">Samma sak händer när du använder ett namn för hakparenteser, så du kan ange \*\* \[system. Environment]\*\* som \*\* \[miljö]\*\*.</span><span class="sxs-lookup"><span data-stu-id="c5d60-120">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]**.</span></span>

<span data-ttu-id="c5d60-121">Klassen **system. Environment** innehåller allmän information om arbets miljön för den aktuella processen, som är PowerShell. exe när du arbetar i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c5d60-121">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="c5d60-122">Om du försöker visa information om den här klassen genom att skriva \*\* \[system. Environment] | Hämta medlem\*\*, objekt typen rapporteras som **system. RuntimeType** , inte **system. Environment**:</span><span class="sxs-lookup"><span data-stu-id="c5d60-122">If you try to view details of this class by typing **\[System.Environment] | Get-Member**, the object type is reported as being **System.RuntimeType** , not **System.Environment**:</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="c5d60-123">Om du vill visa statiska medlemmar med Get-Member anger du den **statiska** parametern:</span><span class="sxs-lookup"><span data-stu-id="c5d60-123">To view static members with Get-Member, specify the **Static** parameter:</span></span>

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

<span data-ttu-id="c5d60-124">Nu kan vi välja egenskaper att visa från system. Environment.</span><span class="sxs-lookup"><span data-stu-id="c5d60-124">We can now select properties to view from System.Environment.</span></span>

### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="c5d60-125">Visar statiska egenskaper för system. Environment</span><span class="sxs-lookup"><span data-stu-id="c5d60-125">Displaying Static Properties of System.Environment</span></span>

<span data-ttu-id="c5d60-126">Egenskaperna för system. Environment är också statiska och måste anges på ett annat sätt än för normala egenskaper.</span><span class="sxs-lookup"><span data-stu-id="c5d60-126">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="c5d60-127">Vi använder **::** för att indikera för Windows PowerShell att vi vill arbeta med en statisk metod eller egenskap.</span><span class="sxs-lookup"><span data-stu-id="c5d60-127">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="c5d60-128">För att se kommandot som användes för att starta Windows PowerShell, kontrollerar vi egenskapen **CommandLine** genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="c5d60-128">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="c5d60-129">Kontrol lera operativ system versionen genom att visa egenskapen OSVersion genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="c5d60-129">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="c5d60-130">Vi kan kontrol lera om datorn håller på att stängas av genom att visa egenskapen **HasShutdownStarted** :</span><span class="sxs-lookup"><span data-stu-id="c5d60-130">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

## <a name="doing-math-with-systemmath"></a><span data-ttu-id="c5d60-131">Gör matematik med system. math</span><span class="sxs-lookup"><span data-stu-id="c5d60-131">Doing Math with System.Math</span></span>

<span data-ttu-id="c5d60-132">Den statiska klassen system. math är användbar för att utföra vissa matematiska åtgärder.</span><span class="sxs-lookup"><span data-stu-id="c5d60-132">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="c5d60-133">De viktiga medlemmarna i **system. matematik** är huvudsakligen metoder som vi kan visa med hjälp av **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="c5d60-133">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member**.</span></span>

> [!NOTE]
> <span data-ttu-id="c5d60-134">System. matematik har flera metoder med samma namn, men de åtskiljs av typen av parametrar.</span><span class="sxs-lookup"><span data-stu-id="c5d60-134">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="c5d60-135">Skriv följande kommando för att lista metoderna i klassen **system. math** .</span><span class="sxs-lookup"><span data-stu-id="c5d60-135">Type the following command to list the methods of the **System.Math** class.</span></span>

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

<span data-ttu-id="c5d60-136">Detta visar flera matematiska metoder.</span><span class="sxs-lookup"><span data-stu-id="c5d60-136">This displays several mathematical methods.</span></span> <span data-ttu-id="c5d60-137">Här är en lista med kommandon som visar hur några av de vanliga metoderna fungerar:</span><span class="sxs-lookup"><span data-stu-id="c5d60-137">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

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
