---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Andra användbara skriptobjekt"
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 8334d0b346e59dea3643a93bf52b780b361d1945
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="other-useful-scripting-objects"></a>Andra användbara skriptobjekt
  Följande objekt innehåller ytterligare scripting funktioner i Windows PowerShell ISE. De är inte en del av den **$psISE** hierarki.

## <a name="useful-scripting-objects"></a>Användbar skript-objekt

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications
 Det finns vissa begränsningar för hur Windows PowerShell ISE samverkar med program. Ett kommando eller ett automation-skript som kräver åtgärder från användaren kanske inte fungerar hur det fungerar från Windows PowerShell-konsolen. Du kanske vill blockera dessa kommandon eller skript från att köras i fönstret Windows PowerShell ISE-kommando. Den **$psUnsupportedConsoleApplications** objekt har en lista över dessa kommandon. Om du försöker köra kommandona i den här listan får ett meddelande om att de inte stöds. Följande skript lägger till en post i listan.

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### <a name="pslocalhelp"></a>$psLocalHelp
 Detta är ett katalogobjekt som underhåller en sammanhangsberoende mappning mellan hjälpavsnitt och deras associerade länkar i den lokala kompilerade HTML-hjälpfilen. Den används för att hitta den lokala hjälpen för ett visst ämne. Du kan lägga till eller ta bort ämnen i den här listan. Följande kodexempel visar några exempel nyckel-värdepar som finns i **$psLocalHelp**.

```
# See the local help map
$psLocalHelp | Format-List

```

### <a name="sample-output"></a>Exempel på utdata

|||
|-|-|
|Nyckel: Lägg till dator|Värde: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|Nyckel: Lägga till innehåll|Värde: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

 Följande skript lägger till en post i listan.

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp
 Detta är ett katalogobjekt som underhåller en sammanhangsberoende mappning mellan avsnittet titlarna på hjälpavsnitt och deras associerade externa URL: er. Den används för att hitta hjälp för ett visst ämne på webben. Du kan lägga till eller ta bort ämnen i den här listan.

```
$psOnlineHelp | Format-List

```

### <a name="sample-output"></a>Exempel på utdata

|||
|-|-|
|Nyckel: Lägg till dator|Värde: http://go.microsoft.com/fwlink/p/?LinkID=135194|
|Nyckel: Lägga till innehåll|Värde: http://go.microsoft.com/fwlink/p/?LinkID=113278|

 Följande skript lägger till en post i listan.

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Se även
- [Windows PowerShell ISE Scripting Object Model](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
