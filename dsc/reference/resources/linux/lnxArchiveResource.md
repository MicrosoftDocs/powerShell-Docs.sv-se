---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxArchive-resurs
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078052"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="71095-103">DSC för Linux nxArchive-resurs</span><span class="sxs-lookup"><span data-stu-id="71095-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="71095-104">Den **nxArchive** resurs i PowerShell Desired State Configuration (DSC) är en mekanism för att packa upp (.tar, .zip) arkivfiler på en specifik sökväg på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="71095-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="71095-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="71095-105">Syntax</span></span>

```
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

## <a name="properties"></a><span data-ttu-id="71095-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="71095-106">Properties</span></span>

|  <span data-ttu-id="71095-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="71095-107">Property</span></span> |  <span data-ttu-id="71095-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="71095-108">Description</span></span> |
|---|---|
| <span data-ttu-id="71095-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="71095-109">SourcePath</span></span>| <span data-ttu-id="71095-110">Anger källsökvägen för arkivfilen.</span><span class="sxs-lookup"><span data-stu-id="71095-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="71095-111">Detta bör vara en .tar .zip, eller..GZ-filen.</span><span class="sxs-lookup"><span data-stu-id="71095-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
| <span data-ttu-id="71095-112">Målsökväg</span><span class="sxs-lookup"><span data-stu-id="71095-112">DestinationPath</span></span>| <span data-ttu-id="71095-113">Anger den plats där du vill kontrollera arkivinnehållet extraheras.</span><span class="sxs-lookup"><span data-stu-id="71095-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="71095-114">Kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="71095-114">Checksum</span></span>| <span data-ttu-id="71095-115">Definierar den typ som ska användas när du bestämmer om käll-arkivet har uppdaterats.</span><span class="sxs-lookup"><span data-stu-id="71095-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="71095-116">Värden är: ”ctime”, ”mtime” eller ”md5”.</span><span class="sxs-lookup"><span data-stu-id="71095-116">Values are: "ctime", "mtime", or "md5".</span></span> <span data-ttu-id="71095-117">Standardvärdet är ”md5”.</span><span class="sxs-lookup"><span data-stu-id="71095-117">The default value is "md5".</span></span>|
| <span data-ttu-id="71095-118">Force</span><span class="sxs-lookup"><span data-stu-id="71095-118">Force</span></span>| <span data-ttu-id="71095-119">Vissa åtgärder för sammansättningsfiler (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="71095-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="71095-120">Med hjälp av den **kraft** egenskapen åsidosätter sådana fel.</span><span class="sxs-lookup"><span data-stu-id="71095-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="71095-121">Standardvärdet är **$false**.</span><span class="sxs-lookup"><span data-stu-id="71095-121">The default value is **$false**.</span></span>|
| <span data-ttu-id="71095-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="71095-122">DependsOn</span></span> | <span data-ttu-id="71095-123">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="71095-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="71095-124">Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="71095-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="71095-125">Se till att</span><span class="sxs-lookup"><span data-stu-id="71095-125">Ensure</span></span>| <span data-ttu-id="71095-126">Avgör om du vill kontrollera om innehållet i arkivet på den **mål**.</span><span class="sxs-lookup"><span data-stu-id="71095-126">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="71095-127">Ange egenskapen ”aktuella” för att säkerställa att innehållet finns.</span><span class="sxs-lookup"><span data-stu-id="71095-127">Set this property to "Present" to ensure the contents exist.</span></span> <span data-ttu-id="71095-128">Ange den till ”inte” för att se till att de inte finns.</span><span class="sxs-lookup"><span data-stu-id="71095-128">Set it to "Absent" to ensure they do not exist.</span></span> <span data-ttu-id="71095-129">Standardvärdet är ”tillgänglig”.</span><span class="sxs-lookup"><span data-stu-id="71095-129">The default value is "Present".</span></span>|

## <a name="example"></a><span data-ttu-id="71095-130">Exempel</span><span class="sxs-lookup"><span data-stu-id="71095-130">Example</span></span>

<span data-ttu-id="71095-131">I följande exempel visas hur du använder den **nxArchive** resurs så att innehållet i en arkivfil heter `website.tar` finns och har extraherats vid ett givet mål.</span><span class="sxs-lookup"><span data-stu-id="71095-131">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```