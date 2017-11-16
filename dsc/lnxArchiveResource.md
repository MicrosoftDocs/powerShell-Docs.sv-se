---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "DSC för Linux nxArchive resurs"
ms.openlocfilehash: da647432e14d2a4a3ceb2a36c7dee2dbfd350116
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="d113b-103">DSC för Linux nxArchive resurs</span><span class="sxs-lookup"><span data-stu-id="d113b-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="d113b-104">Den **nxArchive** resurs i PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att packa upp (.tar, .zip) arkivfiler på en specifik sökväg på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="d113b-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="d113b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d113b-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="d113b-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="d113b-106">Properties</span></span>

|  <span data-ttu-id="d113b-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="d113b-107">Property</span></span> |  <span data-ttu-id="d113b-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d113b-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="d113b-109">Källsökväg</span><span class="sxs-lookup"><span data-stu-id="d113b-109">SourcePath</span></span>| <span data-ttu-id="d113b-110">Anger källsökvägen för arkivfilen.</span><span class="sxs-lookup"><span data-stu-id="d113b-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="d113b-111">Detta bör vara en .tar .zip, eller..GZ-filen.</span><span class="sxs-lookup"><span data-stu-id="d113b-111">This should be a .tar, .zip, or .tar.gz file.</span></span> | 
| <span data-ttu-id="d113b-112">Målsökväg</span><span class="sxs-lookup"><span data-stu-id="d113b-112">DestinationPath</span></span>| <span data-ttu-id="d113b-113">Anger den plats där du vill se till att arkivera innehåll extraheras.</span><span class="sxs-lookup"><span data-stu-id="d113b-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span>| 
| <span data-ttu-id="d113b-114">Kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="d113b-114">Checksum</span></span>| <span data-ttu-id="d113b-115">Definierar den typ som används när du fastställer om arkivet som källa har uppdaterats.</span><span class="sxs-lookup"><span data-stu-id="d113b-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="d113b-116">Värden är: ”ctime”, ”mtime” eller ”md5”.</span><span class="sxs-lookup"><span data-stu-id="d113b-116">Values are: "ctime", "mtime", or "md5".</span></span> <span data-ttu-id="d113b-117">Standardvärdet är ”md5”.</span><span class="sxs-lookup"><span data-stu-id="d113b-117">The default value is "md5".</span></span>| 
| <span data-ttu-id="d113b-118">Force</span><span class="sxs-lookup"><span data-stu-id="d113b-118">Force</span></span>| <span data-ttu-id="d113b-119">Vissa åtgärder (till exempel skriver över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="d113b-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="d113b-120">Med hjälp av den **kraft** egenskapen åsidosätter sådana fel.</span><span class="sxs-lookup"><span data-stu-id="d113b-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="d113b-121">Standardvärdet är **$false**.</span><span class="sxs-lookup"><span data-stu-id="d113b-121">The default value is **$false**.</span></span>| 
| <span data-ttu-id="d113b-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="d113b-122">DependsOn</span></span> | <span data-ttu-id="d113b-123">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="d113b-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d113b-124">Till exempel om den **ID** resursens configuration skriptblock som du vill köra först är **ResourceName** och dess typ är **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d113b-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="d113b-125">Se till att</span><span class="sxs-lookup"><span data-stu-id="d113b-125">Ensure</span></span>| <span data-ttu-id="d113b-126">Anger om du vill kontrollera om det finns innehåll till arkivet på den **mål**.</span><span class="sxs-lookup"><span data-stu-id="d113b-126">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="d113b-127">Ange egenskapen ”aktuella” för att säkerställa att innehållet finns.</span><span class="sxs-lookup"><span data-stu-id="d113b-127">Set this property to "Present" to ensure the contents exist.</span></span> <span data-ttu-id="d113b-128">Ange den till ”saknas” för att säkerställa att de inte finns.</span><span class="sxs-lookup"><span data-stu-id="d113b-128">Set it to "Absent" to ensure they do not exist.</span></span> <span data-ttu-id="d113b-129">Standardvärdet är ”saknas”.</span><span class="sxs-lookup"><span data-stu-id="d113b-129">The default value is "Present".</span></span>| 

## <a name="example"></a><span data-ttu-id="d113b-130">Exempel</span><span class="sxs-lookup"><span data-stu-id="d113b-130">Example</span></span>

<span data-ttu-id="d113b-131">I följande exempel visas hur du använder den **nxArchive** resurs så att innehållet i en fil för `website.tar` finns och har extraherats vid ett givet mål.</span><span class="sxs-lookup"><span data-stu-id="d113b-131">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

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

