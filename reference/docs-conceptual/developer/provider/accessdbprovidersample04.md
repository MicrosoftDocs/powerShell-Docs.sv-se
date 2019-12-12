---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: 7096f8066568c214a5902f6943a2c093932d3b56
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356863"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="d2e07-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="d2e07-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="d2e07-103">Det här exemplet visar hur du skriver över container metoder för att stödja anrop till `Copy-Item`-, `Get-ChildItem`-, `New-Item`-och `Remove-Item`-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="d2e07-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="d2e07-104">Dessa metoder bör implementeras när data lagret innehåller objekt som är behållare.</span><span class="sxs-lookup"><span data-stu-id="d2e07-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="d2e07-105">En behållare är en grupp underordnade objekt under ett gemensamt överordnat objekt.</span><span class="sxs-lookup"><span data-stu-id="d2e07-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="d2e07-106">Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="d2e07-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d2e07-107">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="d2e07-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d2e07-108">Din leverantörs klass kommer förmodligen att härledas från [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="d2e07-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="d2e07-109">Det här exemplet demonstrerar följande:</span><span class="sxs-lookup"><span data-stu-id="d2e07-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="d2e07-110">Deklarera `CmdletProvider`-attributet.</span><span class="sxs-lookup"><span data-stu-id="d2e07-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="d2e07-111">Definiera en leverantörs klass som härleds från klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="d2e07-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="d2e07-112">Skriv över metoden [system. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) för att ändra beteendet för `Copy-Item` cmdleten så att användaren kan kopiera objekt från en plats till en annan.</span><span class="sxs-lookup"><span data-stu-id="d2e07-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="d2e07-113">(Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Copy-Item`-cmdleten.)</span><span class="sxs-lookup"><span data-stu-id="d2e07-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="d2e07-114">Skriv över metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) för att ändra beteendet för Get-ChildItems-cmdleten, vilket gör att användaren kan hämta de underordnade objekten till det överordnade objektet.</span><span class="sxs-lookup"><span data-stu-id="d2e07-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="d2e07-115">(Det här exemplet visar inte hur du lägger till dynamiska parametrar till get-ChildItems-cmdlet: en.)</span><span class="sxs-lookup"><span data-stu-id="d2e07-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="d2e07-116">Skriv över metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) för att ändra beteendet för Get-ChildItems-cmdleten när parametern `Name` för cmdlet: en anges.</span><span class="sxs-lookup"><span data-stu-id="d2e07-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="d2e07-117">Skriv över metoden [system. Management. Automation. Provider. Containercmdletprovider. NewItem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) för att ändra beteendet för `New-Item`-cmdleten, vilket gör att användaren kan lägga till objekt i data lagret.</span><span class="sxs-lookup"><span data-stu-id="d2e07-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="d2e07-118">(Det här exemplet visar inte hur du lägger till dynamiska parametrar i `New-Item`-cmdleten.)</span><span class="sxs-lookup"><span data-stu-id="d2e07-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="d2e07-119">Skriv över metoden [system. Management. Automation. Provider. Containercmdletprovider. RemoveItem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) för att ändra beteendet för `Remove-Item`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d2e07-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="d2e07-120">(Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Remove-Item`-cmdleten.)</span><span class="sxs-lookup"><span data-stu-id="d2e07-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="d2e07-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2e07-121">Example</span></span>

<span data-ttu-id="d2e07-122">Det här exemplet visar hur du skriver över de metoder som behövs för att kopiera, skapa och ta bort objekt, samt metoder för att hämta underordnade objekt till ett överordnat objekt.</span><span class="sxs-lookup"><span data-stu-id="d2e07-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="d2e07-123">Se även</span><span class="sxs-lookup"><span data-stu-id="d2e07-123">See Also</span></span>

[<span data-ttu-id="d2e07-124">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="d2e07-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="d2e07-125">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="d2e07-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="d2e07-126">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="d2e07-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="d2e07-127">Designa din Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="d2e07-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
