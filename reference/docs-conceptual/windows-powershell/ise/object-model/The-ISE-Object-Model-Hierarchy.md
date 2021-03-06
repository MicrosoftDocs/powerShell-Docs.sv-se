---
ms.date: 12/31/2019
title: ISE-objektmodellhierarkin
description: Den här artikeln visar hierarkin med objekt som är en del av Windows PowerShell ISE.
ms.openlocfilehash: 00980cda72f05bc6ccb398079b129de13a98f783
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658318"
---
# <a name="the-ise-object-model-hierarchy"></a>ISE-objektmodellhierarkin

Den här artikeln visar hierarkin med objekt som ingår i Windows PowerShell ISE (Integrated Scripting Environment). Windows PowerShell ISE ingår i Windows PowerShell 3,0, 4,0 och 5,1. Klicka på ett objekt för att ta dig till referens dokumentationen för den klass som definierar objektet.

## <a name="psise-object"></a>$psISE objekt

`$psISE`Objektet är [rotobjektet](The-ObjectModelRoot-Object.md) för den Windows PowerShell ISE Object-hierarkin. På den översta nivån gör den följande objekt tillgängliga för skript:

## <a name="psisecurrentfile"></a>[$psISE. CurrentFile](The-ISEFile-Object.md)

`$psISE.CurrentFile`Objektet är en instans av klassen [ISEFile](The-ISEFile-Object.md) .

## <a name="psisecurrentpowershelltab"></a>[$psISE. CurrentPowerShellTab](The-PowerShellTab-Object.md)

`$psISE.CurrentPowerShellTab`Objektet är en instans av klassen [PowerShellTab](The-PowerShellTab-Object.md) .

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE. CurrentVisibleHorizontalTool

`$psISE.CurrentVisibleHorizontalTool`Objektet är en instans av klassen [ISEAddOnTool](The-ISEAddOnTool-Object.md) . Den representerar det installerade tilläggs verktyget som för närvarande är dockat till den övre kanten i Windows PowerShell ISEs fönstret.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE. CurrentVisibleVerticalTool

`$psISE.CurrentVisibleHorizontalTool`Objektet är en instans av klassen [ISEAddOnTool](The-ISEAddOnTool-Object.md) . Den representerar det installerade tilläggs verktyget som för närvarande är dockat till den högra kanten i Windows PowerShell ISEs fönstret.

## <a name="psiseoptions"></a>[$psISE. alternativ](The-ISEOptions-Object.md)

`$psISE.Options`Objektet är en instans av klassen [ISEOptions](The-ISEOptions-Object.md) . Objektet ISEOptions representerar olika inställningar för Windows PowerShell ISE. Det är en instans av klassen Microsoft. PowerShell. Host. ISE. ISEOptions.

## <a name="psisepowershelltabs"></a>[$psISE. PowerShellTabs](The-PowerShellTabCollection-Object.md)

`$psISE.PowerShellTabs`Objektet är en instans av klassen [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) . Det är en samling av alla öppna PowerShell-flikar som representerar de tillgängliga Windows PowerShell-körnings miljöerna på den lokala datorn eller på anslutna fjärrdatorer. Varje medlem i samlingen är en instans av klassen [PowerShellTab](The-PowerShellTab-Object.md) .

## <a name="see-also"></a>Se även

- [Användningsområden för Windows PowerShell ISE-skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Objekt modells-hierarkin för ISE](The-ISE-Object-Model-Hierarchy.md)
