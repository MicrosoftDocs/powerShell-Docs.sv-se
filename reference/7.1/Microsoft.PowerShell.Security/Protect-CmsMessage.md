---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/protect-cmsmessage?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Protect-CmsMessage
ms.openlocfilehash: 4a181c68527c7b9d3a698ec31bbcadbe36762376
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347235"
---
# Protect-CmsMessage

## SAMMANFATTNING
Krypterar innehåll med hjälp av formatet kryptografiskt meddelande-syntax.

## SYNTAX

### ByContent (standard)

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <PSObject> [[-OutFile] <String>]
 [<CommonParameters>]
```

### ByPath

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <String> [[-OutFile] <String>] [<CommonParameters>]
```

### ByLiteralPath

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <String> [[-OutFile] <String>]
 [<CommonParameters>]
```

## BESKRIVNING

`Protect-CmsMessage`Cmdleten krypterar innehåll med hjälp av CMS-formatet (Encryption Message Syntax).

CMS-cmdletarna stöder kryptering och dekryptering av innehåll med hjälp av IETF-formatet som dokumenteras av [RFC5652](https://tools.ietf.org/html/rfc5652.html).

CMS-standarden för standard använder kryptering med offentliga nycklar, där nycklarna som används för att kryptera innehåll (den offentliga nyckeln) och de nycklar som används för att dekryptera innehållet (den privata nyckeln) är separata. Din offentliga nyckel kan delas mycket och är inte känslig för data. Om något innehåll krypteras med den här offentliga nyckeln kan bara den privata nyckeln dekryptera den. Mer information finns i [kryptering med offentliga nycklar](https://en.wikipedia.org/wiki/Public-key_cryptography).

Innan du kan köra `Protect-CmsMessage` cmdleten måste du konfigurera ett krypterings certifikat.
För att kunna identifieras i PowerShell kräver krypterings certifikat ett unikt ID för utökad nyckel användning ([EKU](/windows/desktop/SecCrypto/eku)) för att identifiera dem som data krypterings certifikat (till exempel ID: n för kod signering och krypterad e-post). Ett exempel på ett certifikat som skulle fungera för dokument kryptering finns i exempel 1 i den här artikeln.

Stöd för Linux och macOS lades till i PowerShell 7,1.

## EXEMPEL

### Exempel 1: skapa ett certifikat för kryptering av innehåll

Innan du kan köra `Protect-CmsMessage` cmdleten måste du skapa ett krypterings certifikat. Använd följande text och ändra namnet på ämnes raden till ditt namn, din e-postadress eller annan identifierare och spara certifikatet i en fil (till exempel `DocumentEncryption.inf` , som visas i det här exemplet).

```powershell
# Create .INF file for certreq
{[Version]
Signature = "$Windows NT$"

[Strings]
szOID_ENHANCED_KEY_USAGE = "2.5.29.37"
szOID_DOCUMENT_ENCRYPTION = "1.3.6.1.4.1.311.80.1"

[NewRequest]
Subject = "cn=youralias@emailaddress.com"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT_KEY_ENCIPHERMENT_KEY_USAGE | CERT_DATA_ENCIPHERMENT_KEY_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"

[Extensions]
%szOID_ENHANCED_KEY_USAGE% = "{text}%szOID_DOCUMENT_ENCRYPTION%"
} | Out-File -FilePath DocumentEncryption.inf

# After you have created your certificate file, run the following command to add
# the certificate file to the certificate store. Now you are ready to encrypt and
# decrypt content with the next two examples.
certreq.exe -new DocumentEncryption.inf DocumentEncryption.cer
```

### Exempel 2: kryptera ett meddelande som skickas via e-post

```powershell
$Protected = "Hello World" | Protect-CmsMessage -To "*youralias@emailaddress.com*"
```

I följande exempel krypterar du ett meddelande, "Hello World", genom att skicka det till `Protect-CmsMessage` cmdleten och sedan spara det krypterade meddelandet i en variabel. Parametern **to** använder värdet för ämnes raden i certifikatet.

### Exempel 3: Visa dokument krypterings certifikat

```
PS C:\> cd Cert:\CurrentUser\My
PS Cert:\CurrentUser\My> Get-ChildItem -DocumentEncryptionCert
```

Om du vill visa dokument krypterings certifikat i certifikat leverantören kan du lägga till den dynamiska parametern **DocumentEncryptionCert** för [Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md), som är tillgänglig endast när certifikat leverantören har lästs in.

## PARAMETRAR

### – Innehåll

Anger en **PSObject** som innehåller innehåll som du vill kryptera. Du kan till exempel kryptera innehållet i ett händelse meddelande och sedan använda variabeln som innehåller meddelandet ( `$Event` i det här exemplet) som värde för **innehålls** parametern: `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1` . Du kan också använda `Get-Content` cmdleten för att hämta innehållet i en fil, till exempel ett Microsoft Word-dokument, och spara innehållet i en variabel som du använder som värde för **innehålls** parametern.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByContent
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Anger sökvägen till det innehåll som du vill kryptera. Till skillnad från **sökväg** används värdet för **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fil

Anger sökvägen och fil namnet för en fil som du vill skicka det krypterade innehållet till.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger sökvägen till det innehåll som du vill kryptera.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Till

Anger ett eller flera CMS-meddelanden som har identifierats i något av följande format:

- Ett faktiskt certifikat (som hämtats från certifikat leverantören).
- Sökväg till filen som innehåller certifikatet.
- Sökväg till en katalog som innehåller certifikatet.
- Tumavtryck för certifikatet (används för att söka i certifikat arkivet).
- Certifikatets ämnes namn (används för att söka i certifikat arkivet).

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

## UTDATA

## ANTECKNINGAR

## RELATERADE LÄNKAR

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-CmsMessage](Get-CmsMessage.md)

[Ta bort skydd-CmsMessage](Unprotect-CmsMessage.md)
