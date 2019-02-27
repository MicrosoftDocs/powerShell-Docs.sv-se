---
title: 'Så här importerar du cmdlet: ar med moduler | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849016"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Importera cmdlets med hjälp av moduler

Det här avsnittet beskriver hur du importerar cmdlet: ar till en Windows PowerShell-session med hjälp av en binär modul.

> [!NOTE]
> Medlemmarna i moduler kan innehålla cmdlets, providers, funktioner, variabler, alias och mycket mer. Snapin-moduler kan innehålla endast-cmdlets och providers.

## <a name="how-to-load-cmdlets-using-a-module"></a>Hur du läser in cmdlet: ar med en modul

1. Skapa en modul-mapp som har samma namn som sammansättningsfilen där cmdletarna har implementerats. I den här proceduren modulmappen skapas i den `system32` mapp.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. Se till att den `PSModulePath` miljövariabeln innehåller sökvägen till den nya modulmappen. Som standard systemmappen har redan lagts till i `PSModulePath` miljövariabeln.

3. Kopiera cmdlet-sammansättningen i modulmappen.

4. Kör följande kommando för att lägga till cmdlets till sessionen:

   `import-module [Module_Name]`

   Den här proceduren kan användas för att testa dina cmdlets. Det lägger till alla cmdletar i sammansättningen till sessionen. Mer information om de olika typerna av moduler, olika sätt att läsa in moduler och hur du begränsar den del av en modul som exporteras, finns i [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Installera moduler](../module/installing-a-powershell-module.md)