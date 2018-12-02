---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Checklista för resursskapande
ms.openlocfilehash: 2b6e972776dba4ecc6fd1ab5c21361d653e1a469
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742847"
---
# <a name="resource-authoring-checklist"></a>Checklista för resursskapande

Den här checklistan är en lista över bästa praxis när du redigerar en ny DSC-resurs.

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>Resurs-modulen innehåller .psd1 fil- och schema.mof för alla resurser

Kontrollera att din resurs har en korrekt struktur och innehåller alla nödvändiga filer. Varje resurs-modulen bör innehålla en .psd1-fil och alla icke sammansatta resurser ska ha schema.mof fil. Resurser som inte innehåller schemat visas inte av `Get-DscResource` och användare kommer inte att kunna använda intellisense när du skriver kod mot dessa moduler i ISE.
Katalogstruktur för xRemoteFile resurs, som är en del av den [xPSDesiredStateConfiguration resource modulen](https://github.com/PowerShell/xPSDesiredStateConfiguration), ser ut så här:

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a>Resurs- och schema är korrekta

Verifiera resursschemat (*. schema.mof) fil. Du kan använda den [DSC-resurs Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner) för att utveckla och testa ditt schema.
Se till att:

- Egenskapstyperna är korrekta (t.ex. Använd inte sträng för egenskaper som accepterar numeriska värden, bör du använda UInt32 eller andra numeriska typer i stället)
- Egenskapsattribut har angetts korrekt som: ([nyckel], [krävs], [skriva], [Läs])
- Minst en parameter i schemat har markeras som [nyckel]
- [Läs] egenskapen inte användas samtidigt tillsammans med någon av: [krävs], [key], [skriva]
- Om flera kvalificerare anges förutom [Läs], prioriteras [key]
- Om [skriva] och [krävs] har angetts och sedan [krävs] har prioritet
- ValueMap anges i förekommande fall exempel:

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- Eget namn har angetts och bekräftar att DSC namngivningskonventioner

  Exempel: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`

- Varje fält har beskrivning. PowerShell GitHub-lagringsplatsen har bra exempel som [det. schema.mof för xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)

Dessutom bör du använda **Test-xDscResource** och **Test-xDscSchema** cmdlet: ar från [DSC-resurs Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner) att automatiskt kontrollera resurs och schema:

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

Till exempel:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>Resurs som läses in utan fel

Kontrollera om resurs-modulen kan läsas.
Detta kan ske manuellt, genom att köra `Import-Module <resource_module> -force` och bekräftar att inga fel har inträffat eller skriva av automatiserad testning. Vid det senare kan du följa den här strukturen i ditt fall test:

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a>Resursen är idempotenta positivt om

En av de grundläggande egenskaperna för DSC-resurser är idempotence. Det innebär att tillämpa en DSC-konfiguration som innehåller den här resursen flera gånger kommer alltid att uppnå samma resultat. Om till exempel skapar vi en konfiguration som innehåller följande filresurs:

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

Efter att ha tillämpat den för första gången filen test.txt ska visas i `C:\test` mapp. Efterföljande körningar av samma konfiguration bör dock inte ändra tillståndet för datorn (t.ex. inga kopior av den `test.txt` filen måste ha skapats).
Att säkerställa att en resurs är idempotent upprepade gånger kan du anropa `Set-TargetResource` när testning av resursen direkt eller anropa `Start-DscConfiguration` flera gånger vid testning från slutpunkt till slutpunkt. Resultatet bör vara samma efter varje körning.

## <a name="test-user-modification-scenario"></a>Testa Användarscenario för ändring av

Genom att ändra tillståndet för datorn och sedan köra DSC, kan du kontrollera att `Set-TargetResource` och `Test-TargetResource` fungerar korrekt. Här är vad du ska göra:

1. Börja med resursen inte i önskat läge.
2. Kör konfiguration med din resurs
3. Kontrollera `Test-DscConfiguration` returnerar värdet True
4. Ändra den konfigurerade artikeln om du vill ha slut på önskat tillstånd
5. Kontrollera `Test-DscConfiguration` returnerar false

Här är ett mer konkreta exempel med hjälp av Registerresurser:

1. Börja med registernyckeln inte i önskat läge
2. Kör `Start-DscConfiguration` med en konfiguration för att placera den i önskat läge och kontrollera att den skickar.
3. Kör `Test-DscConfiguration` och kontrollera att den returnerar true
4. Ändra värdet för nyckeln så att det inte är i önskat läge
5. Kör `Test-DscConfiguration` och kontrollera att den returnerar FALSKT
6. `Get-TargetResource` funktionen har verifierats med hjälp av `Get-DscConfiguration`

`Get-TargetResource` ska returnera information om det aktuella tillståndet för resursen. Se till att testa den genom att anropa `Get-DscConfiguration` när du använder konfigurationen och verifierar som korrekt utdata visar det aktuella tillståndet för datorn. Det är viktigt att testa den separat, eftersom eventuella problem i det här området inte visas när du anropar `Start-DscConfiguration`.

## <a name="call-getsettest-targetresource-functions-directly"></a>Anropa **Get/Set/Test-TargetResource** fungerar direkt

Kontrollera att du testar den **Get/Set/Test-TargetResource** funktioner som implementerats i din resurs genom att anropa dem direkt och verifiera att de fungerar som förväntat.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>Kontrollera från slutpunkt till slutpunkt med hjälp av **Start-DscConfiguration**

Testa **Get/Set/Test-TargetResource** funktioner genom att anropa dem direkt är viktigt, men inte alla problem som identifieras det här sättet. Du bör fokusera betydande del av testet om hur du använder `Start-DscConfiguration` eller pull-servern. Detta är hur användare kommer att använda resursen, så att underskatta inte betydelsen av den här typen av testerna.
Möjliga typer av problem:

- Autentiseringsuppgifter/Session fungera annorlunda eftersom DSC-agenten körs som en tjänst.  Glöm inte att testa alla funktionerna här från slutpunkt till slutpunkt.
- Utdata genom att fel `Start-DscConfiguration` kan skilja sig från de som visas när du anropar den `Set-TargetResource` fungera direkt.

## <a name="test-compatability-on-all-dsc-supported-platforms"></a>Testa kompatibilitet på alla DSC-plattformar som stöds

Resursen ska fungera för alla plattformar som DSC som stöds (Windows Server 2008 R2 och senare). Installera den senaste WMF (Windows Management Framework) på ditt operativsystem för att hämta den senaste versionen av DSC. Om din resurs inte fungerar på några av de här plattformarna avsiktligt, ska ett specifikt felmeddelande returneras. Kontrollera också att din resurs kontrollerar om cmdlets som du anropar finns på en viss dator. Windows Server 2012 lagt till ett stort antal nya cmdletar som inte är tillgängliga på Windows Server 2008R2, även med WMF installerats.

## <a name="verify-on-windows-client-if-applicable"></a>Kontrollera på klienten för Windows (om tillämpligt)

Ett mycket vanligt test gap verifierar resursen endast på server-versioner av Windows. Många resurser är också utformad för att arbeta med klient-SKU: er, så om det är true i ditt fall Glöm inte att testa den på dessa plattformar samt.

## <a name="get-dscresource-lists-the-resource"></a>Get-DSCResource visar resursen

När du har distribuerat modulen anropar `Get-DscResource` bör lista din resurs bland annat som ett resultat. Om du inte hittar din resurs i listan, kontrollera att filen schema.mof för den här resursen finns.

## <a name="resource-module-contains-examples"></a>Resurs-modulen innehåller exempel

Skapa goda exempel som hjälper andra att förstå hur du använder den. Det är viktigt, särskilt eftersom många användare hantera exempelkod som dokumentation.

- Först bestämmer du exemplen som ska inkluderas med modulen – minimum, du bör täcker de viktigaste användningsfallen för din resurs:
- Om din modul innehåller flera resurser som behöver samarbeta i ett scenario för slutpunkt till slutpunkt, är grundläggande slutpunkt till slutpunkt-exempel helst första.
- Första exemplen ska vara mycket enkelt sätt – hur du kommer igång med dina resurser i små hanterbara delar (t.ex. Skapa en ny virtuell Hårddisk)
- Efterföljande exempel bör bygger på dessa exempel (t.ex. Skapa en virtuell dator från en virtuell Hårddisk, ta bort virtuell dator, ändra VM) och visa avancerade funktioner (t.ex. Skapa en virtuell dator med dynamiskt minne)
- Exempelkonfigurationer bör parametriseras (alla värden som ska överföras till konfigurationen som parametrar och det bör finnas några hårdkodade värden):

  ```powershell
  configuration Sample_xRemoteFile_DownloadFile
  {
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
  }
  ```

- Det är en bra idé att inkludera (kommenterade ut) exempel på hur du anropar konfigurationen med de faktiska värdena i slutet av exempelskriptet.
  Till exempel i konfigurationen ovan den inte nödvändigtvis uppenbart att det bästa sättet att ange UserAgent:

  `UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` I så fall kan en kommentar tydliggöra avsedda körningen av konfigurationen:

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- Varje exempel skriva i en kort beskrivning som förklarar vad det gör och innebörden av parametrarna.
- Se till exempel räcker för de flesta viktiga scenarier för din resurs och om det inte finns något saknas, kontrollera att de alla köra och placera dator i önskat läge.

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>Felmeddelanden är lätta att förstå och hjälper användarna att lösa problem

Bra felmeddelanden bör vara:

- : Största problemet med felmeddelanden finns de ofta inte finns, så se till att de finns.
- Lätt att förstå: mänskliga läsbar, inte otydligt felkoder
- Exakt: Beskriv vad som är exakt problemet
- Informell: Råd hur du löser problemet
- Fler: Inte klandra användare eller göra dem att känna sig felaktigt

Kontrollera att du har kontrollerat fel i scenarier från slutpunkt till slutpunkt (med hjälp av `Start-DscConfiguration`), eftersom de kan skilja sig från dem som returneras när du kör resursfunktioner direkt.

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>Loggmeddelanden är lätt att förstå och informativa (inklusive – verbose, – felsökning och ETW-loggar)

Kontrollera att loggarna för utdata av resursen är lätt att förstå och ange värdet för användaren. Resurser bör utdata all information som kan vara användbara för användaren, men flera loggar är inte alltid bättre. Du bör undvika redundans och skickar data som inte har ytterligare värde – inte göra någon Gå igenom hundratals loggposter för att kunna hitta vad de letar efter. Naturligtvis kan inga loggar är inte en godtagbar lösning på problemet antingen.

När du testar kan du bör också analysera utförliga loggar och felsökningsloggar (genom att köra `Start-DscConfiguration` med `–Verbose` och `–Debug` växlar på rätt sätt), samt som ETW-loggar. Om du vill se DSC ETW-loggar, gå till Loggboken och öppna följande mapp: program och tjänster från Microsoft - Windows - Desired State Configuration.  Som standard det ska vara användningskanal, men se till att du aktiverar analytiska och felsöka kanaler innan du kör konfigurationen.
Om du vill aktivera analytiska/Debug kanaler, kan du köra skriptet nedan:

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>Resurs-implementering innehåller inte hårdkodad sökvägar

Kontrollera att det finns inga hårdkodad sökvägar i resurs-implementeringen särskilt om de antar även språk (en-us), eller om det uppstår systemvariabler som kan användas.
Om din resurs behöver åtkomst till specifika sökvägar kan använda miljövariabler i stället för hardcoding sökväg, eftersom det kan skilja sig på andra datorer.

Exempel:

Istället för:

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

Du kan skriva:

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a>Resurs-implementering innehåller inte användarinformation

Kontrollera att det finns inga e-post namn, kontoinformation eller namnen på personer i koden.

## <a name="resource-was-tested-with-validinvalid-credentials"></a>Resursen har testats med giltig/ogiltigt autentiseringsuppgifter

Om din resurs tar en autentiseringsuppgift som parameter:

- Kontrollera att resursen fungerar när lokalt System (eller datorkontot för fjärranslutna resurser) inte har åtkomst.
- Kontrollera att resursen fungerar med en autentiseringsuppgift som angetts för hämta, ange och testa
- Om din resurs har åtkomst till resurser, kan du testa alla varianter som du behöver stöd, till exempel:
  - Standard windows-resurser.
  - DFS-resurser.
  - SAMBA resurser (om du vill stödja Linux.)

## <a name="resource-does-not-require-interactive-input"></a>Resursen kräver ingen interaktiva indata

**Get/Set/Test-TargetResource** funktioner ska köras automatiskt och måste inte väntar för användarens indata under alla stadier av körning (t.ex. Du bör inte använda `Get-Credential` i dessa funktioner). Om du vill ange användarens indata bör du ange till konfigurationen som parameter under fasen för kompilering.

## <a name="resource-functionality-was-thoroughly-tested"></a>Resursen funktioner testat noggrant

Den här checklistan innehåller objekt som är viktiga för att testa och/eller ofta missat. Det blir massa tester, främst funktionella som som är specifika för den resurs du vill testa och anges inte här. Glöm inte negativt testfall.

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>Bästa praxis: resurs-modulen innehåller testerna mapp med ResourceDesignerTests.ps1 skript

Det är en bra idé att skapa mappen ”test” i resource-modul, skapa `ResourceDesignerTests.ps1` filen och Lägg till testerna via **Test-xDscResource** och **Test xDscSchema** för alla resurser i de angivna modulen.
På så sätt kan du snabbt Validera scheman för alla resurser från den angivna moduler och gör en förstånd kontrollera innan du publicerar.
För xRemoteFile, `ResourceTests.ps1` bör se ut så enkelt som:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>Bästa praxis: resursmapp innehåller resurs designerskriptet för att generera schemat

Varje resurs ska innehålla ett resurs-designerskriptet som genererar en mof-schemat för resursen. Den här filen ska placeras i `<ResourceName>\ResourceDesignerScripts` och ges namnet generera `<ResourceName>Schema.ps1` för xRemoteFile resurs den här filen skulle anropas `GenerateXRemoteFileSchema.ps1` och innehålla:

```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```

## <a name="best-practice-resource-supports--whatif"></a>Bästa praxis: resursen stöder - WhatIf

Om din resurs fungerar ”farliga” åtgärder, är det en bra idé att implementera `-WhatIf` funktioner. När det är klart kontrollerar du att `-WhatIf` utdata korrekt beskriver åtgärder som skulle hända om kommandot utfördes utan `-WhatIf` växla.
Kontrollera också att åtgärder inte körs (det görs inga ändringar till nodens tillstånd) när `–WhatIf` finns ett skjutreglage.
Anta exempelvis att vi testar File-resursen. Nedan visas enkel konfiguration, vilket skapar filen `test.txt` med innehåll ”test”:

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

Om vi kompilera och kör sedan konfigurationen med den `-WhatIf` växel, utdata tala om för oss exakt vad som skulle hända när vi kör konfigurationen. Konfigurationen själva men har inte utförts (`test.txt` filen skapades inte).

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

Den här listan är inte uttömmande men den täcker många viktiga problem som kan uppstå när du utformar, utvecklar och testar DSC-resurser.
