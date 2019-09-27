---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Skapa .NET-och COM-objekt nytt objekt
ms.openlocfilehash: 6e98a159451bc7da4ba3b37eaeb813eb71590d2b
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325174"
---
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="403de-103">Skapa .NET-och COM-objekt (nytt-objekt)</span><span class="sxs-lookup"><span data-stu-id="403de-103">Creating .NET and COM Objects (New-Object)</span></span>

<span data-ttu-id="403de-104">Det finns program komponenter med .NET Framework-och COM-gränssnitt som gör att du kan utföra många system administrations uppgifter.</span><span class="sxs-lookup"><span data-stu-id="403de-104">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="403de-105">Med Windows PowerShell kan du använda dessa komponenter, så du är inte begränsad till de uppgifter som kan utföras med hjälp av cmdletar.</span><span class="sxs-lookup"><span data-stu-id="403de-105">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="403de-106">Många av cmdletarna i den första versionen av Windows PowerShell fungerar inte mot fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="403de-106">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="403de-107">Vi visar hur du kommer runt den här begränsningen när du hanterar händelse loggar med hjälp av klassen .NET Framework **system. Diagnostics. EventLog** direkt från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="403de-107">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

## <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="403de-108">Använda nytt-objekt för händelse logg åtkomst</span><span class="sxs-lookup"><span data-stu-id="403de-108">Using New-Object for Event Log Access</span></span>

<span data-ttu-id="403de-109">.NET Framework klass biblioteket innehåller en klass med namnet **system. Diagnostics. EventLog** som kan användas för att hantera händelse loggar.</span><span class="sxs-lookup"><span data-stu-id="403de-109">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="403de-110">Du kan skapa en ny instans av en .NET Framework-klass med hjälp av cmdleten **New-Object** med parametern **TypeName** .</span><span class="sxs-lookup"><span data-stu-id="403de-110">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="403de-111">Till exempel skapar följande kommando en händelse logg referens:</span><span class="sxs-lookup"><span data-stu-id="403de-111">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="403de-112">Även om kommandot har skapat en instans av klassen EventLog, innehåller instansen inga data.</span><span class="sxs-lookup"><span data-stu-id="403de-112">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="403de-113">Det beror på att vi inte angav någon viss händelse logg.</span><span class="sxs-lookup"><span data-stu-id="403de-113">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="403de-114">Hur får du en verklig händelse logg?</span><span class="sxs-lookup"><span data-stu-id="403de-114">How do you get a real event log?</span></span>

### <a name="using-constructors-with-new-object"></a><span data-ttu-id="403de-115">Använda konstruktorer med New-Object</span><span class="sxs-lookup"><span data-stu-id="403de-115">Using Constructors with New-Object</span></span>

<span data-ttu-id="403de-116">Om du vill referera till en speciell händelse logg måste du ange namnet på loggen.</span><span class="sxs-lookup"><span data-stu-id="403de-116">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="403de-117">**New-Object** har en **argument List** -parameter.</span><span class="sxs-lookup"><span data-stu-id="403de-117">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="403de-118">De argument som du skickar som värden för den här parametern används av en särskild start metod för objektet.</span><span class="sxs-lookup"><span data-stu-id="403de-118">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="403de-119">Metoden kallas en *konstruktor* eftersom den används för att konstruera objektet.</span><span class="sxs-lookup"><span data-stu-id="403de-119">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="403de-120">Om du till exempel vill hämta en referens till program loggen anger du strängen ' Application ' som ett argument:</span><span class="sxs-lookup"><span data-stu-id="403de-120">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="403de-121">Eftersom de flesta .NET Framework Core-klasserna finns i system namn rymden försöker Windows PowerShell automatiskt hitta klasser som du anger i systemets namnrymd om det inte går att hitta en matchning för det TypeName som du anger.</span><span class="sxs-lookup"><span data-stu-id="403de-121">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="403de-122">Det innebär att du kan ange Diagnostics. EventLog i stället för system. Diagnostics. EventLog.</span><span class="sxs-lookup"><span data-stu-id="403de-122">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

### <a name="storing-objects-in-variables"></a><span data-ttu-id="403de-123">Lagra objekt i variabler</span><span class="sxs-lookup"><span data-stu-id="403de-123">Storing Objects in Variables</span></span>

