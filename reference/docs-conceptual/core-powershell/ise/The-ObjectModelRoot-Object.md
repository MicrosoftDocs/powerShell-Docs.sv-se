---
ms.date: 08/25/2017
keywords: PowerShell-cmdlet
title: ObjectModelRoot-objektet
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954610"
---
# <a name="the-objectmodelroot-object"></a>ObjectModelRoot-objektet

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

- [Syftet med Windows PowerShell ISE Scripting Object Model](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)