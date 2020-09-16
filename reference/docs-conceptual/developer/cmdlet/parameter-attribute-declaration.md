---
title: Deklaration av parameter-attribut | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.openlocfilehash: 55b157b93c3a42324d63e16ddfa8db1f0d38f82b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781859"
---
# <a name="parameter-attribute-declaration"></a>Deklaration av attributet Parameter

Attributet parameter identifierar en offentlig egenskap för cmdlet-klassen som en cmdlet-parameter.

## <a name="syntax"></a>Syntax

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parametrar

`Mandatory` ([System. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter. `True` anger att cmdlet-parametern är obligatorisk. Om en obligatorisk parameter inte anges när cmdleten anropas, uppmanas användaren att ange ett parameter värde i Windows PowerShell. Standardvärdet är `false`.

`ParameterSetName` ([System. String](/dotnet/api/System.String)) valfri namngiven parameter. Anger den parameter uppsättning som denna cmdlet-parameter tillhör. Om ingen parameter uppsättning anges tillhör parametern alla parameter uppsättningar.

`Position` ([System. Int32](/dotnet/api/System.Int32)) valfri namngiven parameter. Anger positionen för parametern i ett Windows PowerShell-kommando.

`ValueFromPipeline` ([System. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter. `True` anger att cmdlet-parametern tar sitt värde från ett pipeline-objekt. Ange det här nyckelordet om cmdleten har åtkomst till det fullständiga objektet, inte bara en egenskap för objektet. Standardvärdet är `false`.

`ValueFromPipelineByPropertyName` ([System. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter. `True` anger att cmdlet-parametern tar värdet från en egenskap för ett pipeline-objekt som har antingen samma namn eller samma alias som denna parameter. Om till exempel cmdleten har en `Name` parameter och pipelinen också har en `Name` egenskap, tilldelas värdet för `Name` egenskapen till `Name` parametern för cmdleten. Standardvärdet är `false`.

`ValueFromRemainingArguments` ([System. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter. `True` anger att cmdlet-parametern accepterar alla återstående argument som skickas till cmdleten. Standardvärdet är `false`.

`HelpMessage` Valfri namngiven parameter. Anger en kort beskrivning av parametern. Windows PowerShell visar det här meddelandet när en cmdlet körs och en obligatorisk parameter inte har angetts.

`HelpMessageBaseName` Valfri namngiven parameter. Anger den plats där resurs identifierare finns. Den här parametern kan till exempel ange en resurs sammansättning som innehåller hjälp meddelanden som du vill lokalisera.

`HelpMessageResourceId` Valfri namngiven parameter. Anger resurs-ID för ett hjälp meddelande.

## <a name="remarks"></a>Kommentarer

- Mer information om hur du deklarerar det här attributet finns i [så här deklarerar du cmdlet-parametrar](./how-to-declare-cmdlet-parameters.md).

- En cmdlet kan ha valfritt antal parametrar. För en bättre användar upplevelse begränsar du dock antalet parametrar.

- Parametrar måste deklareras för offentliga fält eller egenskaper som inte är statiska. Parametrar ska deklareras för egenskaper. Egenskapen måste ha en offentlig set-accessor, och om `ValueFromPipeline` `ValueFromPipelineByPropertyName` nyckelordet eller har angetts måste egenskapen ha en offentlig get-accessor.

- Om du anger positions parametrar begränsar du antalet positions parametrar i en parameter till mindre än fem. Positions parametrar behöver inte vara sammanhängande. Positionerna 5, 100 och 250 fungerar på samma sätt som positionerna 0, 1 och 2.

- Om `Position` nyckelordet inte anges måste cmdlet-parametern refereras till med dess namn.

- Tänk på följande när du använder parameter uppsättningar:

  - Varje parameter uppsättning måste ha minst en unik parameter. Design av lämplig cmdlet anger att den här unika parametern också bör vara obligatorisk om möjligt. Om cmdleten har utformats för att köras utan parametrar kan den unika parametern inte vara obligatorisk.

  - Ingen parameter uppsättning måste innehålla mer än en positions parameter med samma position.

  - Endast en parameter i en parameter uppsättning bör deklarera `ValueFromPipeline = true` . Flera parametrar kan definieras `ValueFromPipelineByPropertyName = true` .

  - Flera parametrar kan definieras `ValueFromPipelineByPropertyName = true` .

- Mer information om rikt linjerna för parameter namn finns i [cmdlet parameter Names](standard-cmdlet-parameter-names-and-types.md).

- Attributet parameter definieras av klassen [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .

## <a name="see-also"></a>Se även

[System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Parameter namn för cmdlet](standard-cmdlet-parameter-names-and-types.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
