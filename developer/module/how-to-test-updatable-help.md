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
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794271"
---
# <a name="how-to-test-updatable-help"></a>Testa uppdateringsbar hjälp

Det här avsnittet beskrivs metoder för att testa uppdateringsbar hjälp för en modul.

## <a name="using-verbose-to-detect-errors"></a>Med hjälp av utförlig identifiera fel

När du har överfört HelpInfo XML-filen och CAB-filer för att testa filerna genom att köra en [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) med den **utförlig** parametern. Den **utförlig** parametern leder `Update-Help` att rapportera kritisk stegen i dess åtgärder, läser den **HelpInfoUri** nyckeln i modulmanifestet att validera filtyper i uppackat CAB-filen och placera filerna i modulkatalogen språkspecifika.

När alla utförliga meddelanden är löst kör en `Update-Help` med den **felsöka** parametern. Den här parametern ska identifiera eventuella återstående problem med uppdateringsbar hjälp-filer.