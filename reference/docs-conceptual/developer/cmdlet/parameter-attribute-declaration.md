---
title: Deklaration av parameter-attribut | Microsoft Docs
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
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356177"
---
# <a name="parameter-attribute-declaration"></a>Deklaration av attributet Parameter

Attributet parameter identifierar en offentlig egenskap för cmdlet-klassen som en cmdlet-parameter.

## <a name="syntax"></a>Syntax

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parametrar

`Mandatory` ([system. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter. `True` anger att cmdlet-parametern krävs. Om en obligatorisk parameter inte anges när cmdleten anropas, uppmanas användaren att ange ett parameter värde i Windows PowerShell. Standardvärdet är `false`.

`ParameterSetName` ([system. String](/dotnet/api/System.String)) valfri namngiven parameter. Anger den parameter uppsättning som denna cmdlet-parameter tillhör. Om ingen parameter uppsättning anges tillhör parametern alla parameter uppsättningar.

`Position` ([system. Int32](/dotnet/api/System.Int32)) valfri namngiven parameter. Anger positionen för parametern i ett Windows PowerShell-kommando.

`ValueFromPipeline` ([system. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter. `True` anger att cmdlet-parametern tar sitt värde från ett pipeline-objekt. Ange det här nyckelordet om cmdleten har åtkomst till det fullständiga objektet, inte bara en egenskap för objektet. Standardvärdet är `false`.

`ValueFromPipelineByPropertyName` ([system. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter. `True` anger att cmdlet-parametern tar värdet från en egenskap för ett pipeline-objekt som har antingen samma namn eller samma alias som denna parameter. Om till exempel cmdleten har en `Name`-parameter och pipelinen också har en `Name`-egenskap, tilldelas värdet för egenskapen `Name` till parametern `Name` för cmdleten. Standardvärdet är `false`.

`ValueFromRemainingArguments` ([system. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter. `True` anger att cmdlet-parametern accepterar alla återstående argument som skickas till cmdleten. Standardvärdet är `false`.

`HelpMessage` valfri namngiven parameter. Anger en kort beskrivning av parametern. Windows PowerShell visar det här meddelandet när en cmdlet körs och en obligatorisk parameter inte har angetts.

`HelpMessageBaseName` valfri namngiven parameter. Anger den plats där resurs identifierare finns. Den här parametern kan till exempel ange en resurs sammansättning som innehåller hjälp meddelanden som du vill lokalisera.

`HelpMessageResourceId` valfri namngiven parameter. Anger resurs-ID för ett hjälp meddelande.

## <a name="remarks"></a>Anmärkningar

- Mer information om hur du deklarerar det här attributet finns i [så här deklarerar du cmdlet-parametrar](./how-to-declare-cmdlet-parameters.md).

- En cmdlet kan ha valfritt antal parametrar. För en bättre användar upplevelse begränsar du dock antalet parametrar.

- Parametrar måste deklareras för offentliga fält eller egenskaper som inte är statiska. Parametrar ska deklareras för egenskaper. Egenskapen måste ha en offentlig set-accessor och om nyckelordet `ValueFromPipeline` eller `ValueFromPipelineByPropertyName` har angetts måste egenskapen ha en offentlig get-accessor.

- Om du anger positions parametrar begränsar du antalet positions parametrar i en parameter till mindre än fem. Positions parametrar behöver inte vara sammanhängande. Positionerna 5, 100 och 250 fungerar på samma sätt som positionerna 0, 1 och 2.

- Om nyckelordet `Position` inte anges, måste cmdlet-parametern refereras av dess namn.

- Tänk på följande när du använder parameter uppsättningar:

    - Varje parameter uppsättning måste ha minst en unik parameter. Design av lämplig cmdlet anger att den här unika parametern också bör vara obligatorisk om möjligt. Om cmdleten har utformats för att köras utan parametrar kan den unika parametern inte vara obligatorisk.

    - Ingen parameter uppsättning måste innehålla mer än en positions parameter med samma position.

    - Endast en parameter i en parameter uppsättning bör deklarera `ValueFromPipeline = true`. Flera parametrar kan definiera `ValueFromPipelineByPropertyName = true`.

    - Flera parametrar kan definiera `ValueFromPipelineByPropertyName = true`.

- Mer information om rikt linjerna för parameter namn finns i [cmdlet parameter Names](standard-cmdlet-parameter-names-and-types.md).

- Attributet parameter definieras av klassen [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .

## <a name="see-also"></a>Se även

[System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Parameter namn för cmdlet](standard-cmdlet-parameter-names-and-types.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
