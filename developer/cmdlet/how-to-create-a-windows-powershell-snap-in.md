---
title: Så här skapar du en Windows PowerShell snapin-modulen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055945"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Skapa en Windows PowerShell-snapin-modul

Är en mekanism för att registrera uppsättningar med cmdlets och en annan Windows PowerShell-providern med shell, vilket utökar funktionaliteten i gränssnittet för en Windows PowerShell-snapin-modul. En Windows PowerShell-snapin-modul kan registrera alla cmdletar och providers i en enda sammansättning, eller den kan registrera en viss lista med cmdlets och providers.

Snapin-modulen sammansättningar ska installeras i en skyddad katalog, precis som de skulle vara med andra operativsystem. I annat fall kan angripare ersätta en sammansättning med osäkra kod.

## <a name="windows-powershell-snap-in-classes"></a>Windows-snapin-modulen för PowerShell-klasser

Alla Windows PowerShell snapin-modulen klasser som härleds från den [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) eller [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klasser.

## <a name="examples"></a>Exempel

[Skriva ett Windows PowerShell snapin-modulen](./writing-a-windows-powershell-snap-in.md): Det här exemplet visar hur du skapar en snapin-modul som används för att registrera alla cmdletar och providers i en sammansättning.

[Skriva en anpassad Windows PowerShell snapin-modul](./writing-a-custom-windows-powershell-snap-in.md): Det här exemplet visar hur du skapar en anpassad snapin-modul som används för att registrera en specifik uppsättning cmdlets och providers som kanske eller kanske inte finns i en enda sammansättning.

## <a name="see-also"></a>Se även

[System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)

[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Registrera cmdlet: ar](./registering-cmdlets.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
