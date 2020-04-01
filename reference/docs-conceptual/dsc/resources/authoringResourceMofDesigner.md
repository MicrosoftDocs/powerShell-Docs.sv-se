---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Använda Resource designer-verktyget
ms.openlocfilehash: 36eed0fc888380a03a3279e834748708f578d973
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500635"
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="9bb56-103">Använda Resource designer-verktyget</span><span class="sxs-lookup"><span data-stu-id="9bb56-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="9bb56-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="9bb56-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="9bb56-105">Resource designer-verktyget är en uppsättning cmdlets som exponeras av **xDscResourceDesigner** -modulen som gör det enklare att skapa Windows PowerShell-resurser för Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="9bb56-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="9bb56-106">Cmdletarna i den här resursen hjälper dig att skapa MOF-schemat,-modulen och katalog strukturen för den nya resursen.</span><span class="sxs-lookup"><span data-stu-id="9bb56-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="9bb56-107">Mer information om DSC-resurser finns i avsnittet om hur du [skapar anpassade Windows PowerShell Desired State Configuration-resurser](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="9bb56-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span> <span data-ttu-id="9bb56-108">I det här avsnittet ska vi skapa en DSC-resurs som hanterar Active Directory användare.</span><span class="sxs-lookup"><span data-stu-id="9bb56-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span> <span data-ttu-id="9bb56-109">Använd cmdleten [install-module](/powershell/module/PowershellGet/Install-Module) för att installera **xDscResourceDesigner** -modulen.</span><span class="sxs-lookup"><span data-stu-id="9bb56-109">Use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xDscResourceDesigner** module.</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="9bb56-110">Skapar resurs egenskaper</span><span class="sxs-lookup"><span data-stu-id="9bb56-110">Creating resource properties</span></span>
<span data-ttu-id="9bb56-111">Det första vi behöver göra är att bestämma vilka egenskaper som resursen ska exponera.</span><span class="sxs-lookup"><span data-stu-id="9bb56-111">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="9bb56-112">I det här exemplet ska vi definiera en Active Directory användare med följande egenskaper.</span><span class="sxs-lookup"><span data-stu-id="9bb56-112">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="9bb56-113">Beskrivning av parameter namn</span><span class="sxs-lookup"><span data-stu-id="9bb56-113">Parameter name  Description</span></span>
* <span data-ttu-id="9bb56-114">**Användar namn**: nyckel egenskap som unikt identifierar en användare.</span><span class="sxs-lookup"><span data-stu-id="9bb56-114">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="9bb56-115">**Se till att**: anger om användar kontot ska finnas eller saknas.</span><span class="sxs-lookup"><span data-stu-id="9bb56-115">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="9bb56-116">Den här parametern har bara två möjliga värden.</span><span class="sxs-lookup"><span data-stu-id="9bb56-116">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="9bb56-117">**DomainCredential**: användarens domän lösen ord.</span><span class="sxs-lookup"><span data-stu-id="9bb56-117">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="9bb56-118">**Lösen ord**: det önskade lösen ordet för användaren så att en konfiguration kan ändra användarens lösen ord om det behövs.</span><span class="sxs-lookup"><span data-stu-id="9bb56-118">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="9bb56-119">Vi använder cmdleten **New-xDscResourceProperty** för att skapa egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="9bb56-119">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="9bb56-120">Följande PowerShell-kommandon skapar de egenskaper som beskrivs ovan.</span><span class="sxs-lookup"><span data-stu-id="9bb56-120">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet "Present", "Absent"
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="9bb56-121">Skapa resursen</span><span class="sxs-lookup"><span data-stu-id="9bb56-121">Create the resource</span></span>

