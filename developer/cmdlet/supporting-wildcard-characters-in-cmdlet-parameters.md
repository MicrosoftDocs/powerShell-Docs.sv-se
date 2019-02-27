---
title: Stöd för jokertecken i Cmdlet-parametrarna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 296490e4692e72f823be0b00aee90dc8c3dc9131
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851375"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Ge stöd för jokertecken i cmdlet-parametrar

Du får ofta att utforma en cmdlet för att köra mot en grupp med resurser i stället för mot en enskild resurs. Till exempel behöva en cmdlet att hitta alla filer i ett datalager som har samma namn eller tillägg. Du måste tillhandahålla support för jokertecken när du utformar en cmdlet som ska köras mot en grupp med resurser.

> [!NOTE]
> Använda jokertecken är kallas ibland *globbing*.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Windows PowerShell-cmdletar som använder jokertecken

 Många Windows PowerShell-cmdletar stöder jokertecken för sina parametervärden. Till exempel nästan alla cmdlet som har en `Name` eller `Path` parametern har stöd för jokertecken för dessa parametrar. (Även om de flesta cmdletar som har en `Path` parametern också ha en `LiteralPath` parameter som inte stöder jokertecken.) Följande kommando visar hur ett jokertecken används för att returnera alla cmdletar i den aktuella sessionen vars namn innehåller Get-verbet.

 **PS > get-kommandot get -\***

## <a name="supported-wildcard-characters"></a>Jokertecken stöds

Windows PowerShell har stöd för följande jokertecken.

|Jokertecken|Beskrivning|Exempel|Matchningar|Matchar inte|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|Matchar noll eller flera tecken, med början vid den angivna positionen|a*|En, ag, Apple||
|?|Matchningar anycharacter vid den angivna positionen|?n|En i, på|kördes|
|[ ]|Matchar ett teckenintervall|[a-l]ook|bok, Cooköarna, utseende|tog|
|[ ]|Matchar de angivna tecken|[bc]ook|bok, Cooköarna|Titta|

När du utformar cmdletar som stöder jokertecken Tillåt kombinationer av jokertecken. Till exempel följande kommando använder de `Get-ChildItem` cmdlet för att hämta alla txt-filer som finns i mappen c:\Techdocs och som börjar med ”a” till ”l”.

**Get-childitem c:\techdocs\\[a-l]\*.txt**

Föregående kommando använder jokertecknet intervallet **[a-l]** att ange att filnamnet ska börja med tecknen ”a” till ”l”. Kommandot använder sedan den * jokertecknet som platshållare för några tecken mellan den första bokstaven i filnamnet och filnamnstillägget .txt.

I följande exempel används ett intervall med jokerteckensmönster som utesluter bokstaven ”d” men innehåller alla andra bokstäver från ”a” till ”f”.

**Get-childitem c:\techdocs\\[a-cef]\*.txt**

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Hantering av vanliga tecken i mönster med jokertecken

Om mönstret med jokertecken som du anger innehåller vanliga tecken, använder du backtick citattecken (') som escape-tecken. När du anger strängtecken programmässigt kan du använda en enda backtick. När du anger strängtecken i Kommandotolken, använder du två grava accenter. Följande mönster innehåller till exempel två hakparenteser som måste vidtas bokstavligt.

”John Smith \`[*”] ”(anges via programmering)

”John Smith \` \`[*\`”] ”(som anges i Kommandotolken)

Det här mönstret matchar ”John Smith [marknadsföring]” eller ”John Smith [utveckling]”.

## <a name="cmdlet-output-and-wildcard-characters"></a>Cmdlet-utdata och jokertecken

Om cmdlet-parametrarna har stöd för jokertecken, genererar en cmdlet-åtgärd vanligtvis matrisutdata. Ibland kan det vara bra utan att stödja en matris som utdata eftersom användaren kan använda endast en post i taget. Till exempel den `Set-Location` cmdlet har stöd för en matris som utdata eftersom användaren anger en enda plats. Cmdlet: en har fortfarande stöd för jokertecken i den här instansen, men tvingas av lösningen till en enda plats.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[WildcardPattern-klass](/dotnet/api/system.management.automation.wildcardpattern)
