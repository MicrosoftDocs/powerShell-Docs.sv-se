---
title: Windows PowerShell-referens | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell SDK
ms.assetid: cbba4879-bcac-484a-9906-4bbe2cd1eb33
caps.latest.revision: 11
ms.openlocfilehash: 86595ebaac32318a4e3b9a3c4b295c73fb2e1c75
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080509"
---
# <a name="windows-powershell-reference"></a>Windows PowerShell-referens

Windows PowerShell är en Microsoft .NET Framework-anslutna miljö som är utformad för administrativa automation. Windows PowerShell innehåller en ny metod för att skapa kommandon, skapa lösningar och skapa grafiskt gränssnitt-baserade hanteringsverktyg.

Windows PowerShell kan en administratör att automatisera administrationen av systemresurser genom körning av kommandon antingen direkt eller via skript.

## <a name="developer-audience"></a>För utvecklare

Windows PowerShell Software Development Kit (SDK) är avsedd för utvecklare för kommandot som kräver information om API: er som tillhandahålls av Windows PowerShell. Kommandot utvecklare använda Windows PowerShell för att skapa både kommandon och leverantörer som utökar de uppgifter som kan utföras av Windows PowerShell.

## <a name="windows-powershell-resources"></a>Windows PowerShell-resurser

Förutom SDK: N för Windows PowerShell innehåller följande resurser mer information.

[Komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) ger en introduktion till Windows PowerShell: språk, cmdlets, providers och användningen av objekt.

[Skriva ett Windows PowerShell-modul](./module/writing-a-windows-powershell-module.md) innehåller exempel och information för administratörer, skript utvecklare och cmdlet-utvecklare som måste du paketera och distribuera sina Windows PowerShell-lösningar med hjälp av Windows PowerShell-moduler.

[Skriva en Windows PowerShell-Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) innehåller information och kodexempel för programchefer som designar cmdletar och för utvecklare som implementerar cmdlet-kod.

[Windows PowerShell-teamets blogg](https://blogs.msdn.microsoft.com/PowerShell/) den bästa resursen för utbildning från och samarbeta med andra Windows PowerShell-användare. Läs teambloggen för Windows PowerShell och sedan ansluta Windows PowerShell-användarforum (microsoft.public.windows.powershell). Använd Windows Live Search för att hitta andra Windows PowerShell-bloggar och resurser. Sedan, när du utvecklar din expertis aktivt dina idéer.

[PowerShell-modulwebbläsaren](/powershell/module/) ger de senaste versionerna av kommandoradsverktyget hjälpavsnitt.

## <a name="class-libraries"></a>Klassbibliotek

[System.Management.Automation](/dotnet/api/System.Management.Automation) det här namnområdet är rotnamnrymden för Windows PowerShell. Den innehåller klasser, uppräkningar och gränssnitt som krävs för att implementera anpassade cmdlets. I synnerhet de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klassen är basklassen klasser måste härledas från vilken alla cmdlet. Mer information om cmdlet: ar finns i.

[System.Management.Automation.Provider](/dotnet/api/System.Management.Automation.Provider) det här namnområdet innehåller klasser, uppräkningar och gränssnitt som krävs för att implementera en Windows PowerShell-providern. I synnerhet de [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klassen är basklassen providerklasser måste härledas från vilken alla Windows PowerShell.

[Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) det här namnområdet innehåller klasser för cmdlets och providers som implementeras av Windows PowerShell. På samma sätt kan vi rekommenderar att du skapar en *dittnamn*. Kommandon namnområde för cmdletar som du implementerar.

[System.Management.Automation.Host](/dotnet/api/System.Management.Automation.Host) det här namnområdet innehåller klasser, uppräkningar och gränssnitt som cmdlet: en använder för att definiera interaktionen mellan användare och Windows PowerShell.

[System.Management.Automation.Internal](/dotnet/api/System.Management.Automation.Internal) det här namnområdet innehåller basklasser som används av andra klasser i namnområdet. Till exempel den [System.Management.Automation.Internal.Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) klassen är basklass för den [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) klass.

[System.Management.Automation.Runspaces](/dotnet/api/System.Management.Automation.Runspaces) det här namnområdet innehåller klasser, uppräkningar och gränssnitt som används för att skapa ett Windows PowerShell-körningsutrymme. I det här sammanhanget är Windows PowerShell-körningsutrymmet det sammanhang där anropa en eller flera pipelines i Windows PowerShell cmdlets. Det vill säga fungerar cmdlets inom ramen för ett Windows PowerShell-körningsutrymme. Mer information aboutWindows PowerShell körningsutrymmen, se [Windows PowerShell-Körningsutrymmen](http://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9).
