---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Skapa nytt objekt för .NET och COM-objekt"
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: 534e1a9a759d67cfc62ce658a7abddf02f767212
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="58227-103">Skapa .NET och COM-objekt (nya objekt)</span><span class="sxs-lookup"><span data-stu-id="58227-103">Creating .NET and COM Objects (New-Object)</span></span>
<span data-ttu-id="58227-104">Det är programkomponenter med .NET Framework och COM-gränssnitt som gör att du kan utföra administrationsuppgifter för många system.</span><span class="sxs-lookup"><span data-stu-id="58227-104">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="58227-105">Windows PowerShell kan du använda de här komponenterna så att du inte är begränsad till de uppgifter som kan utföras med hjälp av cmdlet: ar.</span><span class="sxs-lookup"><span data-stu-id="58227-105">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="58227-106">Många av cmdletar i den första versionen av Windows PowerShell fungerar inte mot fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="58227-106">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="58227-107">Visar vi hur du komma runt denna begränsning vid hantering av händelseloggar med hjälp av .NET Framework **system.Diagnostics.Eventlog och** klass direkt från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58227-107">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

### <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="58227-108">Med nytt objekt för åtkomst till Loggboken</span><span class="sxs-lookup"><span data-stu-id="58227-108">Using New-Object for Event Log Access</span></span>
<span data-ttu-id="58227-109">.NET Framework-Klassbiblioteket innehåller en klass som heter **system.Diagnostics.Eventlog och** som kan användas för att hantera händelseloggar.</span><span class="sxs-lookup"><span data-stu-id="58227-109">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="58227-110">Du kan skapa en ny instans av en .NET Framework-klass med hjälp av den **New-Object** med den **TypeName** parameter.</span><span class="sxs-lookup"><span data-stu-id="58227-110">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="58227-111">Till exempel skapar följande kommando en referens i händelseloggen:</span><span class="sxs-lookup"><span data-stu-id="58227-111">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="58227-112">Även om kommandot har skapat en instans av klassen EventLog, innehåller instansen inte några data.</span><span class="sxs-lookup"><span data-stu-id="58227-112">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="58227-113">Det beror på att vi inte har angett en viss händelselogg.</span><span class="sxs-lookup"><span data-stu-id="58227-113">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="58227-114">Hur skaffar du en verklig händelselogg</span><span class="sxs-lookup"><span data-stu-id="58227-114">How do you get a real event log?</span></span>

#### <a name="using-constructors-with-new-object"></a><span data-ttu-id="58227-115">Använda konstruktorer med nytt objekt</span><span class="sxs-lookup"><span data-stu-id="58227-115">Using Constructors with New-Object</span></span>
<span data-ttu-id="58227-116">Refererar till en specifik händelselogg, måste du ange namnet på loggen.</span><span class="sxs-lookup"><span data-stu-id="58227-116">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="58227-117">**Nytt objekt** har en **ArgumentList** parameter.</span><span class="sxs-lookup"><span data-stu-id="58227-117">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="58227-118">Argument som du skickar som värden för den här parametern används av en särskild startmetoden för objektet.</span><span class="sxs-lookup"><span data-stu-id="58227-118">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="58227-119">Metoden anropas en *konstruktorn* eftersom den används för att skapa objektet.</span><span class="sxs-lookup"><span data-stu-id="58227-119">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="58227-120">Till exempel för att få en referens till programloggen kan ange du strängen ”program” som ett argument:</span><span class="sxs-lookup"><span data-stu-id="58227-120">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="58227-121">Eftersom de flesta av .NET Framework-kärnklasser finns i namnrymden System, försöker Windows PowerShell automatiskt hitta klasser som du anger i namnrymden System om den inte finns en matchning för typename som du anger.</span><span class="sxs-lookup"><span data-stu-id="58227-121">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="58227-122">Det innebär att du kan ange Diagnostics.EventLog i stället för system.Diagnostics.Eventlog och.</span><span class="sxs-lookup"><span data-stu-id="58227-122">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

