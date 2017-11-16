---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Modellen objekthierarkin ISE
ms.openlocfilehash: 2df6d40f39dbe14bd3f46a6400cde4a6e91052ef
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a>Modellen objekthierarkin ISE
Det här avsnittet visar hierarkin med objekt som är en del av Windows PowerShell Integrated Scripting Environment (ISE). Windows PowerShell ISE ingår i Windows PowerShell 3.0 och Windows PowerShell 4.0. Klicka på ett objekt för att ta dig till referensdokumentationen för den klass som definierar objektet.

## <a name="psise-object"></a>$psISE objekt

Den **$psISE** objektet är den [rotobjektet](The-ObjectModelRoot-Object.md) i hierarkin för Windows PowerShell ISE-objektet.
Finns på den översta nivån är följande objekt tillgängliga för skript:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

Den **$psISE.CurrentFile** objekt är en instans av den [ISEFile](The-ISEFile-Object.md) klass.

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

Den **$psISE.CurrentPowerShellTab** objekt är en instans av den [PowerShellTab](The-PowerShellTab-Object.md) klass.

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

Den **$psISE.CurrentVisibleHorizontalTool** objekt är en instans av den [ISEAddOnTool](The-ISEAddOnTool-Object.md) klass.
Verktyget installerat tillägg som för närvarande är dockad representerar mot överkanten i fönstret Windows PowerShell ISE.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

Den **$psISE.CurrentVisibleHorizontalTool** objekt är en instans av den [ISEAddOnTool](The-ISEAddOnTool-Object.md) klass.
Verktyget installerat tillägg som för närvarande är dockad representerar fönstret Windows PowerShell ISE högra kant.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

Den **$psISE.Options** objekt är en instans av den [ISEOptions](The-ISEOptions-Object.md) klass.
ISEOptions-objektet representerar olika inställningar för Windows PowerShell ISE.
Det är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

Den **$psISE.PowerShellTabs** objekt är en instans av den [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) klass.
Det är en samling av alla öppna PowerShell flikar som representerar tillgängliga Windows PowerShell kör miljöer på den lokala datorn eller på anslutna fjärrdatorer. Varje medlem i samlingen är en instans av den [PowerShellTab](The-PowerShellTab-Object.md) klass.

## <a name="see-also"></a>Se även
- [Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Windows PowerShell ISE objektreferens modellen](Windows-PowerShell-ISE-Object-Model-Reference.md)
