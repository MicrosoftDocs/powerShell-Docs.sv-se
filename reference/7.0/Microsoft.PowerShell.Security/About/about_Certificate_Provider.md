---
description: Certifikat
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/about/about_certificate_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Certifikat leverantör
ms.openlocfilehash: d1280d34429600e8c06e96a36921df3d04f9eda6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272253"
---
# <a name="certificate-provider"></a>Certifikat leverantör

## <a name="provider-name"></a>Providernamn

Certifikat

## <a name="drives"></a>Enheter

`Cert:`

## <a name="capabilities"></a>Funktioner

**ShouldProcess**

## <a name="short-description"></a>Kort beskrivning

Ger åtkomst till certifikat Arkiv för X. 509 och certifikat i PowerShell.

## <a name="detailed-description"></a>Detaljerad beskrivning

Med PowerShell- **certifikatets** Provider kan du hämta, lägga till, ändra, rensa och ta bort certifikat och certifikat Arkiv i PowerShell.

**Certifikat** enheten är ett hierarkiskt namn område som innehåller certifikat arkiven och certifikaten på din dator.

**Certifikat** leverantören stöder följande cmdletar, som beskrivs i den här artikeln.

- [Get-location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Ange plats](xref:Microsoft.PowerShell.Management.Set-Location)
- [Hämta objekt](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Anropa-objekt](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Flytta objekt](xref:Microsoft.PowerShell.Management.Move-Item)
- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)
- [Ta bort objekt](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a>Typer som exponeras av denna provider

Certifikat enheten exponerar följande typer.

- Lagra platser (Microsoft. PowerShell. commands. X509StoreLocation), som är behållare på hög nivå som grupperar certifikaten för den aktuella användaren och för alla användare. Varje system har en CurrentUser-och LocalMachine-lagringsplats (alla användare).

- Certifikat arkiv (system. Security. Cryptography. X509Certificates. X509Store), som är fysiska butiker där certifikat sparas och hanteras.

- X. 509 **system. Security. Cryptography. X509Certificates. X509Certificate2** -certifikat, som representerar ett X. 509-certifikat på datorn.
  Certifikat identifieras av deras tumavtrycken.

## <a name="navigating-the-certificate-drive"></a>Navigera i certifikat enheten

**Certifikat** leverantören visar certifikat namn området som `Cert:` enheten i PowerShell. Det här kommandot använder `Set-Location` kommandot för att ändra den aktuella platsen till rot certifikat arkivet på LocalMachine Arkiv plats. Använd ett omvänt snedstreck ( \\ ) eller ett snedstreck (/) för att ange `Cert:` enhetens nivå.

```powershell
Set-Location Cert:
```

Du kan också arbeta med certifikat leverantören från någon annan PowerShell-enhet. Om du vill referera till ett alias från en annan plats använder du `Cert:` enhets namnet i sökvägen.

```powershell
PS Cert:\> Set-Location -Path LocalMachine\Root
```

Om du vill återgå till en fil systemen het skriver du enhetens namn. Skriv till exempel:

```powershell
Set-Location C:
```

> [!NOTE]
> PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar. Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location).
> och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).

## <a name="displaying-the-contents-of-the-cert-drive"></a>Visar innehållet i certifikatet: enhet

Detta kommando använder `Get-ChildItem` cmdleten för att Visa certifikat arkiven på CurrentUser-certifikatets lagrings plats.

Om du inte är i `Cert:` enheten använder du en absolut sökväg.

```powershell
PS Cert:\CurrentUser\> Get-ChildItem
```

### <a name="displaying-certificate-properties-within-the-cert-drive"></a>Visar certifikat egenskaper inom certifikatet: enhet

Det här exemplet hämtar ett certifikat med `Get-Item` och lagrar det i en variabel.
Exemplet visar de nya certifikat skript egenskaperna ( **DnsNameList** , **EnhancedKeyUsageList** , **SendAsTrustedIssuer** ) med `Select-Object` .

