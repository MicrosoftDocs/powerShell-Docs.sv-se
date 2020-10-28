---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-Arkiv resurs
description: DSC-Arkiv resurs
ms.openlocfilehash: 1116ed068fab09b61daaeb7cdeba7bdbd27da6d8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648687"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="79e97-103">DSC-Arkiv resurs</span><span class="sxs-lookup"><span data-stu-id="79e97-103">DSC Archive Resource</span></span>

> <span data-ttu-id="79e97-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="79e97-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="79e97-105">Arkiv resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att packa upp arkiv (zip-filer) vid en angiven sökväg.</span><span class="sxs-lookup"><span data-stu-id="79e97-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="79e97-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="79e97-106">Syntax</span></span>

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="79e97-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="79e97-107">Properties</span></span>

|<span data-ttu-id="79e97-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="79e97-108">Property</span></span> |<span data-ttu-id="79e97-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="79e97-109">Description</span></span> |
|---|---|
| <span data-ttu-id="79e97-110">Mål</span><span class="sxs-lookup"><span data-stu-id="79e97-110">Destination</span></span> | <span data-ttu-id="79e97-111">Anger den plats där du vill se till att Arkiv innehållet extraheras.</span><span class="sxs-lookup"><span data-stu-id="79e97-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
| <span data-ttu-id="79e97-112">Sökväg</span><span class="sxs-lookup"><span data-stu-id="79e97-112">Path</span></span> | <span data-ttu-id="79e97-113">Anger Arkiv filens käll Sök väg.</span><span class="sxs-lookup"><span data-stu-id="79e97-113">Specifies the source path of the archive file.</span></span> |
| <span data-ttu-id="79e97-114">Kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="79e97-114">Checksum</span></span> | <span data-ttu-id="79e97-115">Definierar den typ som ska användas för att avgöra om två filer är identiska.</span><span class="sxs-lookup"><span data-stu-id="79e97-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="79e97-116">Om ingen **kontroll Summa** anges används bara fil-eller katalog namnet för jämförelse.</span><span class="sxs-lookup"><span data-stu-id="79e97-116">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="79e97-117">Giltiga värden är: **SHA-1** , **SHA-256** , **SHA-512** , **createdDate** , **modifiedDate** .</span><span class="sxs-lookup"><span data-stu-id="79e97-117">Valid values include: **SHA-1** , **SHA-256** , **SHA-512** , **createdDate** , **modifiedDate** .</span></span> <span data-ttu-id="79e97-118">Om du anger **kontroll Summa** utan att validera, kommer konfigurationen att Miss **förklaras** .</span><span class="sxs-lookup"><span data-stu-id="79e97-118">If you specify **Checksum** without **Validate** , the configuration will fail.</span></span> |
| <span data-ttu-id="79e97-119">Autentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="79e97-119">Credential</span></span> | <span data-ttu-id="79e97-120">Autentiseringsuppgifterna för ett användar konto med behörighet att komma åt den angivna Arkiv Sök vägen och målet vid behov.</span><span class="sxs-lookup"><span data-stu-id="79e97-120">The credential of a user account with permissions to access the specified archive path and destination if needed.</span></span> |
| <span data-ttu-id="79e97-121">Force</span><span class="sxs-lookup"><span data-stu-id="79e97-121">Force</span></span> | <span data-ttu-id="79e97-122">Vissa fil åtgärder (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="79e97-122">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="79e97-123">Om du använder **Force** -egenskapen åsidosätts sådana fel.</span><span class="sxs-lookup"><span data-stu-id="79e97-123">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="79e97-124">Standardvärdet är **false** .</span><span class="sxs-lookup"><span data-stu-id="79e97-124">The default value is **False** .</span></span> |
| <span data-ttu-id="79e97-125">Verifiera</span><span class="sxs-lookup"><span data-stu-id="79e97-125">Validate</span></span>| <span data-ttu-id="79e97-126">Använder egenskapen **kontroll Summa** för att avgöra om arkivet matchar signaturen.</span><span class="sxs-lookup"><span data-stu-id="79e97-126">Uses the **Checksum** property to determine if the archive matches the signature.</span></span> <span data-ttu-id="79e97-127">Om du anger **kontroll Summa** utan att validera, kommer konfigurationen att Miss **förklaras** .</span><span class="sxs-lookup"><span data-stu-id="79e97-127">If you specify **Checksum** without **Validate** , the configuration will fail.</span></span> <span data-ttu-id="79e97-128">Om du anger **Verifiera** utan **kontroll Summa** används en _SHA-256-_ **kontrollsumma** som standard.</span><span class="sxs-lookup"><span data-stu-id="79e97-128">If you specify **Validate** without **Checksum** , a _SHA-256_ **Checksum** is used by default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="79e97-129">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="79e97-129">Common properties</span></span>

|<span data-ttu-id="79e97-130">Egenskap</span><span class="sxs-lookup"><span data-stu-id="79e97-130">Property</span></span> |<span data-ttu-id="79e97-131">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="79e97-131">Description</span></span> |
|---|---|
|<span data-ttu-id="79e97-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="79e97-132">DependsOn</span></span> |<span data-ttu-id="79e97-133">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="79e97-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="79e97-134">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="79e97-134">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="79e97-135">Kontrol</span><span class="sxs-lookup"><span data-stu-id="79e97-135">Ensure</span></span> |<span data-ttu-id="79e97-136">Avgör om du ska kontrol lera om arkivets innehåll finns vid **målet** .</span><span class="sxs-lookup"><span data-stu-id="79e97-136">Determines whether to check if the content of the archive exists at the **Destination** .</span></span> <span data-ttu-id="79e97-137">Ange att den här egenskapen **finns för att** se till att innehållet finns.</span><span class="sxs-lookup"><span data-stu-id="79e97-137">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="79e97-138">Ange det som **frånvarande** för att se till att de inte finns.</span><span class="sxs-lookup"><span data-stu-id="79e97-138">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="79e97-139">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="79e97-139">The default value is **Present** .</span></span> |
|<span data-ttu-id="79e97-140">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="79e97-140">PsDscRunAsCredential</span></span> |<span data-ttu-id="79e97-141">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="79e97-141">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="79e97-142">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="79e97-142">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="79e97-143">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="79e97-143">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="79e97-144">Exempel</span><span class="sxs-lookup"><span data-stu-id="79e97-144">Example</span></span>

<span data-ttu-id="79e97-145">I följande exempel visas hur du använder Arkiv resursen för att se till att innehållet i en arkivfil som heter `Test.zip` finns och extraheras vid ett angivet mål med och auktoriseras.</span><span class="sxs-lookup"><span data-stu-id="79e97-145">The following example shows how to use the Archive resource to ensure that the contents of an archive file called `Test.zip` exist and are extracted at a given destination using and authorized.</span></span>

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```
