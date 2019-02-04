---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Skapa .NET- och COM-objekt nytt objekt
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: 1ffd8d4afa419ec0c24321e44aa4a2f41a9bee44
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684131"
---
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="dcf2f-103">Skapa .NET- och COM-objekt (New-Object)</span><span class="sxs-lookup"><span data-stu-id="dcf2f-103">Creating .NET and COM Objects (New-Object)</span></span>

<span data-ttu-id="dcf2f-104">Det finns programvarukomponenter med .NET Framework- och COM-gränssnitt som gör det möjligt att utföra många aktiviteter för administration av system.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-104">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="dcf2f-105">Windows PowerShell kan du använda de här komponenterna så att du inte är begränsad till de uppgifter som kan utföras med hjälp av cmdlet: ar.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-105">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="dcf2f-106">Många av i denna första version av Windows PowerShell-cmdlets fungerar inte mot fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-106">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="dcf2f-107">Vi visar hur du kan komma runt denna begränsning vid hantering av händelseloggar genom att använda .NET Framework **system.Diagnostics.Eventlog och** klass direkt från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-107">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

### <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="dcf2f-108">Med New-Object för händelseloggen åtkomst</span><span class="sxs-lookup"><span data-stu-id="dcf2f-108">Using New-Object for Event Log Access</span></span>

<span data-ttu-id="dcf2f-109">.NET Framework Class-bibliotek innehåller en klass med namnet **system.Diagnostics.Eventlog och** som kan användas för att hantera händelseloggar.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-109">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="dcf2f-110">Du kan skapa en ny instans av en .NET Framework-klass med hjälp av den **New-Object** cmdlet med den **TypeName** parametern.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-110">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="dcf2f-111">Till exempel skapar följande kommando en referens i händelseloggen:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-111">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="dcf2f-112">Även om kommandot har skapat en instans av klassen EventLog, innehåller instansen inte några data.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-112">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="dcf2f-113">Det beror på att vi inte har angett en viss händelselogg.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-113">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="dcf2f-114">Hur får du en verklig händelselogg?</span><span class="sxs-lookup"><span data-stu-id="dcf2f-114">How do you get a real event log?</span></span>

#### <a name="using-constructors-with-new-object"></a><span data-ttu-id="dcf2f-115">Med New-Object konstruktorer</span><span class="sxs-lookup"><span data-stu-id="dcf2f-115">Using Constructors with New-Object</span></span>

<span data-ttu-id="dcf2f-116">Refererar till en specifik händelselogg, måste du ange namn på loggen.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-116">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="dcf2f-117">**New-Object** har en **ArgumentList** parametern.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-117">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="dcf2f-118">Argument som du skickar som värden för den här parametern används av en särskild startmetoden i-objektet.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-118">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="dcf2f-119">Metoden anropas en *konstruktorn* eftersom den används för att skapa objektet.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-119">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="dcf2f-120">Till exempel om du vill hämta en referens till programloggen anger du strängen ”program” som ett argument:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-120">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="dcf2f-121">Eftersom de flesta .NET Framework core klasser finns i namnrymden System, försöker Windows PowerShell automatiskt hitta klasser som du anger i namnrymden System om den inte kan hitta en matchning för typename som du anger.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-121">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="dcf2f-122">Det innebär att du kan ange Diagnostics.EventLog i stället för system.Diagnostics.Eventlog och.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-122">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

#### <a name="storing-objects-in-variables"></a><span data-ttu-id="dcf2f-123">Lagra objekt i variabler</span><span class="sxs-lookup"><span data-stu-id="dcf2f-123">Storing Objects in Variables</span></span>

<span data-ttu-id="dcf2f-124">Du kanske vill spara en referens till ett objekt, så att du kan använda den i det nuvarande gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-124">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="dcf2f-125">Även om Windows PowerShell kan du göra mycket arbete med pipelines inskränkning behovet av variabler, är ibland lagra referenser till objekt i variabler det mer praktiskt att ändra dessa objekt.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-125">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="dcf2f-126">Windows PowerShell kan du skapa variabler som är i stort sett namngivna objekt.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-126">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="dcf2f-127">Utdata från alla giltiga Windows PowerShell-kommandon kan lagras i en variabel.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-127">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="dcf2f-128">Variabelnamn börja alltid med $.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-128">Variable names always begin with $.</span></span> <span data-ttu-id="dcf2f-129">Om du vill lagra Application log-referens i en variabel med namnet $AppLog, skriver du namnet på variabeln, följt av ett likhetstecken och skriv sedan kommandot används för att skapa log programobjektet:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-129">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="dcf2f-130">Om du anger sedan $AppLog kan se du att den innehåller programloggen:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-130">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="dcf2f-131">Åtkomst till en fjärrhantering av händelseloggen med New-Object</span><span class="sxs-lookup"><span data-stu-id="dcf2f-131">Accessing a Remote Event Log with New-Object</span></span>

