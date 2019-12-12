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
ms.openlocfilehash: 9c00ec6de987729fec42dc57245a949d11e31f4b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356856"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="a5c00-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="a5c00-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="a5c00-103">Det här exemplet visar hur du skriver över innehålls metoder för att stödja anrop till `Clear-Content`-, `Get-Content`-och `Set-Content`-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="a5c00-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="a5c00-104">Dessa metoder bör implementeras när användaren behöver hantera innehållet i objekten i data lagret.</span><span class="sxs-lookup"><span data-stu-id="a5c00-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="a5c00-105">Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) och implementerar gränssnittet [system. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a5c00-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a5c00-106">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="a5c00-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a5c00-107">Din leverantörs klass kommer förmodligen att härledas från någon av följande klasser och kan eventuellt implementera andra Provider-gränssnitt:</span><span class="sxs-lookup"><span data-stu-id="a5c00-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="a5c00-108">Klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a5c00-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="a5c00-109">Se [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="a5c00-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="a5c00-110">Klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a5c00-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="a5c00-111">Se [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="a5c00-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="a5c00-112">Klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a5c00-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="a5c00-113">Mer information om hur du väljer vilken leverantörs klass som ska härledas från baserat på funktioner i providern finns i [utforma din Windows PowerShell-Provider](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="a5c00-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="a5c00-114">Det här exemplet demonstrerar följande:</span><span class="sxs-lookup"><span data-stu-id="a5c00-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="a5c00-115">Deklarera `CmdletProvider`-attributet.</span><span class="sxs-lookup"><span data-stu-id="a5c00-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="a5c00-116">Definiera en leverantörs klass som härleds från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) och som deklarerar [system. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) -gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="a5c00-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="a5c00-117">Skriv över metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) för att ändra beteendet för `Clear-Content`-cmdleten, så att användaren kan ta bort innehållet från ett objekt.</span><span class="sxs-lookup"><span data-stu-id="a5c00-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="a5c00-118">(Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Clear-Content`-cmdleten.)</span><span class="sxs-lookup"><span data-stu-id="a5c00-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="a5c00-119">Skriv över metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) för att ändra beteendet för `Get-Content`-cmdleten, så att användaren kan hämta innehållet i ett objekt.</span><span class="sxs-lookup"><span data-stu-id="a5c00-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="a5c00-120">(Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Get-Content`-cmdleten.).</span><span class="sxs-lookup"><span data-stu-id="a5c00-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="a5c00-121">Skriv över metoden [Microsoft. PowerShell. commands. Filesystemprovider. Getcontentwriter \*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) för att ändra beteendet för `Set-Content`-cmdleten, så att användaren kan uppdatera innehållet i ett objekt.</span><span class="sxs-lookup"><span data-stu-id="a5c00-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="a5c00-122">(Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Set-Content`-cmdleten.)</span><span class="sxs-lookup"><span data-stu-id="a5c00-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="a5c00-123">Exempel</span><span class="sxs-lookup"><span data-stu-id="a5c00-123">Example</span></span>

<span data-ttu-id="a5c00-124">Det här exemplet visar hur du skriver över de metoder som behövs för att rensa, hämta och ange innehållet i objekt i en Microsoft Access-databas.</span><span class="sxs-lookup"><span data-stu-id="a5c00-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="a5c00-125">Se även</span><span class="sxs-lookup"><span data-stu-id="a5c00-125">See Also</span></span>

[<span data-ttu-id="a5c00-126">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a5c00-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="a5c00-127">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a5c00-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="a5c00-128">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a5c00-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="a5c00-129">Designa din Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="a5c00-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
