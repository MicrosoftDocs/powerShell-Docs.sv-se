---
title: AccessDBProviderSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849198"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="d3539-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="d3539-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="d3539-103">Det här exemplet visas hur du skriver över den [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) och [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metoder för att stödja anrop till den `Get-Item` och `Set-Item` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="d3539-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="d3539-104">Providerklass i det här exemplet kommer från den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="d3539-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d3539-105">Visar</span><span class="sxs-lookup"><span data-stu-id="d3539-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d3539-106">Din providerklass kommer troligen härleder från en av följande klasser och eventuellt implementera andra provider-gränssnitt:</span><span class="sxs-lookup"><span data-stu-id="d3539-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="d3539-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="d3539-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="d3539-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="d3539-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="d3539-109">Se [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="d3539-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="d3539-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="d3539-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="d3539-111">Se [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="d3539-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="d3539-112">Mer information om hur du väljer vilken providerklass som härleds från baserat på provider-funktioner kan du läsa [designa din Windows PowerShell-providern](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="d3539-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="d3539-113">Detta exempel visar följande:</span><span class="sxs-lookup"><span data-stu-id="d3539-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="d3539-114">Deklarera de `CmdletProvider` attribut.</span><span class="sxs-lookup"><span data-stu-id="d3539-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="d3539-115">Definiera en providerklass som härleds från den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="d3539-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="d3539-116">Skriver över den [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metod för att ändra funktionssättet för den `New-PSDrive` cmdlet, där användaren kan skapa nya enheter.</span><span class="sxs-lookup"><span data-stu-id="d3539-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="d3539-117">(Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `New-PSDrive` cmdlet: en.)</span><span class="sxs-lookup"><span data-stu-id="d3539-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="d3539-118">Skriver över den [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metod för att stödja ta bort befintliga enheter.</span><span class="sxs-lookup"><span data-stu-id="d3539-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="d3539-119">Skriver över den [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metod för att ändra funktionssättet för den `Get-Item` cmdlet, där användaren kan hämta objekt från datalagret.</span><span class="sxs-lookup"><span data-stu-id="d3539-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="d3539-120">(Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Get-Item` cmdlet: en.)</span><span class="sxs-lookup"><span data-stu-id="d3539-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="d3539-121">Skriver över den [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metod för att ändra funktionssättet för den `Set-Item` cmdlet, så att användaren kan uppdatera objekt i datalagret.</span><span class="sxs-lookup"><span data-stu-id="d3539-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="d3539-122">(Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Get-Item` cmdlet: en.)</span><span class="sxs-lookup"><span data-stu-id="d3539-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="d3539-123">Skriver över den [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metod för att ändra funktionssättet för den `Test-Path` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d3539-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="d3539-124">(Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Test-Path` cmdlet: en.)</span><span class="sxs-lookup"><span data-stu-id="d3539-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="d3539-125">Skriver över den [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metod för att avgöra om den angivna sökvägen är giltig.</span><span class="sxs-lookup"><span data-stu-id="d3539-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="d3539-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="d3539-126">Example</span></span>

<span data-ttu-id="d3539-127">Detta exempel visar hur du skriver över de metoder som krävs för att hämta och ange objekt i en Microsoft Access-data.</span><span class="sxs-lookup"><span data-stu-id="d3539-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="d3539-128">Se även</span><span class="sxs-lookup"><span data-stu-id="d3539-128">See Also</span></span>

[<span data-ttu-id="d3539-129">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="d3539-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="d3539-130">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="d3539-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="d3539-131">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="d3539-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="d3539-132">Designa din Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="d3539-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)