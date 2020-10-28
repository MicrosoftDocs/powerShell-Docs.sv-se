---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa en Windows PowerShell-provider
description: Skapa en Windows PowerShell-provider
ms.openlocfilehash: 51f19bf0dfa5f976a5045ae1342730c8f22f695e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647483"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Skapa en Windows PowerShell-provider

I det här avsnittet beskrivs hur du skapar en Windows PowerShell-Provider. En Windows PowerShell-Provider kan övervägas på två sätt. Till användaren representerar providern en uppsättning lagrade data. Till exempel kan lagrade data vara metabasen Internet Information Services (IIS), Microsoft Windows-registret, Windows-filsystemet, Active Directory och de variabel-och alias data som lagras av Windows PowerShell.

I utvecklaren är Windows PowerShell-providern gränssnittet mellan användaren och de data som användaren behöver åtkomst till. I det här perspektivet har varje typ av provider som beskrivs i det här avsnittet stöd för en uppsättning specifika bas klasser och gränssnitt som gör att Windows PowerShell-körningsmiljön kan exponera vissa cmdlets för användaren på ett vanligt sätt.

## <a name="providers-provided-by-windows-powershell"></a>Providers från Windows PowerShell

Windows PowerShell innehåller flera providrar (till exempel fil Systems leverantören, register leverantören och Ali Aset Provider) som används för att komma åt kända data lager. Om du vill ha mer information om providern som tillhandahålls av Windows PowerShell använder du följande kommando för att komma åt onlinehjälpen:

**PS>Get-Help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Komma åt lagrade data med Windows PowerShell-sökvägar

Windows PowerShell-providers är tillgängliga för Windows PowerShell-körningsmiljön och för kommandon via programmering med hjälp av Windows PowerShell-sökvägar. De flesta av tiden används dessa sökvägar för att direkt komma åt data via providern. Vissa sökvägar kan dock matchas mot Provider – interna sökvägar som tillåter att en cmdlet använder icke-Windows PowerShell-API: er (Application Programming Interface) för att komma åt data. Mer information om hur Windows PowerShell-leverantörer fungerar i Windows PowerShell finns i [så här fungerar Windows PowerShell](/previous-versions/ms714658(v=vs.85)).

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Exponerar Provider-cmdletar med hjälp av Windows PowerShell-enheter

En Windows PowerShell-Provider visar sina cmdlets som stöds med hjälp av virtuella Windows PowerShell-enheter.
Windows PowerShell använder följande regler för en Windows PowerShell-enhet:

- Namnet på en enhet kan vara vilken alfanumerisk sekvens som helst.
- En enhet kan anges vid en giltig punkt på en sökväg, som kallas "rot".
- En enhet kan implementeras för alla lagrade data, inte bara fil systemet.
- Varje enhet behåller sin egen aktuella arbets plats, vilket gör att användaren kan behålla kontexten när de växlar mellan enheter.

## <a name="in-this-section"></a>I det här avsnittet

I följande tabell visas avsnitt som innehåller kod exempel som bygger på varandra. Från och med det andra avsnittet kan Basic Windows PowerShell-providern initieras och avinitieras av Windows PowerShell-körningsmiljön, nästa avsnitt lägger till funktioner för att komma åt data, nästa avsnitt lägger till funktioner för att ändra data (objekten i lagrade data) och så vidare.

|                                                    Avsnitt                                                    |                                                                                         Definition                                                                                          |
| ----------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Designa en Windows PowerShell-provider](./designing-your-windows-powershell-provider.md)               | I det här avsnittet beskrivs saker du bör tänka på innan du implementerar en Windows PowerShell-Provider. Den sammanfattar Windows PowerShell-providerns bas klasser och gränssnitt som används. |
| [Skapa en grundläggande Windows PowerShell-provider](./creating-a-basic-windows-powershell-provider.md)           | Det här avsnittet visar hur du skapar en Windows PowerShell-provider som gör det möjligt för Windows PowerShell-körningsmiljön att initiera och avinitiera providern.                                        |
| [Skapa en Windows PowerShell-enhetsprovider](./creating-a-windows-powershell-drive-provider.md)           | Det här avsnittet visar hur du skapar en Windows PowerShell-provider som ger användaren åtkomst till ett data lager via en Windows PowerShell-enhet.                                                |
| [Skapa en Windows PowerShell-objektprovider](./creating-a-windows-powershell-item-provider.md)             | Det här avsnittet visar hur du skapar en Windows PowerShell-provider som gör att användaren kan ändra objekten i ett data lager.                                                                  |
| [Skapa en Windows PowerShell-containerprovider](./creating-a-windows-powershell-container-provider.md)   | Det här avsnittet visar hur du skapar en Windows PowerShell-provider som gör att användaren kan arbeta i Multilayer-data lager.                                                                        |
| [Skapa en Windows PowerShell-navigeringsprovider](./creating-a-windows-powershell-navigation-provider.md) | Det här avsnittet visar hur du skapar en Windows PowerShell-provider som gör att användaren kan navigera i objekt i ett data lager på ett hierarkiskt sätt.                                           |
| [Skapa en Windows PowerShell-innehållsprovider](./creating-a-windows-powershell-content-provider.md)       | Det här avsnittet visar hur du skapar en Windows PowerShell-provider som gör att användaren kan ändra innehållet i objekt i ett data lager.                                                       |
| [Skapa en Windows PowerShell-egenskapsprovider](./creating-a-windows-powershell-property-provider.md)     | Det här avsnittet visar hur du skapar en Windows PowerShell-provider som gör att användaren kan ändra egenskaperna för objekt i ett data lager.                                                    |

## <a name="see-also"></a>Se även

[Så här fungerar Windows PowerShell](/previous-versions/ms714658(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)
