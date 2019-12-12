---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Nya och uppdaterade cmdletar
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71145028"
---
# <a name="new-and-updated-cmdlets"></a>Nya och uppdaterade cmdletar

Vi har lagt till nya och uppdaterade befintliga cmdlets baserade på feedback från communityn.

## <a name="archive-cmdlets"></a>Arkiv-cmdletar

Med två nya cmdletar, `Compress-Archive` och `Expand-Archive`, kan du komprimera och expandera ZIP-filer.

Mer information finns i dokumentationen för modulen [Microsoft. PowerShell. Archive](/powershell/module/microsoft.powershell.archive/) .

## <a name="catalog-cmdlets"></a>Katalog-cmdletar

Två nya cmdletar har lagts till i modulen Microsoft. PowerShell. Security.

- [New-FileCatalog](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [Test-FileCatalog](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

Dessa genererar och validerar Windows Catalog-filer.

## <a name="clipboard-cmdlets"></a>Urklipps-cmdletar

`Get-Clipboard` och `Set-Clipboard` göra det enklare för dig att överföra innehåll till och från en Windows PowerShell-session. Urklipps-cmdletarna stöder bilder, ljudfiler, fil listor och text.

Mer information finns i följande avsnitt:

- [Hämta Urklipp](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [Ange Urklipp](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a>Cmdletar för kryptografiskt meddelande syntax (CMS)

Cmdletarna för kryptografisk meddelandesyntax stöder kryptering och dekryptering av innehåll med hjälp av IETFs standardformat för kryptografiskt skydd av meddelanden som dokumenteras av [RFC5652](https://tools.ietf.org/html/rfc5652.html).

Standardvärdet för CMS-kryptering implementerar kryptering med offentliga nycklar, där nyckeln som används för att kryptera innehåll (den *offentliga nyckeln*) och den nyckel som används för att dekryptera innehållet (den *privata nyckeln*) är separata.

Din offentliga nyckel kan delas mycket och är inte känslig för data. Alla innehåll som krypteras med den offentliga nyckeln kan bara dekrypteras med den privata nyckeln. Mer information finns i [kryptering med offentliga nycklar](https://en.wikipedia.org/wiki/Public-key_cryptography).

Mer information finns i följande avsnitt:

- [Get-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [Skydda – CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [Ta bort skydd-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

Certifikat kräver en unik nyckel användnings identifierare (EKU), t. ex. kod signering eller krypterad e-post, för att identifiera dem som data krypterings certifikat i PowerShell. Om du vill visa dokument krypterings certifikat i certifikat leverantören kan du använda den dynamiska **DocumentEncryptionCert** -parametern för `Get-ChildItem`:

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a>Extrahera och parsa strukturerade objekt från sträng innehåll

### <a name="convertfrom-string"></a>ConvertFrom-sträng

New `ConvertFrom-String`-cmdlet har stöd för två lägen:

- Grundläggande avgränsad parsning
- Automatiskt genererad exempel-driven parsning

Delimited parsing, som standard, delar in indatamängden med blank steg och tilldelar de resulterande grupperna egenskaps namn.

Parametern **UpdateTemplate** sparar resultatet av inlärningen i en kommentar i mallfilen. Detta gör inlärnings processen (den långsammaste fasen) till en engångs kostnad. Att köra `ConvertFrom-String` med en mall som innehåller den kodade inlärnings algoritmen är nu nästan momentan.

Mer information finns i [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).

### <a name="convert-string"></a>Convert-String

med `Convert-String` kan du ange före och efter exempel på hur du vill att texten ska se ut. -Cmdleten formaterar texten automatiskt.

Mer information finns i [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).

## <a name="updates-to-fileinfo-object"></a>Uppdateringar till FileInfo-objektet

Fil versions information kan vara missvisande, särskilt i de fall där filen har korrigerats. WMF 5,0 lägger till nya **FileVersionRaw** -och **ProductVersionRaw** -skript egenskaper till **fileinfo** -objekt.
Här följer de egenskaper som visas för PowerShell. exe (förutsatt att $pid är PowerShell-processens ID):

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a>Format-Hex

med `Format-Hex` kan du Visa text data eller binära data i hexadecimalt format.

Mer information finns i [format-hex](/powershell/module/microsoft.powershell.utility/format-hex).

## <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem har-djupgående-parameter

`Get-ChildItem` har nu en **djup** parameter som används med **rekursivt** för att begränsa den rekursion:

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Moduler har stöd för att deklarera versions intervall (1. * osv.)

Nu kan du kombinera **MinimumVersion** och **MaximumVersion** för att importera modulen inom ett angivet intervall. Parametrarna stöder också jokertecken.

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a>New-Guid

Det finns många scenarier där Youneed för unik identifierare. `New-GUID` cmdlet är ett enkelt sätt att skapa ett nytt GUID.

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a>NoNewLine-parameter

`Out-File`, `Add-Content`och `Set-Content` har nu en ny **NoNewline** -växel som utelämnar en ny rad efter utdata. Till exempel:

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

Om inget **NoNewline** anges så finns varje fragment på en separat rad:

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a>Interagera med symboliska länkar med förbättrade objekt-cmdletar

Objekt-cmdleten och några relaterade cmdlets har utökats för att stödja symboliska länkar.

### <a name="symbolic-link-files"></a>Symboliska länkade filer

I det här exemplet skapar vi en ny symbolisk länk fil med namnet MySymLinkFile. txt i C:\Temp som länkar till $pshome \profile.ps1. Alla tre exempel ger samma resultat.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a>Symboliska länk kataloger

I det här exemplet skapar vi en ny symbolisk länk katalog med namnet MySymLinkDir i C:\Temp som länkar till mappen $pshome. Alla tre exempel ger samma resultat.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a>Hårda länkar

Samma kombination av **sökväg** och **namn** som tillåts enligt beskrivningen ovan.

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a>Katalog Knut punkter

Samma kombination av **sökväg** och **namn** som tillåts enligt beskrivningen ovan.

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a>Get-ChildItem

`Get-ChildItem` visar nu en "l" i egenskapen **mode** för att ange en symbolisk länk fil eller katalog.

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a>Ta bort objekt

Borttagning av symboliska länkar fungerar som att ta bort alla andra objekt typer.

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

Använd parametern **Force** för att ta bort filerna i mål katalogen och den symboliska länken.

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a>New-TemporaryFile

Ibland måste du skapa en temporär fil i dina skript. Nu kan du göra detta med `New-TemporaryFile`-cmdlet:

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a>Hantering av nätverksväxling med PowerShell

Nätverks växel-cmdletar, som introducerades i WMF 5,0, gör att du kan använda Switch, virtuellt LAN (VLAN) och grundläggande Layer 2 nätverks växel port konfiguration för Windows Server 2012 R2 logo typ-certifierade nätverks växlar. Med dessa cmdlet: ar kan du utföra:

- Konfiguration av global växel, till exempel:
  - Ange värdnamn
  - Ange växel banderoll
  - Beständig konfiguration
  - Aktivera eller inaktivera funktion

- VLAN-konfiguration:
  - Skapa eller ta bort VLAN
  - Aktivera eller inaktivera VLAN
  - Räkna upp VLAN
  - Ange ett eget namn på ett VLAN

- Nivå 2-port konfiguration:
  - Räkna upp portar
  - Aktivera eller inaktivera portar
  - Ange port lägen och egenskaper
  - Lägg till eller koppla VLAN till trunk eller åtkomst på porten

Mer information finns i [NetworkSwitchManager](/powershell/module/networkswitchmanager/) -dokumentationen.

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>Generera PowerShell-cmdletar baserade på en OData-slutpunkt med ODataUtils

Med modulen ODataUtils kan du skapa PowerShell-cmdlets från REST-slutpunkter som stöder OData. Modulen Microsoft. PowerShell. ODataUtils innehåller följande funktioner:

- Kanal ytterligare information från slut punkten på Server sidan till klient sidan.
- Stöd för sid indelning på klient Sidan
- Filtrering på Server sidan med hjälp av parametern-Select
- Stöd för webb begär ande rubriker

Proxy-cmdletarna som genereras av `Export-ODataEndPointProxy`-cmdleten ger ytterligare information från OData-slutpunkten på Server sidan i **informations** data strömmen.

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

I följande exempel hämtar vi den översta produkten och fångar in utdata i `$infoStream` variabeln.

Genom att ange parametern **IncludeTotalResponseCount** får vi det totala antalet tillgängliga **produkt** poster på servern.

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

Du kan hämta poster från servern i batchar med stöd för växling vid fel på klient sidan. Detta är användbart när du måste få en stor mängd data från servern över nätverket.

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

De genererade proxy-cmdletarna stöder **Select** -parametern som används som ett filter för att endast ta emot de post egenskaper som klienten behöver. Filtreringen sker på servern, vilket minskar mängden data som överförs via nätverket.

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

`Export-ODataEndpointProxy`-cmdleten och proxy-cmdletarna som genereras av den, stöder nu **headers** -parametern. Sidhuvudet kan användas för att kanal ytterligare information som förväntas av OData-slutpunkten.

I följande exempel anges en hash-tabell som innehåller en prenumerations nyckel för parametern **headers** . Detta är ett typiskt exempel för tjänster som förväntar sig en prenumerations nyckel för autentisering.

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
