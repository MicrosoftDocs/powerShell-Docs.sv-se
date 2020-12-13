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
# <a name="creating-runspaces"></a>Skapa körningsutrymmen

En körnings utrymme är operativ miljön för de kommandon som anropas av ett värd program. Den här miljön innehåller de kommandon och data som för närvarande finns och eventuella språk begränsningar som gäller för närvarande.

 Värd program kan använda standard-körnings utrymme som tillhandahålls av Windows PowerShell, som innehåller alla tillgängliga Core-kommandon, eller skapa en anpassad körnings utrymme som endast innehåller en delmängd av tillgängliga kommandon. Om du vill skapa en anpassad körnings utrymme skapar du ett [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt och tilldelar det till din körnings utrymme.

## <a name="runspace-tasks"></a>Körnings utrymme-uppgifter

1. [Skapa en InitialSessionState](./creating-an-initialsessionstate.md)

2. [Skapa ett begränsat körningsutrymme](./creating-a-constrained-runspace.md)

3. [Skapa flera körningsutrymmen](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Se även
