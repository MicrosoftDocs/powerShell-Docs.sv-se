---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Med hjälp av verktyget Resource Designer
ms.openlocfilehash: 3fd2f06cf46602ee30dd34f8e7bd77d3c92b808f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076675"
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="f3946-103">Med hjälp av verktyget Resource Designer</span><span class="sxs-lookup"><span data-stu-id="f3946-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="f3946-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f3946-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f3946-105">Resurs-Designer-verktyget är en uppsättning cmdletar som exponeras av den **xDscResourceDesigner** modulen som gör det enklare skapa resurser i Windows PowerShell Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="f3946-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="f3946-106">Cmdletar i den här resursen hjälper dig att skapa MOF-schemat och skriptmodul katalogstrukturen för din nya resursen.</span><span class="sxs-lookup"><span data-stu-id="f3946-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="f3946-107">Mer information om DSC-resurser finns i [skapa anpassade Windows PowerShell Desired State Configuration resurser](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="f3946-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span>
<span data-ttu-id="f3946-108">I det här avsnittet skapar vi en DSC-resurs som hanterar Active Directory-användare.</span><span class="sxs-lookup"><span data-stu-id="f3946-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span>
<span data-ttu-id="f3946-109">Använd den [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet för att installera den **xDscResourceDesigner** modulen.</span><span class="sxs-lookup"><span data-stu-id="f3946-109">Use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xDscResourceDesigner** module.</span></span>

><span data-ttu-id="f3946-110">**Obs**: **Install-Module** ingår i den **PowerShellGet** modulen, som ingår i PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="f3946-110">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="f3946-111">Du kan ladda ned den **PowerShellGet** -modulen för PowerShell 3.0 och 4.0 på [PackageManagement PowerShell-moduler förhandsversion](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="f3946-111">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="f3946-112">Skapa resursegenskaper</span><span class="sxs-lookup"><span data-stu-id="f3946-112">Creating resource properties</span></span>
<span data-ttu-id="f3946-113">Det första vi behöver göra är att avgöra om egenskaper som resursen visas.</span><span class="sxs-lookup"><span data-stu-id="f3946-113">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="f3946-114">I det här exemplet definierar vi en Active Directory-användare med följande egenskaper.</span><span class="sxs-lookup"><span data-stu-id="f3946-114">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="f3946-115">Parameternamnet beskrivning</span><span class="sxs-lookup"><span data-stu-id="f3946-115">Parameter name  Description</span></span>
* <span data-ttu-id="f3946-116">**Användarnamn**: Nyckelegenskapen som unikt identifierar en användare.</span><span class="sxs-lookup"><span data-stu-id="f3946-116">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="f3946-117">**Se till att**: Anger om användarkontot ska vara närvarande eller saknade.</span><span class="sxs-lookup"><span data-stu-id="f3946-117">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="f3946-118">Den här parametern har bara två möjliga värden.</span><span class="sxs-lookup"><span data-stu-id="f3946-118">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="f3946-119">**DomainCredential**: Domänlösenordet för användaren.</span><span class="sxs-lookup"><span data-stu-id="f3946-119">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="f3946-120">**lösenord**: Önskad lösenordet för användaren att godkänna en konfiguration för att ändra användarens lösenord om det behövs.</span><span class="sxs-lookup"><span data-stu-id="f3946-120">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="f3946-121">Egenskaperna skapar vi använder den **New xDscResourceProperty** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f3946-121">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="f3946-122">Följande PowerShell-kommandon skapar de egenskaper som beskrivs ovan.</span><span class="sxs-lookup"><span data-stu-id="f3946-122">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="f3946-123">Skapa resursen</span><span class="sxs-lookup"><span data-stu-id="f3946-123">Create the resource</span></span>

<span data-ttu-id="f3946-124">Nu när egenskaper för resursen har skapats, kan du anropa den **New xDscResource** cmdlet för att skapa resursen.</span><span class="sxs-lookup"><span data-stu-id="f3946-124">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="f3946-125">Den **New xDscResource** cmdleten tar i listan över egenskaper som parametrar.</span><span class="sxs-lookup"><span data-stu-id="f3946-125">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="f3946-126">Det tar också sökvägen där modulen ska skapas, namnet på den nya resursen och namnet på modulen där den finns.</span><span class="sxs-lookup"><span data-stu-id="f3946-126">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="f3946-127">Följande PowerShell-kommando skapar resursen.</span><span class="sxs-lookup"><span data-stu-id="f3946-127">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

<span data-ttu-id="f3946-128">Den **New xDscResource** cmdlet skapar MOF-schemat, ett stommen resurs-skript, krävs katalogstrukturen för din nya resursen och ett manifest för den modul som visar den nya resursen.</span><span class="sxs-lookup"><span data-stu-id="f3946-128">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="f3946-129">Schemat MOF-filen finns på **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, och dess innehåll är följande.</span><span class="sxs-lookup"><span data-stu-id="f3946-129">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

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

<span data-ttu-id="f3946-130">Skriptet resurs var **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span><span class="sxs-lookup"><span data-stu-id="f3946-130">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span> <span data-ttu-id="f3946-131">Den omfattar inte den faktiska logiken för att implementera en resurs, som du måste lägga till dig själv.</span><span class="sxs-lookup"><span data-stu-id="f3946-131">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="f3946-132">Innehållet i stommen skript är som följer.</span><span class="sxs-lookup"><span data-stu-id="f3946-132">The contents of the skeleton script are as follows.</span></span>

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

## <a name="updating-the-resource"></a><span data-ttu-id="f3946-133">Uppdaterar resursen</span><span class="sxs-lookup"><span data-stu-id="f3946-133">Updating the resource</span></span>

<span data-ttu-id="f3946-134">Om du vill lägga till eller ändra listan över resursens kan du anropa den **uppdatering xDscResource** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f3946-134">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="f3946-135">Cmdleten uppdaterar resursen med en ny parameterlista.</span><span class="sxs-lookup"><span data-stu-id="f3946-135">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="f3946-136">Om du har redan lagt till logik i skriptet resursen, lämnas den intakta.</span><span class="sxs-lookup"><span data-stu-id="f3946-136">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="f3946-137">Anta exempelvis att du vill inkludera den senaste loggen för användaren i vår resurs.</span><span class="sxs-lookup"><span data-stu-id="f3946-137">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="f3946-138">I stället för att skriva resursen igen helt kan du anropa den **New-xDscResourceProperty** att skapa den nya egenskapen och sedan anropa **uppdatering xDscResource** och Lägg till din nya egenskapen till den egenskapslistan.</span><span class="sxs-lookup"><span data-stu-id="f3946-138">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="f3946-139">Testa ett resurs-schema</span><span class="sxs-lookup"><span data-stu-id="f3946-139">Testing a resource schema</span></span>

<span data-ttu-id="f3946-140">Verktyget Resource Designer visar en mer cmdlet som kan användas för att testa giltigheten hos ett MOF-schema som du har skrivit manuellt.</span><span class="sxs-lookup"><span data-stu-id="f3946-140">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="f3946-141">Anropa den **Test xDscSchema** cmdlet, ange sökvägen för en resurs MOF-schemat som en parameter.</span><span class="sxs-lookup"><span data-stu-id="f3946-141">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="f3946-142">Cmdlet: en kommer utdata eventuella fel i schemat.</span><span class="sxs-lookup"><span data-stu-id="f3946-142">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="f3946-143">Se även</span><span class="sxs-lookup"><span data-stu-id="f3946-143">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="f3946-144">Begrepp</span><span class="sxs-lookup"><span data-stu-id="f3946-144">Concepts</span></span>
[<span data-ttu-id="f3946-145">Skapa anpassade Windows PowerShell Desired State Configuration-resurser</span><span class="sxs-lookup"><span data-stu-id="f3946-145">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="f3946-146">Andra resurser</span><span class="sxs-lookup"><span data-stu-id="f3946-146">Other Resources</span></span>
[<span data-ttu-id="f3946-147">xDscResourceDesigner Module</span><span class="sxs-lookup"><span data-stu-id="f3946-147">xDscResourceDesigner Module</span></span>](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
