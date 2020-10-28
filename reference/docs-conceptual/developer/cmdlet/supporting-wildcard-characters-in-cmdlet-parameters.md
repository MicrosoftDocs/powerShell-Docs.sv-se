---
ms.date: 08/26/2019
ms.topic: reference
title: Ge stöd för jokertecken i cmdlet-parametrar
description: Ge stöd för jokertecken i cmdlet-parametrar
ms.openlocfilehash: 06693c62cd2613050bdeb9d6b12ad6e9597a9894
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646389"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Ge stöd för jokertecken i cmdlet-parametrar

Du måste ofta utforma en cmdlet för att kunna köras mot en grupp resurser i stället för till en enda resurs. En cmdlet kan till exempel behöva hitta alla filer i ett data lager som har samma namn eller tillägg. Du måste ge stöd för jokertecken när du skapar en cmdlet som ska köras mot en grupp med resurser.

> [!NOTE]
> Användning av jokertecken kallas ibland *globbing* .

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Windows PowerShell-cmdletar som använder jokertecken

 Många Windows PowerShell-cmdlets stöder jokertecken för sina parameter värden. Till exempel nästan alla cmdletar som har en- `Name` eller- `Path` parameter stöder jokertecken för dessa parametrar. (Även om de flesta cmdletar som har en `Path` parameter också har en `LiteralPath` parameter som inte stöder jokertecken.) Följande kommando visar hur ett jokertecken används för att returnera alla cmdletar i den aktuella sessionen vars namn innehåller verbet get.

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a>Jokertecken som stöds

Windows PowerShell stöder följande jokertecken.

| Användning |                             Beskrivning                             |  Exempel   |     Matchar      | Matchar inte |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | Matchar noll eller flera tecken, med början vid den angivna positionen | `a*`       | A, AG, Apple     |                |
| ?        | Matchar alla bokstäver vid angiven position                     | `?n`       | En, i, på       | kördes            |
| [ ]      | Matchar ett tecken intervall                                       | `[a-l]ook` | bok, Cook, utseende | Nook, vidtog     |
| [ ]      | Matchar de angivna tecknen                                    | `[bn]ook`  | bok, Nook       | laga, titta     |

När du utformar cmdletar som stöder jokertecken kan du använda kombinationer av jokertecken. Följande kommando använder till exempel `Get-ChildItem` cmdleten för att hämta alla. txt-filer som finns i mappen c:\Techdocs och som börjar med bokstäverna "a" till "l".

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

Föregående kommando använder området jokertecken `[a-l]` för att ange att fil namnet ska börja med tecknen "a" till och med "l" och använder `*` jokertecknet som plats hållare för alla tecken mellan den första bokstaven i fil namnet och **. txt** -tillägget.

I följande exempel används ett mönster med jokertecken som utesluter bokstaven "d", men innehåller alla andra bokstäver från "a" till "f".

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Hantera tecken i mönster med jokertecken

Om det jokertecken du anger innehåller litterala tecken som inte ska tolkas som jokertecken använder du bakstrecks tecknet ( `` ` `` ) som ett escape-tecken. Om du anger litterala tecken int PowerShell-API: et använder du ett enda baktick. Använd två baktick när du anger litterala tecken i PowerShell-Kommandotolken.

Följande mönster innehåller till exempel två hakparenteser som måste beaktas bokstavligen.

När det används i PowerShell-API: et använder du:

- "John Svensson \` [*"] "

När det används från PowerShell-Kommandotolken:

- "John Svensson \` \` [* \` "] "

Det här mönstret matchar "John Svensson [Marketing]" eller "John Svensson [Development]". Exempel:

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a>Cmdlet-utdata och jokertecken

När cmdlet-parametrarna har stöd för jokertecken genererar åtgärden vanligt vis en mat ris utmatning.
Ibland är det ingen mening att stödja mat ris utdata eftersom användaren bara kan använda ett enda objekt. Till exempel `Set-Location` stöder cmdleten inte mat ris utdata eftersom användaren bara anger en enda plats. I den här instansen stöder cmdlet: en fortfarande jokertecken, men den framtvingar matchning till en enda plats.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[WildcardPattern-klass](/dotnet/api/system.management.automation.wildcardpattern)
