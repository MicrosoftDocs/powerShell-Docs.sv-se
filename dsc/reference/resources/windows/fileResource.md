---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-filresurs
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688429"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="f7332-103">DSC-filresurs</span><span class="sxs-lookup"><span data-stu-id="f7332-103">DSC File Resource</span></span>

> <span data-ttu-id="f7332-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f7332-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f7332-105">File-resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att hantera filer och mappar på målnoden.</span><span class="sxs-lookup"><span data-stu-id="f7332-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="f7332-106">Den **DestinationPath** och **SourcePath** måste båda vara tillgängliga för målet noden.</span><span class="sxs-lookup"><span data-stu-id="f7332-106">The **DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f7332-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f7332-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="f7332-108">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="f7332-108">Properties</span></span>

|<span data-ttu-id="f7332-109">Egenskap</span><span class="sxs-lookup"><span data-stu-id="f7332-109">Property</span></span>       |<span data-ttu-id="f7332-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f7332-110">Description</span></span>                                                                   |<span data-ttu-id="f7332-111">Obligatorisk</span><span class="sxs-lookup"><span data-stu-id="f7332-111">Required</span></span>|<span data-ttu-id="f7332-112">Standard</span><span class="sxs-lookup"><span data-stu-id="f7332-112">Default</span></span>|
|---------------|------------------------------------------------------------------------------|--------|-------|
|<span data-ttu-id="f7332-113">Målsökväg</span><span class="sxs-lookup"><span data-stu-id="f7332-113">DestinationPath</span></span>|<span data-ttu-id="f7332-114">Plats på målnoden, som du vill se till att är `Present` eller `Absent`.</span><span class="sxs-lookup"><span data-stu-id="f7332-114">The location, on the target node, you want to ensure is `Present` or `Absent`.</span></span>|<span data-ttu-id="f7332-115">Ja</span><span class="sxs-lookup"><span data-stu-id="f7332-115">Yes</span></span>|<span data-ttu-id="f7332-116">Nej</span><span class="sxs-lookup"><span data-stu-id="f7332-116">No</span></span>|
|<span data-ttu-id="f7332-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="f7332-117">Attributes</span></span>     |<span data-ttu-id="f7332-118">Önskat tillstånd attribut för den aktuella filen eller katalogen.</span><span class="sxs-lookup"><span data-stu-id="f7332-118">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="f7332-119">Giltiga värden är **Arkiv**, **Hidden**, **ReadOnly**, och **System**.</span><span class="sxs-lookup"><span data-stu-id="f7332-119">Valid values are **Archive**, **Hidden**, **ReadOnly**, and **System**.</span></span>|<span data-ttu-id="f7332-120">Nej</span><span class="sxs-lookup"><span data-stu-id="f7332-120">No</span></span>|<span data-ttu-id="f7332-121">Inga</span><span class="sxs-lookup"><span data-stu-id="f7332-121">None</span></span>|
|<span data-ttu-id="f7332-122">Kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="f7332-122">Checksum</span></span>      |<span data-ttu-id="f7332-123">Typen kontrollsumma ska användas för att fastställa om två filer är lika.</span><span class="sxs-lookup"><span data-stu-id="f7332-123">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="f7332-124">Giltiga värden är: SHA-1, SHA-256, SHA-512, createdDate, modifieddate kunde.</span><span class="sxs-lookup"><span data-stu-id="f7332-124">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|<span data-ttu-id="f7332-125">Nej</span><span class="sxs-lookup"><span data-stu-id="f7332-125">No</span></span>|<span data-ttu-id="f7332-126">Endast namnet filen eller katalogen jämförs med.</span><span class="sxs-lookup"><span data-stu-id="f7332-126">Only the file or directory name is compared.</span></span>|
|<span data-ttu-id="f7332-127">Innehåll</span><span class="sxs-lookup"><span data-stu-id="f7332-127">Contents</span></span>       |<span data-ttu-id="f7332-128">Endast giltigt när det används med `File` typen.</span><span class="sxs-lookup"><span data-stu-id="f7332-128">Only valid when used with `File` type.</span></span> <span data-ttu-id="f7332-129">Anger att kontrollera att innehållet är `Present` eller `Absent` från den aktuella filen.</span><span class="sxs-lookup"><span data-stu-id="f7332-129">Indicates the contents to Ensure are `Present` or `Absent` from the targeted file.</span></span> |<span data-ttu-id="f7332-130">Nej</span><span class="sxs-lookup"><span data-stu-id="f7332-130">No</span></span>|<span data-ttu-id="f7332-131">Inga</span><span class="sxs-lookup"><span data-stu-id="f7332-131">None</span></span>|
|<span data-ttu-id="f7332-132">Autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="f7332-132">Credential</span></span>     |<span data-ttu-id="f7332-133">De autentiseringsuppgifter som krävs för att komma åt resurser, till exempel källfiler.</span><span class="sxs-lookup"><span data-stu-id="f7332-133">The credentials that are required to access resources, such as source files.</span></span>|<span data-ttu-id="f7332-134">Nej</span><span class="sxs-lookup"><span data-stu-id="f7332-134">No</span></span>|<span data-ttu-id="f7332-135">Datorkontot för målnoden.</span><span class="sxs-lookup"><span data-stu-id="f7332-135">The target node's Computer Account.</span></span> <span data-ttu-id="f7332-136">(*se anmärkning*)</span><span class="sxs-lookup"><span data-stu-id="f7332-136">(*see note*)</span></span>|
|<span data-ttu-id="f7332-137">Se till att</span><span class="sxs-lookup"><span data-stu-id="f7332-137">Ensure</span></span>         |<span data-ttu-id="f7332-138">Önskat tillstånd för målfilen eller katalogen.</span><span class="sxs-lookup"><span data-stu-id="f7332-138">The desired state of the target file or directory.</span></span> |<span data-ttu-id="f7332-139">Nej</span><span class="sxs-lookup"><span data-stu-id="f7332-139">No</span></span>|<span data-ttu-id="f7332-140">**Närvarande**</span><span class="sxs-lookup"><span data-stu-id="f7332-140">**Present**</span></span>|
|<span data-ttu-id="f7332-141">Force</span><span class="sxs-lookup"><span data-stu-id="f7332-141">Force</span></span>          |<span data-ttu-id="f7332-142">Åsidosätter åtgärder för dataåtkomst som skulle resultera i ett fel (till exempel att skriva över en fil eller ta bort en katalog som inte är tom).</span><span class="sxs-lookup"><span data-stu-id="f7332-142">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span>|<span data-ttu-id="f7332-143">Nej</span><span class="sxs-lookup"><span data-stu-id="f7332-143">No</span></span>|`$false`|
|<span data-ttu-id="f7332-144">Recurse</span><span class="sxs-lookup"><span data-stu-id="f7332-144">Recurse</span></span>        |<span data-ttu-id="f7332-145">Endast giltigt när det används med `Directory` typen.</span><span class="sxs-lookup"><span data-stu-id="f7332-145">Only valid when used with `Directory` type.</span></span> <span data-ttu-id="f7332-146">Utför tillstånd åtgärden rekursivt på alla underkataloger.</span><span class="sxs-lookup"><span data-stu-id="f7332-146">Performs the state operation recursively to all subdirectories.</span></span>|<span data-ttu-id="f7332-147">Nej</span><span class="sxs-lookup"><span data-stu-id="f7332-147">No</span></span>|`$false`|
|<span data-ttu-id="f7332-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f7332-148">DependsOn</span></span>      |<span data-ttu-id="f7332-149">Anger ett beroende för angivna resurserna.</span><span class="sxs-lookup"><span data-stu-id="f7332-149">Sets a dependency on specified resource(s).</span></span> <span data-ttu-id="f7332-150">Den här resursen körs bara när åtgärden har körts för alla beroende resurser.</span><span class="sxs-lookup"><span data-stu-id="f7332-150">This resource will only execute after successful execution of any dependent resources.</span></span> <span data-ttu-id="f7332-151">Du kan ange beroende resurser med hjälp av syntaxen `"[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f7332-151">You can specify dependent resources using the syntax `"[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="f7332-152">See [about_DependsOn](../../../configurations/resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="f7332-152">See [about_DependsOn](../../../configurations/resource-depends-on.md)</span></span>|<span data-ttu-id="f7332-153">Nej</span><span class="sxs-lookup"><span data-stu-id="f7332-153">No</span></span>|<span data-ttu-id="f7332-154">Inga</span><span class="sxs-lookup"><span data-stu-id="f7332-154">None</span></span>|
|<span data-ttu-id="f7332-155">SourcePath</span><span class="sxs-lookup"><span data-stu-id="f7332-155">SourcePath</span></span>     |<span data-ttu-id="f7332-156">Sökvägen som du vill kopiera filen eller mappen resursen från.</span><span class="sxs-lookup"><span data-stu-id="f7332-156">The path from which to copy the file or folder resource.</span></span>|<span data-ttu-id="f7332-157">Nej</span><span class="sxs-lookup"><span data-stu-id="f7332-157">No</span></span>|<span data-ttu-id="f7332-158">Inga</span><span class="sxs-lookup"><span data-stu-id="f7332-158">None</span></span>|
|<span data-ttu-id="f7332-159">Typ</span><span class="sxs-lookup"><span data-stu-id="f7332-159">Type</span></span>           |<span data-ttu-id="f7332-160">Typ av resurs som håller på att konfigureras.</span><span class="sxs-lookup"><span data-stu-id="f7332-160">The type of resource being configured.</span></span> <span data-ttu-id="f7332-161">Giltiga värden är `Directory` och `File`.</span><span class="sxs-lookup"><span data-stu-id="f7332-161">Valid values are `Directory` and `File`.</span></span>|<span data-ttu-id="f7332-162">Nej</span><span class="sxs-lookup"><span data-stu-id="f7332-162">No</span></span>|`File`|
|<span data-ttu-id="f7332-163">MatchSource</span><span class="sxs-lookup"><span data-stu-id="f7332-163">MatchSource</span></span>    |<span data-ttu-id="f7332-164">Anger om resursen ska övervaka för nya filer som lagts till i källkatalogen efter den första kopian.</span><span class="sxs-lookup"><span data-stu-id="f7332-164">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="f7332-165">Värdet `$true` anger att inga nya källfiler efter den inledande kopian ska kopieras till målet.</span><span class="sxs-lookup"><span data-stu-id="f7332-165">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="f7332-166">Om inställd `$False`, resursen cachelagrar innehållet i källkatalogen och ignorerar eventuella filer som läggs till efter den första kopian.</span><span class="sxs-lookup"><span data-stu-id="f7332-166">If set to `$False`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span>|<span data-ttu-id="f7332-167">Nej</span><span class="sxs-lookup"><span data-stu-id="f7332-167">No</span></span>|`$false`|

