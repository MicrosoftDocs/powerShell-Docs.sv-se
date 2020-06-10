---
title: AccessDBProviderSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aaf9351e-157f-4d48-8b8f-1fd64855b682
caps.latest.revision: 10
ms.openlocfilehash: 219f8c2367939d16da928ede789843669b4451c6
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633421"
---
# <a name="accessdbprovidersample02"></a><span data-ttu-id="0dbed-102">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="0dbed-102">AccessDBProviderSample02</span></span>

<span data-ttu-id="0dbed-103">Det här exemplet visar hur du skriver över [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) och [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metoder för att stödja anrop till `New-PSDrive` `Remove-PSDrive` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="0dbed-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span> <span data-ttu-id="0dbed-104">Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="0dbed-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0dbed-105">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="0dbed-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0dbed-106">Din leverantörs klass kommer förmodligen att härledas från någon av följande klasser och kan eventuellt implementera andra Provider-gränssnitt:</span><span class="sxs-lookup"><span data-stu-id="0dbed-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="0dbed-107">Klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="0dbed-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="0dbed-108">Se [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="0dbed-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="0dbed-109">Klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="0dbed-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="0dbed-110">Se [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="0dbed-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="0dbed-111">Klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="0dbed-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="0dbed-112">Se [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="0dbed-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="0dbed-113">Mer information om hur du väljer vilken leverantörs klass som ska härledas från baserat på funktioner i providern finns i [utforma din Windows PowerShell-Provider](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="0dbed-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="0dbed-114">Det här exemplet demonstrerar följande:</span><span class="sxs-lookup"><span data-stu-id="0dbed-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="0dbed-115">Attributet deklareras `CmdletProvider` .</span><span class="sxs-lookup"><span data-stu-id="0dbed-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="0dbed-116">Definiera en leverantörs klass som Drivers från klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="0dbed-116">Defining a provider class that drives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

- <span data-ttu-id="0dbed-117">Skriva över metoden [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) för att stödja skapande av nya enheter.</span><span class="sxs-lookup"><span data-stu-id="0dbed-117">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to support creating new drives.</span></span> <span data-ttu-id="0dbed-118">(Det här exemplet visar inte hur du lägger till dynamiska parametrar i `New-PSDrive` cmdleten.)</span><span class="sxs-lookup"><span data-stu-id="0dbed-118">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="0dbed-119">Skriva över metoden [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) för att stödja borttagning av befintliga enheter.</span><span class="sxs-lookup"><span data-stu-id="0dbed-119">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

## <a name="example"></a><span data-ttu-id="0dbed-120">Exempel</span><span class="sxs-lookup"><span data-stu-id="0dbed-120">Example</span></span>

<span data-ttu-id="0dbed-121">Det här exemplet visar hur du skriver över [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) och [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metoder.</span><span class="sxs-lookup"><span data-stu-id="0dbed-121">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods.</span></span> <span data-ttu-id="0dbed-122">För den här exempel leverantören lagras anslutnings informationen i ett objekt när en enhet skapas `AccessDBPsDriveInfo` .</span><span class="sxs-lookup"><span data-stu-id="0dbed-122">For this sample provider, when a drive is created its connection information is stored in an `AccessDBPsDriveInfo` object.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="0dbed-123">Se även</span><span class="sxs-lookup"><span data-stu-id="0dbed-123">See Also</span></span>

[<span data-ttu-id="0dbed-124">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="0dbed-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="0dbed-125">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="0dbed-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="0dbed-126">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="0dbed-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="0dbed-127">Designa en Windows PowerShell-provider</span><span class="sxs-lookup"><span data-stu-id="0dbed-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
