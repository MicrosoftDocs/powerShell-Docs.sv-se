---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-Arkivera resursen
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048685"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="6cec0-103">DSC-Arkivera resursen</span><span class="sxs-lookup"><span data-stu-id="6cec0-103">DSC Archive Resource</span></span>

> <span data-ttu-id="6cec0-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6cec0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="6cec0-105">Arkivera resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att packa upp arkivfiler (.zip) på en specifik sökväg.</span><span class="sxs-lookup"><span data-stu-id="6cec0-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="6cec0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6cec0-106">Syntax</span></span>
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="6cec0-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="6cec0-107">Properties</span></span>

|  <span data-ttu-id="6cec0-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="6cec0-108">Property</span></span>  |  <span data-ttu-id="6cec0-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6cec0-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="6cec0-110">Mål</span><span class="sxs-lookup"><span data-stu-id="6cec0-110">Destination</span></span>| <span data-ttu-id="6cec0-111">Anger den plats där du vill kontrollera arkivinnehållet extraheras.</span><span class="sxs-lookup"><span data-stu-id="6cec0-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="6cec0-112">Sökväg</span><span class="sxs-lookup"><span data-stu-id="6cec0-112">Path</span></span>| <span data-ttu-id="6cec0-113">Anger källsökvägen för arkivfilen.</span><span class="sxs-lookup"><span data-stu-id="6cec0-113">Specifies the source path of the archive file.</span></span>|
| <span data-ttu-id="6cec0-114">__Kontrollsumma__</span><span class="sxs-lookup"><span data-stu-id="6cec0-114">__Checksum__</span></span>| <span data-ttu-id="6cec0-115">Definierar den typ som ska användas när du bestämmer om två filer är lika.</span><span class="sxs-lookup"><span data-stu-id="6cec0-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="6cec0-116">Om __kontrollsumma__ inte anges endast filen eller katalogen namnet används för jämförelse.</span><span class="sxs-lookup"><span data-stu-id="6cec0-116">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="6cec0-117">Giltiga värden är: SHA-1, SHA-256, SHA-512, createdDate, modifieddate kunde none (standard).</span><span class="sxs-lookup"><span data-stu-id="6cec0-117">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (default).</span></span> <span data-ttu-id="6cec0-118">Om du anger __kontrollsumma__ utan __verifiera__, konfigurationen misslyckas.</span><span class="sxs-lookup"><span data-stu-id="6cec0-118">If you specify __Checksum__ without __Validate__, the configuration will fail.</span></span>|
| <span data-ttu-id="6cec0-119">Se till att</span><span class="sxs-lookup"><span data-stu-id="6cec0-119">Ensure</span></span>| <span data-ttu-id="6cec0-120">Avgör om du vill kontrollera om innehållet i arkivet på den __mål__.</span><span class="sxs-lookup"><span data-stu-id="6cec0-120">Determines whether to check if the content of the archive exists at the __Destination__.</span></span> <span data-ttu-id="6cec0-121">Den här egenskapen __finns__ att säkerställa att innehållet finns.</span><span class="sxs-lookup"><span data-stu-id="6cec0-121">Set this property to __Present__ to ensure the contents exist.</span></span> <span data-ttu-id="6cec0-122">Ange den till __frånvarande__ att se till att de inte finns.</span><span class="sxs-lookup"><span data-stu-id="6cec0-122">Set it to __Absent__ to ensure they do not exist.</span></span> <span data-ttu-id="6cec0-123">Standardvärdet är __finns__.</span><span class="sxs-lookup"><span data-stu-id="6cec0-123">The default value is __Present__.</span></span>|
| <span data-ttu-id="6cec0-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6cec0-124">DependsOn</span></span> | <span data-ttu-id="6cec0-125">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="6cec0-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6cec0-126">Till exempel om ID för resursen configuration skriptblocket som du vill köra först ResourceName och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6cec0-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="6cec0-127">Verifiera</span><span class="sxs-lookup"><span data-stu-id="6cec0-127">Validate</span></span>| <span data-ttu-id="6cec0-128">Använder egenskapen kontrollsumma för att avgöra om arkivet matchar signaturen.</span><span class="sxs-lookup"><span data-stu-id="6cec0-128">Uses the Checksum property to determine if the archive matches the signature.</span></span> <span data-ttu-id="6cec0-129">Om du anger kontrollsumma utan att verifiera misslyckas konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6cec0-129">If you specify Checksum without Validate, the configuration will fail.</span></span> <span data-ttu-id="6cec0-130">Om du anger verifiera utan kontrollsumma, används en SHA-256-kontrollsumma som standard.</span><span class="sxs-lookup"><span data-stu-id="6cec0-130">If you specify Validate without Checksum, a SHA-256 checksum is used by default.</span></span>|
| <span data-ttu-id="6cec0-131">Force</span><span class="sxs-lookup"><span data-stu-id="6cec0-131">Force</span></span>| <span data-ttu-id="6cec0-132">Vissa åtgärder för sammansättningsfiler (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="6cec0-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="6cec0-133">Med hjälp av egenskapen Force åsidosätter sådana fel.</span><span class="sxs-lookup"><span data-stu-id="6cec0-133">Using the Force property overrides such errors.</span></span> <span data-ttu-id="6cec0-134">Standardvärdet är FALSKT.</span><span class="sxs-lookup"><span data-stu-id="6cec0-134">The default value is False.</span></span>|

## <a name="example"></a><span data-ttu-id="6cec0-135">Exempel</span><span class="sxs-lookup"><span data-stu-id="6cec0-135">Example</span></span>

<span data-ttu-id="6cec0-136">I följande exempel visar hur du använder Arkivera resursen så att innehållet i en arkivfil kallas Test.zip finns och har extraherats vid ett givet mål.</span><span class="sxs-lookup"><span data-stu-id="6cec0-136">The following example shows how to use the Archive resource to ensure that the contents of an archive file called Test.zip exist and are extracted at a given destination.</span></span>

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```