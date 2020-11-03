---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-cmsmessage?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CmsMessage
ms.openlocfilehash: bafe666c5cb24accfc931c58cb1805e85455ab30
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265269"
---
# Get-CmsMessage

## SAMMANFATTNING
Hämtar innehåll som har krypterats med hjälp av formatet kryptografiskt meddelande-syntax.

## SYNTAX

### ByContent

```
Get-CmsMessage [-Content] <String> [<CommonParameters>]
```

### ByPath

```
Get-CmsMessage [-Path] <String> [<CommonParameters>]
```

### ByLiteralPath

```
Get-CmsMessage [-LiteralPath] <String> [<CommonParameters>]
```

## BESKRIVNING

`Get-CmsMessage`Cmdleten hämtar innehåll som har krypterats med formatet CMS (Encryption Message Syntax).

CMS-cmdletarna stöder kryptering och dekryptering av innehåll med hjälp av IETF-formatet för kryptografiskt skydd av meddelanden, enligt vad som dokumenterats av [RFC5652](https://tools.ietf.org/html/rfc5652).

CMS-standarden för standard använder kryptering med offentliga nycklar, där nycklarna som används för att kryptera innehåll (den offentliga nyckeln) och de nycklar som används för att dekryptera innehållet (den privata nyckeln) är separata. Din offentliga nyckel kan delas mycket och är inte känslig för data. Om något innehåll krypteras med den här offentliga nyckeln kan bara den privata nyckeln dekryptera den. Mer information finns i [kryptering med offentliga nycklar](https://en.wikipedia.org/wiki/Public-key_cryptography).

`Get-CmsMessage` hämtar innehåll som har krypterats i CMS-format. Det varken dekrypterar eller tar bort skyddet av innehåll. Du kan köra denna cmdlet för att hämta innehåll som du har krypterat genom att köra `Protect-CmsMessage` cmdleten. Du kan ange innehåll som du vill dekryptera som en sträng eller med sökvägen till det krypterade innehållet. Du kan skicka vidare resultatet av `Get-CmsMessage` till för `Unprotect-CmsMessage` att dekryptera innehållet, förutsatt att du har information om det dokument krypterings certifikat som användes för att kryptera innehållet.

## EXEMPEL

### Exempel 1: Hämta krypterat innehåll

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg.Content
```

```Output
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMBFWxlZWhv
bG1AbGljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYP5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNXmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPRwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84AHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1AtDj7nSJc=
-----END CMS-----
```

Det här kommandot hämtar krypterat innehåll som finns på C:\Users\Test\Documents\PowerShell\Future_Plans.txt.

### Exempel 2: pipe-krypterat innehåll till Unprotect-CmsMessage

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg | Unprotect-CmsMessage -To "cn=youralias@emailaddress.com"
```

```Output
Try the new Break All command
```

Det här kommandot rör resultatet av `Get-CmsMessage` cmdleten från exempel 1 till `Unprotect-CmsMessage` , för att dekryptera meddelandet och läsa det i oformaterad text. I det här fallet är värdet för parametern **till** värdet för certifikatets ämnes rad för kryptering. Det dekrypterade meddelandet "testa kommandot ny Break alla" är resultatet.

## PARAMETRAR

### – Innehåll

Anger en krypterad sträng eller en variabel som innehåller en krypterad sträng.

```yaml
Type: System.String
Parameter Sets: ByContent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Anger sökvägen till krypterat innehåll som du vill hämta. Till skillnad från **sökväg** används värdet för **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken, omger du var och en med enkla citat tecken.
Enkla citat tecken instruerar PowerShell att inte tolka omslutna tecken som escape-tecken.

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

### -Path

Anger sökvägen till krypterat innehåll som du vill dekryptera.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

## ANTECKNINGAR

## RELATERADE LÄNKAR

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Skydda – CmsMessage](Protect-CmsMessage.md)

[Ta bort skydd-CmsMessage](Unprotect-CmsMessage.md)
