---
ms.date: 08/27/2018
keywords: PowerShell, cmdlet
title: Få detaljerad hjälpinformation
ms.openlocfilehash: e722eb8a0ca13e3d2de864314775a0a9fa578390
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417656"
---
# <a name="getting-detailed-help-information"></a>Få detaljerad hjälpinformation

PowerShell innehåller detaljerade hjälp artiklar som förklarar PowerShell-koncept och PowerShell-språket. Det finns också hjälp artiklar för varje cmdlet och Provider och för många funktioner och skript.

Du kan visa dessa hjälp artiklar i kommando tolken eller Visa de senaste uppdaterade versionerna av de här artiklarna i [PowerShell](/powershell/scripting/overview) -dokumentationen online.

## <a name="getting-help-for-cmdlets"></a>Få hjälp med cmdletar

Använd cmdleten [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) för att få hjälp om PowerShell-cmdlets. Om du till exempel vill få hjälp med `Get-ChildItem`-cmdlet skriver du:

```powershell
Get-Help Get-ChildItem
```

eller

```powershell
Get-ChildItem -?
```

Du kan även få hjälp med cmdleten Get-Help. Till exempel:

```powershell
Get-Help Get-Help
```

Om du vill hämta en lista över alla hjälp artiklar för cmdlet i sessionen skriver du:

```powershell
Get-Help -Category Cmdlet
```

Om du vill visa en sida i varje hjälp artikel i taget använder du funktionen `help` eller dess alias `man`.
Om du till exempel vill visa hjälp för `Get-ChildItem`-cmdlet skriver du

```powershell
man Get-ChildItem
```

eller

```powershell
help Get-ChildItem
```

Om du vill visa detaljerad information använder du den **detaljerade** parametern i `Get-Help`-cmdleten. Om du till exempel vill få detaljerad information om `Get-ChildItem`-cmdlet skriver du:

```powershell
Get-Help Get-ChildItem -Detailed
```

Om du vill visa allt innehåll i hjälp artikeln använder du parametern **fullständig** i `Get-Help`-cmdleten. Om du till exempel vill visa allt innehåll i hjälp artikeln för cmdleten `Get-ChildItem` skriver du:

```powershell
Get-Help Get-ChildItem -Full
```

Om du vill ha mer information om parametrarna för en cmdlet använder du **parametern** parameter i `Get-Help`-cmdleten. Om du till exempel vill få detaljerad hjälp för alla parametrar i `Get-ChildItem`-cmdleten skriver du:

```powershell
Get-Help Get-ChildItem -Parameter *
```

Om du bara vill visa exemplen i en hjälp artikel använder du parametern **exempel** för `Get-Help`.
Om du till exempel vill visa bara exemplen i hjälp artikeln för cmdleten `Get-ChildItem` skriver du:

```powershell
Get-Help Get-ChildItem -Examples
```

Information om hur du skriver hjälp artiklar för de cmdlet: ar som du skriver in finns i [så här skriver du cmdlet-hjälpen](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).

## <a name="getting-conceptual-help"></a>Få konceptuell hjälp

`Get-Help`-cmdleten visar också information om konceptuella artiklar i PowerShell, inklusive artiklar om PowerShell-språket. Konceptuell hjälp artiklar börjar med prefixet "about_", till exempel about_line_editing. (Namnet på den konceptuella artikeln måste anges på engelska även på icke-engelska versioner av PowerShell.)

Om du vill visa en lista med konceptuella artiklar skriver du:

```powershell
Get-Help about_*
```

Om du vill visa en viss hjälp artikel skriver du artikel namnet, till exempel:

```powershell
Get-Help about_command_syntax
```

Parametrarna för `Get-Help`, till exempel **detaljerade** **parametrar och** **exempel**, har ingen påverkan på visningen av konceptuella hjälp artiklar.

## <a name="getting-help-about-providers"></a>Få hjälp om leverantörer

`Get-Help`-cmdlet visar information om PowerShell-leverantörer. Om du vill ha hjälp med en provider skriver du `Get-Help` följt av namnet på providern. Om du till exempel vill få hjälp med register leverantören skriver du:

```powershell
Get-Help registry
```

Om du vill hämta en lista över alla hjälp artiklar om providern i din session skriver du

```powershell
Get-Help -Category provider
```

Parametrarna för `Get-Help`, till exempel **detaljerade** **parametrar och** **exempel**, har ingen påverkan på visningen av leverantörs hjälp artiklar.

## <a name="getting-help-about-scripts-and-functions"></a>Få hjälp om skript och funktioner

Många skript och funktioner i PowerShell har hjälp artiklar. Använd `Get-Help`-cmdleten för att visa hjälp artiklarna för skript och funktioner.

Om du vill visa hjälpen för en funktion skriver du `Get-Help` följt av funktions namnet. Om du till exempel vill få hjälp med funktionen `Disable-PSRemoting` skriver du:

```powershell
Get-Help Disable-PSRemoting
```

Om du vill visa hjälpen för ett skript anger du sökvägen till skript filen. Om skriptet inte finns i en sökväg som anges i miljövariabeln PATH måste du använda den fullständigt kvalificerade sökvägen.

Om du till exempel har ett skript som heter "TestScript. ps1" i mappen C:\\PS-test för att visa hjälp artikeln för skriptet, skriver du:

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

De parametrar som är utformade för att Visa cmdlet-hjälp fungerar även för skript-och funktions hjälp. Hjälp för funktioner och skript visas dock inte när du kör `Get-Help *`.

Information om hur du skriver hjälp artiklar för dina funktioner och skript finns i följande artiklar:

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a>Få hjälp online

Visa hjälp artiklar online är ett av de bästa sätten att få hjälp. Online-artiklar är enklare att uppdatera och tillhandahålla det mest aktuella innehållet.

Om du vill få hjälp online använder du parametern **online** i `Get-Help`-cmdleten. Alla hjälp artiklar som ingår i PowerShell, inklusive leverantörs hjälp och begreppsmässig (om) hjälp artiklar finns tillgängliga online i [PowerShell](/powershell/scripting/powershell-scripting) -dokumentationen.

> [!NOTE]
> Du kan inte använda parametern **online** med konceptuell (about_\*) eller leverantören hjälp artiklar.
> Direkt hjälpen är valfri, så den fungerar inte för varje cmdlet, funktion eller skript.

Om du till exempel vill hämta online-versionen av hjälp-artikeln om `Get-ChildItem`-cmdlet skriver du:

```powershell
Get-Help Get-ChildItem -Online
```

PowerShell öppnar artikeln i standard webbläsaren. Om onlinehjälpen stöds för en hjälp artikel kan du också Visa webb adressen till hjälp artikeln. URL: en visas i avsnittet relaterade länkar i en hjälp artikel.

Om du till exempel vill visa URL: en för online-versionen av cmdleten Add-Computer skriver du:

```powershell
Get-Help Add-Computer
```

Den första raden i avsnittet relaterade länkar i artikeln visas nedan.

```Output
Online version: https://go.microsoft.com/fwlink/?LinkId=821564
```

Information om hur du tillhandahåller onlinesupport för dina hjälp artiklar finns [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

## <a name="see-also"></a>Se även

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [Get – hjälp](/powershell/module/microsoft.powershell.core/get-help)
