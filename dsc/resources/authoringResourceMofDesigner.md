---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Använda Resource designer-verktyget
ms.openlocfilehash: 4f678f4586c75c830bf876b891fe4784aa3b4e95
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323763"
---
# <a name="using-the-resource-designer-tool"></a>Använda Resource designer-verktyget

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

Resource designer-verktyget är en uppsättning cmdlets som exponeras av **xDscResourceDesigner** -modulen som gör det enklare att skapa Windows PowerShell-resurser för Desired State Configuration (DSC). Cmdletarna i den här resursen hjälper dig att skapa MOF-schemat,-modulen och katalog strukturen för den nya resursen. Mer information om DSC-resurser finns i avsnittet om hur du [skapar anpassade Windows PowerShell Desired State Configuration-resurser](authoringResource.md).
I det här avsnittet ska vi skapa en DSC-resurs som hanterar Active Directory användare.
Använd cmdleten [install-module](/powershell/module/PowershellGet/Install-Module) för att installera **xDscResourceDesigner** -modulen.

>**Obs**: **Install-module** ingår i **PowerShellGet** -modulen, som ingår i PowerShell 5,0. Du kan hämta **PowerShellGet** -modulen för för hands versionen av PowerShell 3,0 och 4,0 i [PackageManagement PowerShell-moduler](https://www.microsoft.com/en-us/download/details.aspx?id=49186).

## <a name="creating-resource-properties"></a>Skapar resurs egenskaper
Det första vi behöver göra är att bestämma vilka egenskaper som resursen ska exponera. I det här exemplet ska vi definiera en Active Directory användare med följande egenskaper.

Beskrivning av parameter namn
* **Användar namn**: Nyckel egenskap som unikt identifierar en användare.
* **Se till att**: Anger om användar kontot ska finnas eller saknas. Den här parametern har bara två möjliga värden.
* **DomainCredential**: Användarens domän lösen ord.
* **Lösen ord**: Det önskade lösen ordet för användaren att tillåta en konfiguration att ändra användarens lösen ord om det behövs.

Vi använder cmdleten **New-xDscResourceProperty** för att skapa egenskaperna. Följande PowerShell-kommandon skapar de egenskaper som beskrivs ovan.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet "Present", "Absent"
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>Skapa resursen

Nu när resurs egenskaperna har skapats kan vi anropa cmdleten **New-xDscResource** för att skapa resursen. Cmdlet: en **New-xDscResource** använder listan över egenskaper som parametrar. Det tar också vägen där modulen ska skapas, namnet på den nya resursen och namnet på modulen där den finns. Följande PowerShell-kommando skapar resursen.

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path 'C:\Program Files\WindowsPowerShell\Modules' –ModuleName Demo_DSCModule
```

Cmdlet: en **New-xDscResource** skapar MOF-schemat, ett Skeleton-resurs skript, den katalog struktur som krävs för den nya resursen och ett manifest för modulen som exponerar den nya resursen.

MOF-schemafilen finns i **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.MOF**och dess innehåll är som följer.

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

Resurs skriptet är i **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Den innehåller inte den faktiska logiken för att implementera resursen, som du måste lägga till själv. Innehållet i Skeleton-skriptet är som följer.

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

## <a name="updating-the-resource"></a>Uppdaterar resursen

Om du behöver lägga till eller ändra parameter listan för resursen kan du anropa cmdleten **Update-xDscResource** . Cmdleten uppdaterar resursen med en ny parameter lista. Om du redan har lagt till logik i resurs skriptet lämnas det kvar.

Anta till exempel att du vill inkludera den senaste inloggnings tiden för användaren i vår resurs. I stället för att skriva resursen igen fullständigt kan du anropa **New-xDscResourceProperty** för att skapa den nya egenskapen och sedan anropa **Update-xDscResource** och lägga till din nya egenskap i listan egenskaper.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description "For mapping users to their last log on time"
Update-xDscResource –Name 'Demo_ADUser' –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>Testa ett resurs schema

Verktyget Resource Designer visar en eller flera cmdlets som kan användas för att testa giltigheten för ett MOF-schema som du har skrivit manuellt. Anropa **test-xDscSchema** -cmdleten och skicka sökvägen till ett MOF-resursnamn som en parameter. Cmdleten kommer att mata ut eventuella fel i schemat.

### <a name="see-also"></a>Se även

#### <a name="concepts"></a>Begrepp
[Bygg anpassade resurser för Desired Configuration för Windows PowerShell](authoringResource.md)

#### <a name="other-resources"></a>Andra resurser
[xDscResourceDesigner-modul](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
