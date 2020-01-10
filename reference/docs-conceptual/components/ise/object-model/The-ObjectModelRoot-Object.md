---
ms.date: 08/25/2017
keywords: PowerShell, cmdlet
title: ObjectModelRoot-objektet
ms.openlocfilehash: 0b04bdb3127edaac7b504556843efb64ee65ed13
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736036"
---
# <a name="the-objectmodelroot-object"></a>ObjectModelRoot-objektet

`$psISE`-objektet, som är huvud rot objekt i Windows PowerShell® Integrated Scripting Environment (ISE) är en instans av klassen Microsoft. PowerShell. Host. ISE. ObjectModelRoot. I det här avsnittet beskrivs egenskaperna för **ObjectModelRoot** -objektet.

## <a name="properties"></a>Egenskaper

### <a name="currentfile"></a>CurrentFile

> Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar filen, som är associerad med det här värd objektet som för närvarande är i fokus.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar PowerShell-fliken som har fokus.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar det för närvarande synliga Windows PowerShell ISE tilläggs verktyget som finns i det vågräta verktygs fönstret längst ned i redigeraren.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar det för närvarande synliga Windows PowerShell ISE tilläggs verktyget som finns i det lodräta verktygs fönstret till höger i redigeraren.

### <a name="options"></a>Options

> Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar de olika alternativen som kan ändra inställningarna i Windows PowerShell ISE.

### <a name="powershelltabs"></a>PowerShellTabs

> Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar insamlingen av PowerShell-flikar, som är öppna i Windows PowerShell ISE. Som standard innehåller det här objektet en PowerShell-flik. Du kan dock lägga till fler PowerShell-flikar i objektet med hjälp av skript eller genom att använda menyerna i Windows PowerShell ISE.

## <a name="see-also"></a>Se även

- [Syftet med Windows PowerShell ISE-skriptets objekt modell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)