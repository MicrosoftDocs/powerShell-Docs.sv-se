---
ms.date: 08/25/2017
keywords: PowerShell cmdlet
title: ObjectModelRoot-objektet
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406033"
---
# <a name="the-objectmodelroot-object"></a>ObjectModelRoot-objektet

Den **$psISE** -objektet, vilket är huvudnamn rotobjektet i Windows PowerShell® Integrated Scripting Environment (ISE) är en instans av klassen Microsoft.PowerShell.Host.ISE.ObjectModelRoot.
Det här avsnittet beskriver egenskaperna för den **ObjectModelRoot** objekt.

## <a name="properties"></a>Egenskaper

### <a name="currentfile"></a>CurrentFile

> Stöds i Windows PowerShell ISE 2.0 och senare.

Den skrivskyddade egenskapen som hämtar filen, som är associerad med den här värdobjekt som för närvarande har fokus.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> Stöds i Windows PowerShell ISE 2.0 och senare.

Den skrivskyddade egenskapen som hämtar fliken PowerShell som är markerat.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> Stöds i Windows PowerShell ISE 2.0 och senare.

Skrivskyddad egenskap som hämtar synliga Windows PowerShell ISE-tilläggsverktyg som finns i verktygsfönstret vågrät längst ned i redigeraren.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> Stöds i Windows PowerShell ISE 2.0 och senare.

Skrivskyddad egenskap som hämtar synliga Windows PowerShell ISE-tilläggsverktyg som finns i den lodräta verktygsfönstret på höger sida av redigeraren.

### <a name="options"></a>Options

> Stöds i Windows PowerShell ISE 2.0 och senare.

Skrivskyddad egenskap som hämtar de olika alternativen som kan ändra inställningarna i Windows PowerShell ISE.

### <a name="powershelltabs"></a>PowerShellTabs

> Stöds i Windows PowerShell ISE 2.0 och senare.

Den skrivskyddade egenskapen som hämtar uppsättning PowerShell-flikar som är öppna i Windows PowerShell ISE. Det här objektet innehåller som standard en PowerShell-flik. Men du kan lägga till fler PowerShell flikar det här objektet med hjälp av skript eller genom att använda menyerna i Windows PowerShell ISE.

## <a name="see-also"></a>Se även

- [Syftet med den Windows PowerShell ISE-Skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)