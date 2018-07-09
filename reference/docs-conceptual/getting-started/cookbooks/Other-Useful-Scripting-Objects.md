---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Andra användbara skriptobjekt
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 2ae9bc1864daedbcb0070c5f3862a6c98f8db2d4
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893288"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="49a26-103">Andra användbara skriptobjekt</span><span class="sxs-lookup"><span data-stu-id="49a26-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="49a26-104">Följande objekt innehåller ytterligare skript funktioner i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="49a26-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="49a26-105">De är inte en del av den **$psISE** hierarki.</span><span class="sxs-lookup"><span data-stu-id="49a26-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="49a26-106">Användbara skript-objekt</span><span class="sxs-lookup"><span data-stu-id="49a26-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="49a26-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="49a26-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="49a26-108">Det finns vissa begränsningar för hur Windows PowerShell ISE interagerar med konsolprogram.</span><span class="sxs-lookup"><span data-stu-id="49a26-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="49a26-109">Ett kommando eller ett skript för automatisering som kräver åtgärder från användaren kanske inte fungerar hur det fungerar från Windows PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="49a26-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="49a26-110">Du kanske vill blockera dessa kommandon eller skript från att köras i fönstret Windows PowerShell ISE-kommando.</span><span class="sxs-lookup"><span data-stu-id="49a26-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="49a26-111">Den **$psUnsupportedConsoleApplications** objektet ser till att en lista över dessa kommandon.</span><span class="sxs-lookup"><span data-stu-id="49a26-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="49a26-112">Om du försöker köra kommandon i den här listan, får du ett meddelande om att de inte stöds.</span><span class="sxs-lookup"><span data-stu-id="49a26-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="49a26-113">Följande skript läggs en post i listan.</span><span class="sxs-lookup"><span data-stu-id="49a26-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="49a26-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="49a26-114">$psLocalHelp</span></span>

<span data-ttu-id="49a26-115">Det här är ett katalogobjekt som upprätthåller en sammanhangsberoende mappning mellan hjälpavsnitt och deras associerade länkar i den lokala kompilerade HTML-hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="49a26-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="49a26-116">Den används för att hitta lokal hjälp för ett visst ämne.</span><span class="sxs-lookup"><span data-stu-id="49a26-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="49a26-117">Du kan lägga till eller ta bort ämnen från den här listan.</span><span class="sxs-lookup"><span data-stu-id="49a26-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="49a26-118">I följande kodexempel visas några exempel nyckel / värde-par som finns i `$psLocalHelp`.</span><span class="sxs-lookup"><span data-stu-id="49a26-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="pslocalhelp-sample-output"></a><span data-ttu-id="49a26-119">$psLocalHelp exempel på utdata</span><span class="sxs-lookup"><span data-stu-id="49a26-119">$psLocalHelp Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="49a26-120">Nyckel: Lägg-dator</span><span class="sxs-lookup"><span data-stu-id="49a26-120">Key : Add-Computer</span></span>|<span data-ttu-id="49a26-121">Värde: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="49a26-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="49a26-122">Nyckel: Lägga till innehåll</span><span class="sxs-lookup"><span data-stu-id="49a26-122">Key : Add-Content</span></span>|<span data-ttu-id="49a26-123">Värde: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="49a26-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

<span data-ttu-id="49a26-124">Följande skript läggs en post i listan.</span><span class="sxs-lookup"><span data-stu-id="49a26-124">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="49a26-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="49a26-125">$psOnlineHelp</span></span>

<span data-ttu-id="49a26-126">Det här är ett katalogobjekt som upprätthåller en sammanhangsberoende mappning mellan avsnittet titlarna på hjälpavsnitt och deras associerade externa URL: er.</span><span class="sxs-lookup"><span data-stu-id="49a26-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="49a26-127">Den används för att hitta hjälp för ett visst ämne på webben.</span><span class="sxs-lookup"><span data-stu-id="49a26-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="49a26-128">Du kan lägga till eller ta bort ämnen från den här listan.</span><span class="sxs-lookup"><span data-stu-id="49a26-128">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

## <a name="psonilnehelp-sample-output"></a><span data-ttu-id="49a26-129">$psOnilneHelp exempel på utdata</span><span class="sxs-lookup"><span data-stu-id="49a26-129">$psOnilneHelp Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="49a26-130">Nyckel: Lägg-dator</span><span class="sxs-lookup"><span data-stu-id="49a26-130">Key : Add-Computer</span></span>|<span data-ttu-id="49a26-131">Värde: http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="49a26-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="49a26-132">Nyckel: Lägga till innehåll</span><span class="sxs-lookup"><span data-stu-id="49a26-132">Key : Add-Content</span></span>|<span data-ttu-id="49a26-133">Värde: http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="49a26-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

<span data-ttu-id="49a26-134">Följande skript läggs en post i listan.</span><span class="sxs-lookup"><span data-stu-id="49a26-134">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="49a26-135">Se även</span><span class="sxs-lookup"><span data-stu-id="49a26-135">See Also</span></span>

[<span data-ttu-id="49a26-136">Syftet med den Windows PowerShell ISE-Skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="49a26-136">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)