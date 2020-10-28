---
ms.date: 08/25/2017
title: ObjectModelRoot-objektet
description: $PsISE-objektet, som är huvud rot objekt i PowerShell ISE, är en instans av klassen Microsoft. PowerShell. Host. ISE. ObjectModelRoot. I det här avsnittet beskrivs egenskaperna för ObjectModelRoot-objektet.
ms.openlocfilehash: c8ae703c2663256ca037090fd3b1eb239cfc431a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660945"
---
# <a name="the-objectmodelroot-object"></a>ObjectModelRoot-objektet

`$psISE`Objektet, som är huvud rot objekt i Windows POWERSHELL &reg; Ise (Integrated Scripting Environment) är en instans av klassen Microsoft. PowerShell. Host. ISE. ObjectModelRoot. I det här avsnittet beskrivs egenskaperna för **ObjectModelRoot** -objektet.

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

### <a name="options"></a>Alternativ

> Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar de olika alternativen som kan ändra inställningarna i Windows PowerShell ISE.

### <a name="powershelltabs"></a>PowerShellTabs

> Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar insamlingen av PowerShell-flikar, som är öppna i Windows PowerShell ISE. Som standard innehåller det här objektet en PowerShell-flik. Du kan dock lägga till fler PowerShell-flikar i objektet med hjälp av skript eller genom att använda menyerna i Windows PowerShell ISE.

## <a name="see-also"></a>Se även

- [Användningsområden för Windows PowerShell ISE-skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Objekt modells-hierarkin för ISE](The-ISE-Object-Model-Hierarchy.md)
