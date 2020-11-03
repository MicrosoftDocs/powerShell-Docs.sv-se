---
description: Beskriver hur du hämtar och kör kommandon i kommando historiken.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_history?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_History
ms.openlocfilehash: 8a79690cc409919286d0f14130df72a7fe278010
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270189"
---
# <a name="about-history"></a>Om historik

## <a name="short-description"></a>Kort beskrivning
Beskriver hur du hämtar och kör kommandon i kommando historiken.

## <a name="long-description"></a>Lång beskrivning

När du anger ett kommando i kommando tolken, sparar PowerShell kommandot i kommando historiken. Du kan använda kommandona i historiken som en post för ditt arbete. Du kan också återkalla och köra kommandona från kommando historiken.

PowerShell har två olika historik leverantörer: den inbyggda historiken och historiken som hanteras av **PSReadLine** -modulen. Historiken hanteras separat, men båda historiken är tillgängliga i sessioner där **PSReadLine** läses in.

## <a name="using-the-psreadline-history"></a>Använda PSReadLine historik

PSReadLine-historiken spårar de kommandon som används i alla PowerShell-sessioner.
Historiken skrivs till en central fil per värd. Historik filen är tillgänglig för alla sessioner och innehåller tidigare historik. Historiken tas inte bort när sessionen avslutas. Den historiken kan inte heller hanteras av `*-History` cmdletarna. Mer information finns i [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).

## <a name="using-the-built-in-session-history"></a>Använda den inbyggda tidigare sessionen

Den inbyggda historiken spårar bara de kommandon som används i den aktuella sessionen. Historiken är inte tillgänglig för andra sessioner och tas bort när sessionen avslutas.

### <a name="history-cmdlets"></a>Historik-cmdletar

PowerShell har en uppsättning cmdletar som hanterar kommando historiken.

| Cmdlet           | Alias  | Beskrivning                                |
| ---------------- | ------ | ------------------------------------------ |
| `Get-History`    | `h`    | Hämtar kommando historiken.                  |
| `Invoke-History` | `r`    | Kör ett kommando i kommando historiken.     |
| `Add-History`    |        | Lägger till ett kommando i kommando historiken.     |
| `Clear-History`  | `clhy` | Tar bort kommandon från kommando historiken. |

### <a name="keyboard-shortcuts-for-managing-history"></a>Kortkommandon för att hantera historik

I PowerShell-konsolen kan du använda följande kortkommandon för att hantera kommando historiken.

- <kbd>Nedåtpil</kbd> – visar föregående kommando.
- <kbd>NEDPIL</kbd> – visar nästa kommando.
- <kbd>F7</kbd> – visar kommando historiken.
- <kbd>ESC</kbd> – för att dölja historiken.
- <kbd>F8</kbd> – hittar ett kommando. Skriv ett eller flera tecken och tryck sedan på <kbd>F8</kbd>. Tryck på <kbd>F8</kbd> igen nästa instans.
- <kbd>F9</kbd> – hitta ett kommando efter historik-ID. Skriv in historik-ID och tryck sedan på <kbd>F9</kbd>. Tryck på <kbd>F7</kbd> för att hitta ID: t.
- <kbd>#</kbd>`<string>`</kbd><kbd>TABB</kbd> – Sök igenom historiken efter `*<string>*` och returnerar den senaste matchningen. Om du trycker på <kbd>TABB</kbd> flera gånger går det att använda matchande objekt i historiken.

> [!NOTE]
> Dessa nyckel bindningar implementeras av konsol värd programmet. Andra program, till exempel Visual Studio Code eller Windows Terminal, kan ha olika nyckel bindningar. Bindningarna kan åsidosättas av PSReadLine-modulen. PSReadLine läses in automatiskt när du startar en PowerShell-session.
> Med PSReadLine inläst är <kbd>F7</kbd> och <kbd>F9</kbd> inte kopplade till någon funktion. PSReadLine tillhandahåller inte motsvarande funktioner. Mer information finns i [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).

### <a name="maximumhistorycount"></a>MaximumHistoryCount

`$MaximumHistoryCount`Variabeln Preference fastställer det maximala antalet kommandon som PowerShell sparar i kommando historiken. Standardvärdet är 
4096.

Följande kommando sänker till exempel `$MaximumHistoryCount` till 100-kommandon:

```powershell
$MaximumHistoryCount = 100
```

Tillämpa inställningen genom att starta om PowerShell.

Om du vill spara det nya variabelvärdet för alla PowerShell-sessioner lägger du till tilldelnings uttrycket i en PowerShell-profil. Mer information om profiler finns [about_Profiles](about_Profiles.md).

Mer information om `$MaximumHistoryCount` variabeln Preference finns [about_Preference_Variables](about_Preference_Variables.md).

### <a name="order-of-commands-in-the-history"></a>Ordning för kommandon i historiken

Kommandon läggs till i historiken när kommandot har körts, inte när kommandot anges. Om kommandona tar lite tid att slutföra, eller om kommandona körs i en kapslad prompt, kan det hända att kommandona verkar vara i historiken. Kommandon som körs i en kapslad prompt slutförs bara när du avslutar prompt-nivån.

## <a name="see-also"></a>Se även

- [about_Line_Editing](about_Line_Editing.md)
- [about_Preference_Variables](about_Preference_Variables.md)
- [about_Profiles](about_Profiles.md)
- [about_Variables](about_Variables.md)
- [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)

