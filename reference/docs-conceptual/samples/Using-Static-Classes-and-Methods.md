---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Använd statiska klasser och metoder
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: e4caff63a1ec7295b6fe450c2915baf0cc7e31af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086025"
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="10c07-103">Använd statiska klasser och metoder</span><span class="sxs-lookup"><span data-stu-id="10c07-103">Using Static Classes and Methods</span></span>

<span data-ttu-id="10c07-104">Inte alla .NET Framework-klasser som kan skapas med hjälp av **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="10c07-104">Not all .NET Framework classes can be created by using **New-Object**.</span></span> <span data-ttu-id="10c07-105">Exempel: Om du försöker skapa en **System.Environment** eller en **System.Math** objekt med **New-Object**, får du följande felmeddelanden:</span><span class="sxs-lookup"><span data-stu-id="10c07-105">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object**, you will get the following error messages:</span></span>

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

<span data-ttu-id="10c07-106">Dessa fel inträffa eftersom det finns inget sätt att skapa ett nytt objekt från de här klasserna.</span><span class="sxs-lookup"><span data-stu-id="10c07-106">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="10c07-107">De här klasserna är referensbibliotek av metoder och egenskaper som inte ändrar tillstånd.</span><span class="sxs-lookup"><span data-stu-id="10c07-107">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="10c07-108">Du behöver inte skapa dem, du helt enkelt använda dem för.</span><span class="sxs-lookup"><span data-stu-id="10c07-108">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="10c07-109">Klasser och metoder som dessa kallas *statiska klasser* eftersom de inte har skapats raderats eller ändrats.</span><span class="sxs-lookup"><span data-stu-id="10c07-109">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="10c07-110">Om du vill göra detta tydligt ger vi exempel som använder statiska klasser.</span><span class="sxs-lookup"><span data-stu-id="10c07-110">To make this clear we will provide examples that use static classes.</span></span>

## <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="10c07-111">Hämta miljödata med System.Environment</span><span class="sxs-lookup"><span data-stu-id="10c07-111">Getting Environment Data with System.Environment</span></span>

<span data-ttu-id="10c07-112">Det första steget i att arbeta med ett objekt i Windows PowerShell är vanligtvis att använda Get-Member för att ta reda på vilka medlemmar som den innehåller.</span><span class="sxs-lookup"><span data-stu-id="10c07-112">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="10c07-113">Processen skiljer sig något med statiska klasser, eftersom den faktiska klassen inte är ett objekt.</span><span class="sxs-lookup"><span data-stu-id="10c07-113">With static classes, the process is a little different because the actual class is not an object.</span></span>

### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="10c07-114">Refererar till den statiska System.Environment-klassen</span><span class="sxs-lookup"><span data-stu-id="10c07-114">Referring to the Static System.Environment Class</span></span>

<span data-ttu-id="10c07-115">Du kan referera till en statisk klass om klassnamnet med hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="10c07-115">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="10c07-116">Exempel: du kan referera till **System.Environment** genom att skriva namnet inom hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="10c07-116">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="10c07-117">Detta visar vissa allmänna typen information:</span><span class="sxs-lookup"><span data-stu-id="10c07-117">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="10c07-118">Som vi nämnde tidigare Windows PowerShell automatiskt läggs '**System.**'</span><span class="sxs-lookup"><span data-stu-id="10c07-118">As we mentioned previously, Windows PowerShell automatically prepends '**System.**'</span></span> <span data-ttu-id="10c07-119">Ange namn när du använder **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="10c07-119">to type names when you use **New-Object**.</span></span> <span data-ttu-id="10c07-120">Samma sak som händer när du använder en inom hakparenteser namn, så att du kan ange  **\[System.Environment]** som  **\[miljö]**.</span><span class="sxs-lookup"><span data-stu-id="10c07-120">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]**.</span></span>

<span data-ttu-id="10c07-121">Den **System.Environment** klassen innehåller allmän information om arbetsmiljö för den aktuella processen, vilket är powershell.exe när du arbetar i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="10c07-121">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="10c07-122">Om du vill visa detaljer för den här klassen genom att skriva  **\[System.Environment] | Get-Member**, typen av objekt som ska rapporteras som **System.RuntimeType** , inte **System.Environment**:</span><span class="sxs-lookup"><span data-stu-id="10c07-122">If you try to view details of this class by typing **\[System.Environment] | Get-Member**, the object type is reported as being **System.RuntimeType** , not **System.Environment**:</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="10c07-123">Om du vill visa statiska medlemmar med Get-Member, ange den **Statiska** parameter:</span><span class="sxs-lookup"><span data-stu-id="10c07-123">To view static members with Get-Member, specify the **Static** parameter:</span></span>

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

<span data-ttu-id="10c07-124">Nu kan vi välja Egenskaper för att visa från System.Environment.</span><span class="sxs-lookup"><span data-stu-id="10c07-124">We can now select properties to view from System.Environment.</span></span>

### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="10c07-125">Visa statiska egenskaperna för System.Environment</span><span class="sxs-lookup"><span data-stu-id="10c07-125">Displaying Static Properties of System.Environment</span></span>

<span data-ttu-id="10c07-126">Egenskaperna för System.Environment också är statiska och måste anges på ett annat sätt än normala egenskaper.</span><span class="sxs-lookup"><span data-stu-id="10c07-126">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="10c07-127">Vi använder **::** som anger att Windows PowerShell som vi vill arbeta med en statisk metod eller egenskap.</span><span class="sxs-lookup"><span data-stu-id="10c07-127">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="10c07-128">Om du vill se det kommando som användes för att starta Windows PowerShell, kontrollerar vi den **CommandLine** egenskapen genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="10c07-128">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="10c07-129">Om du vill kontrollera operativsystemets version, visa egenskapen OSVersion genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="10c07-129">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="10c07-130">Vi kan kontrollera om datorn är håller på att avslutas genom att visa den **HasShutdownStarted** egenskapen:</span><span class="sxs-lookup"><span data-stu-id="10c07-130">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

## <a name="doing-math-with-systemmath"></a><span data-ttu-id="10c07-131">Gör beräkningar med System.Math</span><span class="sxs-lookup"><span data-stu-id="10c07-131">Doing Math with System.Math</span></span>

<span data-ttu-id="10c07-132">Den statiska System.Math-klassen är användbart för att utföra vissa matematiska operationer.</span><span class="sxs-lookup"><span data-stu-id="10c07-132">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="10c07-133">Viktiga medlemmarna i **System.Math** är främst metoder, som vi kan visas med hjälp av **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="10c07-133">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member**.</span></span>

> [!NOTE]
> <span data-ttu-id="10c07-134">System.Math har flera metoder med samma namn, men de åtskiljs av typ av deras parametrar.</span><span class="sxs-lookup"><span data-stu-id="10c07-134">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="10c07-135">Skriv följande kommando för att listas metoderna för den **System.Math** klass.</span><span class="sxs-lookup"><span data-stu-id="10c07-135">Type the following command to list the methods of the **System.Math** class.</span></span>

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

<span data-ttu-id="10c07-136">Då visas flera matematiska metoder.</span><span class="sxs-lookup"><span data-stu-id="10c07-136">This displays several mathematical methods.</span></span> <span data-ttu-id="10c07-137">Här är en lista över kommandon som visar hur några av de vanliga metoderna fungerar:</span><span class="sxs-lookup"><span data-stu-id="10c07-137">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

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