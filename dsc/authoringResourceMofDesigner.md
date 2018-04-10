---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Med hjälp av verktyget resurs Designer
ms.openlocfilehash: e0282671861755a5f147de4d07783a4680024ec5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="dd6ba-103">Med hjälp av verktyget resurs Designer</span><span class="sxs-lookup"><span data-stu-id="dd6ba-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="dd6ba-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="dd6ba-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="dd6ba-105">Verktyget resurs Designer är en uppsättning cmdlets som exponeras av den **xDscResourceDesigner** modulen som gör det enklare att skapa resurser för Windows PowerShell önskad tillstånd Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="dd6ba-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="dd6ba-106">Cmdletar i den här resursen hjälp för att skapa MOF-schemat, modulen skript och katalogstrukturen för din nya resurs.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="dd6ba-107">Läs mer om DSC resurser [skapa anpassade Windows PowerShell önskad tillstånd Configuration resurser](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="dd6ba-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span>
<span data-ttu-id="dd6ba-108">I det här avsnittet skapar vi en DSC-resurs som hanterar Active Directory-användare.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span>
<span data-ttu-id="dd6ba-109">Använd den [installera modulen](https://technet.microsoft.com/library/dn807162.aspx) för att installera den **xDscResourceDesigner** modul.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-109">Use the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to install the **xDscResourceDesigner** module.</span></span>

><span data-ttu-id="dd6ba-110">**Obs**: **installera modulen** ingår i den **PowerShellGet** module, som ingår i PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-110">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="dd6ba-111">Du kan hämta den **PowerShellGet** -modul för PowerShell 3.0 och 4.0 på [PackageManagement PowerShell-moduler Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="dd6ba-111">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="dd6ba-112">Skapa resursegenskaper</span><span class="sxs-lookup"><span data-stu-id="dd6ba-112">Creating resource properties</span></span>
<span data-ttu-id="dd6ba-113">Det första vi behöver göra är att avgöra om egenskaper som resursen ska visa.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-113">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="dd6ba-114">I det här exemplet ska vi definiera en Active Directory-användare med följande egenskaper.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-114">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="dd6ba-115">Parameternamnet beskrivning</span><span class="sxs-lookup"><span data-stu-id="dd6ba-115">Parameter name  Description</span></span>
* <span data-ttu-id="dd6ba-116">**Användarnamnet**: nyckeln egenskap som unikt identifierar en användare.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-116">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="dd6ba-117">**Se till att**: Anger om användarkontot bör vara närvarande eller saknas.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-117">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="dd6ba-118">Den här parametern har bara två möjliga värden.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-118">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="dd6ba-119">**DomainCredential**: domänlösenordet för användaren.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-119">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="dd6ba-120">**Lösenordet**: önskade lösenord för användaren att tillåta en konfiguration för att ändra användarens lösenord om det behövs.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-120">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="dd6ba-121">Egenskaperna skapar vi använder den **ny xDscResourceProperty** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-121">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="dd6ba-122">Följande PowerShell-kommandon skapar de egenskaper som beskrivs ovan.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-122">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="dd6ba-123">Skapa resursen</span><span class="sxs-lookup"><span data-stu-id="dd6ba-123">Create the resource</span></span>

<span data-ttu-id="dd6ba-124">Nu när du har skapat resursegenskaper vi kallar det **ny xDscResource** för att skapa resursen.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-124">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="dd6ba-125">Den **ny xDscResource** cmdlet tar listan över egenskaper som parametrar.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-125">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="dd6ba-126">Det tar också sökvägen där modulen ska skapas, namnet på den nya resursen och namnet på modulen där den finns.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-126">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="dd6ba-127">Följande PowerShell-kommando skapar resursen.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-127">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

<span data-ttu-id="dd6ba-128">Den **ny xDscResource** cmdleten skapar MOF-schemat, stommen resurs skript, katalogstruktur för din nya resurs och ett manifest för den modul som visar den nya resursen.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-128">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="dd6ba-129">Schemat MOF-filen finns på **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, och innehållet är som följer.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-129">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
  [Key] string UserName;
  [Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
  [Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
  [Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

<span data-ttu-id="dd6ba-130">Resurs-skriptet finns på **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-130">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span> <span data-ttu-id="dd6ba-131">Den innehåller inte den faktiska logiken för att implementera den resurs som du måste lägga till dig själv.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-131">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="dd6ba-132">Innehållet i skriptet stommen är som följer.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-132">The contents of the skeleton script are as follows.</span></span>

```powershell
function Get-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Collections.Hashtable])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $returnValue = @{
  UserName = [System.String]
  Ensure = [System.String]
  DomainAdminCredential = [System.Management.Automation.PSCredential]
  Password = [System.Management.Automation.PSCredential]
  }

  $returnValue
  #>
}


function Set-TargetResource
{
  [CmdletBinding()]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  #Include this line if the resource requires a system reboot.
  #$global:DSCMachineStatus = 1


}


function Test-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Boolean])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $result = [System.Boolean]

  $result
  #>
}


Export-ModuleMember -Function *-TargetResource
```

## <a name="updating-the-resource"></a><span data-ttu-id="dd6ba-133">Uppdaterar resursen</span><span class="sxs-lookup"><span data-stu-id="dd6ba-133">Updating the resource</span></span>

<span data-ttu-id="dd6ba-134">Om du behöver lägga till eller ändra parameterlistan för resursen kan du anropa den **uppdatering xDscResource** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-134">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="dd6ba-135">Cmdlet uppdaterar resursen med en ny parameterlista.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-135">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="dd6ba-136">Om du redan har lagt till logik i skriptet resurs lämnas den intakta.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-136">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="dd6ba-137">Anta att du vill inkludera den senaste loggen för användaren i vår resurs.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-137">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="dd6ba-138">I stället för att skriva resursen igen helt, kan du anropa den **ny xDscResourceProperty** att skapa ny egenskap och sedan anropa **uppdatering xDscResource** och lägga till en ny egenskap i den lista över egenskaper.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-138">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="dd6ba-139">Testa ett schema för resurs</span><span class="sxs-lookup"><span data-stu-id="dd6ba-139">Testing a resource schema</span></span>

<span data-ttu-id="dd6ba-140">Verktyget resurs Designer Exponerar en mer cmdlet som kan användas för att testa en MOF-schema som du har skrivit manuellt.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-140">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="dd6ba-141">Anropa den **Test xDscSchema** cmdlet, ange sökvägen för ett schema för MOF-resurs som en parameter.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-141">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="dd6ba-142">Cmdlet kommer att skrivas ut eventuella fel i schemat.</span><span class="sxs-lookup"><span data-stu-id="dd6ba-142">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="dd6ba-143">Se även</span><span class="sxs-lookup"><span data-stu-id="dd6ba-143">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="dd6ba-144">Begrepp</span><span class="sxs-lookup"><span data-stu-id="dd6ba-144">Concepts</span></span>
[<span data-ttu-id="dd6ba-145">Skapa anpassade Windows PowerShell Desired State Configuration-resurser</span><span class="sxs-lookup"><span data-stu-id="dd6ba-145">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="dd6ba-146">Andra resurser</span><span class="sxs-lookup"><span data-stu-id="dd6ba-146">Other Resources</span></span>
[<span data-ttu-id="dd6ba-147">xDscResourceDesigner modul</span><span class="sxs-lookup"><span data-stu-id="dd6ba-147">xDscResourceDesigner Module</span></span>](https://powershellgallery.com/packages/xDscResourceDesigner)