<span data-ttu-id="dcf2f-132">De kommandon som används i föregående avsnitt rikta den lokala datorn. den **Get-EventLog** cmdlet kan göra.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-132">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="dcf2f-133">För att komma åt programloggen på en fjärrdator, måste du ange både namnet på loggen och ett datornamn (eller IP-adress) som argument.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-133">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="dcf2f-134">Nu när vi har en referens till en händelselogg som lagras i variabeln $RemoteAppLog vilka uppgifter kan vi utföra på den?</span><span class="sxs-lookup"><span data-stu-id="dcf2f-134">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

#### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="dcf2f-135">Rensa en händelselogg med objektmetoder</span><span class="sxs-lookup"><span data-stu-id="dcf2f-135">Clearing an Event Log with Object Methods</span></span>

<span data-ttu-id="dcf2f-136">Objekt har ofta metoder som kan anropas för att utföra uppgifter.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-136">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="dcf2f-137">Du kan använda **Get-Member** att visa de metoder som associeras med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-137">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="dcf2f-138">Följande kommando och valda utdata visar några metoder i klassen EventLog:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-138">The following command and selected output show some the methods of the EventLog class:</span></span>

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

<span data-ttu-id="dcf2f-139">Den **Rensa()** metoden kan användas för att rensa händelseloggen.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-139">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="dcf2f-140">När du anropar en metod, måste du göra metodnamnet av parenteser, även om metoden som inte kräver argument.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-140">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="dcf2f-141">På så sätt kan Windows PowerShell skilja mellan metoden och en potentiell egenskap med samma namn.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-141">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="dcf2f-142">Skriv följande för att anropa den **Rensa** metoden:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-142">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="dcf2f-143">Skriv följande om du vill visa loggen.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-143">Type the following to display the log.</span></span> <span data-ttu-id="dcf2f-144">Du ser att händelseloggen har rensats och nu har 0 poster i stället för 262:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-144">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="dcf2f-145">Skapa COM-objekt med New-Object</span><span class="sxs-lookup"><span data-stu-id="dcf2f-145">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="dcf2f-146">Du kan använda **New-Object** att arbeta med komponenter för COM Component Object Model ().</span><span class="sxs-lookup"><span data-stu-id="dcf2f-146">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="dcf2f-147">Komponenter sträcker sig från de olika bibliotek som inkluderas med Windows Script Host (WSH) att ActiveX-program, till exempel Internet Explorer som är installerade på de flesta system.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-147">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="dcf2f-148">**New-Object** använder .NET Framework Runtime-Anropningsbara Omslutningar för att skapa COM-objekt, så att den har samma begränsningar som .NET Framework när du anropar COM-objekt.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-148">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="dcf2f-149">Om du vill skapa ett COM-objekt, måste du ange den **ComObject** parameter med den programmässiga identifieraren eller *ProgId* av COM-klass som du vill använda.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-149">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="dcf2f-150">En fullständig beskrivning av begränsningar av COM-användning och bestämma vilka ProgID är tillgängligt i ett system är utanför omfattningen för den här användarhandboken, men mest välkända objekt från miljöer, till exempel WSH kan användas i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-150">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="dcf2f-151">Du kan skapa WSH-objekt genom att ange dessa ProgID: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-151">You can create the WSH objects by specifying these progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span></span> <span data-ttu-id="dcf2f-152">Följande kommandon kan skapa dessa objekt:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-152">The following commands create these objects:</span></span>

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="dcf2f-153">Även om de flesta av funktionerna i de här klasserna görs tillgänglig på andra sätt i Windows PowerShell, är några uppgifter som att skapa genväg fortfarande lättare att göra med hjälp av WSH-klasser.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-153">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="dcf2f-154">Skapa en genväg på skrivbordet med WScript.Shell</span><span class="sxs-lookup"><span data-stu-id="dcf2f-154">Creating a Desktop Shortcut with WScript.Shell</span></span>

