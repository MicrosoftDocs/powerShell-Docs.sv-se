---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: ISE-objektmodellhierarkin
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405381"
---
# <a name="the-ise-object-model-hierarchy"></a>ISE-objektmodellhierarkin

Det här avsnittet visar hierarkin med objekt som är en del av Windows PowerShell Integrated Scripting Environment (ISE).
Windows PowerShell ISE ingår i Windows PowerShell 3.0 och Windows PowerShell 4.0.
Klicka på ett objekt för att ta dig till referensdokumentation för den klass som definierar objektet.

## <a name="psise-object"></a>$psISE objekt

Den **$psISE** objektet är den [rotobjektet](The-ObjectModelRoot-Object.md) i hierarkin för Windows PowerShell ISE-objektet.
Finns på den översta nivån, är följande objekt tillgängliga för skript:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

Den **$psISE.CurrentFile** objekt är en instans av den [ISEFile](The-ISEFile-Object.md) klass.

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

Den **$psISE.CurrentPowerShellTab** objekt är en instans av den [PowerShellTab](The-PowerShellTab-Object.md) klass.

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

Den **$psISE.CurrentVisibleHorizontalTool** objekt är en instans av den [ISEAddOnTool](The-ISEAddOnTool-Object.md) klass.
Verktyget installerat tillägg som för närvarande är dockad representerar mot överkanten av Windows PowerShell ISE-fönster.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

Den **$psISE.CurrentVisibleHorizontalTool** objekt är en instans av den [ISEAddOnTool](The-ISEAddOnTool-Object.md) klass.
Den motsvarar verktyget installerat tillägg som för närvarande är dockad till den högra kanten av Windows PowerShell ISE-fönster.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

Den **$psISE.Options** objekt är en instans av den [ISEOptions](The-ISEOptions-Object.md) klass.
ISEOptions-objektet representerar olika inställningar för Windows PowerShell ISE.
Det är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

Den **$psISE.PowerShellTabs** objekt är en instans av den [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) klass.
Det är en samling med alla öppna PowerShell flikar som representerar de tillgängliga Windows PowerShell kör miljöer på den lokala datorn eller på anslutna fjärrdatorer.
Varje medlem i samlingen är en instans av den [PowerShellTab](The-PowerShellTab-Object.md) klass.

## <a name="see-also"></a>Se även

- [Syftet med den Windows PowerShell ISE-Skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)