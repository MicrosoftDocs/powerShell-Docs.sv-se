---
ms.date: 08/24/2018
keywords: DSC, powershell, konfiguration, installation
title: DSC-skriptresurs
ms.openlocfilehash: ef84239820a44aab2a028f7f0fe17653a851b72e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048741"
---
# <a name="dsc-script-resource"></a>DSC-skriptresurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.x

Den **skriptet** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att köra Windows PowerShell-skriptblock på målnoder. Den **skriptet** resource använder `GetScript`, `SetScript`, och `TestScript` egenskaper som innehåller skriptblock som du definierar för att utföra motsvarande DSC tillstånd åtgärder.

## <a name="syntax"></a>Syntax

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> Den `GetScript`, `TestScript`, och `SetScript` block lagras som strängar.

## <a name="properties"></a>Egenskaper

|Egenskap|Beskrivning|
|--------|-----------|
|GetScript|Ett skriptblock som returnerar det aktuella tillståndet för noden.|
|SetScript|Ett skriptblock som DSC använder för att tvinga kompatibilitet när noden inte är i önskat läge.|
|TestScript|Ett skriptblock som avgör om noden är statusen som önskas.|
|Autentiseringsuppgifter| Anger autentiseringsuppgifterna som används för att köra det här skriptet om autentiseringsuppgifter krävs.|
|DependsOn| Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.

### <a name="getscript"></a>GetScript

DSC inte använder utdata från `GetScript`. Den [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet körs den `GetScript` att hämta aktuell status för en nod. Det krävs inte ett returvärde från `GetScript`. Om du anger ett returvärde, det måste vara en `hashtable` som innehåller en **resultatet** nyckel vars värde är en `String`.

### <a name="testscript"></a>TestScript

Den `TestScript` körs av DSC för att avgöra om den `SetScript` ska köras. Om den `TestScript` returnerar `$false`, DSC körs den `SetScript` att ge önskat tillstånd för noden. Det måste returnera ett `boolean` värde. Ett resultat av `$true` anger att noden är kompatibel och `SetScript` bör utförs inte.

Den [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, körs den `TestScript` att hämta noder kompatibiliteten med den **skriptet** resurser. Men i det här fallet den `SetScript` inte körs, oavsett vad de `TestScript` blockera returnerar.

> [!NOTE]
> Alla utdata från din `TestScript` är en del av dess returvärde. PowerShell tolkar unsuppressed utdata som inte är noll, vilket innebär att din `TestScript` returnerar `$true` oavsett dina nodens tillstånd.
> Detta leder till oväntade resultat, falska positiva identifieringar, och orsakar problem vid felsökning.

### <a name="setscript"></a>SetScript

Den `SetScript` ändrar noden till enfore önskat läge. Den kommer att anropas av DSC om den `TestScript` skript block returnerar `$false`. Den `SetScript` bör har inget returvärde.

## <a name="examples"></a>Exempel

### <a name="example-1-write-sample-text-using-a-script-resource"></a>Exempel 1: Skriva exempeltext med hjälp av en skriptresurs

Det här exemplet testar förekomsten av `C:\TempFolder\TestFile.txt` på varje nod. Om den inte finns skapas den med hjälp av den `SetScript`. Den `GetScript` returnerar innehållet i filen och dess returnerade värdet inte används.

```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a>Exempel 2: Jämför versionsinformation med hjälp av en skriptresurs

Det här exemplet hämtar den *kompatibla* versionsinformation från en textfil på den redigering datorn och lagrar den i den `$version` variabeln. När du genererar nodens MOF-filen, DSC ersätter den `$using:version` variabler i varje skript blockera med värdet för den `$version` variabeln. Under körningen på *kompatibla* version lagras i en textfil på varje nod och jämfört med och uppdateras vid efterföljande körningar.

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }
                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            }
        }
    }
}
```