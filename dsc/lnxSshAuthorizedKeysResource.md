---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "DSC för Linux nxSshAuthorizedKeys resurs"
ms.openlocfilehash: 3c145eeb86d971dc00e1c7cea60fb50c83d7b9a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="741b2-103">DSC för Linux nxSshAuthorizedKeys resurs</span><span class="sxs-lookup"><span data-stu-id="741b2-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="741b2-104">Den **nxAuthorizedKeys** resurs i PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att hantera behörighet ssh nycklar för en angiven användare.</span><span class="sxs-lookup"><span data-stu-id="741b2-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="741b2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="741b2-105">Syntax</span></span>

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="741b2-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="741b2-106">Properties</span></span>

|  <span data-ttu-id="741b2-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="741b2-107">Property</span></span> |  <span data-ttu-id="741b2-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="741b2-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="741b2-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="741b2-109">KeyComment</span></span>| <span data-ttu-id="741b2-110">En unik kommentar för nyckeln.</span><span class="sxs-lookup"><span data-stu-id="741b2-110">A unique comment for the key.</span></span> <span data-ttu-id="741b2-111">Det här används för att unikt identifiera nycklar.</span><span class="sxs-lookup"><span data-stu-id="741b2-111">This is used to uniquely identify keys.</span></span>| 
| <span data-ttu-id="741b2-112">Se till att</span><span class="sxs-lookup"><span data-stu-id="741b2-112">Ensure</span></span>| <span data-ttu-id="741b2-113">Anger om nyckeln är definierad.</span><span class="sxs-lookup"><span data-stu-id="741b2-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="741b2-114">Ange den här egenskapen till ”saknas” för att se till att nyckeln inte finns i användarens auktoriserade nycklar fil.</span><span class="sxs-lookup"><span data-stu-id="741b2-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="741b2-115">Ange den till ”finns” för att se till att nyckeln har definierats i användarens auktoriserade nyckelfilen.</span><span class="sxs-lookup"><span data-stu-id="741b2-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>| 
| <span data-ttu-id="741b2-116">Användarnamn</span><span class="sxs-lookup"><span data-stu-id="741b2-116">Username</span></span>| <span data-ttu-id="741b2-117">Användarnamn för att hantera ssh behörighet nycklar för.</span><span class="sxs-lookup"><span data-stu-id="741b2-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="741b2-118">Om du inte har definierats, är standardanvändaren ”rot”.</span><span class="sxs-lookup"><span data-stu-id="741b2-118">If not defined, the default user is "root".</span></span>| 
| <span data-ttu-id="741b2-119">Tangent</span><span class="sxs-lookup"><span data-stu-id="741b2-119">Key</span></span>| <span data-ttu-id="741b2-120">Innehållet i nyckeln.</span><span class="sxs-lookup"><span data-stu-id="741b2-120">The contents of the key.</span></span> <span data-ttu-id="741b2-121">Detta krävs om **Kontrollera** är inställd på ”saknas”.</span><span class="sxs-lookup"><span data-stu-id="741b2-121">This is required if **Ensure** is set to "Present".</span></span>| 
| <span data-ttu-id="741b2-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="741b2-122">DependsOn</span></span> | <span data-ttu-id="741b2-123">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="741b2-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="741b2-124">Till exempel om den **ID** resursens configuration skriptblock som du vill köra först är **ResourceName** och dess typ är **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="741b2-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="741b2-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="741b2-125">Example</span></span>

<span data-ttu-id="741b2-126">I följande exempel definieras en offentlig ssh auktoriserad nyckel för användaren ”monuser”.</span><span class="sxs-lookup"><span data-stu-id="741b2-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```
Import-DSCResource -Module nx 

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
} 
}
```

