---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa körningsutrymmen
description: Skapa körningsutrymmen
ms.openlocfilehash: c6b2c577e435ec88364b189a0c3d065f54f02525
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649345"
---
# <a name="creating-runspaces"></a><span data-ttu-id="a4470-103">Skapa körningsutrymmen</span><span class="sxs-lookup"><span data-stu-id="a4470-103">Creating Runspaces</span></span>

<span data-ttu-id="a4470-104">En körnings utrymme är operativ miljön för de kommandon som anropas av ett värd program.</span><span class="sxs-lookup"><span data-stu-id="a4470-104">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="a4470-105">Den här miljön innehåller de kommandon och data som för närvarande finns och eventuella språk begränsningar som gäller för närvarande.</span><span class="sxs-lookup"><span data-stu-id="a4470-105">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="a4470-106">Värd program kan använda standard-körnings utrymme som tillhandahålls av Windows PowerShell, som innehåller alla tillgängliga Core-kommandon, eller skapa en anpassad körnings utrymme som endast innehåller en delmängd av tillgängliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="a4470-106">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="a4470-107">Om du vill skapa en anpassad körnings utrymme skapar du ett [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt och tilldelar det till din körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="a4470-107">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="a4470-108">Körnings utrymme-uppgifter</span><span class="sxs-lookup"><span data-stu-id="a4470-108">Runspace tasks</span></span>

1. [<span data-ttu-id="a4470-109">Skapa en InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="a4470-109">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="a4470-110">Skapa ett begränsat körningsutrymme</span><span class="sxs-lookup"><span data-stu-id="a4470-110">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="a4470-111">Skapa flera körningsutrymmen</span><span class="sxs-lookup"><span data-stu-id="a4470-111">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="a4470-112">Se även</span><span class="sxs-lookup"><span data-stu-id="a4470-112">See Also</span></span>
