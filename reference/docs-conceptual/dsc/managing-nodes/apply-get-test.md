---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Tillämpa, hämta och testa konfigurationer på en nod
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941868"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>Tillämpa, hämta och testa konfigurationer på en nod

I den här guiden får du lära dig hur du arbetar med konfigurationer på en målnod. Den här guiden är uppdelad i följande steg:

## <a name="apply-a-configuration"></a>Använd en konfiguration

Vi måste generera en ". MOF"-fil för att kunna tillämpa och hantera en konfiguration. Följande kod visar en enkel konfiguration som kommer att användas i den här guiden.

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

Om du kompilerar den här konfigurationen skickas två ". MOF"-filer.

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

Använd cmdleten [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) för att tillämpa en konfiguration. Parametern `-Path` anger en katalog där ". MOF"-filer finns. Om ingen `-Computername` anges försöker `Start-DSCConfiguration` tillämpa varje konfiguration till dator namnet som anges med namnet på. MOF-filen (@no__t -2computername\>.mof). Ange `-Verbose` till `Start-DSCConfiguration` om du vill visa mer utförliga utdata.

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

Om `-Wait` inte anges visas ett jobb som skapats. Jobbet som skapas kommer att ha en **ChildJob** för varje ". MOF"-fil som bearbetas av `Start-DSCConfiguration`.

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

Om en konfiguration tar lång tid och du vill stoppa den, kan du använda [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) för att stoppa programmet på den lokala noden.

```powershell
Stop-DSCConfiguration -Force
```

När du är klar kan du Visa jobbets status genom det jobb objekt som returneras av [Get-Job](/powershell/module/microsoft.powershell.core/get-job).

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

Om du vill se **utförliga** utdata använder du följande kommandon för att visa **utförlig** data ström för varje **ChildJob**. Mer information om PowerShell-jobb finns i [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

Från och med PowerShell 5,0 lades parametern `-UseExisting` till `Start-DSCConfiguration`. Genom att ange `-UseExisting` instruerar du cmdleten att använda den befintliga tillämpade konfigurationen i stället för en som anges av parametern `-Path`.

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>Testa en konfiguration

Du kan testa en aktuell konfiguration med hjälp av [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration). `Test-DSCConfiguration` returnerar `True` om noden är kompatibel och `False` om den inte gör det.

```powershell
Test-DSCConfiguration
```

Från och med PowerShell 5,0 lades parametern `-Detailed` till som returnerar ett objekt med samlingar för **ResourcesInDesiredState** och **ResourcesNotInDesiredState**

```powershell
Test-DSCConfiguration -Detailed
```

Från och med PowerShell 5,0 kan du testa en konfiguration utan att använda den. Parametern `-ReferenceConfiguration` accepterar sökvägen till en ". MOF"-fil för att testa noden mot. Inga **uppsättnings** åtgärder vidtas mot noden. I PowerShell 4,0 finns det lösningar för att testa en konfiguration utan att använda den, men de beskrivs inte här.

## <a name="get-configuration-values"></a>Hämta konfigurations värden

Cmdlet [: en get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) returnerar de aktuella värdena för alla konfigurerade resurser i den aktuella konfigurationen.

```powershell
Get-DSCConfiguration
```

Utdata från vår exempel konfiguration skulle se ut så här om de tillämpas korrekt.

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a>Hämta konfigurations status

Med början i PowerShell 5,0 cmdleten [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) kan du se historiken över tillämpade konfigurationer på noden. PowerShell DSC håller koll på de senaste {{N}} konfigurationerna som tillämpas i **push** -eller **pull** -läge. Detta omfattar alla *konsekvens* kontroller som utförs av LCM. Som standard visar `Get-DSCConfigurationStatus` endast den sista historik posten.

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

Använd parametern `-All` om du vill se all konfigurations status historik.

> [!NOTE]
> Utdata trunkeras för det kortfattat.

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a>Hantera konfigurations dokument

LCM hanterar nodens konfiguration genom att arbeta med **konfigurations dokument**. Dessa ". MOF"-filer finns i katalogen "C:\Windows\System32\Configuration".

Från och med PowerShell 5,0 gör [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) att du kan ta bort filerna ". MOF" för att stoppa framtida konsekvens kontroller eller ta bort en konfiguration som har fel när den tillämpas. Med parametern `-Stage` kan du ange vilken ". MOF"-fil som du vill ta bort.

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> I PowerShell 4,0 kan du fortfarande ta bort dessa ". MOF"-filer direkt med [Remove-item](/powershell/module/microsoft.powershell.management/remove-item).

## <a name="publish-configurations"></a>Publicera konfigurationer

Från och med PowerShell 5,0 lades cmdleten [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) till. Med den här cmdleten kan du publicera en ". MOF"-fil på fjärrdatorer utan att använda den.

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>Se även

- [Hämta, testa och ange](../resources/get-test-set.md)