---
title: Skriva ett program för Windows PowerShell-värd | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: 2df5a59833fcdd58c6b2afbb4882111592fb3d76
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056438"
---
# <a name="writing-a-windows-powershell-host-application"></a>Skriva ett Windows PowerShell-värdprogram

Du kan vara värd för Windows PowerShell i ditt program. Värdprogrammet kan definiera runspace där kommandon är köra, öppna sessioner på en lokal dator eller fjärrdator och anropa kommandon synkront eller asynkront, beroende på dina behov för programmet.

I följande avsnitt beskriver hur du skapar ett program som är värd

## <a name="in-this-section"></a>I detta avsnitt

[Snabbstart för Windows PowerShell-värd](./windows-powershell-host-quickstart.md) tillhandahåller instruktioner och kodexempel för att komma igång med att skapa vara värd för program.

[Skapa Körningsutrymmen](./creating-runspaces.md) en samling hjälpavsnitt som beskriver hur du skapar körningsutrymmen för att köra Windows PowerShell-kommando i ett program.

[Att lägga till och anropa kommandon](./adding-and-invoking-commands.md) förklarar hur du skapar och kör en pipeline för kommandot i din värdapp...

[Skapa fjärransluten körningsutrymmen](./creating-remote-runspaces.md) förklarar hur du ansluter ett körningsutrymme till en fjärrdator.

[Skapa ett anpassat användargränssnitt](./creating-a-custom-user-interface.md) Introduces anpassade användarinställningar gränssnitt och innehåller länkar till exempel.

[Vara värd för programmet exempel](./host-application-samples.md) det här avsnittet innehåller exempel på fullständiga värd för program.

## <a name="see-also"></a>Se även

[Windows PowerShell](http://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)