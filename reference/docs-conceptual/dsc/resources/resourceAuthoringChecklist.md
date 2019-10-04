---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Checklista för resursskapande
ms.openlocfilehash: c0a18169b5e9f6ba0c3848b00725731453763611
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941196"
---
# <a name="resource-authoring-checklist"></a>Checklista för resursskapande

Den här check listan är en lista över bästa metoder när du redigerar en ny DSC-resurs.

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>Resource module innehåller. psd1-filen och schema. MOF för varje resurs

Kontrol lera att resursen har rätt struktur och innehåller alla filer som krävs. Varje modul ska innehålla en. psd1-fil och varje icke-sammansatt resurs ska ha schema. MOF-fil. Resurser som inte innehåller schemat visas inte av `Get-DscResource` och användarna kommer inte att kunna använda IntelliSense-funktionen för att skriva kod mot dessa moduler i ISE.
Katalog strukturen för xRemoteFile-resursen, som är en del av [modulen xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), ser ut så här:

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

## <a name="resource-and-schema-are-correct"></a>Resurs och schema är korrekta

Kontrol lera resurs schema filen (*. schema. MOF). Du kan använda [DSC Resource designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) för att utveckla och testa ditt schema.
Kontrol lera att:

- Egenskaps typerna är korrekta (t. ex. Använd inte sträng för egenskaper som accepterar numeriska värden bör du använda UInt32 eller andra numeriska typer i stället)
- Egenskaps attribut anges korrekt som: ([key], [required], [Write], [Read])
- Minst en parameter i schemat måste markeras som [key]
- [Read]-egenskapen är inte tillsammans med någon av: [required], [key], [Write]
- Om flera kvalificerare anges utom [Läs], har [key] företräde
- Om [Write] och [required] anges prioriteras [required]
- ValueMap anges där lämpligt exempel:

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- Eget namn anges och bekräftar till namn konventioner för DSC

  Exempel: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`

- Varje fält har meningsfull beskrivning. PowerShell-GitHub-lagringsplatsen har användbara exempel, till exempel [. schema. MOF för xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)

Dessutom bör du använda **test-xDscResource** och **test-xDscSchema-cmdlet:** ar från [DSC Resource designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) för att automatiskt verifiera resursen och schemat:

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

Exempel:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>Resurs inläsningar utan fel

Kontrol lera om modulen kan läsas in korrekt.
Detta kan uppnås manuellt, genom att `Import-Module <resource_module> -force` köra och bekräfta att inga fel har inträffat, eller genom att skriva test automatisering. I det senare fallet kan du följa den här strukturen i test fallet:

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw "Module was not imported correctly. Errors returned: $error"
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a>Resursen är idempotenta i det positiva fallet

En av de grundläggande egenskaperna hos DSC-resurser är idempotence. Det innebär att att tillämpa en DSC-konfiguration som innehåller resursen flera gånger kommer alltid att uppnå samma resultat. Om vi till exempel skapar en konfiguration som innehåller följande fil resurs:

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

När du har tillämpat det för första gången ska filen test. txt visas `C:\test` i mappen. Efterföljande körningar av samma konfiguration bör dock inte ändra datorns tillstånd (t. ex. inga kopior av `test.txt` filen skapas).
För att se till att en resurs är idempotenta kan `Set-TargetResource` du upprepade gånger anropa när du testar resursen `Start-DscConfiguration` direkt eller anropa flera gånger när du utför testningen. Resultatet bör vara detsamma efter varje körning.

## <a name="test-user-modification-scenario"></a>Testa användar ändrings scenario

Genom att ändra datorns tillstånd och sedan köra DSC igen, kan du kontrol lera att `Set-TargetResource` och `Test-TargetResource` fungerar korrekt. Här följer några steg som du bör vidta:

1. Starta med resursen inte i önskat tillstånd.
2. Kör konfiguration med din resurs
3. Verifiera `Test-DscConfiguration` returnerar true
4. Ändra det konfigurerade objektet så att det inte är i önskat tillstånd
5. Verifiera `Test-DscConfiguration` returnerar falskt

Här är ett mer konkret exempel med hjälp av register resurser:

1. Starta med register nyckeln har inte önskat tillstånd
2. Kör `Start-DscConfiguration` med en konfiguration för att ställa in den med önskat tillstånd och kontrol lera att den är klar.
3. Kör `Test-DscConfiguration` och kontrol lera att den returnerar true
4. Ändra värdet för nyckeln så att det inte är i önskat tillstånd
5. Kör `Test-DscConfiguration` och kontrol lera att den returnerar false
6. `Get-TargetResource`funktionerna har verifierats med hjälp av`Get-DscConfiguration`

`Get-TargetResource`ska returnera information om resursens aktuella tillstånd. Se till att testa den genom att `Get-DscConfiguration` anropa efter att du har tillämpat konfigurationen och verifiera att utdata stämmer överens med datorns aktuella tillstånd. Det är viktigt att testa det separat, eftersom eventuella problem i det här avsnittet inte visas vid `Start-DscConfiguration`anrop.

## <a name="call-getsettest-targetresource-functions-directly"></a>Anropa **Get/Set/test-TargetResource-** funktioner direkt

Se till att testa funktionerna **Get/Set/test-TargetResource** som implementerats i din resurs genom att anropa dem direkt och kontrol lera att de fungerar som förväntat.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>Verifiera slut punkt till slut punkt med **Start-DscConfiguration**

Testa **Get/Set/test-TargetResource-** funktioner genom att anropa dem direkt, men alla problem kommer inte att upptäckas på det sättet. Du bör fokusera en betydande del av testningen på `Start-DscConfiguration` att använda eller hämtnings servern. Detta är i själva verket hur användarna kommer att använda resursen, så funktionen underskattar inte betydelsen av den här typen av tester.
Möjliga typer av problem:

- Autentiseringsuppgiften/sessionen kan fungera annorlunda eftersom DSC-agenten körs som en tjänst.  Se till att testa alla funktioner som slutar att avslutas.
- Fel utdata i `Start-DscConfiguration` kan skilja sig från de som visas när `Set-TargetResource` funktionen anropas direkt.

## <a name="test-compatability-on-all-dsc-supported-platforms"></a>Testa kompatibilitet på alla plattformar som stöds av DSC

Resursen ska fungera på alla plattformar som stöds av DSC (Windows Server 2008 R2 och senare). Installera den senaste versionen av WMF (Windows Management Framework) på ditt operativ system för att få den senaste versionen av DSC. Om resursen inte fungerar på vissa av dessa plattformar efter design ska ett visst fel meddelande returneras. Kontrol lera också att din resurs kontrollerar om cmdlets som du anropar finns på en viss dator. Windows Server 2012 har lagt till ett stort antal nya cmdletar som inte är tillgängliga på Windows Server-2008R2, även med WMF installerat.

## <a name="verify-on-windows-client-if-applicable"></a>Verifiera på Windows-klienten (om tillämpligt)

Ett mycket vanligt test glapp verifierar bara resursen på Server versioner av Windows. Många resurser är också utformade för att fungera på klient-SKU: er, så om det är sant i ditt fall kan du inte glömma att testa det på dessa plattformar.

## <a name="get-dscresource-lists-the-resource"></a>Get-Dscresource Keyword Supports visar resursen

När du har `Get-DscResource` distribuerat modulen ska du ange en lista över din resurs bland andra som ett resultat. Om du inte hittar din resurs i listan ser du till att schema. MOF-filen för resursen finns.

## <a name="resource-module-contains-examples"></a>Resurs modulen innehåller exempel

Skapa kvalitets exempel som hjälper andra att förstå hur de används. Detta är viktigt, särskilt eftersom många användare behandlar exempel kod som dokumentation.

- Först bör du bestämma de exempel som ska ingå i modulen – du bör minst omfatta de viktigaste användnings fallen för din resurs:
- Om din modul innehåller flera resurser som behöver fungera tillsammans för ett scenario från slut punkt till slut punkt skulle det första exemplet vara bäst.
- De inledande exemplen bör vara väldigt enkla – hur du kommer igång med dina resurser i små hanterbara segment (t. ex. skapa en ny virtuell hård disk)
- Efterföljande exempel bör bygga på dessa exempel (t. ex. skapa en virtuell dator från en virtuell hård disk, ta bort virtuell dator, ändra VM) och Visa avancerade funktioner (t. ex. skapa en virtuell dator med dynamiskt minne)
- Exempel på konfigurationer ska vara parameterstyrda (alla värden ska skickas till konfigurationen som parametrar och det får inte finnas några hårdkodad-värden):

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

- Det är en bra idé att inkludera (kommentera ut) exempel på hur du anropar konfigurationen med de faktiska värdena i slutet av exempel skriptet.
  I konfigurationen ovan är det till exempel inte nödvändigt vis uppenbart att det bästa sättet att ange UserAgent är:

  `UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer`I så fall kan en kommentar klargöra den avsedda körningen av konfigurationen:

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- För varje exempel skriver du en kort beskrivning som förklarar vad det gör och syftet med parametrarna.
- Se till att exemplen tar upp de flesta viktiga scenarier för din resurs, och om inget saknas, kontrollerar du att alla kör och sätter datorn i önskat tillstånd.

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>Fel meddelanden är lätta att förstå och hjälpa användare att lösa problem

Fel meddelanden bör vara:

- Föreligg Det största problemet med fel meddelanden är att de ofta inte finns, så se till att de finns där.
- Lätt att förstå: Läslig, inga dolda felkoder
- Noga Beskriv vad som är exakt med problemet
- Informell Råd om hur du löser problemet
- Avslutningen Klandra inte användaren eller gör så att de känner sig dåligt

Se till att kontrol lera om det finns fel i end to `Start-DscConfiguration`end-scenarier (med), eftersom de kan skilja sig från de som returneras när du kör resurs funktionerna direkt.

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>Logg meddelanden är lätta att förstå och informativt (inklusive – utförliga,-felsöka och ETW-loggar)

Se till att de loggar som returneras av resursen är lätta att förstå och ange värde för användaren. Resurserna bör returnera all information som kan vara till hjälp för användaren, men fler loggar är inte alltid bättre. Du bör undvika redundans och att mata ut data som inte ger ytterligare värde – gör inte någon att gå igenom hundratals logg poster för att hitta det du söker. Det är naturligtvis ingen acceptabel lösning för det här problemet.

När du testar bör du även analysera utförliga och felsöka loggar (genom att `Start-DscConfiguration` köra `–Verbose` med `–Debug` och växlar på lämpligt sätt), samt ETW-loggar. Om du vill se DSC ETW loggar går du till Loggboken och öppnar följande mapp: Program och tjänster-Microsoft-Windows-önskad tillstånds konfiguration.  Som standard kommer det att finnas en drifts kanal, men se till att du aktiverar analys-och fel söknings kanaler innan du kör konfigurationen.
Om du vill aktivera analytiska/felsöka kanaler kan du köra skriptet nedan:

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

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>Resurs implementeringen innehåller inte hårdkodad-sökvägar

Se till att det inte finns några hårdkodad sökvägar i resurs implementeringen, särskilt om de antar språk (en-US) eller om det finns systemvariabler som kan användas.
Om din resurs behöver åtkomst till vissa sökvägar använder du miljövariabler istället för att hårdkoda sökvägen, eftersom den kan vara annorlunda på andra datorer.

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

## <a name="resource-implementation-does-not-contain-user-information"></a>Resurs implementeringen innehåller ingen användar information

Se till att det inte finns några e-postnamn, konto information eller namn på personer i koden.

## <a name="resource-was-tested-with-validinvalid-credentials"></a>Resursen har testats med giltiga/ogiltiga autentiseringsuppgifter

Om din resurs tar emot autentiseringsuppgifter som parameter:

- Kontrol lera att resursen fungerar när det lokala systemet (eller dator kontot för fjär resurser) inte har åtkomst.
- Kontrol lera att resursen fungerar med autentiseringsuppgifter som angetts för Get-, set-och test
- Om resursen har åtkomst till resurser testar du alla varianter som du behöver stödja, till exempel:
  - Standard resurser i Windows.
  - DFS-resurser.
  - SAMBA i resurser (om du vill ha stöd för Linux.)

## <a name="resource-does-not-require-interactive-input"></a>Resursen kräver inte interaktiva ingångar

**Get/Set/test-TargetResource-** funktioner ska köras automatiskt och får inte vänta på användarens indata i körnings fasen (t. ex. bör du `Get-Credential` inte använda i dessa funktioner). Om du behöver ange användarens indata, bör du skicka den till konfigurationen som en parameter under kompilerings fasen.

## <a name="resource-functionality-was-thoroughly-tested"></a>Resurs funktionen har testats grundligt

Den här check listan innehåller objekt som är viktiga för att testas och/eller som ofta saknas. Det kommer att finnas flera tester, främst funktioner som är speciella för den resurs som du testar och som inte nämns här. Glöm inte om negativa test fall.

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>Bästa praxis: Resurs modulen innehåller mappen tester med skriptet ResourceDesignerTests. ps1

Det är en bra idé att skapa mappen "tester" i modulen resurs, skapa `ResourceDesignerTests.ps1` fil och lägga till tester med **test-xDscResource** och **test-xDscSchema** för alla resurser i en specifik modul.
På så sätt kan du snabbt verifiera scheman för alla resurser från de aktuella modulerna och göra en Sanity kontroll innan du publicerar.
För xRemoteFile `ResourceTests.ps1` kan se så enkelt som:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>Bästa praxis: Resursens mapp innehåller ett Resource designer-skript för att skapa schema

Varje resurs ska innehålla ett Resource designer-skript som genererar ett MOF-schema för resursen. Den här filen ska placeras i `<ResourceName>\ResourceDesignerScripts` och vara namngiven som `<ResourceName>Schema.ps1` generate för xRemoteFile-resurs den här `GenerateXRemoteFileSchema.ps1` filen skulle anropas och innehålla:

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

## <a name="best-practice-resource-supports--whatif"></a>Bästa praxis: Resurs stöder-WhatIf

Om din resurs utför "farliga" åtgärder är det en bra idé att implementera `-WhatIf` funktioner. När du är klar kontrollerar du att `-WhatIf` utdata korrekt beskriver åtgärder som skulle inträffa om kommandot kördes utan `-WhatIf` växel.
Kontrol lera också att åtgärderna inte körs (inga ändringar i nodens status görs) när `–WhatIf` växeln är tillgänglig.
Vi antar till exempel att vi testar fil resursen. Nedan visas en enkel konfiguration som skapar `test.txt` en fil med innehållet "test":

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

Om vi kompilerar och sedan kör konfigurationen med `-WhatIf` växeln, säger utdata till oss exakt vad som skulle hända när vi kör konfigurationen. Själva konfigurationen utfördes dock inte (`test.txt` filen skapades inte).

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

Den här listan är inte fullständig, men den täcker många viktiga problem som kan uppstå vid design, utveckling och testning av DSC-resurser.
