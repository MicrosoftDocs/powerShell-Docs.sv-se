---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Med hjälp av verktyget resurs Designer
ms.openlocfilehash: 3dc03adefa71eadc5e80532fdeaaa0e0388e6dce
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="using-the-resource-designer-tool"></a>Med hjälp av verktyget resurs Designer

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Verktyget resurs Designer är en uppsättning cmdlets som exponeras av den **xDscResourceDesigner** modulen som gör det enklare att skapa resurser för Windows PowerShell önskad tillstånd Configuration (DSC). Cmdletar i den här resursen hjälp för att skapa MOF-schemat, modulen skript och katalogstrukturen för din nya resurs. Läs mer om DSC resurser [skapa anpassade Windows PowerShell önskad tillstånd Configuration resurser](authoringResource.md).
I det här avsnittet skapar vi en DSC-resurs som hanterar Active Directory-användare.
Använd den [installera modulen](https://technet.microsoft.com/library/dn807162.aspx) för att installera den **xDscResourceDesigner** modul.

>**Obs**: **installera modulen** ingår i den **PowerShellGet** module, som ingår i PowerShell 5.0. Du kan hämta den **PowerShellGet** -modul för PowerShell 3.0 och 4.0 på [PackageManagement PowerShell-moduler Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).

## <a name="creating-resource-properties"></a>Skapa resursegenskaper
Det första vi behöver göra är att avgöra om egenskaper som resursen ska visa. I det här exemplet ska vi definiera en Active Directory-användare med följande egenskaper.

Parameternamnet beskrivning
* **Användarnamnet**: nyckeln egenskap som unikt identifierar en användare.
* **Se till att**: Anger om användarkontot bör vara närvarande eller saknas. Den här parametern har bara två möjliga värden.
* **DomainCredential**: domänlösenordet för användaren.
* **Lösenordet**: önskade lösenord för användaren att tillåta en konfiguration för att ändra användarens lösenord om det behövs.

Egenskaperna skapar vi använder den **ny xDscResourceProperty** cmdlet. Följande PowerShell-kommandon skapar de egenskaper som beskrivs ovan.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>Skapa resursen

Nu när du har skapat resursegenskaper vi kallar det **ny xDscResource** för att skapa resursen. Den **ny xDscResource** cmdlet tar listan över egenskaper som parametrar. Det tar också sökvägen där modulen ska skapas, namnet på den nya resursen och namnet på modulen där den finns. Följande PowerShell-kommando skapar resursen.

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

Den **ny xDscResource** cmdleten skapar MOF-schemat, stommen resurs skript, katalogstruktur för din nya resurs och ett manifest för den modul som visar den nya resursen.

Schemat MOF-filen finns på **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, och innehållet är som följer.

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

Resurs-skriptet finns på **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Den innehåller inte den faktiska logiken för att implementera den resurs som du måste lägga till dig själv. Innehållet i skriptet stommen är som följer.

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

Om du behöver lägga till eller ändra parameterlistan för resursen kan du anropa den **uppdatering xDscResource** cmdlet. Cmdlet uppdaterar resursen med en ny parameterlista. Om du redan har lagt till logik i skriptet resurs lämnas den intakta.

Anta att du vill inkludera den senaste loggen för användaren i vår resurs. I stället för att skriva resursen igen helt, kan du anropa den **ny xDscResourceProperty** att skapa ny egenskap och sedan anropa **uppdatering xDscResource** och lägga till en ny egenskap i den lista över egenskaper.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>Testa ett schema för resurs

Verktyget resurs Designer Exponerar en mer cmdlet som kan användas för att testa en MOF-schema som du har skrivit manuellt. Anropa den **Test xDscSchema** cmdlet, ange sökvägen för ett schema för MOF-resurs som en parameter. Cmdlet kommer att skrivas ut eventuella fel i schemat.

### <a name="see-also"></a>Se även

#### <a name="concepts"></a>Begrepp
[Skapa anpassade Windows PowerShell Desired State Configuration-resurser](authoringResource.md)

#### <a name="other-resources"></a>Andra resurser
[xDscResourceDesigner modul](https://powershellgallery.com/packages/xDscResourceDesigner)