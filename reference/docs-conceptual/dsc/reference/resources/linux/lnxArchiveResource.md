---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxArchive-resurs
ms.openlocfilehash: 386378fa6e1608117d6934b983dcebe23e55d60d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464255"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="afd9c-103">DSC för Linux nxArchive-resurs</span><span class="sxs-lookup"><span data-stu-id="afd9c-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="afd9c-104">**NxArchive** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att packa upp arkiv (. tar. zip)-filer på en särskild sökväg på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="afd9c-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="afd9c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="afd9c-105">Syntax</span></span>

```Syntax
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="afd9c-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="afd9c-106">Properties</span></span>

|<span data-ttu-id="afd9c-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="afd9c-107">Property</span></span> |<span data-ttu-id="afd9c-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="afd9c-108">Description</span></span> |
|---|---|
|<span data-ttu-id="afd9c-109">Sök</span><span class="sxs-lookup"><span data-stu-id="afd9c-109">SourcePath</span></span> |<span data-ttu-id="afd9c-110">Anger Arkiv filens käll Sök väg.</span><span class="sxs-lookup"><span data-stu-id="afd9c-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="afd9c-111">Detta bör vara en. tar-,. zip-eller. tar. gz-fil.</span><span class="sxs-lookup"><span data-stu-id="afd9c-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
|<span data-ttu-id="afd9c-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="afd9c-112">DestinationPath</span></span> |<span data-ttu-id="afd9c-113">Anger den plats där du vill se till att Arkiv innehållet extraheras.</span><span class="sxs-lookup"><span data-stu-id="afd9c-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="afd9c-114">Kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="afd9c-114">Checksum</span></span> |<span data-ttu-id="afd9c-115">Definierar den typ som ska användas för att avgöra om käll arkivet har uppdaterats.</span><span class="sxs-lookup"><span data-stu-id="afd9c-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="afd9c-116">Värdena är: **ctime**, **mtime**eller **MD5**.</span><span class="sxs-lookup"><span data-stu-id="afd9c-116">Values are: **ctime**, **mtime**, or **md5**.</span></span> <span data-ttu-id="afd9c-117">Standardvärdet är **MD5**.</span><span class="sxs-lookup"><span data-stu-id="afd9c-117">The default value is **md5**.</span></span> |
|<span data-ttu-id="afd9c-118">Force</span><span class="sxs-lookup"><span data-stu-id="afd9c-118">Force</span></span> |<span data-ttu-id="afd9c-119">Vissa fil åtgärder (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="afd9c-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="afd9c-120">Om du använder **Force** -egenskapen åsidosätts sådana fel.</span><span class="sxs-lookup"><span data-stu-id="afd9c-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="afd9c-121">Standardvärdet är `$false`.</span><span class="sxs-lookup"><span data-stu-id="afd9c-121">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="afd9c-122">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="afd9c-122">Common properties</span></span>

|<span data-ttu-id="afd9c-123">Egenskap</span><span class="sxs-lookup"><span data-stu-id="afd9c-123">Property</span></span> |<span data-ttu-id="afd9c-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="afd9c-124">Description</span></span> |
|---|---|
|<span data-ttu-id="afd9c-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="afd9c-125">DependsOn</span></span> |<span data-ttu-id="afd9c-126">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="afd9c-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="afd9c-127">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="afd9c-127">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="afd9c-128">Kontrol</span><span class="sxs-lookup"><span data-stu-id="afd9c-128">Ensure</span></span> |<span data-ttu-id="afd9c-129">Avgör om du ska kontrol lera om arkivets innehåll finns vid **målet**.</span><span class="sxs-lookup"><span data-stu-id="afd9c-129">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="afd9c-130">Ange att den här egenskapen **finns för att** se till att innehållet finns.</span><span class="sxs-lookup"><span data-stu-id="afd9c-130">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="afd9c-131">Ange det som **frånvarande** för att se till att de inte finns.</span><span class="sxs-lookup"><span data-stu-id="afd9c-131">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="afd9c-132">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="afd9c-132">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="afd9c-133">Exempel</span><span class="sxs-lookup"><span data-stu-id="afd9c-133">Example</span></span>

<span data-ttu-id="afd9c-134">I följande exempel visas hur du använder **nxArchive** -resursen för att kontrol lera att innehållet i en arkivfil som heter `website.tar` finns och extraheras vid ett angivet mål.</span><span class="sxs-lookup"><span data-stu-id="afd9c-134">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```powershell
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = "http://release.contoso.com/releases/website.tar"
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = "mtime"
}

nxArchive SyncWebDir
{
   SourcePath = "/usr/release/staging/website.tar"
   DestinationPath = "/usr/local/apache2/htdocs/"
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```