#### <a name="storing-objects-in-variables"></a><span data-ttu-id="58227-123">Lagra objekt i variabler</span><span class="sxs-lookup"><span data-stu-id="58227-123">Storing Objects in Variables</span></span>
<span data-ttu-id="58227-124">Du kanske vill lagra en referens till ett objekt så att du kan använda den i den aktuella shell.</span><span class="sxs-lookup"><span data-stu-id="58227-124">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="58227-125">Även om Windows PowerShell kan du göra mycket arbete med pipelines, inskränkning behovet av variabler, gör ibland spara referenser till objekt i variabler det enklare att hantera dessa objekt.</span><span class="sxs-lookup"><span data-stu-id="58227-125">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="58227-126">Windows PowerShell kan du skapa variabler som är i stort sett namngivna objekt.</span><span class="sxs-lookup"><span data-stu-id="58227-126">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="58227-127">Utdata från alla giltiga Windows PowerShell-kommando kan lagras i en variabel.</span><span class="sxs-lookup"><span data-stu-id="58227-127">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="58227-128">Variabelnamn börjar alltid med $.</span><span class="sxs-lookup"><span data-stu-id="58227-128">Variable names always begin with $.</span></span> <span data-ttu-id="58227-129">Om du vill lagra program loggreferens i en variabel med namnet $AppLog, skriver du namnet på variabeln, följt av ett likhetstecken och Skriv det kommando som används för att skapa loggfilen programobjektet:</span><span class="sxs-lookup"><span data-stu-id="58227-129">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="58227-130">Om du anger sedan $AppLog kan se du att den innehåller programloggen:</span><span class="sxs-lookup"><span data-stu-id="58227-130">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="58227-131">Åtkomst till en fjärrhantering av händelseloggen med nya objekt</span><span class="sxs-lookup"><span data-stu-id="58227-131">Accessing a Remote Event Log with New-Object</span></span>
<span data-ttu-id="58227-132">De kommandon som används i föregående avsnitt rikta den lokala datorn. den **Get-EventLog** cmdlet kan göra det.</span><span class="sxs-lookup"><span data-stu-id="58227-132">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="58227-133">För att komma åt programloggen på en fjärrdator måste du ange både namnet på loggen och ett datornamn (eller IP-adress) som argument.</span><span class="sxs-lookup"><span data-stu-id="58227-133">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="58227-134">Nu när vi har en referens till en händelselogg som lagras i variabeln $RemoteAppLog uppgifter kan vi utföra på den?</span><span class="sxs-lookup"><span data-stu-id="58227-134">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

#### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="58227-135">Rensa en händelselogg med objektmetoder</span><span class="sxs-lookup"><span data-stu-id="58227-135">Clearing an Event Log with Object Methods</span></span>
<span data-ttu-id="58227-136">Objekt har ofta metoder som kan användas för att utföra uppgifter.</span><span class="sxs-lookup"><span data-stu-id="58227-136">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="58227-137">Du kan använda **Get-medlemmen** att visa vilka metoder som associeras med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="58227-137">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="58227-138">Följande kommando och valda visar några metoder i klassen händelseloggen:</span><span class="sxs-lookup"><span data-stu-id="58227-138">The following command and selected output show some the methods of the EventLog class:</span></span>

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

