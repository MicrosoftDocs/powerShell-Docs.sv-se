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
ms.openlocfilehash: aa67bb605f90c1ea40323b4583766069ff1226fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352411"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="3271f-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="3271f-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="3271f-103">Det här exemplet visar hur du skriver över [system. Management. Automation. Provider. Itemcmdletprovider. getItem, \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) och [system. Management. Automation. Provider. Itemcmdletprovider. setItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metoder för att stödja anrop till `Get-Item` och @no__ t-3-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="3271f-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="3271f-104">Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="3271f-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3271f-105">Visat</span><span class="sxs-lookup"><span data-stu-id="3271f-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3271f-106">Din leverantörs klass kommer förmodligen att härledas från någon av följande klasser och kan eventuellt implementera andra Provider-gränssnitt:</span><span class="sxs-lookup"><span data-stu-id="3271f-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="3271f-107">Klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="3271f-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="3271f-108">Klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="3271f-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="3271f-109">Se [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="3271f-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="3271f-110">Klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="3271f-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="3271f-111">Se [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="3271f-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="3271f-112">Mer information om hur du väljer vilken leverantörs klass som ska härledas från baserat på funktioner i providern finns i [utforma din Windows PowerShell-Provider](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="3271f-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="3271f-113">Det här exemplet demonstrerar följande:</span><span class="sxs-lookup"><span data-stu-id="3271f-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="3271f-114">Deklarerar attributet `CmdletProvider`.</span><span class="sxs-lookup"><span data-stu-id="3271f-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="3271f-115">Definiera en leverantörs klass som härleds från klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="3271f-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="3271f-116">Skriv över metoden [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) för att ändra beteendet för `New-PSDrive`-cmdleten, så att användaren kan skapa nya enheter.</span><span class="sxs-lookup"><span data-stu-id="3271f-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="3271f-117">(Det här exemplet visar inte hur du lägger till dynamiska parametrar i `New-PSDrive`-cmdleten.)</span><span class="sxs-lookup"><span data-stu-id="3271f-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="3271f-118">Skriva över metoden [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) för att stödja borttagning av befintliga enheter.</span><span class="sxs-lookup"><span data-stu-id="3271f-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="3271f-119">Skriv över metoden [system. Management. Automation. Provider. Itemcmdletprovider. getItem, \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) för att ändra beteendet för `Get-Item`-cmdleten, så att användaren kan hämta objekt från data lagret.</span><span class="sxs-lookup"><span data-stu-id="3271f-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="3271f-120">(Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Get-Item`-cmdleten.)</span><span class="sxs-lookup"><span data-stu-id="3271f-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="3271f-121">Skriv över metoden [system. Management. Automation. Provider. Itemcmdletprovider. setItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) för att ändra beteendet för `Set-Item`-cmdleten, så att användaren kan uppdatera objekten i data lagret.</span><span class="sxs-lookup"><span data-stu-id="3271f-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="3271f-122">(Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Get-Item`-cmdleten.)</span><span class="sxs-lookup"><span data-stu-id="3271f-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="3271f-123">Skriv över metoden [system. Management. Automation. Provider. Itemcmdletprovider. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) för att ändra beteendet för `Test-Path`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3271f-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="3271f-124">(Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Test-Path`-cmdleten.)</span><span class="sxs-lookup"><span data-stu-id="3271f-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="3271f-125">Skriv över metoden [system. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) för att avgöra om den angivna sökvägen är giltig.</span><span class="sxs-lookup"><span data-stu-id="3271f-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="3271f-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="3271f-126">Example</span></span>

<span data-ttu-id="3271f-127">Det här exemplet visar hur du skriver över de metoder som behövs för att hämta och ange objekt i en Microsoft Access-databas.</span><span class="sxs-lookup"><span data-stu-id="3271f-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="3271f-128">Se även</span><span class="sxs-lookup"><span data-stu-id="3271f-128">See Also</span></span>

[<span data-ttu-id="3271f-129">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="3271f-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="3271f-130">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="3271f-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="3271f-131">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="3271f-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="3271f-132">Designa din Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="3271f-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
