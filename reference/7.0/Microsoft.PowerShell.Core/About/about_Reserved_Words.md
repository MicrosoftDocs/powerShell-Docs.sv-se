---
description: Visar en lista med reserverade ord som inte kan användas som identifierare eftersom de har en särskild betydelse i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_reserved_words?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Reserved_Words
ms.openlocfilehash: c4b67a523a40319635d159791b80ab302b9aa3b4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272324"
---
# <a name="about-reserved-words"></a>Om reserverade ord

## <a name="short-description"></a>KORT BESKRIVNING
Visar en lista med reserverade ord som inte kan användas som identifierare eftersom de har en särskild betydelse i PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

Det finns vissa ord som har en särskild betydelse i PowerShell. När dessa ord visas utan citat tecken försöker PowerShell tillämpa sin särskilda innebörd i stället för att behandla dem som tecken strängar. Om du vill använda dessa ord som parameter argument i ett kommando eller skript utan att anropa deras särskilda innebörd, omger du reserverade ord inom citat tecken.

Följande är reserverade ord i PowerShell:

```
assembly         exit            process
base             filter          public
begin            finally         return
break            for             sequence
catch            foreach         static
class            from (*)        switch
command          function        throw
configuration    hidden          trap
continue         if              try
data             in              type
define (*)       inlinescript    until
do               interface       using
dynamicparam     module          var (*)
else             namespace       while
elseif           parallel        workflow
end              param
enum             private

(*) These keywords are reserved for future use.
```

Flera språk nyckelord, inklusive `Foreach` , `If` , `For` och `While` , har sina egna hjälp artiklar. Om du vill visa dem skriver du `Get-Help about_` och lägger till nyckelordet. Om du till exempel vill hämta information om `Foreach` instruktionen skriver du:

```powershell
Get-Help about_ForEach
```

Om du vill ha mer information om `Filter` instruktionen eller `Return` syntaxen för uttrycket skriver du:

```powershell
Get-Help about_Functions
```

Om du vill ha information om andra reserverade ord skriver du:

```powershell
Get-Help <Reserved_Word>
```

> [!NOTE]
> Alla reserverade ord har inte en egen hjälp artikel. Om inte `Get-Help` returnerar en artikel kan du söka efter artiklar som talar om det reserverade ordet med hjälp av följande kommando:
>
> ```powershell
> Get-Help <Reserved_Word> -Category:HelpFile
> ```

## <a name="see-also"></a>SE ÄVEN

- [about_Command_Syntax](about_Command_Syntax.md)
- [about_Language_Keywords](about_Language_Keywords.md)
- [about_Parsing](about_Parsing.md)
- [about_Quoting_Rules](about_Quoting_Rules.md)
- [about_Script_Blocks](about_Script_Blocks.md)
- [about_Special_Characters](about_Special_Characters.md)
