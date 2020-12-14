---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Object
ms.openlocfilehash: 3b2db400c5a8a1c61ec30ecee07f91d29b5eb3c1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710795"
---
# <span data-ttu-id="f86d2-102">New-Object</span><span class="sxs-lookup"><span data-stu-id="f86d2-102">New-Object</span></span>

## <span data-ttu-id="f86d2-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f86d2-103">SYNOPSIS</span></span>
<span data-ttu-id="f86d2-104">Skapar en instans av ett Microsoft .NET Framework-eller COM-objekt.</span><span class="sxs-lookup"><span data-stu-id="f86d2-104">Creates an instance of a Microsoft .NET Framework or COM object.</span></span>

## <span data-ttu-id="f86d2-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f86d2-105">SYNTAX</span></span>

### <span data-ttu-id="f86d2-106">NET (standard)</span><span class="sxs-lookup"><span data-stu-id="f86d2-106">Net (Default)</span></span>

```
New-Object [-TypeName] <String> [[-ArgumentList] <Object[]>] [-Property <IDictionary>] [<CommonParameters>]
```

### <span data-ttu-id="f86d2-107">Com</span><span class="sxs-lookup"><span data-stu-id="f86d2-107">Com</span></span>

```
New-Object [-ComObject] <String> [-Strict] [-Property <IDictionary>] [<CommonParameters>]
```

## <span data-ttu-id="f86d2-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f86d2-108">DESCRIPTION</span></span>

<span data-ttu-id="f86d2-109">`New-Object`Cmdleten skapar en instans av ett .NET Framework-eller COM-objekt.</span><span class="sxs-lookup"><span data-stu-id="f86d2-109">The `New-Object` cmdlet creates an instance of a .NET Framework or COM object.</span></span>

<span data-ttu-id="f86d2-110">Du kan ange antingen typen av en .NET Framework klass eller ett ProgID för ett COM-objekt.</span><span class="sxs-lookup"><span data-stu-id="f86d2-110">You can specify either the type of a .NET Framework class or a ProgID of a COM object.</span></span> <span data-ttu-id="f86d2-111">Som standard skriver du det fullständigt kvalificerade namnet för en .NET Framework-klass och cmdleten returnerar en referens till en instans av klassen.</span><span class="sxs-lookup"><span data-stu-id="f86d2-111">By default, you type the fully qualified name of a .NET Framework class and the cmdlet returns a reference to an instance of that class.</span></span> <span data-ttu-id="f86d2-112">Om du vill skapa en instans av ett COM-objekt använder du parametern **ComObject** och anger objektets ProgID som värde.</span><span class="sxs-lookup"><span data-stu-id="f86d2-112">To create an instance of a COM object, use the **ComObject** parameter and specify the ProgID of the object as its value.</span></span>

## <span data-ttu-id="f86d2-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f86d2-113">EXAMPLES</span></span>

### <span data-ttu-id="f86d2-114">Exempel 1: skapa ett system. version-objekt</span><span class="sxs-lookup"><span data-stu-id="f86d2-114">Example 1: Create a System.Version object</span></span>

<span data-ttu-id="f86d2-115">I det här exemplet skapas ett **system. version** -objekt med hjälp av "1.2.3.4"-strängen som konstruktorn.</span><span class="sxs-lookup"><span data-stu-id="f86d2-115">This example creates a **System.Version** object using the "1.2.3.4" string as the constructor.</span></span>

```powershell
New-Object -TypeName System.Version -ArgumentList "1.2.3.4"
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
1      2      3      4
```

### <span data-ttu-id="f86d2-116">Exempel 2: skapa ett Internet Explorer COM-objekt</span><span class="sxs-lookup"><span data-stu-id="f86d2-116">Example 2: Create an Internet Explorer COM object</span></span>

<span data-ttu-id="f86d2-117">I det här exemplet skapas två instanser av COM-objektet som representerar Internet Explorer-programmet.</span><span class="sxs-lookup"><span data-stu-id="f86d2-117">This example creates two instances of the COM object that represents the Internet Explorer application.</span></span> <span data-ttu-id="f86d2-118">Den första instansen använder hash-tabellen för **egenskaps** parametern för att anropa **Navigate2** -metoden och ange egenskapen **Visible** för objektet för `$True` att göra programmet synligt.</span><span class="sxs-lookup"><span data-stu-id="f86d2-118">The first instance uses the **Property** parameter hash table to call the **Navigate2** method and set the **Visible** property of the object to `$True` to make the application visible.</span></span>
<span data-ttu-id="f86d2-119">Den andra instansen får samma resultat med enskilda kommandon.</span><span class="sxs-lookup"><span data-stu-id="f86d2-119">The second instance gets the same results with individual commands.</span></span>