<span data-ttu-id="403de-124">Du kanske vill lagra en referens till ett objekt, så att du kan använda den i det aktuella gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="403de-124">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="403de-125">Även om Windows PowerShell gör det möjligt att göra mycket arbete med pipelines, vilket minskar behovet av variabler, och ibland lagra referenser till objekt i variabler, gör det mer praktiskt att ändra dessa objekt.</span><span class="sxs-lookup"><span data-stu-id="403de-125">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="403de-126">Med Windows PowerShell kan du skapa variabler som är huvudsakligen namngivna objekt.</span><span class="sxs-lookup"><span data-stu-id="403de-126">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="403de-127">Utdata från alla giltiga Windows PowerShell-kommandon kan lagras i en variabel.</span><span class="sxs-lookup"><span data-stu-id="403de-127">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="403de-128">Variabel namn börjar alltid med $.</span><span class="sxs-lookup"><span data-stu-id="403de-128">Variable names always begin with $.</span></span> <span data-ttu-id="403de-129">Om du vill lagra program logg referensen i en variabel med namnet $AppLog, skriver du namnet på variabeln följt av ett likhets tecken och skriver sedan kommandot som används för att skapa programloggs objekt:</span><span class="sxs-lookup"><span data-stu-id="403de-129">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="403de-130">Om du sedan skriver $AppLog kan du se att den innehåller program loggen:</span><span class="sxs-lookup"><span data-stu-id="403de-130">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="403de-131">Åtkomst till en fjärran sluten händelse logg med New-Object</span><span class="sxs-lookup"><span data-stu-id="403de-131">Accessing a Remote Event Log with New-Object</span></span>

<span data-ttu-id="403de-132">Kommandona som används i föregående avsnitt riktar sig till den lokala datorn. cmdleten **Get-EventLog** kan göra det.</span><span class="sxs-lookup"><span data-stu-id="403de-132">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="403de-133">För att få åtkomst till program loggen på en fjärrdator måste du ange både logg namnet och ett dator namn (eller en IP-adress) som argument.</span><span class="sxs-lookup"><span data-stu-id="403de-133">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="403de-134">Nu när vi har en referens till en händelse logg som lagras i variabeln $RemoteAppLog, vilka uppgifter kan vi utföra på den?</span><span class="sxs-lookup"><span data-stu-id="403de-134">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="403de-135">Rensa en händelse logg med objekt metoder</span><span class="sxs-lookup"><span data-stu-id="403de-135">Clearing an Event Log with Object Methods</span></span>

<span data-ttu-id="403de-136">Objekt har ofta metoder som kan anropas för att utföra uppgifter.</span><span class="sxs-lookup"><span data-stu-id="403de-136">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="403de-137">Du kan använda **Get-Member** för att visa de metoder som är associerade med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="403de-137">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="403de-138">Följande kommando och valda utdata visar några metoder i klassen EventLog:</span><span class="sxs-lookup"><span data-stu-id="403de-138">The following command and selected output show some the methods of the EventLog class:</span></span>

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

<span data-ttu-id="403de-139">Metoden **Clear ()** kan användas för att rensa händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="403de-139">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="403de-140">När du anropar en metod måste du alltid följa metod namnet med parenteser, även om metoden inte kräver argument.</span><span class="sxs-lookup"><span data-stu-id="403de-140">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="403de-141">Detta låter Windows PowerShell skilja mellan metoden och en möjlig egenskap med samma namn.</span><span class="sxs-lookup"><span data-stu-id="403de-141">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="403de-142">Skriv följande för att anropa metoden **Clear** :</span><span class="sxs-lookup"><span data-stu-id="403de-142">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="403de-143">Skriv följande för att visa loggen.</span><span class="sxs-lookup"><span data-stu-id="403de-143">Type the following to display the log.</span></span> <span data-ttu-id="403de-144">Du ser att händelse loggen har rensats och har nu 0 poster i stället för 262:</span><span class="sxs-lookup"><span data-stu-id="403de-144">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

