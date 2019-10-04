---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-filresurs
ms.openlocfilehash: 4c6945d4cdcbc64ac6d52db563823efe8fd0247e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942456"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="82a11-103">DSC-filresurs</span><span class="sxs-lookup"><span data-stu-id="82a11-103">DSC File Resource</span></span>

> <span data-ttu-id="82a11-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="82a11-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="82a11-105">**Fil** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera filer och mappar på målnoden.</span><span class="sxs-lookup"><span data-stu-id="82a11-105">The **File** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="82a11-106">**DestinationPath** och **SourcePath** måste båda vara tillgängliga för målnoden.</span><span class="sxs-lookup"><span data-stu-id="82a11-106">**DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

## <a name="syntax"></a><span data-ttu-id="82a11-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="82a11-107">Syntax</span></span>

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="82a11-108">properties</span><span class="sxs-lookup"><span data-stu-id="82a11-108">Properties</span></span>

|<span data-ttu-id="82a11-109">Egenskap</span><span class="sxs-lookup"><span data-stu-id="82a11-109">Property</span></span> |<span data-ttu-id="82a11-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="82a11-110">Description</span></span> |
|---|---|
|<span data-ttu-id="82a11-111">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="82a11-111">DestinationPath</span></span> |<span data-ttu-id="82a11-112">Platsen, på målnoden, du vill se **till att den** **finns** eller **saknas** .</span><span class="sxs-lookup"><span data-stu-id="82a11-112">The location, on the target node, you want to ensure is **Present** or **Absent** with **Ensure**.</span></span> |
|<span data-ttu-id="82a11-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="82a11-113">Attributes</span></span> |<span data-ttu-id="82a11-114">Det önskade tillstånd för attributen för mål filen eller katalogen.</span><span class="sxs-lookup"><span data-stu-id="82a11-114">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="82a11-115">Giltiga värden är _Arkiv_, _dold_, _ReadOnly_och _system_.</span><span class="sxs-lookup"><span data-stu-id="82a11-115">Valid values are _Archive_, _Hidden_, _ReadOnly_, and _System_.</span></span> |
|<span data-ttu-id="82a11-116">Kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="82a11-116">Checksum</span></span> |<span data-ttu-id="82a11-117">Den typ av kontroll summa som ska användas för att avgöra om två filer är identiska.</span><span class="sxs-lookup"><span data-stu-id="82a11-117">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="82a11-118">Giltiga värden är: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span><span class="sxs-lookup"><span data-stu-id="82a11-118">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> |
|<span data-ttu-id="82a11-119">Innehåll</span><span class="sxs-lookup"><span data-stu-id="82a11-119">Contents</span></span> |<span data-ttu-id="82a11-120">Endast giltigt när det används med en **typ** **fil**.</span><span class="sxs-lookup"><span data-stu-id="82a11-120">Only valid when used with **Type** **File**.</span></span> <span data-ttu-id="82a11-121">Anger innehållet som ska **vara** **tillgängligt** eller **saknas** i mål filen.</span><span class="sxs-lookup"><span data-stu-id="82a11-121">Indicates the contents to **Ensure** are **Present** or **Absent** from the targeted file.</span></span> |
|<span data-ttu-id="82a11-122">Certifiering</span><span class="sxs-lookup"><span data-stu-id="82a11-122">Credential</span></span> |<span data-ttu-id="82a11-123">De autentiseringsuppgifter som krävs för att få åtkomst till resurser, till exempel källfiler.</span><span class="sxs-lookup"><span data-stu-id="82a11-123">The credentials that are required to access resources, such as source files.</span></span> |
|<span data-ttu-id="82a11-124">Force</span><span class="sxs-lookup"><span data-stu-id="82a11-124">Force</span></span> |<span data-ttu-id="82a11-125">Åsidosätter åtkomst åtgärder som resulterar i ett fel (till exempel att skriva över en fil eller ta bort en katalog som inte är tom).</span><span class="sxs-lookup"><span data-stu-id="82a11-125">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span> <span data-ttu-id="82a11-126">Standardvärdet `$false`är.</span><span class="sxs-lookup"><span data-stu-id="82a11-126">Default value is `$false`.</span></span> |
|<span data-ttu-id="82a11-127">Rekursivt</span><span class="sxs-lookup"><span data-stu-id="82a11-127">Recurse</span></span> |<span data-ttu-id="82a11-128">Endast giltigt när det används med **typ** **katalog**.</span><span class="sxs-lookup"><span data-stu-id="82a11-128">Only valid when used with **Type** **Directory**.</span></span> <span data-ttu-id="82a11-129">Utför tillstånds åtgärden rekursivt till alla under kataloger.</span><span class="sxs-lookup"><span data-stu-id="82a11-129">Performs the state operation recursively to all subdirectories.</span></span> <span data-ttu-id="82a11-130">Standardvärdet `$false`är.</span><span class="sxs-lookup"><span data-stu-id="82a11-130">Default value is `$false`.</span></span> |
|<span data-ttu-id="82a11-131">Sök</span><span class="sxs-lookup"><span data-stu-id="82a11-131">SourcePath</span></span> |<span data-ttu-id="82a11-132">Sökvägen som filen eller mappen ska kopieras från.</span><span class="sxs-lookup"><span data-stu-id="82a11-132">The path from which to copy the file or folder resource.</span></span> |
|<span data-ttu-id="82a11-133">type</span><span class="sxs-lookup"><span data-stu-id="82a11-133">Type</span></span> |<span data-ttu-id="82a11-134">Typ av resurs som konfigureras.</span><span class="sxs-lookup"><span data-stu-id="82a11-134">The type of resource being configured.</span></span> <span data-ttu-id="82a11-135">Giltiga värden är **katalog** och **fil**.</span><span class="sxs-lookup"><span data-stu-id="82a11-135">Valid values are **Directory** and **File**.</span></span> <span data-ttu-id="82a11-136">Standardvärdet är **File**.</span><span class="sxs-lookup"><span data-stu-id="82a11-136">Default value is **File**.</span></span> |
|<span data-ttu-id="82a11-137">MatchSource</span><span class="sxs-lookup"><span data-stu-id="82a11-137">MatchSource</span></span> |<span data-ttu-id="82a11-138">Anger om resursen ska övervakas för nya filer som har lagts till i käll katalogen efter den första kopian.</span><span class="sxs-lookup"><span data-stu-id="82a11-138">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="82a11-139">Värdet `$true` anger att efter den ursprungliga kopian ska alla nya källfiler kopieras till målet.</span><span class="sxs-lookup"><span data-stu-id="82a11-139">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="82a11-140">Om värdet `$false`är, cachelagrar resursen innehållet i käll katalogen och ignorerar eventuella filer som lagts till efter den ursprungliga kopian.</span><span class="sxs-lookup"><span data-stu-id="82a11-140">If set to `$false`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span> <span data-ttu-id="82a11-141">Standardvärdet `$false`är.</span><span class="sxs-lookup"><span data-stu-id="82a11-141">Default value is `$false`.</span></span> |