> [!WARNING]
> <span data-ttu-id="f7332-168">Om du inte anger ett värde för `Credential` eller `PSRunAsCredential` (PS V.5) resursen använda datorkontot på målnoden att komma åt den `SourcePath`.</span><span class="sxs-lookup"><span data-stu-id="f7332-168">If you do not specify a value for `Credential` or `PSRunAsCredential` (PS V.5), the resource will use the computer account of the target node to access the `SourcePath`.</span></span>  <span data-ttu-id="f7332-169">När den `SourcePath` är en UNC-resurs, detta kan resultera i ett ”åtkomst nekad”-fel.</span><span class="sxs-lookup"><span data-stu-id="f7332-169">When the `SourcePath` is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="f7332-170">Kontrollera dina behörigheter är inställda i enlighet med detta eller Använd den `Credential` eller `PSRunAsCredential` egenskaper för att ange det konto som ska användas.</span><span class="sxs-lookup"><span data-stu-id="f7332-170">Please ensure your permissions are set accordingly, or use the `Credential` or `PSRunAsCredential` properties to specify the account that should be used.</span></span>

## <a name="present-vs-absent"></a><span data-ttu-id="f7332-171">Presentera vs. Saknas</span><span class="sxs-lookup"><span data-stu-id="f7332-171">Present vs. Absent</span></span>

