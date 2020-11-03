---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Send-MailMessage
ms.openlocfilehash: 6f98c95e6c0144f76393e9d28454833097894512
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264861"
---
# Send-MailMessage

## SAMMANFATTNING
Skickar ett e-postmeddelande.

## SYNTAX

### Alla

```
Send-MailMessage [-To] <string[]> [-Subject] <string> [[-Body] <string>] [[-SmtpServer] <string>]
 -From <string> [-Attachments <string[]>] [-Bcc <string[]>] [-BodyAsHtml] [-Encoding <Encoding>]
 [-Cc <string[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 [-Priority <MailPriority>] [-Credential <pscredential>] [-UseSsl] [-Port <int>]
 [<CommonParameters>]
```

## BESKRIVNING

`Send-MailMessage`Cmdleten skickar ett e-postmeddelande inifrån PowerShell.

Du måste ange en Simple Mail Transfer Protocol-server (SMTP) eller `Send-MailMessage` kommandot fungerar inte. Använd parametern **SmtpServer** eller Ställ in `$PSEmailServer` variabeln på en giltig SMTP-server.
Värdet som tilldelas `$PSEmailServer` är standard SMTP-inställningen för PowerShell. Mer information finns i [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

> [!WARNING]
> `Send-MailMessage`Cmdleten är föråldrad. Denna cmdlet garanterar inte säkra anslutningar till SMTP-servrar. Det finns ingen omedelbar ersättning tillgänglig i PowerShell, men vi rekommenderar att du inte använder `Send-MailMessage` . Mer information finns i [Platform Compatibility NOTE DE0005](https://aka.ms/SendMailMessage).

## EXEMPEL

### Exempel 1: Skicka ett e-postmeddelande från en person till en annan person

I det här exemplet skickas ett e-postmeddelande från en person till en annan person.

Parametrarna **from** , **to** och **subject** krävs av `Send-MailMessage` . I det här exemplet används standard `$PSEmailServer` variabeln för SMTP-servern, så **SmtpServer** -parametern behövs inte.

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

`Send-MailMessage`Cmdleten använder parametern **from** för att ange meddelandets avsändare. Parametern **to** anger meddelandets mottagare. **Ämnes** parametern använder text strängen **Testa e-post** som meddelandet eftersom den valfria **text** parametern inte ingår.

### Exempel 2: skicka en bifogad fil

Det här exemplet skickar ett e-postmeddelande med en bifogad fil.

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

`Send-MailMessage`Cmdleten använder parametern **from** för att ange meddelandets avsändare. Parametern **to** anger meddelandets mottagare. **Ämnes** parametern beskriver meddelandets innehåll. **Body** -parametern är meddelandets innehåll.

Parametern **Attachments** anger filen i den aktuella katalogen som är kopplad till e-postmeddelandet. **Prioritets** parametern anger meddelandet till **hög** prioritet. Parametern **-DeliveryNotificationOption** anger två värden, **OnSuccess** och **onFailure**. Avsändaren får e-postaviseringar för att bekräfta att meddelande leveransen har lyckats eller misslyckats.
Parametern **SmtpServer** anger SMTP-servern till **SMTP.fabrikam.com**.

### Exempel 3: skicka e-post till en distributions lista

Det här exemplet skickar ett e-postmeddelande till en distributions lista.

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

`Send-MailMessage`Cmdleten använder parametern **from** för att ange meddelandets avsändare. Parametern **to** anger meddelandets mottagare. Parametern **CC** skickar en kopia av meddelandet till den angivna mottagaren. Parametern **hemlig** kopia skickar en hemlig kopia av meddelandet. En hemlig kopia är en e-postadress som är dold från de andra mottagarna. **Subject** -parametern är meddelandet eftersom den valfria **text** parametern inte ingår.

Parametern **Credential** anger en domän administratörs autentiseringsuppgifter som används för att skicka meddelandet. Parametern **UseSsl** anger att SSL (Secure Socket Layer) skapar en säker anslutning.

## PARAMETRAR

### -Bilagor

Anger sökväg och fil namn för de filer som ska bifogas i e-postmeddelandet. Du kan använda den här parametern eller Ange sökvägar och fil namn till `Send-MailMessage` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PsPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – Hemlig kopia

Anger e-postadresserna som får en kopia av e-postmeddelandet men som inte visas som mottagare av meddelandet. Ange namn (valfritt) och e-postadressen, till exempel `Name <someone@fabrikam.com>` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Body

Anger e-postmeddelandets innehåll.

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

### -BodyAsHtml

Anger att värdet för **text** parametern innehåller HTML.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: BAH

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CC

Anger e-postadresserna som en kopia av e-postmeddelandet skickas till. Ange namn (valfritt) och e-postadressen, till exempel `Name <someone@fabrikam.com>` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Standard är den aktuella användaren.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01**. Eller ange ett **PSCredential** -objekt, till exempel ett från `Get-Credential` cmdleten.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DeliveryNotificationOption

Anger alternativ för leverans meddelande för e-postmeddelandet. Du kan ange flera värden.
Inget värde är standardvärdet. Aliaset för den här parametern är **DNO**.

Leverans meddelandena skickas till adressen i **från** -parametern.

De acceptabla värdena för den här parametern är följande:

- `None`: Ingen avisering.
- `OnSuccess`: Meddela om leveransen lyckades.
- `OnFailure`: Meddela om leveransen Miss lyckas.
- `Delay`: Meddela om leveransen är försenad.
- `Never`: Meddela aldrig.

```yaml
Type: System.Net.Mail.DeliveryNotificationOptions
Parameter Sets: (All)
Aliases: DNO
Accepted values: None, OnSuccess, OnFailure, Delay, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Anger typ av kodning för mål filen. Standardvärdet är `Default`.

De acceptabla värdena för den här parametern är följande:

- `ASCII` Använder ASCII-teckenuppsättning (7-bitars).
- `BigEndianUnicode` Använder UTF-16 med big-endian byte-ordningen.
- `Default` Använder kodningen som motsvarar systemets aktiva tecken tabell (vanligt vis ANSI).
- `OEM` Använder kodningen som motsvarar systemets aktuella OEM Code-sida.
- `Unicode` Använder UTF-16 med en liten-endian-order.
- `UTF7` Använder UTF-7.
- `UTF8` Använder UTF-8.
- `UTF32` Använder UTF-32 med en liten-endian-order.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases: BE
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### – Från

Parametern **from** måste anges. Den här parametern anger avsändarens e-postadress. Ange ett namn (valfritt) och en e-postadress, till exempel `Name <someone@fabrikam.com>` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Anger en alternativ port på SMTP-servern. Standardvärdet är 25, vilket är standard-SMTP-porten.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 25
Accept pipeline input: False
Accept wildcard characters: False
```

### -Prioritet

Anger e-postmeddelandets prioritet. Normal är standardvärdet. De acceptabla värdena för den här parametern är normal, hög och låg.

```yaml
Type: System.Net.Mail.MailPriority
Parameter Sets: (All)
Aliases:
Accepted values: Normal, High, Low

Required: False
Position: Named
Default value: Normal
Accept pipeline input: False
Accept wildcard characters: False
```

### -SmtpServer

Anger namnet på den SMTP-server som skickar e-postmeddelandet.

Standardvärdet är värdet för Preference- `$PSEmailServer` variabeln. Om Preference-variabeln inte har angetts och den här parametern inte används, `Send-MailMessage` Miss lyckas kommandot.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ComputerName

Required: False
Position: 3
Default value: $PSEmailServer
Accept pipeline input: False
Accept wildcard characters: False
```

### -Subject

**Ämnes** parametern måste anges. Den här parametern anger ämnet för e-postmeddelandet.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sub

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Till

Parametern **to** måste anges. Den här parametern anger mottagarens e-postadress. Om det finns flera mottagare avgränsar du deras adresser med kommatecken ( `,` ). Ange namn (valfritt) och e-postadressen, till exempel `Name <someone@fabrikam.com>` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSsl

Secure Sockets Layer-protokollet (SSL) används för att upprätta en säker anslutning till fjärrdatorn för att skicka e-post. Som standard används inte SSL.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare sökvägen och fil namnen för bilagor till `Send-MailMessage` .

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)