```powershell
$IE1 = New-Object -COMObject InternetExplorer.Application -Property @{Navigate2="www.microsoft.com"; Visible = $True}

# The following command gets the same results as the example above.
$IE2 = New-Object -COMObject InternetExplorer.Application`
$IE2.Navigate2("www.microsoft.com")`
$IE2.Visible = $True`
```

### <span data-ttu-id="f86d2-120">Exempel 3: Använd den strikta parametern för att generera ett icke-avslutande fel</span><span class="sxs-lookup"><span data-stu-id="f86d2-120">Example 3: Use the Strict parameter to generate a non-terminating error</span></span>

<span data-ttu-id="f86d2-121">Det här exemplet visar att om du lägger till en **strikt** parameter `New-Object` genererar cmdleten ett icke-avslutande fel när com-objektet använder en interop-sammansättning.</span><span class="sxs-lookup"><span data-stu-id="f86d2-121">This example demonstrates that adding the **Strict** parameter causes the `New-Object` cmdlet to generate a non-terminating error when the COM object uses an interop assembly.</span></span>

```powershell
$A = New-Object -COMObject Word.Application -Strict -Property @{Visible = $True}
```

```Output
New-Object : The object written to the pipeline is an instance of the type
"Microsoft.Office.Interop.Word.ApplicationClass" from the component's primary interop assembly. If
this type exposes different members than the IDispatch members, scripts written to work with this
object might not work if the primary interop assembly is not installed.

At line:1 char:14
+ $A = New-Object  <<<< -COM Word.Application -Strict; $a.visible=$true
```

### <span data-ttu-id="f86d2-122">Exempel 4: skapa ett COM-objekt för att hantera Windows-skrivbordet</span><span class="sxs-lookup"><span data-stu-id="f86d2-122">Example 4: Create a COM object to manage Windows desktop</span></span>

<span data-ttu-id="f86d2-123">Det här exemplet visar hur du skapar och använder ett COM-objekt för att hantera Windows-skrivbordet.</span><span class="sxs-lookup"><span data-stu-id="f86d2-123">This example shows how to create and use a COM object to manage your Windows desktop.</span></span>

<span data-ttu-id="f86d2-124">Det första kommandot använder **ComObject** -parametern för `New-Object` cmdleten för att skapa ett com-objekt med **Shell. Application** ProgID.</span><span class="sxs-lookup"><span data-stu-id="f86d2-124">The first command uses the **ComObject** parameter of the `New-Object` cmdlet to create a COM object with the **Shell.Application** ProgID.</span></span> <span data-ttu-id="f86d2-125">Det lagrar det resulterande objektet i `$ObjShell` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f86d2-125">It stores the resulting object in the `$ObjShell` variable.</span></span> <span data-ttu-id="f86d2-126">Det andra kommandot rör `$ObjShell` variabeln till `Get-Member` cmdleten, som visar egenskaper och metoder för com-objektet.</span><span class="sxs-lookup"><span data-stu-id="f86d2-126">The second command pipes the `$ObjShell` variable to the `Get-Member` cmdlet, which displays the properties and methods of the COM object.</span></span> <span data-ttu-id="f86d2-127">Metoden **ToggleDesktop** är mellan metoderna.</span><span class="sxs-lookup"><span data-stu-id="f86d2-127">Among the methods is the **ToggleDesktop** method.</span></span> <span data-ttu-id="f86d2-128">Det tredje kommandot anropar **ToggleDesktop** -metoden för objektet för att minimera öppna fönster på Skriv bordet.</span><span class="sxs-lookup"><span data-stu-id="f86d2-128">The third command calls the **ToggleDesktop** method of the object to minimize the open windows on your desktop.</span></span>

```powershell
$Objshell = New-Object -COMObject "Shell.Application"
$objshell | Get-Member
$objshell.ToggleDesktop()
```

```Output
   TypeName: System.__ComObject#{866738b9-6cf2-4de8-8767-f794ebe74f4e}

