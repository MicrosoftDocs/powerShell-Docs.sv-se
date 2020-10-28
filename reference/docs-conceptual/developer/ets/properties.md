---
ms.date: 07/09/2020
ms.topic: reference
title: Egenskaper för utökad typ system
description: Egenskaper för utökad typ system
ms.openlocfilehash: cccd3c400a8822ee25c44e8e1625e35571420259
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646138"
---
# <a name="ets-properties"></a>ETS-egenskaper

Egenskaper är medlemmar som kan hanteras som en egenskap. De kan egentligen visas till vänster i ett uttryck. De egenskaper som är tillgängliga inkluderar alias, kod, anteckning och skript egenskaper.

## <a name="alias-property"></a>Alias egenskap

En alias-egenskap är en egenskap som refererar till en annan egenskap som **PSObject** -objektet innehåller. Den används främst för att byta namn på den refererade egenskapen. Det kan dock också användas för att konvertera den refererade egenskapens värde till en annan typ. Med avseende på ETS är den här typen av egenskap alltid en utökad medlem och definieras av [PSAliasProperty](/dotnet/api/system.management.automation.psaliasproperty) -klassen. Klassen innehåller följande egenskaper.

- **ConversionType** -egenskap: den CLR-typ som används för att konvertera den refererade medlemmens värde.
- **IsGettable** -egenskap: anger om det går att hämta värdet för den refererade egenskapen.
  Den här egenskapen bestäms dynamiskt genom att undersöka egenskapen **IsGettable** för den refererade egenskapen.
- **IsSettable** -egenskap: anger om det går att ange värdet för den refererade egenskapen. Den här egenskapen bestäms dynamiskt genom att undersöka egenskapen **IsSettable** för den refererade egenskapen.
- **MemberType** -egenskap: en **AliasProperty** -uppräknings konstant som definierar den här egenskapen som en Ali Aset-egenskap.
- **ReferencedMemberName** -egenskap: namnet på den refererade egenskap som det här aliaset refererar till.
- **TypeNameOfValue** -egenskap: det fullständiga namnet på CLR-typen för den refererade egenskapens värde.
- **Värde** egenskap: värdet för den refererade egenskapen.

## <a name="code-property"></a>Kod egenskap

En kod egenskap är en egenskap som är en get-och set-metod som definieras i ett CLR-språk. För att en kod egenskap ska bli tillgänglig måste en utvecklare skriva egenskapen i vissa CLR-språk, kompilera och leverera den resulterande sammansättningen. Den här sammansättningen måste vara tillgänglig i körnings utrymme där kod egenskapen önskas. Med avseende på ETS är den här typen av egenskap alltid en utökad medlem och definieras av [PSCodeProperty](/dotnet/api/system.management.automation.pscodeproperty) -klassen. Klassen innehåller följande egenskaper.

- **GetterCodeReference** -egenskap: metoden som används för att hämta värdet för kod egenskapen.
- **IsGettable** -egenskap: anger om värdet för egenskapen Code kan hämtas, att egenskapen **SetterCodeReference** : metoden som används för att ange värdet för kod egenskapen.
- **IsSettable** -egenskap: anger om värdet för egenskapen Code kan anges, att egenskapen **SetterCodeReference** inte är null.
- **MemberType** -egenskap: en **CodeProperty** -uppräknings konstant som definierar den här egenskapen som en kod egenskap.
- **SetterCodeReference** -egenskap: metoden som används för att hämta värdet för kod egenskapen.
- **TypeNameOfValue** -egenskap: CLR-typ för det kod egenskaps värde som returneras av åtgärden Hämta egenskaper.
- **Värde** egenskap: värdet för egenskapen Code. När den här egenskapen hämtas anropas get-koden i GetterCodeReference-egenskapen, den aktuella **PSObject** -objektet skickas och det värde som returneras av anropet returneras. När den här egenskapen har angetts anropas set-koden i **SetterCodeReference** -egenskapen och skickar det aktuella **PSObject** -objektet som det första argumentet och det objekt som används för att ange värdet som det andra argumentet.

## <a name="note-property"></a>Antecknings egenskap

En antecknings egenskap är en egenskap som har ett namn/värde-par. Med avseende på ETS är den här typen av egenskap alltid en utökad medlem och definieras av [PSNoteProperty](/dotnet/api/system.management.automation.psnoteproperty) -klassen. Klassen innehåller följande egenskaper.

- **IsGettable** -egenskap: anger om det går att hämta värdet för antecknings egenskapen.
- **IsSettable** -egenskap: anger om det går att ange värdet för antecknings egenskapen.
- **MemberType** -egenskap: en **NoteProperty** -uppräknings konstant som definierar den här egenskapen som en antecknings egenskap.
- **TypeNameOfValue** -egenskap: det fullständigt kvalificerade typ namnet för objektet som returneras av antecknings egenskapens get-åtgärd.
- **Värde** : värdet för antecknings egenskapen.

## <a name="powershell-property"></a>PowerShell-egenskap

En PowerShell-egenskap är en egenskap som definierats för bas objektet eller en egenskap som görs tillgänglig via en adapter. Det kan referera till både CLR-fält och CLR-egenskaper. Med avseende på ETS kan denna typ av egenskap antingen vara en bas medlem eller en adapter och definieras av klassen [PSProperty](/dotnet/api/system.management.automation.psproperty) . Klassen innehåller följande egenskaper.

- **IsGettable** -egenskap: anger om värdet för bas-eller den anpassade egenskapen kan hämtas.
- **IsSettable** -egenskap: anger om värdet för egenskapen bas eller anpassad kan anges.
- **MemberType** -egenskap: en konstant egenskaps uppräkning som definierar den här egenskapen som en PowerShell-egenskap.
- **TypeNameOfValue** -egenskap: det fullständigt kvalificerade namnet på egenskaps värde typen. Till exempel, för en egenskap vars värde är en sträng, är egenskaps värde typen **system. String** .
- **Värde** egenskap: egenskapens värde. Om Get-eller Set-åtgärden anropas för en egenskap som inte stöder den åtgärden genereras ett **GetValueException** -eller **SetValueException** -undantag

## <a name="powershell-script-property"></a>Egenskaper för PowerShell-skript

En skript egenskap är en egenskap med get-och set-skript. Med avseende på ETS är den här typen av egenskap alltid en utökad medlem och definieras av [PSScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) -klassen. Klassen innehåller följande egenskaper.

- **GetterScript** -egenskap: skriptet som används för att hämta skript egenskap svärdet.
- **IsGettable** -egenskap: anger om egenskapen **GetterScript** visar ett skript block.
- **IsSettable** -egenskap: anger om egenskapen **SetterScript** visar ett skript block.
- **MemberType** -egenskap: en ScriptProperty-uppräknings konstant som identifierar den här egenskapen som en skript egenskap.
- **SetterScript** -egenskap: skriptet som används för att ange skript egenskap svärdet.
- **TypeNameOfValue** -egenskap: det fullständigt kvalificerade typ namnet för objektet som returnerades av Get-skriptet. I det här fallet returneras alltid **system. Object** .
- **Värde** egenskap: värdet för skript egenskapen. En get anropar get-skriptet och returnerar det angivna värdet. En uppsättning anropar setter-skriptet.
