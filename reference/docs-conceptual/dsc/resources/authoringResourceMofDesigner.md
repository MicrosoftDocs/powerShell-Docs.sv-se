---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Använda Resource designer-verktyget
ms.openlocfilehash: 4f678f4586c75c830bf876b891fe4784aa3b4e95
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941182"
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="3abe0-103">Använda Resource designer-verktyget</span><span class="sxs-lookup"><span data-stu-id="3abe0-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="3abe0-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="3abe0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="3abe0-105">Resource designer-verktyget är en uppsättning cmdlets som exponeras av **xDscResourceDesigner** -modulen som gör det enklare att skapa Windows PowerShell-resurser för Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="3abe0-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="3abe0-106">Cmdletarna i den här resursen hjälper dig att skapa MOF-schemat,-modulen och katalog strukturen för den nya resursen.</span><span class="sxs-lookup"><span data-stu-id="3abe0-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="3abe0-107">Mer information om DSC-resurser finns i avsnittet om hur du [skapar anpassade Windows PowerShell Desired State Configuration-resurser](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="3abe0-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span>
<span data-ttu-id="3abe0-108">I det här avsnittet ska vi skapa en DSC-resurs som hanterar Active Directory användare.</span><span class="sxs-lookup"><span data-stu-id="3abe0-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span>
<span data-ttu-id="3abe0-109">Använd cmdleten [install-module](/powershell/module/PowershellGet/Install-Module) för att installera **xDscResourceDesigner** -modulen.</span><span class="sxs-lookup"><span data-stu-id="3abe0-109">Use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xDscResourceDesigner** module.</span></span>

