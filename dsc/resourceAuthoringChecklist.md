---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Checklista för redigering av resursen"
ms.openlocfilehash: 8f6ea79ec4936b13f54d2b2a5c6974a180735344
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="resource-authoring-checklist"></a>Checklista för redigering av resursen
Den här checklistan är en lista över rekommenderade metoder när du skapar en ny DSC-resurs.
## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>Resursmodul innehåller .psd1 fil- och schema.mof för alla resurser 
Kontrollera att resursen har rätt struktur och innehåller alla nödvändiga filer. Resursmodul för varje ska innehålla en .psd1-fil och alla icke sammansatta resurser ska ha schema.mof fil. Resurser som inte innehåller schemat visas inte av **Get-DscResource** och användare kommer inte att kunna använda intellisense när skriva kod mot dessa moduler i ISE. Katalogstruktur för xRemoteFile resurs, som är en del av den [xPSDesiredStateConfiguration Resursmodul](https://github.com/PowerShell/xPSDesiredStateConfiguration), ser ut som följer:


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

## <a name="resource-and-schema-are-correct"></a>Resurs- och schema är korrekta ##
Verifiera resursschemat (*. schema.mof) fil. Du kan använda den [DSC resurs Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) för att utveckla och testa ditt schema. Kontrollera att:
- Egenskapstyperna är rätt (t.ex. Använd inte sträng för egenskaper som accepterar numeriska värden, bör du använda UInt32 eller andra numeriska typer i stället)
- Egenskapsattribut är angivna korrekt som: ([nyckel], [krävs], [skriva] [läsa])
- Minst en parameter i schemat har markerats som [nyckel]
- [läsa] egenskapen inte användas samtidigt tillsammans med någon av: [krävs], [key], [skriva]
- Om flera kvalificerare anges förutom [Läs], prioriteras [key]
- Om [skriva] och [krävs] har angetts och sedan [krävs] har prioritet
- ValueMap anges i förekommande fall

Exempel:
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

- Eget namn har angetts och bekräftar att DSC namngivningskonventioner

Exempel: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```

- Varje fält har beskrivning. PowerShell GitHub-lagringsplatsen har bra exempel som [det. schema.mof för xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)

Dessutom bör du använda **Test xDscResource** och **Test xDscSchema** cmdlets från [DSC resurs Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) att automatiskt kontrollera resurs- och schema:
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
Till exempel:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>Resursen har lästs in utan fel ##
Kontrollera om modulen resurs kan läsas.
Detta kan ske manuellt, genom att köra `Import-Module <resource_module> -force ` och bekräftar att inga fel uppstått eller skrivning av test automation. Du kan följa den här strukturen i din testfall vid denna:
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
## <a name="resource-is-idempotent-in-the-positive-case"></a>Resursen är idempotent positivt om 
En av de grundläggande egenskaperna för DSC-resurser är vara idempotence. Det innebär att tillämpa en DSC-konfiguration som innehåller den här resursen flera gånger kommer alltid att uppnå samma resultat. Om till exempel skapar vi en konfiguration som innehåller följande filresurs:
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
} 
```
Efter att den första gången, ska filen test.txt visas i mappen C:\test. Efterföljande körningar av samma konfiguration bör inte ändra tillståndet för den datorn (t.ex. inga kopior av filen test.txt ska skapas).
En resurs är idempotent upprepade gånger kan du anropa **Set TargetResource** vid testning av resursen direkt eller anropa **Start DscConfiguration** flera gånger vid testning av slutpunkt till slutpunkt. Resultatet bör vara samma efter varje kör. 


## <a name="test-user-modification-scenario"></a>Testa Användarscenario ändring ##
Genom att ändra tillståndet för datorn och sedan köra DSC, kan du kontrollera att **Set TargetResource** och **Test TargetResource** fungerar korrekt. Här är vad du bör göra:
1.  Börja med resursen inte finns i tillståndet.
2.  Kör konfiguration med din resurs
3.  Kontrollera **Test DscConfiguration** returnerar True
4.  Ändra den konfigurerade artikeln för att vara utanför tillståndet
5.  Kontrollera **Test DscConfiguration** returnerar false här är en mer konkreta exempel med hjälp av registret resursen:
1.  Börja med registernyckeln inte i tillståndet
2.  Kör **Start DscConfiguration** till en konfiguration för att placera den i tillståndet och kontrollera att den skickar.
3.  Kör **Test DscConfiguration** och kontrollera att den returnerar SANT
4.  Ändra värdet för nyckeln så att den inte är i tillståndet önskade
5.  Kör **Test DscConfiguration** och kontrollera att den returnerar värdet false
6.  Get-TargetResource funktioner har verifierats med hjälp av Get-DscConfiguration

Get-TargetResource ska returnera information om det aktuella tillståndet för resursen. Se till att testa genom att anropa Get-DscConfiguration när du använder konfigurationen och verifiera att utdata korrekt visar det aktuella tillståndet för datorn. Det är viktigt att testa den separat, eftersom eventuella problem i det här området inte visas när du anropar Start DscConfiguration.

## <a name="call-getsettest-targetresource-functions-directly"></a>Anropa **Get/Set/Test-TargetResource** fungerar direkt ##

Kontrollera att du testar den **Get/Set/Test-TargetResource** funktioner som implementeras i din resurs genom att anropa dem direkt och verifiera att de fungerar som förväntat.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>Kontrollera slutpunkt till slutpunkt med **Start DscConfiguration** ##

Testa **Get/Set/Test-TargetResource** funktioner genom att anropa dem direkt är viktigt, men inte alla problem identifieras det här sättet. Löningen bör beakta betydande del av din testning med hjälp av **Start DscConfiguration** eller pull-servern. Detta är hur användare kommer att använda resursen, så att inte underskattar betydelsen av den här typen av testerna. Möjliga typer av problem:
- Autentiseringsuppgifter/Session fungera annorlunda eftersom DSC-agent körs som en tjänst.  Se till att testa alla funktioner här slutpunkt till slutpunkt.
- Utdata genom att fel **Start DscConfiguration** skiljer sig från de som visas när du anropar den **Set TargetResource** fungera direkt.

## <a name="test-compatability-on-all-dsc-supported-platforms"></a>Testa kompatibilitet alla DSC plattformar som stöds ##
Resursen ska fungera för alla plattformar som stöds DSC (Windows Server 2008 R2 och senare). Installera den senaste WMF (Windows Management Framework) på ditt operativsystem för att hämta den senaste versionen av DSC. Om din resurs inte fungerar på några av dessa plattformar avsiktligt, ska ett visst felmeddelande returneras. Kontrollera också att din resurs kontrollerar om cmdlets som du ringer finns på en viss dator. Windows Server 2012 läggas till ett stort antal nya cmdlet: ar som inte är tillgängliga på Windows Server 2008R2 även med WMF installerats. 

## <a name="verify-on-windows-client-if-applicable"></a>Kontrollera på Windows-klient (om tillämpligt) ##
Ett mycket vanligt test lucka verifierar resursen endast på Windows serverversioner. Många resurser är också utformade att fungera på klienten SKU: er, så om detta är true i ditt fall Glöm inte att testa på dessa plattformar samt. 
## <a name="get-dscresource-lists-the-resource"></a>Get-DSCResource visar resursen ##
När du har distribuerat modulen bör anropar Get-DscResource innehålla resurs bland annat som ett resultat. Om du inte hittar din resurs i listan, kontrollera att filen schema.mof för den här resursen finns. 
## <a name="resource-module-contains-examples"></a>Resursmodul innehåller exempel ##
Skapa goda exempel som hjälper andra att förstå hur du använder den. Det är viktigt, särskilt eftersom många användare hantera exempelkod som dokumentation. 
- Först bör du fastställa exemplen som inkluderas med modulen – åtminstone, du bör omfatta viktigaste användningsområden för din resurs:
- Om din modulen innehåller flera resurser som arbetar tillsammans för en slutpunkt till slutpunkt-scenario, skulle grundläggande slutpunkt till slutpunkt-exempel helst vara den första.
- Inledande exemplen ska vara enkelt – hur du kommer igång med dina resurser i små hanterbara bitar (t.ex. Skapa en ny virtuell Hårddisk)
- Efterföljande exempel bör bygger på dessa exempel (t.ex. Skapa en virtuell dator från en virtuell Hårddisk, ta bort VM, ändra VM) och visa avancerade funktioner (t.ex. Skapa en virtuell dator med dynamiskt minne)
- Exempelkonfigurationer bör parameteriseras (alla värden ska skickas till konfigurationen som parametrar och det inte finnas några hårdkodad värden):
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
- Det är en bra idé att inkludera (kommenterad ut) exempel på hur du anropar konfigurationen med de faktiska värdena i slutet av exempelskriptet. Till exempel i konfigurationen ovan den inte nödvändigtvis visar att det är det bästa sättet att ange UserAgent:

`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer`  
I så fall kan en kommentar tydliggöra avsedda körningen av konfigurationen:
```
<# 
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>  
```
- För varje exempel skriver du en kort beskrivning som förklarar vad det gör och innebörden av parametrarna. 
- Se till exempel täcker de flesta viktiga scenarier för din resurs och om det inte finns något saknas, kontrollera att de alla köra och placera datorn status som önskas.  

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>Felmeddelanden är lätta att förstå och hjälper användarna att lösa problem ##
Bra felmeddelanden bör vara:
- : Största problemet med felmeddelanden finns de ofta inte finns, så se till att de förekommer. 
- Lätt att förstå: mänsklig läsbar, inte otydligt felkoder
- Exakt: Beskriv vad är exakt problemet
- Informell: Råd hur du löser problemet
- Fler: Inte skuld användaren eller se dem anser felaktiga se till att du verifiera fel i slutpunkt till slutpunkt-scenarier (med hjälp av **Start DscConfiguration**), eftersom de kan skilja sig från dem som returneras när du kör resursfunktioner direkt. 

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>Loggmeddelanden är lätta att förstå och informativ (inklusive – verbose,-ETW-loggar och felsökningsloggar) ##
Kontrollera att loggarna för utdata av resursen är enkelt att förstå och ange ett värde för användaren. Resurser bör utdata all information som kan vara användbar för användaren, men fler loggar är inte alltid bättre. Du bör undvika redundans och skickar data som inte ger ytterligare värde – inte göra någon Gå igenom hundratals loggposter för att hitta vad de letar efter. Naturligtvis inga loggar är inte en godtagbar lösning på problemet antingen. 

När du testar, bör du också analysera utförlig och debug-loggar (genom att köra **Start DscConfiguration** med – utförlig och – felsöka växlar på lämpligt sätt), samt som ETW-loggar. Om du vill se DSC ETW loggar, gå till Loggboken och öppna följande mapp: program och tjänster från Microsoft - Windows - Desired State Configuration.  Som standard det ska vara operativa kanalen, men se till att du aktiverar analys och felsökning kanaler innan du kör konfigurationen. Om du vill aktivera analytiska/Debug kanaler, kan du köra skriptet nedan:
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
## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>Resurs-implementeringen innehåller inte hårdkodad sökvägar ##
Kontrollera att det finns inga hårdkodad sökvägar i resurs-implementeringen särskilt om de tar språk (en-us), eller när systemvariabler som kan användas.
Om din resurs behöver åtkomst till specifika sökvägar, använda miljövariabler i stället hardcoding sökväg, eftersom den kan variera på andra datorer.

Exempel:

Istället för:
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
Du kan skriva:
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)} 
```
## <a name="resource-implementation-does-not-contain-user-information"></a>Resurs-implementeringen innehåller inte användarinformation ##
Kontrollera att det finns ingen e-namn, kontoinformation eller namnen på personer i koden.
## <a name="resource-was-tested-with-validinvalid-credentials"></a>Resursen har testats med giltig/ogiltiga autentiseringsuppgifter ##
Om din resurs tar en autentiseringsuppgift som parameter:
- Kontrollera resurs fungerar när lokalt System (eller datorkontot för fjärresurser) inte har åtkomst.
- Kontrollera resurs fungerar med en autentiseringsuppgift som angetts för få, ange och testa 
- Om din resurs har åtkomst till resurser, testa alla varianter som du behöver stöd som:
  - Standard windows-resurser.
  - DFS-resurser.
  - SAMBA resurser (om du vill stödja Linux.)

## <a name="resource-does-not-require-interactive-input"></a>Resursen kräver ingen interaktiva indata ##
**Get/Set/Test-TargetResource** funktioner ska köras automatiskt och måste vänta inte för användaren input någon gång körning (t.ex. Du bör inte använda **Get-Credential** i dessa funktioner). Om du behöver ange användarens indata ska du skickar till konfigurationen som parameter under fasen kompilering. 
## <a name="resource-functionality-was-thoroughly-tested"></a>Resursen funktioner testat noggrant ##
Den här checklistan innehåller objekt som är viktiga för att testa och/eller missas ofta. Det blir bunch tester, främst fungerar de som är specifika för resursen du vill testa och anges inte här. Glöm inte negativt testfall. 
## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>Bästa praxis: Resursmodul innehåller testerna mapp med ResourceDesignerTests.ps1 skript ##
Det är en bra idé att skapa mappen ”test” i Resursmodul, skapa ResourceDesignerTests.ps1 filen och Lägg till testerna via **Test xDscResource** och **Test xDscSchema** för alla resurser i de angivna modul. Det här sättet kan du snabbt Validera scheman för alla resurser från den angivna moduler och gör en förstånd kontrollera innan du publicerar.
För xRemoteFile, ResourceTests.ps1 kan se ut så enkelt som:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof 
```
##<a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>Bästa praxis: resursmapp innehåller resurs designer skript för att skapa schemat ##
Varje resurs ska innehålla ett resurs designer skript som genererar en mof-schemat för resursen. Den här filen ska placeras i <ResourceName>\ResourceDesignerScripts och namnges generera<ResourceName>Schema.ps1 för xRemoteFile resurs för den här filen skulle anropas GenerateXRemoteFileSchema.ps1 och innehåller:
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
## <a name="best-practice-resource-supports--whatif"></a>Bästa praxis: resursen stöder - whatif ##
Om din resurs utför ”farliga” åtgärder, är det en bra idé att implementera - whatif funktionalitet. Kontrollera att whatif utdata korrekt beskriver åtgärder som skulle hända om kommandot kördes utan whatif växeln när det är klart.
Kontrollera också att åtgärder inte körs (det görs inga ändringar till nodens tillstånd) när-whatif växeln finns. Anta exempelvis att vi testar filresurs. Nedan visas enkel konfiguration skapas filen ”test.txt” med innehållet ”test”:
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
Om vi kompilera och köra konfigurationen med växeln-whatif utdata tala om för oss exakt vad som händer när vi kör konfigurationen. Konfigurationen själva men har inte utförts (test.txt filen skapades inte).
```powershell 
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
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

Den här listan är inte komplett, men det täcker många viktiga problem som kan uppstå vid design, utveckling och testning DSC-resurser.

