---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-filresurs
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048748"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="59960-103">DSC-filresurs</span><span class="sxs-lookup"><span data-stu-id="59960-103">DSC File Resource</span></span>

> <span data-ttu-id="59960-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="59960-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="59960-105">File-resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att hantera filer och mappar på målnoden.</span><span class="sxs-lookup"><span data-stu-id="59960-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="59960-106">**Obs:** Om den **MatchSource** är inställd på **$false** (vilket är standardvärdet), kopieras innehållet cachelagras första gången konfigurationen används.</span><span class="sxs-lookup"><span data-stu-id="59960-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span>
><span data-ttu-id="59960-107">Efterföljande program av konfigurationen inte att söka efter uppdaterade filer och/eller mappar i sökvägen som angetts av **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="59960-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="59960-108">Om du vill söka efter uppdateringar till filer och/eller mappar i **SourcePath** varje gång konfigurationen används, ange **MatchSource** till **$true**.</span><span class="sxs-lookup"><span data-stu-id="59960-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span>

## <a name="syntax"></a><span data-ttu-id="59960-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="59960-109">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="59960-110">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="59960-110">Properties</span></span>

|  <span data-ttu-id="59960-111">Egenskap</span><span class="sxs-lookup"><span data-stu-id="59960-111">Property</span></span>  |  <span data-ttu-id="59960-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="59960-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="59960-113">Målsökväg</span><span class="sxs-lookup"><span data-stu-id="59960-113">DestinationPath</span></span>| <span data-ttu-id="59960-114">Anger den plats där du vill kontrollera status för en fil eller katalog.</span><span class="sxs-lookup"><span data-stu-id="59960-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="59960-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="59960-115">Attributes</span></span>| <span data-ttu-id="59960-116">Anger det önskade tillståndet för attribut för den aktuella filen eller katalogen.</span><span class="sxs-lookup"><span data-stu-id="59960-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>|
| <span data-ttu-id="59960-117">Kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="59960-117">Checksum</span></span>| <span data-ttu-id="59960-118">Anger kontrollsumma ska användas för att avgöra om de två filerna är samma typ.</span><span class="sxs-lookup"><span data-stu-id="59960-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="59960-119">Om __kontrollsumma__ inte anges endast filen eller katalogen namnet används för jämförelse.</span><span class="sxs-lookup"><span data-stu-id="59960-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="59960-120">Giltiga värden är: SHA-1, SHA-256, SHA-512, createdDate, modifieddate kunde.</span><span class="sxs-lookup"><span data-stu-id="59960-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|
| <span data-ttu-id="59960-121">Innehåll</span><span class="sxs-lookup"><span data-stu-id="59960-121">Contents</span></span>| <span data-ttu-id="59960-122">Anger innehållet i en fil, till exempel en viss sträng.</span><span class="sxs-lookup"><span data-stu-id="59960-122">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="59960-123">Autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="59960-123">Credential</span></span>| <span data-ttu-id="59960-124">Anger de autentiseringsuppgifter som krävs för att komma åt resurser, till exempel källfiler, om sådan åtkomst krävs.</span><span class="sxs-lookup"><span data-stu-id="59960-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>|
| <span data-ttu-id="59960-125">Se till att</span><span class="sxs-lookup"><span data-stu-id="59960-125">Ensure</span></span>| <span data-ttu-id="59960-126">Anger om filen eller katalogen finns.</span><span class="sxs-lookup"><span data-stu-id="59960-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="59960-127">Ange den här egenskapen till ”” så att filen eller katalogen inte finns.</span><span class="sxs-lookup"><span data-stu-id="59960-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="59960-128">Ange den ”aktuella” för att se till att filen eller katalogen finns.</span><span class="sxs-lookup"><span data-stu-id="59960-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="59960-129">Standardvärdet är ”tillgänglig”.</span><span class="sxs-lookup"><span data-stu-id="59960-129">The default is "Present".</span></span>|
| <span data-ttu-id="59960-130">Force</span><span class="sxs-lookup"><span data-stu-id="59960-130">Force</span></span>| <span data-ttu-id="59960-131">Vissa åtgärder för sammansättningsfiler (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="59960-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="59960-132">Med hjälp av egenskapen Force åsidosätter sådana fel.</span><span class="sxs-lookup"><span data-stu-id="59960-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="59960-133">Standardvärdet är __$false__.</span><span class="sxs-lookup"><span data-stu-id="59960-133">The default value is __$false__.</span></span>|
| <span data-ttu-id="59960-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="59960-134">Recurse</span></span>| <span data-ttu-id="59960-135">Anger om underkataloger ingår.</span><span class="sxs-lookup"><span data-stu-id="59960-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="59960-136">Den här egenskapen __$true__ att indikera att du vill att underkataloger som ska tas med.</span><span class="sxs-lookup"><span data-stu-id="59960-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="59960-137">Standardvärdet är __$false__.</span><span class="sxs-lookup"><span data-stu-id="59960-137">The default is __$false__.</span></span> <span data-ttu-id="59960-138">**Obs**: Den här egenskapen gäller endast när egenskapen Type har angetts till katalogen.</span><span class="sxs-lookup"><span data-stu-id="59960-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>|
| <span data-ttu-id="59960-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="59960-139">DependsOn</span></span> | <span data-ttu-id="59960-140">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="59960-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="59960-141">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="59960-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="59960-142">Källsökväg</span><span class="sxs-lookup"><span data-stu-id="59960-142">SourcePath</span></span>| <span data-ttu-id="59960-143">Anger sökvägen som du vill kopiera filen eller mappen resursen från.</span><span class="sxs-lookup"><span data-stu-id="59960-143">Indicates the path from which to copy the file or folder resource.</span></span>|
| <span data-ttu-id="59960-144">Typ</span><span class="sxs-lookup"><span data-stu-id="59960-144">Type</span></span>| <span data-ttu-id="59960-145">Anger om resursen som konfigureras är en katalog eller en fil.</span><span class="sxs-lookup"><span data-stu-id="59960-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="59960-146">Ange egenskapen till ”Directory” för att indikera att resursen är en katalog.</span><span class="sxs-lookup"><span data-stu-id="59960-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="59960-147">Ange den till ”fil” för att indikera att resursen är en fil.</span><span class="sxs-lookup"><span data-stu-id="59960-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="59960-148">Standardvärdet är ”fil”.</span><span class="sxs-lookup"><span data-stu-id="59960-148">The default value is “File”.</span></span>|
| <span data-ttu-id="59960-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="59960-149">MatchSource</span></span>| <span data-ttu-id="59960-150">Om inställd på standardvärdet __$false__, och sedan alla filer på källan (t.ex, filer A, B och C) kommer att läggas till målet första gången konfigurationen används.</span><span class="sxs-lookup"><span data-stu-id="59960-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="59960-151">Om en ny fil (D) läggs till i källan, läggs det inte till mål, även när konfigurationen används igen senare.</span><span class="sxs-lookup"><span data-stu-id="59960-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="59960-152">Om värdet är __$true__, och sedan varje gång konfigurationen används nya filerna senare finns på källan (t.ex filer D i det här exemplet) läggs till målet.</span><span class="sxs-lookup"><span data-stu-id="59960-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="59960-153">Standardvärdet är **$false**.</span><span class="sxs-lookup"><span data-stu-id="59960-153">The default value is **$false**.</span></span>|

## <a name="example"></a><span data-ttu-id="59960-154">Exempel</span><span class="sxs-lookup"><span data-stu-id="59960-154">Example</span></span>

<span data-ttu-id="59960-155">I följande exempel visas hur du använder File-resursen för att säkerställa att en katalog med sökvägen `C:\Users\Public\Documents\DSCDemo\DemoSource` på en källa datorn (till exempel ”pull”-server) finns också (tillsammans med alla underkataloger) på målnoden.</span><span class="sxs-lookup"><span data-stu-id="59960-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="59960-156">Den skriver en bekräftande meddelande till loggen när du är klar och innehåller en instruktion för att se till att åtgärden filkontroll körs innan loggningsåtgärden.</span><span class="sxs-lookup"><span data-stu-id="59960-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

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