<span data-ttu-id="f7332-172">Varje DSC-resurs utför olika åtgärder baserat på värdet som du anger för den `Ensure` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f7332-172">Each DSC resource performs different operations based on the value you specify for the `Ensure` property.</span></span> <span data-ttu-id="f7332-173">De värden som du anger för ovanstående egenskaper anger tillstånd-åtgärd utförs.</span><span class="sxs-lookup"><span data-stu-id="f7332-173">The values you specify for the above properties determines the state operation performed.</span></span>

### <a name="existence"></a><span data-ttu-id="f7332-174">Förekomst</span><span class="sxs-lookup"><span data-stu-id="f7332-174">Existence</span></span>

<span data-ttu-id="f7332-175">Om du bara anger en `DestinationPath`, resursen ser till att sökvägen finns (`Present`) eller så finns inte (`Absent`).</span><span class="sxs-lookup"><span data-stu-id="f7332-175">When you only specify a `DestinationPath`, the resource ensures that the path exists (`Present`) or does not exist (`Absent`).</span></span>

### <a name="copy-operations"></a><span data-ttu-id="f7332-176">Kopieringsåtgärder</span><span class="sxs-lookup"><span data-stu-id="f7332-176">Copy Operations</span></span>

<span data-ttu-id="f7332-177">När du anger en `SourcePath` och en `DestinationPath` med en `Type` värdet för **Directory**, resursbiblioteket för kopior som källa till målsökväg.</span><span class="sxs-lookup"><span data-stu-id="f7332-177">When you specify a `SourcePath` and a `DestinationPath` with a `Type` value of **Directory**, the resource copies source directory to the destination path.</span></span> <span data-ttu-id="f7332-178">Egenskaperna `Recurse`, `Force`, och `MatchSource` ändra typen av kopieringsåtgärden utförs, medan `Credential` avgör vilket konto du använder för att komma åt källkatalogen.</span><span class="sxs-lookup"><span data-stu-id="f7332-178">The properties `Recurse`, `Force`, and `MatchSource` change the type of copy operation performed, while `Credential` determines which account to use to access the source directory.</span></span>