> [!WARNING]
> <span data-ttu-id="82a11-142">Om du inte anger något värde för **Credential** eller **PSRunAsCredential**använder resursen dator kontot för målnoden för att få åtkomst till **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="82a11-142">If you do not specify a value for **Credential** or **PSRunAsCredential**, the resource will use the computer account of the target node to access the **SourcePath**.</span></span> <span data-ttu-id="82a11-143">När **SourcePath** är en UNC-resurs kan detta resultera i ett "åtkomst nekad"-fel.</span><span class="sxs-lookup"><span data-stu-id="82a11-143">When the **SourcePath** is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="82a11-144">Kontrol lera att dina behörigheter har angetts, eller Använd egenskaperna **Credential** eller **PSRunAsCredential** för att ange det konto som ska användas.</span><span class="sxs-lookup"><span data-stu-id="82a11-144">Please ensure your permissions are set accordingly, or use the **Credential** or **PSRunAsCredential** properties to specify the account that should be used.</span></span>

## <a name="common-properties"></a><span data-ttu-id="82a11-145">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="82a11-145">Common properties</span></span>

|<span data-ttu-id="82a11-146">Egenskap</span><span class="sxs-lookup"><span data-stu-id="82a11-146">Property</span></span> |<span data-ttu-id="82a11-147">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="82a11-147">Description</span></span> |
|---|---|
|<span data-ttu-id="82a11-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="82a11-148">DependsOn</span></span> |<span data-ttu-id="82a11-149">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="82a11-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="82a11-150">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="82a11-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="82a11-151">Kontrol</span><span class="sxs-lookup"><span data-stu-id="82a11-151">Ensure</span></span> |<span data-ttu-id="82a11-152">Anger om filen och **innehållet** på **målet** ska finnas eller inte.</span><span class="sxs-lookup"><span data-stu-id="82a11-152">Determines whether the file and **Contents** at the **Destination** should exist or not.</span></span> <span data-ttu-id="82a11-153">Ange att den här egenskapen **finns för att se till att** filen finns.</span><span class="sxs-lookup"><span data-stu-id="82a11-153">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="82a11-154">Ange det som **frånvarande** för att se till att de inte finns.</span><span class="sxs-lookup"><span data-stu-id="82a11-154">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="82a11-155">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="82a11-155">The default value is **Present**.</span></span> |
|<span data-ttu-id="82a11-156">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="82a11-156">PsDscRunAsCredential</span></span> |<span data-ttu-id="82a11-157">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="82a11-157">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="82a11-158">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="82a11-158">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="82a11-159">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="82a11-159">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="82a11-160">Ytterligare information</span><span class="sxs-lookup"><span data-stu-id="82a11-160">Additional information</span></span>

