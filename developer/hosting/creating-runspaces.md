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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848148"
---
# <a name="creating-runspaces"></a>Skapa körningsutrymmen

Ett körningsutrymme är driftsmiljön för de kommandon som anropas av en värdprogrammet. Den här miljön innehåller kommandon och data som för närvarande finns och alla språk begränsningar som gäller för närvarande.

 Vara värd för program kan använda standard-körningsutrymmet som tillhandahålls av Windows PowerShell, som innehåller alla tillgängliga kärnor kommandon, eller skapa en anpassad körningsutrymme som innehåller endast en delmängd av tillgängliga kommandon. Om du vill skapa en anpassad körningsutrymme, skapar du en [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objekt och tilldela den till din körningsutrymme.

## <a name="runspace-tasks"></a>Körningsutrymme uppgifter

1. [Skapa en InitialSessionState](./creating-an-initialsessionstate.md)

2. [Skapa en begränsad körningsutrymme](./creating-a-constrained-runspace.md)

3. [Skapa flera körningsutrymmen](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Se även
