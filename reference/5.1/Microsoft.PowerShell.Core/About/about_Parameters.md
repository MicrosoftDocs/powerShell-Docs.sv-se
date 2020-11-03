---
description: Beskriver hur du arbetar med kommando parametrar i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 02/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters
ms.openlocfilehash: 7cc5c071116df8d3326a4ea13802227d350bfac3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272060"
---
# <a name="about-parameters"></a>Om parametrar

## <a name="short-description"></a>Kort beskrivning
Beskriver hur du arbetar med kommando parametrar i PowerShell.

## <a name="long-description"></a>Lång beskrivning

De flesta PowerShell-kommandon, till exempel cmdlets, Functions och scripts, förlitar sig på parametrar för att tillåta användare att välja alternativ eller ange information. Parametrarna följer kommando namnet och har följande format:

```
-<parameter_name> <parameter_value>
-<parameter_name>:<parameter_value>
```

Namnet på parametern föregås av ett bindestreck (-), som signalerar till PowerShell att ordet efter bindestrecket är ett parameter namn. Parameter namnet och värdet kan avgränsas med ett blank steg eller ett kolon. Vissa parametrar kräver inte eller accepterar inte ett parameter värde. Andra parametrar kräver ett värde, men kräver inte parameter namnet i kommandot.

Typ av parametrar och kraven för dessa parametrar varierar. Använd cmdleten för att hitta information om parametrarna för ett kommando `Get-Help` . Om du till exempel vill hitta information om parametrarna för `Get-ChildItem` cmdleten skriver du:

```powershell
Get-Help Get-ChildItem
```

Om du vill hitta information om parametrarna för ett skript använder du den fullständiga sökvägen till skript filen. Ett exempel:

```powershell
Get-Help $home\Documents\Scripts\Get-Function.ps1
```

`Get-Help`Cmdleten returnerar olika uppgifter om kommandot, inklusive en beskrivning, kommandosyntaxen, information om parametrarna och exempel som visar hur du använder parametrarna i ett kommando.

Du kan också använda parametern parameter för `Get-Help` cmdlet: en för att hitta information om en viss parameter. Eller så kan du använda **parameter** parametern med värdet jokertecken ( `*` ) för att hitta information om alla parametrar för kommandot. Följande kommando hämtar till exempel information om alla parametrar för `Get-Member` cmdleten:

```powershell
Get-Help Get-Member -Parameter *
```

### <a name="default-parameter-values"></a>Standard parameter värden

Valfria parametrar har ett standardvärde, vilket är det värde som används eller antas när parametern inte anges i kommandot.

Standardvärdet för parametern **computername** för många cmdletar är till exempel namnet på den lokala datorn. Därför används namnet på den lokala datorn i kommandot om inte parametern **computername** anges.

Du hittar standardvärdet för parametern i hjälp avsnittet för cmdleten. Parameter beskrivningen ska innehålla standardvärdet.

Du kan också ange ett anpassat standardvärde för vilken parameter som helst av en cmdlet eller en avancerad funktion. Information om hur du ställer in anpassade standardvärden finns [about_Parameters_Default_Values](about_Parameters_Default_Values.md).

### <a name="parameter-attribute-table"></a>Parameter egenskaps tabell

När du använder parametrarna **fullständig** , **parameter** eller **online** i `Get-Help` cmdleten, `Get-Help` visar en tabell med parameter-attribut med detaljerad information om parametern.

Den här informationen innehåller information som du behöver känna till när du använder-parametern.
Till exempel innehåller hjälp avsnittet för `Get-ChildItem` cmdleten följande information om dess Sök vägs parameter:

```
-path <string[]>
    Specifies a path of one or more locations. Wildcard characters are
    permitted. The default location is the current directory (.).

Required?                    false
Position?                    0
Default value                Current directory
Accept pipeline input?       true (ByValue, ByPropertyName)
Accept wildcard characters?  true
```

Parameter informationen innehåller parameter-syntaxen, en beskrivning av parametern och attributen för parametern. I följande avsnitt beskrivs attributen för parametern.

#### <a name="parameter-required"></a>Parameter krävs

Den här inställningen anger om parametern är obligatorisk, det vill säga om alla kommandon som använder denna cmdlet måste innehålla denna parameter. När värdet är **True** och parametern saknas i kommandot, uppmanas du att ange ett värde för parametern i PowerShell.

#### <a name="parameter-position"></a>Parameter position

Om `Position` inställningen har angetts till ett positivt heltal, krävs inte parameter namnet. Den här typen av parameter kallas för en positions parameter och siffran anger den position där parametern måste visas i förhållande till andra positions parametrar. En namngiven parameter kan anges i valfri position efter cmdlet-namnet. Om du inkluderar parameter namnet för en positions parameter, kan parametern anges i valfri position efter cmdlet-namnet.

