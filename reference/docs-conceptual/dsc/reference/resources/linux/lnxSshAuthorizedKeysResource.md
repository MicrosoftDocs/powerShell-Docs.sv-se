---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxSshAuthorizedKeys-resurs
ms.openlocfilehash: 6e008efcbff2e679650d0bc3d5b8b573f6ef83e0
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941462"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="03db5-103">DSC för Linux nxSshAuthorizedKeys-resurs</span><span class="sxs-lookup"><span data-stu-id="03db5-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="03db5-104">**NxAuthorizedKeys** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera behöriga SSH-nycklar för en angiven användare.</span><span class="sxs-lookup"><span data-stu-id="03db5-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="03db5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="03db5-105">Syntax</span></span>

```Syntax
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="03db5-106">properties</span><span class="sxs-lookup"><span data-stu-id="03db5-106">Properties</span></span>

|<span data-ttu-id="03db5-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="03db5-107">Property</span></span> |<span data-ttu-id="03db5-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="03db5-108">Description</span></span> |
|---|---|
|<span data-ttu-id="03db5-109">Kommentar</span><span class="sxs-lookup"><span data-stu-id="03db5-109">KeyComment</span></span> |<span data-ttu-id="03db5-110">En unik kommentar för nyckeln.</span><span class="sxs-lookup"><span data-stu-id="03db5-110">A unique comment for the key.</span></span> <span data-ttu-id="03db5-111">Detta används för att identifiera nycklar unikt.</span><span class="sxs-lookup"><span data-stu-id="03db5-111">This is used to uniquely identify keys.</span></span> |
|<span data-ttu-id="03db5-112">Användarnamn</span><span class="sxs-lookup"><span data-stu-id="03db5-112">Username</span></span> |<span data-ttu-id="03db5-113">Användar namnet för hantering av SSH-auktoriserade nycklar för.</span><span class="sxs-lookup"><span data-stu-id="03db5-113">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="03db5-114">Om den inte är definierad är standard användaren **roten**.</span><span class="sxs-lookup"><span data-stu-id="03db5-114">If not defined, the default user is **root**.</span></span> |
|<span data-ttu-id="03db5-115">Nyckel</span><span class="sxs-lookup"><span data-stu-id="03db5-115">Key</span></span> |<span data-ttu-id="03db5-116">Nyckelns innehåll.</span><span class="sxs-lookup"><span data-stu-id="03db5-116">The contents of the key.</span></span> <span data-ttu-id="03db5-117">Detta **är obligatoriskt om alternativet** är angivet som **tillgängligt**.</span><span class="sxs-lookup"><span data-stu-id="03db5-117">This is required if **Ensure** is set to **Present**.</span></span>|

## <a name="common-properties"></a><span data-ttu-id="03db5-118">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="03db5-118">Common properties</span></span>

|<span data-ttu-id="03db5-119">Egenskap</span><span class="sxs-lookup"><span data-stu-id="03db5-119">Property</span></span> |<span data-ttu-id="03db5-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="03db5-120">Description</span></span> |
|---|---|
|<span data-ttu-id="03db5-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="03db5-121">DependsOn</span></span> |<span data-ttu-id="03db5-122">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="03db5-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="03db5-123">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="03db5-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="03db5-124">Kontrol</span><span class="sxs-lookup"><span data-stu-id="03db5-124">Ensure</span></span> |<span data-ttu-id="03db5-125">Anger om nyckeln har definierats.</span><span class="sxs-lookup"><span data-stu-id="03db5-125">Specifies whether the key is defined.</span></span> <span data-ttu-id="03db5-126">Ange den här egenskapen som **saknas** för att se till att nyckeln inte finns i användarens auktoriserade nyckel fil.</span><span class="sxs-lookup"><span data-stu-id="03db5-126">Set this property to **Absent** to ensure the key does not exist in the user's authorized keys file.</span></span> <span data-ttu-id="03db5-127">Ange att den **finns** för att säkerställa att nyckeln definieras i användarens auktoriserade nyckel fil.</span><span class="sxs-lookup"><span data-stu-id="03db5-127">Set it to **Present** to ensure the key is defined in the user's authorized key file.</span></span> |

## <a name="example"></a><span data-ttu-id="03db5-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="03db5-128">Example</span></span>

<span data-ttu-id="03db5-129">I följande exempel definieras en offentlig SSH-auktoriserad nyckel för användaren "monuser".</span><span class="sxs-lookup"><span data-stu-id="03db5-129">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxSshAuthorizedKeys myKey
    {
        KeyComment = "myKey"
        Ensure = "Present"
        Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
        UserName = "monuser"
    }
}
```