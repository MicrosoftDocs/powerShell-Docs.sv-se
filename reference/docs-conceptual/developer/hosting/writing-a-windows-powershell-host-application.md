---
title: Skriva ett Windows PowerShell-värdprogram | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: b44708b3bbcb974a6178323dff2302b7da121af6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357521"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="fb67a-102">Skriva ett Windows PowerShell-värdprogram</span><span class="sxs-lookup"><span data-stu-id="fb67a-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="fb67a-103">Du kan vara värd för Windows PowerShell i ditt program.</span><span class="sxs-lookup"><span data-stu-id="fb67a-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="fb67a-104">Värd programmet kan definiera körnings utrymme där kommandon körs, öppna sessioner på en lokal eller fjärran sluten dator och anropa kommandona antingen synkront eller asynkront baserat på programmets behov.</span><span class="sxs-lookup"><span data-stu-id="fb67a-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="fb67a-105">I följande avsnitt förklaras hur du skapar ett program som är värd för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb67a-105">The following topics explain how to create an application that hosts Windows PowerShell.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fb67a-106">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="fb67a-106">In This Section</span></span>

<span data-ttu-id="fb67a-107">[Snabb start för Windows PowerShell-värd](./windows-powershell-host-quickstart.md) Innehåller instruktioner och kod exempel för att komma igång med att skapa värd program.</span><span class="sxs-lookup"><span data-stu-id="fb67a-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="fb67a-108">[Skapar körnings utrymmen](./creating-runspaces.md) En uppsättning ämnen som förklarar hur du skapar körnings utrymmen för att köra Windows PowerShell-kommandot i ett värd program.</span><span class="sxs-lookup"><span data-stu-id="fb67a-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="fb67a-109">[Lägga till och anropa kommandon](./adding-and-invoking-commands.md) Förklarar hur du skapar och kör en kommando pipeline i värd programmet..</span><span class="sxs-lookup"><span data-stu-id="fb67a-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="fb67a-110">[Skapar fjärran körnings utrymmen](./creating-remote-runspaces.md) Förklarar hur du ansluter en körnings utrymme till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="fb67a-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="fb67a-111">[Skapa ett anpassat användar gränssnitt](./creating-a-custom-user-interface.md) Introducerar anpassade användar gränssnitt och innehåller länkar till exempel.</span><span class="sxs-lookup"><span data-stu-id="fb67a-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="fb67a-112">[Värd program exempel](./host-application-samples.md) Det här avsnittet innehåller exempel på kompletta värd program.</span><span class="sxs-lookup"><span data-stu-id="fb67a-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb67a-113">Se även</span><span class="sxs-lookup"><span data-stu-id="fb67a-113">See Also</span></span>

[<span data-ttu-id="fb67a-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb67a-114">Windows PowerShell</span></span>](https://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)