><span data-ttu-id="3abe0-110">**Obs!** **install-module** ingår i **PowerShellGet** -modulen, som ingår i PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="3abe0-110">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="3abe0-111">Du kan hämta **PowerShellGet** -modulen för för hands versionen av PowerShell 3,0 och 4,0 i [PackageManagement PowerShell-moduler](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="3abe0-111">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="3abe0-112">Skapar resurs egenskaper</span><span class="sxs-lookup"><span data-stu-id="3abe0-112">Creating resource properties</span></span>
<span data-ttu-id="3abe0-113">Det första vi behöver göra är att bestämma vilka egenskaper som resursen ska exponera.</span><span class="sxs-lookup"><span data-stu-id="3abe0-113">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="3abe0-114">I det här exemplet ska vi definiera en Active Directory användare med följande egenskaper.</span><span class="sxs-lookup"><span data-stu-id="3abe0-114">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="3abe0-115">Beskrivning av parameter namn</span><span class="sxs-lookup"><span data-stu-id="3abe0-115">Parameter name  Description</span></span>
* <span data-ttu-id="3abe0-116">**Användar namn**: nyckel egenskap som unikt identifierar en användare.</span><span class="sxs-lookup"><span data-stu-id="3abe0-116">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="3abe0-117">**Se till att**: anger om användar kontot ska finnas eller saknas.</span><span class="sxs-lookup"><span data-stu-id="3abe0-117">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="3abe0-118">Den här parametern har bara två möjliga värden.</span><span class="sxs-lookup"><span data-stu-id="3abe0-118">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="3abe0-119">**DomainCredential**: användarens domän lösen ord.</span><span class="sxs-lookup"><span data-stu-id="3abe0-119">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="3abe0-120">**Lösen ord**: det önskade lösen ordet för användaren så att en konfiguration kan ändra användarens lösen ord om det behövs.</span><span class="sxs-lookup"><span data-stu-id="3abe0-120">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="3abe0-121">Vi använder cmdleten **New-xDscResourceProperty** för att skapa egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="3abe0-121">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="3abe0-122">Följande PowerShell-kommandon skapar de egenskaper som beskrivs ovan.</span><span class="sxs-lookup"><span data-stu-id="3abe0-122">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet "Present", "Absent"
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="3abe0-123">Skapa resursen</span><span class="sxs-lookup"><span data-stu-id="3abe0-123">Create the resource</span></span>

<span data-ttu-id="3abe0-124">Nu när resurs egenskaperna har skapats kan vi anropa cmdleten **New-xDscResource** för att skapa resursen.</span><span class="sxs-lookup"><span data-stu-id="3abe0-124">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="3abe0-125">Cmdlet: en **New-xDscResource** använder listan över egenskaper som parametrar.</span><span class="sxs-lookup"><span data-stu-id="3abe0-125">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="3abe0-126">Det tar också vägen där modulen ska skapas, namnet på den nya resursen och namnet på modulen där den finns.</span><span class="sxs-lookup"><span data-stu-id="3abe0-126">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="3abe0-127">Följande PowerShell-kommando skapar resursen.</span><span class="sxs-lookup"><span data-stu-id="3abe0-127">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path 'C:\Program Files\WindowsPowerShell\Modules' –ModuleName Demo_DSCModule
```

<span data-ttu-id="3abe0-128">Cmdlet: en **New-xDscResource** skapar MOF-schemat, ett Skeleton-resurs skript, den katalog struktur som krävs för den nya resursen och ett manifest för modulen som exponerar den nya resursen.</span><span class="sxs-lookup"><span data-stu-id="3abe0-128">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="3abe0-129">MOF-schemafilen finns i **C:\Program files\windowspowershell\modules\ Demo_DSCModule \dscresources\ Demo_ADUser \ Demo_ADUser. schema. MOF**och dess innehåll är som följer.</span><span class="sxs-lookup"><span data-stu-id="3abe0-129">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

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

<span data-ttu-id="3abe0-130">Resurs skriptet finns i **C:\Program files\windowspowershell\modules\ Demo_DSCModule \dscresources\ Demo_ADUser \ Demo_ADUser. psm1**.</span><span class="sxs-lookup"><span data-stu-id="3abe0-130">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span> <span data-ttu-id="3abe0-131">Den innehåller inte den faktiska logiken för att implementera resursen, som du måste lägga till själv.</span><span class="sxs-lookup"><span data-stu-id="3abe0-131">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="3abe0-132">Innehållet i Skeleton-skriptet är som följer.</span><span class="sxs-lookup"><span data-stu-id="3abe0-132">The contents of the skeleton script are as follows.</span></span>

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

## <a name="updating-the-resource"></a><span data-ttu-id="3abe0-133">Uppdaterar resursen</span><span class="sxs-lookup"><span data-stu-id="3abe0-133">Updating the resource</span></span>

<span data-ttu-id="3abe0-134">Om du behöver lägga till eller ändra parameter listan för resursen kan du anropa cmdleten **Update-xDscResource** .</span><span class="sxs-lookup"><span data-stu-id="3abe0-134">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="3abe0-135">Cmdleten uppdaterar resursen med en ny parameter lista.</span><span class="sxs-lookup"><span data-stu-id="3abe0-135">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="3abe0-136">Om du redan har lagt till logik i resurs skriptet lämnas det kvar.</span><span class="sxs-lookup"><span data-stu-id="3abe0-136">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="3abe0-137">Anta till exempel att du vill inkludera den senaste inloggnings tiden för användaren i vår resurs.</span><span class="sxs-lookup"><span data-stu-id="3abe0-137">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="3abe0-138">I stället för att skriva resursen igen fullständigt kan du anropa **New-xDscResourceProperty** för att skapa den nya egenskapen och sedan anropa **Update-xDscResource** och lägga till din nya egenskap i listan egenskaper.</span><span class="sxs-lookup"><span data-stu-id="3abe0-138">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description "For mapping users to their last log on time"
Update-xDscResource –Name 'Demo_ADUser' –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="3abe0-139">Testa ett resurs schema</span><span class="sxs-lookup"><span data-stu-id="3abe0-139">Testing a resource schema</span></span>

<span data-ttu-id="3abe0-140">Verktyget Resource Designer visar en eller flera cmdlets som kan användas för att testa giltigheten för ett MOF-schema som du har skrivit manuellt.</span><span class="sxs-lookup"><span data-stu-id="3abe0-140">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="3abe0-141">Anropa **test-xDscSchema** -cmdleten och skicka sökvägen till ett MOF-resursnamn som en parameter.</span><span class="sxs-lookup"><span data-stu-id="3abe0-141">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="3abe0-142">Cmdleten kommer att mata ut eventuella fel i schemat.</span><span class="sxs-lookup"><span data-stu-id="3abe0-142">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="3abe0-143">Se även</span><span class="sxs-lookup"><span data-stu-id="3abe0-143">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="3abe0-144">Begrepp</span><span class="sxs-lookup"><span data-stu-id="3abe0-144">Concepts</span></span>
[<span data-ttu-id="3abe0-145">Bygg anpassade resurser för Desired Configuration för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3abe0-145">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="3abe0-146">Andra resurser</span><span class="sxs-lookup"><span data-stu-id="3abe0-146">Other Resources</span></span>
[<span data-ttu-id="3abe0-147">xDscResourceDesigner-modul</span><span class="sxs-lookup"><span data-stu-id="3abe0-147">xDscResourceDesigner Module</span></span>](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
