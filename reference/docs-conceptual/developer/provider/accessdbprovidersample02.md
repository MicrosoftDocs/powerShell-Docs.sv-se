---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample02
description: AccessDBProviderSample02
ms.openlocfilehash: ebba2381370cf73f1e39015990f81dc4fd6dd937
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667444"
---
# <a name="accessdbprovidersample02"></a><span data-ttu-id="b66ad-103">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="b66ad-103">AccessDBProviderSample02</span></span>

<span data-ttu-id="b66ad-104">Det här exemplet visar hur du skriver över [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) och [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metoder för att stödja anrop till `New-PSDrive` `Remove-PSDrive` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="b66ad-104">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span> <span data-ttu-id="b66ad-105">Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b66ad-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b66ad-106">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="b66ad-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b66ad-107">Din leverantörs klass kommer förmodligen att härledas från någon av följande klasser och kan eventuellt implementera andra Provider-gränssnitt:</span><span class="sxs-lookup"><span data-stu-id="b66ad-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="b66ad-108">Klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b66ad-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="b66ad-109">Se [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="b66ad-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="b66ad-110">Klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b66ad-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="b66ad-111">Se [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="b66ad-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="b66ad-112">Klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b66ad-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="b66ad-113">Se [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="b66ad-113">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="b66ad-114">Mer information om hur du väljer vilken leverantörs klass som ska härledas från baserat på funktioner i providern finns i [utforma din Windows PowerShell-Provider](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="b66ad-114">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="b66ad-115">Det här exemplet demonstrerar följande:</span><span class="sxs-lookup"><span data-stu-id="b66ad-115">This sample demonstrates the following:</span></span>

- <span data-ttu-id="b66ad-116">Attributet deklareras `CmdletProvider` .</span><span class="sxs-lookup"><span data-stu-id="b66ad-116">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="b66ad-117">Definiera en leverantörs klass som Drivers från klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b66ad-117">Defining a provider class that drives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

- <span data-ttu-id="b66ad-118">Skriva över metoden [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) för att stödja skapande av nya enheter.</span><span class="sxs-lookup"><span data-stu-id="b66ad-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to support creating new drives.</span></span> <span data-ttu-id="b66ad-119">(Det här exemplet visar inte hur du lägger till dynamiska parametrar i `New-PSDrive` cmdleten.)</span><span class="sxs-lookup"><span data-stu-id="b66ad-119">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="b66ad-120">Skriva över metoden [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) för att stödja borttagning av befintliga enheter.</span><span class="sxs-lookup"><span data-stu-id="b66ad-120">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

## <a name="example"></a><span data-ttu-id="b66ad-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="b66ad-121">Example</span></span>

<span data-ttu-id="b66ad-122">Det här exemplet visar hur du skriver över [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) och [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metoder.</span><span class="sxs-lookup"><span data-stu-id="b66ad-122">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods.</span></span> <span data-ttu-id="b66ad-123">För den här exempel leverantören lagras anslutnings informationen i ett objekt när en enhet skapas `AccessDBPsDriveInfo` .</span><span class="sxs-lookup"><span data-stu-id="b66ad-123">For this sample provider, when a drive is created its connection information is stored in an `AccessDBPsDriveInfo` object.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="b66ad-124">Se även</span><span class="sxs-lookup"><span data-stu-id="b66ad-124">See Also</span></span>

[<span data-ttu-id="b66ad-125">System. Management. Automation. Provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="b66ad-125">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="b66ad-126">System. Management. Automation. Provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="b66ad-126">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="b66ad-127">System. Management. Automation. Provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="b66ad-127">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="b66ad-128">Designa en Windows PowerShell-provider</span><span class="sxs-lookup"><span data-stu-id="b66ad-128">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
