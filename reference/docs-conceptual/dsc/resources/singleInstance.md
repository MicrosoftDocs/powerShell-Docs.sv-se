---
ms.date: 07/08/2020
keywords: DSC, PowerShell, konfiguration, installation
title: Skriva en DSC-resurs med en enskild instans (metodtips)
ms.openlocfilehash: cd6048c0f8aeef7fb5458a5f0bfefef25169297c
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217618"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="20bdf-103">Skriva en DSC-resurs med en enskild instans (metodtips)</span><span class="sxs-lookup"><span data-stu-id="20bdf-103">Writing a single-instance DSC resource (best practice)</span></span>

> [!NOTE]
> <span data-ttu-id="20bdf-104">I det här avsnittet beskrivs bästa praxis för att definiera en DSC-resurs som bara tillåter en enda instans i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="20bdf-104">This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="20bdf-105">Det finns för närvarande ingen inbyggd DSC-funktion för detta.</span><span class="sxs-lookup"><span data-stu-id="20bdf-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="20bdf-106">Detta kan ändras i framtiden.</span><span class="sxs-lookup"><span data-stu-id="20bdf-106">That might change in the future.</span></span>

<span data-ttu-id="20bdf-107">Det finns situationer där du inte vill tillåta att en resurs används flera gånger i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="20bdf-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="20bdf-108">I en tidigare implementering av [xTimeZone](https://github.com/PowerShell/xTimeZone) -resursen kan en konfiguration exempelvis anropa resursen flera gånger, vilket ställer in tids zonen till en annan inställning i varje resurs block:</span><span class="sxs-lookup"><span data-stu-id="20bdf-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

```powershell
Configuration SetTimeZone
{
    Param
    (
        [String[]]$NodeName = $env:COMPUTERNAME

    )

    Import-DSCResource -ModuleName xTimeZone


    Node $NodeName
    {
         xTimeZone TimeZoneExample
         {

            TimeZone = 'Eastern Standard Time'
         }

         xTimeZone TimeZoneExample2
         {

            TimeZone = 'Pacific Standard Time'

         }

    }
}
```

<span data-ttu-id="20bdf-109">Detta beror på hur DSC-resursens nycklar fungerar.</span><span class="sxs-lookup"><span data-stu-id="20bdf-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="20bdf-110">En resurs måste ha minst en nyckel egenskap.</span><span class="sxs-lookup"><span data-stu-id="20bdf-110">A resource must have at least one key property.</span></span> <span data-ttu-id="20bdf-111">En resurs instans betraktas som unik om kombinationen av värdena för alla nyckel egenskaper är unik.</span><span class="sxs-lookup"><span data-stu-id="20bdf-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="20bdf-112">I den tidigare implementeringen hade [xTimeZone](https://github.com/PowerShell/xTimeZone) -resursen bara en egenskap--**timezone**, som krävdes för att vara en nyckel.</span><span class="sxs-lookup"><span data-stu-id="20bdf-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="20bdf-113">Därför skulle en konfiguration som ovan kompileras och köras utan varning.</span><span class="sxs-lookup"><span data-stu-id="20bdf-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="20bdf-114">Var och en av **xTimeZone** -resurs blocken betraktas som unika.</span><span class="sxs-lookup"><span data-stu-id="20bdf-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="20bdf-115">Detta skulle göra att konfigurationen upprepas flera gånger på noden, och att den försätts i timezone och tillbaka.</span><span class="sxs-lookup"><span data-stu-id="20bdf-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="20bdf-116">För att säkerställa att en konfiguration bara kan ställa in tids zonen för en målnod en gång, uppdaterades resursen för att lägga till en andra egenskap, **IsSingleInstance**, som blev nyckel egenskapen.</span><span class="sxs-lookup"><span data-stu-id="20bdf-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span> <span data-ttu-id="20bdf-117">**IsSingleInstance** var begränsad till ett enda värde, "Ja" med hjälp av en **ValueMap**.</span><span class="sxs-lookup"><span data-stu-id="20bdf-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="20bdf-118">Det gamla MOF-schemat för resursen var:</span><span class="sxs-lookup"><span data-stu-id="20bdf-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="20bdf-119">Det uppdaterade MOF-schemat för resursen är:</span><span class="sxs-lookup"><span data-stu-id="20bdf-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="20bdf-120">Resurs skriptet har också uppdaterats för att använda den nya parametern.</span><span class="sxs-lookup"><span data-stu-id="20bdf-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="20bdf-121">Här är resurs skriptet ändrat:</span><span class="sxs-lookup"><span data-stu-id="20bdf-121">Here how the resource script was changed:</span></span>

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Get-TimeZone

    $returnValue = @{
        TimeZone = $CurrentTimeZone
        IsSingleInstance = 'Yes'
    }

    #Output the target resource
    $returnValue
}

function Set-TargetResource
{
    [CmdletBinding()]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output the result of Get-TargetResource function.
    $CurrentTimeZone = Get-TimeZone

    Write-Verbose -Message "Replace the System Time Zone to $TimeZone"

    try
    {
        if($CurrentTimeZone -ne $TimeZone)
        {
            Write-Verbose -Verbose "Setting the TimeZone"
            Set-TimeZone -TimeZone $TimeZone
        }
        else
        {
            Write-Verbose -Verbose "TimeZone already set to $TimeZone"
        }
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose -Verbose $ErrorMsg
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $CurrentTimeZone = Get-TimeZone

    if($TimeZone -eq $CurrentTimeZone)
    {
        return $true
    }
    else
    {
        return $false
    }
}

Function Get-TimeZone {
    [CmdletBinding()]
    param()

    & tzutil.exe /g
}

Function Set-TimeZone {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [System.String]
        $TimeZone
    )

    try
    {
        & tzutil.exe /s $TimeZone
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose $ErrorMsg
    }
}

Export-ModuleMember -Function *-TargetResource
```

<span data-ttu-id="20bdf-122">Observera att egenskapen **timezone** inte längre är en nyckel.</span><span class="sxs-lookup"><span data-stu-id="20bdf-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="20bdf-123">Om en konfiguration försöker ställa in tids zonen två gånger (genom att använda två olika **xTimeZone** -block med olika **timezone** -värden), kommer försök att kompilera konfigurationen att orsaka ett fel:</span><span class="sxs-lookup"><span data-stu-id="20bdf-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

```Output
Test-ConflictingResources : A conflict was detected between resources '[xTimeZone]TimeZoneExample (::15::10::xTimeZone)' and
'[xTimeZone]TimeZoneExample2 (::22::10::xTimeZone)' in node 'CONTOSO-CLIENT'. Resources have identical key properties but there are differences in the
following non-key properties: 'TimeZone'. Values 'Eastern Standard Time' don't match values 'Pacific Standard Time'. Please update these property
values so that they are identical in both cases.
At line:271 char:9
+         Test-ConflictingResources $keywordName $canonicalizedValue $k ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : ConflictingDuplicateResource,Test-ConflictingResources
Errors occurred while processing configuration 'SetTimeZone'.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3705 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (SetTimeZone:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```