- <span data-ttu-id="82a11-161">Om du bara anger en **DestinationPath**, ser resursen till att sökvägen finns om den **finns eller inte** finns om den **saknas**.</span><span class="sxs-lookup"><span data-stu-id="82a11-161">When you only specify a **DestinationPath**, the resource ensures that the path exists if **Present** or does not exist if **Absent**.</span></span>
- <span data-ttu-id="82a11-162">När du anger en **SourcePath** och en **DestinationPath** med ett **typ** värde för **katalog**, kopieras käll katalogen till mål Sök vägen med resursen.</span><span class="sxs-lookup"><span data-stu-id="82a11-162">When you specify a **SourcePath** and a **DestinationPath** with a **Type** value of **Directory**, the resource copies source directory to the destination path.</span></span> <span data-ttu-id="82a11-163">Egenskaperna **rekursivt**, **Force**och **MatchSource** ändrar vilken typ av kopierings åtgärd som utförs, medan **autentiseringsuppgiften** avgör vilket konto som ska användas för åtkomst till käll katalogen.</span><span class="sxs-lookup"><span data-stu-id="82a11-163">The properties **Recurse**, **Force**, and **MatchSource** change the type of copy operation performed, while **Credential** determines which account to use to access the source directory.</span></span>
- <span data-ttu-id="82a11-164">Om du har angett värdet **ReadOnly** för egenskapen **attribut** tillsammans med en **DestinationPath**, **Se till att** det **finns** en sökväg för att skapa den angivna sökvägen, medan **innehållet** skulle ange innehållet i filen.</span><span class="sxs-lookup"><span data-stu-id="82a11-164">If you specified a value of **ReadOnly** for the **Attributes** property alongside a **DestinationPath**, **Ensure** **Present** would create the path specified, while **Contents** would set the contents of the file.</span></span> <span data-ttu-id="82a11-165">Inställningen för **att se till att** ingen **kommer att ignorera** egenskapen **attributs** fullständigt och ta bort alla filer på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="82a11-165">An **Ensure** **Absent** setting would ignore the **Attributes** property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="82a11-166">Exempel</span><span class="sxs-lookup"><span data-stu-id="82a11-166">Example</span></span>

<span data-ttu-id="82a11-167">I följande exempel kopieras en katalog och dess under kataloger från en pull-server till en målnod med hjälp av fil resursen.</span><span class="sxs-lookup"><span data-stu-id="82a11-167">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="82a11-168">Om åtgärden lyckas skriver logg resursen ett bekräftelse meddelande till händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="82a11-168">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="82a11-169">Käll katalogen är en UNC-sökväg (`\\PullServer\DemoSource`) som delas från hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="82a11-169">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="82a11-170">Egenskapen **rekursivt** säkerställer att alla under kataloger också kopieras.</span><span class="sxs-lookup"><span data-stu-id="82a11-170">The **Recurse** property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="82a11-171">LCM på målnoden körs i kontexten för det lokala system kontot som standard.</span><span class="sxs-lookup"><span data-stu-id="82a11-171">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="82a11-172">Om du vill bevilja åtkomst till **SourcePath**, ger du målnoden dator konto rätt behörigheter.</span><span class="sxs-lookup"><span data-stu-id="82a11-172">To grant access to the **SourcePath**, give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="82a11-173">Både **autentiseringsuppgiften** och **PSDSCRunAsCredential** ändrar den kontext som LCM använder för att få åtkomst till **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="82a11-173">The **Credential** and **PSDSCRunAsCredential** both change the context the LCM uses to access the **SourcePath**.</span></span> <span data-ttu-id="82a11-174">Du måste fortfarande bevilja åtkomst till det konto som ska användas för åtkomst till **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="82a11-174">You still need to grant access to the account that will be used to access the **SourcePath**.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

<span data-ttu-id="82a11-175">Mer information om hur du använder **autentiseringsuppgifter** i DSC finns i [Kör som-användare](../../../configurations/runAsUser.md) eller [autentiseringsuppgifter för konfigurations data](../../../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="82a11-175">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>