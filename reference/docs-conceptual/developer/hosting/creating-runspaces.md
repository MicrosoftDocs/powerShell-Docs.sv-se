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
# <a name="creating-runspaces"></a>Skapa körningsutrymmen

En körnings utrymme är operativ miljön för de kommandon som anropas av ett värd program. Den här miljön innehåller de kommandon och data som för närvarande finns och eventuella språk begränsningar som gäller för närvarande.

 Värd program kan använda standard-körnings utrymme som tillhandahålls av Windows PowerShell, som innehåller alla tillgängliga Core-kommandon, eller skapa en anpassad körnings utrymme som endast innehåller en delmängd av tillgängliga kommandon. Om du vill skapa en anpassad körnings utrymme skapar du ett [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt och tilldelar det till din körnings utrymme.

## <a name="runspace-tasks"></a>Körnings utrymme-uppgifter

1. [Skapa en InitialSessionState](./creating-an-initialsessionstate.md)

2. [Skapa ett begränsat körningsutrymme](./creating-a-constrained-runspace.md)

3. [Skapa flera körningsutrymmen](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Se även