Till exempel `Get-ChildItem` har cmdleten sökväg och exkludera parametrar. `Position`Inställningen för **sökväg** är **0** , vilket innebär att den är en positions parameter. `Position`Inställningen för **exclude** kallas **named**.

Det innebär att **sökvägen** inte kräver parameter namnet, men dess parameter värde måste vara det första eller enda parameter värde som inte är namn i kommandot.
Men eftersom parametern exclude är en namngiven parameter, kan du placera den i valfri position i kommandot.

Som ett resultat av `Position` inställningarna för dessa två parametrar kan du använda något av följande kommandon:

```powershell
Get-ChildItem -Path c:\techdocs -Exclude *.ppt
Get-ChildItem c:\techdocs -Exclude *.ppt
Get-ChildItem -Exclude *.ppt -Path c:\techdocs
Get-ChildItem -Exclude *.ppt c:\techdocs
```

Om du vill inkludera en annan positions parameter utan att inkludera parameter namnet, måste den parametern placeras i den ordning som anges av `Position` inställningen.

#### <a name="parameter-type"></a>Parameter typ

Den här inställningen anger parameter värdets Microsoft .NET Framework-typ. Om typen till exempel är **Int32** , måste parametervärdet vara ett heltal. Om typen är sträng måste parametervärdet vara en tecken sträng. Om strängen innehåller blank steg måste värdet stå inom citat tecken, eller så måste blank stegen föregås av Escape-tecknet (").

#### <a name="default-value"></a>Standardvärde

Den här inställningen anger värdet som parametern kommer att anta om inget annat värde anges. Till exempel är standardvärdet för Sök vägs parametern ofta den aktuella katalogen. De obligatoriska parametrarna har aldrig ett standardvärde.
För många valfria parametrar finns det inget standardvärde eftersom parametern inte har någon inverkan om den inte används.

#### <a name="accepts-multiple-values"></a>Accepterar flera värden

Den här inställningen anger om en parameter accepterar flera parameter värden.
När en parameter accepterar flera värden kan du skriva en kommaavgränsad lista som värde för parametern i kommandot eller spara en kommaavgränsad lista (en matris) i en variabel och sedan ange variabeln som parameter värde.

Till exempel accepterar ServiceName-parametern för `Get-Service` cmdleten flera värden. Följande kommandon är både giltiga:

```powershell
Get-Service -servicename winrm, netlogon
```

```powershell
$s = "winrm", "netlogon"
Get-Service -servicename $s
```

#### <a name="accepts-pipeline-input"></a>Accepterar inmatade pipelines

Den här inställningen anger om du kan använda pipeline-operatorn ( `|` ) för att skicka ett värde till parametern.

```
Value                    Description
-----                    -----------
False                    Indicates that you cannot pipe a value to the
                         parameter.

True (by Value)          Indicates that you can pipe any value to the
                         parameter, just so the value has the .NET
                         Framework type specified for the parameter or the
                         value can be converted to the specified .NET
                         Framework type.
```

När en parameter är "sant (efter värde)" försöker PowerShell associera alla skickas-värden med den parametern innan den försöker med andra metoder för att tolka kommandot.

```
True (by Property Name)  Indicates that you can pipe a value to the
                         parameter, but the .NET Framework type of the
                         parameter must include a property with the same
                         name as the parameter.
```

Du kan till exempel skicka ett värde till en **namn** parameter endast när värdet har en egenskap som heter **Name**.

> [!NOTE]
> En typ parameter som godkänner pipeline-inmatare ( `by Value` ) eller ( `by PropertyName` ) aktiverar användning av skript blocken **Delay-bind** i parametern.
>
> Skript blocket **Delay-bind** körs automatiskt under **ParameterBinding**. Resultatet är kopplat till parametern. Fördröjd bindning fungerar **inte** för parametrar som har definierats som typ `ScriptBlock` eller `System.Object` , skript blocket skickas genom **utan** att anropas.
>
> Du kan läsa mer om **fördröjning – binda** skript block här [about_Script_Blocks. MD](about_Script_Blocks.md)

#### <a name="accepts-wildcard-characters"></a>Accepterar jokertecken

Den här inställningen anger om parameterns värde kan innehålla jokertecken så att parametervärdet kan matchas mot fler än ett befintligt objekt i mål behållaren.

#### <a name="common-parameters"></a>Vanliga parametrar

Vanliga parametrar är parametrar som du kan använda med valfri cmdlet. Mer information om vanliga parametrar finns [about_CommonParameters](about_CommonParameters.md).

## <a name="see-also"></a>Se även

[about_Command_syntax](about_Command_syntax.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Parameters_Default_Values](about_Parameters_Default_Values.md)

[about_Pipelines](about_Pipelines.md)

[about_Wildcards](about_Wildcards.md)
