---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell SDK
description: Windows PowerShell SDK
ms.openlocfilehash: 751ccb02741db0ea63df1768dec4a19c5fa9ce92
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "94390209"
---
# <a name="windows-powershell"></a><span data-ttu-id="ef657-103">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ef657-103">Windows PowerShell</span></span>

<span data-ttu-id="ef657-104">Uppdaterad: 8 juli 2013</span><span class="sxs-lookup"><span data-stu-id="ef657-104">Updated: July 8, 2013</span></span>

<span data-ttu-id="ef657-105">Windows PowerShell &reg; är ett uppgifts baserat kommando rads gränssnitt och skript språk som är särskilt utformat för system administration.</span><span class="sxs-lookup"><span data-stu-id="ef657-105">Windows PowerShell&reg; is a task-based command-line shell and scripting language designed especially for system administration.</span></span> <span data-ttu-id="ef657-106">Windows PowerShell bygger på .NET Framework och &reg; hjälper IT-proffs och privilegierade användare att styra och automatisera administrationen av Windows-operativsystemet och program som körs i Windows.</span><span class="sxs-lookup"><span data-stu-id="ef657-106">Built on the .NET Framework, Windows PowerShell&reg; helps IT professionals and power users control and automate the administration of the Windows operating system and applications that run on Windows.</span></span>

<span data-ttu-id="ef657-107">Dokumenten som publiceras här skrivs främst för cmdlet-, Provider-och värd program utvecklare som behöver referensinformation om de API: er som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef657-107">The documents published here are written primarily for cmdlet, provider, and host application developers who require reference information about the APIs provided by Windows PowerShell.</span></span>
<span data-ttu-id="ef657-108">System administratörer kan dock också hitta den information som tillhandahålls av dessa dokument.</span><span class="sxs-lookup"><span data-stu-id="ef657-108">However, system administrators might also find the information provided by these documents useful.</span></span>

<span data-ttu-id="ef657-109">Grundläggande information som behövs för att börja använda Windows PowerShell finns i Komma igång med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef657-109">For the basic information needed to start using Windows PowerShell, see Getting Started with Windows PowerShell .</span></span>

## <a name="windows-powershell-documents"></a><span data-ttu-id="ef657-110">Windows PowerShell-dokument</span><span class="sxs-lookup"><span data-stu-id="ef657-110">Windows PowerShell Documents</span></span>

- <span data-ttu-id="ef657-111">[Installera Windows POWERSHELL SDK](./installing-the-windows-powershell-sdk.md) Innehåller information om hur du installerar Windows PowerShell SDK.</span><span class="sxs-lookup"><span data-stu-id="ef657-111">[Installing the Windows PowerShell SDK](./installing-the-windows-powershell-sdk.md) Provides information about how to install the Windows PowerShell SDK.</span></span>

- <span data-ttu-id="ef657-112">[Skriva en Windows PowerShell-modul](./module/writing-a-windows-powershell-module.md) Innehåller information för administratörer, skript utvecklare och cmdlet-utvecklare som behöver paketera och distribuera sina Windows PowerShell-lösningar.</span><span class="sxs-lookup"><span data-stu-id="ef657-112">[Writing a Windows PowerShell Module](./module/writing-a-windows-powershell-module.md) Provides information for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell solutions.</span></span>

- <span data-ttu-id="ef657-113">[Skriva en Windows PowerShell-cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) Innehåller information om att utforma och implementera cmdlets.</span><span class="sxs-lookup"><span data-stu-id="ef657-113">[Writing a Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) Provides information for designing and implementing cmdlets.</span></span>

- <span data-ttu-id="ef657-114">[Skriva en Windows PowerShell-Provider](./provider/writing-a-windows-powershell-provider.md) Innehåller information om hur du utformar och implementerar Windows PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="ef657-114">[Writing a Windows PowerShell Provider](./provider/writing-a-windows-powershell-provider.md) Provides information for designing and implementing Windows PowerShell providers.</span></span> <span data-ttu-id="ef657-115">Det hjälper dig att förstå hur Windows PowerShell-leverantörer fungerar och innehåller exempel kod som du kan använda för att börja utforma eller skriva egna leverantörer.</span><span class="sxs-lookup"><span data-stu-id="ef657-115">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

- <span data-ttu-id="ef657-116">[Skriva ett Windows PowerShell-värdprogram](./hosting/writing-a-windows-powershell-host-application.md) Innehåller information som kan användas av program hanterare som utformar värd program och av utvecklare som implementerar dem.</span><span class="sxs-lookup"><span data-stu-id="ef657-116">[Writing a Windows PowerShell Host Application](./hosting/writing-a-windows-powershell-host-application.md) Provides information that can be used by program managers who are designing host applications and by developers who are implementing them.</span></span> <span data-ttu-id="ef657-117">Värd programmet kan, definiera körnings utrymme där kommandon körs, öppna sessioner på en lokal dator eller fjärrdator och anropa kommandona synkront eller asynkront baserat på programmets behov.</span><span class="sxs-lookup"><span data-stu-id="ef657-117">The host application can, define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

- <span data-ttu-id="ef657-118">[Skriva en fil med PowerShell-formatering](./format/writing-a-powershell-formatting-file.md) Innehåller information för redigering av formateringsattribut, som styr visnings formatet för de objekt som returneras av-kommandon (cmdlets, Functions och scripts).</span><span class="sxs-lookup"><span data-stu-id="ef657-118">[Writing a PowerShell Formatting File](./format/writing-a-powershell-formatting-file.md) Provides information for the authoring of formatting files, which control the display format for the objects that are returned by commands (cmdlets, functions, and scripts).</span></span>

- <span data-ttu-id="ef657-119">[Windows PowerShell-referens](./windows-powershell-reference.md) Innehåller referens innehåll för de API: er som används i skrivning av cmdlets, providers och värd program, samt andra stödda API: er.</span><span class="sxs-lookup"><span data-stu-id="ef657-119">[Windows PowerShell Reference](./windows-powershell-reference.md) Provides reference content for the APIs used in writing cmdlets, providers, and host applications, as well as other supporting APIs.</span></span>
