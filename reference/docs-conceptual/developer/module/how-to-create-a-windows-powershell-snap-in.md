---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa en Windows PowerShell-snapin-modul
description: Skapa en Windows PowerShell-snapin-modul
ms.openlocfilehash: 29394ebcd2f7c4a547aabcb88685ff494b2c381d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657265"
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
