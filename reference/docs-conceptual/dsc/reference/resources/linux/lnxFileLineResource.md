---
ms.date: 07/17/2020
ms.topic: reference
title: DSC för Linux nxFileLine-resurs
description: DSC för Linux nxFileLine-resurs
ms.openlocfilehash: b342021176e4d8584afec82173f31bf5191ad264
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644754"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="f1f85-103">DSC för Linux nxFileLine-resurs</span><span class="sxs-lookup"><span data-stu-id="f1f85-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="f1f85-104">**NxFileLine** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera rader i en konfigurations fil på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="f1f85-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f1f85-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f1f85-105">Syntax</span></span>

```Syntax
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="f1f85-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="f1f85-106">Properties</span></span>

|<span data-ttu-id="f1f85-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="f1f85-107">Property</span></span> |<span data-ttu-id="f1f85-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f1f85-108">Description</span></span> |
|---|---|
|<span data-ttu-id="f1f85-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="f1f85-109">FilePath</span></span> |<span data-ttu-id="f1f85-110">Den fullständiga sökvägen till filen som hanterar rader i på målnoden.</span><span class="sxs-lookup"><span data-stu-id="f1f85-110">The full path to the file to manage lines in on the target node.</span></span> |
|<span data-ttu-id="f1f85-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="f1f85-111">ContainsLine</span></span> |<span data-ttu-id="f1f85-112">En rad för att se till att den finns i filen.</span><span class="sxs-lookup"><span data-stu-id="f1f85-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="f1f85-113">Den här raden läggs till i filen om den inte finns i filen.</span><span class="sxs-lookup"><span data-stu-id="f1f85-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="f1f85-114">**ContainsLine** är obligatoriskt, men kan anges till en tom sträng ( `ContainsLine = ""` ) om det inte behövs.</span><span class="sxs-lookup"><span data-stu-id="f1f85-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span> |
|<span data-ttu-id="f1f85-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="f1f85-115">DoesNotContainPattern</span></span> |<span data-ttu-id="f1f85-116">Ett mönster för reguljära uttryck för rader som inte ska finnas i filen.</span><span class="sxs-lookup"><span data-stu-id="f1f85-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="f1f85-117">För rader som finns i den fil som matchar det här reguljära uttrycket tas raden bort från filen.</span><span class="sxs-lookup"><span data-stu-id="f1f85-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="f1f85-118">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="f1f85-118">Common properties</span></span>

|<span data-ttu-id="f1f85-119">Egenskap</span><span class="sxs-lookup"><span data-stu-id="f1f85-119">Property</span></span> |<span data-ttu-id="f1f85-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f1f85-120">Description</span></span> |
|---|---|
|<span data-ttu-id="f1f85-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f1f85-121">DependsOn</span></span> |<span data-ttu-id="f1f85-122">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="f1f85-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f1f85-123">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="f1f85-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="f1f85-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="f1f85-124">Example</span></span>

<span data-ttu-id="f1f85-125">Det här exemplet visar hur du konfigurerar filen genom att använda **nxFileLine** `/etc/sudoers` -resursen och se till att användaren: monuser är konfigurerad till inte requiretty.</span><span class="sxs-lookup"><span data-stu-id="f1f85-125">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = "/etc/sudoers"
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```
