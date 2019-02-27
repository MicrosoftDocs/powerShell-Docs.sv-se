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
ms.openlocfilehash: 2039e181becd1b39fc3d6cf0cdbcf0c20e9fc206
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851837"
---
# <a name="writing-a-windows-powershell-host-application"></a>Skriva ett Windows PowerShell-värdprogram

Du kan vara värd för Windows PowerShell i ditt program. Värdprogrammet kan definiera runspace där kommandon är köra, öppna sessioner på en lokal dator eller fjärrdator och anropa kommandon synkront eller asynkront, beroende på dina behov för programmet.

I följande avsnitt beskriver hur du skapar ett program som är värd

## <a name="in-this-section"></a>I detta avsnitt

[Snabbstart för Windows PowerShell-värd](./windows-powershell-host-quickstart.md) tillhandahåller instruktioner och kodexempel för att komma igång med att skapa vara värd för program.

[Skapa Körningsutrymmen](./creating-runspaces.md) en samling hjälpavsnitt som beskriver hur du skapar körningsutrymmen för att köra Windows PowerShell-kommando i ett program.

[Att lägga till och anropa kommandon](./adding-and-invoking-commands.md) förklarar hur du skapar och kör en pipeline för kommandot i din värdapp...

[Skapa fjärransluten körningsutrymmen](./creating-remote-runspaces.md) Expains hur du ansluter ett körningsutrymme till en fjärrdator.

[Skapa ett anpassat användargränssnitt](./creating-a-custom-user-interface.md) Introduces anpassade användarinställningar gränssnitt och innehåller länkar till exempel.

[Vara värd för programmet exempel](./host-application-samples.md) det här avsnittet innehåller exempel på fullständiga värd för program.

## <a name="see-also"></a>Se även

[Windows PowerShell](http://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)