<span data-ttu-id="dcf2f-155">En aktivitet som kan utföras snabbt med ett COM-objekt är att skapa en genväg.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-155">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="dcf2f-156">Anta att du vill skapa en genväg på skrivbordet som länkar till arbetsmappen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-156">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="dcf2f-157">Du måste först skapa en referens till **WScript.Shell**, som vi lagrar i en variabel med namnet **$WshShell**:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-157">You first need to create a reference to **WScript.Shell**, which we will store in a variable named **$WshShell**:</span></span>

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="dcf2f-158">Get-Member fungerar med COM-objekt, så du kan utforska medlemmarna i objektet genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-158">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="dcf2f-159">**Get-Member** har en valfri **InputObject** parameter som du kan använda i stället för omdirigering som indata för **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-159">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member**.</span></span> <span data-ttu-id="dcf2f-160">Du skulle få samma utdata som ovan om du i stället använde kommandot **Get-Member - InputObject $WshShell**.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-160">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell**.</span></span> <span data-ttu-id="dcf2f-161">Om du använder **InputObject**, den behandlar dess argument som ett enskilt objekt.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-161">If you use **InputObject**, it treats its argument as a single item.</span></span> <span data-ttu-id="dcf2f-162">Det innebär att om du har flera objekt i en variabel, **Get-Member** behandlar dem som en matris med objekt.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-162">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="dcf2f-163">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-163">For example:</span></span>

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="dcf2f-164">Den **WScript.Shell CreateShortcut** metoden godkänner ett argument, sökvägen till genvägsfilen för att skapa.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-164">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="dcf2f-165">Vi kan skriva i den fullständiga sökvägen till skrivbordet, men det finns ett enklare sätt.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-165">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="dcf2f-166">Skrivbordet är vanligtvis representeras av en mapp med namnet Desktop i arbetsmappen för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-166">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="dcf2f-167">Windows PowerShell har en variabel **$Home** som innehåller sökvägen till den här mappen.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-167">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="dcf2f-168">Vi kan ange sökvägen till arbetsmappen med hjälp av den här variabeln och Lägg sedan till namnet på mappen Skrivbord och namnet på genvägen till skapa genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-168">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="dcf2f-169">När du använder något som ser ut som ett variabelnamn inom dubbla citattecken, försöker Windows PowerShell att ersätta ett motsvarande värde.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-169">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="dcf2f-170">Om du använder en citattecken, försöker Windows PowerShell inte att ersätta variabelvärdet.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-170">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="dcf2f-171">Prova till exempel att skriva följande kommandon:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-171">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="dcf2f-172">Nu har vi en variabel med namnet **$lnk** som innehåller en ny genväg referens.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-172">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="dcf2f-173">Om du vill visa medlemmarna kan du skicka det till **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-173">If you want to see its members, you can pipe it to **Get-Member**.</span></span> <span data-ttu-id="dcf2f-174">Utdata nedan visar medlemmarna som vi behöver använda skapa vår genväg:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-174">The output below shows the members we need to use to finish creating our shortcut:</span></span>

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

<span data-ttu-id="dcf2f-175">Vi måste du ange den **TargetPath**, vilket är programmappen för Windows PowerShell och sedan spara genvägen **$lnk** genom att anropa den **spara** metod.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-175">We need to specify the **TargetPath**, which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="dcf2f-176">Mappsökväg för Windows PowerShell-programmet lagras i variabeln **$PSHome**, så vi kan göra detta genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-176">The Windows PowerShell application folder path is stored in the variable **$PSHome**, so we can do this by typing:</span></span>

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="dcf2f-177">Med hjälp av Internet Explorer från Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dcf2f-177">Using Internet Explorer from Windows PowerShell</span></span>

