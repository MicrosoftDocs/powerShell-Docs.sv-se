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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068614"
---
# <a name="cmdlet-attributes"></a>Cmdlet-attribut

Windows PowerShell definierar flera attribut som du kan använda för att lägga till vanliga funktioner i dina cmdlets utan att implementera den funktionen i din egen kod. Detta inkluderar Cmdlet-attributet som identifierar en Microsoft .NET Framework-klass som OutputType-attributet som anger vilka .NET Framework-typer som returneras av cmdlet: en, parameterattributet som identifierar offentliga egenskaper som cmdlet: en cmdlet-klass parametrar och mycket mer.

## <a name="in-this-section"></a>I detta avsnitt

[I Cmdlet-koden](./attributes-in-cmdlet-code.md) beskriver fördelarna med att använda attribut i cmdlet-kod.

[Attributet typer](./attribute-types.md) beskrivs olika attribut som kan anpassa en cmdlet-klass.

[Alias attributet deklarationen](./alias-attribute-declaration.md) beskriver hur du definierar alias för en cmdlet-namn för parametern.

[Cmdlet: en deklaration av attribut](./cmdlet-attribute-declaration.md) beskriver hur du definierar en .NET Framework-klass som en cmdlet.

[Autentiseringsuppgifter för attributet deklarationen](./credential-attribute-declaration.md) beskriver hur du lägger till stöd för att konvertera strängen mata in en [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) objekt.

[OutputType-attributet deklarationen](./outputtype-attribute-declaration.md) beskriver hur du anger .NET Framework-typer som returneras av cmdlet: en.

[Attributet parameterdeklaration](./parameter-attribute-declaration.md) beskriver hur du definierar parametrar för en cmdlet.

[ValidateCount attributet deklarationen](./validatecount-attribute-declaration.md) beskriver hur du definierar hur många argument är tillåtna för en parameter.

[ValidateLength attributet deklarationen](./validatelength-attribute-declaration.md) beskriver hur du definierar längden (i antal tecken) för en Parameterargumentet.

[ValidatePattern attributet deklarationen](./validatepattern-attribute-declaration.md) beskriver hur du definierar de giltiga mönster för ett argument för parametern.

[ValidateRange attributet deklarationen](./validaterange-attribute-declaration.md) beskriver hur du definierar det giltiga intervallet för ett argument för parametern.

[ValidateSet attributet deklarationen](./validateset-attribute-declaration.md) beskriver hur du definierar de möjliga värdena för ett argument för parametern.

## <a name="reference"></a>Referens

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
