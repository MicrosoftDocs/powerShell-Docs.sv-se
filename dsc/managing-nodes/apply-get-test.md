---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Tillämpa, Get, och testa konfigurationer på en nod
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405243"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>Tillämpa, Get, och testa konfigurationer på en nod

Den här guiden visar hur du arbetar med konfigurationer på ett mål noden. Den här guiden har delats upp i följande steg:

## <a name="apply-a-configuration"></a>Tillämpa en konfiguration

Vill använda och hantera en konfiguration, måste vi du generera en ”.mof”-fil. Följande kod representerar en enkel konfiguration som ska användas i den här guiden.

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

Kompilera den här konfigurationen ger två MOF-filerna.

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

Tillämpa en konfiguration genom att använda den [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet. Den `-Path` parametern anger en katalog som där MOF-filerna finns. Om ingen `-Computername` anges `Start-DSCConfiguration` försöker gäller varje konfiguration för datornamnet som anges av namnet på 'MOF-filen (\<computername\>.mof). Ange `-Verbose` till `Start-DSCConfiguration` att se mer utförliga utdata.

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

Om `-Wait` inte anges visas ett jobb som skapats. Ett jobb som skapats ska ha en **ChildJob** för varje ”.mof” fil bearbetas av `Start-DSCConfiguration`.

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

Om en konfiguration tar lång tid och du vill stoppa den kan du använda [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) att stoppa programmet på den lokala noden.

```powershell
Stop-DSCConfiguration -Force
```

När du är klar kan du visa status för jobb via jobbobjektet som returnerades av [Get-Job](/powershell/module/microsoft.powershell.core/get-job).

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

Se den **utförlig** utdata, Använd följande kommandon för att visa den **utförlig** stream för varje **ChildJob**. Mer information om PowerShell-jobb finns i [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).

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

Från och med PowerShell 5.0, den `-UseExisting` parameter har lagts till i `Start-DSCConfiguration`. Genom att ange `-UseExisting`, du instruera cmdlet för att använda den befintliga konfigurationen som används i stället för som anges av den `-Path` parametern.

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>Testa en konfiguration

Du kan testa en som används konfiguration med hjälp av [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration). `Test-DSCConfiguration` Returnerar `True` om noden inte är kompatibelt, och `False` om den inte.

```powershell
Test-DSCConfiguration
```

Från och med PowerShell 5.0, den `-Detailed` parameter har lagts till som returnerar ett objekt med samlingar för **ResourcesInDesiredState** och **ResourcesNotInDesiredState**

```powershell
Test-DSCConfiguration -Detailed
```

Från och med PowerShell 5.0 du kan testa en konfiguration utan att använda den. Den `-ReferenceConfiguration` parametern accepterar sökvägen för filsegment ”.mof” att testa noden mot. Inte **ange** åtgärder utförs i noden. Det finns lösningar för att testa en konfiguration utan att använda det i PowerShell 4.0, men de beskrivs inte här.

## <a name="get-configuration-values"></a>Få konfigurationsvärden

Den [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returnerar de aktuella värdena för alla resurser som är konfigurerade i konfigurationen som används.

```powershell
Get-DSCConfiguration
```

Utdata från vårt exempel konfigurationen skulle se ut så här om du har tillämpats.

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

## <a name="get-configuration-status"></a>Hämta Konfigurationsstatus

Från och med PowerShell 5.0 den [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet: en kan du se historiken för tillämpade konfigurationer till noden. PowerShell DSC håller reda på de senaste {{N}} konfigurationer som används i **Push** eller **hämta** läge. Detta inkluderar alla *konsekvens* kontroller som utförs av LCM. Som standard `Get-DSCConfigurationStatus` visar den senaste historikpost endast.

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

Använd den `-All` parametern för att se all Konfigurationsstatus historik.

> [!NOTE]
> Utdata trunkeras av utrymmesskäl.

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

## <a name="manage-configuration-documents"></a>Hantera Configuration dokument

LCM hanterar konfigurationen av noden genom att arbeta med **Configuration dokument**. De här MOF-filerna finns i katalogen ”C:\Windows\System32\Configuration”.

Från och med PowerShell 5.0 den [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) kan du ta bort de MOF-filerna för att stoppa framtida konsekvenskontroller eller ta bort en konfiguration som innehåller fel vid tillämpning. Den `-Stage` parametern kan du ange vilken ”.mof”-fil som du vill ta bort.

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> I PowerShell 4.0 kan du fortfarande ta bort dessa MOF-filerna direkt med hjälp av [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).

## <a name="publish-configurations"></a>Publicera konfigurationer

Från och med PowerShell 5.0, den [publicera-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet har lagts till. Denna cmdlet kan du publicera en ”.mof”-fil till fjärrdatorer, utan att använda den.

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>Se även

- [Hämta, Test, och ange](../resources/get-test-set.md)
