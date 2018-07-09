---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Andra användbara skriptobjekt
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 2ae9bc1864daedbcb0070c5f3862a6c98f8db2d4
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893288"
---
# <a name="other-useful-scripting-objects"></a>Andra användbara skriptobjekt

Följande objekt innehåller ytterligare skript funktioner i Windows PowerShell ISE. De är inte en del av den **$psISE** hierarki.

## <a name="useful-scripting-objects"></a>Användbara skript-objekt

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications

Det finns vissa begränsningar för hur Windows PowerShell ISE interagerar med konsolprogram. Ett kommando eller ett skript för automatisering som kräver åtgärder från användaren kanske inte fungerar hur det fungerar från Windows PowerShell-konsolen. Du kanske vill blockera dessa kommandon eller skript från att köras i fönstret Windows PowerShell ISE-kommando. Den **$psUnsupportedConsoleApplications** objektet ser till att en lista över dessa kommandon. Om du försöker köra kommandon i den här listan, får du ett meddelande om att de inte stöds. Följande skript läggs en post i listan.

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a>$psLocalHelp

Det här är ett katalogobjekt som upprätthåller en sammanhangsberoende mappning mellan hjälpavsnitt och deras associerade länkar i den lokala kompilerade HTML-hjälpfilen. Den används för att hitta lokal hjälp för ett visst ämne. Du kan lägga till eller ta bort ämnen från den här listan. I följande kodexempel visas några exempel nyckel / värde-par som finns i `$psLocalHelp`.

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="pslocalhelp-sample-output"></a>$psLocalHelp exempel på utdata

|||
|-|-|
|Nyckel: Lägg-dator|Värde: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|Nyckel: Lägga till innehåll|Värde: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

Följande skript läggs en post i listan.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

Det här är ett katalogobjekt som upprätthåller en sammanhangsberoende mappning mellan avsnittet titlarna på hjälpavsnitt och deras associerade externa URL: er. Den används för att hitta hjälp för ett visst ämne på webben. Du kan lägga till eller ta bort ämnen från den här listan.

```powershell
$psOnlineHelp | Format-List
```

## <a name="psonilnehelp-sample-output"></a>$psOnilneHelp exempel på utdata

|||
|-|-|
|Nyckel: Lägg-dator|Värde: http://go.microsoft.com/fwlink/p/?LinkID=135194|
|Nyckel: Lägga till innehåll|Värde: http://go.microsoft.com/fwlink/p/?LinkID=113278|

Följande skript läggs en post i listan.

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Se även

[Syftet med den Windows PowerShell ISE-Skriptobjektmodellen](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)