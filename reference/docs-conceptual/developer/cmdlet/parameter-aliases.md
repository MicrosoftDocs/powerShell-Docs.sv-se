---
title: Parameter Ali Aset | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359264"
---
# <a name="parameter-aliases"></a>Parameteralias

Cmdlet-parametrar kan också ha alias. Du kan använda alias i stället för parameter namn när du skriver eller anger en parameter i ett kommando.

## <a name="benefits-of-using-aliases"></a>Fördelar med att använda alias

Att lägga till alias i parametrar ger följande fördelar.

- Du kan ange en genväg så att användaren inte behöver använda det fullständiga parameter namnet när cmdleten anropas. Du kan till exempel använda aliaset "CN" i stället för parameter namnet "ComputerName".

- Du kan definiera flera alias om du vill ange olika namn för samma parameter. Du kanske vill definiera flera alias om du måste arbeta med flera användar grupper som refererar till samma data på olika sätt.

- Du kan ange bakåtkompatibilitet för befintliga skript om namnet på en parameter ändras.

- Genom att använda attributet alias tillsammans med attributet ValueFromPipelineByName kan du definiera en parameter som tillåter att din cmdlet binder till olika objekt typer. Anta till exempel att du har två objekt av olika typer och att det första objektet hade en skrivar egenskap och det andra objektet hade en redigerings egenskap. Om cmdleten hade en parameter som hade Skriv-och redigerings Ali Aset och cmdleten accepterade pipeline-inflöden baserat på egenskaps namn, kan cmdlet: en binda till båda objekten med de två parameter-aliasen.

Mer information om alias som kan användas med vissa parametrar finns i [vanliga parameter namn](./common-parameter-names.md).

## <a name="defining-parameter-aliases"></a>Definiera parameter-alias

Om du vill definiera ett alias för en parameter deklarerar du attributet alias, som du ser i följande parameter deklaration. I det här exemplet definieras flera alias för samma parameter. (Mer information finns i[så här deklarerar du cmdlet-parametrar](./how-to-declare-cmdlet-parameters.md).)

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

[Vanliga parameter namn](./common-parameter-names.md)

[Så här deklarerar du cmdlet-parametrar](./how-to-declare-cmdlet-parameters.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
