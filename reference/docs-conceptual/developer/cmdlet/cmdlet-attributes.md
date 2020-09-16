---
title: Cmdlet-attribut | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.openlocfilehash: f22c2882fbe5b2f51ca5ea218b921192b0a7d41f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784528"
---
# <a name="cmdlet-attributes"></a>Cmdlet-attribut

Windows PowerShell definierar flera attribut som du kan använda för att lägga till vanliga funktioner i dina cmdletar utan att implementera den funktionen i din egen kod. Detta inkluderar det cmdlet-attribut som identifierar en Microsoft .NET Framework-klass som en cmdlet-klass, attributet OutputType som anger de .NET Framework typer som returneras av cmdleten, attributet parameter som identifierar offentliga egenskaper som cmdlet-parametrar med mera.

## <a name="in-this-section"></a>I det här avsnittet

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
