---
description: Beskriver det attribut som gör att en funktion fungerar som en kompilerad cmdlet.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_CmdletBindingAttribute
ms.openlocfilehash: eb6e161fd03898fe420103c04b26c0f6249be590
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271731"
---
# <a name="about-functions-cmdletbindingattribute"></a>Om functions-CmdletBindingAttribute

## <a name="short-description"></a>Kort beskrivning
Beskriver det attribut som gör att en funktion fungerar som en kompilerad cmdlet.

## <a name="long-description"></a>Lång beskrivning

`CmdletBinding`Attributet är ett attribut med funktioner som gör att de fungerar som kompilerade cmdlets skrivna i C#. Den ger åtkomst till funktionerna i-cmdletar.

PowerShell binder parametrarna för funktioner som har `CmdletBinding` attributet på samma sätt som de binder parametrarna för kompilerade cmdlets. Den `$PSCmdlet` automatiska variabeln är tillgänglig för functions med `CmdletBinding` attributet, men `$Args` variabeln är inte tillgänglig.

I funktioner som har `CmdletBinding` attributet, okända parametrar och positions argument som inte har några matchande positions parametrar, orsakar parameter bindningen fel.

> [!NOTE]
> Kompilerade cmdletar använder `Cmdlet` attributet som krävs, vilket liknar det `CmdletBinding` attribut som beskrivs i det här avsnittet.

## <a name="syntax"></a>Syntax

I följande exempel visas formatet för en funktion som anger alla valfria argument för `CmdletBinding` attributet. En kort beskrivning av varje argument följer det här exemplet.

```powershell
{
    [CmdletBinding(ConfirmImpact=<String>,
    DefaultParameterSetName=<String>,
    HelpURI=<URI>,
    SupportsPaging=<Boolean>,
    SupportsShouldProcess=<Boolean>,
    PositionalBinding=<Boolean>)]

    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

## <a name="confirmimpact"></a>ConfirmImpact

Argumentet **ConfirmImpact** anger när funktions åtgärden ska bekräftas av ett anrop till **ShouldProcess** -metoden. Anropet till **ShouldProcess** -metoden visar bara en bekräftelse när argumentet **ConfirmImpact** är lika med eller större än värdet för `$ConfirmPreference` variabeln Preference. (Standardvärdet för argumentet är **medium**.) Ange bara det här argumentet om argumentet **SupportsShouldProcess** också anges.

Mer information om bekräftelse begär Anden finns i [begära bekräftelse](/powershell/scripting/developer/cmdlet/requesting-confirmation).

## <a name="defaultparametersetname"></a>DefaultParameterSetName

Argumentet **DefaultParameterSetName** anger namnet på den parameter uppsättning som PowerShell ska försöka använda när det inte går att avgöra vilken parameter som ska användas. Du kan undvika det här problemet genom att göra den unika parametern för varje parameter inställd på en obligatorisk parameter.

## <a name="helpuri"></a>HelpURI

Argumentet **HelpURI** anger Internet adressen till onlineversionen av hjälp avsnittet som beskriver funktionen. Värdet för argumentet **HelpURI** måste börja med http eller https.

Värdet för argumentet **HelpURI** används för värdet för egenskapen **HelpURI** för **CommandInfo** -objektet som `Get-Command` returneras för funktionen.

Men när hjälpfiler installeras på datorn och värdet för den första länken i **RelatedLinks** -avsnittet i Hjälp filen är en URI, eller värdet för det första `.Link` direktivet i den kommenterade hjälpen är en URI, används URI: n i Hjälp filen som värde för egenskapen **HelpUri** för funktionen.

`Get-Help`Cmdlet: en använder värdet för egenskapen **HelpURI** för att hitta online-versionen av funktions hjälp avsnittet när du har angett en **online** -parameter `Get-Help` i ett kommando.

## <a name="supportspaging"></a>SupportsPaging

Argumentet **SupportsPaging** lägger till de **första** , **Skip** -och **IncludeTotalCount** -parametrarna i funktionen. Med de här parametrarna kan användarna välja utdata från en mycket stor resultat uppsättning. Det här argumentet är utformat för cmdlets och Functions som returnerar data från stora data lager som har stöd för data urval, till exempel en SQL-databas.

Det här argumentet introducerades i Windows PowerShell 3,0.

- **Första** : endast de första n-objekten hämtas.
- **Skip** : ignorerar de första n-objekten och hämtar sedan de återstående objekten.
- **IncludeTotalCount** : rapporterar antalet objekt i data uppsättningen (ett heltal) följt av objekten. Om cmdleten inte kan avgöra det totala antalet returneras "okänt antal".

PowerShell innehåller **NewTotalCount** , en hjälp metod som hämtar det totala Count-värdet för att returnera och innehåller en uppskattning av precisionen för det totala Count-värdet.

Följande exempel funktion visar hur du lägger till stöd för växlings parametrarna i en avancerad funktion.

```powershell
function Get-Numbers {
    [CmdletBinding(SupportsPaging = $true)]
    param()

    $FirstNumber = [Math]::Min($PSCmdlet.PagingParameters.Skip, 100)
    $LastNumber = [Math]::Min($PSCmdlet.PagingParameters.First +
      $FirstNumber - 1, 100)

    if ($PSCmdlet.PagingParameters.IncludeTotalCount) {
        $TotalCountAccuracy = 1.0
        $TotalCount = $PSCmdlet.PagingParameters.NewTotalCount(100,
          $TotalCountAccuracy)
        Write-Output $TotalCount
    }
    $FirstNumber .. $LastNumber | Write-Output
}
```

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

Argumentet **SupportsShouldProcess** lägger till **Confirm** -och **whatIf** -parametrar i funktionen. Parametern **Confirm** efterfrågar användaren innan kommandot körs på varje objekt i pipelinen. Parametern **whatIf** listar de ändringar som kommandot gör, i stället för att köra kommandot.

## <a name="positionalbinding"></a>PositionalBinding

Argumentet **PositionalBinding** avgör om parametrar i funktionen är placerade som standard. Standardvärdet är `$True`. Du kan använda argumentet **PositionalBinding** med värdet för `$False` att inaktivera positions bindning.

**PositionalBinding** -argumentet introduceras i Windows PowerShell 3,0.

Parameter namnet är valfritt när parametrarna är placerade.
PowerShell associerar parameter värden utan namn med funktions parametrarna enligt ordningen eller positionen för de värden som inte är namngivna i funktions kommandot.

När parametrar inte är positionerade (de är "namngivna"), krävs parameter namnet (eller en förkortning eller ett alias för namnet) i kommandot.

När **PositionalBinding** är är `$True` funktions parametrarna placerade som standard. PowerShell tilldelar parametrarna positions nummer till parametrarna i den ordning som de deklareras i funktionen.

När **PositionalBinding** är `$False` funktions parametrar placeras de inte som standard. Om inte **positions** argumentet för attributet **parameter** deklareras i parametern, måste parameter namnet (eller ett alias eller en förkortning) inkluderas när parametern används i en funktion.

**Positions** argumentet för attributet **parameter** har företräde framför **PositionalBinding** -standardvärdet. Du kan använda argumentet **position** för att ange ett positions värde för en parameter. Mer information om **positions** argumentet finns [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).

## <a name="notes"></a>Kommentarer

**SupportsTransactions** -argumentet stöds inte i avancerade funktioner.

## <a name="keywords"></a>Nyckelord

about_Functions_CmdletBinding_Attribute

## <a name="see-also"></a>Se även

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
