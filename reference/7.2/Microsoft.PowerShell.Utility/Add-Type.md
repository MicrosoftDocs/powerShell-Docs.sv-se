---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: d55925b0580542459e62e60108f855508232f232
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709114"
---
# <span data-ttu-id="abb83-102">Add-Type</span><span class="sxs-lookup"><span data-stu-id="abb83-102">Add-Type</span></span>

## <span data-ttu-id="abb83-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="abb83-103">SYNOPSIS</span></span>
<span data-ttu-id="abb83-104">Lägger till en Microsoft .NET Core-klass till en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="abb83-104">Adds a Microsoft .NET Core class to a PowerShell session.</span></span>

## <span data-ttu-id="abb83-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="abb83-105">SYNTAX</span></span>

### <span data-ttu-id="abb83-106">FromSource (standard)</span><span class="sxs-lookup"><span data-stu-id="abb83-106">FromSource (Default)</span></span>

```
Add-Type [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="abb83-107">FromMember</span><span class="sxs-lookup"><span data-stu-id="abb83-107">FromMember</span></span>

```
Add-Type [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>]
 [-UsingNamespace <String[]>] [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="abb83-108">FromPath</span><span class="sxs-lookup"><span data-stu-id="abb83-108">FromPath</span></span>

```
Add-Type [-Path] <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="abb83-109">FromLiteralPath</span><span class="sxs-lookup"><span data-stu-id="abb83-109">FromLiteralPath</span></span>

```
Add-Type -LiteralPath <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="abb83-110">FromAssemblyName</span><span class="sxs-lookup"><span data-stu-id="abb83-110">FromAssemblyName</span></span>

```
Add-Type -AssemblyName <String[]> [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="abb83-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="abb83-111">DESCRIPTION</span></span>

<span data-ttu-id="abb83-112">Med `Add-Type` cmdleten kan du definiera en Microsoft .net Core-klass i din PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="abb83-112">The `Add-Type` cmdlet lets you define a Microsoft .NET Core class in your PowerShell session.</span></span> <span data-ttu-id="abb83-113">Du kan sedan instansiera objekt med hjälp av `New-Object` cmdleten och använda objekten på samma sätt som du använder ett .net Core-objekt.</span><span class="sxs-lookup"><span data-stu-id="abb83-113">You can then instantiate objects, by using the `New-Object` cmdlet, and use the objects just as you would use any .NET Core object.</span></span> <span data-ttu-id="abb83-114">Om du lägger till ett `Add-Type` kommando i din PowerShell-profil, är klassen tillgänglig i alla PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="abb83-114">If you add an `Add-Type` command to your PowerShell profile, the class is available in all PowerShell sessions.</span></span>

<span data-ttu-id="abb83-115">Du kan ange typen genom att ange en befintlig sammansättning eller källfiler, eller så kan du ange käll koden infogad eller Sparad i en variabel.</span><span class="sxs-lookup"><span data-stu-id="abb83-115">You can specify the type by specifying an existing assembly or source code files, or you can specify the source code inline or saved in a variable.</span></span> <span data-ttu-id="abb83-116">Du kan även ange en metod och `Add-Type` definiera och generera klassen.</span><span class="sxs-lookup"><span data-stu-id="abb83-116">You can even specify only a method and `Add-Type` defines and generates the class.</span></span> <span data-ttu-id="abb83-117">I Windows kan du använda den här funktionen för att göra plattforms anrop (P/Invoke)-anrop till ohanterade funktioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abb83-117">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span> <span data-ttu-id="abb83-118">Om du anger käll kod `Add-Type` kompilerar den angivna käll koden och genererar en minnes intern sammansättning som innehåller de nya .net Core-typerna.</span><span class="sxs-lookup"><span data-stu-id="abb83-118">If you specify source code, `Add-Type` compiles the specified source code and generates an in-memory assembly that contains the new .NET Core types.</span></span>

<span data-ttu-id="abb83-119">Du kan använda parametrarna för `Add-Type` för att ange ett alternativt språk och en kompilerare, C# är standard, kompilator alternativ, sammansättnings beroenden, klass namn område, namn på typen och den resulterande sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="abb83-119">You can use the parameters of `Add-Type` to specify an alternate language and compiler, C# is the default, compiler options, assembly dependencies, the class namespace, the names of the type, and the resulting assembly.</span></span>

<span data-ttu-id="abb83-120">Från och med PowerShell 7 `Add-Type` kompileras inte en typ om det redan finns en typ med samma namn.</span><span class="sxs-lookup"><span data-stu-id="abb83-120">Beginning in PowerShell 7, `Add-Type` does not compile a type if a type with the same name already exists.</span></span> <span data-ttu-id="abb83-121">Söker också `Add-Type` efter sammansättningar i en `ref` mapp under mappen som innehåller `pwsh.dll` .</span><span class="sxs-lookup"><span data-stu-id="abb83-121">Also, `Add-Type` looks for assemblies in a `ref` folder under the folder that contains `pwsh.dll`.</span></span>

## <span data-ttu-id="abb83-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="abb83-122">EXAMPLES</span></span>

### <span data-ttu-id="abb83-123">Exempel 1: Lägg till en .NET-typ i en session</span><span class="sxs-lookup"><span data-stu-id="abb83-123">Example 1: Add a .NET type to a session</span></span>

<span data-ttu-id="abb83-124">I det här exemplet läggs klassen **BasicTest** till i sessionen genom att du anger käll koden som lagras i en variabel.</span><span class="sxs-lookup"><span data-stu-id="abb83-124">This example adds the **BasicTest** class to the session by specifying source code that is stored in a variable.</span></span> <span data-ttu-id="abb83-125">**BasicTest** -klassen används för att lägga till heltal, skapa ett objekt och multiplicera heltal.</span><span class="sxs-lookup"><span data-stu-id="abb83-125">The **BasicTest** class is used to add integers, create an object, and multiply integers.</span></span>

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

<span data-ttu-id="abb83-126">`$Source`Variabeln lagrar käll koden för klassen.</span><span class="sxs-lookup"><span data-stu-id="abb83-126">The `$Source` variable stores the source code for the class.</span></span> <span data-ttu-id="abb83-127">Typen har en statisk metod som kallas `Add` och en icke-statisk metod som kallas `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="abb83-127">The type has a static method called `Add` and a non-static method called `Multiply`.</span></span>

<span data-ttu-id="abb83-128">`Add-Type`Cmdleten lägger till klassen i sessionen.</span><span class="sxs-lookup"><span data-stu-id="abb83-128">The `Add-Type` cmdlet adds the class to the session.</span></span> <span data-ttu-id="abb83-129">Eftersom den använder infogad källkod använder kommandot **TypeDefinition** -parametern för att ange koden i `$Source` variabeln.</span><span class="sxs-lookup"><span data-stu-id="abb83-129">Because it's using inline source code, the command uses the **TypeDefinition** parameter to specify the code in the `$Source` variable.</span></span>

<span data-ttu-id="abb83-130">Den `Add` statiska metoden i **BasicTest** -klassen använder dubbla kolon tecken ( `::` ) för att ange en statisk medlem i klassen.</span><span class="sxs-lookup"><span data-stu-id="abb83-130">The `Add` static method of the **BasicTest** class uses the double-colon characters (`::`) to specify a static member of the class.</span></span> <span data-ttu-id="abb83-131">Heltalen läggs till och summan visas.</span><span class="sxs-lookup"><span data-stu-id="abb83-131">The integers are added and the sum is displayed.</span></span>

<span data-ttu-id="abb83-132">`New-Object`Cmdlet: en instansierar en instans av klassen **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="abb83-132">The `New-Object` cmdlet instantiates an instance of the **BasicTest** class.</span></span> <span data-ttu-id="abb83-133">Det sparar det nya objektet i `$BasicTestObject` variabeln.</span><span class="sxs-lookup"><span data-stu-id="abb83-133">It saves the new object in the `$BasicTestObject` variable.</span></span>

<span data-ttu-id="abb83-134">`$BasicTestObject` använder- `Multiply` metoden.</span><span class="sxs-lookup"><span data-stu-id="abb83-134">`$BasicTestObject` uses the `Multiply` method.</span></span> <span data-ttu-id="abb83-135">Heltalen multipliceras och produkten visas.</span><span class="sxs-lookup"><span data-stu-id="abb83-135">The integers are multiplied and the product is displayed.</span></span>

### <span data-ttu-id="abb83-136">Exempel 2: granska en tillagd typ</span><span class="sxs-lookup"><span data-stu-id="abb83-136">Example 2: Examine an added type</span></span>

<span data-ttu-id="abb83-137">I det här exemplet används `Get-Member` cmdleten för att undersöka de objekt som `Add-Type` `New-Object` cmdletarna och skapade i **exempel 1**.</span><span class="sxs-lookup"><span data-stu-id="abb83-137">This example uses the `Get-Member` cmdlet to examine the objects that the `Add-Type` and `New-Object` cmdlets created in **Example 1**.</span></span>

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

<span data-ttu-id="abb83-138">`Get-Member`Cmdleten hämtar typ och medlemmar i **BasicTest** -klassen som `Add-Type` har lagts till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="abb83-138">The `Get-Member` cmdlet gets the type and members of the **BasicTest** class that `Add-Type` added to the session.</span></span> <span data-ttu-id="abb83-139">`Get-Member`Kommandot visar att det är ett **system. RuntimeType** -objekt, som härleds från klassen **system. Object** .</span><span class="sxs-lookup"><span data-stu-id="abb83-139">The `Get-Member` command reveals that it's a **System.RuntimeType** object, which is derived from the **System.Object** class.</span></span>

<span data-ttu-id="abb83-140">Den `Get-Member` **statiska** parametern hämtar statiska egenskaper och metoder för klassen **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="abb83-140">The `Get-Member` **Static** parameter gets the static properties and methods of the **BasicTest** class.</span></span> <span data-ttu-id="abb83-141">Utdata visar att `Add` metoden ingår.</span><span class="sxs-lookup"><span data-stu-id="abb83-141">The output shows that the `Add` method is included.</span></span>

<span data-ttu-id="abb83-142">`Get-Member`Cmdlet: en hämtar medlemmarna i objektet som lagras i `$BasicTestObject` variabeln.</span><span class="sxs-lookup"><span data-stu-id="abb83-142">The `Get-Member` cmdlet gets the members of the object stored in the `$BasicTestObject` variable.</span></span>
<span data-ttu-id="abb83-143">`$BasicTestObject` har skapats med hjälp av `New-Object` cmdleten med klassen **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="abb83-143">`$BasicTestObject` was created by using the `New-Object` cmdlet with the **BasicTest** class.</span></span> <span data-ttu-id="abb83-144">Utdata visar att värdet för `$BasicTestObject` variabeln är en instans av klassen **BasicTest** och att den innehåller en medlem som kallas `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="abb83-144">The output reveals that the value of the `$BasicTestObject` variable is an instance of the **BasicTest** class and that it includes a member called `Multiply`.</span></span>

### <span data-ttu-id="abb83-145">Exempel 3: lägga till typer från en sammansättning</span><span class="sxs-lookup"><span data-stu-id="abb83-145">Example 3: Add types from an assembly</span></span>

<span data-ttu-id="abb83-146">I det här exemplet läggs klasserna från `NJsonSchema.dll` sammansättningen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="abb83-146">This example adds the classes from the `NJsonSchema.dll` assembly to the current session.</span></span>

```powershell
Set-Location -Path $PSHOME
$AccType = Add-Type -AssemblyName *jsonschema* -PassThru
```

<span data-ttu-id="abb83-147">`Set-Location` använder parametern **Path** för att ange `$PSHOME` variabeln.</span><span class="sxs-lookup"><span data-stu-id="abb83-147">`Set-Location` uses the **Path** parameter to specify the `$PSHOME` variable.</span></span> <span data-ttu-id="abb83-148">Variabeln refererar till PowerShell-installations katalogen där DLL-filen finns.</span><span class="sxs-lookup"><span data-stu-id="abb83-148">The variable references the PowerShell installation directory where the DLL file is located.</span></span>

<span data-ttu-id="abb83-149">`$AccType`Variabeln lagrar ett objekt som skapats med `Add-Type` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="abb83-149">The `$AccType` variable stores an object created with the `Add-Type` cmdlet.</span></span> <span data-ttu-id="abb83-150">`Add-Type` använder parametern **AssemblyName** för att ange namnet på sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="abb83-150">`Add-Type` uses the **AssemblyName** parameter to specify the name of the assembly.</span></span> <span data-ttu-id="abb83-151">Med jokertecknet asterisk ( `*` ) kan du hämta rätt sammansättning även om du inte är säker på namnet eller stavningen.</span><span class="sxs-lookup"><span data-stu-id="abb83-151">The asterisk (`*`) wildcard character allows you to get the correct assembly even when you aren't sure of the name or its spelling.</span></span> <span data-ttu-id="abb83-152">Parametern **Passthru** genererar objekt som representerar de klasser som läggs till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="abb83-152">The **PassThru** parameter generates objects that represent the classes that are added to the session.</span></span>

### <span data-ttu-id="abb83-153">Exempel 4: anropa inbyggda Windows-API: er</span><span class="sxs-lookup"><span data-stu-id="abb83-153">Example 4: Call native Windows APIs</span></span>

<span data-ttu-id="abb83-154">Det här exemplet visar hur du anropar inbyggda Windows-API: er i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abb83-154">This example demonstrates how to call native Windows APIs in PowerShell.</span></span> <span data-ttu-id="abb83-155">`Add-Type` använder mekanismen för plattforms anrop (P/Invoke) för att anropa en funktion i `User32.dll` från PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abb83-155">`Add-Type` uses the Platform Invoke (P/Invoke) mechanism to call a function in `User32.dll` from PowerShell.</span></span> <span data-ttu-id="abb83-156">Det här exemplet fungerar endast på datorer som kör operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="abb83-156">This example only works on computers running the Windows operating system.</span></span>

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

<span data-ttu-id="abb83-157">`$Signature`Variabeln lagrar C#-signaturen för `ShowWindowAsync` funktionen.</span><span class="sxs-lookup"><span data-stu-id="abb83-157">The `$Signature` variable stores the C# signature of the `ShowWindowAsync` function.</span></span> <span data-ttu-id="abb83-158">För att säkerställa att den resulterande metoden visas i en PowerShell-session har `public` nyckelordet lagts till i standard-signaturen.</span><span class="sxs-lookup"><span data-stu-id="abb83-158">To ensure that the resulting method is visible in a PowerShell session, the `public` keyword was added to the standard signature.</span></span> <span data-ttu-id="abb83-159">Mer information finns i [ShowWindowAsync-funktionen](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span><span class="sxs-lookup"><span data-stu-id="abb83-159">For more information, see [ShowWindowAsync function](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span></span>

<span data-ttu-id="abb83-160">`$ShowWindowAsync`Variabeln lagrar objektet som skapats av parametern `Add-Type` **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="abb83-160">The `$ShowWindowAsync` variable stores the object created by the `Add-Type` **PassThru** parameter.</span></span>
<span data-ttu-id="abb83-161">`Add-Type`Cmdleten lägger till `ShowWindowAsync` funktionen i PowerShell-sessionen som en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="abb83-161">The `Add-Type` cmdlet adds the `ShowWindowAsync` function to the PowerShell session as a static method.</span></span> <span data-ttu-id="abb83-162">Kommandot använder parametern **MemberDefinition** för att ange den metod definition som sparats i `$Signature` variabeln.</span><span class="sxs-lookup"><span data-stu-id="abb83-162">The command uses the **MemberDefinition** parameter to specify the method definition saved in the `$Signature` variable.</span></span> <span data-ttu-id="abb83-163">Kommandot använder **namn** och namn **områdes** parametrar för att ange ett namn och ett namn område för klassen.</span><span class="sxs-lookup"><span data-stu-id="abb83-163">The command uses the **Name** and **Namespace** parameters to specify a name and namespace for the class.</span></span> <span data-ttu-id="abb83-164">Parametern **Passthru** genererar ett objekt som representerar typerna.</span><span class="sxs-lookup"><span data-stu-id="abb83-164">The **PassThru** parameter generates an object that represents the types.</span></span>

<span data-ttu-id="abb83-165">Den nya `ShowWindowAsync` statiska metoden används i kommandona för att minimera och återställa PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="abb83-165">The new `ShowWindowAsync` static method is used in the commands to minimize and restore the PowerShell console.</span></span> <span data-ttu-id="abb83-166">Metoden tar två parametrar: fönster handtaget och ett heltal som anger hur fönstret visas.</span><span class="sxs-lookup"><span data-stu-id="abb83-166">The method takes two parameters: the window handle, and an integer that specifies how the window is displayed.</span></span>

<span data-ttu-id="abb83-167">För att minimera PowerShell-konsolen, `ShowWindowAsync` använder `Get-Process` cmdleten med den `$PID` automatiska variabeln för att hämta den process som är värd för den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="abb83-167">To minimize the PowerShell console, `ShowWindowAsync` uses the `Get-Process` cmdlet with the `$PID` automatic variable to get the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="abb83-168">Sedan används egenskapen **MainWindowHandle** för den aktuella processen och värdet `2` , som representerar `SW_MINIMIZE` värdet.</span><span class="sxs-lookup"><span data-stu-id="abb83-168">Then it uses the **MainWindowHandle** property of the current process and a value of `2`, which represents the `SW_MINIMIZE` value.</span></span>

<span data-ttu-id="abb83-169">För att återställa fönstret `ShowWindowAsync` använder värdet `4` för fönstrets position, som representerar `SW_RESTORE` värdet.</span><span class="sxs-lookup"><span data-stu-id="abb83-169">To restore the window, `ShowWindowAsync` uses a value of `4` for the window position, which represents the `SW_RESTORE` value.</span></span>

<span data-ttu-id="abb83-170">Maximera fönstret genom att använda värdet för `3` som representerar `SW_MAXIMIZE` .</span><span class="sxs-lookup"><span data-stu-id="abb83-170">To maximize the window, use the value of `3` that represents `SW_MAXIMIZE`.</span></span>

## <span data-ttu-id="abb83-171">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="abb83-171">PARAMETERS</span></span>

### <span data-ttu-id="abb83-172">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="abb83-172">-AssemblyName</span></span>

<span data-ttu-id="abb83-173">Anger namnet på en sammansättning som innehåller typerna.</span><span class="sxs-lookup"><span data-stu-id="abb83-173">Specifies the name of an assembly that includes the types.</span></span> <span data-ttu-id="abb83-174">`Add-Type` tar typer från den angivna sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="abb83-174">`Add-Type` takes the types from the specified assembly.</span></span> <span data-ttu-id="abb83-175">Den här parametern krävs när du skapar typer baserat på ett sammansättnings namn.</span><span class="sxs-lookup"><span data-stu-id="abb83-175">This parameter is required when you're creating types based on an assembly name.</span></span>

<span data-ttu-id="abb83-176">Ange det fullständiga eller enkla namnet, även kallat det partiella namnet för en sammansättning.</span><span class="sxs-lookup"><span data-stu-id="abb83-176">Enter the full or simple name, also known as the partial name, of an assembly.</span></span> <span data-ttu-id="abb83-177">Jokertecken tillåts i sammansättnings namnet.</span><span class="sxs-lookup"><span data-stu-id="abb83-177">Wildcard characters are permitted in the assembly name.</span></span> <span data-ttu-id="abb83-178">Om du anger ett enkelt eller partiellt namn `Add-Type` matchas det med det fullständiga namnet och sedan används det fullständiga namnet för att läsa in sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="abb83-178">If you enter a simple or partial name, `Add-Type` resolves it to the full name, and then uses the full name to load the assembly.</span></span>

<span data-ttu-id="abb83-179">Den här parametern accepterar inte en sökväg eller ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="abb83-179">This parameter doesn't accept a path or a filename.</span></span> <span data-ttu-id="abb83-180">Om du vill ange sökvägen till DLL-filen för Assembly-DLL-filen använder du parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="abb83-180">To enter the path to the assembly dynamic-link library (DLL) file, use the **Path** parameter.</span></span>

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

### <span data-ttu-id="abb83-181">-CompilerOptions</span><span class="sxs-lookup"><span data-stu-id="abb83-181">-CompilerOptions</span></span>

<span data-ttu-id="abb83-182">Anger alternativ för käll kods kompileraren.</span><span class="sxs-lookup"><span data-stu-id="abb83-182">Specifies the options for the source code compiler.</span></span> <span data-ttu-id="abb83-183">De här alternativen skickas till kompilatorn utan revidering.</span><span class="sxs-lookup"><span data-stu-id="abb83-183">These options are sent to the compiler without revision.</span></span>

<span data-ttu-id="abb83-184">Med den här parametern kan du dirigera kompilatorn för att generera en körbar fil, bädda in resurser eller ange kommando rads alternativ, till exempel `/unsafe` alternativet.</span><span class="sxs-lookup"><span data-stu-id="abb83-184">This parameter allows you to direct the compiler to generate an executable file, embed resources, or set command-line options, such as the `/unsafe` option.</span></span>

<span data-ttu-id="abb83-185">Du kan inte använda parametrarna **CompilerOptions** och **ReferencedAssemblies** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="abb83-185">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

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

### <span data-ttu-id="abb83-186">-IgnoreWarnings</span><span class="sxs-lookup"><span data-stu-id="abb83-186">-IgnoreWarnings</span></span>

<span data-ttu-id="abb83-187">Ignorerar kompilator varningar.</span><span class="sxs-lookup"><span data-stu-id="abb83-187">Ignores compiler warnings.</span></span> <span data-ttu-id="abb83-188">Använd den här parametern för att förhindra `Add-Type` hantering av kompilator varningar som fel.</span><span class="sxs-lookup"><span data-stu-id="abb83-188">Use this parameter to prevent `Add-Type` from handling compiler warnings as errors.</span></span>

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

### <span data-ttu-id="abb83-189">– Språk</span><span class="sxs-lookup"><span data-stu-id="abb83-189">-Language</span></span>

<span data-ttu-id="abb83-190">Anger det språk som används i käll koden.</span><span class="sxs-lookup"><span data-stu-id="abb83-190">Specifies the language that is used in the source code.</span></span> <span data-ttu-id="abb83-191">Det acceptabla värdet för den här parametern är **csharp**.</span><span class="sxs-lookup"><span data-stu-id="abb83-191">The acceptable value for this parameter is **CSharp**.</span></span>

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

### <span data-ttu-id="abb83-192">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="abb83-192">-LiteralPath</span></span>

<span data-ttu-id="abb83-193">Anger sökvägen till käll kods filer eller sammansättnings-DLL-filer som innehåller typerna.</span><span class="sxs-lookup"><span data-stu-id="abb83-193">Specifies the path to source code files or assembly DLL files that contain the types.</span></span> <span data-ttu-id="abb83-194">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det skrivs.</span><span class="sxs-lookup"><span data-stu-id="abb83-194">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="abb83-195">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="abb83-195">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="abb83-196">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="abb83-196">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="abb83-197">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="abb83-197">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="abb83-198">-MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="abb83-198">-MemberDefinition</span></span>

<span data-ttu-id="abb83-199">Anger nya egenskaper eller metoder för klassen.</span><span class="sxs-lookup"><span data-stu-id="abb83-199">Specifies new properties or methods for the class.</span></span> <span data-ttu-id="abb83-200">`Add-Type` skapar den mallkod som krävs för att stödja egenskaper eller metoder.</span><span class="sxs-lookup"><span data-stu-id="abb83-200">`Add-Type` generates the template code that is required to support the properties or methods.</span></span>

<span data-ttu-id="abb83-201">I Windows kan du använda den här funktionen för att göra plattforms anrop (P/Invoke)-anrop till ohanterade funktioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abb83-201">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span>

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

### <span data-ttu-id="abb83-202">-Name</span><span class="sxs-lookup"><span data-stu-id="abb83-202">-Name</span></span>

<span data-ttu-id="abb83-203">Anger namnet på den klass som ska skapas.</span><span class="sxs-lookup"><span data-stu-id="abb83-203">Specifies the name of the class to create.</span></span> <span data-ttu-id="abb83-204">Den här parametern krävs när en typ skapas från en medlems definition.</span><span class="sxs-lookup"><span data-stu-id="abb83-204">This parameter is required when generating a type from a member definition.</span></span>

<span data-ttu-id="abb83-205">Typ namnet och namn området måste vara unikt inom en session.</span><span class="sxs-lookup"><span data-stu-id="abb83-205">The type name and namespace must be unique within a session.</span></span> <span data-ttu-id="abb83-206">Du kan inte ta bort en typ eller ändra den.</span><span class="sxs-lookup"><span data-stu-id="abb83-206">You can't unload a type or change it.</span></span>
<span data-ttu-id="abb83-207">Om du vill ändra koden för en typ måste du ändra namnet eller starta en ny PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="abb83-207">To change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="abb83-208">Annars Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="abb83-208">Otherwise, the command fails.</span></span>

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

### <span data-ttu-id="abb83-209">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="abb83-209">-Namespace</span></span>

<span data-ttu-id="abb83-210">Anger ett namn område för typen.</span><span class="sxs-lookup"><span data-stu-id="abb83-210">Specifies a namespace for the type.</span></span>

<span data-ttu-id="abb83-211">Om den här parametern inte ingår i kommandot skapas typen i namn området **Microsoft. PowerShell. commands. AddType. AutoGeneratedTypes** .</span><span class="sxs-lookup"><span data-stu-id="abb83-211">If this parameter isn't included in the command, the type is created in the **Microsoft.PowerShell.Commands.AddType.AutoGeneratedTypes** namespace.</span></span> <span data-ttu-id="abb83-212">Om parametern ingår i kommandot med ett tomt sträng värde eller ett värde av `$Null` genereras typen i det globala namn området.</span><span class="sxs-lookup"><span data-stu-id="abb83-212">If the parameter is included in the command with an empty string value or a value of `$Null`, the type is generated in the global namespace.</span></span>

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

### <span data-ttu-id="abb83-213">-OutputAssembly</span><span class="sxs-lookup"><span data-stu-id="abb83-213">-OutputAssembly</span></span>

<span data-ttu-id="abb83-214">Genererar en DLL-fil för sammansättningen med det angivna namnet på platsen.</span><span class="sxs-lookup"><span data-stu-id="abb83-214">Generates a DLL file for the assembly with the specified name in the location.</span></span> <span data-ttu-id="abb83-215">Ange en valfri sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="abb83-215">Enter an optional path and filename.</span></span> <span data-ttu-id="abb83-216">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="abb83-216">Wildcard characters are permitted.</span></span> <span data-ttu-id="abb83-217">Som standard `Add-Type` genererar sammansättningen endast i minnet.</span><span class="sxs-lookup"><span data-stu-id="abb83-217">By default, `Add-Type` generates the assembly only in memory.</span></span>

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

### <span data-ttu-id="abb83-218">– OutputType</span><span class="sxs-lookup"><span data-stu-id="abb83-218">-OutputType</span></span>

<span data-ttu-id="abb83-219">Anger utdatatypen för den utgående sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="abb83-219">Specifies the output type of the output assembly.</span></span> <span data-ttu-id="abb83-220">Som standard har ingen Utdatatyp angetts.</span><span class="sxs-lookup"><span data-stu-id="abb83-220">By default, no output type is specified.</span></span> <span data-ttu-id="abb83-221">Den här parametern är endast giltig när en utgående sammansättning anges i kommandot.</span><span class="sxs-lookup"><span data-stu-id="abb83-221">This parameter is valid only when an output assembly is specified in the command.</span></span> <span data-ttu-id="abb83-222">Mer information om värdena finns i OutputAssemblyType- [uppräkning](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span><span class="sxs-lookup"><span data-stu-id="abb83-222">For more information about the values, see [OutputAssemblyType Enumeration](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span></span>

<span data-ttu-id="abb83-223">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="abb83-223">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="abb83-224">ConsoleApplication</span><span class="sxs-lookup"><span data-stu-id="abb83-224">ConsoleApplication</span></span>
- <span data-ttu-id="abb83-225">Bibliotek</span><span class="sxs-lookup"><span data-stu-id="abb83-225">Library</span></span>
- <span data-ttu-id="abb83-226">WindowsApplication</span><span class="sxs-lookup"><span data-stu-id="abb83-226">WindowsApplication</span></span>

> [!IMPORTANT]
> <span data-ttu-id="abb83-227">Från och med PowerShell 7,1 `ConsoleApplication` och som `WindowsApplication` inte stöds och returnerar PowerShell ett avslutande fel om någon av dem anges som värden för parametern **OutputType** .</span><span class="sxs-lookup"><span data-stu-id="abb83-227">As of PowerShell 7.1, `ConsoleApplication` and `WindowsApplication` are not supported and PowerShell throws a terminating error if either are specified as values for the **OutputType** parameter.</span></span>

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

### <span data-ttu-id="abb83-228">– PassThru</span><span class="sxs-lookup"><span data-stu-id="abb83-228">-PassThru</span></span>

<span data-ttu-id="abb83-229">Returnerar ett **system. Runtime** -objekt som representerar de typer som har lagts till.</span><span class="sxs-lookup"><span data-stu-id="abb83-229">Returns a **System.Runtime** object that represents the types that were added.</span></span> <span data-ttu-id="abb83-230">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="abb83-230">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="abb83-231">-Path</span><span class="sxs-lookup"><span data-stu-id="abb83-231">-Path</span></span>

<span data-ttu-id="abb83-232">Anger sökvägen till käll kods filer eller sammansättnings-DLL-filer som innehåller typerna.</span><span class="sxs-lookup"><span data-stu-id="abb83-232">Specifies the path to source code files or assembly DLL files that contain the types.</span></span>

<span data-ttu-id="abb83-233">Om du skickar källfiler `Add-Type` kompilerar koden i filerna och skapar en minnes intern sammansättning av typerna.</span><span class="sxs-lookup"><span data-stu-id="abb83-233">If you submit source code files, `Add-Type` compiles the code in the files and creates an in-memory assembly of the types.</span></span> <span data-ttu-id="abb83-234">Fil tillägget som anges i **Path** -värdet avgör vilken kompilator som `Add-Type` använder.</span><span class="sxs-lookup"><span data-stu-id="abb83-234">The file extension specified in the value of **Path** determines the compiler that `Add-Type` uses.</span></span>

<span data-ttu-id="abb83-235">Om du skickar en sammansättnings fil, `Add-Type` tar de olika typerna från sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="abb83-235">If you submit an assembly file, `Add-Type` takes the types from the assembly.</span></span> <span data-ttu-id="abb83-236">Om du vill ange en minnes intern sammansättning eller Global Assembly Cache använder du parametern **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="abb83-236">To specify an in-memory assembly or the global assembly cache, use the **AssemblyName** parameter.</span></span>

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

### <span data-ttu-id="abb83-237">-ReferencedAssemblies</span><span class="sxs-lookup"><span data-stu-id="abb83-237">-ReferencedAssemblies</span></span>

<span data-ttu-id="abb83-238">Anger de sammansättningar som typen är beroende av.</span><span class="sxs-lookup"><span data-stu-id="abb83-238">Specifies the assemblies upon which the type depends.</span></span> <span data-ttu-id="abb83-239">Som standard `Add-Type` refererar `System.dll` och `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="abb83-239">By default, `Add-Type` references `System.dll` and `System.Management.Automation.dll`.</span></span> <span data-ttu-id="abb83-240">De sammansättningar som du anger med hjälp av den här parametern refereras till utöver standard sammansättningarna.</span><span class="sxs-lookup"><span data-stu-id="abb83-240">The assemblies that you specify by using this parameter are referenced in addition to the default assemblies.</span></span>

<span data-ttu-id="abb83-241">Från och med PowerShell 6 inkluderar **ReferencedAssemblies** inte standard-.net-sammansättningarna.</span><span class="sxs-lookup"><span data-stu-id="abb83-241">Beginning in PowerShell 6, **ReferencedAssemblies** doesn't include the default .NET assemblies.</span></span> <span data-ttu-id="abb83-242">Du måste inkludera en speciell referens till dem i värdet som skickas till den här parametern.</span><span class="sxs-lookup"><span data-stu-id="abb83-242">You must include a specific reference to them in the value passed to this parameter.</span></span>

<span data-ttu-id="abb83-243">Du kan inte använda parametrarna **CompilerOptions** och **ReferencedAssemblies** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="abb83-243">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

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

### <span data-ttu-id="abb83-244">-TypeDefinition</span><span class="sxs-lookup"><span data-stu-id="abb83-244">-TypeDefinition</span></span>

<span data-ttu-id="abb83-245">Anger den käll kod som innehåller typ definitionerna.</span><span class="sxs-lookup"><span data-stu-id="abb83-245">Specifies the source code that contains the type definitions.</span></span> <span data-ttu-id="abb83-246">Ange käll koden i en sträng eller här – sträng, eller ange en variabel som innehåller käll koden.</span><span class="sxs-lookup"><span data-stu-id="abb83-246">Enter the source code in a string or here-string, or enter a variable that contains the source code.</span></span> <span data-ttu-id="abb83-247">Mer information om här – strängar finns [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="abb83-247">For more information about here-strings, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span></span>

<span data-ttu-id="abb83-248">Ta med en namn områdes deklaration i din typ definition.</span><span class="sxs-lookup"><span data-stu-id="abb83-248">Include a namespace declaration in your type definition.</span></span> <span data-ttu-id="abb83-249">Om du utelämnar namn områdes deklarationen kan typen ha samma namn som en annan typ eller genvägen till en annan typ, vilket orsakar en oavsiktlig överskrivning.</span><span class="sxs-lookup"><span data-stu-id="abb83-249">If you omit the namespace declaration, your type might have the same name as another type or the shortcut for another type, causing an unintentional overwrite.</span></span> <span data-ttu-id="abb83-250">Om du till exempel definierar en typ som heter **Exception**, kommer skript som använder **undantag** som genväg för **system. Exception** inte att fungera.</span><span class="sxs-lookup"><span data-stu-id="abb83-250">For example, if you define a type called **Exception**, scripts that use **Exception** as the shortcut for **System.Exception** will fail.</span></span>

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

### <span data-ttu-id="abb83-251">-UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="abb83-251">-UsingNamespace</span></span>

<span data-ttu-id="abb83-252">Anger andra namn områden som krävs för klassen.</span><span class="sxs-lookup"><span data-stu-id="abb83-252">Specifies other namespaces that are required for the class.</span></span> <span data-ttu-id="abb83-253">Detta är ungefär som nyckelordet C#, `Using` .</span><span class="sxs-lookup"><span data-stu-id="abb83-253">This is much like the C# keyword, `Using`.</span></span>

<span data-ttu-id="abb83-254">Som standard `Add-Type` refererar **system** namn området.</span><span class="sxs-lookup"><span data-stu-id="abb83-254">By default, `Add-Type` references the **System** namespace.</span></span> <span data-ttu-id="abb83-255">När parametern **MemberDefinition** används `Add-Type` refererar även namn området **system. Runtime. InteropServices** som standard.</span><span class="sxs-lookup"><span data-stu-id="abb83-255">When the **MemberDefinition** parameter is used, `Add-Type` also references the **System.Runtime.InteropServices** namespace by default.</span></span> <span data-ttu-id="abb83-256">De namn områden som du lägger till med hjälp av parametern **UsingNamespace** refereras till utöver standard namn områdena.</span><span class="sxs-lookup"><span data-stu-id="abb83-256">The namespaces that you add by using the **UsingNamespace** parameter are referenced in addition to the default namespaces.</span></span>

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

### <span data-ttu-id="abb83-257">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="abb83-257">CommonParameters</span></span>

<span data-ttu-id="abb83-258">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="abb83-258">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="abb83-259">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="abb83-259">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="abb83-260">INDATA</span><span class="sxs-lookup"><span data-stu-id="abb83-260">INPUTS</span></span>

### <span data-ttu-id="abb83-261">Inga</span><span class="sxs-lookup"><span data-stu-id="abb83-261">None</span></span>

<span data-ttu-id="abb83-262">Du kan inte skicka objekt nedåt i pipelinen till `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="abb83-262">You can't send objects down the pipeline to `Add-Type`.</span></span>

## <span data-ttu-id="abb83-263">UTDATA</span><span class="sxs-lookup"><span data-stu-id="abb83-263">OUTPUTS</span></span>

### <span data-ttu-id="abb83-264">Ingen eller system. Type</span><span class="sxs-lookup"><span data-stu-id="abb83-264">None or System.Type</span></span>

<span data-ttu-id="abb83-265">När du använder parametern **Passthru** `Add-Type` returneras ett **system. Type** -objekt som representerar den nya typen.</span><span class="sxs-lookup"><span data-stu-id="abb83-265">When you use the **PassThru** parameter, `Add-Type` returns a **System.Type** object that represents the new type.</span></span> <span data-ttu-id="abb83-266">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="abb83-266">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="abb83-267">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="abb83-267">NOTES</span></span>

<span data-ttu-id="abb83-268">De typer som du lägger till finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="abb83-268">The types that you add exist only in the current session.</span></span> <span data-ttu-id="abb83-269">Om du vill använda typerna i alla sessioner lägger du till dem i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="abb83-269">To use the types in all sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="abb83-270">Mer information om profilen finns [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="abb83-270">For more information about the profile, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="abb83-271">Typ namn och namn områden måste vara unika inom en session.</span><span class="sxs-lookup"><span data-stu-id="abb83-271">Type names and namespaces must be unique within a session.</span></span> <span data-ttu-id="abb83-272">Du kan inte ta bort en typ eller ändra den.</span><span class="sxs-lookup"><span data-stu-id="abb83-272">You can't unload a type or change it.</span></span> <span data-ttu-id="abb83-273">Om du behöver ändra koden för en typ måste du ändra namnet eller starta en ny PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="abb83-273">If you need to change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="abb83-274">Annars Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="abb83-274">Otherwise, the command fails.</span></span>

<span data-ttu-id="abb83-275">I Windows PowerShell (version 5,1 och senare) måste du använda `Add-Type` för allt som inte redan har lästs in.</span><span class="sxs-lookup"><span data-stu-id="abb83-275">In Windows PowerShell (version 5.1 and below), you need to use `Add-Type` for anything that isn't already loaded.</span></span> <span data-ttu-id="abb83-276">Oftast gäller detta för sammansättningar som finns i GAC (Global Assembly Cache).</span><span class="sxs-lookup"><span data-stu-id="abb83-276">Most commonly, this applies to assemblies found in the Global Assembly Cache (GAC).</span></span>
<span data-ttu-id="abb83-277">I PowerShell 6 och senare finns det ingen GAC, så PowerShell installerar sina egna sammansättningar i `$PSHome` .</span><span class="sxs-lookup"><span data-stu-id="abb83-277">In PowerShell 6 and higher, there is no GAC, so PowerShell installs its own assemblies in `$PSHome`.</span></span>
<span data-ttu-id="abb83-278">Dessa sammansättningar läses in automatiskt på begäran, så du behöver inte använda `Add-Type` för att läsa in dem.</span><span class="sxs-lookup"><span data-stu-id="abb83-278">These assemblies are automatically loaded on request, so there's no need to use `Add-Type` to load them.</span></span> <span data-ttu-id="abb83-279">Användningen tillåts dock `Add-Type` fortfarande tillåta skript att vara implicit kompatibla med vilken version av PowerShell som helst.</span><span class="sxs-lookup"><span data-stu-id="abb83-279">However, using `Add-Type` is still permitted to allow scripts to be implicitly compatible with any version of PowerShell.</span></span>

<span data-ttu-id="abb83-280">Sammansättningar i GAC kan läsas in med typnamn i stället för sökväg.</span><span class="sxs-lookup"><span data-stu-id="abb83-280">Assemblies in the GAC can be loaded by type name, rather than by path.</span></span> <span data-ttu-id="abb83-281">Inläsning av sammansättningar från en godtycklig sökväg kräver `Add-Type` , eftersom dessa sammansättningar inte kan läsas in automatiskt.</span><span class="sxs-lookup"><span data-stu-id="abb83-281">Loading assemblies from an arbitrary path requires `Add-Type`, since those assemblies cannot not be loaded automatically.</span></span>

## <span data-ttu-id="abb83-282">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="abb83-282">RELATED LINKS</span></span>

[<span data-ttu-id="abb83-283">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="abb83-283">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_profiles.md)

[<span data-ttu-id="abb83-284">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="abb83-284">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="abb83-285">Lägg till medlem</span><span class="sxs-lookup"><span data-stu-id="abb83-285">Add-Member</span></span>](Add-Member.md)

[<span data-ttu-id="abb83-286">Nytt – objekt</span><span class="sxs-lookup"><span data-stu-id="abb83-286">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="abb83-287">OutputAssemblyType</span><span class="sxs-lookup"><span data-stu-id="abb83-287">OutputAssemblyType</span></span>](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[<span data-ttu-id="abb83-288">Plattforms anrop (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="abb83-288">Platform Invoke (P/Invoke)</span></span>](/dotnet/standard/native-interop/pinvoke)

[<span data-ttu-id="abb83-289">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="abb83-289">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
