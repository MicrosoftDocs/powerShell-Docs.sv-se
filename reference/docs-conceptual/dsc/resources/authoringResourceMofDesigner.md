---
ms.date: 07/08/2020
keywords: DSC, PowerShell, konfiguration, installation
title: Använda Resource designer-verktyget
description: Resource designer-verktyget är en uppsättning cmdlets som exponeras av xDscResourceDesigner-modulen som gör det enklare att skapa PowerShell DSC-resurser.
ms.openlocfilehash: efe36d045ac3fba3823cb1f812bb5761d238fdf1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656482"
---
# <a name="using-the-resource-designer-tool"></a>Använda Resource designer-verktyget

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

Resource designer-verktyget är en uppsättning cmdlets som exponeras av **xDscResourceDesigner** -modulen som gör det enklare att skapa Windows PowerShell-resurser för Desired State Configuration (DSC). Cmdletarna i den här resursen hjälper dig att skapa MOF-schemat,-modulen och katalog strukturen för den nya resursen. Mer information om DSC-resurser finns i avsnittet om hur du [skapar anpassade Windows PowerShell Desired State Configuration-resurser](authoringResource.md). I den här artikeln ska vi skapa en DSC-resurs som hanterar Active Directory användare. Använd cmdleten [install-module](/powershell/module/PowershellGet/Install-Module) för att installera **xDscResourceDesigner** -modulen.

## <a name="creating-resource-properties"></a>Skapar resurs egenskaper

Det första vi behöver göra är att bestämma vilka egenskaper som resursen ska exponera. I det här exemplet ska vi definiera en Active Directory användare med följande egenskaper.

Beskrivning av parameter namn

- **Användar namn** : nyckel egenskap som unikt identifierar en användare.
- **Se till att** : anger om användar kontot ska finnas eller saknas. Den här parametern har bara två möjliga värden.
- **DomainCredential** : användarens domän lösen ord.
- **Lösen ord** : det önskade lösen ordet för användaren så att en konfiguration kan ändra användarens lösen ord om det behövs.

Vi använder cmdleten för att skapa egenskaperna `New-xDscResourceProperty` . Följande PowerShell-kommandon skapar de egenskaper som beskrivs ovan.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet "Present", "Absent"
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>Skapa resursen

Nu när resurs egenskaperna har skapats kan vi anropa `New-xDscResource` cmdleten för att skapa resursen. `New-xDscResource`Cmdlet: en använder listan över egenskaper som parametrar. Det tar också vägen där modulen ska skapas, namnet på den nya resursen och namnet på modulen där den finns. Följande PowerShell-kommando skapar resursen.

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path 'C:\Program Files\WindowsPowerShell\Modules' –ModuleName Demo_DSCModule
```

`New-xDscResource`Cmdleten skapar MOF-schemat, ett Skeleton-resurs skript, den katalog struktur som krävs för den nya resursen och ett manifest för modulen som exponerar den nya resursen.

MOF-schemafilen är i `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof` och dess innehåll är som följer.

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

Resurs skriptet är på `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1` .
Den innehåller inte den faktiska logiken för att implementera resursen, som du måste lägga till själv. Innehållet i Skeleton-skriptet är som följer.

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

Om du behöver lägga till eller ändra parameter listan för resursen kan du anropa- `Update-xDscResource` cmdleten. Cmdleten uppdaterar resursen med en ny parameter lista. Om du redan har lagt till logik i resurs skriptet lämnas det kvar.

Anta till exempel att du vill inkludera den senaste inloggnings tiden för användaren i vår resurs. I stället för att skriva resursen igen fullständigt kan du anropa `New-xDscResourceProperty` för att skapa den nya egenskapen och sedan anropa `Update-xDscResource` och lägga till din nya egenskap i listan egenskaper.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description "For mapping users to their last log on time"
Update-xDscResource –Name 'Demo_ADUser' –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>Testa ett resurs schema

Verktyget Resource Designer visar en eller flera cmdlets som kan användas för att testa giltigheten för ett MOF-schema som du har skrivit manuellt. Anropa `Test-xDscSchema` cmdleten och skicka sökvägen till ett MOF-resursnamn som en parameter. Cmdleten kommer att mata ut eventuella fel i schemat.

### <a name="see-also"></a>Se även

#### <a name="concepts"></a>Begrepp

[Bygg anpassade resurser för Desired Configuration för Windows PowerShell](authoringResource.md)

#### <a name="other-resources"></a>Andra resurser

[xDscResourceDesigner-modul](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
