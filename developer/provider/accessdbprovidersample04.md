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
ms.openlocfilehash: fd013384a4b588bcdb397d7771425fe5c031c48f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847301"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="472bf-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="472bf-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="472bf-103">Det här exemplet visas hur du skriver över behållare metoder för att stödja anrop till den `Copy-Item`, `Get-ChildItem`, `New-Item`, och `Remove-Item` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="472bf-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="472bf-104">Dessa metoder bör implementeras när datalagret innehåller objekt som är behållare.</span><span class="sxs-lookup"><span data-stu-id="472bf-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="472bf-105">En behållare är en grupp med underordnade objekt under en gemensam överordnad artikel.</span><span class="sxs-lookup"><span data-stu-id="472bf-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="472bf-106">Providerklass i det här exemplet kommer från den [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="472bf-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="472bf-107">Visar</span><span class="sxs-lookup"><span data-stu-id="472bf-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="472bf-108">Din providerklass kommer troligen härleds från den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="472bf-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="472bf-109">Detta exempel visar följande:</span><span class="sxs-lookup"><span data-stu-id="472bf-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="472bf-110">Deklarera de `CmdletProvider` attribut.</span><span class="sxs-lookup"><span data-stu-id="472bf-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="472bf-111">Definiera en providerklass som härleds från den [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="472bf-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="472bf-112">Skriver över den [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) metod för att ändra funktionssättet för den `Copy-Item` cmdlet som används att kopiera objekt från en plats till en annan.</span><span class="sxs-lookup"><span data-stu-id="472bf-112">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="472bf-113">(Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Copy-Item` cmdlet: en.)</span><span class="sxs-lookup"><span data-stu-id="472bf-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="472bf-114">Skriver över den [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metod för att ändra funktionssättet för cmdleten Get-ChildItems, vilket gör att användaren kan hämta de underordnade objekten i den överordnade artikeln .</span><span class="sxs-lookup"><span data-stu-id="472bf-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="472bf-115">(Det här exemplet visar inte hur du lägger till dynamiska parametrar för cmdleten Get-ChildItems.)</span><span class="sxs-lookup"><span data-stu-id="472bf-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="472bf-116">Skriver över den [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metod för att ändra funktionssättet för cmdleten Get-ChildItems när den `Name` parametern för cmdlet har angetts.</span><span class="sxs-lookup"><span data-stu-id="472bf-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="472bf-117">Skriver över den [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metod för att ändra funktionssättet för den `New-Item` cmdleten, som gör att användaren kan lägga till objekt i datalagret.</span><span class="sxs-lookup"><span data-stu-id="472bf-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="472bf-118">(Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `New-Item` cmdlet: en.)</span><span class="sxs-lookup"><span data-stu-id="472bf-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="472bf-119">Skriver över den [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) metod för att ändra funktionssättet för den `Remove-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="472bf-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="472bf-120">(Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Remove-Item` cmdlet: en.)</span><span class="sxs-lookup"><span data-stu-id="472bf-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="472bf-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="472bf-121">Example</span></span>

<span data-ttu-id="472bf-122">Detta exempel visar hur du skriver över de metoder som krävs för att kopiera, skapa och ta bort objekt samt metoder för att hämta underordnat objekt för en överordnad artikel.</span><span class="sxs-lookup"><span data-stu-id="472bf-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="472bf-123">Se även</span><span class="sxs-lookup"><span data-stu-id="472bf-123">See Also</span></span>

[<span data-ttu-id="472bf-124">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="472bf-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="472bf-125">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="472bf-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="472bf-126">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="472bf-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="472bf-127">Designa din Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="472bf-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)