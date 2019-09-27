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
ms.openlocfilehash: ffbf8028ba2b52e77d8e22c061baa9b8b67f6da3
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323078"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Skapa en Windows PowerShell-provider

I det här avsnittet beskrivs hur du skapar en Windows PowerShell-Provider. En Windows PowerShell-Provider kan övervägas på två sätt. Till användaren representerar providern en uppsättning lagrade data. Till exempel kan lagrade data vara metabasen Internet Information Services (IIS), Microsoft Windows-registret, Windows-filsystemet, Active Directory och de variabel-och alias data som lagras av Windows PowerShell.

I utvecklaren är Windows PowerShell-providern gränssnittet mellan användaren och de data som användaren behöver åtkomst till. I det här perspektivet har varje typ av provider som beskrivs i det här avsnittet stöd för en uppsättning specifika bas klasser och gränssnitt som gör att Windows PowerShell-körningsmiljön kan exponera vissa cmdlets för användaren på ett vanligt sätt.

## <a name="providers-provided-by-windows-powershell"></a>Providers från Windows PowerShell

Windows PowerShell innehåller flera providrar (till exempel fil Systems leverantören, register leverantören och Ali Aset Provider) som används för att komma åt kända data lager. Om du vill ha mer information om providern som tillhandahålls av Windows PowerShell använder du följande kommando för att komma åt onlinehjälpen:

**PS > Get-Help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Komma åt lagrade data med Windows PowerShell-sökvägar

Windows PowerShell-providers är tillgängliga för Windows PowerShell-körningsmiljön och för kommandon via programmering med hjälp av Windows PowerShell-sökvägar. De flesta av tiden används dessa sökvägar för att direkt komma åt data via providern. Vissa sökvägar kan dock matchas mot Provider – interna sökvägar som tillåter att en cmdlet använder icke-Windows PowerShell-API: er (Application Programming Interface) för att komma åt data. Mer information om hur Windows PowerShell-leverantörer fungerar i Windows PowerShell finns i [så här fungerar Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Exponerar Provider-cmdletar med hjälp av Windows PowerShell-enheter

En Windows PowerShell-Provider visar sina cmdlets som stöds med hjälp av virtuella Windows PowerShell-enheter. Windows PowerShell använder följande regler för en Windows PowerShell-enhet:

- Namnet på en enhet kan vara vilken alfanumerisk sekvens som helst.

- En enhet kan anges vid en giltig punkt på en sökväg, som kallas "rot".

- En enhet kan implementeras för alla lagrade data, inte bara fil systemet.

- Varje enhet behåller sin egen aktuella arbets plats, vilket gör att användaren kan behålla kontexten när de växlar mellan enheter.

## <a name="in-this-section"></a>I detta avsnitt

I följande tabell visas avsnitt som innehåller kod exempel som bygger på varandra. Från och med det andra avsnittet kan Basic Windows PowerShell-providern initieras och avinitieras av Windows PowerShell-körningsmiljön, nästa avsnitt lägger till funktioner för att komma åt data, nästa avsnitt lägger till funktioner för att ändra data ( objekten i lagrade data) och så vidare.

|Avsnitt|Definition|
|-----------|----------------|
|[Designa din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)|I det här avsnittet beskrivs saker du bör tänka på innan du implementerar en Windows PowerShell-Provider. Den sammanfattar Windows PowerShell-providerns bas klasser och gränssnitt som används.|
|[Skapa en grundläggande Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md)|Det här avsnittet visar hur du skapar en Windows PowerShell-provider som gör det möjligt för Windows PowerShell-körningsmiljön att initiera och avinitiera providern.|
|[Skapa en Windows PowerShell-enhets leverantör](./creating-a-windows-powershell-drive-provider.md)|Det här avsnittet visar hur du skapar en Windows PowerShell-provider som ger användaren åtkomst till ett data lager via en Windows PowerShell-enhet.|
|[Skapa en Windows PowerShell-dataprovider](./creating-a-windows-powershell-item-provider.md)|Det här avsnittet visar hur du skapar en Windows PowerShell-provider som gör att användaren kan ändra objekten i ett data lager.|
|[Skapa en Windows PowerShell container-Provider](./creating-a-windows-powershell-container-provider.md)|Det här avsnittet visar hur du skapar en Windows PowerShell-provider som gör att användaren kan arbeta i Multilayer-data lager.|
|[Skapa en Windows PowerShell-navigerings leverantör](./creating-a-windows-powershell-navigation-provider.md)|Det här avsnittet visar hur du skapar en Windows PowerShell-provider som gör att användaren kan navigera i objekt i ett data lager på ett hierarkiskt sätt.|
|[Skapa en Windows PowerShell-innehålls leverantör](./creating-a-windows-powershell-content-provider.md)|Det här avsnittet visar hur du skapar en Windows PowerShell-provider som gör att användaren kan ändra innehållet i objekt i ett data lager.|
|[Skapa en Windows PowerShell-egenskaps leverantör](./creating-a-windows-powershell-property-provider.md)|Det här avsnittet visar hur du skapar en Windows PowerShell-provider som gör att användaren kan ändra egenskaperna för objekt i ett data lager.|

## <a name="see-also"></a>Se även

[Så här fungerar Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell Programmer ' s guide](./windows-powershell-programmer-s-guide.md)