## <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="403de-145">Skapa COM-objekt med New-Object</span><span class="sxs-lookup"><span data-stu-id="403de-145">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="403de-146">Du kan använda **nya-objekt** för att arbeta med Component Object Model (com)-komponenter.</span><span class="sxs-lookup"><span data-stu-id="403de-146">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="403de-147">Komponenter sträcker sig från de olika bibliotek som ingår i Windows Script Host (WSH) till ActiveX-program, till exempel Internet Explorer som är installerade på de flesta system.</span><span class="sxs-lookup"><span data-stu-id="403de-147">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="403de-148">**New-Object** använder .NET Framework runtime-anropade omslutningar för att skapa com-objekt, så den har samma begränsningar som .NET Framework gör vid anrop till com-objekt.</span><span class="sxs-lookup"><span data-stu-id="403de-148">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="403de-149">Om du vill skapa ett COM-objekt måste du ange parametern **ComObject** med program-ID eller *ProgID* för den com-klass som du vill använda.</span><span class="sxs-lookup"><span data-stu-id="403de-149">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="403de-150">En fullständig beskrivning av begränsningarna med COM-användning och hur du avgör vilka ProgId som är tillgängliga på ett system ligger utanför den här användarens Användar handbok, men de mest välkända objekten från miljöer som WSH kan användas i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="403de-150">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="403de-151">Du kan skapa WSH-objekt genom att ange följande ProgID: **Wscript. Shell**, **wscript. Network**, **Scripting. Dictionary**och **Scripting. FileSystemObject**.</span><span class="sxs-lookup"><span data-stu-id="403de-151">You can create the WSH objects by specifying these progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span></span> <span data-ttu-id="403de-152">Följande kommandon skapar följande objekt:</span><span class="sxs-lookup"><span data-stu-id="403de-152">The following commands create these objects:</span></span>

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="403de-153">Även om de flesta av funktionerna i dessa klasser görs tillgängliga på andra sätt i Windows PowerShell, är det enklare att skapa några uppgifter som att skapa genvägar med hjälp av WSH-klasser.</span><span class="sxs-lookup"><span data-stu-id="403de-153">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

## <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="403de-154">Skapa en Skriv bords gen väg med WScript. Shell</span><span class="sxs-lookup"><span data-stu-id="403de-154">Creating a Desktop Shortcut with WScript.Shell</span></span>

