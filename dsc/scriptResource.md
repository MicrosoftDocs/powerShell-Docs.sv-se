---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Resursen DSC-skript
ms.openlocfilehash: 1163d454972d8ee519d1c55b77bb85979faf3536
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-script-resource"></a>Resursen DSC-skript


> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Den **skriptet** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att köra Windows PowerShell-skriptblock på målnoder. Den `Script` resursen har `GetScript`, `SetScript`, och `TestScript` egenskaper. De här egenskaperna ska anges till skriptblock som ska köras på varje målnoden.

Den `GetScript` skriptblock ska returnera en hash-tabell som representerar tillståndet för den aktuella noden. Hash-tabellen får bara innehålla en nyckel `Result` och värdet måste vara av typen `String`. Det krävs inte returnerar något. DSC göra inte något med utdata från den här skriptblock.

Den `TestScript` skriptblock bestämmer om den aktuella noden ska ändras. Det ska returnera `$true` om noden är uppdaterad. Det ska returnera `$false` om nodens konfiguration är inaktuell och bör uppdateras av den `SetScript` skriptblock. Den `TestScript` skriptblock anropas av DSC.

Den `SetScript` skriptblock bör ändra noden. Den anropas av DSC om den `TestScript` blockera returnera `$false`.

Om du behöver använda variabler i konfigurationen skriptet i den `GetScript`, `TestScript`, eller `SetScript` skriptblock som använder den `$using:` omfång (se nedan ett exempel).


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

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   |
|---|---|
| GetScript| Ger ett block med Windows PowerShell-skript som körs när du anropar den [Get-DscConfiguration](https://technet.microsoft.com/library/dn407379.aspx) cmdlet. Det här blocket måste returnera en hash-tabell. Hash-tabellen får bara innehålla en nyckel **resultatet** och värdet måste vara av typen **sträng**.|
| SetScript| Innehåller ett block med Windows PowerShell-skript. När du anropar den [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, den **TestScript** block körs första. Om den **TestScript** blockera returnerar **$false**, **SetScript** block körs. Om den **TestScript** blockera returnerar **$true**, **SetScript** block körs inte.|
| TestScript| Innehåller ett block med Windows PowerShell-skript. När du anropar den [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, det här blocket körs. Om den returnerar **$false**, SetScript blocket körs. Om den returnerar **$true**, SetScript som block kommer inte att köra. Den **TestScript** block körs även när du anropar den [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet. Men i det här fallet den **SetScript** block inte körs, oavsett vilket värde som TestScript blockera returnerar. Den **TestScript** block måste returnera True om den faktiska konfigurationen matchar aktuella önskad tillståndskonfiguration och FALSKT om den inte matchar. (Den aktuella tillståndskonfigurationen är den senaste konfigurationen trätt i kraft på den nod som använder DSC.)|
| autentiseringsuppgifter| Anger autentiseringsuppgifter som ska användas för att köra detta skript om autentiseringsuppgifter krävs.|
| dependsOn| Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis **ResourceName** och dess typ är **ResourceType**, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.

## <a name="example-1"></a>Exempel 1
```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript =
        {
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
    }
}
```

## <a name="example-2"></a>Exempel 2
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = {
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Result' = "$currentVersion" }
        }
        TestScript = {
            $state = $GetScript
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
```

Den här resursen skriver konfigurationens version till en textfil. Den här versionen finns på klientdatorn, men inte på någon av noderna, så att den har ska skickas till var och en av de `Script` resursens skriptblock med PowerShells `using` omfång. När genererar nodens MOF-fil, värdet för den `$version` variabeln läses från en textfil på klientdatorn. DSC-ersätter den `$using:version` variabler i varje skript blockera med värdet för den `$version` variabeln.