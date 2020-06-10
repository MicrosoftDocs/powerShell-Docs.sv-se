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
ms.openlocfilehash: 5d738de60bc47d000377779ee4e564bff4ad31ad
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633438"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="8258d-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="8258d-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="8258d-103">Det här exemplet visar hur du deklarerar en leverantörs klass som härleds direkt från klassen [system. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="8258d-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="8258d-104">Den ingår bara här för fullständighet.</span><span class="sxs-lookup"><span data-stu-id="8258d-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8258d-105">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="8258d-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8258d-106">Din leverantörs klass kommer förmodligen att härledas från någon av följande klasser och kan eventuellt implementera andra Provider-gränssnitt:</span><span class="sxs-lookup"><span data-stu-id="8258d-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="8258d-107">Klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="8258d-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="8258d-108">Se [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="8258d-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="8258d-109">Klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="8258d-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="8258d-110">Se [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="8258d-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="8258d-111">Klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="8258d-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="8258d-112">Se [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="8258d-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="8258d-113">Mer information om hur du väljer vilken leverantörs klass som ska härledas från baserat på funktioner i providern finns i [utforma din Windows PowerShell-Provider](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="8258d-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="8258d-114">Det här exemplet demonstrerar följande:</span><span class="sxs-lookup"><span data-stu-id="8258d-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="8258d-115">Attributet deklareras `CmdletProvider` .</span><span class="sxs-lookup"><span data-stu-id="8258d-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="8258d-116">Definiera en leverantörs klass som härleds direkt från klassen [system. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="8258d-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="8258d-117">Exempel</span><span class="sxs-lookup"><span data-stu-id="8258d-117">Example</span></span>

<span data-ttu-id="8258d-118">Det här exemplet visar hur du definierar en provider-klass och hur du deklarerar `CmdletProvider` attributet.</span><span class="sxs-lookup"><span data-stu-id="8258d-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="8258d-119">Se även</span><span class="sxs-lookup"><span data-stu-id="8258d-119">See Also</span></span>

[<span data-ttu-id="8258d-120">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="8258d-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="8258d-121">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="8258d-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="8258d-122">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="8258d-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="8258d-123">Designa en Windows PowerShell-provider</span><span class="sxs-lookup"><span data-stu-id="8258d-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
