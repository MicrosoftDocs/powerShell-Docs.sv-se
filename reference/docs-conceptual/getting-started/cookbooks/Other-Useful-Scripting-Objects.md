---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Andra användbara skriptobjekt
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 04e94f858b568928b3910dd0ee85a912a6afc264
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268508"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="7a92a-103">Andra användbara skriptobjekt</span><span class="sxs-lookup"><span data-stu-id="7a92a-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="7a92a-104">Följande objekt innehåller ytterligare skript funktioner i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7a92a-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="7a92a-105">De är inte en del av den **$psISE** hierarki.</span><span class="sxs-lookup"><span data-stu-id="7a92a-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="7a92a-106">Användbara skript-objekt</span><span class="sxs-lookup"><span data-stu-id="7a92a-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="7a92a-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="7a92a-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="7a92a-108">Det finns vissa begränsningar för hur Windows PowerShell ISE interagerar med konsolprogram.</span><span class="sxs-lookup"><span data-stu-id="7a92a-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="7a92a-109">Ett kommando eller ett skript för automatisering som kräver åtgärder från användaren kanske inte fungerar hur det fungerar från Windows PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="7a92a-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="7a92a-110">Du kanske vill blockera dessa kommandon eller skript från att köras i fönstret Windows PowerShell ISE-kommando.</span><span class="sxs-lookup"><span data-stu-id="7a92a-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="7a92a-111">Den **$psUnsupportedConsoleApplications** objektet ser till att en lista över dessa kommandon.</span><span class="sxs-lookup"><span data-stu-id="7a92a-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="7a92a-112">Om du försöker köra kommandon i den här listan, får du ett meddelande om att de inte stöds.</span><span class="sxs-lookup"><span data-stu-id="7a92a-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="7a92a-113">Följande skript läggs en post i listan.</span><span class="sxs-lookup"><span data-stu-id="7a92a-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="7a92a-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="7a92a-114">$psLocalHelp</span></span>

<span data-ttu-id="7a92a-115">Det här är ett katalogobjekt som upprätthåller en sammanhangsberoende mappning mellan hjälpavsnitt och deras associerade länkar i den lokala kompilerade HTML-hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="7a92a-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="7a92a-116">Den används för att hitta lokal hjälp för ett visst ämne.</span><span class="sxs-lookup"><span data-stu-id="7a92a-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="7a92a-117">Du kan lägga till eller ta bort ämnen från den här listan.</span><span class="sxs-lookup"><span data-stu-id="7a92a-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="7a92a-118">I följande kodexempel visas några exempel nyckel / värde-par som finns i `$psLocalHelp`.</span><span class="sxs-lookup"><span data-stu-id="7a92a-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

<span data-ttu-id="7a92a-119">Följande skript läggs en post i listan.</span><span class="sxs-lookup"><span data-stu-id="7a92a-119">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="7a92a-120">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="7a92a-120">$psOnlineHelp</span></span>

<span data-ttu-id="7a92a-121">Det här är ett katalogobjekt som upprätthåller en sammanhangsberoende mappning mellan avsnittet titlarna på hjälpavsnitt och deras associerade externa URL: er.</span><span class="sxs-lookup"><span data-stu-id="7a92a-121">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="7a92a-122">Den används för att hitta hjälp för ett visst ämne på webben.</span><span class="sxs-lookup"><span data-stu-id="7a92a-122">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="7a92a-123">Du kan lägga till eller ta bort ämnen från den här listan.</span><span class="sxs-lookup"><span data-stu-id="7a92a-123">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : http://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : http://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="7a92a-124">Följande skript läggs en post i listan.</span><span class="sxs-lookup"><span data-stu-id="7a92a-124">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="7a92a-125">Se även</span><span class="sxs-lookup"><span data-stu-id="7a92a-125">See Also</span></span>

[<span data-ttu-id="7a92a-126">Syftet med den Windows PowerShell ISE-Skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="7a92a-126">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)