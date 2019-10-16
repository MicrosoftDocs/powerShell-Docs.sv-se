---
title: Skapar körnings utrymmen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357731"
---
# <a name="creating-runspaces"></a><span data-ttu-id="53b33-102">Skapa körningsutrymmen</span><span class="sxs-lookup"><span data-stu-id="53b33-102">Creating Runspaces</span></span>

<span data-ttu-id="53b33-103">En körnings utrymme är operativ miljön för de kommandon som anropas av ett värd program.</span><span class="sxs-lookup"><span data-stu-id="53b33-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="53b33-104">Den här miljön innehåller de kommandon och data som för närvarande finns och eventuella språk begränsningar som gäller för närvarande.</span><span class="sxs-lookup"><span data-stu-id="53b33-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="53b33-105">Värd program kan använda standard-körnings utrymme som tillhandahålls av Windows PowerShell, som innehåller alla tillgängliga Core-kommandon, eller skapa en anpassad körnings utrymme som endast innehåller en delmängd av tillgängliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="53b33-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="53b33-106">Om du vill skapa en anpassad körnings utrymme skapar du ett [system. Management. Automation. körnings utrymmen. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt och tilldelar det till din körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="53b33-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="53b33-107">Körnings utrymme-uppgifter</span><span class="sxs-lookup"><span data-stu-id="53b33-107">Runspace tasks</span></span>

1. [<span data-ttu-id="53b33-108">Skapa en InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="53b33-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="53b33-109">Skapa en begränsad körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="53b33-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="53b33-110">Skapa flera körnings utrymmen</span><span class="sxs-lookup"><span data-stu-id="53b33-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="53b33-111">Se även</span><span class="sxs-lookup"><span data-stu-id="53b33-111">See Also</span></span>