<span data-ttu-id="58227-139">Den **Rensa()** metoden kan användas för att rensa händelseloggen.</span><span class="sxs-lookup"><span data-stu-id="58227-139">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="58227-140">När du anropar en metod, måste du göra metodnamnet av parenteser, även om metoden som inte kräver argument.</span><span class="sxs-lookup"><span data-stu-id="58227-140">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="58227-141">Detta gör att Windows PowerShell skilja mellan metoden och potentiella egenskap med samma namn.</span><span class="sxs-lookup"><span data-stu-id="58227-141">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="58227-142">Skriv följande för att anropa den **Rensa** metoden:</span><span class="sxs-lookup"><span data-stu-id="58227-142">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="58227-143">Skriv följande för att visa loggen.</span><span class="sxs-lookup"><span data-stu-id="58227-143">Type the following to display the log.</span></span> <span data-ttu-id="58227-144">Du ser att händelseloggen har rensats och nu har 0 poster i stället för 262:</span><span class="sxs-lookup"><span data-stu-id="58227-144">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="58227-145">Skapa COM-objekt med nytt objekt</span><span class="sxs-lookup"><span data-stu-id="58227-145">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="58227-146">Du kan använda **New-Object** att arbeta med COM Component Object Model ()-komponenter.</span><span class="sxs-lookup"><span data-stu-id="58227-146">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="58227-147">Komponenter mellan de olika biblioteken som inkluderas med Windows Script Host (WSH) att ActiveX-program, till exempel Internet Explorer som är installerade på de flesta datorer.</span><span class="sxs-lookup"><span data-stu-id="58227-147">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="58227-148">**Nytt objekt** använder .NET Framework Runtime-Callable Omslutningar för att skapa COM-objekt, så att den har samma begränsningar som .NET Framework vid anrop av COM-objekt.</span><span class="sxs-lookup"><span data-stu-id="58227-148">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="58227-149">För att skapa ett COM-objekt, måste du ange den **ComObject** parameter med programmässiga identifierare eller *ProgId* av COM-klass som du vill använda.</span><span class="sxs-lookup"><span data-stu-id="58227-149">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="58227-150">En fullständig beskrivning av begränsningarna i COM-användning och bestämma vilka ProgID är tillgängligt i ett system som ligger utanför omfånget för den här användarhandboken, men de flesta välkända objekt från miljöer, till exempel WSH kan användas i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58227-150">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="58227-151">Du kan skapa WSH-objekt genom att ange dessa ProgID: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, och  **Scripting.FileSystemObject**.</span><span class="sxs-lookup"><span data-stu-id="58227-151">You can create the WSH objects by specifying these progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span></span> <span data-ttu-id="58227-152">Dessa objekt skapar du följande kommandon:</span><span class="sxs-lookup"><span data-stu-id="58227-152">The following commands create these objects:</span></span>

```
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="58227-153">Även om de flesta av funktionerna i de här klasserna görs tillgänglig på andra sätt i Windows PowerShell är några uppgifter som att skapa genväg fortfarande lättare att göra med hjälp av WSH-klasser.</span><span class="sxs-lookup"><span data-stu-id="58227-153">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="58227-154">Skapa en genväg på skrivbordet med WScript.Shell</span><span class="sxs-lookup"><span data-stu-id="58227-154">Creating a Desktop Shortcut with WScript.Shell</span></span>
<span data-ttu-id="58227-155">En uppgift som kan utföras snabbt med ett COM-objekt är att skapa en genväg.</span><span class="sxs-lookup"><span data-stu-id="58227-155">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="58227-156">Anta att du vill skapa en genväg på skrivbordet som länkar till arbetsmappen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58227-156">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="58227-157">Först måste du skapa en referens till **WScript.Shell**, som vi lagrar i en variabel med namnet **$WshShell**:</span><span class="sxs-lookup"><span data-stu-id="58227-157">You first need to create a reference to **WScript.Shell**, which we will store in a variable named **$WshShell**:</span></span>

```
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="58227-158">Get-medlem fungerar med COM-objekt, så du kan utforska medlemmarna i objektet genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="58227-158">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="58227-159">**Get-medlemmen** har en valfri **InputObject** parameter som används i stället för omdirigering för att ange indata för **Get-medlemmen**.</span><span class="sxs-lookup"><span data-stu-id="58227-159">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member**.</span></span> <span data-ttu-id="58227-160">Du skulle få samma utdata som visas ovan om du i stället använde kommandot **Get-medlem - InputObject $WshShell**.</span><span class="sxs-lookup"><span data-stu-id="58227-160">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell**.</span></span> <span data-ttu-id="58227-161">Om du använder **InputObject**, det behandlar argument som ett enskilt objekt.</span><span class="sxs-lookup"><span data-stu-id="58227-161">If you use **InputObject**, it treats its argument as a single item.</span></span> <span data-ttu-id="58227-162">Detta innebär att om du har flera objekt i en variabel **Get-medlemmen** behandlar dem som en matris med objekt.</span><span class="sxs-lookup"><span data-stu-id="58227-162">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="58227-163">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="58227-163">For example:</span></span>


