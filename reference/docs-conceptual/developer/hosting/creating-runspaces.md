---
title: Skapar körnings utrymmen | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0c27e2bf54e16a3bdc93c4b91629893bb1cc1e3e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779581"
---
# <a name="creating-runspaces"></a><span data-ttu-id="3e955-102">Skapa körningsutrymmen</span><span class="sxs-lookup"><span data-stu-id="3e955-102">Creating Runspaces</span></span>

<span data-ttu-id="3e955-103">En körnings utrymme är operativ miljön för de kommandon som anropas av ett värd program.</span><span class="sxs-lookup"><span data-stu-id="3e955-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="3e955-104">Den här miljön innehåller de kommandon och data som för närvarande finns och eventuella språk begränsningar som gäller för närvarande.</span><span class="sxs-lookup"><span data-stu-id="3e955-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="3e955-105">Värd program kan använda standard-körnings utrymme som tillhandahålls av Windows PowerShell, som innehåller alla tillgängliga Core-kommandon, eller skapa en anpassad körnings utrymme som endast innehåller en delmängd av tillgängliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="3e955-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="3e955-106">Om du vill skapa en anpassad körnings utrymme skapar du ett [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt och tilldelar det till din körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="3e955-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="3e955-107">Körnings utrymme-uppgifter</span><span class="sxs-lookup"><span data-stu-id="3e955-107">Runspace tasks</span></span>

1. [<span data-ttu-id="3e955-108">Skapa en InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="3e955-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="3e955-109">Skapa ett begränsat körningsutrymme</span><span class="sxs-lookup"><span data-stu-id="3e955-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="3e955-110">Skapa flera körningsutrymmen</span><span class="sxs-lookup"><span data-stu-id="3e955-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="3e955-111">Se även</span><span class="sxs-lookup"><span data-stu-id="3e955-111">See Also</span></span>
