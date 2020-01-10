---
ms.date: 12/31/2019
keywords: PowerShell, cmdlet
title: ISE-objektmodellhierarkin
ms.openlocfilehash: 1ec5810fc5e7b765c2a08af83bce0415dd61a54b
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737040"
---
# <a name="the-ise-object-model-hierarchy"></a>ISE-objektmodellhierarkin

I det här avsnittet visas hierarkin för objekt som ingår i Windows PowerShell ISE (Integrated Scripting Environment). Windows PowerShell ISE ingår i Windows PowerShell 3,0, 4,0 och 5,1. Klicka på ett objekt för att ta dig till referens dokumentationen för den klass som definierar objektet.

## <a name="psise-object"></a>$psISE objekt

`$psISE`-objektet är [rotobjektet](The-ObjectModelRoot-Object.md) för hierarkin Windows PowerShell ISE objekt. På den översta nivån gör den följande objekt tillgängliga för skript:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE. CurrentFile](The-ISEFile-Object.md)

`$psISE.CurrentFile`-objektet är en instans av klassen [ISEFile](The-ISEFile-Object.md) .

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE. CurrentPowerShellTab](The-PowerShellTab-Object.md)

`$psISE.CurrentPowerShellTab`-objektet är en instans av klassen [PowerShellTab](The-PowerShellTab-Object.md) .

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE. CurrentVisibleHorizontalTool

`$psISE.CurrentVisibleHorizontalTool`-objektet är en instans av klassen [ISEAddOnTool](The-ISEAddOnTool-Object.md) . Den representerar det installerade tilläggs verktyget som för närvarande är dockat till den övre kanten i Windows PowerShell ISEs fönstret.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE. CurrentVisibleVerticalTool

`$psISE.CurrentVisibleHorizontalTool`-objektet är en instans av klassen [ISEAddOnTool](The-ISEAddOnTool-Object.md) . Den representerar det installerade tilläggs verktyget som för närvarande är dockat till den högra kanten i Windows PowerShell ISEs fönstret.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE. alternativ](The-ISEOptions-Object.md)

`$psISE.Options`-objektet är en instans av klassen [ISEOptions](The-ISEOptions-Object.md) . Objektet ISEOptions representerar olika inställningar för Windows PowerShell ISE. Det är en instans av klassen Microsoft. PowerShell. Host. ISE. ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE. PowerShellTabs](The-PowerShellTabCollection-Object.md)

`$psISE.PowerShellTabs`-objektet är en instans av klassen [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) . Det är en samling av alla öppna PowerShell-flikar som representerar de tillgängliga Windows PowerShell-körnings miljöerna på den lokala datorn eller på anslutna fjärrdatorer. Varje medlem i samlingen är en instans av klassen [PowerShellTab](The-PowerShellTab-Object.md) .

## <a name="see-also"></a>Se även

- [Syftet med Windows PowerShell ISE-skriptets objekt modell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)
