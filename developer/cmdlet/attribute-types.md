---
title: Attributet typer | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56852278"
---
# <a name="attribute-types"></a>Attributtyper

Cmdlet-attribut kan grupperas per funktion.
I följande avsnitt beskrivs tillgängliga attribut och Beskriv vad körningen gör när attributet anropas.

## <a name="cmdlet-attributes"></a>Cmdlet-attribut

### <a name="cmdlet"></a>Cmdlet

Identifierar en .NET Framework-klass som en cmdlet.
Det här är nödvändig basattributet.
Mer information finns i [Cmdlet attributet deklarationen](./cmdlet-attribute-declaration.md).

## <a name="parameter-attributes"></a>Parameterattribut

### <a name="parameter"></a>Parameter

Identifierar en offentlig egenskap i klassen cmdlet som en cmdlet-parameter.
Mer information finns i [parameterdeklaration för attributet](./parameter-attribute-declaration.md).

### <a name="alias"></a>Alias

Anger en eller flera alias för en parameter.
Mer information finns i [Alias attributet deklarationen](./alias-attribute-declaration.md).

## <a name="argument-validation-attributes"></a>Argumentet verifiering attribut

### <a name="validatecount"></a>ValidateCount

Anger minsta och största antalet argument som tillåts för en cmdlet-parameter.
Mer information finns i [ValidateCount attributet deklarationen](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Anger en lägsta och högsta antalet tillåtna tecken för en cmdlet-argument för parametern.
Mer information finns i [ValidateLength attributet deklarationen](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Anger ett mönster för reguljärt uttryck som cmdlet-argument för parametern måste matcha.
Mer information finns i [ValidatePattern attributet deklarationen](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Anger minsta och högsta värden för en cmdlet-argument för parametern.
Mer information finns i [ValidateRange attributet deklarationen](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Anger en uppsättning med giltiga värden för cmdlet-argument för parametern.
Mer information finns i [ValidateSet attributet deklarationen](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
