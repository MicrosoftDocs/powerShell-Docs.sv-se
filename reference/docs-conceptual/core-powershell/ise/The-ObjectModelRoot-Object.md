---
ms.date: 2017-08-25
keywords: PowerShell-cmdlet
title: Objektet ObjectModelRoot
ms.openlocfilehash: eb3424ff147c35364fa08543d59ebd30f6d2d857
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="the-objectmodelroot-object"></a>Objektet ObjectModelRoot

Den **$psISE** -objektet, vilket är det viktigaste rotobjektet i Windows PowerShell® Integrated Scripting Environment (ISE) är en instans av klassen Microsoft.PowerShell.Host.ISE.ObjectModelRoot.
Det här avsnittet beskriver egenskaperna för den **ObjectModelRoot** objekt.

## <a name="properties"></a>Egenskaper

### <a name="currentfile"></a>CurrentFile

> Stöds i Windows PowerShell ISE 2.0 och senare. 

Den skrivskyddade egenskapen som hämtar filen, som är associerat med denna Värdobjektet som har fokus för tillfället.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> Stöds i Windows PowerShell ISE 2.0 och senare.

Den skrivskyddade egenskapen som hämtar fliken PowerShell som har fokus.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> Stöds i Windows PowerShell ISE 2.0 och senare.

Skrivskyddad egenskap som hämtar synliga tilläggsverktyg för Windows PowerShell ISE som finns i verktygsfönstret vågräta längst ned i redigeraren.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> Stöds i Windows PowerShell ISE 2.0 och senare. 

Skrivskyddad egenskap som hämtar synliga tilläggsverktyg för Windows PowerShell ISE som finns i verktygsfönstret lodräta på höger sida av redigeraren.

### <a name="options"></a>Options

> Stöds i Windows PowerShell ISE 2.0 och senare. 

Skrivskyddad egenskap som hämtar de olika alternativ som kan ändra inställningar i Windows PowerShell ISE.

### <a name="powershelltabs"></a>PowerShellTabs

> Stöds i Windows PowerShell ISE 2.0 och senare. 

Den skrivskyddade egenskapen som hämtar insamling av PowerShell-flikar som är öppna i Windows PowerShell ISE. Det här objektet innehåller som standard en PowerShell-flik. Men du kan lägga till fler PowerShell flikar objektet med hjälp av skript eller genom att använda menyerna i Windows PowerShell ISE.

## <a name="see-also"></a>Se även

- [Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Windows PowerShell ISE objektreferens modellen](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [Modellen objekthierarkin ISE](The-ISE-Object-Model-Hierarchy.md)
