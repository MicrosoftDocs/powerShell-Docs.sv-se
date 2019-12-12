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
ms.openlocfilehash: 48b2b2b9ab2a39cf185ed54bcfa99d46562e13b6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356821"
---
# <a name="windows-powershell-reference"></a>Windows PowerShell-referens

Windows PowerShell är en Microsoft .NET Framework-ansluten miljö som är utformad för administrations automatisering. Windows PowerShell innehåller en ny metod för att skapa kommandon, skapa lösningar och skapa grafiska verktyg för användar gränssnitts hantering.

Med Windows PowerShell kan en system administratör automatisera administrationen av system resurser genom att köra kommandon antingen direkt eller genom skript.

## <a name="developer-audience"></a>Användare för utvecklare

Windows PowerShell Software Development Kit (SDK) är skrivet för kommando utvecklare som behöver referensinformation om de API: er som tillhandahålls av Windows PowerShell. Kommando utvecklare använder Windows PowerShell för att skapa både kommandon och providers som utökar de uppgifter som kan utföras av Windows PowerShell.

## <a name="windows-powershell-resources"></a>Windows PowerShell-resurser

Förutom Windows PowerShell SDK innehåller följande resurser mer information.

[Komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) Innehåller en introduktion till Windows PowerShell: språk, cmdlets, providers och användningen av-objekt.

[Skriva en Windows PowerShell-modul](./module/writing-a-windows-powershell-module.md) Innehåller information och exempel för administratörer, skript utvecklare och cmdlet-utvecklare som behöver paketera och distribuera sina Windows PowerShell-lösningar med hjälp av Windows PowerShell-moduler.

[Skriva en Windows PowerShell-cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) Innehåller information och kod exempel för program hanterare som utformar cmdlets och för utvecklare som implementerar cmdlet-kod.

[Windows PowerShell-teamets blogg](https://blogs.msdn.microsoft.com/PowerShell/) Den bästa resursen för att lära sig och samar beta med andra Windows PowerShell-användare. Läs Windows PowerShell-teamets blogg och gå sedan till forumet för Windows PowerShell-användare (Microsoft. offentlig. Windows. PowerShell). Använd Windows Live Search för att hitta andra Windows PowerShell-Bloggar och-resurser. När du utvecklar dina kunskaper kan du sedan utveckla dina idéer fritt.

[PowerShell-modulens webbläsare](/powershell/module/) Innehåller de senaste versionerna av kommando rads hjälp avsnitten.

## <a name="class-libraries"></a>Klass bibliotek

[System. Management. Automation](/dotnet/api/System.Management.Automation) det här namn området är rot namn området för Windows PowerShell. Den innehåller klasser, uppräkningar och gränssnitt som krävs för att implementera anpassade cmdletar. I synnerhet är klassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) Bask Lassen som alla cmdlet-klasser måste härledas från. Mer information om cmdlets finns i.

[System. Management. Automation. Provider](/dotnet/api/System.Management.Automation.Provider) denna namnrymd innehåller de klasser, uppräkningar och gränssnitt som krävs för att implementera en Windows PowerShell-Provider. I synnerhet är klassen [system. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) den basklass från vilken alla klasser för Windows PowerShell-leverantörer måste härledas.

[Microsoft. PowerShell. kommandon](/dotnet/api/Microsoft.PowerShell.Commands) denna namnrymd innehåller klasserna för de cmdlets och providers som implementeras av Windows PowerShell. På samma sätt rekommenderar vi att du skapar en *dittnamn*. Kommando namn området för de cmdlets som du implementerar.

[System. Management. Automation. Host](/dotnet/api/System.Management.Automation.Host) denna namnrymd innehåller de klasser, uppräkningar och gränssnitt som cmdleten använder för att definiera interaktionen mellan användaren och Windows PowerShell.

[System. Management. Automation. Internal](/dotnet/api/System.Management.Automation.Internal) det här namn området innehåller bas klasserna som används av andra namn områdes klasser. Klassen [system. Management. Automation. Internal. Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) är till exempel Bask Lassen för klassen [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .

[System. Management. Automation. körnings utrymmen](/dotnet/api/System.Management.Automation.Runspaces) denna namnrymd innehåller de klasser, uppräkningar och gränssnitt som används för att skapa en Windows PowerShell-körnings utrymme. I det här sammanhanget är Windows PowerShell-körnings utrymme kontexten där en eller flera Windows PowerShell-pipeliner anropar cmdletar. Det vill säga cmdlets fungerar inom ramen för en Windows PowerShell-körnings utrymme. Mer information aboutWindows PowerShell-körnings utrymmen finns i [Windows PowerShell körnings utrymmen](https://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9).