Name                 MemberType Definition
----                 ---------- ----------
AddToRecent          Method     void AddToRecent (Variant, string)
BrowseForFolder      Method     Folder BrowseForFolder (int, string, int, Variant)
CanStartStopService  Method     Variant CanStartStopService (string)
CascadeWindows       Method     void CascadeWindows ()
ControlPanelItem     Method     void ControlPanelItem (string)
EjectPC              Method     void EjectPC ()
Explore              Method     void Explore (Variant)
ExplorerPolicy       Method     Variant ExplorerPolicy (string)
FileRun              Method     void FileRun ()
FindComputer         Method     void FindComputer ()
FindFiles            Method     void FindFiles ()
FindPrinter          Method     void FindPrinter (string, string, string)
GetSetting           Method     bool GetSetting (int)
GetSystemInformation Method     Variant GetSystemInformation (string)
Help                 Method     void Help ()
IsRestricted         Method     int IsRestricted (string, string)
IsServiceRunning     Method     Variant IsServiceRunning (string)
MinimizeAll          Method     void MinimizeAll ()
NameSpace            Method     Folder NameSpace (Variant)
Open                 Method     void Open (Variant)
RefreshMenu          Method     void RefreshMenu ()
ServiceStart         Method     Variant ServiceStart (string, Variant)
ServiceStop          Method     Variant ServiceStop (string, Variant)
SetTime              Method     void SetTime ()
ShellExecute         Method     void ShellExecute (string, Variant, Variant, Variant, Variant)
ShowBrowserBar       Method     Variant ShowBrowserBar (string, Variant)
ShutdownWindows      Method     void ShutdownWindows ()
Suspend              Method     void Suspend ()
TileHorizontally     Method     void TileHorizontally ()
TileVertically       Method     void TileVertically ()
ToggleDesktop        Method     void ToggleDesktop ()
TrayProperties       Method     void TrayProperties ()
UndoMinimizeALL      Method     void UndoMinimizeALL ()
Windows              Method     IDispatch Windows ()
WindowsSecurity      Method     void WindowsSecurity ()
WindowSwitcher       Method     void WindowSwitcher ()
Application          Property   IDispatch Application () {get}
Parent               Property   IDispatch Parent () {get}
```

### <span data-ttu-id="f86d2-129">Exempel 5: skicka flera argument till en konstruktor</span><span class="sxs-lookup"><span data-stu-id="f86d2-129">Example 5: Pass multiple arguments to a constructor</span></span>

<span data-ttu-id="f86d2-130">Det här exemplet visar hur du skapar ett objekt med en konstruktor som tar flera parametrar.</span><span class="sxs-lookup"><span data-stu-id="f86d2-130">This example shows how to create an object with a constructor that takes multiple parameters.</span></span> <span data-ttu-id="f86d2-131">Parametrarna måste placeras i en matris när parametern **argument List** används.</span><span class="sxs-lookup"><span data-stu-id="f86d2-131">The parameters must be put in an array when using **ArgumentList** parameter.</span></span>

```powershell
$array = @('One', 'Two', 'Three')
$parameters = @{
    TypeName = 'System.Collections.Generic.HashSet[string]'
    ArgumentList = ([string[]]$array, [System.StringComparer]::OrdinalIgnoreCase)
}
$set = New-Object @parameters
```

<span data-ttu-id="f86d2-132">PowerShell binder varje medlem i matrisen till en parameter i konstruktorn.</span><span class="sxs-lookup"><span data-stu-id="f86d2-132">PowerShell binds each member of the array to a parameter of the constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="f86d2-133">I det här exemplet används parametern ihopbuntning för läsbarhet.</span><span class="sxs-lookup"><span data-stu-id="f86d2-133">This example uses parameter splatting for readability.</span></span> <span data-ttu-id="f86d2-134">Mer information finns i [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="f86d2-134">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

### <span data-ttu-id="f86d2-135">Exempel 6: anropa en konstruktor som tar en matris som en enda parameter</span><span class="sxs-lookup"><span data-stu-id="f86d2-135">Example 6: Calling a constructor that takes an array as a single parameter</span></span>

<span data-ttu-id="f86d2-136">Det här exemplet visar hur du skapar ett objekt med en konstruktor som tar en parameter som är en matris eller samling.</span><span class="sxs-lookup"><span data-stu-id="f86d2-136">This example shows how to create an object with a constructor that takes a parameter that is an array or collection.</span></span> <span data-ttu-id="f86d2-137">Mat ris parametern måste placeras i en omsluten rad inuti en annan matris.</span><span class="sxs-lookup"><span data-stu-id="f86d2-137">The array parameter must be put in wrapped inside another array.</span></span>

```powershell
$array = @('One', 'Two', 'Three')
# This command throws an exception.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList $array
# This command succeeds.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList (,[string[]]$array)
$set
```

```Output
New-Object : Cannot find an overload for "HashSet`1" and the argument count: "3".
At line:1 char:8
+ $set = New-Object -TypeName 'System.Collections.Generic.HashSet[strin ...
+        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidOperation: (:) [New-Object], MethodException
+ FullyQualifiedErrorId : ConstructorInvokedThrowException,Microsoft.PowerShell.Commands.NewObjectCommand

