---
title: Cmdlet-attribut | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359447"
---
# <a name="cmdlet-attributes"></a>Cmdlet-attribut

Windows PowerShell definierar flera attribut som du kan använda för att lägga till vanliga funktioner i dina cmdletar utan att implementera den funktionen i din egen kod. Detta inkluderar det cmdlet-attribut som identifierar en Microsoft .NET Framework-klass som en cmdlet-klass, attributet OutputType som anger de .NET Framework typer som returneras av cmdleten, attributet parameter som identifierar offentliga egenskaper som cmdlet parametrar med mera.

## <a name="in-this-section"></a>I detta avsnitt

[Attribut i cmdlet-kod](./attributes-in-cmdlet-code.md) Beskriver fördelen med att använda attribut i cmdlet-kod.

[Attributtyper](./attribute-types.md) Beskriver de olika attribut som kan dekorera en cmdlet-klass.

[Deklaration av alias-attribut](./alias-attribute-declaration.md) Beskriver hur du definierar alias för ett cmdlet-parameter namn.

[Deklaration av cmdlet-attribut](./cmdlet-attribute-declaration.md) Beskriver hur du definierar en .NET Framework-klass som en cmdlet.

[Deklaration för attribut för autentiseringsuppgift](./credential-attribute-declaration.md) Beskriver hur du lägger till stöd för att konvertera inmatade strängar till ett [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -objekt.

[Deklaration av OutputType-attribut](./outputtype-attribute-declaration.md) Beskriver hur du anger de .NET Framework typer som returneras av cmdleten.

[Deklaration av parameter attribut](./parameter-attribute-declaration.md) Beskriver hur du definierar parametrarna för en cmdlet.

[ValidateCount-Attribute-deklaration](./validatecount-attribute-declaration.md) Beskriver hur du definierar hur många argument som tillåts för en parameter.

[ValidateLength-Attribute-deklaration](./validatelength-attribute-declaration.md) Beskriver hur du definierar längden (i tecken) för ett parameter argument.

[ValidatePattern-Attribute-deklaration](./validatepattern-attribute-declaration.md) Beskriver hur du definierar giltiga mönster för ett parameter argument.

[ValidateRange-Attribute-deklaration](./validaterange-attribute-declaration.md) Beskriver hur du definierar ett giltigt intervall för ett parameter argument.

[ValidateSet-Attribute-deklaration](./validateset-attribute-declaration.md) Beskriver hur du definierar möjliga värden för ett parameter argument.

## <a name="reference"></a>Referens

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