```powershell
$c = Get-Item cert:\LocalMachine\My\52A149D0393CE8A8D4AF0B172ED667A9E3A1F44E
$c | Format-List DnsNameList, EnhancedKeyUsageList, SendAsTrustedIssuer
```

```output
DnsNameList          : {SERVER01.contoso.com}
EnhancedKeyUsageList : {WiFi-Machine (1.3.6.1.4.1.311.42.2.6),
                       Client Authentication (1.3.6.1.5.5.7.3.2)}
SendAsTrustedIssuer  : False
```

### <a name="find-all-codesigning-certificates"></a>Hitta alla samdesignande certifikat

Detta kommando använder parametrarna **CodeSigningCert** och **rekursivt** för `Get-ChildItem` cmdleten för att hämta alla certifikat på datorn som har kod signerings auktoritet.

```powershell
Get-ChildItem -Path cert: -CodeSigningCert -Recurse
```

### <a name="find-expired-certificates"></a>Hitta utgångna certifikat

Det här kommandot använder **ExpiringInDays** -parametern för `Get-ChildItem` cmdleten för att hämta certifikat som upphör att gälla inom de närmaste 30 dagarna.

```powershell
Get-ChildItem -Path cert:\LocalMachine\WebHosting -ExpiringInDays 30
```

### <a name="find-server-ssl-certificates"></a>Hitta Server SSL-certifikat

Det här kommandot använder **SSLServerAuthentication** -parametern för `Get-ChildItem` cmdleten för att hämta alla Server-SSL-certifikat i butikerna My och webvärding.

```powershell
Get-ChildItem -Path cert:\LocalMachine\My, cert:\LocalMachine\WebHosting `
  -SSLServerAuthentication