One
Two
Three
```

<span data-ttu-id="f86d2-138">Det första försöket att skapa objektet i det här exemplet misslyckades.</span><span class="sxs-lookup"><span data-stu-id="f86d2-138">The first attempt to create the object in this example fails.</span></span> <span data-ttu-id="f86d2-139">PowerShell försökte binda de tre medlemmarna av till- `$array` parametrarna för konstruktorn, men konstruktorn tar inte tre parametrar.</span><span class="sxs-lookup"><span data-stu-id="f86d2-139">PowerShell attempted to bind the three members of `$array` to parameters of the constructor but the constructor does not take three parameter.</span></span> <span data-ttu-id="f86d2-140">`$array`Genom att figursätta i en annan matris förhindrar du att PowerShell försöker binda de tre medlemmarna av `$array` till-parametrarna för konstruktorn.</span><span class="sxs-lookup"><span data-stu-id="f86d2-140">Wrapping `$array` in another array prevents PowerShell from attempting to bind the three members of `$array` to parameters of the constructor.</span></span>

## <span data-ttu-id="f86d2-141">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f86d2-141">PARAMETERS</span></span>

### <span data-ttu-id="f86d2-142">– Argument List</span><span class="sxs-lookup"><span data-stu-id="f86d2-142">-ArgumentList</span></span>

<span data-ttu-id="f86d2-143">Anger en matris med argument som ska skickas till konstruktorn för klassen .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f86d2-143">Specifies an array of arguments to pass to the constructor of the .NET Framework class.</span></span> <span data-ttu-id="f86d2-144">Om konstruktorn använder en enda parameter som är en matris måste du figursätta den parametern inuti en annan matris.</span><span class="sxs-lookup"><span data-stu-id="f86d2-144">If the constructor takes a single parameter that is an array, you must wrap that parameter inside another array.</span></span> <span data-ttu-id="f86d2-145">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f86d2-145">For example:</span></span>

`$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate -ArgumentList (,$bytes)`

<span data-ttu-id="f86d2-146">Mer information om beteendet för **argument List** finns [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="f86d2-146">For more information about the behavior of **ArgumentList**, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="f86d2-147">Aliaset för **argument List** är **argument**.</span><span class="sxs-lookup"><span data-stu-id="f86d2-147">The alias for **ArgumentList** is **Args**.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: Net
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f86d2-148">-ComObject</span><span class="sxs-lookup"><span data-stu-id="f86d2-148">-ComObject</span></span>

<span data-ttu-id="f86d2-149">Anger program-ID: n (ProgID) för COM-objektet.</span><span class="sxs-lookup"><span data-stu-id="f86d2-149">Specifies the programmatic identifier (ProgID) of the COM object.</span></span>

```yaml
Type: System.String
Parameter Sets: Com
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f86d2-150">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="f86d2-150">-Property</span></span>

<span data-ttu-id="f86d2-151">Anger egenskaps värden och anropar metoder för det nya objektet.</span><span class="sxs-lookup"><span data-stu-id="f86d2-151">Sets property values and invokes methods of the new object.</span></span>

<span data-ttu-id="f86d2-152">Ange en hash-tabell där nycklarna är namnen på egenskaper eller metoder och värdena är egenskaps värden eller metod argument.</span><span class="sxs-lookup"><span data-stu-id="f86d2-152">Enter a hash table in which the keys are the names of properties or methods and the values are property values or method arguments.</span></span> <span data-ttu-id="f86d2-153">`New-Object` skapar objektet och anger varje egenskaps värde och anropar varje metod i den ordning som de visas i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="f86d2-153">`New-Object` creates the object and sets each property value and invokes each method in the order that they appear in the hash table.</span></span>

<span data-ttu-id="f86d2-154">Om det nya objektet härleds från **PSObject** -klassen och du anger en egenskap som inte finns på objektet, `New-Object` lägger till den angivna egenskapen i objektet som en NoteProperty.</span><span class="sxs-lookup"><span data-stu-id="f86d2-154">If the new object is derived from the **PSObject** class, and you specify a property that does not exist on the object, `New-Object` adds the specified property to the object as a NoteProperty.</span></span> <span data-ttu-id="f86d2-155">Om objektet inte är ett **PSObject** genererar kommandot ett icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="f86d2-155">If the object is not a **PSObject**, the command generates a non-terminating error.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f86d2-156">– Strikt</span><span class="sxs-lookup"><span data-stu-id="f86d2-156">-Strict</span></span>

