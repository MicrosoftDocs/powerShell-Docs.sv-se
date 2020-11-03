---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: 9a51c97def7cddf45c391ed91ff67ad97fbedf77
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/10/2020
ms.locfileid: "93269463"
---
# <span data-ttu-id="07a9e-103">Add-Type</span><span class="sxs-lookup"><span data-stu-id="07a9e-103">Add-Type</span></span>

## <span data-ttu-id="07a9e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="07a9e-104">SYNOPSIS</span></span>
<span data-ttu-id="07a9e-105">Lägger till en Microsoft .NET Core-klass till en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="07a9e-105">Adds a Microsoft .NET Core class to a PowerShell session.</span></span>

## <span data-ttu-id="07a9e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="07a9e-106">SYNTAX</span></span>

### <span data-ttu-id="07a9e-107">FromSource (standard)</span><span class="sxs-lookup"><span data-stu-id="07a9e-107">FromSource (Default)</span></span>

```
Add-Type [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="07a9e-108">FromMember</span><span class="sxs-lookup"><span data-stu-id="07a9e-108">FromMember</span></span>

```
Add-Type [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>]
 [-UsingNamespace <String[]>] [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="07a9e-109">FromPath</span><span class="sxs-lookup"><span data-stu-id="07a9e-109">FromPath</span></span>

```
Add-Type [-Path] <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="07a9e-110">FromLiteralPath</span><span class="sxs-lookup"><span data-stu-id="07a9e-110">FromLiteralPath</span></span>

```
Add-Type -LiteralPath <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="07a9e-111">FromAssemblyName</span><span class="sxs-lookup"><span data-stu-id="07a9e-111">FromAssemblyName</span></span>

```
Add-Type -AssemblyName <String[]> [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="07a9e-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="07a9e-112">DESCRIPTION</span></span>

<span data-ttu-id="07a9e-113">Med `Add-Type` cmdleten kan du definiera en Microsoft .net Core-klass i din PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="07a9e-113">The `Add-Type` cmdlet lets you define a Microsoft .NET Core class in your PowerShell session.</span></span> <span data-ttu-id="07a9e-114">Du kan sedan instansiera objekt med hjälp av `New-Object` cmdleten och använda objekten på samma sätt som du använder ett .net Core-objekt.</span><span class="sxs-lookup"><span data-stu-id="07a9e-114">You can then instantiate objects, by using the `New-Object` cmdlet, and use the objects just as you would use any .NET Core object.</span></span> <span data-ttu-id="07a9e-115">Om du lägger till ett `Add-Type` kommando i din PowerShell-profil, är klassen tillgänglig i alla PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="07a9e-115">If you add an `Add-Type` command to your PowerShell profile, the class is available in all PowerShell sessions.</span></span>

<span data-ttu-id="07a9e-116">Du kan ange typen genom att ange en befintlig sammansättning eller källfiler, eller så kan du ange käll koden infogad eller Sparad i en variabel.</span><span class="sxs-lookup"><span data-stu-id="07a9e-116">You can specify the type by specifying an existing assembly or source code files, or you can specify the source code inline or saved in a variable.</span></span> <span data-ttu-id="07a9e-117">Du kan även ange en metod och `Add-Type` definiera och generera klassen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-117">You can even specify only a method and `Add-Type` defines and generates the class.</span></span> <span data-ttu-id="07a9e-118">I Windows kan du använda den här funktionen för att göra plattforms anrop (P/Invoke)-anrop till ohanterade funktioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07a9e-118">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span> <span data-ttu-id="07a9e-119">Om du anger käll kod `Add-Type` kompilerar den angivna käll koden och genererar en minnes intern sammansättning som innehåller de nya .net Core-typerna.</span><span class="sxs-lookup"><span data-stu-id="07a9e-119">If you specify source code, `Add-Type` compiles the specified source code and generates an in-memory assembly that contains the new .NET Core types.</span></span>

<span data-ttu-id="07a9e-120">Du kan använda parametrarna för `Add-Type` för att ange ett alternativt språk och en kompilerare, C# är standard, kompilator alternativ, sammansättnings beroenden, klass namn område, namn på typen och den resulterande sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-120">You can use the parameters of `Add-Type` to specify an alternate language and compiler, C# is the default, compiler options, assembly dependencies, the class namespace, the names of the type, and the resulting assembly.</span></span>

## <span data-ttu-id="07a9e-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="07a9e-121">EXAMPLES</span></span>

### <span data-ttu-id="07a9e-122">Exempel 1: Lägg till en .NET-typ i en session</span><span class="sxs-lookup"><span data-stu-id="07a9e-122">Example 1: Add a .NET type to a session</span></span>

<span data-ttu-id="07a9e-123">I det här exemplet läggs klassen **BasicTest** till i sessionen genom att du anger käll koden som lagras i en variabel.</span><span class="sxs-lookup"><span data-stu-id="07a9e-123">This example adds the **BasicTest** class to the session by specifying source code that is stored in a variable.</span></span> <span data-ttu-id="07a9e-124">**BasicTest** -klassen används för att lägga till heltal, skapa ett objekt och multiplicera heltal.</span><span class="sxs-lookup"><span data-stu-id="07a9e-124">The **BasicTest** class is used to add integers, create an object, and multiply integers.</span></span>

```powershell
$Source = @"
public class BasicTest
{
  public static int Add(int a, int b)
    {
        return (a + b);
    }
  public int Multiply(int a, int b)
    {
    return (a * b);
    }
}
"@

Add-Type -TypeDefinition $Source
[BasicTest]::Add(4, 3)
$BasicTestObject = New-Object BasicTest
$BasicTestObject.Multiply(5, 2)
```

<span data-ttu-id="07a9e-125">`$Source`Variabeln lagrar käll koden för klassen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-125">The `$Source` variable stores the source code for the class.</span></span> <span data-ttu-id="07a9e-126">Typen har en statisk metod som kallas `Add` och en icke-statisk metod som kallas `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="07a9e-126">The type has a static method called `Add` and a non-static method called `Multiply`.</span></span>

<span data-ttu-id="07a9e-127">`Add-Type`Cmdleten lägger till klassen i sessionen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-127">The `Add-Type` cmdlet adds the class to the session.</span></span> <span data-ttu-id="07a9e-128">Eftersom den använder infogad källkod använder kommandot **TypeDefinition** -parametern för att ange koden i `$Source` variabeln.</span><span class="sxs-lookup"><span data-stu-id="07a9e-128">Because it's using inline source code, the command uses the **TypeDefinition** parameter to specify the code in the `$Source` variable.</span></span>

<span data-ttu-id="07a9e-129">Den `Add` statiska metoden i **BasicTest** -klassen använder dubbla kolon tecken ( `::` ) för att ange en statisk medlem i klassen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-129">The `Add` static method of the **BasicTest** class uses the double-colon characters (`::`) to specify a static member of the class.</span></span> <span data-ttu-id="07a9e-130">Heltalen läggs till och summan visas.</span><span class="sxs-lookup"><span data-stu-id="07a9e-130">The integers are added and the sum is displayed.</span></span>

<span data-ttu-id="07a9e-131">`New-Object`Cmdlet: en instansierar en instans av klassen **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="07a9e-131">The `New-Object` cmdlet instantiates an instance of the **BasicTest** class.</span></span> <span data-ttu-id="07a9e-132">Det sparar det nya objektet i `$BasicTestObject` variabeln.</span><span class="sxs-lookup"><span data-stu-id="07a9e-132">It saves the new object in the `$BasicTestObject` variable.</span></span>

<span data-ttu-id="07a9e-133">`$BasicTestObject` använder- `Multiply` metoden.</span><span class="sxs-lookup"><span data-stu-id="07a9e-133">`$BasicTestObject` uses the `Multiply` method.</span></span> <span data-ttu-id="07a9e-134">Heltalen multipliceras och produkten visas.</span><span class="sxs-lookup"><span data-stu-id="07a9e-134">The integers are multiplied and the product is displayed.</span></span>

### <span data-ttu-id="07a9e-135">Exempel 2: granska en tillagd typ</span><span class="sxs-lookup"><span data-stu-id="07a9e-135">Example 2: Examine an added type</span></span>

<span data-ttu-id="07a9e-136">I det här exemplet används `Get-Member` cmdleten för att undersöka de objekt som `Add-Type` `New-Object` cmdletarna och skapade i **exempel 1**.</span><span class="sxs-lookup"><span data-stu-id="07a9e-136">This example uses the `Get-Member` cmdlet to examine the objects that the `Add-Type` and `New-Object` cmdlets created in **Example 1**.</span></span>

```powershell
[BasicTest] | Get-Member
```

```Output
   TypeName: System.RuntimeType

Name                 MemberType Definition
----                 ---------- ----------
AsType               Method     type AsType()
Clone                Method     System.Object Clone(), System.Object ICloneable.Clone()
Equals               Method     bool Equals(System.Object obj), bool Equals(type o)
FindInterfaces       Method     type[] FindInterfaces(System.Reflection.TypeFilter filter...
...
```

```powershell
[BasicTest] | Get-Member -Static
```

```Output
  TypeName: BasicTest

Name            MemberType Definition
----            ---------- ----------
Add             Method     static int Add(int a, int b)
Equals          Method     static bool Equals(System.Object objA, System.Object objB)
new             Method     BasicTest new()
ReferenceEquals Method     static bool ReferenceEquals(System.Object objA, System.Object objB)
```

```powershell
$BasicTestObject | Get-Member
```

```Output
   TypeName: BasicTest

Name        MemberType Definition
----        ---------- ----------
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
Multiply    Method     int Multiply(int a, int b)
ToString    Method     string ToString()
```

<span data-ttu-id="07a9e-137">`Get-Member`Cmdleten hämtar typ och medlemmar i **BasicTest** -klassen som `Add-Type` har lagts till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-137">The `Get-Member` cmdlet gets the type and members of the **BasicTest** class that `Add-Type` added to the session.</span></span> <span data-ttu-id="07a9e-138">`Get-Member`Kommandot visar att det är ett **system. RuntimeType** -objekt, som härleds från klassen **system. Object** .</span><span class="sxs-lookup"><span data-stu-id="07a9e-138">The `Get-Member` command reveals that it's a **System.RuntimeType** object, which is derived from the **System.Object** class.</span></span>

<span data-ttu-id="07a9e-139">Den `Get-Member` **statiska** parametern hämtar statiska egenskaper och metoder för klassen **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="07a9e-139">The `Get-Member` **Static** parameter gets the static properties and methods of the **BasicTest** class.</span></span> <span data-ttu-id="07a9e-140">Utdata visar att `Add` metoden ingår.</span><span class="sxs-lookup"><span data-stu-id="07a9e-140">The output shows that the `Add` method is included.</span></span>

<span data-ttu-id="07a9e-141">`Get-Member`Cmdlet: en hämtar medlemmarna i objektet som lagras i `$BasicTestObject` variabeln.</span><span class="sxs-lookup"><span data-stu-id="07a9e-141">The `Get-Member` cmdlet gets the members of the object stored in the `$BasicTestObject` variable.</span></span>
<span data-ttu-id="07a9e-142">`$BasicTestObject` har skapats med hjälp av `New-Object` cmdleten med klassen **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="07a9e-142">`$BasicTestObject` was created by using the `New-Object` cmdlet with the **BasicTest** class.</span></span> <span data-ttu-id="07a9e-143">Utdata visar att värdet för `$BasicTestObject` variabeln är en instans av klassen **BasicTest** och att den innehåller en medlem som kallas `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="07a9e-143">The output reveals that the value of the `$BasicTestObject` variable is an instance of the **BasicTest** class and that it includes a member called `Multiply`.</span></span>

### <span data-ttu-id="07a9e-144">Exempel 3: lägga till typer från en sammansättning</span><span class="sxs-lookup"><span data-stu-id="07a9e-144">Example 3: Add types from an assembly</span></span>

<span data-ttu-id="07a9e-145">I det här exemplet läggs klasserna från `NJsonSchema.dll` sammansättningen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-145">This example adds the classes from the `NJsonSchema.dll` assembly to the current session.</span></span>

```powershell
Set-Location -Path $PSHOME
$AccType = Add-Type -AssemblyName *jsonschema* -PassThru
```

<span data-ttu-id="07a9e-146">`Set-Location` använder parametern **Path** för att ange `$PSHOME` variabeln.</span><span class="sxs-lookup"><span data-stu-id="07a9e-146">`Set-Location` uses the **Path** parameter to specify the `$PSHOME` variable.</span></span> <span data-ttu-id="07a9e-147">Variabeln refererar till PowerShell-installations katalogen där DLL-filen finns.</span><span class="sxs-lookup"><span data-stu-id="07a9e-147">The variable references the PowerShell installation directory where the DLL file is located.</span></span>

<span data-ttu-id="07a9e-148">`$AccType`Variabeln lagrar ett objekt som skapats med `Add-Type` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="07a9e-148">The `$AccType` variable stores an object created with the `Add-Type` cmdlet.</span></span> <span data-ttu-id="07a9e-149">`Add-Type` använder parametern **AssemblyName** för att ange namnet på sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-149">`Add-Type` uses the **AssemblyName** parameter to specify the name of the assembly.</span></span> <span data-ttu-id="07a9e-150">Med jokertecknet asterisk ( `*` ) kan du hämta rätt sammansättning även om du inte är säker på namnet eller stavningen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-150">The asterisk (`*`) wildcard character allows you to get the correct assembly even when you aren't sure of the name or its spelling.</span></span> <span data-ttu-id="07a9e-151">Parametern **Passthru** genererar objekt som representerar de klasser som läggs till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-151">The **PassThru** parameter generates objects that represent the classes that are added to the session.</span></span>

### <span data-ttu-id="07a9e-152">Exempel 4: anropa inbyggda Windows-API: er</span><span class="sxs-lookup"><span data-stu-id="07a9e-152">Example 4: Call native Windows APIs</span></span>

<span data-ttu-id="07a9e-153">Det här exemplet visar hur du anropar inbyggda Windows-API: er i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07a9e-153">This example demonstrates how to call native Windows APIs in PowerShell.</span></span> <span data-ttu-id="07a9e-154">`Add-Type` använder mekanismen för plattforms anrop (P/Invoke) för att anropa en funktion i `User32.dll` från PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07a9e-154">`Add-Type` uses the Platform Invoke (P/Invoke) mechanism to call a function in `User32.dll` from PowerShell.</span></span> <span data-ttu-id="07a9e-155">Det här exemplet fungerar endast på datorer som kör operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="07a9e-155">This example only works on computers running the Windows operating system.</span></span>

```powershell
$Signature = @"
[DllImport("user32.dll")]public static extern bool ShowWindowAsync(IntPtr hWnd, int nCmdShow);
"@

$ShowWindowAsync = Add-Type -MemberDefinition $Signature -Name "Win32ShowWindowAsync" -Namespace Win32Functions -PassThru

# Minimize the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $pid).MainWindowHandle, 2)

# Restore the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $Pid).MainWindowHandle, 4)
```

<span data-ttu-id="07a9e-156">`$Signature`Variabeln lagrar C#-signaturen för `ShowWindowAsync` funktionen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-156">The `$Signature` variable stores the C# signature of the `ShowWindowAsync` function.</span></span> <span data-ttu-id="07a9e-157">För att säkerställa att den resulterande metoden visas i en PowerShell-session har `public` nyckelordet lagts till i standard-signaturen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-157">To ensure that the resulting method is visible in a PowerShell session, the `public` keyword was added to the standard signature.</span></span> <span data-ttu-id="07a9e-158">Mer information finns i [ShowWindowAsync-funktionen](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span><span class="sxs-lookup"><span data-stu-id="07a9e-158">For more information, see [ShowWindowAsync function](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span></span>

<span data-ttu-id="07a9e-159">`$ShowWindowAsync`Variabeln lagrar objektet som skapats av parametern `Add-Type` **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="07a9e-159">The `$ShowWindowAsync` variable stores the object created by the `Add-Type` **PassThru** parameter.</span></span>
<span data-ttu-id="07a9e-160">`Add-Type`Cmdleten lägger till `ShowWindowAsync` funktionen i PowerShell-sessionen som en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="07a9e-160">The `Add-Type` cmdlet adds the `ShowWindowAsync` function to the PowerShell session as a static method.</span></span> <span data-ttu-id="07a9e-161">Kommandot använder parametern **MemberDefinition** för att ange den metod definition som sparats i `$Signature` variabeln.</span><span class="sxs-lookup"><span data-stu-id="07a9e-161">The command uses the **MemberDefinition** parameter to specify the method definition saved in the `$Signature` variable.</span></span> <span data-ttu-id="07a9e-162">Kommandot använder **namn** och namn **områdes** parametrar för att ange ett namn och ett namn område för klassen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-162">The command uses the **Name** and **Namespace** parameters to specify a name and namespace for the class.</span></span> <span data-ttu-id="07a9e-163">Parametern **Passthru** genererar ett objekt som representerar typerna.</span><span class="sxs-lookup"><span data-stu-id="07a9e-163">The **PassThru** parameter generates an object that represents the types.</span></span>

<span data-ttu-id="07a9e-164">Den nya `ShowWindowAsync` statiska metoden används i kommandona för att minimera och återställa PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-164">The new `ShowWindowAsync` static method is used in the commands to minimize and restore the PowerShell console.</span></span> <span data-ttu-id="07a9e-165">Metoden tar två parametrar: fönster handtaget och ett heltal som anger hur fönstret visas.</span><span class="sxs-lookup"><span data-stu-id="07a9e-165">The method takes two parameters: the window handle, and an integer that specifies how the window is displayed.</span></span>

<span data-ttu-id="07a9e-166">För att minimera PowerShell-konsolen, `ShowWindowAsync` använder `Get-Process` cmdleten med den `$PID` automatiska variabeln för att hämta den process som är värd för den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-166">To minimize the PowerShell console, `ShowWindowAsync` uses the `Get-Process` cmdlet with the `$PID` automatic variable to get the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="07a9e-167">Sedan används egenskapen **MainWindowHandle** för den aktuella processen och värdet `2` , som representerar `SW_MINIMIZE` värdet.</span><span class="sxs-lookup"><span data-stu-id="07a9e-167">Then it uses the **MainWindowHandle** property of the current process and a value of `2`, which represents the `SW_MINIMIZE` value.</span></span>

<span data-ttu-id="07a9e-168">För att återställa fönstret `ShowWindowAsync` använder värdet `4` för fönstrets position, som representerar `SW_RESTORE` värdet.</span><span class="sxs-lookup"><span data-stu-id="07a9e-168">To restore the window, `ShowWindowAsync` uses a value of `4` for the window position, which represents the `SW_RESTORE` value.</span></span>

<span data-ttu-id="07a9e-169">Maximera fönstret genom att använda värdet för `3` som representerar `SW_MAXIMIZE` .</span><span class="sxs-lookup"><span data-stu-id="07a9e-169">To maximize the window, use the value of `3` that represents `SW_MAXIMIZE`.</span></span>

## <span data-ttu-id="07a9e-170">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="07a9e-170">PARAMETERS</span></span>

### <span data-ttu-id="07a9e-171">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="07a9e-171">-AssemblyName</span></span>

<span data-ttu-id="07a9e-172">Anger namnet på en sammansättning som innehåller typerna.</span><span class="sxs-lookup"><span data-stu-id="07a9e-172">Specifies the name of an assembly that includes the types.</span></span> <span data-ttu-id="07a9e-173">`Add-Type` tar typer från den angivna sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-173">`Add-Type` takes the types from the specified assembly.</span></span> <span data-ttu-id="07a9e-174">Den här parametern krävs när du skapar typer baserat på ett sammansättnings namn.</span><span class="sxs-lookup"><span data-stu-id="07a9e-174">This parameter is required when you're creating types based on an assembly name.</span></span>

<span data-ttu-id="07a9e-175">Ange det fullständiga eller enkla namnet, även kallat det partiella namnet för en sammansättning.</span><span class="sxs-lookup"><span data-stu-id="07a9e-175">Enter the full or simple name, also known as the partial name, of an assembly.</span></span> <span data-ttu-id="07a9e-176">Jokertecken tillåts i sammansättnings namnet.</span><span class="sxs-lookup"><span data-stu-id="07a9e-176">Wildcard characters are permitted in the assembly name.</span></span> <span data-ttu-id="07a9e-177">Om du anger ett enkelt eller partiellt namn `Add-Type` matchas det med det fullständiga namnet och sedan används det fullständiga namnet för att läsa in sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-177">If you enter a simple or partial name, `Add-Type` resolves it to the full name, and then uses the full name to load the assembly.</span></span>

<span data-ttu-id="07a9e-178">Den här parametern accepterar inte en sökväg eller ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="07a9e-178">This parameter doesn't accept a path or a filename.</span></span> <span data-ttu-id="07a9e-179">Om du vill ange sökvägen till DLL-filen för Assembly-DLL-filen använder du parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="07a9e-179">To enter the path to the assembly dynamic-link library (DLL) file, use the **Path** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromAssemblyName
Aliases: AN

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="07a9e-180">-CompilerOptions</span><span class="sxs-lookup"><span data-stu-id="07a9e-180">-CompilerOptions</span></span>

<span data-ttu-id="07a9e-181">Anger alternativ för käll kods kompileraren.</span><span class="sxs-lookup"><span data-stu-id="07a9e-181">Specifies the options for the source code compiler.</span></span> <span data-ttu-id="07a9e-182">De här alternativen skickas till kompilatorn utan revidering.</span><span class="sxs-lookup"><span data-stu-id="07a9e-182">These options are sent to the compiler without revision.</span></span>

<span data-ttu-id="07a9e-183">Med den här parametern kan du dirigera kompilatorn för att generera en körbar fil, bädda in resurser eller ange kommando rads alternativ, till exempel `/unsafe` alternativet.</span><span class="sxs-lookup"><span data-stu-id="07a9e-183">This parameter allows you to direct the compiler to generate an executable file, embed resources, or set command-line options, such as the `/unsafe` option.</span></span>

<span data-ttu-id="07a9e-184">Du kan inte använda parametrarna **CompilerOptions** och **ReferencedAssemblies** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="07a9e-184">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="07a9e-185">-IgnoreWarnings</span><span class="sxs-lookup"><span data-stu-id="07a9e-185">-IgnoreWarnings</span></span>

<span data-ttu-id="07a9e-186">Ignorerar kompilator varningar.</span><span class="sxs-lookup"><span data-stu-id="07a9e-186">Ignores compiler warnings.</span></span> <span data-ttu-id="07a9e-187">Använd den här parametern för att förhindra `Add-Type` hantering av kompilator varningar som fel.</span><span class="sxs-lookup"><span data-stu-id="07a9e-187">Use this parameter to prevent `Add-Type` from handling compiler warnings as errors.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="07a9e-188">– Språk</span><span class="sxs-lookup"><span data-stu-id="07a9e-188">-Language</span></span>

<span data-ttu-id="07a9e-189">Anger det språk som används i käll koden.</span><span class="sxs-lookup"><span data-stu-id="07a9e-189">Specifies the language that is used in the source code.</span></span> <span data-ttu-id="07a9e-190">Det acceptabla värdet för den här parametern är **csharp**.</span><span class="sxs-lookup"><span data-stu-id="07a9e-190">The acceptable value for this parameter is **CSharp**.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.Language
Parameter Sets: FromSource, FromMember
Aliases:
Accepted values: CSharp

Required: False
Position: Named
Default value: CSharp
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="07a9e-191">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="07a9e-191">-LiteralPath</span></span>

<span data-ttu-id="07a9e-192">Anger sökvägen till käll kods filer eller sammansättnings-DLL-filer som innehåller typerna.</span><span class="sxs-lookup"><span data-stu-id="07a9e-192">Specifies the path to source code files or assembly DLL files that contain the types.</span></span> <span data-ttu-id="07a9e-193">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det skrivs.</span><span class="sxs-lookup"><span data-stu-id="07a9e-193">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="07a9e-194">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="07a9e-194">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="07a9e-195">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="07a9e-195">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="07a9e-196">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="07a9e-196">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="07a9e-197">-MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="07a9e-197">-MemberDefinition</span></span>

<span data-ttu-id="07a9e-198">Anger nya egenskaper eller metoder för klassen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-198">Specifies new properties or methods for the class.</span></span> <span data-ttu-id="07a9e-199">`Add-Type` skapar den mallkod som krävs för att stödja egenskaper eller metoder.</span><span class="sxs-lookup"><span data-stu-id="07a9e-199">`Add-Type` generates the template code that is required to support the properties or methods.</span></span>

<span data-ttu-id="07a9e-200">I Windows kan du använda den här funktionen för att göra plattforms anrop (P/Invoke)-anrop till ohanterade funktioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07a9e-200">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="07a9e-201">-Name</span><span class="sxs-lookup"><span data-stu-id="07a9e-201">-Name</span></span>

<span data-ttu-id="07a9e-202">Anger namnet på den klass som ska skapas.</span><span class="sxs-lookup"><span data-stu-id="07a9e-202">Specifies the name of the class to create.</span></span> <span data-ttu-id="07a9e-203">Den här parametern krävs när en typ skapas från en medlems definition.</span><span class="sxs-lookup"><span data-stu-id="07a9e-203">This parameter is required when generating a type from a member definition.</span></span>

<span data-ttu-id="07a9e-204">Typ namnet och namn området måste vara unikt inom en session.</span><span class="sxs-lookup"><span data-stu-id="07a9e-204">The type name and namespace must be unique within a session.</span></span> <span data-ttu-id="07a9e-205">Du kan inte ta bort en typ eller ändra den.</span><span class="sxs-lookup"><span data-stu-id="07a9e-205">You can't unload a type or change it.</span></span>
<span data-ttu-id="07a9e-206">Om du vill ändra koden för en typ måste du ändra namnet eller starta en ny PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="07a9e-206">To change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="07a9e-207">Annars Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="07a9e-207">Otherwise, the command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="07a9e-208">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="07a9e-208">-Namespace</span></span>

<span data-ttu-id="07a9e-209">Anger ett namn område för typen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-209">Specifies a namespace for the type.</span></span>

<span data-ttu-id="07a9e-210">Om den här parametern inte ingår i kommandot skapas typen i namn området **Microsoft. PowerShell. commands. AddType. AutoGeneratedTypes** .</span><span class="sxs-lookup"><span data-stu-id="07a9e-210">If this parameter isn't included in the command, the type is created in the **Microsoft.PowerShell.Commands.AddType.AutoGeneratedTypes** namespace.</span></span> <span data-ttu-id="07a9e-211">Om parametern ingår i kommandot med ett tomt sträng värde eller ett värde av `$Null` genereras typen i det globala namn området.</span><span class="sxs-lookup"><span data-stu-id="07a9e-211">If the parameter is included in the command with an empty string value or a value of `$Null`, the type is generated in the global namespace.</span></span>

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="07a9e-212">-OutputAssembly</span><span class="sxs-lookup"><span data-stu-id="07a9e-212">-OutputAssembly</span></span>

<span data-ttu-id="07a9e-213">Genererar en DLL-fil för sammansättningen med det angivna namnet på platsen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-213">Generates a DLL file for the assembly with the specified name in the location.</span></span> <span data-ttu-id="07a9e-214">Ange en valfri sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="07a9e-214">Enter an optional path and filename.</span></span> <span data-ttu-id="07a9e-215">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="07a9e-215">Wildcard characters are permitted.</span></span> <span data-ttu-id="07a9e-216">Som standard `Add-Type` genererar sammansättningen endast i minnet.</span><span class="sxs-lookup"><span data-stu-id="07a9e-216">By default, `Add-Type` generates the assembly only in memory.</span></span>

```yaml
Type: System.String
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="07a9e-217">– OutputType</span><span class="sxs-lookup"><span data-stu-id="07a9e-217">-OutputType</span></span>

<span data-ttu-id="07a9e-218">Anger utdatatypen för den utgående sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-218">Specifies the output type of the output assembly.</span></span> <span data-ttu-id="07a9e-219">Som standard har ingen Utdatatyp angetts.</span><span class="sxs-lookup"><span data-stu-id="07a9e-219">By default, no output type is specified.</span></span> <span data-ttu-id="07a9e-220">Den här parametern är endast giltig när en utgående sammansättning anges i kommandot.</span><span class="sxs-lookup"><span data-stu-id="07a9e-220">This parameter is valid only when an output assembly is specified in the command.</span></span> <span data-ttu-id="07a9e-221">Mer information om värdena finns i OutputAssemblyType- [uppräkning](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span><span class="sxs-lookup"><span data-stu-id="07a9e-221">For more information about the values, see [OutputAssemblyType Enumeration](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span></span>

<span data-ttu-id="07a9e-222">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="07a9e-222">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="07a9e-223">ConsoleApplication</span><span class="sxs-lookup"><span data-stu-id="07a9e-223">ConsoleApplication</span></span>
- <span data-ttu-id="07a9e-224">Bibliotek</span><span class="sxs-lookup"><span data-stu-id="07a9e-224">Library</span></span>
- <span data-ttu-id="07a9e-225">WindowsApplication</span><span class="sxs-lookup"><span data-stu-id="07a9e-225">WindowsApplication</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07a9e-226">`ConsoleApplication`Värdena och kan inte `WindowsApplication` producera fungerande utdata och bör inte användas.</span><span class="sxs-lookup"><span data-stu-id="07a9e-226">The `ConsoleApplication` and `WindowsApplication` values don't produce working output and should not be used.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutputAssemblyType
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OT
Accepted values: ConsoleApplication, Library, WindowsApplication

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="07a9e-227">– PassThru</span><span class="sxs-lookup"><span data-stu-id="07a9e-227">-PassThru</span></span>

<span data-ttu-id="07a9e-228">Returnerar ett **system. Runtime** -objekt som representerar de typer som har lagts till.</span><span class="sxs-lookup"><span data-stu-id="07a9e-228">Returns a **System.Runtime** object that represents the types that were added.</span></span> <span data-ttu-id="07a9e-229">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="07a9e-229">By default, this cmdlet doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="07a9e-230">-Path</span><span class="sxs-lookup"><span data-stu-id="07a9e-230">-Path</span></span>

<span data-ttu-id="07a9e-231">Anger sökvägen till käll kods filer eller sammansättnings-DLL-filer som innehåller typerna.</span><span class="sxs-lookup"><span data-stu-id="07a9e-231">Specifies the path to source code files or assembly DLL files that contain the types.</span></span>

<span data-ttu-id="07a9e-232">Om du skickar källfiler `Add-Type` kompilerar koden i filerna och skapar en minnes intern sammansättning av typerna.</span><span class="sxs-lookup"><span data-stu-id="07a9e-232">If you submit source code files, `Add-Type` compiles the code in the files and creates an in-memory assembly of the types.</span></span> <span data-ttu-id="07a9e-233">Fil tillägget som anges i **Path** -värdet avgör vilken kompilator som `Add-Type` använder.</span><span class="sxs-lookup"><span data-stu-id="07a9e-233">The file extension specified in the value of **Path** determines the compiler that `Add-Type` uses.</span></span>

<span data-ttu-id="07a9e-234">Om du skickar en sammansättnings fil, `Add-Type` tar de olika typerna från sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-234">If you submit an assembly file, `Add-Type` takes the types from the assembly.</span></span> <span data-ttu-id="07a9e-235">Om du vill ange en minnes intern sammansättning eller Global Assembly Cache använder du parametern **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="07a9e-235">To specify an in-memory assembly or the global assembly cache, use the **AssemblyName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="07a9e-236">-ReferencedAssemblies</span><span class="sxs-lookup"><span data-stu-id="07a9e-236">-ReferencedAssemblies</span></span>

<span data-ttu-id="07a9e-237">Anger de sammansättningar som typen är beroende av.</span><span class="sxs-lookup"><span data-stu-id="07a9e-237">Specifies the assemblies upon which the type depends.</span></span> <span data-ttu-id="07a9e-238">Som standard `Add-Type` refererar `System.dll` och `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="07a9e-238">By default, `Add-Type` references `System.dll` and `System.Management.Automation.dll`.</span></span> <span data-ttu-id="07a9e-239">De sammansättningar som du anger med hjälp av den här parametern refereras till utöver standard sammansättningarna.</span><span class="sxs-lookup"><span data-stu-id="07a9e-239">The assemblies that you specify by using this parameter are referenced in addition to the default assemblies.</span></span>

<span data-ttu-id="07a9e-240">Från och med PowerShell 6 inkluderar **ReferencedAssemblies** inte standard-.net-sammansättningarna.</span><span class="sxs-lookup"><span data-stu-id="07a9e-240">Beginning in PowerShell 6, **ReferencedAssemblies** doesn't include the default .NET assemblies.</span></span> <span data-ttu-id="07a9e-241">Du måste inkludera en speciell referens till dem i värdet som skickas till den här parametern.</span><span class="sxs-lookup"><span data-stu-id="07a9e-241">You must include a specific reference to them in the value passed to this parameter.</span></span>

<span data-ttu-id="07a9e-242">Du kan inte använda parametrarna **CompilerOptions** och **ReferencedAssemblies** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="07a9e-242">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: RA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="07a9e-243">-TypeDefinition</span><span class="sxs-lookup"><span data-stu-id="07a9e-243">-TypeDefinition</span></span>

<span data-ttu-id="07a9e-244">Anger den käll kod som innehåller typ definitionerna.</span><span class="sxs-lookup"><span data-stu-id="07a9e-244">Specifies the source code that contains the type definitions.</span></span> <span data-ttu-id="07a9e-245">Ange käll koden i en sträng eller här – sträng, eller ange en variabel som innehåller käll koden.</span><span class="sxs-lookup"><span data-stu-id="07a9e-245">Enter the source code in a string or here-string, or enter a variable that contains the source code.</span></span> <span data-ttu-id="07a9e-246">Mer information om här – strängar finns [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="07a9e-246">For more information about here-strings, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span></span>

<span data-ttu-id="07a9e-247">Ta med en namn områdes deklaration i din typ definition.</span><span class="sxs-lookup"><span data-stu-id="07a9e-247">Include a namespace declaration in your type definition.</span></span> <span data-ttu-id="07a9e-248">Om du utelämnar namn områdes deklarationen kan typen ha samma namn som en annan typ eller genvägen till en annan typ, vilket orsakar en oavsiktlig överskrivning.</span><span class="sxs-lookup"><span data-stu-id="07a9e-248">If you omit the namespace declaration, your type might have the same name as another type or the shortcut for another type, causing an unintentional overwrite.</span></span> <span data-ttu-id="07a9e-249">Om du till exempel definierar en typ som heter **Exception** , kommer skript som använder **undantag** som genväg för **system. Exception** inte att fungera.</span><span class="sxs-lookup"><span data-stu-id="07a9e-249">For example, if you define a type called **Exception** , scripts that use **Exception** as the shortcut for **System.Exception** will fail.</span></span>

```yaml
Type: System.String
Parameter Sets: FromSource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="07a9e-250">-UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="07a9e-250">-UsingNamespace</span></span>

<span data-ttu-id="07a9e-251">Anger andra namn områden som krävs för klassen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-251">Specifies other namespaces that are required for the class.</span></span> <span data-ttu-id="07a9e-252">Detta är ungefär som nyckelordet C#, `Using` .</span><span class="sxs-lookup"><span data-stu-id="07a9e-252">This is much like the C# keyword, `Using`.</span></span>

<span data-ttu-id="07a9e-253">Som standard `Add-Type` refererar **system** namn området.</span><span class="sxs-lookup"><span data-stu-id="07a9e-253">By default, `Add-Type` references the **System** namespace.</span></span> <span data-ttu-id="07a9e-254">När parametern **MemberDefinition** används `Add-Type` refererar även namn området **system. Runtime. InteropServices** som standard.</span><span class="sxs-lookup"><span data-stu-id="07a9e-254">When the **MemberDefinition** parameter is used, `Add-Type` also references the **System.Runtime.InteropServices** namespace by default.</span></span> <span data-ttu-id="07a9e-255">De namn områden som du lägger till med hjälp av parametern **UsingNamespace** refereras till utöver standard namn områdena.</span><span class="sxs-lookup"><span data-stu-id="07a9e-255">The namespaces that you add by using the **UsingNamespace** parameter are referenced in addition to the default namespaces.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases: Using

Required: False
Position: Named
Default value: System namespace
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="07a9e-256">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="07a9e-256">CommonParameters</span></span>

<span data-ttu-id="07a9e-257">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="07a9e-257">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="07a9e-258">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="07a9e-258">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="07a9e-259">INDATA</span><span class="sxs-lookup"><span data-stu-id="07a9e-259">INPUTS</span></span>

### <span data-ttu-id="07a9e-260">Inget</span><span class="sxs-lookup"><span data-stu-id="07a9e-260">None</span></span>

<span data-ttu-id="07a9e-261">Du kan inte skicka objekt nedåt i pipelinen till `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="07a9e-261">You can't send objects down the pipeline to `Add-Type`.</span></span>

## <span data-ttu-id="07a9e-262">UTDATA</span><span class="sxs-lookup"><span data-stu-id="07a9e-262">OUTPUTS</span></span>

### <span data-ttu-id="07a9e-263">Ingen eller system. Type</span><span class="sxs-lookup"><span data-stu-id="07a9e-263">None or System.Type</span></span>

<span data-ttu-id="07a9e-264">När du använder parametern **Passthru** `Add-Type` returneras ett **system. Type** -objekt som representerar den nya typen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-264">When you use the **PassThru** parameter, `Add-Type` returns a **System.Type** object that represents the new type.</span></span> <span data-ttu-id="07a9e-265">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="07a9e-265">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="07a9e-266">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="07a9e-266">NOTES</span></span>

<span data-ttu-id="07a9e-267">De typer som du lägger till finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="07a9e-267">The types that you add exist only in the current session.</span></span> <span data-ttu-id="07a9e-268">Om du vill använda typerna i alla sessioner lägger du till dem i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="07a9e-268">To use the types in all sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="07a9e-269">Mer information om profilen finns [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="07a9e-269">For more information about the profile, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="07a9e-270">Typ namn och namn områden måste vara unika inom en session.</span><span class="sxs-lookup"><span data-stu-id="07a9e-270">Type names and namespaces must be unique within a session.</span></span> <span data-ttu-id="07a9e-271">Du kan inte ta bort en typ eller ändra den.</span><span class="sxs-lookup"><span data-stu-id="07a9e-271">You can't unload a type or change it.</span></span> <span data-ttu-id="07a9e-272">Om du behöver ändra koden för en typ måste du ändra namnet eller starta en ny PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="07a9e-272">If you need to change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="07a9e-273">Annars Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="07a9e-273">Otherwise, the command fails.</span></span>

<span data-ttu-id="07a9e-274">I Windows PowerShell (version 5,1 och senare) måste du använda `Add-Type` för allt som inte redan har lästs in.</span><span class="sxs-lookup"><span data-stu-id="07a9e-274">In Windows PowerShell (version 5.1 and below), you need to use `Add-Type` for anything that isn't already loaded.</span></span> <span data-ttu-id="07a9e-275">Oftast gäller detta för sammansättningar som finns i GAC (Global Assembly Cache).</span><span class="sxs-lookup"><span data-stu-id="07a9e-275">Most commonly, this applies to assemblies found in the Global Assembly Cache (GAC).</span></span>
<span data-ttu-id="07a9e-276">I PowerShell 6 och senare finns det ingen GAC, så PowerShell installerar sina egna sammansättningar i `$PSHome` .</span><span class="sxs-lookup"><span data-stu-id="07a9e-276">In PowerShell 6 and higher, there is no GAC, so PowerShell installs its own assemblies in `$PSHome`.</span></span>
<span data-ttu-id="07a9e-277">Dessa sammansättningar läses in automatiskt på begäran, så du behöver inte använda `Add-Type` för att läsa in dem.</span><span class="sxs-lookup"><span data-stu-id="07a9e-277">These assemblies are automatically loaded on request, so there's no need to use `Add-Type` to load them.</span></span> <span data-ttu-id="07a9e-278">Användningen tillåts dock `Add-Type` fortfarande tillåta skript att vara implicit kompatibla med vilken version av PowerShell som helst.</span><span class="sxs-lookup"><span data-stu-id="07a9e-278">However, using `Add-Type` is still permitted to allow scripts to be implicitly compatible with any version of PowerShell.</span></span>

<span data-ttu-id="07a9e-279">Sammansättningar i GAC kan läsas in med typnamn i stället för sökväg.</span><span class="sxs-lookup"><span data-stu-id="07a9e-279">Assemblies in the GAC can be loaded by type name, rather than by path.</span></span> <span data-ttu-id="07a9e-280">Inläsning av sammansättningar från en godtycklig sökväg kräver `Add-Type` , eftersom dessa sammansättningar inte kan läsas in automatiskt.</span><span class="sxs-lookup"><span data-stu-id="07a9e-280">Loading assemblies from an arbitrary path requires `Add-Type`, since those assemblies cannot not be loaded automatically.</span></span>

## <span data-ttu-id="07a9e-281">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="07a9e-281">RELATED LINKS</span></span>

[<span data-ttu-id="07a9e-282">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="07a9e-282">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_profiles.md)

[<span data-ttu-id="07a9e-283">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="07a9e-283">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="07a9e-284">Lägg till medlem</span><span class="sxs-lookup"><span data-stu-id="07a9e-284">Add-Member</span></span>](Add-Member.md)

[<span data-ttu-id="07a9e-285">Nytt – objekt</span><span class="sxs-lookup"><span data-stu-id="07a9e-285">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="07a9e-286">OutputAssemblyType</span><span class="sxs-lookup"><span data-stu-id="07a9e-286">OutputAssemblyType</span></span>](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[<span data-ttu-id="07a9e-287">Plattforms anrop (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="07a9e-287">Platform Invoke (P/Invoke)</span></span>](/dotnet/standard/native-interop/pinvoke)

[<span data-ttu-id="07a9e-288">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="07a9e-288">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
