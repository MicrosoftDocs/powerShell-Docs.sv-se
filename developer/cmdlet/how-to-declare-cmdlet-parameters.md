---
title: Hur du deklarera Cmdlet-parametrarna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067931"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Deklarera cmdlet-parametrar

De här exemplen visar hur du deklarera namngivna, namngivna, obligatorisk, valfri och växla parametrar. De här exemplen visar också hur du definierar ett parameteralias.

## <a name="how-to-declare-a-named-parameter"></a>Hur du deklarera en namngiven Parameter

- Definiera en offentlig egenskap enligt följande kod. När du lägger till parametern-attributet utelämna den `Position` nyckelord från attributet.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Läs mer om parameterattributet [parameterdeklaration för attributet](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-positional-parameter"></a>Hur du deklarera ett namngivna parametern

- Definiera en offentlig egenskap enligt följande kod. När du lägger till parametern-attributet i `Position` nyckelord till argumentet positionen. Värdet 0 anger den första positionen.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Läs mer om parameterattributet [parameterdeklaration för attributet](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-mandatory-parameter"></a>Hur du deklarera en obligatorisk Parameter

- Definiera en offentlig egenskap enligt följande kod. När du lägger till parametern-attributet i `Mandatory` nyckelord till `true`.

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Läs mer om parameterattributet [parameterdeklaration för attributet](./parameter-attribute-declaration.md).

## <a name="how-to-declare-an-optional-parameter"></a>Hur du deklarera en valfri Parameter

- Definiera en offentlig egenskap enligt följande kod. När du lägger till parametern-attributet utelämna den `Mandatory` nyckelord.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>Hur du deklarera ett växlingsparametern

- Definiera en offentlig egenskap som typen [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), och sedan deklarera parametern-attributet.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

Läs mer om parameterattributet [parameterdeklaration för attributet](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-parameter-with-aliases"></a>Hur du deklarera en Parameter med alias

- Definiera en offentlig egenskap enligt följande kod. Lägg till ett Alias-attribut som visas tillgängliga alias för parametern. I det här exemplet definieras tre alias för samma parameter. Det första aliaset innehåller en genväg. Andra och tredje alias ger namn som du kan använda för olika scenarier.

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

Läs mer om attributet Alias [Alias attributet deklarationen](./alias-attribute-declaration.md).

## <a name="see-also"></a>Se även

[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[Attributet parameterdeklaration](./parameter-attribute-declaration.md)

[Aliasdeklaration av attribut](./alias-attribute-declaration.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
