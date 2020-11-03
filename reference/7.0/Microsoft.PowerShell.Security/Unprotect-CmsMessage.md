---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/unprotect-cmsmessage?view=powershell-7.x&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unprotect-CmsMessage
ms.openlocfilehash: 63d979f1d48da4805111b77c5d1c68d7fc4d0fac
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93263025"
---
# Unprotect-CmsMessage

## SAMMANFATTNING
Dekrypterar innehåll som har krypterats med hjälp av formatet kryptografiskt meddelande-syntax.

## SYNTAX

### ByWinEvent (standard)

```
Unprotect-CmsMessage [-EventLogRecord] <PSObject> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

### ByContent

```
Unprotect-CmsMessage [-Content] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### ByPath

```
Unprotect-CmsMessage [-Path] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### ByLiteralPath

```
Unprotect-CmsMessage [-LiteralPath] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

## BESKRIVNING

`Unprotect-CmsMessage`Cmdleten dekrypterar innehåll som har krypterats med formatet CMS (Cryptographic Message Syntax).

CMS-cmdletarna stöder kryptering och dekryptering av innehåll med hjälp av IETF-standardformatet för kryptografiskt skydd av meddelanden, enligt beskrivningen i [RFC5652](https://tools.ietf.org/html/rfc5652).

CMS-standarden för standard använder kryptering med offentliga nycklar, där nycklarna som används för att kryptera innehåll (den offentliga nyckeln) och de nycklar som används för att dekryptera innehållet (den privata nyckeln) är separata. Din offentliga nyckel kan delas mycket och är inte känslig för data. Om något innehåll krypteras med den här offentliga nyckeln kan bara den privata nyckeln dekryptera den. Mer information finns i [kryptering med offentliga nycklar](https://en.wikipedia.org/wiki/Public-key_cryptography).

`Unprotect-CmsMessage` dekrypterar innehåll som har krypterats i CMS-format. Du kan köra denna cmdlet för att dekryptera innehåll som du har krypterat genom att köra `Protect-CmsMessage` cmdleten. Du kan ange innehåll som du vill dekryptera som en sträng, genom att ange ID-numret för krypterings händelse logg posten eller med sökvägen till det krypterade innehållet. `Unprotect-CmsMessage`Cmdleten returnerar det dekrypterade innehållet.

> [!NOTE]
> Den här cmdleten är endast tillgänglig i Windows.

## EXEMPEL

### Exempel 1: dekryptera ett meddelande

I följande exempel dekrypterar du innehåll som finns på den litterala sökvägen `C:\Users\Test\Documents\PowerShell` . För värdet **för parametern som** krävs, använder det här exemplet tumavtrycket för det certifikat som användes för att utföra krypteringen. Det dekrypterade meddelandet "testa kommandot ny Break alla" är resultatet.

```powershell
$parameters = @{
  LiteralPath = "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
  To = '0f 8j b1 ab e0 ce 35 1d 67 d2 f2 6f a2 d2 00 cl 22 z9 m9 85'
}
Unprotect-CmsMessage -LiteralPath @parameters
```

```Output
Try the new Break All command
```

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
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -EventLogRecord

Anger ett post-ID för händelse loggen som representerar en CMS-krypterings åtgärd.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByWinEvent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -IncludeContext

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

### -LiteralPath

Anger sökvägen till krypterat innehåll som du vill dekryptera. Till skillnad från **sökväg** används värdet för **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 0
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
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Till

Anger ett eller flera CMS-meddelanden som har identifierats i något av följande format:

- Ett faktiskt certifikat (som hämtats från certifikat leverantören).
- Sökväg till en fil som innehåller certifikatet.
- Sökväg till en katalog som innehåller certifikatet.
- Tumavtryck för certifikatet (används för att söka i certifikat arkivet).
- Certifikatets ämnes namn (används för att söka i certifikat arkivet).

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Diagnostics. Eventing. Reader. EventLogRecord eller system. String

Du kan skicka vidare ett objekt som innehåller krypterat innehåll till `Unprotect-CmsMessage` .

## UTDATA

### System. String

Det okrypterade meddelandet.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-CmsMessage](Get-CmsMessage.md)

[Skydda – CmsMessage](Protect-CmsMessage.md)
