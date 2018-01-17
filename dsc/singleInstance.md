---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Skriva en enda instans DSC-resurs (metodtips)
ms.openlocfilehash: 4510bec5b4600334b845831ec6700da01e1a110c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a>Skriva en enda instans DSC-resurs (metodtips)

>**Obs:** det här avsnittet beskrivs bästa praxis för att definiera en DSC-resurs som tillåter bara en instans i en konfiguration. Det finns för närvarande inga inbyggda DSC-funktionen för att göra detta. Som kan ändras i framtiden.

Det finns situationer där du inte vill att en resurs som ska användas flera gånger i en konfiguration. Till exempel i en tidigare implementeringen av den [xTimeZone](https://github.com/PowerShell/xTimeZone) resurs, en konfiguration kan kalla resursen flera gånger tidszonen till en annan inställning i varje block på resursen:

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

Detta beror på det sätt som DSC resurs fungerar. En resurs måste ha minst en nyckelegenskap. En resursinstansen anses vara unika om kombinationen av värden för alla dess nyckelegenskaper är unikt. I den tidigare implementeringen av [xTimeZone](https://github.com/PowerShell/xTimeZone) resursen hade bara en egenskap--**tidszonen**, som krävdes för att vara en nyckel. Därför skulle en konfiguration, till exempel ovannämnda kompilera och köra utan varning. Var och en av de **xTimeZone** resurs block anses vara unika. Detta innebär att konfigurationen ska tillämpas upprepade gånger på noden reglering tidszonen fram och tillbaka.

Att kontrollera att en konfiguration kan tidszonen för en målnod bara en gång, resursen har uppdaterats för att lägga till en andra egenskap **IsSingleInstance**, som blev nyckelegenskapen. Den **IsSingleInstance** har begränsad till ett enda värde ”Ja” med hjälp av en **ValueMap**. Det gamla MOF-schemat för resursen var:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Det uppdaterade MOF-schemat för resursen är:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Skriptet resurs har också uppdaterats om du vill använda den nya parametern. Här är det gamla resurs-skriptet:

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

Observera att den **tidszonen** egenskaper är inte en nyckel. Nu, om en konfiguration som försöker ange tidszonen två gånger (med hjälp av två olika **xTimeZone** block med olika **tidszonen** värden), försöker kompilera konfigurationen visas ett felmeddelande:

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
   
