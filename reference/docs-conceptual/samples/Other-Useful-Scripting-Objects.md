---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Andra användbara skriptobjekt
ms.openlocfilehash: 4f236246714b0608658bbd535851489912430336
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71325149"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="97b68-103">Andra användbara skriptobjekt</span><span class="sxs-lookup"><span data-stu-id="97b68-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="97b68-104">Följande objekt ger ytterligare skript funktioner i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="97b68-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="97b68-105">De ingår inte i **$psISE** hierarkin.</span><span class="sxs-lookup"><span data-stu-id="97b68-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="97b68-106">Användbara skript objekt</span><span class="sxs-lookup"><span data-stu-id="97b68-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="97b68-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="97b68-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="97b68-108">Det finns vissa begränsningar för hur Windows PowerShell ISE interagerar med konsol program.</span><span class="sxs-lookup"><span data-stu-id="97b68-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="97b68-109">Ett kommando eller ett Automation-skript som kräver åtgärder från användaren kanske inte fungerar på samma sätt som i Windows PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="97b68-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="97b68-110">Du kanske vill blockera de här kommandona eller skripten från att köras i Windows PowerShell ISE kommando fönstret.</span><span class="sxs-lookup"><span data-stu-id="97b68-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="97b68-111">**$PsUnsupportedConsoleApplications** -objektet innehåller en lista över sådana kommandon.</span><span class="sxs-lookup"><span data-stu-id="97b68-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="97b68-112">Om du försöker köra kommandona i den här listan får du ett meddelande om att de inte stöds.</span><span class="sxs-lookup"><span data-stu-id="97b68-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="97b68-113">Följande skript lägger till en post i listan.</span><span class="sxs-lookup"><span data-stu-id="97b68-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="97b68-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="97b68-114">$psLocalHelp</span></span>

<span data-ttu-id="97b68-115">Detta är ett Dictionary-objekt som upprätthåller en Sammanhangs beroende mappning mellan hjälp ämnen och tillhör ande länkar i den lokala kompilerade HTML-hjälp filen.</span><span class="sxs-lookup"><span data-stu-id="97b68-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="97b68-116">Den används för att hitta den lokala hjälpen för ett visst ämne.</span><span class="sxs-lookup"><span data-stu-id="97b68-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="97b68-117">Du kan lägga till eller ta bort ämnen från den här listan.</span><span class="sxs-lookup"><span data-stu-id="97b68-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="97b68-118">I följande kod exempel visas några exempel på nyckel/värde-par som finns `$psLocalHelp`i.</span><span class="sxs-lookup"><span data-stu-id="97b68-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

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

<span data-ttu-id="97b68-119">Följande skript lägger till en post i listan.</span><span class="sxs-lookup"><span data-stu-id="97b68-119">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="97b68-120">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="97b68-120">$psOnlineHelp</span></span>

<span data-ttu-id="97b68-121">Detta är ett Dictionary-objekt som upprätthåller en Sammanhangs beroende mappning mellan ämnes titlarna i hjälp avsnitten och deras associerade externa URL: er.</span><span class="sxs-lookup"><span data-stu-id="97b68-121">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="97b68-122">Den används för att hitta hjälpen för ett visst ämne på webben.</span><span class="sxs-lookup"><span data-stu-id="97b68-122">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="97b68-123">Du kan lägga till eller ta bort ämnen från den här listan.</span><span class="sxs-lookup"><span data-stu-id="97b68-123">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : https://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : https://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="97b68-124">Följande skript lägger till en post i listan.</span><span class="sxs-lookup"><span data-stu-id="97b68-124">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "https://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="97b68-125">Se även</span><span class="sxs-lookup"><span data-stu-id="97b68-125">See Also</span></span>

[<span data-ttu-id="97b68-126">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="97b68-126">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