<span data-ttu-id="403de-155">En uppgift som snabbt kan utföras med ett COM-objekt är att skapa en genväg.</span><span class="sxs-lookup"><span data-stu-id="403de-155">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="403de-156">Anta att du vill skapa en genväg på Skriv bordet som länkar till hem-mappen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="403de-156">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="403de-157">Du måste först skapa en referens till **wscript. Shell**, som vi kommer att lagra i en variabel med namnet **$WshShell**:</span><span class="sxs-lookup"><span data-stu-id="403de-157">You first need to create a reference to **WScript.Shell**, which we will store in a variable named **$WshShell**:</span></span>

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="403de-158">Get-Member fungerar med COM-objekt, så att du kan utforska medlemmar i objektet genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="403de-158">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="403de-159">**Get-Member** har en valfri **InputObject** -parameter som du kan använda i stället för rörledningar för att tillhandahålla inmatade **medlemmar**.</span><span class="sxs-lookup"><span data-stu-id="403de-159">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member**.</span></span> <span data-ttu-id="403de-160">Du får samma utdata som visas ovan om du i stället använde kommandot **Get-Member-InputObject $WshShell**.</span><span class="sxs-lookup"><span data-stu-id="403de-160">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell**.</span></span> <span data-ttu-id="403de-161">Om du använder **InputObject**behandlar den sitt argument som ett enda objekt.</span><span class="sxs-lookup"><span data-stu-id="403de-161">If you use **InputObject**, it treats its argument as a single item.</span></span> <span data-ttu-id="403de-162">Det innebär att om du har flera objekt i en variabel behandlar **Get-Member** dem som en objekt mat ris.</span><span class="sxs-lookup"><span data-stu-id="403de-162">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="403de-163">Exempel:</span><span class="sxs-lookup"><span data-stu-id="403de-163">For example:</span></span>

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="403de-164">Metoden **wscript. Shell CreateShortcut** accepterar ett enda argument, sökvägen till gen vägs filen som ska skapas.</span><span class="sxs-lookup"><span data-stu-id="403de-164">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="403de-165">Vi kan ange den fullständiga sökvägen till Skriv bordet, men det finns ett enklare sätt.</span><span class="sxs-lookup"><span data-stu-id="403de-165">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="403de-166">Skriv bordet representeras vanligt vis av en mapp med namnet Desktop i den aktuella användarens hem mapp.</span><span class="sxs-lookup"><span data-stu-id="403de-166">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="403de-167">Windows PowerShell har en variabel **$Home** som innehåller sökvägen till den här mappen.</span><span class="sxs-lookup"><span data-stu-id="403de-167">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="403de-168">Vi kan ange sökvägen till arbetsmappen med hjälp av den här variabeln och sedan lägga till namnet på mappen Desktop och namnet på genvägen att skapa genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="403de-168">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="403de-169">När du använder något som ser ut som ett variabel namn inuti dubbla citat tecken försöker Windows PowerShell ersätta ett matchande värde.</span><span class="sxs-lookup"><span data-stu-id="403de-169">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="403de-170">Om du använder enkla citat tecken försöker inte det variabla värdet ersättas med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="403de-170">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="403de-171">Försök till exempel att skriva följande kommandon:</span><span class="sxs-lookup"><span data-stu-id="403de-171">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="403de-172">Nu har vi en variabel med namnet **$lnk** som innehåller en ny gen vägs referens.</span><span class="sxs-lookup"><span data-stu-id="403de-172">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="403de-173">Om du vill se dess medlemmar kan du lägga till den för att **bli medlem**.</span><span class="sxs-lookup"><span data-stu-id="403de-173">If you want to see its members, you can pipe it to **Get-Member**.</span></span> <span data-ttu-id="403de-174">I följande utdata visas de medlemmar som vi behöver använda för att slutföra skapandet av vår genväg:</span><span class="sxs-lookup"><span data-stu-id="403de-174">The output below shows the members we need to use to finish creating our shortcut:</span></span>

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

<span data-ttu-id="403de-175">Vi måste ange **TargetPath**, som är programmappen för Windows PowerShell, och sedan spara genvägen **$lnk** genom att anropa metoden **Save** .</span><span class="sxs-lookup"><span data-stu-id="403de-175">We need to specify the **TargetPath**, which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="403de-176">Sökvägen till Windows PowerShell-programmappen lagras i variabeln **$PSHome**, så vi kan göra detta genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="403de-176">The Windows PowerShell application folder path is stored in the variable **$PSHome**, so we can do this by typing:</span></span>

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

## <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="403de-177">Använda Internet Explorer från Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="403de-177">Using Internet Explorer from Windows PowerShell</span></span>

<span data-ttu-id="403de-178">Många program (inklusive Microsoft Office serie program och Internet Explorer) kan automatiseras med hjälp av COM.</span><span class="sxs-lookup"><span data-stu-id="403de-178">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="403de-179">Internet Explorer visar några typiska tekniker och problem som ingår i arbetet med COM-baserade program.</span><span class="sxs-lookup"><span data-stu-id="403de-179">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="403de-180">Du skapar en Internet Explorer-instans genom att ange Internet Explorer ProgId, **InternetExplorer. Application**:</span><span class="sxs-lookup"><span data-stu-id="403de-180">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application**:</span></span>

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="403de-181">Det här kommandot startar Internet Explorer, men gör det inte synligt.</span><span class="sxs-lookup"><span data-stu-id="403de-181">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="403de-182">Om du skriver get-process kan du se att processen som heter iexplore körs.</span><span class="sxs-lookup"><span data-stu-id="403de-182">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="403de-183">I själva verket fortsätter processen att köras om du avslutar Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="403de-183">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="403de-184">Du måste starta om datorn eller använda ett verktyg som aktivitets hanteraren för att avsluta iexplore-processen.</span><span class="sxs-lookup"><span data-stu-id="403de-184">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="403de-185">COM-objekt som startar som separata processer, vanligt vis kallade *ActiveX-körbara filer*, kan visa ett användar gränssnitts fönster när de startar.</span><span class="sxs-lookup"><span data-stu-id="403de-185">COM objects that start as separate processes, commonly called *ActiveX executables*, may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="403de-186">Om de skapar ett fönster men inte gör det synligt, t. ex. Internet Explorer, går fokus i allmänhet till Windows-skrivbordet och du måste göra fönstret synligt för att interagera med det.</span><span class="sxs-lookup"><span data-stu-id="403de-186">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="403de-187">Genom att skriva **$IE | Hämta medlem**kan du Visa egenskaper och metoder för Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="403de-187">By typing **$ie | Get-Member**, you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="403de-188">Om du vill visa Internet Explorer-fönstret anger du egenskapen visible till $true genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="403de-188">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```powershell
$ie.Visible = $true
```

