---
title: Windows PowerShell SDK
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 7627ab336ddc40ab47c3017eed77c78bbdac4e7f
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470822"
---
# <a name="windows-powershell"></a><span data-ttu-id="610a9-102">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="610a9-102">Windows PowerShell</span></span>

<span data-ttu-id="610a9-103">Uppdaterad: 8 juli 2013</span><span class="sxs-lookup"><span data-stu-id="610a9-103">Updated: July 8, 2013</span></span>

<span data-ttu-id="610a9-104">Windows PowerShell® är ett uppgiftsbaserat kommandoradsgränssnitt och skriptspråk som utformats specifikt för systemadministration.</span><span class="sxs-lookup"><span data-stu-id="610a9-104">Windows PowerShell® is a task-based command-line shell and scripting language designed especially for system administration.</span></span> <span data-ttu-id="610a9-105">Bygger på .NET Framework och Windows PowerShell® hjälper IT-proffs och erfarna användare att styra och automatisera administrationen av Windows-operativsystem och program som körs på Windows.</span><span class="sxs-lookup"><span data-stu-id="610a9-105">Built on the .NET Framework, Windows PowerShell® helps IT professionals and power users control and automate the administration of the Windows operating system and applications that run on Windows.</span></span>

<span data-ttu-id="610a9-106">Dokument som publiceras här skrivs främst för cmdlet-providern och värden programutvecklare som kräver information om API: er som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="610a9-106">The documents published here are written primarily for cmdlet, provider, and host application developers who require reference information about the APIs provided by Windows PowerShell.</span></span>
<span data-ttu-id="610a9-107">Systemadministratörer kan också hitta den information som tillhandahålls av dokumenten användbart.</span><span class="sxs-lookup"><span data-stu-id="610a9-107">However, system administrators might also find the information provided by these documents useful.</span></span>

<span data-ttu-id="610a9-108">Den grundläggande informationen som behövs för att starta med hjälp av Windows PowerShell, finns i komma igång med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="610a9-108">For the basic information needed to start using Windows PowerShell, see Getting Started with Windows PowerShell .</span></span>

## <a name="windows-powershell-documents-on-msdn"></a><span data-ttu-id="610a9-109">Windows PowerShell-dokument på MSDN</span><span class="sxs-lookup"><span data-stu-id="610a9-109">Windows PowerShell Documents on MSDN</span></span>

- <span data-ttu-id="610a9-110">[Installera Windows PowerShell SDK](./installing-the-windows-powershell-sdk.md) innehåller information om hur du installerar Windows PowerShell SDK: N.</span><span class="sxs-lookup"><span data-stu-id="610a9-110">[Installing the Windows PowerShell SDK](./installing-the-windows-powershell-sdk.md) Provides information about how to install the Windows PowerShell SDK.</span></span>

- <span data-ttu-id="610a9-111">[Skriva ett Windows PowerShell-modul](./module/writing-a-windows-powershell-module.md) innehåller information för administratörer, skript, utvecklare och cmdlet-utvecklare som måste du paketera och distribuera sina Windows PowerShell-lösningar.</span><span class="sxs-lookup"><span data-stu-id="610a9-111">[Writing a Windows PowerShell Module](./module/writing-a-windows-powershell-module.md) Provides information for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell solutions.</span></span>

- <span data-ttu-id="610a9-112">[Skriva en Windows PowerShell-Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) innehåller information för att utforma och implementera cmdletar.</span><span class="sxs-lookup"><span data-stu-id="610a9-112">[Writing a Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) Provides information for designing and implementing cmdlets.</span></span>

- <span data-ttu-id="610a9-113">[Skriva ett Windows PowerShell-providern](./provider/writing-a-windows-powershell-provider.md) innehåller information för att utforma och implementera Windows PowerShell-providers.</span><span class="sxs-lookup"><span data-stu-id="610a9-113">[Writing a Windows PowerShell Provider](./provider/writing-a-windows-powershell-provider.md) Provides information for designing and implementing Windows PowerShell providers.</span></span> <span data-ttu-id="610a9-114">Det hjälper dig att förstå hur Windows PowerShell-leverantörer fungerar och den exempelkod som du kan använda för att börja utforma eller skriva egna providers.</span><span class="sxs-lookup"><span data-stu-id="610a9-114">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

- <span data-ttu-id="610a9-115">[Skriva ett Windows PowerShell-värdprogram](./hosting/writing-a-windows-powershell-host-application.md) innehåller information som kan användas genom programchefer som designar vara värd för program och utvecklare som implementerar dem.</span><span class="sxs-lookup"><span data-stu-id="610a9-115">[Writing a Windows PowerShell Host Application](./hosting/writing-a-windows-powershell-host-application.md) Provides information that can be used by program managers who are designing host applications and by developers who are implementing them.</span></span> <span data-ttu-id="610a9-116">Värdprogrammet kan definiera runspace där kommandon är körning, öppna sessioner på en lokal eller fjärransluten dator och anropa kommandon synkront eller asynkront, beroende på dina behov för programmet.</span><span class="sxs-lookup"><span data-stu-id="610a9-116">The host application can, define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

- <span data-ttu-id="610a9-117">[Skriver en PowerShell-formatering fil](./format/writing-a-powershell-formatting-file.md) ger information om redigering av formatering filer, vilket styr visningsformatet för de objekt som returneras av kommandon (cmdlet: ar, funktioner och skript).</span><span class="sxs-lookup"><span data-stu-id="610a9-117">[Writing a PowerShell Formatting File](./format/writing-a-powershell-formatting-file.md) Provides information for the authoring of formatting files, which control the display format for the objects that are returned by commands (cmdlets, functions, and scripts).</span></span>

- <span data-ttu-id="610a9-118">[Windows PowerShell-referens](./windows-powershell-reference.md) tillhandahåller Referensinnehåll för API: er som används i skriva cmdlets, leverantörer och vara värd för program, samt andra stödjande API: er.</span><span class="sxs-lookup"><span data-stu-id="610a9-118">[Windows PowerShell Reference](./windows-powershell-reference.md) Provides reference content for the APIs used in writing cmdlets, providers, and host applications, as well as other supporting APIs.</span></span>
