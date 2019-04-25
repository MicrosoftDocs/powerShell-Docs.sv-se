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
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081129"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="dab57-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="dab57-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="dab57-103">Det här exemplet visar hur du deklarera en providerklass som härleds direkt från den [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="dab57-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="dab57-104">Det är här ingår endast för fullständighetens skull.</span><span class="sxs-lookup"><span data-stu-id="dab57-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="dab57-105">Visar</span><span class="sxs-lookup"><span data-stu-id="dab57-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dab57-106">Din providerklass kommer troligen härleder från en av följande klasser och eventuellt implementera andra provider-gränssnitt:</span><span class="sxs-lookup"><span data-stu-id="dab57-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="dab57-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="dab57-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="dab57-108">Se [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="dab57-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="dab57-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="dab57-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="dab57-110">Se [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="dab57-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="dab57-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="dab57-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="dab57-112">Se [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="dab57-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="dab57-113">Mer information om hur du väljer vilken providerklass som härleds från baserat på provider-funktioner kan du läsa [designa din Windows PowerShell-providern](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="dab57-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="dab57-114">Detta exempel visar följande:</span><span class="sxs-lookup"><span data-stu-id="dab57-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="dab57-115">Deklarera de `CmdletProvider` attribut.</span><span class="sxs-lookup"><span data-stu-id="dab57-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="dab57-116">Definiera en providerklass som härleds direkt från den [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="dab57-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="dab57-117">Exempel</span><span class="sxs-lookup"><span data-stu-id="dab57-117">Example</span></span>

<span data-ttu-id="dab57-118">Det här exemplet visar hur du definierar en providerklass och hur du deklarera den `CmdletProvider` attribut.</span><span class="sxs-lookup"><span data-stu-id="dab57-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dab57-119">Se även</span><span class="sxs-lookup"><span data-stu-id="dab57-119">See Also</span></span>

[<span data-ttu-id="dab57-120">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="dab57-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="dab57-121">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="dab57-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="dab57-122">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="dab57-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="dab57-123">Designa din Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="dab57-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)