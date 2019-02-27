---
title: Så här testar du uppdateringsbar hjälp | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: f2f319a3cab4b4bd91e9b634dda57d58a6476b62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845929"
---
# <a name="how-to-test-updatable-help"></a>Testa uppdateringsbar hjälp

Det här avsnittet beskrivs metoder för att testa uppdateringsbar hjälp för en modul.

## <a name="using-verbose-to-detect-errors"></a>Med hjälp av utförlig identifiera fel

När du har överfört HelpInfo XML-filen och CAB-filer för att testa filerna genom att köra en [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) med den **utförlig** parametern. Den **utförlig** parametern leder `Update-Help` att rapportera kritisk stegen i dess åtgärder, läser den **HelpInfoUri** nyckeln i modulmanifestet att validera filtyper i uppackat CAB-filen och placera filerna i modulkatalogen språkspecifika.
När du har överfört HelpInfo XML-filen och CAB-filer för att testa filerna genom att köra en [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) med den **utförlig** parametern. Den **utförlig** parametern leder `Update-Help` att rapportera kritisk stegen i dess åtgärder, läser den **HelpInfoUri** nyckeln i modulmanifestet att validera filtyper i uppackat CAB-filen och placera filerna i modulkatalogen språkspecifika.

När alla utförliga meddelanden är löst kör en `Update-Help` med den **felsöka** parametern. Den här parametern ska identifiera eventuella återstående problem med uppdateringsbar hjälp-filer.