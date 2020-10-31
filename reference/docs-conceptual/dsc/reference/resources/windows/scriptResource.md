---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-skript resurs
description: DSC-skript resurs
ms.openlocfilehash: f404bf3137caa9f57ad56034895cb15c8944ec07
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142981"
---
# <a name="dsc-script-resource"></a>DSC-skript resurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

`Script`Resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att köra Windows PowerShell-skript block på målnoden. `Script`Resursen använder `GetScript` 
 `SetScript` och `TestScript` egenskaper som innehåller skript block som du definierar för att utföra motsvarande DSC-tillstånds åtgärder.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntax

```Syntax
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> `GetScript``TestScript`och `SetScript` block lagras som strängar.

## <a name="properties"></a>Egenskaper

|  Egenskap  |                                          Beskrivning                                          |
| ---------- | --------------------------------------------------------------------------------------------- |
| GetScript  | Ett skript block som returnerar nodens aktuella tillstånd.                                    |
| SetScript  | Ett skript block som DSC använder för att genomdriva efterlevnad om noden inte har önskat tillstånd. |
| TestScript | Ett skript block som avgör om noden har önskat tillstånd.                           |
| Autentiseringsuppgift | Anger de autentiseringsuppgifter som ska användas för att köra det här skriptet, om autentiseringsuppgifter krävs.        |

## <a name="common-properties"></a>Gemensamma egenskaper

|       Egenskap       |                                            Beskrivning                                            |
| -------------------- | ------------------------------------------------------------------------------------------------- |
| DependsOn            | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. |
| PsDscRunAsCredential | Anger autentiseringsuppgifter för att köra hela resursen som.                                           |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

### <a name="additional-information"></a>Ytterligare information

#### <a name="getscript"></a>GetScript

DSC använder inte utdata från `GetScript` cmdleten [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) `GetScript` för att hämta en nods aktuella status. Ett retur värde krävs inte från `GetScript` om du anger ett retur värde, det måste vara en hash-text som innehåller en **resultat** nyckel vars värde är en sträng.

#### <a name="testscript"></a>TestScript

`TestScript` körs av DSC för att avgöra om `SetScript` ska köras. Om `TestScript` returnerar `$false` , körs DSC `SetScript` för att flytta tillbaka noden till önskat tillstånd. Det måste returnera ett booleskt värde. Resultatet av `$true` indikerar att noden är kompatibel och `SetScript` inte ska köras.

Cmdleten [test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) körs `TestScript` för att hämta nodernas kompatibilitet med `Script` resurserna. I det här fallet körs dock `SetScript` inte, oavsett vilket `TestScript` block som returneras.

> [!NOTE]
> Alla utdata från din `TestScript` är en del av dess retur värde. PowerShell tolkar ignorerade utdata som icke-noll, vilket innebär att dina data `TestScript` returneras `$true` oavsett nodens tillstånd. Detta resulterar i oförutsägbara resultat, falska positiva identifieringar och orsakar problem under fel sökningen.

#### <a name="setscript"></a>SetScript

`SetScript` ändrar noden för att framtvinga det önskade läget. Den anropas av DSC om `TestScript` skript blocket returnerar `$false` . `SetScript`Ska inte ha något retur värde.

## <a name="examples"></a>Exempel

### <a name="example-1-write-sample-text-using-a-script-resource"></a>Exempel 1: Skriv exempel text med hjälp av en skript resurs

I det här exemplet testas om det finns `C:\TempFolder\TestFile.txt` på varje nod. Om den inte finns skapas den med hjälp av `SetScript` . `GetScript`Returnerar filens innehåll och dess retur värde används inte.

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

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

### <a name="example-2-compare-version-information-using-a-script-resource"></a>Exempel 2: jämför versions information med hjälp av en skript resurs

I det här exemplet hämtas den _kompatibla_ versions informationen från en textfil på den redigerings datorn och lagras i `$version` variabeln. När du genererar nodens MOF-fil ersätter DSC `$using:version` variablerna i varje skript block med värdet för `$version` variabeln.
Under körningen lagras den _kompatibla_ versionen i en textfil på varje nod och jämförs och uppdateras vid efterföljande körningar.

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

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

                if( $state.Result -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state.Result,$using:version)
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

### <a name="example-3-utilizing-parameters-in-a-script-resource"></a>Exempel 3: använda parametrar i en skript resurs

I det här exemplet används parametrar från skript resursen genom att använda `using` omfånget.
Observera att **ConfigurationData** kan nås på ett liknande sätt. Till exempel 2 förväntas en version lagras i en lokal fil på målnoden. Både den lokala fil Sök vägen och versionen kan konfigureras för att dock koppla ifrån kod från konfigurations data.

```powershell
Configuration ScriptTest
{
    param
    (
        [Version]
        $Version,

        [string]
        $FilePath
    )

    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content -Path $using:FilePath
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:Version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }

                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                Set-Content -Path $using:FilePath -Value $using:Version
            }
        }
    }
}
```

Den resulterande MOF-filen innehåller variablerna och deras värden som nås via `using` omfånget.
De matas in i varje script block som använder variablerna. Test-och set-skript har tagits bort för det kortfattat:

```Output
instance of MSFT_ScriptResource as $MSFT_ScriptResource1ref
{
 GetScript = "$FilePath ='C:\\Config.ini'\n\n $currentVersion = Get-Content -Path $FilePath\n return @{ 'Result' = \"$currentVersion\" }\n";
 TestScript = ...;
 SetScript = ...;
};
```

### <a name="known-limitations"></a>Kända begränsningar

- Autentiseringsuppgifter som skickas i en skript resurs är inte alltid tillförlitliga när du använder en pull-eller push-server-modell. Vi rekommenderar att du använder en fullständig resurs i stället för att använda en skript resurs i det här fallet.
