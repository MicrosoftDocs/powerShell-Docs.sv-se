---
title: AccessDBProviderSample05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a26661f2-a63c-4ca7-ad3e-dcb4d32ce5a1
caps.latest.revision: 8
ms.openlocfilehash: 43d18672ec4f52961b2a2460635468a2d6fb41e5
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633387"
---
# <a name="accessdbprovidersample05"></a><span data-ttu-id="c5e47-102">AccessDBProviderSample05</span><span class="sxs-lookup"><span data-stu-id="c5e47-102">AccessDBProviderSample05</span></span>

<span data-ttu-id="c5e47-103">Det här exemplet visar hur du skriver över container metoder för att stödja anrop `Move-Item` till `Join-Path` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="c5e47-103">This sample shows how to overwrite container methods to support calls to the `Move-Item` and `Join-Path` cmdlets.</span></span> <span data-ttu-id="c5e47-104">Dessa metoder bör implementeras när användaren behöver flytta objekt i en behållare och om data lagret innehåller kapslade behållare.</span><span class="sxs-lookup"><span data-stu-id="c5e47-104">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span> <span data-ttu-id="c5e47-105">Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="c5e47-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c5e47-106">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="c5e47-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c5e47-107">Din leverantörs klass kommer förmodligen att härledas från någon av följande klasser och kan eventuellt implementera andra Provider-gränssnitt:</span><span class="sxs-lookup"><span data-stu-id="c5e47-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="c5e47-108">Klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="c5e47-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="c5e47-109">Se [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="c5e47-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="c5e47-110">Klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="c5e47-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="c5e47-111">Se [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="c5e47-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="c5e47-112">Klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="c5e47-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="c5e47-113">Mer information om hur du väljer vilken leverantörs klass som ska härledas från baserat på funktioner i providern finns i [utforma din Windows PowerShell-Provider](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="c5e47-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="c5e47-114">Det här exemplet demonstrerar följande:</span><span class="sxs-lookup"><span data-stu-id="c5e47-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="c5e47-115">Attributet deklareras `CmdletProvider` .</span><span class="sxs-lookup"><span data-stu-id="c5e47-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="c5e47-116">Definiera en leverantörs klass som härleds från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="c5e47-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

- <span data-ttu-id="c5e47-117">Skriv över metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) för att ändra beteendet för `Move-Item` cmdleten, så att användaren kan flytta objekt från en plats till en annan.</span><span class="sxs-lookup"><span data-stu-id="c5e47-117">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method to change the behavior of the `Move-Item` cmdlet, allowing the user to move items from one location to another.</span></span> <span data-ttu-id="c5e47-118">(Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Move-Item` cmdleten.)</span><span class="sxs-lookup"><span data-stu-id="c5e47-118">(This sample does not show how to add dynamic parameters to the `Move-Item` cmdlet.)</span></span>

- <span data-ttu-id="c5e47-119">Skriv över metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) för att ändra funktions sättet för `Join-Path` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c5e47-119">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to change the behavior of the `Join-Path` cmdlet.</span></span>

- <span data-ttu-id="c5e47-120">Skriver över metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) .</span><span class="sxs-lookup"><span data-stu-id="c5e47-120">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method.</span></span>

- <span data-ttu-id="c5e47-121">Skriver över metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) .</span><span class="sxs-lookup"><span data-stu-id="c5e47-121">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method.</span></span>

- <span data-ttu-id="c5e47-122">Skriver över metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) .</span><span class="sxs-lookup"><span data-stu-id="c5e47-122">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method.</span></span>

- <span data-ttu-id="c5e47-123">Skriver över metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) .</span><span class="sxs-lookup"><span data-stu-id="c5e47-123">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method.</span></span>

## <a name="example"></a><span data-ttu-id="c5e47-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="c5e47-124">Example</span></span>

<span data-ttu-id="c5e47-125">Det här exemplet visar hur du skriver över de metoder som behövs för att flytta objekt i en Microsoft Access-databas.</span><span class="sxs-lookup"><span data-stu-id="c5e47-125">This sample shows how to overwrite the methods needed to move items in a Microsoft Access data base.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="11-1960":::

## <a name="see-also"></a><span data-ttu-id="c5e47-126">Se även</span><span class="sxs-lookup"><span data-stu-id="c5e47-126">See Also</span></span>

[<span data-ttu-id="c5e47-127">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="c5e47-127">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="c5e47-128">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="c5e47-128">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="c5e47-129">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="c5e47-129">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="c5e47-130">Designa en Windows PowerShell-provider</span><span class="sxs-lookup"><span data-stu-id="c5e47-130">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
