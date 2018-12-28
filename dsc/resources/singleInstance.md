---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Skriva en DSC-resurs med en enskild instans (metodtips)
ms.openlocfilehash: 9494964b1b13eaa082ad5cbc279b4586bb7211cc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405332"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="f3785-103">Skriva en DSC-resurs med en enskild instans (metodtips)</span><span class="sxs-lookup"><span data-stu-id="f3785-103">Writing a single-instance DSC resource (best practice)</span></span>

><span data-ttu-id="f3785-104">**Obs:** Det här avsnittet beskrivs bästa praxis för att definiera en DSC-resurs som tillåter bara en instans i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="f3785-104">**Note:** This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="f3785-105">Det finns för närvarande ingen inbyggd DSC-funktion för att göra detta.</span><span class="sxs-lookup"><span data-stu-id="f3785-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="f3785-106">Som kan ändras i framtiden.</span><span class="sxs-lookup"><span data-stu-id="f3785-106">That might change in the future.</span></span>

<span data-ttu-id="f3785-107">Det finns situationer där du inte vill att en resurs som ska användas flera gånger i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="f3785-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="f3785-108">Till exempel i en föregående implementering av den [xTimeZone](https://github.com/PowerShell/xTimeZone) resurs, en konfiguration kan anropa resursen flera gånger, tidszonen till en annan inställning i varje block för resursen:</span><span class="sxs-lookup"><span data-stu-id="f3785-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

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

<span data-ttu-id="f3785-109">Detta beror på det sätt som DSC resursnycklar fungerar.</span><span class="sxs-lookup"><span data-stu-id="f3785-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="f3785-110">En resurs måste ha minst en nyckelegenskap.</span><span class="sxs-lookup"><span data-stu-id="f3785-110">A resource must have at least one key property.</span></span> <span data-ttu-id="f3785-111">En resursinstans anses vara unika om kombinationen av värdena för alla viktiga egenskaper är unikt.</span><span class="sxs-lookup"><span data-stu-id="f3785-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="f3785-112">I den tidigare implementeringen i [xTimeZone](https://github.com/PowerShell/xTimeZone) resurs hade endast en egenskap--**tidszon**, som måste vara en nyckel.</span><span class="sxs-lookup"><span data-stu-id="f3785-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="f3785-113">Därför skulle en konfiguration, till exempel det ovanstående kompilera och kör utan varning.</span><span class="sxs-lookup"><span data-stu-id="f3785-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="f3785-114">Var och en av de **xTimeZone** resource block anses vara unika.</span><span class="sxs-lookup"><span data-stu-id="f3785-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="f3785-115">Detta innebär att konfigurationen ska tillämpas upprepade gånger på noden och cykling tidszonen fram och tillbaka.</span><span class="sxs-lookup"><span data-stu-id="f3785-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="f3785-116">Att kontrollera att en konfiguration kan tidszonen för en målnoden bara en gång, resursen har uppdaterats för att lägga till en andra egenskap **IsSingleInstance**, som blev nyckelegenskapen.</span><span class="sxs-lookup"><span data-stu-id="f3785-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span>
<span data-ttu-id="f3785-117">Den **IsSingleInstance** har begränsat till ett enda värde, ”Yes” med hjälp av en **ValueMap**.</span><span class="sxs-lookup"><span data-stu-id="f3785-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="f3785-118">Det gamla MOF-schemat för resursen var:</span><span class="sxs-lookup"><span data-stu-id="f3785-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="f3785-119">Det uppdaterade MOF-schemat för resursen är:</span><span class="sxs-lookup"><span data-stu-id="f3785-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="f3785-120">Resurs-skriptet har också uppdaterats om du vill använda den nya parametern.</span><span class="sxs-lookup"><span data-stu-id="f3785-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="f3785-121">Här är gammal resurs-skriptet:</span><span class="sxs-lookup"><span data-stu-id="f3785-121">Here is the old resource script:</span></span>

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
    [CmdletBinding(SupportsShouldProcess=$true)]
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

    if($PSCmdlet.ShouldProcess("'$TimeZone'","Replace the System Time Zone"))
    {
        try
        {
            if($CurrentTimeZone -ne $TimeZone)
            {
                Write-Verbose -Verbose "Setting the TimeZone"
                Set-TimeZone -TimeZone $TimeZone}
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

<span data-ttu-id="f3785-122">Observera att den **tidszon** egenskaper är inte en nyckel.</span><span class="sxs-lookup"><span data-stu-id="f3785-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="f3785-123">Om en konfiguration som försöker ange tidszonen två gånger (med hjälp av två olika **xTimeZone** block med olika **tidszon** värden), försök att kompilera konfigurationen visas ett felmeddelande:</span><span class="sxs-lookup"><span data-stu-id="f3785-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

```powershell
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