---
title: Attributet parameterdeklaration | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067560"
---
# <a name="parameter-attribute-declaration"></a>Deklaration av attributet Parameter

Parameterattributet identifierar en offentlig egenskap för klassen cmdlet som en cmdlet-parameter.

## <a name="syntax"></a>Syntax

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parametrar

`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) valfritt med namnet parametern. `True` Visar den cmdlet-parametern krävs. Om en obligatorisk parameter inte anges när cmdleten har anropats, frågar Windows PowerShell användaren om ett parametervärde. Standardvärdet är `false`.

`ParameterSetName` ([System.String](/dotnet/api/System.String)) valfritt med namnet parametern. Anger parametern anger att den här cmdlet-parameter som tillhör. Om inga parameteruppsättningen anges tillhör parametern alla parameteruppsättningar.

`Position` ([System.Integer](/dotnet/api/System.Integer)) valfritt med namnet parametern. Anger positionen för parameter i ett Windows PowerShell-kommando.

`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) valfritt med namnet parametern. `True` Anger att cmdlet-parameter tar dess värde från ett pipeline-objekt. Ange det här nyckelordet om cmdlet: en har åtkomst till hela objektet, inte bara en egenskap för objektet. Standardvärdet är `false`.

`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) valfritt med namnet parametern. `True` Anger att cmdlet-parameter tar dess värde från en egenskap för en pipeline-objekt som har samma namn eller samma alias som den här parametern. Om cmdleten har till exempel en `Name` parametern och pipeline-objektet har också en `Name` egenskap, värdet för den `Name` egenskapen tilldelas den `Name` parametern för cmdlet. Standardvärdet är `false`.

`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) valfritt med namnet parametern. `True` Anger att cmdlet-parameter godkänner alla återstående argument som skickas till cmdleten. Standardvärdet är `false`.

`HelpMessage` Valfritt med namnet parametern. Anger en kort beskrivning av parametern. Windows PowerShell visar det här meddelandet när en cmdlet körs och en obligatorisk parameter har angetts.

`HelpMessageBaseName` Valfritt med namnet parametern. Anger den plats där resursidentifierare finns. Den här parametern kan till exempel ange en resurs sammansättning som innehåller hjälpmeddelanden som du vill lokalisera.

`HelpMessageResourceId` Valfritt med namnet parametern. Anger resurs-ID för ett hjälpmeddelande.

## <a name="remarks"></a>Anmärkningar

- Läs mer om hur du deklarera det här attributet [så deklarera Cmdlet-parametrarna](./how-to-declare-cmdlet-parameters.md).

- En cmdlet kan ha valfritt antal parametrar. Dock begränsa antalet parametrar för en bättre användarupplevelse.

- Parametrar måste deklareras i offentliga icke-statiska fält eller egenskaper. Parametrar måste deklareras i egenskaper. Egenskapen måste ha en offentlig uppsättning accessor och om den `ValueFromPipeline` eller `ValueFromPipelineByPropertyName` nyckelord har angetts, egenskapen måste ha en offentlig läsaccessor.

- När du anger namngivna parametrar kan du begränsa antalet namngivna parametrar i en parameteruppsättning på mindre än fem. Och namngivna parametrar behöver inte vara sammanhängande. Positioner 5, 100 och 250 fungerar på samma sätt som positioner 0, 1 och 2.

- När den `Position` nyckelordet inte anges, cmdlet-parameter måste refereras av dess namn.

- När du använder parameteruppsättningar, Tänk på följande:

    - Varje parameteruppsättningen måste ha minst en unik parameter. Cmdlet: en bra design anger den här unika parametern också vara obligatorisk om möjligt. Om din cmdlet: en är avsedd att köras utan parametrar, får inte unika parametern vara obligatorisk.

    - Inga parameteruppsättningen ska innehålla mer än en namngivna parametern med samma plats.

    - Endast en parameter i en parameteruppsättning bör deklarera `ValueFromPipeline = true`. Flera parametrar kan definiera `ValueFromPipelineByPropertyName = true`.

    - Flera parametrar kan definiera `ValueFromPipelineByPropertyName = true`.

- Läs mer om riktlinjerna för parameternamn, [Cmdlet parameternamn](standard-cmdlet-parameter-names-and-types.md).

- Parameterattributet definieras av den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) klass.

## <a name="see-also"></a>Se även

[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Cmdlet-parameternamn](standard-cmdlet-parameter-names-and-types.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
