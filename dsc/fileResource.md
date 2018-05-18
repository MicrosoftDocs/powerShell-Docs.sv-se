---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-filresurs
ms.openlocfilehash: 86a5dcd97b4163b3780038c815d3de5a523ce4bf
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-file-resource"></a><span data-ttu-id="6be1d-103">DSC-filresurs</span><span class="sxs-lookup"><span data-stu-id="6be1d-103">DSC File Resource</span></span>

> <span data-ttu-id="6be1d-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6be1d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="6be1d-105">Filresurser i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att hantera filer och mappar på målnoden.</span><span class="sxs-lookup"><span data-stu-id="6be1d-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="6be1d-106">**Obs:** om den **MatchSource** egenskap är inställd på **$false** (vilket är standardvärdet), innehållet kopieras cachelagras första gången konfigurationen tillämpas.</span><span class="sxs-lookup"><span data-stu-id="6be1d-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span>
><span data-ttu-id="6be1d-107">Efterföljande program av konfigurationen kommer inte att söka efter uppdaterade filer eller mappar i sökvägen som anges av **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="6be1d-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="6be1d-108">Om du vill söka efter uppdateringar av filer eller mappar i **SourcePath** varje gång konfigurationen tillämpas ange **MatchSource** till **$true**.</span><span class="sxs-lookup"><span data-stu-id="6be1d-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span>

## <a name="syntax"></a><span data-ttu-id="6be1d-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="6be1d-109">Syntax</span></span>
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="6be1d-110">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="6be1d-110">Properties</span></span>

