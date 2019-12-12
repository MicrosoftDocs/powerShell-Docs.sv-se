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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357731"
---
# <a name="creating-runspaces"></a>Skapa körningsutrymmen

En körnings utrymme är operativ miljön för de kommandon som anropas av ett värd program. Den här miljön innehåller de kommandon och data som för närvarande finns och eventuella språk begränsningar som gäller för närvarande.

 Värd program kan använda standard-körnings utrymme som tillhandahålls av Windows PowerShell, som innehåller alla tillgängliga Core-kommandon, eller skapa en anpassad körnings utrymme som endast innehåller en delmängd av tillgängliga kommandon. Om du vill skapa en anpassad körnings utrymme skapar du ett [system. Management. Automation. körnings utrymmen. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt och tilldelar det till din körnings utrymme.

## <a name="runspace-tasks"></a>Körnings utrymme-uppgifter

1. [Skapa en InitialSessionState](./creating-an-initialsessionstate.md)

2. [Skapa en begränsad körnings utrymme](./creating-a-constrained-runspace.md)

3. [Skapa flera körnings utrymmen](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Se även
