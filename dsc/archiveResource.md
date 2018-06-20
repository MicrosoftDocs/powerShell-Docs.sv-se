---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-Arkiv resurs
ms.openlocfilehash: 458b4f0f20dc96dab62e709183c25ff57d971aae
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219478"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="bdbfa-103">DSC-Arkiv resurs</span><span class="sxs-lookup"><span data-stu-id="bdbfa-103">DSC Archive Resource</span></span>

> <span data-ttu-id="bdbfa-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bdbfa-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="bdbfa-105">Arkiv-resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att packa upp arkivfiler (.zip) på en angiven sökväg.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="bdbfa-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="bdbfa-106">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="bdbfa-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="bdbfa-107">Properties</span></span>

|  <span data-ttu-id="bdbfa-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="bdbfa-108">Property</span></span>  |  <span data-ttu-id="bdbfa-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bdbfa-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="bdbfa-110">Mål</span><span class="sxs-lookup"><span data-stu-id="bdbfa-110">Destination</span></span>| <span data-ttu-id="bdbfa-111">Anger den plats där du vill se till att arkivera innehåll extraheras.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="bdbfa-112">Sökväg</span><span class="sxs-lookup"><span data-stu-id="bdbfa-112">Path</span></span>| <span data-ttu-id="bdbfa-113">Anger källsökvägen för arkivfilen.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-113">Specifies the source path of the archive file.</span></span>|
| <span data-ttu-id="bdbfa-114">__Kontrollsumma__</span><span class="sxs-lookup"><span data-stu-id="bdbfa-114">__Checksum__</span></span>| <span data-ttu-id="bdbfa-115">Definierar den typ som används när du fastställer om två filerna är samma.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="bdbfa-116">Om __kontrollsumma__ anges endast filen eller katalogen namn som används för jämförelse.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-116">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="bdbfa-117">Giltiga värden är: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate ingen (standard).</span><span class="sxs-lookup"><span data-stu-id="bdbfa-117">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (default).</span></span> <span data-ttu-id="bdbfa-118">Om du anger __kontrollsumma__ utan __verifiera__, konfigurationen misslyckas.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-118">If you specify __Checksum__ without __Validate__, the configuration will fail.</span></span>|
| <span data-ttu-id="bdbfa-119">Se till att</span><span class="sxs-lookup"><span data-stu-id="bdbfa-119">Ensure</span></span>| <span data-ttu-id="bdbfa-120">Anger om du vill kontrollera om det finns innehåll till arkivet på den __mål__.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-120">Determines whether to check if the content of the archive exists at the __Destination__.</span></span> <span data-ttu-id="bdbfa-121">Den här egenskapen __finns__ så innehållet finns.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-121">Set this property to __Present__ to ensure the contents exist.</span></span> <span data-ttu-id="bdbfa-122">Ange det till __saknas__ så de inte finns.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-122">Set it to __Absent__ to ensure they do not exist.</span></span> <span data-ttu-id="bdbfa-123">Standardvärdet är __finns__.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-123">The default value is __Present__.</span></span>|
| <span data-ttu-id="bdbfa-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="bdbfa-124">DependsOn</span></span> | <span data-ttu-id="bdbfa-125">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bdbfa-126">Till exempel om ID för resursen configuration skriptblock som du vill köra först ResourceName och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="bdbfa-127">Validera</span><span class="sxs-lookup"><span data-stu-id="bdbfa-127">Validate</span></span>| <span data-ttu-id="bdbfa-128">Använder egenskapen kontrollsumma för att avgöra om arkivet matchar signaturen.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-128">Uses the Checksum property to determine if the archive matches the signature.</span></span> <span data-ttu-id="bdbfa-129">Om du anger kontrollsumma utan att verifiera misslyckas konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-129">If you specify Checksum without Validate, the configuration will fail.</span></span> <span data-ttu-id="bdbfa-130">Om du anger verifiera utan kontrollsumma, används en SHA-256-kontrollsumma som standard.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-130">If you specify Validate without Checksum, a SHA-256 checksum is used by default.</span></span>|
| <span data-ttu-id="bdbfa-131">Force</span><span class="sxs-lookup"><span data-stu-id="bdbfa-131">Force</span></span>| <span data-ttu-id="bdbfa-132">Vissa åtgärder (till exempel skriver över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="bdbfa-133">Med hjälp av egenskapen Force åsidosätter sådana fel.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-133">Using the Force property overrides such errors.</span></span> <span data-ttu-id="bdbfa-134">Standardvärdet är False.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-134">The default value is False.</span></span>|

## <a name="example"></a><span data-ttu-id="bdbfa-135">Exempel</span><span class="sxs-lookup"><span data-stu-id="bdbfa-135">Example</span></span>

<span data-ttu-id="bdbfa-136">I följande exempel visas hur du använder Arkiv-resurs så att innehållet i en fil kallad Test.zip finns och har extraherats vid ett givet mål.</span><span class="sxs-lookup"><span data-stu-id="bdbfa-136">The following example shows how to use the Archive resource to ensure that the contents of an archive file called Test.zip exist and are extracted at a given destination.</span></span>

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```