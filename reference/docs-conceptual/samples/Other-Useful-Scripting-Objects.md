---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Andra användbara skriptobjekt
description: I den här artikeln beskrivs objekt som innehåller ytterligare skript funktioner i Windows PowerShell ISE.
ms.openlocfilehash: c20daa0045bc07b1f21aafa42a80ce7c47ee7331
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500274"
---
# <a name="other-useful-scripting-objects"></a>Andra användbara skriptobjekt

Följande objekt ger ytterligare skript funktioner i Windows PowerShell ISE. De ingår inte i **$psISE** hierarkin.

## <a name="useful-scripting-objects"></a>Användbara skript objekt

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications

Det finns vissa begränsningar för hur Windows PowerShell ISE interagerar med konsol program. Ett kommando eller ett Automation-skript som kräver åtgärder från användaren kanske inte fungerar på samma sätt som i Windows PowerShell-konsolen. Du kanske vill blockera de här kommandona eller skripten från att köras i Windows PowerShell ISE kommando fönstret. **$PsUnsupportedConsoleApplications** -objektet innehåller en lista över sådana kommandon. Om du försöker köra kommandona i den här listan får du ett meddelande om att de inte stöds. Följande skript lägger till en post i listan.

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a>$psLocalHelp

Detta är ett Dictionary-objekt som upprätthåller en Sammanhangs beroende mappning mellan hjälp ämnen och tillhör ande länkar i den lokala kompilerade HTML-hjälp filen. Den används för att hitta den lokala hjälpen för ett visst ämne. Du kan lägga till eller ta bort ämnen från den här listan. I följande kod exempel visas några exempel på nyckel/värde-par som finns i `$psLocalHelp` .

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```Output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

Följande skript lägger till en post i listan.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

Detta är ett Dictionary-objekt som upprätthåller en Sammanhangs beroende mappning mellan ämnes titlarna i hjälp avsnitten och deras associerade externa URL: er. Den används för att hitta hjälpen för ett visst ämne på webben. Du kan lägga till eller ta bort ämnen från den här listan.

```powershell
$psOnlineHelp | Format-List
```

```Output
Key   : Add-Computer
Value : https://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : https://go.microsoft.com/fwlink/p/?LinkID=113278
```

Följande skript lägger till en post i listan.

```powershell
$psOnlineHelp.Add("get-myNoun", "https://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Se även

[Användningsområden för Windows PowerShell ISE-skriptobjektmodellen](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
