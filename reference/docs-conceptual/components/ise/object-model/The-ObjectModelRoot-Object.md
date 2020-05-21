---
ms.date: 08/25/2017
keywords: powershell,cmdlet
title: ObjectModelRoot-objektet
ms.openlocfilehash: cd94e69de2e62f7ce9fac413e15458ae9986540e
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560652"
---
# <a name="the-objectmodelroot-object"></a>ObjectModelRoot-objektet

`$psISE`Objektet, som är huvud rotens objekt i Windows PowerShell® ISE (Integrated Scripting Environment) är en instans av klassen Microsoft. PowerShell. Host. ISE. ObjectModelRoot. I det här avsnittet beskrivs egenskaperna för **ObjectModelRoot** -objektet.

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
