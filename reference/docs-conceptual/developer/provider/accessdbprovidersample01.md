---
title: AccessDBProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: 67c2b6cfd36a805fce25bf0c7c55db56ec14092c
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83690916"
---
# <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

Det här exemplet visar hur du deklarerar en leverantörs klass som härleds direkt från klassen [system. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . Den ingår bara här för fullständighet.

## <a name="demonstrates"></a>Demonstrationer

> [!IMPORTANT]
> Din leverantörs klass kommer förmodligen att härledas från någon av följande klasser och kan eventuellt implementera andra Provider-gränssnitt:
>
> - Klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Se [AccessDBProviderSample03](./accessdbprovidersample03.md).
> - Klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Se [AccessDBProviderSample04](./accessdbprovidersample04.md).
> - Klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Se [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Mer information om hur du väljer vilken leverantörs klass som ska härledas från baserat på funktioner i providern finns i [utforma din Windows PowerShell-Provider](./provider-types.md).

Det här exemplet demonstrerar följande:

- Attributet deklareras `CmdletProvider` .

- Definiera en leverantörs klass som härleds direkt från klassen [system. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .

## <a name="example"></a>Exempel

Det här exemplet visar hur du definierar en provider-klass och hur du deklarerar `CmdletProvider` attributet.

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a>Se även

[System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Designa en Windows PowerShell-provider](./provider-types.md)
