---
title: Skriva ett program för Windows PowerShell-värd | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: 1aaf936aa22af5c4a4b8c2fa4e6b3bbd2cff6d20
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855091"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="3367f-102">Skriva ett Windows PowerShell-värdprogram</span><span class="sxs-lookup"><span data-stu-id="3367f-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="3367f-103">Du kan vara värd för Windows PowerShell i ditt program.</span><span class="sxs-lookup"><span data-stu-id="3367f-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="3367f-104">Värdprogrammet kan definiera runspace där kommandon är köra, öppna sessioner på en lokal dator eller fjärrdator och anropa kommandon synkront eller asynkront, beroende på dina behov för programmet.</span><span class="sxs-lookup"><span data-stu-id="3367f-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="3367f-105">I följande avsnitt beskriver hur du skapar ett program som är värd för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3367f-105">The following topics explain how to create an application that hosts Windows PowerShell.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3367f-106">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="3367f-106">In This Section</span></span>

<span data-ttu-id="3367f-107">[Snabbstart för Windows PowerShell-värd](./windows-powershell-host-quickstart.md) tillhandahåller instruktioner och kodexempel för att komma igång med att skapa vara värd för program.</span><span class="sxs-lookup"><span data-stu-id="3367f-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="3367f-108">[Skapa Körningsutrymmen](./creating-runspaces.md) en samling hjälpavsnitt som beskriver hur du skapar körningsutrymmen för att köra Windows PowerShell-kommando i ett program.</span><span class="sxs-lookup"><span data-stu-id="3367f-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="3367f-109">[Att lägga till och anropa kommandon](./adding-and-invoking-commands.md) förklarar hur du skapar och kör en pipeline för kommandot i din värdapp...</span><span class="sxs-lookup"><span data-stu-id="3367f-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="3367f-110">[Skapa fjärransluten körningsutrymmen](./creating-remote-runspaces.md) förklarar hur du ansluter ett körningsutrymme till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="3367f-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="3367f-111">[Skapa ett anpassat användargränssnitt](./creating-a-custom-user-interface.md) Introduces anpassade användarinställningar gränssnitt och innehåller länkar till exempel.</span><span class="sxs-lookup"><span data-stu-id="3367f-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="3367f-112">[Vara värd för programmet exempel](./host-application-samples.md) det här avsnittet innehåller exempel på fullständiga värd för program.</span><span class="sxs-lookup"><span data-stu-id="3367f-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="3367f-113">Se även</span><span class="sxs-lookup"><span data-stu-id="3367f-113">See Also</span></span>

[<span data-ttu-id="3367f-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3367f-114">Windows PowerShell</span></span>](http://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)
