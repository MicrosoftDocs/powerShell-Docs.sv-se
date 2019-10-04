---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-skript resurs
ms.openlocfilehash: e09e86011fa7dbb2a4d7f28b5032b4328b6f6ec2
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941329"
---
# <a name="dsc-script-resource"></a>DSC-skript resurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**Skript** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att köra Windows PowerShell-skript block på målnoden. **Skript** resursen använder **GetScript**-, **SetScript**-och **TestScript** -egenskaper som innehåller skript block som du definierar för att utföra motsvarande DSC-tillstånds åtgärder.

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
> **GetScript**-, **TestScript**-och **SetScript** -block lagras som strängar.

## <a name="properties"></a>properties

|Egenskap |Beskrivning |
|---|---|
|GetScript |Ett skript block som returnerar nodens aktuella tillstånd. |
|SetScript |Ett skript block som DSC använder för att genomdriva efterlevnad om noden inte har önskat tillstånd. |
|TestScript |Ett skript block som avgör om noden har önskat tillstånd. |
|Certifiering |Anger de autentiseringsuppgifter som ska användas för att köra det här skriptet, om autentiseringsuppgifter krävs. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

### <a name="additional-information"></a>Ytterligare information

#### <a name="getscript"></a>GetScript

DSC använder inte utdata från **GetScript**. Cmdlet: en [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) kör **GetScript** för att hämta en nods aktuella status. Ett retur värde krävs inte från **GetScript**. Om du anger ett retur värde måste det vara en hash som innehåller en **resultat** nyckel vars värde är en sträng.

#### <a name="testscript"></a>TestScript

**TestScript** körs av DSC för att avgöra om **SetScript** ska köras. Om **TestScript** returnerar `$false`kör DSC **SetScript** för att återställa noden till önskat tillstånd. Det måste returnera ett booleskt värde. Resultatet av `$true` indikerar att noden är kompatibel och att **SetScript** inte ska köras.

Cmdleten [test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) kör **TestScript** för att hämta nodernas kompatibilitet med **skript** resurserna.
I det här fallet körs dock inte **SetScript** , oavsett vilket **TestScript** -block som returneras.

> [!NOTE]
> Alla utdata från din **TestScript** är en del av dess retur värde. PowerShell tolkar ignorerade utdata som icke-noll, vilket innebär att din **TestScript** returneras `$true` oavsett nodens tillstånd. Detta resulterar i oförutsägbara resultat, falska positiva identifieringar och orsakar problem under fel sökningen.

#### <a name="setscript"></a>SetScript

**SetScript** ändrar noden för att framtvinga det önskade läget. Den anropas av DSC om **TestScript** -skript blocket `$false`returnerar. **SetScript** får inte ha något retur värde.

## <a name="examples"></a>Exempel

### <a name="example-1-write-sample-text-using-a-script-resource"></a>Exempel 1: Skriv exempel text med hjälp av en skript resurs

`C:\TempFolder\TestFile.txt` I det här exemplet testas om det finns på varje nod. Om den inte finns skapas den med hjälp `SetScript`av. `GetScript` Returnerar filens innehåll och dess retur värde används inte.

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

### <a name="example-2-compare-version-information-using-a-script-resource"></a>Exempel 2: Jämför versions information med hjälp av en skript resurs

I det här exemplet hämtas den *kompatibla* versions informationen från en textfil på den redigerings datorn och lagras i `$version` variabeln. När du genererar nodens MOF-fil ersätter `$using:version` DSC variablerna i varje skript block med värdet `$version` för variabeln.
Under körningen lagras den *kompatibla* versionen i en textfil på varje nod och jämförs och uppdateras vid efterföljande körningar.

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