|  <span data-ttu-id="6be1d-111">Egenskap</span><span class="sxs-lookup"><span data-stu-id="6be1d-111">Property</span></span>  |  <span data-ttu-id="6be1d-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6be1d-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="6be1d-113">Målsökväg</span><span class="sxs-lookup"><span data-stu-id="6be1d-113">DestinationPath</span></span>| <span data-ttu-id="6be1d-114">Anger den plats där du vill kontrollera tillståndet för en fil eller katalog.</span><span class="sxs-lookup"><span data-stu-id="6be1d-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="6be1d-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="6be1d-115">Attributes</span></span>| <span data-ttu-id="6be1d-116">Anger tillståndet som attribut för filen eller katalogen.</span><span class="sxs-lookup"><span data-stu-id="6be1d-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>|
| <span data-ttu-id="6be1d-117">Kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="6be1d-117">Checksum</span></span>| <span data-ttu-id="6be1d-118">Anger kontrollsumma ska användas för att fastställa om de två filerna är samma typ.</span><span class="sxs-lookup"><span data-stu-id="6be1d-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="6be1d-119">Om __kontrollsumma__ anges endast filen eller katalogen namn som används för jämförelse.</span><span class="sxs-lookup"><span data-stu-id="6be1d-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="6be1d-120">Giltiga värden är: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span><span class="sxs-lookup"><span data-stu-id="6be1d-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|
| <span data-ttu-id="6be1d-121">Innehåll</span><span class="sxs-lookup"><span data-stu-id="6be1d-121">Contents</span></span>| <span data-ttu-id="6be1d-122">Anger innehållet i en fil, till exempel en viss sträng.</span><span class="sxs-lookup"><span data-stu-id="6be1d-122">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="6be1d-123">autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="6be1d-123">Credential</span></span>| <span data-ttu-id="6be1d-124">Anger de autentiseringsuppgifter som krävs för att komma åt resurser, till exempel källfiler, om sådan åtkomst krävs.</span><span class="sxs-lookup"><span data-stu-id="6be1d-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>|
| <span data-ttu-id="6be1d-125">Se till att</span><span class="sxs-lookup"><span data-stu-id="6be1d-125">Ensure</span></span>| <span data-ttu-id="6be1d-126">Anger om filen eller katalogen finns.</span><span class="sxs-lookup"><span data-stu-id="6be1d-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="6be1d-127">Ange den här egenskapen till ”saknas” för att se till att filen eller katalogen inte finns.</span><span class="sxs-lookup"><span data-stu-id="6be1d-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="6be1d-128">Ange den till ”finns” för att se till att filen eller katalogen finns.</span><span class="sxs-lookup"><span data-stu-id="6be1d-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="6be1d-129">Standardvärdet är ”saknas”.</span><span class="sxs-lookup"><span data-stu-id="6be1d-129">The default is "Present".</span></span>|
| <span data-ttu-id="6be1d-130">Force</span><span class="sxs-lookup"><span data-stu-id="6be1d-130">Force</span></span>| <span data-ttu-id="6be1d-131">Vissa åtgärder (till exempel skriver över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="6be1d-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="6be1d-132">Med hjälp av egenskapen Force åsidosätter sådana fel.</span><span class="sxs-lookup"><span data-stu-id="6be1d-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="6be1d-133">Standardvärdet är __$false__.</span><span class="sxs-lookup"><span data-stu-id="6be1d-133">The default value is __$false__.</span></span>|
| <span data-ttu-id="6be1d-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="6be1d-134">Recurse</span></span>| <span data-ttu-id="6be1d-135">Anger om underkataloger ingår.</span><span class="sxs-lookup"><span data-stu-id="6be1d-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="6be1d-136">Den här egenskapen __$true__ att ange att du vill underkataloger som ska inkluderas.</span><span class="sxs-lookup"><span data-stu-id="6be1d-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="6be1d-137">Standardvärdet är __$false__.</span><span class="sxs-lookup"><span data-stu-id="6be1d-137">The default is __$false__.</span></span> <span data-ttu-id="6be1d-138">**Obs**: den här egenskapen är endast giltig när egenskapen Type har angetts till katalogen.</span><span class="sxs-lookup"><span data-stu-id="6be1d-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>|
| <span data-ttu-id="6be1d-139">dependsOn</span><span class="sxs-lookup"><span data-stu-id="6be1d-139">DependsOn</span></span> | <span data-ttu-id="6be1d-140">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="6be1d-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6be1d-141">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6be1d-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="6be1d-142">Källsökväg</span><span class="sxs-lookup"><span data-stu-id="6be1d-142">SourcePath</span></span>| <span data-ttu-id="6be1d-143">Anger sökvägen som du vill kopiera filen eller mappen resurs.</span><span class="sxs-lookup"><span data-stu-id="6be1d-143">Indicates the path from which to copy the file or folder resource.</span></span>|
| <span data-ttu-id="6be1d-144">Typ</span><span class="sxs-lookup"><span data-stu-id="6be1d-144">Type</span></span>| <span data-ttu-id="6be1d-145">Anger om resursen som konfigureras är en katalog eller fil.</span><span class="sxs-lookup"><span data-stu-id="6be1d-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="6be1d-146">Ange den här egenskapen till ”Directory” för att indikera att resursen är en katalog.</span><span class="sxs-lookup"><span data-stu-id="6be1d-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="6be1d-147">Ange den till ”fil” för att indikera att resursen är en fil.</span><span class="sxs-lookup"><span data-stu-id="6be1d-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="6be1d-148">Standardvärdet är ”fil”.</span><span class="sxs-lookup"><span data-stu-id="6be1d-148">The default value is “File”.</span></span>|
| <span data-ttu-id="6be1d-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="6be1d-149">MatchSource</span></span>| <span data-ttu-id="6be1d-150">Om inställd på standardvärdet __$false__, och alla filer på källan (exempelvis filer A, B och C) kommer att läggas till målet första gången konfigurationen tillämpas.</span><span class="sxs-lookup"><span data-stu-id="6be1d-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="6be1d-151">Om en ny fil (D) läggs till källan kommer den inte att lägga till målet trots att använda konfigurationen igen senare.</span><span class="sxs-lookup"><span data-stu-id="6be1d-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="6be1d-152">Om värdet är __$true__, och varje gång konfigurationen tillämpas nya filerna senare på källan (till exempel fil D i det här exemplet) läggs till målet.</span><span class="sxs-lookup"><span data-stu-id="6be1d-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="6be1d-153">Standardvärdet är **$false**.</span><span class="sxs-lookup"><span data-stu-id="6be1d-153">The default value is **$false**.</span></span>|

## <a name="example"></a><span data-ttu-id="6be1d-154">Exempel</span><span class="sxs-lookup"><span data-stu-id="6be1d-154">Example</span></span>

<span data-ttu-id="6be1d-155">I följande exempel visas hur du använder filresurs så att en katalog med sökvägen `C:\Users\Public\Documents\DSCDemo\DemoSource` på en dator (till exempel ”pull”-server) finns också (tillsammans med alla undermappar) på målnoden.</span><span class="sxs-lookup"><span data-stu-id="6be1d-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="6be1d-156">Dessutom skriver ett bekräftande meddelande till loggfilen när du är klar och innehåller en instruktion för att säkerställa att filkontroll-åtgärden körs innan loggningsåtgärden.</span><span class="sxs-lookup"><span data-stu-id="6be1d-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```