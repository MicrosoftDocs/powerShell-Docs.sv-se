---
title: Parameteralias | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067594"
---
# <a name="parameter-aliases"></a>Parameteralias

Cmdlet-parametrarna kan också ha alias. Du kan använda alias i stället för i parameternamnen när du skriver eller ange parametern i ett kommando.

## <a name="benefits-of-using-aliases"></a>Fördelarna med att använda alias

Att lägga till alias i Parametrar ger följande fördelar.

- Du kan ange en genväg så att användaren inte behöver använda det fullständiga parameternamnet när cmdlet anropas. Du kan exempelvis använda aliaset ”CN” i stället för parameternamnet ”datornamn”.

- Du kan definiera flera alias om du vill ge olika namn för samma parameter. Du kanske vill definiera flera alias om du ska arbeta med flera användargrupper som refererar till samma data på olika sätt.

- Du kan ge bakåtkompatibilitet kompatibilitet för befintliga skript om namnet på en parameter ändras.

- Genom att använda attributet Alias tillsammans med attributet ValueFromPipelineByName kan definiera du en parameter för cmdlet: att binda till olika objekttyper. Anta exempelvis att du har två objekt av olika typer och det första objektet hade en skrivare egenskap och det andra objektet hade en redigerare-egenskap. Om din cmdlet hade en parameter som hade skrivaren och redigerare alias och cmdleten accepterat indata från pipeline i egenskapsnamn, cmdlet: kan bindas till båda objekt med hjälp av två parameteralias.

Mer information om alias som kan användas med specifika parametrar finns i [vanliga parameternamn](./common-parameter-names.md).

## <a name="defining-parameter-aliases"></a>Definiera Parameteralias

Deklarera Alias-attributet för att definiera ett alias för en parameter, enligt följande parameterdeklaration. I det här exemplet definieras flera alias för samma parameter. (Mer information finns i[så deklarera Cmdlet-parametrarna](./how-to-declare-cmdlet-parameters.md).)

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a>Se även

[Vanliga parameternamn](./common-parameter-names.md)

[Hur du deklarera Cmdlet-parametrarna](./how-to-declare-cmdlet-parameters.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
