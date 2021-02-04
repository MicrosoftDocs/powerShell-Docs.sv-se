---
description: Förklarar data avsnitt, som isolerar text strängar och andra skrivskyddade data från skript logik.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_data_sections?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Data_Sections
ms.openlocfilehash: bf86d8aeec1094205ace1a64fdf584f5be000313
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879226"
---
# <a name="about-data-sections"></a>Om data avsnitt

## <a name="short-description"></a>Kort beskrivning
Förklarar data avsnitt, som isolerar text strängar och andra skrivskyddade data från skript logik.

## <a name="long-description"></a>Lång beskrivning

Skript som har utformats för PowerShell kan ha ett eller flera data avsnitt som bara innehåller data. Du kan inkludera ett eller flera data avsnitt i valfritt skript, funktion eller avancerad funktion. Innehållet i data avsnittet är begränsat till en angiven delmängd av PowerShell-skript språket.

Genom att skilja data från kod logiken blir det enklare att identifiera och hantera både logik och data. Det gör att du kan ha separata String-resursfiler för text, till exempel fel meddelanden och hjälp strängar. Den isolerar också kod logiken som underlättar säkerhets-och verifieringstester.

I PowerShell används data avsnittet för att stödja skript internationalisering.
Du kan använda data avsnitt för att göra det enklare att isolera, leta upp och bearbeta strängar som kommer att översättas till flera användar gränssnitts språk.

Data avsnittet är en PowerShell 2,0-funktion. Skript med data avsnitt kommer inte att köras i PowerShell 1,0 utan revidering.

### <a name="syntax"></a>Syntax

Syntaxen för ett data avsnitt är följande:

```
DATA [<variable-name>] [-supportedCommand <cmdlet-name>] {
    <Permitted content>
}
```

Nyckelordet data krävs. Det är inte Skift läges känsligt. Det tillåtna innehållet är begränsat till följande element:

- Alla PowerShell-operatorer, förutom `-match`
- `If`-, `Else` -och- `ElseIf` uttryck
- Följande automatiska variabler: `$PsCulture` , `$PsUICulture` ,, `$True` `$False` och `$Null`
- Kommentarer
- Pipelines
- Instruktioner avgränsade med semikolon ( `;` )
- Litteraler, till exempel följande:

  ```powershell
  a
  1
  1,2,3
  "PowerShell 2.0"
  @( "red", "green", "blue" )
  @{ a = 0x1; b = "great"; c ="script" }
  [XML] @'
  <p> Hello, World </p>
  '@
  ```

- Cmdletar som är tillåtna i ett data avsnitt. Som standard `ConvertFrom-StringData` tillåts bara cmdleten.
- -Cmdletar som du tillåter i ett data avsnitt med hjälp av- `-SupportedCommand` parametern.

När du använder `ConvertFrom-StringData` cmdleten i ett data avsnitt kan du ange nyckel/värde-par i ensamt citat tecken eller strängar med dubbla citat tecken eller med en eller två citat tecken som anges här – strängar. Strängar som innehåller variabler och under uttryck måste vara inneslutna i enciterade strängar eller i enciterade här – strängar så att variablerna inte expanderas och under uttryck inte är körbara.

### <a name="-supportedcommand"></a>-SupportedCommand

Med `-SupportedCommand` parametern kan du ange att en cmdlet eller funktion bara genererar data. Det är utformat för att tillåta användare att inkludera cmdlets och funktioner i ett data avsnitt som de har skrivit eller testat.

Värdet för `-SupportedCommand` är en kommaavgränsad lista med en eller flera cmdlet-eller funktions namn.

Följande data avsnitt innehåller till exempel en användardefinierad cmdlet, `Format-Xml` som formaterar data i en XML-fil:

```powershell
DATA -supportedCommand Format-Xml
{
    Format-Xml -Strings string1, string2, string3
}
```

### <a name="using-a-data-section"></a>Använda ett data avsnitt

Om du vill använda innehållet i ett data avsnitt, tilldelar du det till en variabel och använder variabel notation för att komma åt innehållet.

Följande data avsnitt innehåller till exempel ett `ConvertFrom-StringData` kommando som konverterar denna-sträng till en hash-tabell. Hash-tabellen är tilldelad `$TextMsgs` variabeln.

`$TextMsgs`Variabeln är inte en del av data avsnittet.

```powershell
$TextMsgs = DATA {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

Använd följande kommandon för att komma åt nycklar och värden i hash-tabellen i `$TextMsgs` .

```powershell
$TextMsgs.Text001
$TextMsgs.Text002
```

Alternativt kan du ange variabel namnet i definitionen av data avsnittet. Exempel:

```powershell
DATA TextMsgs {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}

$TextMsgs
```

Resultatet är detsamma som i föregående exempel.

```Output
Name                           Value
----                           -----
Text001                        Windows 7
Text002                        Windows Server 2008 R2
```

### <a name="examples"></a>Exempel

Enkla data strängar.

```powershell
DATA {
    "Thank you for using my PowerShell Organize.pst script."
    "It is provided free of charge to the community."
    "I appreciate your comments and feedback."
}
```

Strängar som innehåller tillåtna variabler.

```powershell
DATA {
    if ($null) {
        "To get help for this cmdlet, type get-help new-dictionary."
    }
}
```

En ensiffrig här-sträng som använder `ConvertFrom-StringData` cmdleten:

```powershell
DATA {
    ConvertFrom-StringData -stringdata @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

En Double-citerad här – sträng som använder `ConvertFrom-StringData` cmdleten:

```powershell
DATA  {
    ConvertFrom-StringData -stringdata @"
Msg1 = To start, press any key.
Msg2 = To exit, type "quit".
"@
}
```

Ett data avsnitt som innehåller en användardefinierad cmdlet som genererar data:

```powershell
DATA -supportedCommand Format-XML {
    Format-Xml -strings string1, string2, string3
}
```

## <a name="see-also"></a>Se även

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_If](about_If.md)

[about_Operators](about_Operators.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Script_Internationalization](about_Script_Internationalization.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[Importera – LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

