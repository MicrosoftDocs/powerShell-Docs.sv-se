---
title: Windows PowerShell SDK
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 7627ab336ddc40ab47c3017eed77c78bbdac4e7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356667"
---
# <a name="windows-powershell"></a><span data-ttu-id="58d07-102">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="58d07-102">Windows PowerShell</span></span>

<span data-ttu-id="58d07-103">Uppdaterad: 8 juli 2013</span><span class="sxs-lookup"><span data-stu-id="58d07-103">Updated: July 8, 2013</span></span>

<span data-ttu-id="58d07-104">Windows PowerShell® är ett aktivitetsbaserat kommandoradsskal och skriptspråk som är särskilt utformat för systemadministration.</span><span class="sxs-lookup"><span data-stu-id="58d07-104">Windows PowerShell® is a task-based command-line shell and scripting language designed especially for system administration.</span></span> <span data-ttu-id="58d07-105">Windows PowerShell® bygger på .NET Framework och hjälper IT-proffs och privilegierade användare att styra och automatisera administrationen av Windows-operativsystemet och program som körs i Windows.</span><span class="sxs-lookup"><span data-stu-id="58d07-105">Built on the .NET Framework, Windows PowerShell® helps IT professionals and power users control and automate the administration of the Windows operating system and applications that run on Windows.</span></span>

<span data-ttu-id="58d07-106">Dokumenten som publiceras här skrivs främst för cmdlet-, Provider-och värd program utvecklare som behöver referensinformation om de API: er som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58d07-106">The documents published here are written primarily for cmdlet, provider, and host application developers who require reference information about the APIs provided by Windows PowerShell.</span></span>
<span data-ttu-id="58d07-107">System administratörer kan dock också hitta den information som tillhandahålls av dessa dokument.</span><span class="sxs-lookup"><span data-stu-id="58d07-107">However, system administrators might also find the information provided by these documents useful.</span></span>

<span data-ttu-id="58d07-108">Grundläggande information som behövs för att börja använda Windows PowerShell finns i Komma igång med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58d07-108">For the basic information needed to start using Windows PowerShell, see Getting Started with Windows PowerShell .</span></span>

## <a name="windows-powershell-documents-on-msdn"></a><span data-ttu-id="58d07-109">Windows PowerShell-dokument på MSDN</span><span class="sxs-lookup"><span data-stu-id="58d07-109">Windows PowerShell Documents on MSDN</span></span>

- <span data-ttu-id="58d07-110">[Installera Windows POWERSHELL SDK](./installing-the-windows-powershell-sdk.md) Innehåller information om hur du installerar Windows PowerShell SDK.</span><span class="sxs-lookup"><span data-stu-id="58d07-110">[Installing the Windows PowerShell SDK](./installing-the-windows-powershell-sdk.md) Provides information about how to install the Windows PowerShell SDK.</span></span>

- <span data-ttu-id="58d07-111">[Skriva en Windows PowerShell-modul](./module/writing-a-windows-powershell-module.md) Innehåller information för administratörer, skript utvecklare och cmdlet-utvecklare som behöver paketera och distribuera sina Windows PowerShell-lösningar.</span><span class="sxs-lookup"><span data-stu-id="58d07-111">[Writing a Windows PowerShell Module](./module/writing-a-windows-powershell-module.md) Provides information for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell solutions.</span></span>

- <span data-ttu-id="58d07-112">[Skriva en Windows PowerShell-cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) Innehåller information om att utforma och implementera cmdlets.</span><span class="sxs-lookup"><span data-stu-id="58d07-112">[Writing a Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) Provides information for designing and implementing cmdlets.</span></span>

- <span data-ttu-id="58d07-113">[Skriva en Windows PowerShell-Provider](./provider/writing-a-windows-powershell-provider.md) Innehåller information om hur du utformar och implementerar Windows PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="58d07-113">[Writing a Windows PowerShell Provider](./provider/writing-a-windows-powershell-provider.md) Provides information for designing and implementing Windows PowerShell providers.</span></span> <span data-ttu-id="58d07-114">Det hjälper dig att förstå hur Windows PowerShell-leverantörer fungerar och innehåller exempel kod som du kan använda för att börja utforma eller skriva egna leverantörer.</span><span class="sxs-lookup"><span data-stu-id="58d07-114">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

- <span data-ttu-id="58d07-115">[Skriva ett Windows PowerShell-värdprogram](./hosting/writing-a-windows-powershell-host-application.md) Innehåller information som kan användas av program hanterare som utformar värd program och av utvecklare som implementerar dem.</span><span class="sxs-lookup"><span data-stu-id="58d07-115">[Writing a Windows PowerShell Host Application](./hosting/writing-a-windows-powershell-host-application.md) Provides information that can be used by program managers who are designing host applications and by developers who are implementing them.</span></span> <span data-ttu-id="58d07-116">Värd programmet kan, definiera körnings utrymme där kommandon körs, öppna sessioner på en lokal dator eller fjärrdator och anropa kommandona synkront eller asynkront baserat på programmets behov.</span><span class="sxs-lookup"><span data-stu-id="58d07-116">The host application can, define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

- <span data-ttu-id="58d07-117">[Skriva en fil med PowerShell-formatering](./format/writing-a-powershell-formatting-file.md) Innehåller information för redigering av formateringsattribut, som styr visnings formatet för de objekt som returneras av-kommandon (cmdlets, Functions och scripts).</span><span class="sxs-lookup"><span data-stu-id="58d07-117">[Writing a PowerShell Formatting File](./format/writing-a-powershell-formatting-file.md) Provides information for the authoring of formatting files, which control the display format for the objects that are returned by commands (cmdlets, functions, and scripts).</span></span>

- <span data-ttu-id="58d07-118">[Windows PowerShell-referens](./windows-powershell-reference.md) Innehåller referens innehåll för de API: er som används i skrivning av cmdlets, providers och värd program, samt andra stödda API: er.</span><span class="sxs-lookup"><span data-stu-id="58d07-118">[Windows PowerShell Reference](./windows-powershell-reference.md) Provides reference content for the APIs used in writing cmdlets, providers, and host applications, as well as other supporting APIs.</span></span>
