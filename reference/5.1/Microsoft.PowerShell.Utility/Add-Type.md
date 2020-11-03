---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: af7cd937ccfc7c5f05fd0213764ed51a3ba9f2bb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265185"
---
# <span data-ttu-id="b58cf-103">Add-Type</span><span class="sxs-lookup"><span data-stu-id="b58cf-103">Add-Type</span></span>

## <span data-ttu-id="b58cf-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b58cf-104">SYNOPSIS</span></span>
<span data-ttu-id="b58cf-105">Lägger till en Microsoft .NET Framework-klass till en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="b58cf-105">Adds a Microsoft .NET Framework class to a PowerShell session.</span></span>

## <span data-ttu-id="b58cf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b58cf-106">SYNTAX</span></span>

### <span data-ttu-id="b58cf-107">FromSource (standard)</span><span class="sxs-lookup"><span data-stu-id="b58cf-107">FromSource (Default)</span></span>

```
Add-Type [-CodeDomProvider <CodeDomProvider>] [-CompilerParameters <CompilerParameters>]
 [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [<CommonParameters>]
```

### <span data-ttu-id="b58cf-108">FromMember</span><span class="sxs-lookup"><span data-stu-id="b58cf-108">FromMember</span></span>

```
Add-Type [-CodeDomProvider <CodeDomProvider>] [-CompilerParameters <CompilerParameters>]
 [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>] [-UsingNamespace <String[]>]
 [-Language <Language>] [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

### <span data-ttu-id="b58cf-109">FromPath</span><span class="sxs-lookup"><span data-stu-id="b58cf-109">FromPath</span></span>

```
Add-Type [-CompilerParameters <CompilerParameters>] [-Path] <String[]>
 [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>]
 [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

### <span data-ttu-id="b58cf-110">FromLiteralPath</span><span class="sxs-lookup"><span data-stu-id="b58cf-110">FromLiteralPath</span></span>

```
Add-Type [-CompilerParameters <CompilerParameters>] -LiteralPath <String[]>
 [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>]
 [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

### <span data-ttu-id="b58cf-111">FromAssemblyName</span><span class="sxs-lookup"><span data-stu-id="b58cf-111">FromAssemblyName</span></span>

```
Add-Type -AssemblyName <String[]> [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

## <span data-ttu-id="b58cf-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b58cf-112">DESCRIPTION</span></span>

<span data-ttu-id="b58cf-113">Med `Add-Type` cmdleten kan du definiera en Microsoft .NET Framework-klass i din PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="b58cf-113">The `Add-Type` cmdlet lets you define a Microsoft .NET Framework class in your PowerShell session.</span></span>
<span data-ttu-id="b58cf-114">Du kan sedan instansiera objekt med hjälp av `New-Object` cmdleten och använda objekten på samma sätt som du använder ett .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="b58cf-114">You can then instantiate objects, by using the `New-Object` cmdlet, and use the objects just as you would use any .NET Framework object.</span></span> <span data-ttu-id="b58cf-115">Om du lägger till ett `Add-Type` kommando i din PowerShell-profil, är klassen tillgänglig i alla PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="b58cf-115">If you add an `Add-Type` command to your PowerShell profile, the class is available in all PowerShell sessions.</span></span>

<span data-ttu-id="b58cf-116">Du kan ange typen genom att ange en befintlig sammansättning eller källfiler, eller så kan du ange käll koden infogad eller Sparad i en variabel.</span><span class="sxs-lookup"><span data-stu-id="b58cf-116">You can specify the type by specifying an existing assembly or source code files, or you can specify the source code inline or saved in a variable.</span></span> <span data-ttu-id="b58cf-117">Du kan även ange en metod och `Add-Type` definiera och skapa klassen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-117">You can even specify only a method and `Add-Type` will define and generate the class.</span></span> <span data-ttu-id="b58cf-118">I Windows kan du använda den här funktionen för att göra plattforms anrop (P/Invoke)-anrop till ohanterade funktioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b58cf-118">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span> <span data-ttu-id="b58cf-119">Om du anger käll kod `Add-Type` kompilerar den angivna käll koden och genererar en minnes intern sammansättning som innehåller de nya .NET Framework typerna.</span><span class="sxs-lookup"><span data-stu-id="b58cf-119">If you specify source code, `Add-Type` compiles the specified source code and generates an in-memory assembly that contains the new .NET Framework types.</span></span>

<span data-ttu-id="b58cf-120">Du kan använda parametrarna för `Add-Type` för att ange ett alternativt språk och en kompilerare, C# är standard, kompilator alternativ, sammansättnings beroenden, klass namn område, namn på typen och den resulterande sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-120">You can use the parameters of `Add-Type` to specify an alternate language and compiler, C# is the default, compiler options, assembly dependencies, the class namespace, the names of the type, and the resulting assembly.</span></span>

## <span data-ttu-id="b58cf-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b58cf-121">EXAMPLES</span></span>

### <span data-ttu-id="b58cf-122">Exempel 1: Lägg till en .NET-typ i en session</span><span class="sxs-lookup"><span data-stu-id="b58cf-122">Example 1: Add a .NET type to a session</span></span>

<span data-ttu-id="b58cf-123">I det här exemplet läggs klassen **BasicTest** till i sessionen genom att du anger käll koden som lagras i en variabel.</span><span class="sxs-lookup"><span data-stu-id="b58cf-123">This example adds the **BasicTest** class to the session by specifying source code that is stored in a variable.</span></span> <span data-ttu-id="b58cf-124">**BasicTest** -klassen används för att lägga till heltal, skapa ett objekt och multiplicera heltal.</span><span class="sxs-lookup"><span data-stu-id="b58cf-124">The **BasicTest** class is used to add integers, create an object, and multiply integers.</span></span>

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

<span data-ttu-id="b58cf-125">`$Source`Variabeln lagrar käll koden för klassen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-125">The `$Source` variable stores the source code for the class.</span></span> <span data-ttu-id="b58cf-126">Typen har en statisk metod som kallas `Add` och en icke-statisk metod som kallas `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="b58cf-126">The type has a static method called `Add` and a non-static method called `Multiply`.</span></span>

<span data-ttu-id="b58cf-127">`Add-Type`Cmdleten lägger till klassen i sessionen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-127">The `Add-Type` cmdlet adds the class to the session.</span></span> <span data-ttu-id="b58cf-128">Eftersom den använder infogad källkod använder kommandot **TypeDefinition** -parametern för att ange koden i `$Source` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b58cf-128">Because it's using inline source code, the command uses the **TypeDefinition** parameter to specify the code in the `$Source` variable.</span></span>

<span data-ttu-id="b58cf-129">Den `Add` statiska metoden i **BasicTest** -klassen använder dubbla kolon tecken ( `::` ) för att ange en statisk medlem i klassen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-129">The `Add` static method of the **BasicTest** class uses the double-colon characters (`::`) to specify a static member of the class.</span></span> <span data-ttu-id="b58cf-130">Heltalen läggs till och summan visas.</span><span class="sxs-lookup"><span data-stu-id="b58cf-130">The integers are added and the sum is displayed.</span></span>

<span data-ttu-id="b58cf-131">`New-Object`Cmdlet: en instansierar en instans av klassen **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="b58cf-131">The `New-Object` cmdlet instantiates an instance of the **BasicTest** class.</span></span> <span data-ttu-id="b58cf-132">Det sparar det nya objektet i `$BasicTestObject` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b58cf-132">It saves the new object in the `$BasicTestObject` variable.</span></span>

<span data-ttu-id="b58cf-133">`$BasicTestObject` använder- `Multiply` metoden.</span><span class="sxs-lookup"><span data-stu-id="b58cf-133">`$BasicTestObject` uses the `Multiply` method.</span></span> <span data-ttu-id="b58cf-134">Heltalen multipliceras och produkten visas.</span><span class="sxs-lookup"><span data-stu-id="b58cf-134">The integers are multiplied and the product is displayed.</span></span>

### <span data-ttu-id="b58cf-135">Exempel 2: granska en tillagd typ</span><span class="sxs-lookup"><span data-stu-id="b58cf-135">Example 2: Examine an added type</span></span>

<span data-ttu-id="b58cf-136">I det här exemplet används `Get-Member` cmdleten för att undersöka de objekt som `Add-Type` `New-Object` cmdletarna och skapade i **exempel 1**.</span><span class="sxs-lookup"><span data-stu-id="b58cf-136">This example uses the `Get-Member` cmdlet to examine the objects that the `Add-Type` and `New-Object` cmdlets created in **Example 1**.</span></span>

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

<span data-ttu-id="b58cf-137">`Get-Member`Cmdleten hämtar typ och medlemmar i **BasicTest** -klassen som `Add-Type` har lagts till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-137">The `Get-Member` cmdlet gets the type and members of the **BasicTest** class that `Add-Type` added to the session.</span></span> <span data-ttu-id="b58cf-138">`Get-Member`Kommandot visar att det är ett **system. RuntimeType** -objekt, som härleds från klassen **system. Object** .</span><span class="sxs-lookup"><span data-stu-id="b58cf-138">The `Get-Member` command reveals that it's a **System.RuntimeType** object, which is derived from the **System.Object** class.</span></span>

<span data-ttu-id="b58cf-139">Den `Get-Member` **statiska** parametern hämtar statiska egenskaper och metoder för klassen **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="b58cf-139">The `Get-Member` **Static** parameter gets the static properties and methods of the **BasicTest** class.</span></span> <span data-ttu-id="b58cf-140">Utdata visar att `Add` metoden ingår.</span><span class="sxs-lookup"><span data-stu-id="b58cf-140">The output shows that the `Add` method is included.</span></span>

<span data-ttu-id="b58cf-141">`Get-Member`Cmdlet: en hämtar medlemmarna i objektet som lagras i `$BasicTestObject` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b58cf-141">The `Get-Member` cmdlet gets the members of the object stored in the `$BasicTestObject` variable.</span></span>
<span data-ttu-id="b58cf-142">`$BasicTestObject` har skapats med hjälp av `New-Object` cmdleten med klassen **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="b58cf-142">`$BasicTestObject` was created by using the `New-Object` cmdlet with the **BasicTest** class.</span></span> <span data-ttu-id="b58cf-143">Utdata visar att värdet för `$BasicTestObject` variabeln är en instans av klassen **BasicTest** och att den innehåller en medlem som kallas `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="b58cf-143">The output reveals that the value of the `$BasicTestObject` variable is an instance of the **BasicTest** class and that it includes a member called `Multiply`.</span></span>

### <span data-ttu-id="b58cf-144">Exempel 3: lägga till typer från en sammansättning</span><span class="sxs-lookup"><span data-stu-id="b58cf-144">Example 3: Add types from an assembly</span></span>

<span data-ttu-id="b58cf-145">I det här exemplet läggs klasserna från `Accessibility.dll` sammansättningen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-145">This example adds the classes from the `Accessibility.dll` assembly to the current session.</span></span>

```powershell
$AccType = Add-Type -AssemblyName "accessib*" -PassThru
```

<span data-ttu-id="b58cf-146">`$AccType`Variabeln lagrar ett objekt som skapats med `Add-Type` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b58cf-146">The `$AccType` variable stores an object created with the `Add-Type` cmdlet.</span></span> <span data-ttu-id="b58cf-147">`Add-Type` använder parametern **AssemblyName** för att ange namnet på sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-147">`Add-Type` uses the **AssemblyName** parameter to specify the name of the assembly.</span></span> <span data-ttu-id="b58cf-148">Med jokertecknet asterisk ( `*` ) kan du hämta rätt sammansättning även om du inte är säker på namnet eller stavningen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-148">The asterisk (`*`) wildcard character allows you to get the correct assembly even when you aren't sure of the name or its spelling.</span></span> <span data-ttu-id="b58cf-149">Parametern **Passthru** genererar objekt som representerar de klasser som läggs till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-149">The **PassThru** parameter generates objects that represent the classes that are added to the session.</span></span>

### <span data-ttu-id="b58cf-150">Exempel 4: anropa inbyggda Windows-API: er</span><span class="sxs-lookup"><span data-stu-id="b58cf-150">Example 4: Call native Windows APIs</span></span>

<span data-ttu-id="b58cf-151">Det här exemplet visar hur du anropar inbyggda Windows-API: er i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b58cf-151">This example demonstrates how to call native Windows APIs in PowerShell.</span></span> <span data-ttu-id="b58cf-152">`Add-Type` använder mekanismen för plattforms anrop (P/Invoke) för att anropa en funktion i `User32.dll` från PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b58cf-152">`Add-Type` uses the Platform Invoke (P/Invoke) mechanism to call a function in `User32.dll` from PowerShell.</span></span> <span data-ttu-id="b58cf-153">Det här exemplet fungerar endast på datorer som kör operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="b58cf-153">This example only works on computers running the Windows operating system.</span></span>

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

<span data-ttu-id="b58cf-154">`$Signature`Variabeln lagrar C#-signaturen för `ShowWindowAsync` funktionen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-154">The `$Signature` variable stores the C# signature of the `ShowWindowAsync` function.</span></span> <span data-ttu-id="b58cf-155">För att säkerställa att den resulterande metoden visas i en PowerShell-session har `public` nyckelordet lagts till i standard-signaturen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-155">To ensure that the resulting method will be visible in a PowerShell session, the `public` keyword was added to the standard signature.</span></span> <span data-ttu-id="b58cf-156">Mer information finns i [ShowWindowAsync-funktionen](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span><span class="sxs-lookup"><span data-stu-id="b58cf-156">For more information, see [ShowWindowAsync function](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span></span>

<span data-ttu-id="b58cf-157">`$ShowWindowAsync`Variabeln lagrar objektet som skapats av parametern `Add-Type` **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="b58cf-157">The `$ShowWindowAsync` variable stores the object created by the `Add-Type` **PassThru** parameter.</span></span>
<span data-ttu-id="b58cf-158">`Add-Type`Cmdleten lägger till `ShowWindowAsync` funktionen i PowerShell-sessionen som en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="b58cf-158">The `Add-Type` cmdlet adds the `ShowWindowAsync` function to the PowerShell session as a static method.</span></span> <span data-ttu-id="b58cf-159">Kommandot använder parametern **MemberDefinition** för att ange den metod definition som sparats i `$Signature` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b58cf-159">The command uses the **MemberDefinition** parameter to specify the method definition saved in the `$Signature` variable.</span></span> <span data-ttu-id="b58cf-160">Kommandot använder **namn** och namn **områdes** parametrar för att ange ett namn och ett namn område för klassen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-160">The command uses the **Name** and **Namespace** parameters to specify a name and namespace for the class.</span></span> <span data-ttu-id="b58cf-161">Parametern **Passthru** genererar ett objekt som representerar typerna.</span><span class="sxs-lookup"><span data-stu-id="b58cf-161">The **PassThru** parameter generates an object that represents the types.</span></span>

<span data-ttu-id="b58cf-162">Den nya `ShowWindowAsync` statiska metoden används i kommandona för att minimera och återställa PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-162">The new `ShowWindowAsync` static method is used in the commands to minimize and restore the PowerShell console.</span></span> <span data-ttu-id="b58cf-163">Metoden tar två parametrar: fönster handtaget och ett heltal som anger hur fönstret visas.</span><span class="sxs-lookup"><span data-stu-id="b58cf-163">The method takes two parameters: the window handle, and an integer that specifies how the window is displayed.</span></span>

<span data-ttu-id="b58cf-164">För att minimera PowerShell-konsolen, `ShowWindowAsync` använder `Get-Process` cmdleten med den `$PID` automatiska variabeln för att hämta den process som är värd för den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-164">To minimize the PowerShell console, `ShowWindowAsync` uses the `Get-Process` cmdlet with the `$PID` automatic variable to get the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="b58cf-165">Sedan används egenskapen **MainWindowHandle** för den aktuella processen och värdet `2` , som representerar `SW_MINIMIZE` värdet.</span><span class="sxs-lookup"><span data-stu-id="b58cf-165">Then it uses the **MainWindowHandle** property of the current process and a value of `2`, which represents the `SW_MINIMIZE` value.</span></span>

<span data-ttu-id="b58cf-166">För att återställa fönstret `ShowWindowAsync` använder värdet `4` för fönstrets position, som representerar `SW_RESTORE` värdet.</span><span class="sxs-lookup"><span data-stu-id="b58cf-166">To restore the window, `ShowWindowAsync` uses a value of `4` for the window position, which represents the `SW_RESTORE` value.</span></span>

<span data-ttu-id="b58cf-167">Maximera fönstret genom att använda värdet för `3` som representerar `SW_MAXIMIZE` .</span><span class="sxs-lookup"><span data-stu-id="b58cf-167">To maximize the window, use the value of `3` that represents `SW_MAXIMIZE`.</span></span>

### <span data-ttu-id="b58cf-168">Exempel 5: Lägg till en typ från en Visual Basic-fil</span><span class="sxs-lookup"><span data-stu-id="b58cf-168">Example 5: Add a type from a Visual Basic file</span></span>

<span data-ttu-id="b58cf-169">I det här exemplet används `Add-Type` cmdleten för att lägga till **VBFromFile** -klassen som är definierad i `Hello.vb` filen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-169">This example uses the `Add-Type` cmdlet to add the **VBFromFile** class that's defined in the `Hello.vb` file to the current session.</span></span> <span data-ttu-id="b58cf-170">`Hello.vb`Filens text visas i kommandots utdata.</span><span class="sxs-lookup"><span data-stu-id="b58cf-170">The text of the `Hello.vb` file is shown in the command output.</span></span>

```powershell
Add-Type -Path "C:\PS-Test\Hello.vb"
[VBFromFile]::SayHello(", World")

# From Hello.vb

Public Class VBFromFile
  Public Shared Function SayHello(sourceName As String) As String
    Dim myValue As String = "Hello"
    return myValue + sourceName
  End Function
End Class
```

```Output
Hello, World
```

<span data-ttu-id="b58cf-171">`Add-Type` använder parametern **Path** för att ange käll filen, `Hello.vb` och lägger till den typ som definierats i filen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-171">`Add-Type` uses the **Path** parameter to specify the source file, `Hello.vb`, and adds the type defined in the file.</span></span> <span data-ttu-id="b58cf-172">`SayHello`Funktionen anropas som en statisk metod i klassen **VBFromFile** .</span><span class="sxs-lookup"><span data-stu-id="b58cf-172">The `SayHello` function is called as a static method of the **VBFromFile** class.</span></span>

### <span data-ttu-id="b58cf-173">Exempel 6: Lägg till en klass med JScript.NET</span><span class="sxs-lookup"><span data-stu-id="b58cf-173">Example 6: Add a class with JScript.NET</span></span>

<span data-ttu-id="b58cf-174">I det här exemplet används JScript.NET för att skapa en ny klass, **FRectangle** , i din PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="b58cf-174">This example uses JScript.NET to create a new class, **FRectangle** , in your PowerShell session.</span></span>

```powershell
Add-Type @'
 class FRectangle {
   var Length : double;
   var Height : double;
   function Perimeter() : double {
       return (Length + Height) * 2; }
   function Area() : double {
       return Length * Height;  } }
'@ -Language JScript

$rect = [FRectangle]::new()
$rect
```

```Output
Length Height
------ ------
     0      0
```

### <span data-ttu-id="b58cf-175">Exempel 7: Lägg till en F #-kompilator</span><span class="sxs-lookup"><span data-stu-id="b58cf-175">Example 7: Add an F# compiler</span></span>

<span data-ttu-id="b58cf-176">Det här exemplet visar hur du använder `Add-Type` cmdleten för att lägga till en F #-kod kompilator i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-176">This example shows how to use the `Add-Type` cmdlet to add an F# code compiler to your PowerShell session.</span></span> <span data-ttu-id="b58cf-177">Om du vill köra det här exemplet i PowerShell måste du ha det `FSharp.Compiler.CodeDom.dll` som är installerat med F #-språket.</span><span class="sxs-lookup"><span data-stu-id="b58cf-177">To run this example in PowerShell, you must have the `FSharp.Compiler.CodeDom.dll` that is installed with the F# language.</span></span>

```powershell
Add-Type -Path "FSharp.Compiler.CodeDom.dll"
$Provider = New-Object Microsoft.FSharp.Compiler.CodeDom.FSharpCodeProvider
$FSharpCode = @"
let rec loop n =if n <= 0 then () else beginprint_endline (string_of_int n);loop (n-1)end
"@
$FSharpType = Add-Type -TypeDefinition $FSharpCode -CodeDomProvider $Provider -PassThru |
   Where-Object { $_.IsPublic }
$FSharpType::loop(4)
```

```Output
4
3
2
1
```

<span data-ttu-id="b58cf-178">`Add-Type` använder parametern **Path** för att ange en sammansättning och hämtar typerna i sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-178">`Add-Type` uses the **Path** parameter to specify an assembly and gets the types in the assembly.</span></span>
<span data-ttu-id="b58cf-179">`New-Object` skapar en instans av providern för F #-kod och sparar resultatet i `$Provider` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b58cf-179">`New-Object` creates an instance of the F# code provider and saves the result in the `$Provider` variable.</span></span> <span data-ttu-id="b58cf-180">`$FSharpCode`Variabeln sparar F #-koden som definierar **loop** -metoden.</span><span class="sxs-lookup"><span data-stu-id="b58cf-180">The `$FSharpCode` variable saves the F# code that defines the **Loop** method.</span></span>

<span data-ttu-id="b58cf-181">`$FSharpType`Variabeln lagrar resultatet från den `Add-Type` cmdlet som sparar de offentliga typer som definieras i `$FSharpCode` .</span><span class="sxs-lookup"><span data-stu-id="b58cf-181">The the `$FSharpType` variable stores the results of the `Add-Type` cmdlet that saves the public types defined in `$FSharpCode`.</span></span> <span data-ttu-id="b58cf-182">Parametern **TypeDefinition** anger den käll kod som definierar typerna.</span><span class="sxs-lookup"><span data-stu-id="b58cf-182">The **TypeDefinition** parameter specifies the source code that defines the types.</span></span> <span data-ttu-id="b58cf-183">Parametern **CodeDomProvider** anger käll kods kompilatorn.</span><span class="sxs-lookup"><span data-stu-id="b58cf-183">The **CodeDomProvider** parameter specifies the source code compiler.</span></span> <span data-ttu-id="b58cf-184">Parametern **Passthru** styrs `Add-Type` för att returnera ett **körnings** objekt som representerar typerna.</span><span class="sxs-lookup"><span data-stu-id="b58cf-184">The **PassThru** parameter directs `Add-Type` to return a **Runtime** object that represents the types.</span></span>
<span data-ttu-id="b58cf-185">Objekten skickas ned pipelinen till `Where-Object` cmdleten, som endast returnerar de offentliga typerna.</span><span class="sxs-lookup"><span data-stu-id="b58cf-185">The objects are sent down the pipeline to the `Where-Object` cmdlet, which returns only the public types.</span></span> <span data-ttu-id="b58cf-186">Cmdleten **Where-Object** används eftersom F #-providern genererar icke-offentliga typer för att stödja den offentliga typ som stöds.</span><span class="sxs-lookup"><span data-stu-id="b58cf-186">The **Where-Object** cmdlet is used because the F# provider generates non-public types to support the resulting public type.</span></span>

<span data-ttu-id="b58cf-187">Loop-metoden anropas som en statisk metod av typen som lagras i `$FSharpType` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b58cf-187">The Loop method is called as a static method of the type stored in the `$FSharpType` variable.</span></span>

## <span data-ttu-id="b58cf-188">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b58cf-188">PARAMETERS</span></span>

### <span data-ttu-id="b58cf-189">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="b58cf-189">-AssemblyName</span></span>

<span data-ttu-id="b58cf-190">Anger namnet på en sammansättning som innehåller typerna.</span><span class="sxs-lookup"><span data-stu-id="b58cf-190">Specifies the name of an assembly that includes the types.</span></span> <span data-ttu-id="b58cf-191">`Add-Type` tar typer från den angivna sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-191">`Add-Type` takes the types from the specified assembly.</span></span> <span data-ttu-id="b58cf-192">Den här parametern krävs när du skapar typer baserat på ett sammansättnings namn.</span><span class="sxs-lookup"><span data-stu-id="b58cf-192">This parameter is required when you're creating types based on an assembly name.</span></span>

<span data-ttu-id="b58cf-193">Ange det fullständiga eller enkla namnet, även kallat det partiella namnet för en sammansättning.</span><span class="sxs-lookup"><span data-stu-id="b58cf-193">Enter the full or simple name, also known as the partial name, of an assembly.</span></span> <span data-ttu-id="b58cf-194">Jokertecken tillåts i sammansättnings namnet.</span><span class="sxs-lookup"><span data-stu-id="b58cf-194">Wildcard characters are permitted in the assembly name.</span></span> <span data-ttu-id="b58cf-195">Om du anger ett enkelt eller partiellt namn `Add-Type` matchas det med det fullständiga namnet och sedan används det fullständiga namnet för att läsa in sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-195">If you enter a simple or partial name, `Add-Type` resolves it to the full name, and then uses the full name to load the assembly.</span></span>

<span data-ttu-id="b58cf-196">Den här parametern accepterar inte en sökväg eller ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="b58cf-196">This parameter doesn't accept a path or a file name.</span></span> <span data-ttu-id="b58cf-197">Om du vill ange sökvägen till DLL-filen för Assembly-DLL-filen använder du parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="b58cf-197">To enter the path to the assembly dynamic-link library (DLL) file, use the **Path** parameter.</span></span>

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

### <span data-ttu-id="b58cf-198">– CodeDomProvider</span><span class="sxs-lookup"><span data-stu-id="b58cf-198">-CodeDomProvider</span></span>

<span data-ttu-id="b58cf-199">Anger en kod generator eller kompilerare.</span><span class="sxs-lookup"><span data-stu-id="b58cf-199">Specifies a code generator or compiler.</span></span> <span data-ttu-id="b58cf-200">`Add-Type` använder den angivna kompilatorn för att kompilera käll koden.</span><span class="sxs-lookup"><span data-stu-id="b58cf-200">`Add-Type` uses the specified compiler to compile the source code.</span></span> <span data-ttu-id="b58cf-201">Standardvärdet är C#-kompilatorn.</span><span class="sxs-lookup"><span data-stu-id="b58cf-201">The default is the C# compiler.</span></span> <span data-ttu-id="b58cf-202">Använd den här parametern om du använder ett språk som inte kan anges med hjälp av **språk** parametern.</span><span class="sxs-lookup"><span data-stu-id="b58cf-202">Use this parameter if you're using a language that can't be specified by using the **Language** parameter.</span></span> <span data-ttu-id="b58cf-203">**CodeDomProvider** som du anger måste kunna generera sammansättningar från käll koden.</span><span class="sxs-lookup"><span data-stu-id="b58cf-203">The **CodeDomProvider** that you specify must be able to generate assemblies from source code.</span></span>

```yaml
Type: System.CodeDom.Compiler.CodeDomProvider
Parameter Sets: FromSource, FromMember
Aliases: Provider

Required: False
Position: Named
Default value: C# compiler
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b58cf-204">-CompilerParameters</span><span class="sxs-lookup"><span data-stu-id="b58cf-204">-CompilerParameters</span></span>

<span data-ttu-id="b58cf-205">Anger alternativ för käll kods kompileraren.</span><span class="sxs-lookup"><span data-stu-id="b58cf-205">Specifies the options for the source code compiler.</span></span> <span data-ttu-id="b58cf-206">De här alternativen skickas till kompilatorn utan revidering.</span><span class="sxs-lookup"><span data-stu-id="b58cf-206">These options are sent to the compiler without revision.</span></span>

<span data-ttu-id="b58cf-207">Med den här parametern kan du dirigera kompilatorn för att generera en körbar fil, bädda in resurser eller ange kommando rads alternativ, till exempel `/unsafe` alternativet.</span><span class="sxs-lookup"><span data-stu-id="b58cf-207">This parameter allows you to direct the compiler to generate an executable file, embed resources, or set command-line options, such as the `/unsafe` option.</span></span> <span data-ttu-id="b58cf-208">Den här parametern implementerar klassen **CompilerParameters** , **system. CodeDom. compiler. CompilerParameters**.</span><span class="sxs-lookup"><span data-stu-id="b58cf-208">This parameter implements the **CompilerParameters** class, **System.CodeDom.Compiler.CompilerParameters**.</span></span>

<span data-ttu-id="b58cf-209">Du kan inte använda parametrarna **CompilerParameters** och **ReferencedAssemblies** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="b58cf-209">You can't use the **CompilerParameters** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.CodeDom.Compiler.CompilerParameters
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: CP

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b58cf-210">-IgnoreWarnings</span><span class="sxs-lookup"><span data-stu-id="b58cf-210">-IgnoreWarnings</span></span>

<span data-ttu-id="b58cf-211">Ignorerar kompilator varningar.</span><span class="sxs-lookup"><span data-stu-id="b58cf-211">Ignores compiler warnings.</span></span> <span data-ttu-id="b58cf-212">Använd den här parametern för att förhindra `Add-Type` hantering av kompilator varningar som fel.</span><span class="sxs-lookup"><span data-stu-id="b58cf-212">Use this parameter to prevent `Add-Type` from handling compiler warnings as errors.</span></span>

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

### <span data-ttu-id="b58cf-213">– Språk</span><span class="sxs-lookup"><span data-stu-id="b58cf-213">-Language</span></span>

<span data-ttu-id="b58cf-214">Anger det språk som används i käll koden.</span><span class="sxs-lookup"><span data-stu-id="b58cf-214">Specifies the language that is used in the source code.</span></span> <span data-ttu-id="b58cf-215">`Add-Type`Cmdleten använder värdet för den här parametern för att välja lämplig **CodeDomProvider**.</span><span class="sxs-lookup"><span data-stu-id="b58cf-215">The `Add-Type` cmdlet uses the value of this parameter to select the appropriate **CodeDomProvider**.</span></span> <span data-ttu-id="b58cf-216">CSharp är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="b58cf-216">CSharp is the default value.</span></span> <span data-ttu-id="b58cf-217">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="b58cf-217">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="b58cf-218">CSharp</span><span class="sxs-lookup"><span data-stu-id="b58cf-218">CSharp</span></span>
- <span data-ttu-id="b58cf-219">CSharpVersion2</span><span class="sxs-lookup"><span data-stu-id="b58cf-219">CSharpVersion2</span></span>
- <span data-ttu-id="b58cf-220">CSharpVersion3</span><span class="sxs-lookup"><span data-stu-id="b58cf-220">CSharpVersion3</span></span>
- <span data-ttu-id="b58cf-221">JScript</span><span class="sxs-lookup"><span data-stu-id="b58cf-221">JScript</span></span>
- <span data-ttu-id="b58cf-222">VisualBasic</span><span class="sxs-lookup"><span data-stu-id="b58cf-222">VisualBasic</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.Language
Parameter Sets: FromSource, FromMember
Aliases:
Accepted values: CSharp, CSharpVersion2, CSharpVersion3, JScript, VisualBasic

Required: False
Position: Named
Default value: CSharp
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b58cf-223">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b58cf-223">-LiteralPath</span></span>

<span data-ttu-id="b58cf-224">Anger sökvägen till käll kods filer eller sammansättnings-DLL-filer som innehåller typerna.</span><span class="sxs-lookup"><span data-stu-id="b58cf-224">Specifies the path to source code files or assembly DLL files that contain the types.</span></span> <span data-ttu-id="b58cf-225">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det skrivs.</span><span class="sxs-lookup"><span data-stu-id="b58cf-225">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="b58cf-226">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="b58cf-226">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b58cf-227">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="b58cf-227">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b58cf-228">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="b58cf-228">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b58cf-229">-MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="b58cf-229">-MemberDefinition</span></span>

<span data-ttu-id="b58cf-230">Anger nya egenskaper eller metoder för klassen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-230">Specifies new properties or methods for the class.</span></span> <span data-ttu-id="b58cf-231">`Add-Type` skapar den mallkod som krävs för att stödja egenskaper eller metoder.</span><span class="sxs-lookup"><span data-stu-id="b58cf-231">`Add-Type` generates the template code that is required to support the properties or methods.</span></span>

<span data-ttu-id="b58cf-232">I Windows kan du använda den här funktionen för att göra plattforms anrop (P/Invoke)-anrop till ohanterade funktioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b58cf-232">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span>

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

### <span data-ttu-id="b58cf-233">-Name</span><span class="sxs-lookup"><span data-stu-id="b58cf-233">-Name</span></span>

<span data-ttu-id="b58cf-234">Anger namnet på den klass som ska skapas.</span><span class="sxs-lookup"><span data-stu-id="b58cf-234">Specifies the name of the class to create.</span></span> <span data-ttu-id="b58cf-235">Den här parametern krävs när en typ skapas från en medlems definition.</span><span class="sxs-lookup"><span data-stu-id="b58cf-235">This parameter is required when generating a type from a member definition.</span></span>

<span data-ttu-id="b58cf-236">Typ namnet och namn området måste vara unikt inom en session.</span><span class="sxs-lookup"><span data-stu-id="b58cf-236">The type name and namespace must be unique within a session.</span></span> <span data-ttu-id="b58cf-237">Du kan inte ta bort en typ eller ändra den.</span><span class="sxs-lookup"><span data-stu-id="b58cf-237">You can't unload a type or change it.</span></span>
<span data-ttu-id="b58cf-238">Om du vill ändra koden för en typ måste du ändra namnet eller starta en ny PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="b58cf-238">To change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="b58cf-239">Annars Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="b58cf-239">Otherwise, the command fails.</span></span>

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

### <span data-ttu-id="b58cf-240">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="b58cf-240">-Namespace</span></span>

<span data-ttu-id="b58cf-241">Anger ett namn område för typen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-241">Specifies a namespace for the type.</span></span>

<span data-ttu-id="b58cf-242">Om den här parametern inte ingår i kommandot skapas typen i namn området **Microsoft. PowerShell. commands. AddType. AutoGeneratedTypes** .</span><span class="sxs-lookup"><span data-stu-id="b58cf-242">If this parameter isn't included in the command, the type is created in the **Microsoft.PowerShell.Commands.AddType.AutoGeneratedTypes** namespace.</span></span> <span data-ttu-id="b58cf-243">Om parametern ingår i kommandot med ett tomt sträng värde eller ett värde av `$Null` genereras typen i det globala namn området.</span><span class="sxs-lookup"><span data-stu-id="b58cf-243">If the parameter is included in the command with an empty string value or a value of `$Null`, the type is generated in the global namespace.</span></span>

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

### <span data-ttu-id="b58cf-244">-OutputAssembly</span><span class="sxs-lookup"><span data-stu-id="b58cf-244">-OutputAssembly</span></span>

<span data-ttu-id="b58cf-245">Genererar en DLL-fil för sammansättningen med det angivna namnet på platsen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-245">Generates a DLL file for the assembly with the specified name in the location.</span></span> <span data-ttu-id="b58cf-246">Ange en valfri sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="b58cf-246">Enter an optional path and file name.</span></span> <span data-ttu-id="b58cf-247">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="b58cf-247">Wildcard characters are permitted.</span></span> <span data-ttu-id="b58cf-248">Som standard `Add-Type` genererar sammansättningen endast i minnet.</span><span class="sxs-lookup"><span data-stu-id="b58cf-248">By default, `Add-Type` generates the assembly only in memory.</span></span>

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

### <span data-ttu-id="b58cf-249">– OutputType</span><span class="sxs-lookup"><span data-stu-id="b58cf-249">-OutputType</span></span>

<span data-ttu-id="b58cf-250">Anger utdatatypen för den utgående sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-250">Specifies the output type of the output assembly.</span></span> <span data-ttu-id="b58cf-251">Som standard har ingen Utdatatyp angetts.</span><span class="sxs-lookup"><span data-stu-id="b58cf-251">By default, no output type is specified.</span></span> <span data-ttu-id="b58cf-252">Den här parametern är endast giltig när en utgående sammansättning anges i kommandot.</span><span class="sxs-lookup"><span data-stu-id="b58cf-252">This parameter is valid only when an output assembly is specified in the command.</span></span> <span data-ttu-id="b58cf-253">Mer information om värdena finns i OutputAssemblyType- [uppräkning](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span><span class="sxs-lookup"><span data-stu-id="b58cf-253">For more information about the values, see [OutputAssemblyType Enumeration](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span></span>

<span data-ttu-id="b58cf-254">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="b58cf-254">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="b58cf-255">ConsoleApplication</span><span class="sxs-lookup"><span data-stu-id="b58cf-255">ConsoleApplication</span></span>
- <span data-ttu-id="b58cf-256">Bibliotek</span><span class="sxs-lookup"><span data-stu-id="b58cf-256">Library</span></span>
- <span data-ttu-id="b58cf-257">WindowsApplication</span><span class="sxs-lookup"><span data-stu-id="b58cf-257">WindowsApplication</span></span>

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

### <span data-ttu-id="b58cf-258">– PassThru</span><span class="sxs-lookup"><span data-stu-id="b58cf-258">-PassThru</span></span>

<span data-ttu-id="b58cf-259">Returnerar ett **system. Runtime** -objekt som representerar de typer som har lagts till.</span><span class="sxs-lookup"><span data-stu-id="b58cf-259">Returns a **System.Runtime** object that represents the types that were added.</span></span> <span data-ttu-id="b58cf-260">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b58cf-260">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="b58cf-261">-Path</span><span class="sxs-lookup"><span data-stu-id="b58cf-261">-Path</span></span>

<span data-ttu-id="b58cf-262">Anger sökvägen till käll kods filer eller sammansättnings-DLL-filer som innehåller typerna.</span><span class="sxs-lookup"><span data-stu-id="b58cf-262">Specifies the path to source code files or assembly DLL files that contain the types.</span></span>

<span data-ttu-id="b58cf-263">Om du skickar källfiler `Add-Type` kompilerar koden i filerna och skapar en minnes intern sammansättning av typerna.</span><span class="sxs-lookup"><span data-stu-id="b58cf-263">If you submit source code files, `Add-Type` compiles the code in the files and creates an in-memory assembly of the types.</span></span> <span data-ttu-id="b58cf-264">Fil namns tillägget som anges i **Path** -värdet avgör vilken kompilator som `Add-Type` använder.</span><span class="sxs-lookup"><span data-stu-id="b58cf-264">The file name extension specified in the value of **Path** determines the compiler that `Add-Type` uses.</span></span>

<span data-ttu-id="b58cf-265">Om du skickar en sammansättnings fil, `Add-Type` tar de olika typerna från sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-265">If you submit an assembly file, `Add-Type` takes the types from the assembly.</span></span> <span data-ttu-id="b58cf-266">Om du vill ange en minnes intern sammansättning eller Global Assembly Cache använder du parametern **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="b58cf-266">To specify an in-memory assembly or the global assembly cache, use the **AssemblyName** parameter.</span></span>

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

### <span data-ttu-id="b58cf-267">-ReferencedAssemblies</span><span class="sxs-lookup"><span data-stu-id="b58cf-267">-ReferencedAssemblies</span></span>

<span data-ttu-id="b58cf-268">Anger de sammansättningar som typen är beroende av.</span><span class="sxs-lookup"><span data-stu-id="b58cf-268">Specifies the assemblies upon which the type depends.</span></span> <span data-ttu-id="b58cf-269">Som standard `Add-Type` refererar `System.dll` och `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="b58cf-269">By default, `Add-Type` references `System.dll` and `System.Management.Automation.dll`.</span></span> <span data-ttu-id="b58cf-270">De sammansättningar som du anger med hjälp av den här parametern refereras till utöver standard sammansättningarna.</span><span class="sxs-lookup"><span data-stu-id="b58cf-270">The assemblies that you specify by using this parameter are referenced in addition to the default assemblies.</span></span>

<span data-ttu-id="b58cf-271">Du kan inte använda parametrarna **CompilerParameters** och **ReferencedAssemblies** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="b58cf-271">You can't use the **CompilerParameters** and **ReferencedAssemblies** parameters in the same command.</span></span>

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

### <span data-ttu-id="b58cf-272">-TypeDefinition</span><span class="sxs-lookup"><span data-stu-id="b58cf-272">-TypeDefinition</span></span>

<span data-ttu-id="b58cf-273">Anger den käll kod som innehåller typ definitionerna.</span><span class="sxs-lookup"><span data-stu-id="b58cf-273">Specifies the source code that contains the type definitions.</span></span> <span data-ttu-id="b58cf-274">Ange käll koden i en sträng eller här – sträng, eller ange en variabel som innehåller käll koden.</span><span class="sxs-lookup"><span data-stu-id="b58cf-274">Enter the source code in a string or here-string, or enter a variable that contains the source code.</span></span> <span data-ttu-id="b58cf-275">Mer information om här – strängar finns [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="b58cf-275">For more information about here-strings, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span></span>

<span data-ttu-id="b58cf-276">Ta med en namn områdes deklaration i din typ definition.</span><span class="sxs-lookup"><span data-stu-id="b58cf-276">Include a namespace declaration in your type definition.</span></span> <span data-ttu-id="b58cf-277">Om du utelämnar namn områdes deklarationen kan typen ha samma namn som en annan typ eller genvägen till en annan typ, vilket orsakar en oavsiktlig överskrivning.</span><span class="sxs-lookup"><span data-stu-id="b58cf-277">If you omit the namespace declaration, your type might have the same name as another type or the shortcut for another type, causing an unintentional overwrite.</span></span> <span data-ttu-id="b58cf-278">Om du till exempel definierar en typ som heter **Exception** , kommer skript som använder **undantag** som genväg för **system. Exception** inte att fungera.</span><span class="sxs-lookup"><span data-stu-id="b58cf-278">For example, if you define a type called **Exception** , scripts that use **Exception** as the shortcut for **System.Exception** will fail.</span></span>

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

### <span data-ttu-id="b58cf-279">-UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="b58cf-279">-UsingNamespace</span></span>

<span data-ttu-id="b58cf-280">Anger andra namn områden som krävs för klassen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-280">Specifies other namespaces that are required for the class.</span></span> <span data-ttu-id="b58cf-281">Detta är ungefär som nyckelordet C#, `Using` .</span><span class="sxs-lookup"><span data-stu-id="b58cf-281">This is much like the C# keyword, `Using`.</span></span>

<span data-ttu-id="b58cf-282">Som standard `Add-Type` refererar **system** namn området.</span><span class="sxs-lookup"><span data-stu-id="b58cf-282">By default, `Add-Type` references the **System** namespace.</span></span> <span data-ttu-id="b58cf-283">När parametern **MemberDefinition** används `Add-Type` refererar även namn området **system. Runtime. InteropServices** som standard.</span><span class="sxs-lookup"><span data-stu-id="b58cf-283">When the **MemberDefinition** parameter is used, `Add-Type` also references the **System.Runtime.InteropServices** namespace by default.</span></span> <span data-ttu-id="b58cf-284">De namn områden som du lägger till med hjälp av parametern **UsingNamespace** refereras till utöver standard namn områdena.</span><span class="sxs-lookup"><span data-stu-id="b58cf-284">The namespaces that you add by using the **UsingNamespace** parameter are referenced in addition to the default namespaces.</span></span>

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

### <span data-ttu-id="b58cf-285">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b58cf-285">CommonParameters</span></span>

<span data-ttu-id="b58cf-286">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b58cf-286">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b58cf-287">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b58cf-287">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b58cf-288">INDATA</span><span class="sxs-lookup"><span data-stu-id="b58cf-288">INPUTS</span></span>

### <span data-ttu-id="b58cf-289">Inget</span><span class="sxs-lookup"><span data-stu-id="b58cf-289">None</span></span>

<span data-ttu-id="b58cf-290">Du kan inte skicka objekt nedåt i pipelinen till `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="b58cf-290">You can't send objects down the pipeline to `Add-Type`.</span></span>

## <span data-ttu-id="b58cf-291">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b58cf-291">OUTPUTS</span></span>

### <span data-ttu-id="b58cf-292">Ingen eller system. Type</span><span class="sxs-lookup"><span data-stu-id="b58cf-292">None or System.Type</span></span>

<span data-ttu-id="b58cf-293">När du använder parametern **Passthru** `Add-Type` returneras ett **system. Type** -objekt som representerar den nya typen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-293">When you use the **PassThru** parameter, `Add-Type` returns a **System.Type** object that represents the new type.</span></span> <span data-ttu-id="b58cf-294">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b58cf-294">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="b58cf-295">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b58cf-295">NOTES</span></span>

<span data-ttu-id="b58cf-296">De typer som du lägger till finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="b58cf-296">The types that you add exist only in the current session.</span></span> <span data-ttu-id="b58cf-297">Om du vill använda typerna i alla sessioner lägger du till dem i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="b58cf-297">To use the types in all sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="b58cf-298">Mer information om profilen finns [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b58cf-298">For more information about the profile, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="b58cf-299">Typ namn och namn områden måste vara unika inom en session.</span><span class="sxs-lookup"><span data-stu-id="b58cf-299">Type names and namespaces must be unique within a session.</span></span> <span data-ttu-id="b58cf-300">Du kan inte ta bort en typ eller ändra den.</span><span class="sxs-lookup"><span data-stu-id="b58cf-300">You can't unload a type or change it.</span></span> <span data-ttu-id="b58cf-301">Om du behöver ändra koden för en typ måste du ändra namnet eller starta en ny PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="b58cf-301">If you need to change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="b58cf-302">Annars Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="b58cf-302">Otherwise, the command fails.</span></span>

<span data-ttu-id="b58cf-303">**CodeDomProvider** -klassen för vissa språk, till exempel ironpython och J#, genererar inte utdata.</span><span class="sxs-lookup"><span data-stu-id="b58cf-303">The **CodeDomProvider** class for some languages, such as IronPython and J#, doesn't generate output.</span></span> <span data-ttu-id="b58cf-304">Därför kan typer som skrivits på dessa språk inte användas med `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="b58cf-304">As a result, types written in these languages can't be used with `Add-Type`.</span></span>

<span data-ttu-id="b58cf-305">Denna cmdlet baseras på Microsoft .NET Framework CodeDomProvider- [klass](/dotnet/api/system.codedom.compiler.codedomprovider).</span><span class="sxs-lookup"><span data-stu-id="b58cf-305">This cmdlet is based on the Microsoft .NET Framework [CodeDomProvider Class](/dotnet/api/system.codedom.compiler.codedomprovider).</span></span>

## <span data-ttu-id="b58cf-306">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b58cf-306">RELATED LINKS</span></span>

[<span data-ttu-id="b58cf-307">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="b58cf-307">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_profiles.md)

[<span data-ttu-id="b58cf-308">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="b58cf-308">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="b58cf-309">Lägg till medlem</span><span class="sxs-lookup"><span data-stu-id="b58cf-309">Add-Member</span></span>](Add-Member.md)

[<span data-ttu-id="b58cf-310">Nytt – objekt</span><span class="sxs-lookup"><span data-stu-id="b58cf-310">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="b58cf-311">OutputAssemblyType</span><span class="sxs-lookup"><span data-stu-id="b58cf-311">OutputAssemblyType</span></span>](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[<span data-ttu-id="b58cf-312">Plattforms anrop (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="b58cf-312">Platform Invoke (P/Invoke)</span></span>](/dotnet/standard/native-interop/pinvoke)

[<span data-ttu-id="b58cf-313">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="b58cf-313">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
