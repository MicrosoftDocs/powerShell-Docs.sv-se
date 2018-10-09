---
ms.date: 08/27/2018
keywords: PowerShell cmdlet
title: Få detaljerad hjälpinformation
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: d2578604ec7c01c0b2734bd180e1babaca58b153
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851280"
---
# <a name="getting-detailed-help-information"></a>Få detaljerad hjälpinformation

PowerShell innehåller detaljerade hjälpartiklar som förklarar PowerShell-koncept och PowerShell-språket. Det finns även hjälpartiklar för varje cmdlet och providern och för många funktioner och skript.

Du kan visa dessa hjälpartiklar i Kommandotolken eller visa den senast uppdaterade versioner av de här artiklarna i den [PowerShell](/powershell/scripting/powershell-scripting) dokumentationen online.

## <a name="getting-help-for-cmdlets"></a>Få hjälp om cmdlet: ar

Om du behöver hjälp om PowerShell-cmdletar, använda den [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet. Till exempel för att få hjälp med den `Get-ChildItem` cmdlet, typ:

```powershell
Get-Help Get-ChildItem
```

eller

```powershell
Get-ChildItem -?
```

Du kan även få hjälp om cmdleten Get-Help. Till exempel:

```powershell
Get-Help Get-Help
```

Om du vill hämta en lista över alla cmdlet hjälpartiklar i sessionen, skriver du:

```powershell
Get-Help -Category Cmdlet
```

Använd för att visa en sida med varje hjälpartikeln i taget, den `help` funktion eller dess alias `man`.
Till exempel vill visa hjälp för den `Get-ChildItem` cmdlet, typ

```powershell
man Get-ChildItem
```

eller

```powershell
help Get-ChildItem
```

Använd för att visa detaljerad information i **detaljerat** -parametern för den `Get-Help` cmdlet. Till exempel för att få detaljerad information den `Get-ChildItem` cmdlet, typ:

```powershell
Get-Help Get-ChildItem -Detailed
```

Använd för att visa allt innehåll i hjälpartikeln den **fullständig** -parametern för den `Get-Help` cmdlet. Till exempel för att visa allt innehåll i hjälpartikeln för den `Get-ChildItem` cmdlet, typ:

```powershell
Get-Help Get-ChildItem -Full
```

Få ytterligare hjälp om parametrarna för en cmdlet, Använd den **parametern** -parametern för den `Get-Help` cmdlet. Till exempel utförlig information för alla parametrar för att hämta den `Get-ChildItem` cmdlet, typ:

```powershell
Get-Help Get-ChildItem -Parameter *
```

Använd för att visa endast i exemplen i en hjälpartikeln den **exempel** -parametern för den `Get-Help`.
Till exempel för att visa endast i exemplen i hjälpartikeln för den `Get-ChildItem `cmdlet, typ:

```powershell
Get-Help Get-ChildItem -Examples
```

Information om hur du skriver hjälpartiklar för de cmdletar som du skriver finns i [hur du skriver hjälp för cmdleten](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).

## <a name="getting-conceptual-help"></a>Konceptuell hjälp

Den `Get-Help` cmdleten visar också information om konceptuella artiklar i PowerShell, bland annat artiklar om PowerShell-språket. Konceptuell hjälp artiklar som börjar med prefixet ”about_”, till exempel about_line_editing. (Namnet på den konceptuella artikeln måste anges på engelska även på icke-engelska versioner av PowerShell.)

Om du vill visa en lista över konceptuella artiklar, skriver du:

```powershell
Get-Help about_*
```

Om du vill visa en viss hjälpartikeln, skriver du artikelnamnet på till exempel:

```powershell
Get-Help about_command_syntax
```

Parametrarna för `Get-Help`, till exempel **detaljerat**, **parametern**, och **exempel**, har ingen effekt på visning av konceptuell hjälpartiklar.

## <a name="getting-help-about-providers"></a>Få hjälp om leverantörer

Den `Get-Help` cmdlet visar information om PowerShell-leverantörer. Om du vill få hjälp med en provider, skriver `Get-Help` följt av providernamn. Till exempel om du behöver hjälp för register-provider, skriver du:

```powershell
Get-Help registry
```

Om du vill hämta en lista över alla providern hjälpartiklar i sessionen, skriver du:

```powershell
Get-Help -Category provider
```

Parametrarna för `Get-Help`, till exempel **detaljerat**, **parametern**, och **exempel**, har ingen effekt på visning av providern hjälpartiklar.

## <a name="getting-help-about-scripts-and-functions"></a>Få hjälp om skript och funktioner

Många skript och funktioner i PowerShell har hjälpartiklar. Använd den `Get-Help` cmdleten för att visa hjälpartiklar för skript och funktioner.

Om du vill visa hjälpen för en funktion, skriver `Get-Help` följt av namnet på funktionen. Till exempel för att få hjälp med den `Disable-PSRemoting` skriver:

```powershell
Get-Help Disable-PSRemoting
```

Om du vill visa hjälp för ett skript, ange sökvägen till skriptfilen. Om skriptet inte är i en sökväg som anges i miljövariabeln Path måste du använda den fullständiga sökvägen.

Exempel: Om du har ett skript som heter ”TestScript.ps1” i din C:\\PS-Test directory för att visa hjälpartikeln för skriptet, typ:

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

De parametrar som är utformade för att visa cmdlet Help arbete för skriptet och funktionen hjälper för. Hjälp för funktioner och skript är dock inte visas när du kör `Get-Help *`.

Information om hur du skriver hjälpartiklar för dina funktioner och skript finns i följande artiklar:

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a>Få hjälp online

Visa hjälpartiklar online är en av de bästa sätten att få hjälp. Online artiklar är lättare att uppdatera och ger det mest aktuella innehållet.

Om du vill få hjälp online, använda den **Online** -parametern för den `Get-Help` cmdlet. Alla hjälpartiklar som levereras med PowerShell, inklusive providern hjälp och konceptuella (om) hjälpartiklar, är tillgängliga online i den [PowerShell](/powershell/scripting/powershell-scripting) dokumentation.

> [!NOTE]
> Du kan inte använda den **Online** parameter med konceptuella (about_\*) eller hjälpartiklar för providern.
> Onlinehjälp är valfritt, så inte fungerar för varje cmdlet, en funktion eller ett skript.

Till exempel för att få onlineversionen av hjälpavsnittet om den `Get-ChildItem` cmdlet, typ:

```powershell
Get-Help Get-ChildItem -Online
```

PowerShell öppnas artikeln i din standardwebbläsare. Du kan också visa Webbadressen till hjälpartikeln om onlinehjälp stöds för en hjälpartikeln. Webbadressen visas i avsnittet med länkar i en hjälpartikeln.

Till exempel om du vill se URL-Adressen för online-versionen av cmdleten Lägg till dator skriver du:

```powershell
Get-Help Add-Computer
```

Den första raden i avsnittet med länkar i artikeln visas nedan.

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

Information om hur du ger online support för dina hjälpartiklar finns i [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

## <a name="see-also"></a>Se även

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [Get-Help](/powershell/module/microsoft.powershell.core/get-help)
