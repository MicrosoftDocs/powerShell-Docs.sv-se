---
title: Attributtyper | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355631"
---
# <a name="attribute-types"></a>Attributtyper

Cmdlet-attribut kan grupperas efter funktionalitet.
I följande avsnitt beskrivs tillgängliga attribut och hur du kan beskriva vad körningen gör när attributet anropas.

## <a name="cmdlet-attributes"></a>Cmdlet-attribut

### <a name="cmdlet"></a>Cmdlet

Identifierar en .NET Framework-klass som en cmdlet.
Detta är det grundläggande attributet som krävs.
Mer information finns i [deklaration av cmdlet-attribut](./cmdlet-attribute-declaration.md).

## <a name="parameter-attributes"></a>Parameter-attribut

### <a name="parameter"></a>Parameter

Identifierar en offentlig egenskap i cmdlet-klassen som en cmdlet-parameter.
Mer information finns i [deklaration av parameter attribut](./parameter-attribute-declaration.md).

### <a name="alias"></a>Alias

Anger ett eller flera alias för en parameter.
Mer information finns i [deklaration för alias](./alias-attribute-declaration.md).

## <a name="argument-validation-attributes"></a>Attribut för argument verifiering

### <a name="validatecount"></a>ValidateCount

Anger det lägsta och högsta antalet argument som tillåts för en cmdlet-parameter.
Mer information finns i [ValidateCount Attribute-deklaration](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Anger ett minsta och högsta antal tecken för ett cmdlet parameter argument.
Mer information finns i [ValidateLength Attribute-deklaration](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Anger ett mönster för reguljära uttryck som argumentet cmdlet-parameter måste matcha.
Mer information finns i [ValidatePattern Attribute-deklaration](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Anger det lägsta och högsta värdet för ett cmdlet parameter argument.
Mer information finns i [ValidateRange Attribute-deklaration](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Anger en uppsättning giltiga värden för argumentet cmdlet-parameter.
Mer information finns i [ValidateSet Attribute-deklaration](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
