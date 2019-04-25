---
title: Skapa Körningsutrymmen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082948"
---
# <a name="creating-runspaces"></a><span data-ttu-id="6af31-102">Skapa körningsutrymmen</span><span class="sxs-lookup"><span data-stu-id="6af31-102">Creating Runspaces</span></span>

<span data-ttu-id="6af31-103">Ett körningsutrymme är driftsmiljön för de kommandon som anropas av en värdprogrammet.</span><span class="sxs-lookup"><span data-stu-id="6af31-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="6af31-104">Den här miljön innehåller kommandon och data som för närvarande finns och alla språk begränsningar som gäller för närvarande.</span><span class="sxs-lookup"><span data-stu-id="6af31-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="6af31-105">Vara värd för program kan använda standard-körningsutrymmet som tillhandahålls av Windows PowerShell, som innehåller alla tillgängliga kärnor kommandon, eller skapa en anpassad körningsutrymme som innehåller endast en delmängd av tillgängliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="6af31-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="6af31-106">Om du vill skapa en anpassad körningsutrymme, skapar du en [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objekt och tilldela den till din körningsutrymme.</span><span class="sxs-lookup"><span data-stu-id="6af31-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="6af31-107">Körningsutrymme uppgifter</span><span class="sxs-lookup"><span data-stu-id="6af31-107">Runspace tasks</span></span>

1. [<span data-ttu-id="6af31-108">Skapa en InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="6af31-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="6af31-109">Skapa en begränsad körningsutrymme</span><span class="sxs-lookup"><span data-stu-id="6af31-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="6af31-110">Skapa flera körningsutrymmen</span><span class="sxs-lookup"><span data-stu-id="6af31-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="6af31-111">Se även</span><span class="sxs-lookup"><span data-stu-id="6af31-111">See Also</span></span>
