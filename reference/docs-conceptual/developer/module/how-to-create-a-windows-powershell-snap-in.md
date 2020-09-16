---
title: Så här skapar du en Windows PowerShell-snapin-modul | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.openlocfilehash: 4150ba582544d1daa4a898f0ff20b169c24a0ee0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787333"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Skapa en Windows PowerShell-snapin-modul

En Windows PowerShell-snapin-modul innehåller en mekanism för registrering av uppsättningar av cmdlets och en annan Windows PowerShell-Provider med gränssnittet, vilket utökar funktionerna i gränssnittet. En snapin-modul för Windows PowerShell kan registrera alla cmdlets och providers i en enda sammansättning, eller så kan den registrera en viss lista med cmdlets och providers.

Snapin-sammansättningar bör installeras i en skyddad katalog, precis som de skulle vara med andra operativ system. Annars kan obehöriga användare ersätta en sammansättning med osäker kod.

## <a name="windows-powershell-snap-in-classes"></a>Windows PowerShell snap-in-klasser

Alla Windows PowerShell snap-in-klasser härleds från klassen [system. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) eller [system. Management. Automation. Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .

## <a name="examples"></a>Exempel

[Skriva en Windows PowerShell-snapin-modul](./writing-a-windows-powershell-snap-in.md): det här exemplet visar hur du skapar en snapin-modul som används för att registrera alla cmdlets och providers i en sammansättning.

[Skriva en anpassad Windows PowerShell-snapin-modul](./writing-a-custom-windows-powershell-snap-in.md): det här exemplet visar hur du skapar en anpassad snapin-modul som används för att registrera en viss uppsättning cmdlets och providrar som kan vara eller inte finns i en enda sammansättning.

## <a name="see-also"></a>Se även

[System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)

[System. Management. Automation. Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Registrera cmdlets](./registering-cmdlets.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
