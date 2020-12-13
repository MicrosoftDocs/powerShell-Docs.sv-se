---
ms.date: 09/13/2016
ms.topic: reference
title: Deklarera cmdlet-parametrar
description: Deklarera cmdlet-parametrar
ms.openlocfilehash: ed53f9788c9afb142b137e08966dff33551b9d0f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667104"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Deklarera cmdlet-parametrar

I de här exemplen visas hur du deklarerar namngivna, positionerade, obligatoriska, valfria och växla parametrar. De här exemplen visar också hur du definierar ett parameter Ali Aset.

## <a name="how-to-declare-a-named-parameter"></a>Så här deklarerar du en namngiven parameter

- Definiera en offentlig egenskap som visas i följande kod. När du lägger till attributet parameter utelämnar du `Position` nyckelordet från attributet.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Mer information om attributet parameter finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-positional-parameter"></a>Så här deklarerar du en positions parameter

- Definiera en offentlig egenskap som visas i följande kod. När du lägger till attributet parameter anger du `Position` nyckelordet till argument positionen. Värdet 0 anger den första positionen.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Mer information om attributet parameter finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-mandatory-parameter"></a>Så här deklarerar du en obligatorisk parameter

- Definiera en offentlig egenskap som visas i följande kod. När du lägger till attributet parameter anger du `Mandatory` nyckelordet till `true` .

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Mer information om attributet parameter finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).

## <a name="how-to-declare-an-optional-parameter"></a>Så här deklarerar du en valfri parameter

- Definiera en offentlig egenskap som visas i följande kod. När du lägger till attributet parameter utelämnar du `Mandatory` nyckelordet.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>Så här deklarerar du en växel parameter

- Definiera en offentlig egenskap som typ [system. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)och deklarera sedan attributet parameter.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

Mer information om attributet parameter finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-parameter-with-aliases"></a>Så här deklarerar du en parameter med alias

- Definiera en offentlig egenskap som visas i följande kod. Lägg till ett alias som visar ett alias för parametern. I det här exemplet definieras tre alias för samma parameter. Det första aliaset innehåller en genväg. Det andra och tredje aliaset ger namn som du kan använda för olika scenarier.

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

Mer information om alias-attributet finns i [deklarationen alias](./alias-attribute-declaration.md).

## <a name="see-also"></a>Se även

[System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[Deklaration av attributet Parameter](./parameter-attribute-declaration.md)

[Deklaration av attributet Alias](./alias-attribute-declaration.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
