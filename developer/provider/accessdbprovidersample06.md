---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055554"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="c288e-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="c288e-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="c288e-103">Det här exemplet visas hur du skriver över innehåll metoder för att stödja anrop till den `Clear-Content`, `Get-Content`, och `Set-Content` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="c288e-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="c288e-104">Dessa metoder bör implementeras när användaren behöver för att hantera innehåll över hur objekten i datalagret.</span><span class="sxs-lookup"><span data-stu-id="c288e-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="c288e-105">Providerklass i det här exemplet kommer från den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klass och det implementerar den [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="c288e-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c288e-106">Visar</span><span class="sxs-lookup"><span data-stu-id="c288e-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c288e-107">Din providerklass kommer troligen härleder från en av följande klasser och eventuellt implementera andra provider-gränssnitt:</span><span class="sxs-lookup"><span data-stu-id="c288e-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="c288e-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="c288e-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="c288e-109">Se [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="c288e-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="c288e-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="c288e-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="c288e-111">Se [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="c288e-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="c288e-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klass.</span><span class="sxs-lookup"><span data-stu-id="c288e-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="c288e-113">Mer information om hur du väljer vilken providerklass som härleds från baserat på provider-funktioner kan du läsa [designa din Windows PowerShell-providern](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="c288e-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="c288e-114">Detta exempel visar följande:</span><span class="sxs-lookup"><span data-stu-id="c288e-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="c288e-115">Deklarera de `CmdletProvider` attribut.</span><span class="sxs-lookup"><span data-stu-id="c288e-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="c288e-116">Definiera en providerklass som härleds från den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klass och som förklarar den [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="c288e-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="c288e-117">Skriver över den [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metod för att ändra funktionssättet för den `Clear-Content` cmdlet, där användaren kan ta bort innehållet från ett objekt.</span><span class="sxs-lookup"><span data-stu-id="c288e-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="c288e-118">(Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Clear-Content` cmdlet: en.)</span><span class="sxs-lookup"><span data-stu-id="c288e-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="c288e-119">Skriver över den [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metod för att ändra funktionssättet för den `Get-Content` cmdlet, så att användaren att hämta innehållet i ett objekt.</span><span class="sxs-lookup"><span data-stu-id="c288e-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="c288e-120">(Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Get-Content` cmdlet: en.).</span><span class="sxs-lookup"><span data-stu-id="c288e-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="c288e-121">Skriver över den [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) metod för att ändra funktionssättet för den `Set-Content` cmdlet, så att användaren att uppdatera innehållet i ett objekt.</span><span class="sxs-lookup"><span data-stu-id="c288e-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="c288e-122">(Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Set-Content` cmdlet: en.)</span><span class="sxs-lookup"><span data-stu-id="c288e-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="c288e-123">Exempel</span><span class="sxs-lookup"><span data-stu-id="c288e-123">Example</span></span>

<span data-ttu-id="c288e-124">Detta exempel visar hur du skriver över de metoder som krävs för att rensa, hämta och ange innehållet för objekt i en Microsoft Access-data.</span><span class="sxs-lookup"><span data-stu-id="c288e-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="c288e-125">Se även</span><span class="sxs-lookup"><span data-stu-id="c288e-125">See Also</span></span>

[<span data-ttu-id="c288e-126">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="c288e-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="c288e-127">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="c288e-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="c288e-128">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="c288e-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="c288e-129">Designa din Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="c288e-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)