```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="58227-164">Den **WScript.Shell CreateShortcut** metoden godkänner ett argument, sökvägen till genvägsfilen för att skapa.</span><span class="sxs-lookup"><span data-stu-id="58227-164">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="58227-165">Vi kan ange den fullständiga sökvägen till skrivbordet, men det finns ett enklare sätt.</span><span class="sxs-lookup"><span data-stu-id="58227-165">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="58227-166">Skrivbordet representeras normalt av en mapp med namnet skrivbordet i arbetsmappen för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="58227-166">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="58227-167">Windows PowerShell har en variabel **$Home** som innehåller sökvägen till den här mappen.</span><span class="sxs-lookup"><span data-stu-id="58227-167">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="58227-168">Vi kan ange sökvägen till arbetsmappen med hjälp av den här variabeln och Lägg sedan till namnet på mappen Skrivbord och namnet på genvägen till skapa genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="58227-168">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="58227-169">När du använder något som ser ut som ett variabelnamn inom citattecken, försöker Windows PowerShell i stället använda ett motsvarande värde.</span><span class="sxs-lookup"><span data-stu-id="58227-169">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="58227-170">Om du använder en citattecken, försöker Windows PowerShell inte ersätta variabelvärdet.</span><span class="sxs-lookup"><span data-stu-id="58227-170">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="58227-171">Skriv till exempel följande kommandon:</span><span class="sxs-lookup"><span data-stu-id="58227-171">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="58227-172">Nu har vi en variabel med namnet **$lnk** som innehåller en ny genväg referens.</span><span class="sxs-lookup"><span data-stu-id="58227-172">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="58227-173">Om du vill visa dess medlemmar kan du skicka det till **Get-medlemmen**.</span><span class="sxs-lookup"><span data-stu-id="58227-173">If you want to see its members, you can pipe it to **Get-Member**.</span></span> <span data-ttu-id="58227-174">Utdata nedan visas medlemmarna som vi behöver använda för att skapa våra genvägen:</span><span class="sxs-lookup"><span data-stu-id="58227-174">The output below shows the members we need to use to finish creating our shortcut:</span></span>

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

<span data-ttu-id="58227-175">Vi behöver ange den **TargetPath**, vilket är programmappen för Windows PowerShell och sedan spara genvägen **$lnk** genom att anropa den **spara** metod.</span><span class="sxs-lookup"><span data-stu-id="58227-175">We need to specify the **TargetPath**, which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="58227-176">Sökvägen till Windows PowerShell programmet lagras i variabeln **$PSHome**, så vi kan göra detta genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="58227-176">The Windows PowerShell application folder path is stored in the variable **$PSHome**, so we can do this by typing:</span></span>

```
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="58227-177">Med hjälp av Internet Explorer från Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="58227-177">Using Internet Explorer from Windows PowerShell</span></span>
<span data-ttu-id="58227-178">Många program (inklusive Microsoft Office-familjen av program och Internet Explorer) kan automatiseras med hjälp av COM.</span><span class="sxs-lookup"><span data-stu-id="58227-178">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="58227-179">Internet Explorer visar några av de vanliga tekniker och problem som ingår i att arbeta med COM-baserade program.</span><span class="sxs-lookup"><span data-stu-id="58227-179">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="58227-180">Du skapar en instans av Internet Explorer genom att ange den Internet Explorer ProgId, **InternetExplorer.Application**:</span><span class="sxs-lookup"><span data-stu-id="58227-180">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application**:</span></span>

