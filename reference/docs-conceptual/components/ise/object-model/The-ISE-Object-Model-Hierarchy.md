---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: ISE-objektmodellhierarkin
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "62057731"
---
# <a name="the-ise-object-model-hierarchy"></a>ISE-objektmodellhierarkin

I det här avsnittet visas hierarkin för objekt som ingår i Windows PowerShell ISE (Integrated Scripting Environment).
Windows PowerShell ISE ingår i Windows PowerShell 3,0 och i Windows PowerShell 4,0.
Klicka på ett objekt för att ta dig till referens dokumentationen för den klass som definierar objektet.

## <a name="psise-object"></a>$psISE objekt

**$PsISE** -objektet är [rotobjektet](The-ObjectModelRoot-Object.md) för hierarkin Windows PowerShell ISE objekt.
På den översta nivån gör den följande objekt tillgängliga för skript:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE. CurrentFile](The-ISEFile-Object.md)

Objektet **$psISE. CurrentFile** är en instans av klassen [ISEFile](The-ISEFile-Object.md) .

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE. CurrentPowerShellTab](The-PowerShellTab-Object.md)

Objektet **$psISE. CurrentPowerShellTab** är en instans av klassen [PowerShellTab](The-PowerShellTab-Object.md) .

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE. CurrentVisibleHorizontalTool

Objektet **$psISE. CurrentVisibleHorizontalTool** är en instans av klassen [ISEAddOnTool](The-ISEAddOnTool-Object.md) .
Den representerar det installerade tilläggs verktyget som för närvarande är dockat till den övre kanten i Windows PowerShell ISEs fönstret.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE. CurrentVisibleVerticalTool

Objektet **$psISE. CurrentVisibleHorizontalTool** är en instans av klassen [ISEAddOnTool](The-ISEAddOnTool-Object.md) .
Den representerar det installerade tilläggs verktyget som för närvarande är dockat till den högra kanten i Windows PowerShell ISEs fönstret.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE. alternativ](The-ISEOptions-Object.md)

Objektet **$psISE. Options** är en instans av klassen [ISEOptions](The-ISEOptions-Object.md) .
Objektet ISEOptions representerar olika inställningar för Windows PowerShell ISE.
Det är en instans av klassen Microsoft. PowerShell. Host. ISE. ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE. PowerShellTabs](The-PowerShellTabCollection-Object.md)

Objektet **$psISE. PowerShellTabs** är en instans av klassen [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) .
Det är en samling av alla öppna PowerShell-flikar som representerar de tillgängliga Windows PowerShell-körnings miljöerna på den lokala datorn eller på anslutna fjärrdatorer.
Varje medlem i samlingen är en instans av klassen [PowerShellTab](The-PowerShellTab-Object.md) .

## <a name="see-also"></a>Se även

- [Syftet med Windows PowerShell ISE-skriptets objekt modell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)