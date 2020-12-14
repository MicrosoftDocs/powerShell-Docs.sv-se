---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-authenticodesignature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-AuthenticodeSignature
ms.openlocfilehash: 831f40e9bd24cee20eeae54a41e0b022dc6300da
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709870"
---
# Set-AuthenticodeSignature

## SAMMANFATTNING
Lägger till en [Authenticode](/windows-hardware/drivers/install/authenticode) -signatur i ett PowerShell-skript eller en annan fil.

## SYNTAX

### ByPath (standard)

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] [-FilePath] <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -LiteralPath <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByContent

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -SourcePathOrExtension <String[]>
 -Content <Byte[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Set-AuthenticodeSignature`Cmdleten lägger till en Authenticode-signatur till alla filer som stöder SIP (subject Interface Package).

I en PowerShell-skriptfil tar signaturen formen av ett textblock som anger slutet på de instruktioner som körs i skriptet. Om det finns en signatur i filen när denna cmdlet körs, tas signaturen bort.

## EXEMPEL

### Exempel 1 – signera ett skript med ett certifikat från det lokala certifikat arkivet

De här kommandona hämtar ett kod signerings certifikat från PowerShell-certifikat leverantören och använder det för att signera ett PowerShell-skript.

```powershell
$cert=Get-ChildItem -Path Cert:\CurrentUser\My -CodeSigningCert
Set-AuthenticodeSignature -FilePath PsTestInternet2.ps1 -Certificate $cert
```

Det första kommandot använder `Get-ChildItem` cmdleten och PowerShell-certifikat leverantören för att hämta certifikaten i under `Cert:\CurrentUser\My` katalogen i certifikat arkivet. `Cert:`Enheten är den enhet som exponeras av certifikat leverantören. Parametern **CodeSigningCert** , som endast stöds av certifikat leverantören, begränsar de certifikat som hämtas till dem med kod signerings utfärdare. Kommandot lagrar resultatet i `$cert` variabeln.

Det andra kommandot använder `Set-AuthenticodeSignature` cmdleten för att signera `PSTestInternet2.ps1` skriptet. Parametern **sökväg** används för att ange namnet på skriptet och parametern **Certificate** för att ange att certifikatet lagras i `$cert` variabeln.

> [!NOTE]
> Om du använder parametern **CodeSigningCert** med `Get-ChildItem` returneras bara certifikat som har kod signerings auktoritet och innehåller en privat nyckel. Om det inte finns någon privat nyckel kan certifikaten inte användas för signering.

### Exempel 2 – signera ett skript med ett certifikat från en PFX-fil

Dessa kommandon använder `Get-PfxCertificate` cmdleten för att läsa in ett kod signerings certifikat. Använd den sedan för att signera ett PowerShell-skript.

```powershell
$cert = Get-PfxCertificate -FilePath C:\Test\Mysign.pfx
Set-AuthenticodeSignature -FilePath ServerProps.ps1 -Certificate $cert
```

Det första kommandot använder `Get-PfxCertificate` cmdleten för att läsa in C:\Test\MySign.PFX-certifikatet i `$cert` variabeln.

Det andra kommandot använder `Set-AuthenticodeSignature` för att signera skriptet. Parametern  `Set-AuthenticodeSignature` pathname i anger sökvägen till skript filen som signeras och parametern **cert** skickar `$cert` variabeln som innehåller certifikatet till `Set-AuthenticodeSignature` .

Om certifikat filen är lösenordsskyddad, uppmanas du att ange lösen ordet i PowerShell.

### Exempel 3 – Lägg till en signatur som innehåller rot utfärdaren

Det här kommandot lägger till en digital signatur som innehåller rot utfärdaren i förtroende kedjan och den är signerad av en tredjeparts tids stämplings Server.

```powershell
Set-AuthenticodeSignature -FilePath c:\scripts\Remodel.ps1 -Certificate $cert -IncludeChain All -TimestampServer "http://timestamp.fabrikam.com/scripts/timstamper.dll"
```

Kommandot använder parametern **sökväg** för att ange vilket skript som signeras och parametern **certifikat** för att ange det certifikat som sparas i `$cert` variabeln. Parametern **IncludeChain** används för att inkludera alla signaturer i förtroende kedjan, inklusive rot utfärdaren. Den använder också parametern **TimeStampServer** för att lägga till en tidstämpel i signaturen.
Detta förhindrar att skriptet kraschar när certifikatet upphör att gälla.

## PARAMETRAR

### – Certifikat

Anger det certifikat som ska användas för att signera skriptet eller filen. Ange en variabel som lagrar ett objekt som representerar certifikatet eller ett uttryck som hämtar certifikatet.

Om du vill söka efter ett certifikat använder `Get-PfxCertificate` eller använder du `Get-ChildItem` cmdleten i certifikat `Cert:` enheten. Om certifikatet inte är giltigt eller saknar `code-signing` behörighet, Miss lyckas kommandot.

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sökväg

Anger sökvägen till en fil som signeras.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Force

Tillåter cmdleten att lägga till en signatur i en skrivskyddad fil. Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – HashAlgorithm

Anger den hash-algoritm som Windows använder för att beräkna den digitala signaturen för filen.

För PowerShell 3,0 är standardvärdet SHA256, som är algoritmen för Windows standard-hashing. För PowerShell 2,0 är standardvärdet SHA1. Filer som är signerade med en annan hash-algoritm kanske inte kan identifieras på andra system. Vilka algoritmer som stöds beror på vilken version av operativ systemet som används.

En lista över möjliga värden finns i [HashAlgorithmName struct](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SHA256
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeChain

Avgör vilka certifikat i certifikat förtroende kedjan som ingår i den digitala signaturen.
**NotRoot** är standardinställningen.

Giltiga värden är:

- Undertecknare: innehåller bara signerarens certifikat.
- NotRoot: innehåller alla certifikat i certifikat kedjan, förutom rot utfärdaren.
- Alla: innehåller alla certifikat i certifikat kedjan.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: NotRoot
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimestampServer

Använder den angivna tids stämplings servern för att lägga till en tidstämpel i signaturen. Ange URL: en för tids stämplings servern som en sträng.

Tidsstämpeln representerar den exakta tiden som certifikatet lades till i filen. En tidsstämpel förhindrar skriptet från att fungera om certifikatet upphör att gälla eftersom användare och program kan verifiera att certifikatet är giltigt vid tidpunkten för signeringen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Anger sökvägen till en fil som signeras. Till skillnad från **sökväg**, används värdet för parametern **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourcePathOrExtension

Sökväg till filen eller filtypen för innehållet som den digitala signaturen ska läggas till för. Den här parametern används med **innehåll** där fil innehåll skickas som en byte mat ris.

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### – Innehåll

Innehållet i en fil som en byte-matris för vilken den digitala signaturen läggs till. Den här parametern måste användas med parametern **SourcePathOrExtension** . Filens innehåll måste vara i Unicode-format (UTF-16LE).

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller fil Sök vägen till `Set-AuthenticodeSignature` .

## UTDATA

### System. Management. Automation. signatur

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

## RELATERADE LÄNKAR

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Get-ExecutionPolicy](Get-ExecutionPolicy.md)

[Get-PfxCertificate](Get-PfxCertificate.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)
