---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-Arkiv resurs
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942519"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="a6cd8-103">DSC-Arkiv resurs</span><span class="sxs-lookup"><span data-stu-id="a6cd8-103">DSC Archive Resource</span></span>

> <span data-ttu-id="a6cd8-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="a6cd8-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="a6cd8-105">Arkiv resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att packa upp arkiv (zip-filer) vid en angiven sökväg.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="a6cd8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a6cd8-106">Syntax</span></span>

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="a6cd8-107">properties</span><span class="sxs-lookup"><span data-stu-id="a6cd8-107">Properties</span></span>

|<span data-ttu-id="a6cd8-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="a6cd8-108">Property</span></span> |<span data-ttu-id="a6cd8-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a6cd8-109">Description</span></span> |
|---|---|
|<span data-ttu-id="a6cd8-110">Destination</span><span class="sxs-lookup"><span data-stu-id="a6cd8-110">Destination</span></span> |<span data-ttu-id="a6cd8-111">Anger den plats där du vill se till att Arkiv innehållet extraheras.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="a6cd8-112">`Path`</span><span class="sxs-lookup"><span data-stu-id="a6cd8-112">Path</span></span> |<span data-ttu-id="a6cd8-113">Anger Arkiv filens käll Sök väg.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-113">Specifies the source path of the archive file.</span></span> |
|<span data-ttu-id="a6cd8-114">Kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="a6cd8-114">Checksum</span></span> |<span data-ttu-id="a6cd8-115">Definierar den typ som ska användas för att avgöra om två filer är identiska.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="a6cd8-116">Om ingen **kontroll Summa** anges används bara fil-eller katalog namnet för jämförelse.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-116">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="a6cd8-117">Giltiga värden är: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-117">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> <span data-ttu-id="a6cd8-118">Om du anger **kontroll Summa** utan att validera, kommer konfigurationen att Miss **förklaras**.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-118">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> |
|<span data-ttu-id="a6cd8-119">Force</span><span class="sxs-lookup"><span data-stu-id="a6cd8-119">Force</span></span> |<span data-ttu-id="a6cd8-120">Vissa fil åtgärder (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-120">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="a6cd8-121">Om du använder **Force** -egenskapen åsidosätts sådana fel.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-121">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="a6cd8-122">Standardvärdet är **false**.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-122">The default value is **False**.</span></span> |
|<span data-ttu-id="a6cd8-123">kontrollerar</span><span class="sxs-lookup"><span data-stu-id="a6cd8-123">Validate</span></span>| <span data-ttu-id="a6cd8-124">Använder egenskapen **kontroll Summa** för att avgöra om arkivet matchar signaturen.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-124">Uses the **Checksum** property to determine if the archive matches the signature.</span></span> <span data-ttu-id="a6cd8-125">Om du anger **kontroll Summa** utan att validera, kommer konfigurationen att Miss **förklaras**.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-125">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> <span data-ttu-id="a6cd8-126">Om du anger **Verifiera** utan **kontroll Summa**används en _SHA-256-_ **kontrollsumma** som standard.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-126">If you specify **Validate** without **Checksum**, a _SHA-256_ **Checksum** is used by default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="a6cd8-127">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="a6cd8-127">Common properties</span></span>

|<span data-ttu-id="a6cd8-128">Egenskap</span><span class="sxs-lookup"><span data-stu-id="a6cd8-128">Property</span></span> |<span data-ttu-id="a6cd8-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a6cd8-129">Description</span></span> |
|---|---|
|<span data-ttu-id="a6cd8-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a6cd8-130">DependsOn</span></span> |<span data-ttu-id="a6cd8-131">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a6cd8-132">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="a6cd8-133">Kontrol</span><span class="sxs-lookup"><span data-stu-id="a6cd8-133">Ensure</span></span> |<span data-ttu-id="a6cd8-134">Avgör om du ska kontrol lera om arkivets innehåll finns vid **målet**.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-134">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="a6cd8-135">Ange att den här egenskapen **finns för att** se till att innehållet finns.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-135">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="a6cd8-136">Ange det som **frånvarande** för att se till att de inte finns.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-136">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="a6cd8-137">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="a6cd8-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="a6cd8-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a6cd8-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="a6cd8-139">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="a6cd8-140">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="a6cd8-141">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="a6cd8-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="a6cd8-142">Exempel</span><span class="sxs-lookup"><span data-stu-id="a6cd8-142">Example</span></span>

<span data-ttu-id="a6cd8-143">Följande exempel visar hur du använder Arkiv resursen för att kontrol lera att innehållet i en arkivfil som heter `Test.zip` finns och extraheras vid ett angivet mål.</span><span class="sxs-lookup"><span data-stu-id="a6cd8-143">The following example shows how to use the Archive resource to ensure that the contents of an archive file called `Test.zip` exist and are extracted at a given destination.</span></span>

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```