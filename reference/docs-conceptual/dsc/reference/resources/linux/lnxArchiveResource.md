---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxArchive-resurs
ms.openlocfilehash: 77b52ad68344ba791501baeb585a5001cc97a126
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941511"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="f8650-103">DSC för Linux nxArchive-resurs</span><span class="sxs-lookup"><span data-stu-id="f8650-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="f8650-104">**NxArchive** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att packa upp arkiv (. tar. zip)-filer på en särskild sökväg på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="f8650-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f8650-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f8650-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="f8650-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="f8650-106">Properties</span></span>

|<span data-ttu-id="f8650-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="f8650-107">Property</span></span> |<span data-ttu-id="f8650-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f8650-108">Description</span></span> |
|---|---|
|<span data-ttu-id="f8650-109">Sök</span><span class="sxs-lookup"><span data-stu-id="f8650-109">SourcePath</span></span> |<span data-ttu-id="f8650-110">Anger Arkiv filens käll Sök väg.</span><span class="sxs-lookup"><span data-stu-id="f8650-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="f8650-111">Detta bör vara en. tar-,. zip-eller. tar. gz-fil.</span><span class="sxs-lookup"><span data-stu-id="f8650-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
|<span data-ttu-id="f8650-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="f8650-112">DestinationPath</span></span> |<span data-ttu-id="f8650-113">Anger den plats där du vill se till att Arkiv innehållet extraheras.</span><span class="sxs-lookup"><span data-stu-id="f8650-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="f8650-114">Kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="f8650-114">Checksum</span></span> |<span data-ttu-id="f8650-115">Definierar den typ som ska användas för att avgöra om käll arkivet har uppdaterats.</span><span class="sxs-lookup"><span data-stu-id="f8650-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="f8650-116">Värdena är: **ctime**, **mtime**eller **MD5**.</span><span class="sxs-lookup"><span data-stu-id="f8650-116">Values are: **ctime**, **mtime**, or **md5**.</span></span> <span data-ttu-id="f8650-117">Standardvärdet är **MD5**.</span><span class="sxs-lookup"><span data-stu-id="f8650-117">The default value is **md5**.</span></span> |
|<span data-ttu-id="f8650-118">Force</span><span class="sxs-lookup"><span data-stu-id="f8650-118">Force</span></span> |<span data-ttu-id="f8650-119">Vissa fil åtgärder (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="f8650-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="f8650-120">Om du använder **Force** -egenskapen åsidosätts sådana fel.</span><span class="sxs-lookup"><span data-stu-id="f8650-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="f8650-121">Standardvärdet är `$false`.</span><span class="sxs-lookup"><span data-stu-id="f8650-121">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="f8650-122">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="f8650-122">Common properties</span></span>

|<span data-ttu-id="f8650-123">Egenskap</span><span class="sxs-lookup"><span data-stu-id="f8650-123">Property</span></span> |<span data-ttu-id="f8650-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f8650-124">Description</span></span> |
|---|---|
|<span data-ttu-id="f8650-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f8650-125">DependsOn</span></span> |<span data-ttu-id="f8650-126">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="f8650-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f8650-127">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f8650-127">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="f8650-128">Kontrol</span><span class="sxs-lookup"><span data-stu-id="f8650-128">Ensure</span></span> |<span data-ttu-id="f8650-129">Avgör om du ska kontrol lera om arkivets innehåll finns vid **målet**.</span><span class="sxs-lookup"><span data-stu-id="f8650-129">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="f8650-130">Ange att den här egenskapen **finns för att** se till att innehållet finns.</span><span class="sxs-lookup"><span data-stu-id="f8650-130">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="f8650-131">Ange det som **frånvarande** för att se till att de inte finns.</span><span class="sxs-lookup"><span data-stu-id="f8650-131">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="f8650-132">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="f8650-132">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="f8650-133">Exempel</span><span class="sxs-lookup"><span data-stu-id="f8650-133">Example</span></span>

<span data-ttu-id="f8650-134">I följande exempel visas hur du använder **nxArchive** -resursen för att kontrol lera att innehållet i en arkivfil som heter `website.tar` finns och extraheras vid ett angivet mål.</span><span class="sxs-lookup"><span data-stu-id="f8650-134">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

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