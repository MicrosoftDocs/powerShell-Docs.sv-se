---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Andra användbara skriptobjekt"
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 8334d0b346e59dea3643a93bf52b780b361d1945
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="99ae2-103">Andra användbara skriptobjekt</span><span class="sxs-lookup"><span data-stu-id="99ae2-103">Other Useful Scripting Objects</span></span>
  <span data-ttu-id="99ae2-104">Följande objekt innehåller ytterligare scripting funktioner i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="99ae2-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="99ae2-105">De är inte en del av den **$psISE** hierarki.</span><span class="sxs-lookup"><span data-stu-id="99ae2-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="99ae2-106">Användbar skript-objekt</span><span class="sxs-lookup"><span data-stu-id="99ae2-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="99ae2-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="99ae2-107">$psUnsupportedConsoleApplications</span></span>
 <span data-ttu-id="99ae2-108">Det finns vissa begränsningar för hur Windows PowerShell ISE samverkar med program.</span><span class="sxs-lookup"><span data-stu-id="99ae2-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="99ae2-109">Ett kommando eller ett automation-skript som kräver åtgärder från användaren kanske inte fungerar hur det fungerar från Windows PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="99ae2-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="99ae2-110">Du kanske vill blockera dessa kommandon eller skript från att köras i fönstret Windows PowerShell ISE-kommando.</span><span class="sxs-lookup"><span data-stu-id="99ae2-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="99ae2-111">Den **$psUnsupportedConsoleApplications** objekt har en lista över dessa kommandon.</span><span class="sxs-lookup"><span data-stu-id="99ae2-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="99ae2-112">Om du försöker köra kommandona i den här listan får ett meddelande om att de inte stöds.</span><span class="sxs-lookup"><span data-stu-id="99ae2-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="99ae2-113">Följande skript lägger till en post i listan.</span><span class="sxs-lookup"><span data-stu-id="99ae2-113">The following script adds an entry to the list.</span></span>

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### <a name="pslocalhelp"></a><span data-ttu-id="99ae2-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="99ae2-114">$psLocalHelp</span></span>
 <span data-ttu-id="99ae2-115">Detta är ett katalogobjekt som underhåller en sammanhangsberoende mappning mellan hjälpavsnitt och deras associerade länkar i den lokala kompilerade HTML-hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="99ae2-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="99ae2-116">Den används för att hitta den lokala hjälpen för ett visst ämne.</span><span class="sxs-lookup"><span data-stu-id="99ae2-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="99ae2-117">Du kan lägga till eller ta bort ämnen i den här listan.</span><span class="sxs-lookup"><span data-stu-id="99ae2-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="99ae2-118">Följande kodexempel visar några exempel nyckel-värdepar som finns i **$psLocalHelp**.</span><span class="sxs-lookup"><span data-stu-id="99ae2-118">The following code example shows some example key-value pairs that are contained in **$psLocalHelp**.</span></span>

```
# See the local help map
$psLocalHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="99ae2-119">Exempel på utdata</span><span class="sxs-lookup"><span data-stu-id="99ae2-119">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="99ae2-120">Nyckel: Lägg till dator</span><span class="sxs-lookup"><span data-stu-id="99ae2-120">Key : Add-Computer</span></span>|<span data-ttu-id="99ae2-121">Värde: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="99ae2-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="99ae2-122">Nyckel: Lägga till innehåll</span><span class="sxs-lookup"><span data-stu-id="99ae2-122">Key : Add-Content</span></span>|<span data-ttu-id="99ae2-123">Värde: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="99ae2-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

 <span data-ttu-id="99ae2-124">Följande skript lägger till en post i listan.</span><span class="sxs-lookup"><span data-stu-id="99ae2-124">The following script adds an entry to the list.</span></span>

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="99ae2-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="99ae2-125">$psOnlineHelp</span></span>
 <span data-ttu-id="99ae2-126">Detta är ett katalogobjekt som underhåller en sammanhangsberoende mappning mellan avsnittet titlarna på hjälpavsnitt och deras associerade externa URL: er.</span><span class="sxs-lookup"><span data-stu-id="99ae2-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="99ae2-127">Den används för att hitta hjälp för ett visst ämne på webben.</span><span class="sxs-lookup"><span data-stu-id="99ae2-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="99ae2-128">Du kan lägga till eller ta bort ämnen i den här listan.</span><span class="sxs-lookup"><span data-stu-id="99ae2-128">You can add or delete topics from this list.</span></span>

```
$psOnlineHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="99ae2-129">Exempel på utdata</span><span class="sxs-lookup"><span data-stu-id="99ae2-129">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="99ae2-130">Nyckel: Lägg till dator</span><span class="sxs-lookup"><span data-stu-id="99ae2-130">Key : Add-Computer</span></span>|<span data-ttu-id="99ae2-131">Värde: http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="99ae2-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="99ae2-132">Nyckel: Lägga till innehåll</span><span class="sxs-lookup"><span data-stu-id="99ae2-132">Key : Add-Content</span></span>|<span data-ttu-id="99ae2-133">Värde: http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="99ae2-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

 <span data-ttu-id="99ae2-134">Följande skript lägger till en post i listan.</span><span class="sxs-lookup"><span data-stu-id="99ae2-134">The following script adds an entry to the list.</span></span>

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="99ae2-135">Se även</span><span class="sxs-lookup"><span data-stu-id="99ae2-135">See Also</span></span>
- [<span data-ttu-id="99ae2-136">Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="99ae2-136">The Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