```

### <a name="find-expired-certificates-on-remote-computers"></a>Hitta utgångna certifikat på fjärrdatorer

Det här kommandot använder `Invoke-Command` cmdleten för att köra ett `Get-ChildItem` kommando på datorerna SRV01 och Srv02. Värdet noll (0) i parametern **ExpiringInDays** hämtar certifikat på de SRV01-och Srv02-datorer som har upphört att gälla.

```powershell
Invoke-Command -ComputerName Srv01, Srv02 {Get-ChildItem -Path cert:\* `
  -Recurse -ExpiringInDays 0}
```

### <a name="combining-filters-to-find-a-specific-set-of-certificates"></a>Kombinera filter för att hitta en bestämd uppsättning certifikat

Det här kommandot hämtar alla certifikat på LocalMachine Store-platsen som har följande attribut:

- "Fabrikam" i deras DNS-namn
- "Klientautentisering" i deras EKU
- ett värde för `$true` egenskapen **SendAsTrustedIssuer**
- förfaller inte inom de närmaste 30 dagarna.

Egenskapen **NotAfter** lagrar certifikatets förfallo datum.

```powershell
[DateTime] $ValidThrough = (Get-Date) + (New-TimeSpan -Days 30)
Get-ChildItem -Path cert:\* -Recurse -DNSName "*fabrikam*" `
  -EKU "*Client Authentication*" | Where-Object {
                                     $_.SendAsTrustedIssuer -and `
                                     $_.NotAfter -gt $ValidThrough
                                   }
```

## <a name="opening-the-certificates-mmc-snap-in"></a>Öppna MMC-snapin-modulen certifikat

`Invoke-Item`Cmdlet: en använder standard programmet för att öppna en sökväg som du anger. För certifikat är standard programmet MMC-snapin-modulen certifikat.

Det här kommandot öppnar MMC-snapin-modulen certifikat för att hantera det angivna certifikatet.

```powershell
Invoke-Item cert:\CurrentUser\my\6B8223358119BB08840DEE50FD8AF9EA776CE66B
```

## <a name="copying-certificates"></a>Kopiera certifikat

Kopiering av certifikat stöds inte av **certifikat** leverantören. När du försöker kopiera ett certifikat visas det här felet.

```
$path = "Cert:\LocalMachine\Root\E2C0F6662D3C569705B4B31FE2CBF3434094B254"
PS Cert:\LocalMachine\> Copy-Item -Path $path -Destination .\CA\
Copy-Item : Provider operation stopped because the provider does not support
this operation.
At line:1 char:1
+ Copy-Item -Path $path -Destination .\CA\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotImplemented: (:) [Copy-Item],
                              PSNotSupportedException
    + FullyQualifiedErrorId : NotSupported,
                              Microsoft.PowerShell.Commands.CopyItemCommand
```

## <a name="moving-certificates"></a>Flytta certifikat

### <a name="move-all-ssl-server-authentication-certs-to-the-webhosting-store"></a>Flytta alla SSL-certifikat för serverautentisering till webbvärds arkivet

Det här kommandot använder `Move-Item` cmdleten för att flytta ett certifikat från My Store till webb värd arkivet.

`Move-Item` flyttar inte certifikat Arkiv och kommer inte att flytta certifikat till en annan lagrings plats, till exempel att flytta ett certifikat från LocalMachine till CurrentUser. `Move-Item`Cmdleten flyttar certifikat, men flyttar inte privata nycklar.

Det här kommandot använder **SSLServerAuthentication** -parametern för `Get-ChildItem` cmdleten för att hämta certifikat för SSL-serverautentisering i mitt certifikat arkiv.

De returnerade certifikaten är skickas till `Move-Item` -cmdleten, som flyttar certifikaten till värd lagrings platsen.

```powershell
Get-ChildItem cert:\LocalMachine\My -SSLServerAuthentication | Move-Item `
  -Destination cert:\LocalMachine\WebHosting
```

## <a name="deleting-certificates-and-private-keys"></a>Ta bort certifikat och privata nycklar

`Remove-Item`Cmdleten tar bort de certifikat som du anger. Den `-DeleteKey` dynamiska parametern tar bort den privata nyckeln.

### <a name="delete-a-certificate-from-the-ca-store"></a>Ta bort ett certifikat från CA-butiken

Det här kommandot tar bort ett certifikat från CA-certifikatarkivet, men lämnar den tillhör ande privata nyckeln intakt.

I `Cert:` enheten `Remove-Item` stöder cmdleten bara parametrarna **DeleteKey** , **Path** , **whatIf** och **Confirm** . Alla andra parametrar ignoreras.

```powershell
Remove-Item cert:\LocalMachine\CA\5DDC44652E62BF9AA1116DC41DE44AB47C87BDD0
```

### <a name="delete-a-certificate-using-a-wildcards-in-the-dns-name"></a>Ta bort ett certifikat med jokertecken i DNS-namnet

Det här kommandot tar bort alla certifikat som har ett DNS-namn som innehåller "Fabrikam". Den använder **DNSName** -parametern för `Get-ChildItem` cmdleten för att hämta certifikaten och `Remove-Item` cmdleten för att ta bort dem.

```powershell
Get-ChildItem -Path cert:\LocalMachine -DnsName *Fabrikam* | Remove-Item
```

### <a name="delete-private-keys-from-a-remote-computer"></a>Ta bort privata nycklar från en fjärran sluten dator

Den här serien med kommandon aktiverar delegering och tar sedan bort certifikatet och den tillhör ande privata nyckeln på en fjärrdator. Om du vill ta bort en privat nyckel på en fjärrdator måste du använda delegerade autentiseringsuppgifter.

Använd `Enable-WSManCredSSP` cmdleten för att aktivera autentisering av Credential Security Service Provider (CredSSP) på en klient på den lokala S1-datorn.
CredSSP tillåter delegerad autentisering.

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer S1
```

Använd `Connect-WSMan` cmdleten för att ansluta S1-datorn till WinRM-tjänsten på den lokala datorn. När det här kommandot har slutförts visas S1-datorn på den lokala `WSMan:` enheten i PowerShell.

```powershell
Connect-WSMan -ComputerName S1 -Credential Domain01\Admin01
```

Nu kan du använda cmdleten Set-Item i WSMan: Drive för att aktivera CredSSP-attributet för WinRM-tjänsten.

```powershell
Set-Item -Path WSMan:\S1\Service\Auth\CredSSP -Value $true
```

Starta en fjärran sluten session på S1-datorn med `New-PSSession` cmdleten och ange CredSSP-autentisering. Sparar sessionen i `$s` variabeln.

```powershell
$s  = New-PSSession S1 -Authentication CredSSP -Credential Domain01\Admin01
```

Använd slutligen `Invoke-Command` cmdleten för att köra ett `Remove-Item` kommando i sessionen i `$s` variabeln. `Remove-Item`Kommandot använder parametern **DeleteKey** för att ta bort den privata nyckeln tillsammans med det angivna certifikatet.

```powershell
Invoke-Command -Session $s { Remove-Item `
  -Path cert:\LocalMachine\My\D2D38EBA60CAA1C12055A2E1C83B15AD450110C2 `
  -DeleteKey
  }
```

### <a name="delete-expired-certificates"></a>Ta bort utgångna certifikat

Det här kommandot använder **ExpiringInDays** -parametern för `Get-ChildItem` cmdleten med värdet 0 för att hämta certifikat i den webvärdskaps lager som har upphört att gälla.

Variabeln som innehåller de returnerade certifikaten är skickas till `Remove-Item` cmdleten, som tar bort dem. Kommandot använder parametern **DeleteKey** för att ta bort den privata nyckeln tillsammans med certifikatet.

```powershell
$expired = Get-ChildItem cert:\LocalMachine\WebHosting -ExpiringInDays 0
$expired | Remove-Item -DeleteKey
```

## <a name="creating-certificates"></a>Skapa certifikat

`New-Item`Cmdleten skapar inga nya certifikat i **certifikat** leverantören. Använd cmdleten [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) för att skapa ett certifikat för test ändamål.

## <a name="creating-certificate-stores"></a>Skapa certifikat Arkiv

I cert: Drive, `New-Item` skapar cmdleten certifikat Arkiv på platsen för LocalMachine-platsen. Den har stöd för parametrarna **namn** , **sökväg** , **whatIf** och **Confirm** . Alla andra parametrar ignoreras. Kommandot returnerar en **system. Security. Cryptography. X509Certificates. X509Store** som representerar det nya certifikat arkivet.

Det här kommandot skapar ett nytt certifikat Arkiv med namnet "CustomStore" på LocalMachine-lagringsplatsen.

```powershell
New-Item -Path cert:\LocalMachine\CustomStore
```

### <a name="create-a-new-certificate-store-on-a-remote-computer"></a>Skapa ett nytt certifikat Arkiv på en fjärran sluten dator

Det här kommandot skapar ett nytt certifikat Arkiv med namnet "HostingStore" på LocalMachine Store-platsen på Server01-datorn.

Kommandot använder `Invoke-Command` cmdleten för att köra ett `New-Item` kommando på Server01-datorn. Kommandot returnerar en **system. Security. Cryptography. X509Certificates. X509Store** som representerar det nya certifikat arkivet.

```powershell
Invoke-Command { New-Item -Path cert:\LocalMachine\CustomStore } `
  -ComputerName Server01
```

## <a name="creating-client-certificates-for-ws-man"></a>Skapa klient certifikat för WS-Man

Det här kommandot skapar en **ClientCertificate** -post som kan användas av **WS-Management-** klienten. Den nya **ClientCertificate** visas under katalogen **ClientCertificate** som "ClientCertificate_1234567890". Alla parametrar är obligatoriska. **Utfärdaren** måste vara tumavtryck för utfärdarcertifikatet.

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* -Credential $cred
```

## <a name="deleting-certificate-stores"></a>Ta bort certifikat Arkiv

### <a name="delete-a-certificate-store-from-a-remote-computer"></a>Ta bort ett certifikat arkiv från en fjärran sluten dator

Det här kommandot använder `Invoke-Command` cmdleten för att köra ett `Remove-Item` kommando på datorerna S1 och S2. `Remove-Item`Kommandot innehåller parametern **rekursivt** , som tar bort certifikaten i arkivet innan det tas bort.

```powershell
Invoke-Command { Remove-Item -Path cert:\LocalMachine\TestStore -Recurse } `
  -ComputerName S1, S2
```

## <a name="dynamic-parameters"></a>Dynamiska parametrar

Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten. Dessa parametrar är giltiga i alla under kataloger i certifikat leverantören, men gäller endast för certifikat.

> [!NOTE]
> Parametrar som utför filtrering mot `EnhancedKeyUsageList` egenskapen returnerar även objekt med ett tomt `EnhancedKeyUsageList` egenskaps värde.
> Certifikat som har en tom **EnhancedKeyUsageList** kan användas i alla syfte.

Följande parametrar för certifikat leverantörer togs bort i PowerShell 6,0.

- DNSName
- DocumentEncryptionCert
- ANVÄNDNING
- ExpiringInDays
- SSLServerAuthentication

### <a name="codesigningcert-systemmanagementautomationswitchparameter"></a>CodeSigningCert <system. Management. Automation. SwitchParameter>

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Hämta objekt](xref:Microsoft.PowerShell.Management.Get-Item)

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

Den här parametern hämtar certifikat som har "kod signering" i deras värde för egenskapen **EnhancedKeyUsageList** .

### <a name="deletekey-systemmanagementautomationswitchparameter"></a>DeleteKey <system. Management. Automation. SwitchParameter>

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Ta bort objekt](xref:Microsoft.PowerShell.Management.Remove-Item)

Den här parametern tar bort den tillhör ande privata nyckeln när certifikatet tas bort.

> [!IMPORTANT]
> Om du vill ta bort en privat nyckel som är kopplad till ett användar certifikat i `Cert:\CurrentUser` arkivet på en fjärrdator måste du använda delegerade autentiseringsuppgifter. `Invoke-Command`Cmdleten stöder delegering av autentiseringsuppgifter med hjälp av **CredSSP** -parametern. Du bör överväga eventuella säkerhets risker innan du använder `Remove-Item` med `Invoke-Command` och delegering av autentiseringsuppgifter.

Den här parametern introducerades i Windows PowerShell 3,0.

### <a name="itemtype-string"></a>ItemType \<String\>

Med den här parametern kan du ange vilken typ av objekt som skapas av `New-Item` .

I en `Certificate` enhet tillåts följande värden:

- Certifikat leverantör
- Certifikat
- Lagringsplats
- StoreLocation

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="script-properties"></a>Skript egenskaper

Nya skript egenskaper har lagts till i **x509Certificate2** -objektet som representerar certifikaten för att göra det enkelt att söka efter och hantera certifikaten.

- `DnsNameList`: Om du vill fylla i `DnsNameList` egenskapen kopierar certifikat leverantören innehållet från DNSName-posten i SubjectAlternativeName (San)-tillägget. Om SAN-tillägget är tomt fylls egenskapen i med innehåll från certifikatets ämnes fält.

- `EnhancedKeyUsageList`: Om du vill fylla i `EnhancedKeyUsageList` egenskapen kopierar certifikat leverantören OID-egenskaperna för fältet EnhancedKeyUsage (EKU) i certifikatet och skapar ett eget namn för det.

- `SendAsTrustedIssuer`: Om du vill fylla i `SendAsTrustedIssuer` egenskapen kopierar certifikat leverantören `SendAsTrustedIssuer` egenskapen från certifikatet.  Mer information finns i [hantering av betrodda utfärdare för klientautentisering](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers).

Med de här nya funktionerna kan du söka efter certifikat baserat på deras DNS-namn och förfallo datum och särskilja certifikat för klient-och serverautentisering genom att värdet för egenskaperna för utökad nyckel användning (EKU) används.

## <a name="using-the-pipeline"></a>Använda pipelinen

Provider-cmdletar accepterar pipeline-ininformation. Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.
Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.

## <a name="getting-help"></a>Få hjälp

Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.

Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för `Get-Help` att ange en fil system enhet.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path cert:
```

## <a name="see-also"></a>Se även

[about_Providers](../../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Signing](../../Microsoft.PowerShell.Core/About/about_Signing.md)

[Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)

[Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[Get-PfxCertificate](xref:Microsoft.PowerShell.Security.Get-PfxCertificate)