<span data-ttu-id="dcf2f-178">Många program (inklusive i Microsoft Office-familjen av program och Internet Explorer) kan automatiseras med hjälp av COM.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-178">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="dcf2f-179">Internet Explorer visar några av de vanliga metoder och problem som ingår i att arbeta med COM-baserade program.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-179">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="dcf2f-180">Du skapar en instans av Internet Explorer genom att ange den Internet Explorer ProgId, **InternetExplorer.Application**:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-180">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application**:</span></span>

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="dcf2f-181">Det här kommandot startar Internet Explorer, men gör inte det synligt.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-181">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="dcf2f-182">Om du skriver Get-Process, kan du se att en process som kallas iexplore körs.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-182">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="dcf2f-183">Om du avslutar Windows PowerShell i själva verket fortsätter processen att köras.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-183">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="dcf2f-184">Du måste starta om datorn eller använda ett verktyg som Aktivitetshanteraren för att avsluta processen iexplore.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-184">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="dcf2f-185">COM-objekt som börjar som separata processer kallas *ActiveX körbara filer*, kanske eller kanske inte visas ett fönster för user interface när de startas.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-185">COM objects that start as separate processes, commonly called *ActiveX executables*, may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="dcf2f-186">Om de skapa ett fönster, men inte gör det visas, till exempel Internet Explorer, kommer vanligtvis att flytta fokus på Windows-skrivbordet och du måste göra fönstret synlig för att interagera med den.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-186">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="dcf2f-187">Genom att skriva **$ie | Get-Member**, du kan visa egenskaper och metoder för Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-187">By typing **$ie | Get-Member**, you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="dcf2f-188">Om du vill se i Internet Explorer-fönstret visas egenskapen värdet $true genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-188">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```powershell
$ie.Visible = $true
```

<span data-ttu-id="dcf2f-189">Du kan sedan navigera till en specifik webbadress med hjälp av metoden analysera:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-189">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

<span data-ttu-id="dcf2f-190">Med andra medlemmar i Internet Explorer: objektmodell, är det möjligt att hämta textinnehållet från webbsidan.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-190">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="dcf2f-191">Följande kommando visar HTML-texten i brödtexten i den aktuella webbsidan:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-191">The following command will display the HTML text in the body of the current Web page:</span></span>

```powershell
$ie.Document.Body.InnerText
```

<span data-ttu-id="dcf2f-192">Stäng Internet Explorer från PowerShell genom att anropa dess Quit()-metoden:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-192">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```powershell
$ie.Quit()
```

<span data-ttu-id="dcf2f-193">Detta kommer att tvinga den att Stäng.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-193">This will force it to close.</span></span> <span data-ttu-id="dcf2f-194">$Ie variabeln innehåller inte längre en giltig referens trots att den fortfarande verkar vara ett COM-objekt.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-194">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="dcf2f-195">Om du försöker använda den, får du ett automationfel:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-195">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="dcf2f-196">Du kan antingen ta bort de återstående referera med ett kommando som $ie = $null eller helt ta bort variabeln genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-196">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```powershell
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="dcf2f-197">Det finns ingen gemensam standard för huruvida ActiveX körbara filer avsluta eller fortsätta att köras när du tar bort en referens till en.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-197">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="dcf2f-198">Beroende på omständigheterna som huruvida programmet är synliga, om ett redigerat dokument körs i den och även om Windows PowerShell fortfarande körs programmet kan eller kan inte avslutas.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-198">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="dcf2f-199">Därför bör du testa avslutning beteendet för varje ActiveX körbara du vill använda i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-199">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="dcf2f-200">Få varningar om .NET Framework-omslutna COM-objekt</span><span class="sxs-lookup"><span data-stu-id="dcf2f-200">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>

<span data-ttu-id="dcf2f-201">I vissa fall kan en COM-objektet kan ha en associerad .NET Framework *Runtime-Anropningsbara omslutning* eller RCW och det här kommer att användas av **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-201">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object**.</span></span> <span data-ttu-id="dcf2f-202">Eftersom RCW beteende kan skilja sig från beteendet för normal COM-objektet **New-Object** har en **Strict** parameter för att varna dig om RCW åtkomst.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-202">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="dcf2f-203">Om du anger den **Strict** parametern och sedan skapa ett COM-objekt som använder en RCW, du får ett varningsmeddelande:</span><span class="sxs-lookup"><span data-stu-id="dcf2f-203">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

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

<span data-ttu-id="dcf2f-204">Även om objektet fortfarande har skapats, ett meddelande om att det inte är ett standard COM-objekt.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-204">Although the object is still created, you are warned that it is not a standard COM object.</span></span>