<span data-ttu-id="f86d2-157">Anger att cmdleten genererar ett icke-avslutande fel när ett COM-objekt som du försöker skapa använder en interop-sammansättning.</span><span class="sxs-lookup"><span data-stu-id="f86d2-157">Indicates that the cmdlet generates a non-terminating error when a COM object that you attempt to create uses an interop assembly.</span></span> <span data-ttu-id="f86d2-158">Den här funktionen särskiljer faktiska COM-objekt från .NET Framework objekt med COM-anropade omslutningar.</span><span class="sxs-lookup"><span data-stu-id="f86d2-158">This feature distinguishes actual COM objects from .NET Framework objects with COM-callable wrappers.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Com
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f86d2-159">-TypeName</span><span class="sxs-lookup"><span data-stu-id="f86d2-159">-TypeName</span></span>

<span data-ttu-id="f86d2-160">Anger det fullständigt kvalificerade namnet på .NET Framework-klassen.</span><span class="sxs-lookup"><span data-stu-id="f86d2-160">Specifies the fully qualified name of the .NET Framework class.</span></span> <span data-ttu-id="f86d2-161">Du kan inte ange både parametern **TypeName** och parametern **ComObject** .</span><span class="sxs-lookup"><span data-stu-id="f86d2-161">You cannot specify both the **TypeName** parameter and the **ComObject** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: Net
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f86d2-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f86d2-162">CommonParameters</span></span>

<span data-ttu-id="f86d2-163">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f86d2-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f86d2-164">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f86d2-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f86d2-165">INDATA</span><span class="sxs-lookup"><span data-stu-id="f86d2-165">INPUTS</span></span>

### <span data-ttu-id="f86d2-166">Inga</span><span class="sxs-lookup"><span data-stu-id="f86d2-166">None</span></span>

<span data-ttu-id="f86d2-167">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f86d2-167">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="f86d2-168">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f86d2-168">OUTPUTS</span></span>

### <span data-ttu-id="f86d2-169">Objekt</span><span class="sxs-lookup"><span data-stu-id="f86d2-169">Object</span></span>

<span data-ttu-id="f86d2-170">`New-Object` Returnerar det objekt som har skapats.</span><span class="sxs-lookup"><span data-stu-id="f86d2-170">`New-Object` returns the object that is created.</span></span>

## <span data-ttu-id="f86d2-171">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f86d2-171">NOTES</span></span>

- <span data-ttu-id="f86d2-172">`New-Object` innehåller de vanligaste funktionerna i funktionen VBScript CreateObject.</span><span class="sxs-lookup"><span data-stu-id="f86d2-172">`New-Object` provides the most commonly-used functionality of the VBScript CreateObject function.</span></span> <span data-ttu-id="f86d2-173">En instruktion som `Set objShell = CreateObject("Shell.Application")` i VBScript kan översättas till `$objShell = New-Object -COMObject "Shell.Application"` i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f86d2-173">A statement like `Set objShell = CreateObject("Shell.Application")` in VBScript can be translated to `$objShell = New-Object -COMObject "Shell.Application"` in PowerShell.</span></span>
- <span data-ttu-id="f86d2-174">`New-Object` expanderar på de funktioner som är tillgängliga i Windows Script Host-miljön genom att göra det enkelt att arbeta med .NET Framework objekt från kommando raden och inom skript.</span><span class="sxs-lookup"><span data-stu-id="f86d2-174">`New-Object` expands upon the functionality available in the Windows Script Host environment by making it easy to work with .NET Framework objects from the command line and within scripts.</span></span>

## <span data-ttu-id="f86d2-175">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f86d2-175">RELATED LINKS</span></span>

[<span data-ttu-id="f86d2-176">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="f86d2-176">about_Object_Creation</span></span>](../Microsoft.PowerShell.Core/About/about_Object_Creation.md)

[<span data-ttu-id="f86d2-177">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="f86d2-177">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="f86d2-178">Gruppera objekt</span><span class="sxs-lookup"><span data-stu-id="f86d2-178">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="f86d2-179">Mått – objekt</span><span class="sxs-lookup"><span data-stu-id="f86d2-179">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="f86d2-180">Select-Object</span><span class="sxs-lookup"><span data-stu-id="f86d2-180">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="f86d2-181">Sortera objekt</span><span class="sxs-lookup"><span data-stu-id="f86d2-181">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="f86d2-182">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="f86d2-182">Tee-Object</span></span>](Tee-Object.md)

