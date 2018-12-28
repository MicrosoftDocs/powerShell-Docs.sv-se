---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Med hjälp av verktyget Resource Designer
ms.openlocfilehash: 3fd2f06cf46602ee30dd34f8e7bd77d3c92b808f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404942"
---
# <a name="using-the-resource-designer-tool"></a>Med hjälp av verktyget Resource Designer

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Resurs-Designer-verktyget är en uppsättning cmdletar som exponeras av den **xDscResourceDesigner** modulen som gör det enklare skapa resurser i Windows PowerShell Desired State Configuration (DSC). Cmdletar i den här resursen hjälper dig att skapa MOF-schemat och skriptmodul katalogstrukturen för din nya resursen. Mer information om DSC-resurser finns i [skapa anpassade Windows PowerShell Desired State Configuration resurser](authoringResource.md).
I det här avsnittet skapar vi en DSC-resurs som hanterar Active Directory-användare.
Använd den [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet för att installera den **xDscResourceDesigner** modulen.

>**Obs**: **Install-Module** ingår i den **PowerShellGet** modulen, som ingår i PowerShell 5.0. Du kan ladda ned den **PowerShellGet** -modulen för PowerShell 3.0 och 4.0 på [PackageManagement PowerShell-moduler förhandsversion](https://www.microsoft.com/en-us/download/details.aspx?id=49186).

## <a name="creating-resource-properties"></a>Skapa resursegenskaper
Det första vi behöver göra är att avgöra om egenskaper som resursen visas. I det här exemplet definierar vi en Active Directory-användare med följande egenskaper.

Parameternamnet beskrivning
* **Användarnamn**: Nyckelegenskapen som unikt identifierar en användare.
* **Se till att**: Anger om användarkontot ska vara närvarande eller saknade. Den här parametern har bara två möjliga värden.
* **DomainCredential**: Domänlösenordet för användaren.
* **Lösenord**: Önskad lösenordet för användaren att godkänna en konfiguration för att ändra användarens lösenord om det behövs.

Egenskaperna skapar vi använder den **New xDscResourceProperty** cmdlet. Följande PowerShell-kommandon skapar de egenskaper som beskrivs ovan.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>Skapa resursen

Nu när egenskaper för resursen har skapats, kan du anropa den **New xDscResource** cmdlet för att skapa resursen. Den **New xDscResource** cmdleten tar i listan över egenskaper som parametrar. Det tar också sökvägen där modulen ska skapas, namnet på den nya resursen och namnet på modulen där den finns. Följande PowerShell-kommando skapar resursen.

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

Den **New xDscResource** cmdlet skapar MOF-schemat, ett stommen resurs-skript, krävs katalogstrukturen för din nya resursen och ett manifest för den modul som visar den nya resursen.

Schemat MOF-filen finns på **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, och dess innehåll är följande.

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

Skriptet resurs var **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Den omfattar inte den faktiska logiken för att implementera en resurs, som du måste lägga till dig själv. Innehållet i stommen skript är som följer.

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

Om du vill lägga till eller ändra listan över resursens kan du anropa den **uppdatering xDscResource** cmdlet. Cmdleten uppdaterar resursen med en ny parameterlista. Om du har redan lagt till logik i skriptet resursen, lämnas den intakta.

Anta exempelvis att du vill inkludera den senaste loggen för användaren i vår resurs. I stället för att skriva resursen igen helt kan du anropa den **New-xDscResourceProperty** att skapa den nya egenskapen och sedan anropa **uppdatering xDscResource** och Lägg till din nya egenskapen till den egenskapslistan.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>Testa ett resurs-schema

Verktyget Resource Designer visar en mer cmdlet som kan användas för att testa giltigheten hos ett MOF-schema som du har skrivit manuellt. Anropa den **Test xDscSchema** cmdlet, ange sökvägen för en resurs MOF-schemat som en parameter. Cmdlet: en kommer utdata eventuella fel i schemat.

### <a name="see-also"></a>Se även

#### <a name="concepts"></a>Begrepp
[Skapa anpassade Windows PowerShell Desired State Configuration-resurser](authoringResource.md)

#### <a name="other-resources"></a>Andra resurser
[xDscResourceDesigner modul](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