```
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="58227-181">Detta kommando startar Internet Explorer, men göra inte den synlig.</span><span class="sxs-lookup"><span data-stu-id="58227-181">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="58227-182">Om du skriver Get-Process, kan du se att en process som kallas iexplore körs.</span><span class="sxs-lookup"><span data-stu-id="58227-182">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="58227-183">Om du avslutar Windows PowerShell i själva verket fortsätter processen att köras.</span><span class="sxs-lookup"><span data-stu-id="58227-183">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="58227-184">Du måste starta om datorn eller använda ett verktyg som Aktivitetshanteraren för att avsluta processen iexplore.</span><span class="sxs-lookup"><span data-stu-id="58227-184">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="58227-185">COM-objekt som startar som separata processer kallas ofta *ActiveX körbara filer*, kanske eller kanske inte visas ett fönster för gränssnittet användare när de startas.</span><span class="sxs-lookup"><span data-stu-id="58227-185">COM objects that start as separate processes, commonly called *ActiveX executables*, may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="58227-186">Om de skapa ett fönster utan att göra den synlig som Internet Explorer, fokus flyttas vanligtvis till Windows-skrivbordet och måste du göra fönstret synlig kan interagera med den.</span><span class="sxs-lookup"><span data-stu-id="58227-186">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="58227-187">Genom att skriva **$ie | Get-medlemmen**, du kan visa egenskaper och metoder för Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="58227-187">By typing **$ie | Get-Member**, you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="58227-188">Visa Internet Explorer-fönstret genom att ange egenskapen Visible till $true genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="58227-188">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```
$ie.Visible = $true
```

<span data-ttu-id="58227-189">Sedan kan du gå till en specifik webbadress med hjälp av metoden analysera:</span><span class="sxs-lookup"><span data-stu-id="58227-189">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

<span data-ttu-id="58227-190">Med andra medlemmar i objektmodellen i Internet Explorer är det möjligt att hämta textinnehåll från webbsidan.</span><span class="sxs-lookup"><span data-stu-id="58227-190">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="58227-191">Följande kommando visar HTML-texten i brödtexten för den aktuella webbsidan:</span><span class="sxs-lookup"><span data-stu-id="58227-191">The following command will display the HTML text in the body of the current Web page:</span></span>

```
$ie.Document.Body.InnerText
```

<span data-ttu-id="58227-192">Stäng Internet Explorer från PowerShell genom att anropa dess Quit()-metoden:</span><span class="sxs-lookup"><span data-stu-id="58227-192">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```
$ie.Quit()
```

<span data-ttu-id="58227-193">Detta kräver att den stängs.</span><span class="sxs-lookup"><span data-stu-id="58227-193">This will force it to close.</span></span> <span data-ttu-id="58227-194">$Ie variabeln innehåller inte längre en giltig referens till trots att den fortfarande kan vara ett COM-objekt.</span><span class="sxs-lookup"><span data-stu-id="58227-194">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="58227-195">Om du försöker använda den får du ett automationfel:</span><span class="sxs-lookup"><span data-stu-id="58227-195">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="58227-196">Du kan antingen ta bort de återstående referera med ett kommando som $ie = $null eller ta bort variabeln helt genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="58227-196">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="58227-197">Det finns ingen gemensam standard för om ActiveX körbara filer avsluta eller fortsätta att köras när du tar bort en referens till en.</span><span class="sxs-lookup"><span data-stu-id="58227-197">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="58227-198">Beroende på omständigheter som anger om programmet är synliga, om ett redigerat dokument körs i den och även om Windows PowerShell fortfarande körs programmet kan eller kan inte avslutas.</span><span class="sxs-lookup"><span data-stu-id="58227-198">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="58227-199">Därför bör du testa avslutning beteendet för varje ActiveX körbara du vill använda i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58227-199">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="58227-200">Visa varningar om .NET Framework radbrutet COM-objekt</span><span class="sxs-lookup"><span data-stu-id="58227-200">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>
<span data-ttu-id="58227-201">I vissa fall kan ett COM-objekt kan ha en associerad .NET Framework *Runtime-Callable Wrapper* eller RCW och det här kan användas av **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="58227-201">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object**.</span></span> <span data-ttu-id="58227-202">Eftersom beteendet för RCW kan skilja sig från beteendet för normal COM-objektet **New-Object** har en **strikt** parametern för att varna dig om RCW åtkomst.</span><span class="sxs-lookup"><span data-stu-id="58227-202">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="58227-203">Om du anger den **strikt** parameter och sedan skapa ett COM-objekt som använder en RCW, du får ett varningsmeddelande:</span><span class="sxs-lookup"><span data-stu-id="58227-203">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

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

<span data-ttu-id="58227-204">Även om det fortfarande skapas, varnas du att det inte är ett standard COM-objekt.</span><span class="sxs-lookup"><span data-stu-id="58227-204">Although the object is still created, you are warned that it is not a standard COM object.</span></span>