<span data-ttu-id="403de-189">Du kan sedan navigera till en speciell webb adress med hjälp av metoden navigera:</span><span class="sxs-lookup"><span data-stu-id="403de-189">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```powershell
$ie.Navigate("https://devblogs.microsoft.com/scripting/")
```

<span data-ttu-id="403de-190">Med andra medlemmar i Internet Explorer-objektmodellen är det möjligt att hämta text innehåll från webb sidan.</span><span class="sxs-lookup"><span data-stu-id="403de-190">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="403de-191">Följande kommando visar HTML-texten i bröd texten på den aktuella webb sidan:</span><span class="sxs-lookup"><span data-stu-id="403de-191">The following command will display the HTML text in the body of the current Web page:</span></span>

```powershell
$ie.Document.Body.InnerText
```

<span data-ttu-id="403de-192">För att stänga Internet Explorer inifrån PowerShell, anropa metoden quit ():</span><span class="sxs-lookup"><span data-stu-id="403de-192">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```powershell
$ie.Quit()
```

<span data-ttu-id="403de-193">Detta kommer att tvinga den att stängas.</span><span class="sxs-lookup"><span data-stu-id="403de-193">This will force it to close.</span></span> <span data-ttu-id="403de-194">Variabeln $ie inte längre innehåller en giltig referens trots att den fortfarande verkar vara ett COM-objekt.</span><span class="sxs-lookup"><span data-stu-id="403de-194">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="403de-195">Om du försöker använda den får du ett Automation-fel:</span><span class="sxs-lookup"><span data-stu-id="403de-195">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="403de-196">Du kan antingen ta bort den återstående referensen med ett kommando som $ie = $null eller helt ta bort variabeln genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="403de-196">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```powershell
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="403de-197">Det finns ingen gemensam standard för om du avslutar ActiveX-körbara filer eller fortsätter att köra när du tar bort en referens till en.</span><span class="sxs-lookup"><span data-stu-id="403de-197">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="403de-198">Beroende på omständigheterna, till exempel om programmet är synligt, om ett redigerat dokument körs i det och även om Windows PowerShell fortfarande körs, kan det hända att programmet inte avslutas.</span><span class="sxs-lookup"><span data-stu-id="403de-198">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="403de-199">Därför bör du testa avslutnings beteendet för varje ActiveX-fil som du vill använda i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="403de-199">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

## <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="403de-200">Få varningar om .NET Framework-figursatta COM-objekt</span><span class="sxs-lookup"><span data-stu-id="403de-200">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>

<span data-ttu-id="403de-201">I vissa fall kan ett COM-objekt ha en associerad .NET Framework *runtime-anropad wrapper* eller RCW, och detta kommer att användas av **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="403de-201">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object**.</span></span> <span data-ttu-id="403de-202">Eftersom beteendet för RCW kan skilja sig från det normala COM-objektets beteende, har **New-Object** en **strikt** parameter som VARNAr dig om RCW-åtkomst.</span><span class="sxs-lookup"><span data-stu-id="403de-202">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="403de-203">Om du anger en **strikt** parameter och sedan skapar ett com-objekt som använder en RCW, får du ett varnings meddelande:</span><span class="sxs-lookup"><span data-stu-id="403de-203">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

<span data-ttu-id="403de-204">Även om objektet fortfarande har skapats visas en varning om att det inte är ett standard-COM-objekt.</span><span class="sxs-lookup"><span data-stu-id="403de-204">Although the object is still created, you are warned that it is not a standard COM object.</span></span>
