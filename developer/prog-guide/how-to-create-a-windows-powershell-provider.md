---
title: Så här skapar du en Windows PowerShell-Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: 286df63e75d6372cb41c974e60e79b02bd13686e
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429677"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Skapa en Windows PowerShell-provider

Det här avsnittet beskrivs hur du skapar en Windows PowerShell-providern. En Windows PowerShell-providern kan ses på två sätt. Providern representerar en uppsättning lagrade data för användaren. Lagrade data kan till exempel vara metabasen Internet Information Services (IIS), Microsoft Windows-registret, Windows-filsystem, Active Directory och variabeln och alias data som lagras av Windows PowerShell.

Utvecklare är Windows PowerShell-providern gränssnittet mellan användaren och de data som användaren behöver åtkomst till. Varje typ av provider som beskrivs i det här avsnittet stöder en uppsättning specifika basklasser och gränssnitt som gör att Windows PowerShell-körning för att exponera vissa cmdletar för användaren i ett vanligt sätt från det här perspektivet.

## <a name="providers-provided-by-windows-powershell"></a>Providers som tillhandahålls av Windows PowerShell

Windows PowerShell innehåller flera providers (till exempel filsystem-providern, registerprovidern och Alias provider) som används för att få åtkomst till kända datalager. Mer information om providers som tillhandahålls av Windows PowerShell använder du följande kommando till onlinehjälpen:

**PS > get-help about_provider**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Åtkomst till lagrade Data med hjälp av Windows PowerShell-sökvägar

Windows PowerShell-providers är tillgängliga att Windows PowerShell-runtime och kommandon via programmering genom att använda Windows PowerShell-sökvägar. I de flesta fall, används dessa sökvägar för direkt åtkomst till data via providern. Dock kan vissa sökvägar matchas till provider-interna sökvägar som gör att en cmdlet för att använda icke - Windows PowerShell programgränssnitt (API: er) för att komma åt data. Mer information om hur Windows PowerShell-leverantörer fungerar i Windows PowerShell finns i [hur Windows PowerShell fungerar](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Exponera med hjälp av Windows PowerShell Cmdlets för Provider-enheter

En Windows PowerShell-providern visar dess stöds cmdlet: ar med hjälp av virtuella Windows PowerShell-enheter. Windows PowerShell gäller följande regler för en Windows PowerShell-enhet:

- Namnet på en enhet kan vara valfri alfanumerisk ordning.

- En enhet kan anges när som helst giltig på en sökväg som kallas en ”rot”.

- En enhet kan implementeras för alla lagrade data, inte bara filsystemet.

- Varje enhet behåller sin egen aktuella arbetsplats tillåter användare att behålla kontext när man växlar mellan enheter.

## <a name="in-this-section"></a>I detta avsnitt

I följande tabell visar avsnitt som innehåller kodexempel som bygger på varandra. Från och med det andra avsnittet, grundläggande Windows PowerShell-providern kan initieras och ej initierad av Windows PowerShell-körningen, nästa avsnitt lägger till funktioner för att komma åt data, nästa avsnitt lägger till funktioner för att manipulera data ( objekten i lagrade data), och så vidare.

|Ämne|Definition|
|-----------|----------------|
|[Designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md)|Det här avsnittet beskrivs saker du bör tänka på innan du implementerar en Windows PowerShell-providern. Det sammanfattar de Windows PowerShell-providern basklasser och gränssnitt som används.|
|[Skapa en grundläggande Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md)|Det här avsnittet visar hur du skapar en Windows PowerShell-provider som tillåter Windows PowerShell-körning för att initiera och uninitialize providern.|
|[Skapa en Provider för Windows PowerShell-enhet](./creating-a-windows-powershell-drive-provider.md)|Det här avsnittet visar hur du skapar en Windows PowerShell-provider som tillåter att användaren kommer åt ett datalager genom en Windows PowerShell-enhet.|
|[Skapa en Provider för Windows PowerShell-objekt](./creating-a-windows-powershell-item-provider.md)|Det här avsnittet visar hur du skapar en Windows PowerShell-providern som används att manipulera objekt i ett datalager.|
|[Skapa en Windows PowerShell-providern för behållare](./creating-a-windows-powershell-container-provider.md)|Det här avsnittet visar hur du skapar en Windows PowerShell-providern som används att arbeta med flera lager datalager.|
|[Skapa en Windows PowerShell-providern för navigering](./creating-a-windows-powershell-navigation-provider.md)|Det här avsnittet visar hur du skapar en Windows PowerShell-provider som gör att användaren kan navigera objekten i ett datalager hierarkiskt.|
|[Skapa en Windows PowerShell-innehållsleverantör](./creating-a-windows-powershell-content-provider.md)|Det här avsnittet visar hur du skapar en Windows PowerShell-provider som gör att användaren kan ändra innehållet i objekt i ett datalager.|
|[Skapa en Provider för Windows PowerShell-egenskap](./creating-a-windows-powershell-property-provider.md)|Det här avsnittet visar hur du skapar en Windows PowerShell-provider som gör att användaren kan ändra egenskaperna för objekt i ett datalager.|

## <a name="see-also"></a>Se även

[Så här fungerar Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)