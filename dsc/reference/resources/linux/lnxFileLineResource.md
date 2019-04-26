---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxFileLine-resurs
ms.openlocfilehash: 6a91db25638b09659adfabcec78f91bcb2e69dd9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077969"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="4732d-103">DSC för Linux nxFileLine-resurs</span><span class="sxs-lookup"><span data-stu-id="4732d-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="4732d-104">Den **nxFileLine** resursen i PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera rader i en fil på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="4732d-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="4732d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4732d-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="4732d-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="4732d-106">Properties</span></span>

|  <span data-ttu-id="4732d-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="4732d-107">Property</span></span> |  <span data-ttu-id="4732d-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4732d-108">Description</span></span> |
|---|---|
| <span data-ttu-id="4732d-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="4732d-109">FilePath</span></span>| <span data-ttu-id="4732d-110">Den fullständiga sökvägen till filen för att hantera rader i på målnoden.</span><span class="sxs-lookup"><span data-stu-id="4732d-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="4732d-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="4732d-111">ContainsLine</span></span>| <span data-ttu-id="4732d-112">En rad för att se till att det finns i filen.</span><span class="sxs-lookup"><span data-stu-id="4732d-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="4732d-113">Den här raden kommer att läggas till filen om den inte finns i filen.</span><span class="sxs-lookup"><span data-stu-id="4732d-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="4732d-114">**ContainsLine** är obligatorisk, men kan anges till en tom sträng (`ContainsLine = ""`) om det inte behövs.</span><span class="sxs-lookup"><span data-stu-id="4732d-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span>|
| <span data-ttu-id="4732d-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="4732d-115">DoesNotContainPattern</span></span>| <span data-ttu-id="4732d-116">Ett mönster för reguljärt uttryck för rader som inte ska finnas i filen.</span><span class="sxs-lookup"><span data-stu-id="4732d-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="4732d-117">För alla rader som redan finns i filen som matchar den här reguljärt uttryck, tas raden bort från filen.</span><span class="sxs-lookup"><span data-stu-id="4732d-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="4732d-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4732d-118">DependsOn</span></span> | <span data-ttu-id="4732d-119">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="4732d-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4732d-120">Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="4732d-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="4732d-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="4732d-121">Example</span></span>

<span data-ttu-id="4732d-122">Det här exemplet visar hur du använder den **nxFileLine** resursen för att konfigurera den `/etc/sudoers` filen, vilket säkerställer att användaren: monuser är konfigurerad för att inte requiretty.</span><span class="sxs-lookup"><span data-stu-id="4732d-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```