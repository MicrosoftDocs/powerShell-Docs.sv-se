---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Andra användbara skriptobjekt
description: I den här artikeln beskrivs objekt som innehåller ytterligare skript funktioner i Windows PowerShell ISE.
ms.openlocfilehash: c20daa0045bc07b1f21aafa42a80ce7c47ee7331
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500274"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="43475-104">Andra användbara skriptobjekt</span><span class="sxs-lookup"><span data-stu-id="43475-104">Other Useful Scripting Objects</span></span>

<span data-ttu-id="43475-105">Följande objekt ger ytterligare skript funktioner i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="43475-105">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="43475-106">De ingår inte i **$psISE** hierarkin.</span><span class="sxs-lookup"><span data-stu-id="43475-106">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="43475-107">Användbara skript objekt</span><span class="sxs-lookup"><span data-stu-id="43475-107">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="43475-108">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="43475-108">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="43475-109">Det finns vissa begränsningar för hur Windows PowerShell ISE interagerar med konsol program.</span><span class="sxs-lookup"><span data-stu-id="43475-109">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="43475-110">Ett kommando eller ett Automation-skript som kräver åtgärder från användaren kanske inte fungerar på samma sätt som i Windows PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="43475-110">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="43475-111">Du kanske vill blockera de här kommandona eller skripten från att köras i Windows PowerShell ISE kommando fönstret.</span><span class="sxs-lookup"><span data-stu-id="43475-111">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="43475-112">**$PsUnsupportedConsoleApplications** -objektet innehåller en lista över sådana kommandon.</span><span class="sxs-lookup"><span data-stu-id="43475-112">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="43475-113">Om du försöker köra kommandona i den här listan får du ett meddelande om att de inte stöds.</span><span class="sxs-lookup"><span data-stu-id="43475-113">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="43475-114">Följande skript lägger till en post i listan.</span><span class="sxs-lookup"><span data-stu-id="43475-114">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="43475-115">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="43475-115">$psLocalHelp</span></span>

<span data-ttu-id="43475-116">Detta är ett Dictionary-objekt som upprätthåller en Sammanhangs beroende mappning mellan hjälp ämnen och tillhör ande länkar i den lokala kompilerade HTML-hjälp filen.</span><span class="sxs-lookup"><span data-stu-id="43475-116">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="43475-117">Den används för att hitta den lokala hjälpen för ett visst ämne.</span><span class="sxs-lookup"><span data-stu-id="43475-117">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="43475-118">Du kan lägga till eller ta bort ämnen från den här listan.</span><span class="sxs-lookup"><span data-stu-id="43475-118">You can add or delete topics from this list.</span></span> <span data-ttu-id="43475-119">I följande kod exempel visas några exempel på nyckel/värde-par som finns i `$psLocalHelp` .</span><span class="sxs-lookup"><span data-stu-id="43475-119">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```Output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

<span data-ttu-id="43475-120">Följande skript lägger till en post i listan.</span><span class="sxs-lookup"><span data-stu-id="43475-120">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="43475-121">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="43475-121">$psOnlineHelp</span></span>

<span data-ttu-id="43475-122">Detta är ett Dictionary-objekt som upprätthåller en Sammanhangs beroende mappning mellan ämnes titlarna i hjälp avsnitten och deras associerade externa URL: er.</span><span class="sxs-lookup"><span data-stu-id="43475-122">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="43475-123">Den används för att hitta hjälpen för ett visst ämne på webben.</span><span class="sxs-lookup"><span data-stu-id="43475-123">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="43475-124">Du kan lägga till eller ta bort ämnen från den här listan.</span><span class="sxs-lookup"><span data-stu-id="43475-124">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```Output
Key   : Add-Computer
Value : https://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : https://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="43475-125">Följande skript lägger till en post i listan.</span><span class="sxs-lookup"><span data-stu-id="43475-125">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "https://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="43475-126">Se även</span><span class="sxs-lookup"><span data-stu-id="43475-126">See Also</span></span>

[<span data-ttu-id="43475-127">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="43475-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
