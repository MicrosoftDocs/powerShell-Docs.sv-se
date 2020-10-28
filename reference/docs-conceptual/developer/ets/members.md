---
ms.date: 07/09/2020
ms.topic: reference
title: Medlemmar i utökad typ system klass
description: Medlemmar i utökad typ system klass
ms.openlocfilehash: 06488ce423f363a285ab53b21ab45989654346dc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666849"
---
# <a name="extended-type-system-class-members"></a>Medlemmar i utökad typ system klass

ETS refererar till ett antal olika typer av medlemmar vars typer definieras av **PSMemberTypes** -uppräkningen. Dessa medlems typer innehåller egenskaper, metoder, medlemmar och medlems uppsättningar som definieras av deras egna CLR-typ. En **NoteProperty** definieras till exempel av en egen **PSNoteProperty** -typ. Dessa enskilda CLR-typer har både egna unika egenskaper och gemensamma egenskaper som ärvs från PSMemberInfo- [klassen](/dotnet/api/system.management.automation.psmemberinfo).

## <a name="the-psmemberinfo-class"></a>PSMemberInfo-klassen

**PSMemberInfo** -klassen fungerar som en basklass för alla typer av ETS-medlemmar. Den här klassen ger följande grundläggande egenskaper till alla medlems CLR-typer.

- **Namn** egenskap: medlemmens namn. Det här namnet kan definieras av Bask-objektet eller definieras av PowerShell när anpassade medlemmar eller utökade medlemmar exponeras.
- **Value** -egenskap: det värde som returneras från en viss medlem. Varje medlems typ definierar hur den hanterar sitt medlems värde.
- **TypeNameOfValue** -egenskap: Detta är namnet på CLR-typen för det värde som returneras av value-egenskapen.

## <a name="accessing-members"></a>Åtkomst till medlemmar

Samlingar med medlemmar kan nås via egenskaperna **members** , **Method** och **Properties** för **PSObject** -objektet.

## <a name="ets-properties"></a>ETS-egenskaper

ETS-egenskaper är medlemmar som kan hanteras som en egenskap. De kan egentligen visas till vänster i ett uttryck. De innehåller egenskaper för alias, kod egenskaper, PowerShell-egenskaper, antecknings egenskaper och skript egenskaper. Mer information om dessa typer av egenskaper finns i [ETS-egenskaper](properties.md).

## <a name="ets-methods"></a>ETS-metoder

ETS-metoder är medlemmar som kan ta argument, kan returnera resultat och får inte visas till vänster i ett uttryck. De innehåller kod metoder, PowerShell-metoder och skript metoder.
Mer information om dessa typer av metoder finns i [ETS-metoder](methods.md).
