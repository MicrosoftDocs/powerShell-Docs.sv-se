---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Nya och uppdaterade cmdletar
ms.openlocfilehash: 9ec31c89c0bc4b111b40e2d4725fa0782a573204
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856247"
---
# <a name="new-and-updated-cmdlets"></a>Nya och uppdaterade cmdletar

Vi har lagt till nya och uppdaterade befintliga cmdletar baserade på feedback från diskussionsgruppen.

## <a name="archive-cmdlets"></a>Arkiv-cmdletar

Två nya cmdletar `Compress-Archive` och `Expand-Archive`, kan du komprimera och expandera ZIP-filer.

Mer information finns i den [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) modulen dokumentation.

## <a name="catalog-cmdlets"></a>Katalog-cmdletar

Två nya cmdletar har lagts till i modulen Microsoft.PowerShell.Security.

- [New-FileCatalog](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [Test-FileCatalog](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

Dessa generera och verifiera filerna för Windows-katalogen.

## <a name="clipboard-cmdlets"></a>Urklipps-cmdletar

`Get-Clipboard` och `Set-Clipboard` gör det enklare att överföra innehåll till och från en Windows PowerShell-session. Urklipps-cmdletar har stöd för bilder, ljudfiler, fillistor och text.

Mer information finns i följande avsnitt:

- [Get-Urklipp](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [Set-Urklipp](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a>Cryptographic Message Syntax CMS-cmdletar

Syntaxen Cryptographic Message Syntax-cmdletarna har stöd för kryptering och dekryptering av innehåll med hjälp av IETF standardformat för att skydda kryptografiskt meddelanden som det dokumenterats i [RFC5652](https://tools.ietf.org/html/rfc5652).

Standard CMS krypteringen implementerar kryptering med offentlig nyckel, där nyckeln används för att kryptera innehållet (den *offentlig nyckel*) och den nyckel som används för att dekryptera innehåll (den *privata nyckeln*) är separata.

Din offentliga nyckel kan delas brett och är inte känsliga data. Allt innehåll som krypterats med den offentliga nyckeln kan endast dekrypteras med den privata nyckeln. Mer information finns i [kryptografi med offentliga nycklar](https://en.wikipedia.org/wiki/Public-key_cryptography).

Mer information finns i följande avsnitt:

- [Get-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage.md)
- [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage.md)
- [Unprotect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/rotect-CmsMessage.md)

Certifikat krävs en identifierare för unika nyckelanvändning (EKU), som ”kodsignering” eller ”krypterad Mail', för att identifiera dem som certifikat för kryptering av data i PowerShell. Om du vill visa dokumentet krypteringscertifikat i certifikatleverantör, du kan använda den **DocumentEncryptionCert** dynamisk parameter för `Get-ChildItem`:

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a>Extrahera och parsa strukturerade objekt från sträng innehåll

### <a name="convertfrom-string"></a>ConvertFrom-sträng

Den nya `ConvertFrom-String` cmdleten stöder två lägen:

- Basic avgränsade parsning
- Autogenererad dold exempel-drivna parsning

Avgränsad parsning, som standard delar upp inmatningen vid blanksteg och tilldelar egenskapsnamn till grupperna.

Den **UpdateTemplate** parametern sparar resultatet av Inlärningsalgoritmen till en kommentar i mallfilen. Detta gör learning bearbeta (långsammaste scenen) en engångskostnad. Kör `ConvertFrom-String` med en mall som innehåller kodade Inlärningsalgoritmen är nu nästan omedelbart.

Mer information finns i [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).

### <a name="convert-string"></a>Convert-String

`Convert-String` kan du tillhandahålla före och efter exempel på hur du vill att texten ska se ut. Cmdlet: en format texten automatiskt.

Mer information finns i [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).

## <a name="updates-to-fileinfo-object"></a>Uppdateringar till FileInfo-objektet

Kan vilseledande filversionsinformation speciellt i fall där filen var korrigeras. WMF 5.0 lägger till nya **FileVersionRaw** och **ProductVersionRaw** skript egenskaper så att **FileInfo** objekt.
Här är egenskaperna som visas för powershell.exe (förutsatt att $pid är ID för PowerShell-process):

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

`Format-Hex` kan du visa text eller binära data i hexadecimalt format.

Mer information finns i [hexadecimalt Format](/powershell/module/microsoft.powershell.utility/format-hex).

## <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem har parametern - Depth

`Get-ChildItem` har nu en **djup** parametern för användning med **Recurse** att begränsa rekursion:

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Modulstöd för att deklarera versionsintervall (1.*, osv)

Nu kan du kombinera **MinimumVersion** och **MaximumVersion** importera modul inom specifika intervall. Parametrarna har också stöd för jokertecken.

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

Det finns många scenarier där youneed för unik identifierare. Den `New-GUID` cmdlet ger ett enkelt sätt att skapa en ny GUID.

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a>NoNewLine-parametern

`Out-File`, `Add-Content`, och `Set-Content` har nu en ny **NoNewline** växeln som utesluter en ny rad efter utdatan. Till exempel:

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt

```Output
This is a single sentence.
```

Utan **NoNewline** anges varje fragment är på en separat rad:

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

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a>Interagera med symboliska länkar med förbättrad artikel-cmdletar

Objekt-cmdlet och några relaterade cmdlets har utökats för att stödja symboliska länkar.

### <a name="symbolic-link-files"></a>Symbolisk länk filer

I det här exemplet skapar vi en ny symbolisk länk-fil med namnet MySymLinkFile.txt i C:\Temp som länkar till $pshome\profile.ps1. Alla tre exempel ger samma resultat.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a>Symbolisk länk kataloger

I det här exemplet skapar vi en ny symbolisk länk-katalog med namnet MySymLinkDir i C:\Temp som länkar till mappen $pshome. Alla tre exempel ger samma resultat.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a>Hårda länkar

Samma kombinationer av **sökväg** och **namn** tillåts enligt beskrivningen ovan.

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a>Directory vägkorsningar

Samma kombinationer av **sökväg** och **namn** tillåts enligt beskrivningen ovan.

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a>Get-ChildItem

`Get-ChildItem` Nu visar en l i den **läge** egenskap som anger en symbolisk länkfil eller katalog.

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

Ta bort symboliska länkar fungerar som att ta bort någon annan objekttyp av.

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

Använd den **kraft** parametern för att ta bort filer i målkatalogen och den symboliska länken.

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a>New-TemporaryFile

Ibland måste du skapa en temporär fil i ett skript. Du kan nu göra detta med den `New-TemporaryFile` cmdlet:

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a>Hantering av nätverksväxling med PowerShell

Nätverksswitch-cmdlets med WMF 5.0, kan du använda växeln, virtuellt LAN (VLAN) och grundläggande nivå 2-portkonfiguration av nätverksväxel för Windows Server 2012 R2-logotyp-certifierade nätverksväxlar. Med dessa cmdletar kan du utföra:

- Global växla konfiguration, till exempel:
  - Set-värdnamn
  - Ange växeln banderoll
  - Spara konfigurationen
  - Aktivera eller inaktivera funktionen

- VLAN-konfiguration:
  - Skapa eller ta bort VLAN
  - Aktivera eller inaktivera VLAN
  - Räkna upp VLAN
  - Ange eget namn som ett VLAN

- Portkonfiguration för Layer 2:
  - Räkna upp portar
  - Aktivera eller inaktivera portar
  - Ange port lägen och egenskaper
  - Lägga till eller associera VLAN till segment eller åtkomst på port

Mer information finns i den [NetworkSwitchManager](/powershell/module/networkswitchmanager/) dokumentation.

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>Skapa PowerShell-cmdletar baserade på en OData-slutpunkt med ODataUtils

Modulen ODataUtils kan generation av PowerShell-cmdletar från REST-slutpunkter som har stöd för OData. Modulen Microsoft.PowerShell.ODataUtils innehåller följande funktioner:

- Kanal för ytterligare information från serversidan slutpunkten till klienten.
- Stöd för klientsidan växling
- Serversidan filtrering med hjälp av väljer parametern -
- Stöd för web-begärandehuvuden

Proxy-cmdletar som genererats av den `Export-ODataEndPointProxy` cmdleten ger ytterligare information från serversidan OData-slutpunkten på den **Information** stream.

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

I följande exempel vi hämtar topprodukt och samla in utdata i den `$infoStream` variabeln.

Genom att ange **IncludeTotalResponseCount** parameter, vi får det totala antalet av alla de **produkten** poster som är tillgängliga på servern.

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

Du kan hämta poster från servern i batchar med stöd för klientsidan sidindelning. Detta är användbart när du måste hämta en stor mängd data från servern via nätverket.

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

Genererade proxy-cmdletarna har stöd för den **Välj** parameter som används som ett filter för att ta emot endast postegenskaperna som klienten behöver. Den filtrering utförs på servern, vilket minskar mängden data som överförs över nätverket.

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

Den `Export-ODataEndpointProxy` cmdlet och proxy-cmdletar som genereras av det, stöder nu den **rubriker** parametern. Rubriken kan användas på channel ytterligare information som förväntas av OData-slutpunkten.

I följande exempel visas en hash-tabell som innehåller en prenumerationsnyckel som har angetts för den **rubriker** parametern. Det här är ett typexempel för tjänster som väntar en prenumerationsnyckel för autentisering.

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