### <a name="limitations"></a><span data-ttu-id="f7332-179">Begränsningar</span><span class="sxs-lookup"><span data-stu-id="f7332-179">Limitations</span></span>

<span data-ttu-id="f7332-180">Om du har angett ett värde av `ReadOnly` för den `Attributes` egenskapen tillsammans med en `DestinationPath`, `Ensure = "Present"` skulle skapa den angivna sökvägen, medan `Contents` skulle ange filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="f7332-180">If you specified a value of `ReadOnly` for the `Attributes` property alongside a `DestinationPath`, `Ensure = "Present"` would create the path specified, while `Contents` would set the contents of the file.</span></span>  <span data-ttu-id="f7332-181">En `Absent` tillstånd-åtgärd skulle ignorera den `Attributes` egenskapen helt och hållet, och ta bort alla filer i den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="f7332-181">An `Absent` state operation would ignore the `Attributes` property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="f7332-182">Exempel</span><span class="sxs-lookup"><span data-stu-id="f7332-182">Example</span></span>

<span data-ttu-id="f7332-183">I följande exempel kopierar en katalog och dess underkataloger från en pull-server till en målnod med hjälp av File-resursen.</span><span class="sxs-lookup"><span data-stu-id="f7332-183">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="f7332-184">Om åtgärden lyckas Log-resurs skriver ett bekräftelsemeddelande till händelseloggen.</span><span class="sxs-lookup"><span data-stu-id="f7332-184">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="f7332-185">Källkatalogen är en UNCsökväg (`\\PullServer\DemoSource`) delas från Pull-servern.</span><span class="sxs-lookup"><span data-stu-id="f7332-185">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="f7332-186">Den `Recurse` egenskapen säkerställer att alla underkataloger kopieras även.</span><span class="sxs-lookup"><span data-stu-id="f7332-186">The `Recurse` property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f7332-187">LCM på mål-noden körs i kontexten för kontot Lokalt system som standard.</span><span class="sxs-lookup"><span data-stu-id="f7332-187">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="f7332-188">Att bevilja åtkomst till den **SourcePath**, ge den målnoden datorkonto behörighet.</span><span class="sxs-lookup"><span data-stu-id="f7332-188">To grant access to the **SourcePath**, give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="f7332-189">Den **Credential** och **PSDSCRunAsCredential** (v5) både ändra kontexten LCM-används för att komma åt den **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="f7332-189">The **Credential** and **PSDSCRunAsCredential** (v5) both change the context the LCM uses to access the **SourcePath**.</span></span> <span data-ttu-id="f7332-190">Du behöver att bevilja åtkomst till det konto som ska användas för att komma åt den **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="f7332-190">You still need to grant access to the account that will be used to access the **SourcePath**.</span></span>

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

<span data-ttu-id="f7332-191">För mer på med **autentiseringsuppgifter** i DSC Se [kör som användare](../../../configurations/runAsUser.md) eller [Config autentiseringsuppgifter](../../../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="f7332-191">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>
