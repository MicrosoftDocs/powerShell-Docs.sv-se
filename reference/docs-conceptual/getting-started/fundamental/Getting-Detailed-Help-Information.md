---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Få detaljerad hjälpinformation
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 29c24af3f688f9388893044952442910e793842d
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/25/2018
---
# <a name="getting-detailed-help-information"></a>Få detaljerad hjälpinformation
Windows PowerShell innehåller detaljerade hjälpavsnitt som beskriver begrepp för Windows PowerShell och Windows PowerShell-språk. Det finns även hjälpavsnitt för varje cmdlet och providern och hjälpavsnitt för många funktioner och skript.

Du kan visa de här hjälpavsnitten i Kommandotolken eller visa senast uppdaterade versioner av dessa avsnitt i Microsoft TechNet Library. Många program som är värdar för Windows PowerShell, till exempel Windows PowerShell Integrated Scripting Environment, ange ytterligare hjälp-funktioner, till exempel sammanhangsberoende hjälp och kompilerade hjälpfilen (.chm).

## <a name="getting-help-for-cmdlets"></a>Få hjälp med cmdletar
För att få hjälp om Windows PowerShell-cmdlets kan använda den [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet. Till exempel för att få hjälp med den [Get-ChildItem [m2]](https://technet.microsoft.com/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, skriv:

```
get-help get-childitem
```

eller

```
get-childitem -?
```

Du kan även få hjälp om cmdlet Get-Help. Till exempel:

```
get-help get-help
```

Om du vill hämta en lista över alla skriver cmdlet-hjälpavsnitten i sessionen, du:

```
get-help -category cmdlet
```

Använd för att visa en sida i varje hjälpavsnitt samtidigt i **hjälp** funktion eller dess alias **man**. Skriv till exempel om du vill visa hjälpen för cmdleten Get-ChildItem

```
man get-childitem
```

eller

```
help get-childitem
```

Använd för att visa detaljerad information om en cmdlet-, function- eller skript, inklusive beskrivningar av dess parametrar och exempel på dess användning av *detaljerad* parametern för cmdleten Get-Help. Om du vill hämta detaljerad information om cmdlet Get-ChildItem, exempelvis:

```
get-help get-childitem -detailed
```

Använd för att visa allt innehåll i hjälpavsnittet den *fullständig* parametern för cmdleten Get-Help. Om du vill visa allt innehåll i hjälpavsnittet för cmdleten Get-ChildItem, exempelvis:

```
get-help get-childitem -full
```

Få detaljerad hjälp om parametrarna för en cmdlet, Använd den *parametern* parametern för cmdleten Get-Help. Till exempel få detaljerad hjälp för alla parametrar för cmdleten Get-ChildItem typ:

```
get-help get-childitem -parameter *
```

Använd för att visa endast exemplen i ett hjälpavsnitt den *exempel* parametern för Get-Help. Om du vill visa endast exemplen i hjälpavsnittet för cmdleten Get-ChildItem, exempelvis:

```
get-help get-childitem -examples
```

Information om hur du skriver hjälpavsnitt för de cmdlets som du skriver finns [så att skriva Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) i MSDN library.

## <a name="getting-conceptual-help"></a>Konceptuell hjälp
Cmdleten Get-Help visar även information om konceptuella avsnitt i Windows PowerShell, inklusive information om Windows PowerShell-språk. Konceptuell hjälpavsnitt som börjar med prefixet ”about_”, till exempel about_line_editing. (Namnet på konceptuellt avsnitt måste anges på engelska även på icke-engelska versioner av Windows PowerShell.)

Om du vill visa en lista över grundläggande information skriver du:

```
get-help about_*
```

Om du vill visa ett hjälpavsnitt, skriver du avsnittsnamnet på till exempel:

```
get-help about_command_syntax
```

Parametrarna för Get-Help som *detaljerad*, *parametern*, och *exempel*, har ingen effekt på visning av konceptuella hjälpavsnitt.

## <a name="getting-help-about-providers"></a>Få hjälp om leverantörer
Cmdleten Get-Help visar information om Windows PowerShell-providers. För att få hjälp för en provider, Skriv ”Get-Help” följt av providernamn. Skriv till exempel för att få hjälp för register-provider:

```
get-help registry
```

Om du vill hämta en lista över alla hjälpavsnitt för providern i sessionen, skriver du:

```
get-help -category provider
```

Parametrarna för Get-Help som *detaljerad*, *parametern*, och *exempel*, har ingen effekt på visning av hjälpavsnitt för providern.

## <a name="getting-help-about-scripts-and-functions"></a>Få hjälp om skript och funktioner
Många skript och funktioner i Windows PowerShell har hjälpavsnitt. Använd cmdleten Get-Help om du vill visa hjälpavsnitt för skript och funktioner.

Om du vill visa hjälp för en funktion, Skriv ”get-help” följt av namnet på funktionen. Om du vill få hjälp med funktionen inaktivera PSRemoting, exempelvis:

```
get-help disable-psremoting
```

Visa hjälp för ett skript, skriva den fullständiga sökvägen till skriptfilen. Om skriptet finns på en sökväg som anges i miljövariabeln Path, kan du utelämna sökvägen från kommandot.

Till exempel om du har ett skript som heter ”TestScript.ps1” i din C:\\PS-Test directory vill visa hjälpavsnitt för skriptet, typ:

```
get-help c:\ps-test\TestScript.ps1
```

De parametrar som utformats för att visa cmdlet hjälp som *detaljerad*, *fullständig*, *exempel*, och *parametern*arbetar för skriptet hjälp och funktionen hjälp, för. Men när du visar alla hjälp genom att skriva ”get-help \*”, för funktioner och skript inte visas.

Information om hur du skriver hjälpavsnitt för funktioner och skript finns i [about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/library/7dc08334-dcfe-450b-b949-0554855623af), och [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).

## <a name="getting-help-online"></a>Få hjälp Online
Om du är ansluten till Internet, är ett bra sätt att få hjälp att visa hjälpavsnitt online. Eftersom det är enkelt att uppdatera online avsnitt, är det troligt att ange det mest aktuella innehållet.

För att få hjälp online försök den *Online* parametern för cmdleten Get-Help. Den *Online* parametern för Get-Help cmdleten fungerar endast för cmdlet hjälp fungera hjälp och skript för hjälp. Du kan inte använda den *Online* parameter med konceptuella (om) avsnitt eller hjälpavsnitt för providern. Dessutom eftersom den här funktionen är valfritt, fungerar det inte för varje cmdlet-, function- eller skript hjälpavsnitt.

Men alla hjälpavsnitt som levereras med Windows PowerShell, inklusive providern hjälp och konceptuella (hjälpavsnitt), är tillgänglig online i den [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) avsnitt i Microsoft TechNet Library.

Att använda den *Online* parametern för cmdleten Get-Help använder du följande kommandoformat.

```
get-help <command-name> -online
```

Till exempel för att få onlineversionen av hjälpavsnittet om cmdlet Get-ChildItem, skriver du:

```
get-help get-childitem -online
```

Om det finns en onlineversionen av hjälpavsnittet öppnas i standardwebbläsaren.

Du kan också visa Internet-adress (URL) i hjälpavsnittet om hjälp online har stöd för ett hjälpavsnitt. Internet-adressen visas i avsnittet med länkar i ett hjälpavsnitt.

Till exempel vill se URL: en för online-versionen av cmdlet Add-Computer skriver du:

```
get-help add-computer
```

Den första raden i avsnittet länkarna i avsnittet visas nedan.

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

Information om hur du ska ge support online för dina hjälpavsnitt finns [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), och se [så att skriva Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) i MSDN library.

## <a name="see-also"></a>Se även
- [about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105)
- [about_Scripts](https://technet.microsoft.com/library/7dc08334-dcfe-450b-b949-0554855623af)
- [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)