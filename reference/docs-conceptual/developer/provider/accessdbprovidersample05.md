---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample05
description: AccessDBProviderSample05
ms.openlocfilehash: ad273720ded0b200530f4f81482d01a8fbb82aa3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92656906"
---
# <a name="accessdbprovidersample05"></a><span data-ttu-id="a5b8d-103">AccessDBProviderSample05</span><span class="sxs-lookup"><span data-stu-id="a5b8d-103">AccessDBProviderSample05</span></span>

<span data-ttu-id="a5b8d-104">Det här exemplet visar hur du skriver över container metoder för att stödja anrop `Move-Item` till `Join-Path` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="a5b8d-104">This sample shows how to overwrite container methods to support calls to the `Move-Item` and `Join-Path` cmdlets.</span></span> <span data-ttu-id="a5b8d-105">Dessa metoder bör implementeras när användaren behöver flytta objekt i en behållare och om data lagret innehåller kapslade behållare.</span><span class="sxs-lookup"><span data-stu-id="a5b8d-105">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span> <span data-ttu-id="a5b8d-106">Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a5b8d-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a5b8d-107">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="a5b8d-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a5b8d-108">Din leverantörs klass kommer förmodligen att härledas från någon av följande klasser och kan eventuellt implementera andra Provider-gränssnitt:</span><span class="sxs-lookup"><span data-stu-id="a5b8d-108">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="a5b8d-109">Klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a5b8d-109">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="a5b8d-110">Se [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="a5b8d-110">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="a5b8d-111">Klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a5b8d-111">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="a5b8d-112">Se [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="a5b8d-112">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="a5b8d-113">Klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a5b8d-113">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="a5b8d-114">Mer information om hur du väljer vilken leverantörs klass som ska härledas från baserat på funktioner i providern finns i [utforma din Windows PowerShell-Provider](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="a5b8d-114">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="a5b8d-115">Det här exemplet demonstrerar följande:</span><span class="sxs-lookup"><span data-stu-id="a5b8d-115">This sample demonstrates the following:</span></span>

- <span data-ttu-id="a5b8d-116">Attributet deklareras `CmdletProvider` .</span><span class="sxs-lookup"><span data-stu-id="a5b8d-116">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="a5b8d-117">Definiera en leverantörs klass som härleds från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a5b8d-117">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

- <span data-ttu-id="a5b8d-118">Skriv över metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) för att ändra beteendet för `Move-Item` cmdleten, så att användaren kan flytta objekt från en plats till en annan.</span><span class="sxs-lookup"><span data-stu-id="a5b8d-118">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method to change the behavior of the `Move-Item` cmdlet, allowing the user to move items from one location to another.</span></span> <span data-ttu-id="a5b8d-119">(Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Move-Item` cmdleten.)</span><span class="sxs-lookup"><span data-stu-id="a5b8d-119">(This sample does not show how to add dynamic parameters to the `Move-Item` cmdlet.)</span></span>

- <span data-ttu-id="a5b8d-120">Skriv över metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) för att ändra funktions sättet för `Join-Path` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a5b8d-120">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to change the behavior of the `Join-Path` cmdlet.</span></span>

- <span data-ttu-id="a5b8d-121">Skriver över metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) .</span><span class="sxs-lookup"><span data-stu-id="a5b8d-121">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method.</span></span>

- <span data-ttu-id="a5b8d-122">Skriver över metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) .</span><span class="sxs-lookup"><span data-stu-id="a5b8d-122">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method.</span></span>

- <span data-ttu-id="a5b8d-123">Skriver över metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) .</span><span class="sxs-lookup"><span data-stu-id="a5b8d-123">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method.</span></span>

- <span data-ttu-id="a5b8d-124">Skriver över metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) .</span><span class="sxs-lookup"><span data-stu-id="a5b8d-124">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method.</span></span>

## <a name="example"></a><span data-ttu-id="a5b8d-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="a5b8d-125">Example</span></span>

<span data-ttu-id="a5b8d-126">Det här exemplet visar hur du skriver över de metoder som behövs för att flytta objekt i en Microsoft Access-databas.</span><span class="sxs-lookup"><span data-stu-id="a5b8d-126">This sample shows how to overwrite the methods needed to move items in a Microsoft Access data base.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="11-1960":::

## <a name="see-also"></a><span data-ttu-id="a5b8d-127">Se även</span><span class="sxs-lookup"><span data-stu-id="a5b8d-127">See Also</span></span>

[<span data-ttu-id="a5b8d-128">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a5b8d-128">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="a5b8d-129">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a5b8d-129">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="a5b8d-130">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a5b8d-130">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="a5b8d-131">Designa en Windows PowerShell-provider</span><span class="sxs-lookup"><span data-stu-id="a5b8d-131">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