<span data-ttu-id="9bb56-122">Nu när resurs egenskaperna har skapats kan vi anropa cmdleten **New-xDscResource** för att skapa resursen.</span><span class="sxs-lookup"><span data-stu-id="9bb56-122">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="9bb56-123">Cmdlet: en **New-xDscResource** använder listan över egenskaper som parametrar.</span><span class="sxs-lookup"><span data-stu-id="9bb56-123">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="9bb56-124">Det tar också vägen där modulen ska skapas, namnet på den nya resursen och namnet på modulen där den finns.</span><span class="sxs-lookup"><span data-stu-id="9bb56-124">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="9bb56-125">Följande PowerShell-kommando skapar resursen.</span><span class="sxs-lookup"><span data-stu-id="9bb56-125">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path 'C:\Program Files\WindowsPowerShell\Modules' –ModuleName Demo_DSCModule
```

<span data-ttu-id="9bb56-126">Cmdlet: en **New-xDscResource** skapar MOF-schemat, ett Skeleton-resurs skript, den katalog struktur som krävs för den nya resursen och ett manifest för modulen som exponerar den nya resursen.</span><span class="sxs-lookup"><span data-stu-id="9bb56-126">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="9bb56-127">MOF-schemafilen finns i **C:\Program files\windowspowershell\modules\ Demo_DSCModule \dscresources\ Demo_ADUser \ Demo_ADUser. schema. MOF**och dess innehåll är som följer.</span><span class="sxs-lookup"><span data-stu-id="9bb56-127">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

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

<span data-ttu-id="9bb56-128">Resurs skriptet finns i **C:\Program files\windowspowershell\modules\ Demo_DSCModule \dscresources\ Demo_ADUser \ Demo_ADUser. psm1**.</span><span class="sxs-lookup"><span data-stu-id="9bb56-128">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span>
<span data-ttu-id="9bb56-129">Den innehåller inte den faktiska logiken för att implementera resursen, som du måste lägga till själv.</span><span class="sxs-lookup"><span data-stu-id="9bb56-129">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="9bb56-130">Innehållet i Skeleton-skriptet är som följer.</span><span class="sxs-lookup"><span data-stu-id="9bb56-130">The contents of the skeleton script are as follows.</span></span>

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

## <a name="updating-the-resource"></a><span data-ttu-id="9bb56-131">Uppdaterar resursen</span><span class="sxs-lookup"><span data-stu-id="9bb56-131">Updating the resource</span></span>

<span data-ttu-id="9bb56-132">Om du behöver lägga till eller ändra parameter listan för resursen kan du anropa cmdleten **Update-xDscResource** .</span><span class="sxs-lookup"><span data-stu-id="9bb56-132">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="9bb56-133">Cmdleten uppdaterar resursen med en ny parameter lista.</span><span class="sxs-lookup"><span data-stu-id="9bb56-133">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="9bb56-134">Om du redan har lagt till logik i resurs skriptet lämnas det kvar.</span><span class="sxs-lookup"><span data-stu-id="9bb56-134">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="9bb56-135">Anta till exempel att du vill inkludera den senaste inloggnings tiden för användaren i vår resurs.</span><span class="sxs-lookup"><span data-stu-id="9bb56-135">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="9bb56-136">I stället för att skriva resursen igen fullständigt kan du anropa **New-xDscResourceProperty** för att skapa den nya egenskapen och sedan anropa **Update-xDscResource** och lägga till din nya egenskap i listan egenskaper.</span><span class="sxs-lookup"><span data-stu-id="9bb56-136">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description "For mapping users to their last log on time"
Update-xDscResource –Name 'Demo_ADUser' –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="9bb56-137">Testa ett resurs schema</span><span class="sxs-lookup"><span data-stu-id="9bb56-137">Testing a resource schema</span></span>

<span data-ttu-id="9bb56-138">Verktyget Resource Designer visar en eller flera cmdlets som kan användas för att testa giltigheten för ett MOF-schema som du har skrivit manuellt.</span><span class="sxs-lookup"><span data-stu-id="9bb56-138">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="9bb56-139">Anropa **test-xDscSchema** -cmdleten och skicka sökvägen till ett MOF-resursnamn som en parameter.</span><span class="sxs-lookup"><span data-stu-id="9bb56-139">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="9bb56-140">Cmdleten kommer att mata ut eventuella fel i schemat.</span><span class="sxs-lookup"><span data-stu-id="9bb56-140">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="9bb56-141">Se även</span><span class="sxs-lookup"><span data-stu-id="9bb56-141">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="9bb56-142">Koncept</span><span class="sxs-lookup"><span data-stu-id="9bb56-142">Concepts</span></span>
[<span data-ttu-id="9bb56-143">Bygg anpassade resurser för Desired Configuration för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bb56-143">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="9bb56-144">Andra resurser</span><span class="sxs-lookup"><span data-stu-id="9bb56-144">Other Resources</span></span>
[<span data-ttu-id="9bb56-145">xDscResourceDesigner-modul</span><span class="sxs-lookup"><span data-stu-id="9bb56-145">xDscResourceDesigner Module</span></span>](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
