---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: cbf211f4ae5262255a74fa7fb97d2493202d71fa
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/10/2020
ms.locfileid: "93269457"
---
# <span data-ttu-id="31937-103">Add-Type</span><span class="sxs-lookup"><span data-stu-id="31937-103">Add-Type</span></span>

## <span data-ttu-id="31937-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="31937-104">SYNOPSIS</span></span>
<span data-ttu-id="31937-105">Lägger till en Microsoft .NET Core-klass till en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="31937-105">Adds a Microsoft .NET Core class to a PowerShell session.</span></span>

## <span data-ttu-id="31937-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="31937-106">SYNTAX</span></span>

### <span data-ttu-id="31937-107">FromSource (standard)</span><span class="sxs-lookup"><span data-stu-id="31937-107">FromSource (Default)</span></span>

```
Add-Type [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="31937-108">FromMember</span><span class="sxs-lookup"><span data-stu-id="31937-108">FromMember</span></span>

```
Add-Type [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>]
 [-UsingNamespace <String[]>] [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="31937-109">FromPath</span><span class="sxs-lookup"><span data-stu-id="31937-109">FromPath</span></span>

```
Add-Type [-Path] <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="31937-110">FromLiteralPath</span><span class="sxs-lookup"><span data-stu-id="31937-110">FromLiteralPath</span></span>

```
Add-Type -LiteralPath <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="31937-111">FromAssemblyName</span><span class="sxs-lookup"><span data-stu-id="31937-111">FromAssemblyName</span></span>

```
Add-Type -AssemblyName <String[]> [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="31937-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="31937-112">DESCRIPTION</span></span>

<span data-ttu-id="31937-113">Med `Add-Type` cmdleten kan du definiera en Microsoft .net Core-klass i din PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="31937-113">The `Add-Type` cmdlet lets you define a Microsoft .NET Core class in your PowerShell session.</span></span> <span data-ttu-id="31937-114">Du kan sedan instansiera objekt med hjälp av `New-Object` cmdleten och använda objekten på samma sätt som du använder ett .net Core-objekt.</span><span class="sxs-lookup"><span data-stu-id="31937-114">You can then instantiate objects, by using the `New-Object` cmdlet, and use the objects just as you would use any .NET Core object.</span></span> <span data-ttu-id="31937-115">Om du lägger till ett `Add-Type` kommando i din PowerShell-profil, är klassen tillgänglig i alla PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="31937-115">If you add an `Add-Type` command to your PowerShell profile, the class is available in all PowerShell sessions.</span></span>

<span data-ttu-id="31937-116">Du kan ange typen genom att ange en befintlig sammansättning eller källfiler, eller så kan du ange käll koden infogad eller Sparad i en variabel.</span><span class="sxs-lookup"><span data-stu-id="31937-116">You can specify the type by specifying an existing assembly or source code files, or you can specify the source code inline or saved in a variable.</span></span> <span data-ttu-id="31937-117">Du kan även ange en metod och `Add-Type` definiera och generera klassen.</span><span class="sxs-lookup"><span data-stu-id="31937-117">You can even specify only a method and `Add-Type` defines and generates the class.</span></span> <span data-ttu-id="31937-118">I Windows kan du använda den här funktionen för att göra plattforms anrop (P/Invoke)-anrop till ohanterade funktioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="31937-118">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span> <span data-ttu-id="31937-119">Om du anger käll kod `Add-Type` kompilerar den angivna käll koden och genererar en minnes intern sammansättning som innehåller de nya .net Core-typerna.</span><span class="sxs-lookup"><span data-stu-id="31937-119">If you specify source code, `Add-Type` compiles the specified source code and generates an in-memory assembly that contains the new .NET Core types.</span></span>

<span data-ttu-id="31937-120">Du kan använda parametrarna för `Add-Type` för att ange ett alternativt språk och en kompilerare, C# är standard, kompilator alternativ, sammansättnings beroenden, klass namn område, namn på typen och den resulterande sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="31937-120">You can use the parameters of `Add-Type` to specify an alternate language and compiler, C# is the default, compiler options, assembly dependencies, the class namespace, the names of the type, and the resulting assembly.</span></span>

<span data-ttu-id="31937-121">Från och med PowerShell 7 `Add-Type` kompileras inte en typ om det redan finns en typ med samma namn.</span><span class="sxs-lookup"><span data-stu-id="31937-121">Beginning in PowerShell 7, `Add-Type` does not compile a type if a type with the same name already exists.</span></span> <span data-ttu-id="31937-122">Söker också `Add-Type` efter sammansättningar i en `ref` mapp under mappen som innehåller `pwsh.dll` .</span><span class="sxs-lookup"><span data-stu-id="31937-122">Also, `Add-Type` looks for assemblies in a `ref` folder under the folder that contains `pwsh.dll`.</span></span>

## <span data-ttu-id="31937-123">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="31937-123">EXAMPLES</span></span>

### <span data-ttu-id="31937-124">Exempel 1: Lägg till en .NET-typ i en session</span><span class="sxs-lookup"><span data-stu-id="31937-124">Example 1: Add a .NET type to a session</span></span>

<span data-ttu-id="31937-125">I det här exemplet läggs klassen **BasicTest** till i sessionen genom att du anger käll koden som lagras i en variabel.</span><span class="sxs-lookup"><span data-stu-id="31937-125">This example adds the **BasicTest** class to the session by specifying source code that is stored in a variable.</span></span> <span data-ttu-id="31937-126">**BasicTest** -klassen används för att lägga till heltal, skapa ett objekt och multiplicera heltal.</span><span class="sxs-lookup"><span data-stu-id="31937-126">The **BasicTest** class is used to add integers, create an object, and multiply integers.</span></span>

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

<span data-ttu-id="31937-127">`$Source`Variabeln lagrar käll koden för klassen.</span><span class="sxs-lookup"><span data-stu-id="31937-127">The `$Source` variable stores the source code for the class.</span></span> <span data-ttu-id="31937-128">Typen har en statisk metod som kallas `Add` och en icke-statisk metod som kallas `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="31937-128">The type has a static method called `Add` and a non-static method called `Multiply`.</span></span>

<span data-ttu-id="31937-129">`Add-Type`Cmdleten lägger till klassen i sessionen.</span><span class="sxs-lookup"><span data-stu-id="31937-129">The `Add-Type` cmdlet adds the class to the session.</span></span> <span data-ttu-id="31937-130">Eftersom den använder infogad källkod använder kommandot **TypeDefinition** -parametern för att ange koden i `$Source` variabeln.</span><span class="sxs-lookup"><span data-stu-id="31937-130">Because it's using inline source code, the command uses the **TypeDefinition** parameter to specify the code in the `$Source` variable.</span></span>

<span data-ttu-id="31937-131">Den `Add` statiska metoden i **BasicTest** -klassen använder dubbla kolon tecken ( `::` ) för att ange en statisk medlem i klassen.</span><span class="sxs-lookup"><span data-stu-id="31937-131">The `Add` static method of the **BasicTest** class uses the double-colon characters (`::`) to specify a static member of the class.</span></span> <span data-ttu-id="31937-132">Heltalen läggs till och summan visas.</span><span class="sxs-lookup"><span data-stu-id="31937-132">The integers are added and the sum is displayed.</span></span>

<span data-ttu-id="31937-133">`New-Object`Cmdlet: en instansierar en instans av klassen **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="31937-133">The `New-Object` cmdlet instantiates an instance of the **BasicTest** class.</span></span> <span data-ttu-id="31937-134">Det sparar det nya objektet i `$BasicTestObject` variabeln.</span><span class="sxs-lookup"><span data-stu-id="31937-134">It saves the new object in the `$BasicTestObject` variable.</span></span>

<span data-ttu-id="31937-135">`$BasicTestObject` använder- `Multiply` metoden.</span><span class="sxs-lookup"><span data-stu-id="31937-135">`$BasicTestObject` uses the `Multiply` method.</span></span> <span data-ttu-id="31937-136">Heltalen multipliceras och produkten visas.</span><span class="sxs-lookup"><span data-stu-id="31937-136">The integers are multiplied and the product is displayed.</span></span>

### <span data-ttu-id="31937-137">Exempel 2: granska en tillagd typ</span><span class="sxs-lookup"><span data-stu-id="31937-137">Example 2: Examine an added type</span></span>

<span data-ttu-id="31937-138">I det här exemplet används `Get-Member` cmdleten för att undersöka de objekt som `Add-Type` `New-Object` cmdletarna och skapade i **exempel 1**.</span><span class="sxs-lookup"><span data-stu-id="31937-138">This example uses the `Get-Member` cmdlet to examine the objects that the `Add-Type` and `New-Object` cmdlets created in **Example 1**.</span></span>

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

<span data-ttu-id="31937-139">`Get-Member`Cmdleten hämtar typ och medlemmar i **BasicTest** -klassen som `Add-Type` har lagts till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="31937-139">The `Get-Member` cmdlet gets the type and members of the **BasicTest** class that `Add-Type` added to the session.</span></span> <span data-ttu-id="31937-140">`Get-Member`Kommandot visar att det är ett **system. RuntimeType** -objekt, som härleds från klassen **system. Object** .</span><span class="sxs-lookup"><span data-stu-id="31937-140">The `Get-Member` command reveals that it's a **System.RuntimeType** object, which is derived from the **System.Object** class.</span></span>

<span data-ttu-id="31937-141">Den `Get-Member` **statiska** parametern hämtar statiska egenskaper och metoder för klassen **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="31937-141">The `Get-Member` **Static** parameter gets the static properties and methods of the **BasicTest** class.</span></span> <span data-ttu-id="31937-142">Utdata visar att `Add` metoden ingår.</span><span class="sxs-lookup"><span data-stu-id="31937-142">The output shows that the `Add` method is included.</span></span>

<span data-ttu-id="31937-143">`Get-Member`Cmdlet: en hämtar medlemmarna i objektet som lagras i `$BasicTestObject` variabeln.</span><span class="sxs-lookup"><span data-stu-id="31937-143">The `Get-Member` cmdlet gets the members of the object stored in the `$BasicTestObject` variable.</span></span>
<span data-ttu-id="31937-144">`$BasicTestObject` har skapats med hjälp av `New-Object` cmdleten med klassen **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="31937-144">`$BasicTestObject` was created by using the `New-Object` cmdlet with the **BasicTest** class.</span></span> <span data-ttu-id="31937-145">Utdata visar att värdet för `$BasicTestObject` variabeln är en instans av klassen **BasicTest** och att den innehåller en medlem som kallas `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="31937-145">The output reveals that the value of the `$BasicTestObject` variable is an instance of the **BasicTest** class and that it includes a member called `Multiply`.</span></span>

### <span data-ttu-id="31937-146">Exempel 3: lägga till typer från en sammansättning</span><span class="sxs-lookup"><span data-stu-id="31937-146">Example 3: Add types from an assembly</span></span>

<span data-ttu-id="31937-147">I det här exemplet läggs klasserna från `NJsonSchema.dll` sammansättningen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="31937-147">This example adds the classes from the `NJsonSchema.dll` assembly to the current session.</span></span>

```powershell
Set-Location -Path $PSHOME
$AccType = Add-Type -AssemblyName *jsonschema* -PassThru
```

<span data-ttu-id="31937-148">`Set-Location` använder parametern **Path** för att ange `$PSHOME` variabeln.</span><span class="sxs-lookup"><span data-stu-id="31937-148">`Set-Location` uses the **Path** parameter to specify the `$PSHOME` variable.</span></span> <span data-ttu-id="31937-149">Variabeln refererar till PowerShell-installations katalogen där DLL-filen finns.</span><span class="sxs-lookup"><span data-stu-id="31937-149">The variable references the PowerShell installation directory where the DLL file is located.</span></span>

<span data-ttu-id="31937-150">`$AccType`Variabeln lagrar ett objekt som skapats med `Add-Type` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="31937-150">The `$AccType` variable stores an object created with the `Add-Type` cmdlet.</span></span> <span data-ttu-id="31937-151">`Add-Type` använder parametern **AssemblyName** för att ange namnet på sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="31937-151">`Add-Type` uses the **AssemblyName** parameter to specify the name of the assembly.</span></span> <span data-ttu-id="31937-152">Med jokertecknet asterisk ( `*` ) kan du hämta rätt sammansättning även om du inte är säker på namnet eller stavningen.</span><span class="sxs-lookup"><span data-stu-id="31937-152">The asterisk (`*`) wildcard character allows you to get the correct assembly even when you aren't sure of the name or its spelling.</span></span> <span data-ttu-id="31937-153">Parametern **Passthru** genererar objekt som representerar de klasser som läggs till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="31937-153">The **PassThru** parameter generates objects that represent the classes that are added to the session.</span></span>

### <span data-ttu-id="31937-154">Exempel 4: anropa inbyggda Windows-API: er</span><span class="sxs-lookup"><span data-stu-id="31937-154">Example 4: Call native Windows APIs</span></span>

<span data-ttu-id="31937-155">Det här exemplet visar hur du anropar inbyggda Windows-API: er i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="31937-155">This example demonstrates how to call native Windows APIs in PowerShell.</span></span> <span data-ttu-id="31937-156">`Add-Type` använder mekanismen för plattforms anrop (P/Invoke) för att anropa en funktion i `User32.dll` från PowerShell.</span><span class="sxs-lookup"><span data-stu-id="31937-156">`Add-Type` uses the Platform Invoke (P/Invoke) mechanism to call a function in `User32.dll` from PowerShell.</span></span> <span data-ttu-id="31937-157">Det här exemplet fungerar endast på datorer som kör operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="31937-157">This example only works on computers running the Windows operating system.</span></span>

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

<span data-ttu-id="31937-158">`$Signature`Variabeln lagrar C#-signaturen för `ShowWindowAsync` funktionen.</span><span class="sxs-lookup"><span data-stu-id="31937-158">The `$Signature` variable stores the C# signature of the `ShowWindowAsync` function.</span></span> <span data-ttu-id="31937-159">För att säkerställa att den resulterande metoden visas i en PowerShell-session har `public` nyckelordet lagts till i standard-signaturen.</span><span class="sxs-lookup"><span data-stu-id="31937-159">To ensure that the resulting method is visible in a PowerShell session, the `public` keyword was added to the standard signature.</span></span> <span data-ttu-id="31937-160">Mer information finns i [ShowWindowAsync-funktionen](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span><span class="sxs-lookup"><span data-stu-id="31937-160">For more information, see [ShowWindowAsync function](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span></span>

<span data-ttu-id="31937-161">`$ShowWindowAsync`Variabeln lagrar objektet som skapats av parametern `Add-Type` **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="31937-161">The `$ShowWindowAsync` variable stores the object created by the `Add-Type` **PassThru** parameter.</span></span>
<span data-ttu-id="31937-162">`Add-Type`Cmdleten lägger till `ShowWindowAsync` funktionen i PowerShell-sessionen som en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="31937-162">The `Add-Type` cmdlet adds the `ShowWindowAsync` function to the PowerShell session as a static method.</span></span> <span data-ttu-id="31937-163">Kommandot använder parametern **MemberDefinition** för att ange den metod definition som sparats i `$Signature` variabeln.</span><span class="sxs-lookup"><span data-stu-id="31937-163">The command uses the **MemberDefinition** parameter to specify the method definition saved in the `$Signature` variable.</span></span> <span data-ttu-id="31937-164">Kommandot använder **namn** och namn **områdes** parametrar för att ange ett namn och ett namn område för klassen.</span><span class="sxs-lookup"><span data-stu-id="31937-164">The command uses the **Name** and **Namespace** parameters to specify a name and namespace for the class.</span></span> <span data-ttu-id="31937-165">Parametern **Passthru** genererar ett objekt som representerar typerna.</span><span class="sxs-lookup"><span data-stu-id="31937-165">The **PassThru** parameter generates an object that represents the types.</span></span>

<span data-ttu-id="31937-166">Den nya `ShowWindowAsync` statiska metoden används i kommandona för att minimera och återställa PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="31937-166">The new `ShowWindowAsync` static method is used in the commands to minimize and restore the PowerShell console.</span></span> <span data-ttu-id="31937-167">Metoden tar två parametrar: fönster handtaget och ett heltal som anger hur fönstret visas.</span><span class="sxs-lookup"><span data-stu-id="31937-167">The method takes two parameters: the window handle, and an integer that specifies how the window is displayed.</span></span>

<span data-ttu-id="31937-168">För att minimera PowerShell-konsolen, `ShowWindowAsync` använder `Get-Process` cmdleten med den `$PID` automatiska variabeln för att hämta den process som är värd för den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="31937-168">To minimize the PowerShell console, `ShowWindowAsync` uses the `Get-Process` cmdlet with the `$PID` automatic variable to get the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="31937-169">Sedan används egenskapen **MainWindowHandle** för den aktuella processen och värdet `2` , som representerar `SW_MINIMIZE` värdet.</span><span class="sxs-lookup"><span data-stu-id="31937-169">Then it uses the **MainWindowHandle** property of the current process and a value of `2`, which represents the `SW_MINIMIZE` value.</span></span>

<span data-ttu-id="31937-170">För att återställa fönstret `ShowWindowAsync` använder värdet `4` för fönstrets position, som representerar `SW_RESTORE` värdet.</span><span class="sxs-lookup"><span data-stu-id="31937-170">To restore the window, `ShowWindowAsync` uses a value of `4` for the window position, which represents the `SW_RESTORE` value.</span></span>

<span data-ttu-id="31937-171">Maximera fönstret genom att använda värdet för `3` som representerar `SW_MAXIMIZE` .</span><span class="sxs-lookup"><span data-stu-id="31937-171">To maximize the window, use the value of `3` that represents `SW_MAXIMIZE`.</span></span>

## <span data-ttu-id="31937-172">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="31937-172">PARAMETERS</span></span>

### <span data-ttu-id="31937-173">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="31937-173">-AssemblyName</span></span>

<span data-ttu-id="31937-174">Anger namnet på en sammansättning som innehåller typerna.</span><span class="sxs-lookup"><span data-stu-id="31937-174">Specifies the name of an assembly that includes the types.</span></span> <span data-ttu-id="31937-175">`Add-Type` tar typer från den angivna sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="31937-175">`Add-Type` takes the types from the specified assembly.</span></span> <span data-ttu-id="31937-176">Den här parametern krävs när du skapar typer baserat på ett sammansättnings namn.</span><span class="sxs-lookup"><span data-stu-id="31937-176">This parameter is required when you're creating types based on an assembly name.</span></span>

<span data-ttu-id="31937-177">Ange det fullständiga eller enkla namnet, även kallat det partiella namnet för en sammansättning.</span><span class="sxs-lookup"><span data-stu-id="31937-177">Enter the full or simple name, also known as the partial name, of an assembly.</span></span> <span data-ttu-id="31937-178">Jokertecken tillåts i sammansättnings namnet.</span><span class="sxs-lookup"><span data-stu-id="31937-178">Wildcard characters are permitted in the assembly name.</span></span> <span data-ttu-id="31937-179">Om du anger ett enkelt eller partiellt namn `Add-Type` matchas det med det fullständiga namnet och sedan används det fullständiga namnet för att läsa in sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="31937-179">If you enter a simple or partial name, `Add-Type` resolves it to the full name, and then uses the full name to load the assembly.</span></span>

<span data-ttu-id="31937-180">Den här parametern accepterar inte en sökväg eller ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="31937-180">This parameter doesn't accept a path or a filename.</span></span> <span data-ttu-id="31937-181">Om du vill ange sökvägen till DLL-filen för Assembly-DLL-filen använder du parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="31937-181">To enter the path to the assembly dynamic-link library (DLL) file, use the **Path** parameter.</span></span>

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

### <span data-ttu-id="31937-182">-CompilerOptions</span><span class="sxs-lookup"><span data-stu-id="31937-182">-CompilerOptions</span></span>

<span data-ttu-id="31937-183">Anger alternativ för käll kods kompileraren.</span><span class="sxs-lookup"><span data-stu-id="31937-183">Specifies the options for the source code compiler.</span></span> <span data-ttu-id="31937-184">De här alternativen skickas till kompilatorn utan revidering.</span><span class="sxs-lookup"><span data-stu-id="31937-184">These options are sent to the compiler without revision.</span></span>

<span data-ttu-id="31937-185">Med den här parametern kan du dirigera kompilatorn för att generera en körbar fil, bädda in resurser eller ange kommando rads alternativ, till exempel `/unsafe` alternativet.</span><span class="sxs-lookup"><span data-stu-id="31937-185">This parameter allows you to direct the compiler to generate an executable file, embed resources, or set command-line options, such as the `/unsafe` option.</span></span>

<span data-ttu-id="31937-186">Du kan inte använda parametrarna **CompilerOptions** och **ReferencedAssemblies** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="31937-186">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

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

### <span data-ttu-id="31937-187">-IgnoreWarnings</span><span class="sxs-lookup"><span data-stu-id="31937-187">-IgnoreWarnings</span></span>

<span data-ttu-id="31937-188">Ignorerar kompilator varningar.</span><span class="sxs-lookup"><span data-stu-id="31937-188">Ignores compiler warnings.</span></span> <span data-ttu-id="31937-189">Använd den här parametern för att förhindra `Add-Type` hantering av kompilator varningar som fel.</span><span class="sxs-lookup"><span data-stu-id="31937-189">Use this parameter to prevent `Add-Type` from handling compiler warnings as errors.</span></span>

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

### <span data-ttu-id="31937-190">– Språk</span><span class="sxs-lookup"><span data-stu-id="31937-190">-Language</span></span>

<span data-ttu-id="31937-191">Anger det språk som används i käll koden.</span><span class="sxs-lookup"><span data-stu-id="31937-191">Specifies the language that is used in the source code.</span></span> <span data-ttu-id="31937-192">Det acceptabla värdet för den här parametern är **csharp**.</span><span class="sxs-lookup"><span data-stu-id="31937-192">The acceptable value for this parameter is **CSharp**.</span></span>

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

### <span data-ttu-id="31937-193">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="31937-193">-LiteralPath</span></span>

<span data-ttu-id="31937-194">Anger sökvägen till käll kods filer eller sammansättnings-DLL-filer som innehåller typerna.</span><span class="sxs-lookup"><span data-stu-id="31937-194">Specifies the path to source code files or assembly DLL files that contain the types.</span></span> <span data-ttu-id="31937-195">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det skrivs.</span><span class="sxs-lookup"><span data-stu-id="31937-195">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="31937-196">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="31937-196">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="31937-197">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="31937-197">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="31937-198">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="31937-198">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="31937-199">-MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="31937-199">-MemberDefinition</span></span>

<span data-ttu-id="31937-200">Anger nya egenskaper eller metoder för klassen.</span><span class="sxs-lookup"><span data-stu-id="31937-200">Specifies new properties or methods for the class.</span></span> <span data-ttu-id="31937-201">`Add-Type` skapar den mallkod som krävs för att stödja egenskaper eller metoder.</span><span class="sxs-lookup"><span data-stu-id="31937-201">`Add-Type` generates the template code that is required to support the properties or methods.</span></span>

<span data-ttu-id="31937-202">I Windows kan du använda den här funktionen för att göra plattforms anrop (P/Invoke)-anrop till ohanterade funktioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="31937-202">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span>

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

### <span data-ttu-id="31937-203">-Name</span><span class="sxs-lookup"><span data-stu-id="31937-203">-Name</span></span>

<span data-ttu-id="31937-204">Anger namnet på den klass som ska skapas.</span><span class="sxs-lookup"><span data-stu-id="31937-204">Specifies the name of the class to create.</span></span> <span data-ttu-id="31937-205">Den här parametern krävs när en typ skapas från en medlems definition.</span><span class="sxs-lookup"><span data-stu-id="31937-205">This parameter is required when generating a type from a member definition.</span></span>

<span data-ttu-id="31937-206">Typ namnet och namn området måste vara unikt inom en session.</span><span class="sxs-lookup"><span data-stu-id="31937-206">The type name and namespace must be unique within a session.</span></span> <span data-ttu-id="31937-207">Du kan inte ta bort en typ eller ändra den.</span><span class="sxs-lookup"><span data-stu-id="31937-207">You can't unload a type or change it.</span></span>
<span data-ttu-id="31937-208">Om du vill ändra koden för en typ måste du ändra namnet eller starta en ny PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="31937-208">To change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="31937-209">Annars Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="31937-209">Otherwise, the command fails.</span></span>

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

### <span data-ttu-id="31937-210">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="31937-210">-Namespace</span></span>

<span data-ttu-id="31937-211">Anger ett namn område för typen.</span><span class="sxs-lookup"><span data-stu-id="31937-211">Specifies a namespace for the type.</span></span>

<span data-ttu-id="31937-212">Om den här parametern inte ingår i kommandot skapas typen i namn området **Microsoft. PowerShell. commands. AddType. AutoGeneratedTypes** .</span><span class="sxs-lookup"><span data-stu-id="31937-212">If this parameter isn't included in the command, the type is created in the **Microsoft.PowerShell.Commands.AddType.AutoGeneratedTypes** namespace.</span></span> <span data-ttu-id="31937-213">Om parametern ingår i kommandot med ett tomt sträng värde eller ett värde av `$Null` genereras typen i det globala namn området.</span><span class="sxs-lookup"><span data-stu-id="31937-213">If the parameter is included in the command with an empty string value or a value of `$Null`, the type is generated in the global namespace.</span></span>

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

### <span data-ttu-id="31937-214">-OutputAssembly</span><span class="sxs-lookup"><span data-stu-id="31937-214">-OutputAssembly</span></span>

<span data-ttu-id="31937-215">Genererar en DLL-fil för sammansättningen med det angivna namnet på platsen.</span><span class="sxs-lookup"><span data-stu-id="31937-215">Generates a DLL file for the assembly with the specified name in the location.</span></span> <span data-ttu-id="31937-216">Ange en valfri sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="31937-216">Enter an optional path and filename.</span></span> <span data-ttu-id="31937-217">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="31937-217">Wildcard characters are permitted.</span></span> <span data-ttu-id="31937-218">Som standard `Add-Type` genererar sammansättningen endast i minnet.</span><span class="sxs-lookup"><span data-stu-id="31937-218">By default, `Add-Type` generates the assembly only in memory.</span></span>

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

### <span data-ttu-id="31937-219">– OutputType</span><span class="sxs-lookup"><span data-stu-id="31937-219">-OutputType</span></span>

<span data-ttu-id="31937-220">Anger utdatatypen för den utgående sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="31937-220">Specifies the output type of the output assembly.</span></span> <span data-ttu-id="31937-221">Som standard har ingen Utdatatyp angetts.</span><span class="sxs-lookup"><span data-stu-id="31937-221">By default, no output type is specified.</span></span> <span data-ttu-id="31937-222">Den här parametern är endast giltig när en utgående sammansättning anges i kommandot.</span><span class="sxs-lookup"><span data-stu-id="31937-222">This parameter is valid only when an output assembly is specified in the command.</span></span> <span data-ttu-id="31937-223">Mer information om värdena finns i OutputAssemblyType- [uppräkning](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span><span class="sxs-lookup"><span data-stu-id="31937-223">For more information about the values, see [OutputAssemblyType Enumeration](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span></span>

<span data-ttu-id="31937-224">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="31937-224">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="31937-225">ConsoleApplication</span><span class="sxs-lookup"><span data-stu-id="31937-225">ConsoleApplication</span></span>
- <span data-ttu-id="31937-226">Bibliotek</span><span class="sxs-lookup"><span data-stu-id="31937-226">Library</span></span>
- <span data-ttu-id="31937-227">WindowsApplication</span><span class="sxs-lookup"><span data-stu-id="31937-227">WindowsApplication</span></span>

> [!IMPORTANT]
> <span data-ttu-id="31937-228">`ConsoleApplication`Värdena och kan inte `WindowsApplication` producera fungerande utdata och bör inte användas.</span><span class="sxs-lookup"><span data-stu-id="31937-228">The `ConsoleApplication` and `WindowsApplication` values don't produce working output and should not be used.</span></span>

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

### <span data-ttu-id="31937-229">– PassThru</span><span class="sxs-lookup"><span data-stu-id="31937-229">-PassThru</span></span>

<span data-ttu-id="31937-230">Returnerar ett **system. Runtime** -objekt som representerar de typer som har lagts till.</span><span class="sxs-lookup"><span data-stu-id="31937-230">Returns a **System.Runtime** object that represents the types that were added.</span></span> <span data-ttu-id="31937-231">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="31937-231">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="31937-232">-Path</span><span class="sxs-lookup"><span data-stu-id="31937-232">-Path</span></span>

<span data-ttu-id="31937-233">Anger sökvägen till käll kods filer eller sammansättnings-DLL-filer som innehåller typerna.</span><span class="sxs-lookup"><span data-stu-id="31937-233">Specifies the path to source code files or assembly DLL files that contain the types.</span></span>

<span data-ttu-id="31937-234">Om du skickar källfiler `Add-Type` kompilerar koden i filerna och skapar en minnes intern sammansättning av typerna.</span><span class="sxs-lookup"><span data-stu-id="31937-234">If you submit source code files, `Add-Type` compiles the code in the files and creates an in-memory assembly of the types.</span></span> <span data-ttu-id="31937-235">Fil tillägget som anges i **Path** -värdet avgör vilken kompilator som `Add-Type` använder.</span><span class="sxs-lookup"><span data-stu-id="31937-235">The file extension specified in the value of **Path** determines the compiler that `Add-Type` uses.</span></span>

<span data-ttu-id="31937-236">Om du skickar en sammansättnings fil, `Add-Type` tar de olika typerna från sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="31937-236">If you submit an assembly file, `Add-Type` takes the types from the assembly.</span></span> <span data-ttu-id="31937-237">Om du vill ange en minnes intern sammansättning eller Global Assembly Cache använder du parametern **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="31937-237">To specify an in-memory assembly or the global assembly cache, use the **AssemblyName** parameter.</span></span>

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

### <span data-ttu-id="31937-238">-ReferencedAssemblies</span><span class="sxs-lookup"><span data-stu-id="31937-238">-ReferencedAssemblies</span></span>

<span data-ttu-id="31937-239">Anger de sammansättningar som typen är beroende av.</span><span class="sxs-lookup"><span data-stu-id="31937-239">Specifies the assemblies upon which the type depends.</span></span> <span data-ttu-id="31937-240">Som standard `Add-Type` refererar `System.dll` och `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="31937-240">By default, `Add-Type` references `System.dll` and `System.Management.Automation.dll`.</span></span> <span data-ttu-id="31937-241">De sammansättningar som du anger med hjälp av den här parametern refereras till utöver standard sammansättningarna.</span><span class="sxs-lookup"><span data-stu-id="31937-241">The assemblies that you specify by using this parameter are referenced in addition to the default assemblies.</span></span>

<span data-ttu-id="31937-242">Från och med PowerShell 6 inkluderar **ReferencedAssemblies** inte standard-.net-sammansättningarna.</span><span class="sxs-lookup"><span data-stu-id="31937-242">Beginning in PowerShell 6, **ReferencedAssemblies** doesn't include the default .NET assemblies.</span></span> <span data-ttu-id="31937-243">Du måste inkludera en speciell referens till dem i värdet som skickas till den här parametern.</span><span class="sxs-lookup"><span data-stu-id="31937-243">You must include a specific reference to them in the value passed to this parameter.</span></span>

<span data-ttu-id="31937-244">Du kan inte använda parametrarna **CompilerOptions** och **ReferencedAssemblies** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="31937-244">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

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

### <span data-ttu-id="31937-245">-TypeDefinition</span><span class="sxs-lookup"><span data-stu-id="31937-245">-TypeDefinition</span></span>

<span data-ttu-id="31937-246">Anger den käll kod som innehåller typ definitionerna.</span><span class="sxs-lookup"><span data-stu-id="31937-246">Specifies the source code that contains the type definitions.</span></span> <span data-ttu-id="31937-247">Ange käll koden i en sträng eller här – sträng, eller ange en variabel som innehåller käll koden.</span><span class="sxs-lookup"><span data-stu-id="31937-247">Enter the source code in a string or here-string, or enter a variable that contains the source code.</span></span> <span data-ttu-id="31937-248">Mer information om här – strängar finns [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="31937-248">For more information about here-strings, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span></span>

<span data-ttu-id="31937-249">Ta med en namn områdes deklaration i din typ definition.</span><span class="sxs-lookup"><span data-stu-id="31937-249">Include a namespace declaration in your type definition.</span></span> <span data-ttu-id="31937-250">Om du utelämnar namn områdes deklarationen kan typen ha samma namn som en annan typ eller genvägen till en annan typ, vilket orsakar en oavsiktlig överskrivning.</span><span class="sxs-lookup"><span data-stu-id="31937-250">If you omit the namespace declaration, your type might have the same name as another type or the shortcut for another type, causing an unintentional overwrite.</span></span> <span data-ttu-id="31937-251">Om du till exempel definierar en typ som heter **Exception** , kommer skript som använder **undantag** som genväg för **system. Exception** inte att fungera.</span><span class="sxs-lookup"><span data-stu-id="31937-251">For example, if you define a type called **Exception** , scripts that use **Exception** as the shortcut for **System.Exception** will fail.</span></span>

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

### <span data-ttu-id="31937-252">-UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="31937-252">-UsingNamespace</span></span>

<span data-ttu-id="31937-253">Anger andra namn områden som krävs för klassen.</span><span class="sxs-lookup"><span data-stu-id="31937-253">Specifies other namespaces that are required for the class.</span></span> <span data-ttu-id="31937-254">Detta är ungefär som nyckelordet C#, `Using` .</span><span class="sxs-lookup"><span data-stu-id="31937-254">This is much like the C# keyword, `Using`.</span></span>

<span data-ttu-id="31937-255">Som standard `Add-Type` refererar **system** namn området.</span><span class="sxs-lookup"><span data-stu-id="31937-255">By default, `Add-Type` references the **System** namespace.</span></span> <span data-ttu-id="31937-256">När parametern **MemberDefinition** används `Add-Type` refererar även namn området **system. Runtime. InteropServices** som standard.</span><span class="sxs-lookup"><span data-stu-id="31937-256">When the **MemberDefinition** parameter is used, `Add-Type` also references the **System.Runtime.InteropServices** namespace by default.</span></span> <span data-ttu-id="31937-257">De namn områden som du lägger till med hjälp av parametern **UsingNamespace** refereras till utöver standard namn områdena.</span><span class="sxs-lookup"><span data-stu-id="31937-257">The namespaces that you add by using the **UsingNamespace** parameter are referenced in addition to the default namespaces.</span></span>

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

### <span data-ttu-id="31937-258">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="31937-258">CommonParameters</span></span>

<span data-ttu-id="31937-259">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="31937-259">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="31937-260">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="31937-260">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="31937-261">INDATA</span><span class="sxs-lookup"><span data-stu-id="31937-261">INPUTS</span></span>

### <span data-ttu-id="31937-262">Inget</span><span class="sxs-lookup"><span data-stu-id="31937-262">None</span></span>

<span data-ttu-id="31937-263">Du kan inte skicka objekt nedåt i pipelinen till `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="31937-263">You can't send objects down the pipeline to `Add-Type`.</span></span>

## <span data-ttu-id="31937-264">UTDATA</span><span class="sxs-lookup"><span data-stu-id="31937-264">OUTPUTS</span></span>

### <span data-ttu-id="31937-265">Ingen eller system. Type</span><span class="sxs-lookup"><span data-stu-id="31937-265">None or System.Type</span></span>

<span data-ttu-id="31937-266">När du använder parametern **Passthru** `Add-Type` returneras ett **system. Type** -objekt som representerar den nya typen.</span><span class="sxs-lookup"><span data-stu-id="31937-266">When you use the **PassThru** parameter, `Add-Type` returns a **System.Type** object that represents the new type.</span></span> <span data-ttu-id="31937-267">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="31937-267">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="31937-268">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="31937-268">NOTES</span></span>

<span data-ttu-id="31937-269">De typer som du lägger till finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="31937-269">The types that you add exist only in the current session.</span></span> <span data-ttu-id="31937-270">Om du vill använda typerna i alla sessioner lägger du till dem i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="31937-270">To use the types in all sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="31937-271">Mer information om profilen finns [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="31937-271">For more information about the profile, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="31937-272">Typ namn och namn områden måste vara unika inom en session.</span><span class="sxs-lookup"><span data-stu-id="31937-272">Type names and namespaces must be unique within a session.</span></span> <span data-ttu-id="31937-273">Du kan inte ta bort en typ eller ändra den.</span><span class="sxs-lookup"><span data-stu-id="31937-273">You can't unload a type or change it.</span></span> <span data-ttu-id="31937-274">Om du behöver ändra koden för en typ måste du ändra namnet eller starta en ny PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="31937-274">If you need to change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="31937-275">Annars Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="31937-275">Otherwise, the command fails.</span></span>

<span data-ttu-id="31937-276">I Windows PowerShell (version 5,1 och senare) måste du använda `Add-Type` för allt som inte redan har lästs in.</span><span class="sxs-lookup"><span data-stu-id="31937-276">In Windows PowerShell (version 5.1 and below), you need to use `Add-Type` for anything that isn't already loaded.</span></span> <span data-ttu-id="31937-277">Oftast gäller detta för sammansättningar som finns i GAC (Global Assembly Cache).</span><span class="sxs-lookup"><span data-stu-id="31937-277">Most commonly, this applies to assemblies found in the Global Assembly Cache (GAC).</span></span>
<span data-ttu-id="31937-278">I PowerShell 6 och senare finns det ingen GAC, så PowerShell installerar sina egna sammansättningar i `$PSHome` .</span><span class="sxs-lookup"><span data-stu-id="31937-278">In PowerShell 6 and higher, there is no GAC, so PowerShell installs its own assemblies in `$PSHome`.</span></span>
<span data-ttu-id="31937-279">Dessa sammansättningar läses in automatiskt på begäran, så du behöver inte använda `Add-Type` för att läsa in dem.</span><span class="sxs-lookup"><span data-stu-id="31937-279">These assemblies are automatically loaded on request, so there's no need to use `Add-Type` to load them.</span></span> <span data-ttu-id="31937-280">Användningen tillåts dock `Add-Type` fortfarande tillåta skript att vara implicit kompatibla med vilken version av PowerShell som helst.</span><span class="sxs-lookup"><span data-stu-id="31937-280">However, using `Add-Type` is still permitted to allow scripts to be implicitly compatible with any version of PowerShell.</span></span>

<span data-ttu-id="31937-281">Sammansättningar i GAC kan läsas in med typnamn i stället för sökväg.</span><span class="sxs-lookup"><span data-stu-id="31937-281">Assemblies in the GAC can be loaded by type name, rather than by path.</span></span> <span data-ttu-id="31937-282">Inläsning av sammansättningar från en godtycklig sökväg kräver `Add-Type` , eftersom dessa sammansättningar inte kan läsas in automatiskt.</span><span class="sxs-lookup"><span data-stu-id="31937-282">Loading assemblies from an arbitrary path requires `Add-Type`, since those assemblies cannot not be loaded automatically.</span></span>

## <span data-ttu-id="31937-283">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="31937-283">RELATED LINKS</span></span>

[<span data-ttu-id="31937-284">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="31937-284">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_profiles.md)

[<span data-ttu-id="31937-285">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="31937-285">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="31937-286">Lägg till medlem</span><span class="sxs-lookup"><span data-stu-id="31937-286">Add-Member</span></span>](Add-Member.md)

[<span data-ttu-id="31937-287">Nytt – objekt</span><span class="sxs-lookup"><span data-stu-id="31937-287">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="31937-288">OutputAssemblyType</span><span class="sxs-lookup"><span data-stu-id="31937-288">OutputAssemblyType</span></span>](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[<span data-ttu-id="31937-289">Plattforms anrop (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="31937-289">Platform Invoke (P/Invoke)</span></span>](/dotnet/standard/native-interop/pinvoke)

[<span data-ttu-id="31937-290">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="31937-290">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
