---
title: Filtyper som tillåts i en uppdateringsbar hjälp CAB-fil | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 931383858c0b83f0a9a66026c215e16481b89e9e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851599"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Filtyper som tillåts i en CAB-fil för uppdateringsbar hjälp

Detta avsnitt listar och beskriver innehåll för uppdateringsbar hjälp CAB-filer.

## <a name="updatable-help-cab-file-requirements"></a>Krav för uppdateringsbar hjälp CAB-filen

Okomprimerade CAB-filinnehållet är begränsad till 1 GB som standard. Om du vill kringgå den här gränsen, användarna behöver använda den **kraft** -parametern för den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdletar.
Okomprimerade CAB-filinnehållet är begränsad till 1 GB som standard. Om du vill kringgå den här gränsen, användarna behöver använda den **kraft** -parametern för den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdletar.

För att säkerställa säkerheten för hjälp med att filer som hämtas från Internet, kan en uppdateringsbar hjälp CAB-fil endast de filtyper som anges nedan. Den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validerar alla filer mot hjälpavsnitt scheman. Om den `Update-Help` cmdlet påträffar en fil som är ogiltig eller är inte en tillåten typ och installerar inte filen ogiltig stoppar installerar filer från CAB-fil på användarens dator.
För att säkerställa säkerheten för hjälp med att filer som hämtas från Internet, kan en uppdateringsbar hjälp CAB-fil endast de filtyper som anges nedan. Den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validerar alla filer mot hjälpavsnitt scheman. Om den `Update-Help` cmdlet påträffar en fil som är ogiltig eller är inte en tillåten typ och installerar inte filen ogiltig stoppar installerar filer från CAB-fil på användarens dator.

- XML-baserade hjälpavsnitt för cmdlet: ar.

- XML-baserade hjälpavsnitt för skript och funktioner.

- XML-baserade hjälpavsnitt för Windows PowerShell-leverantörer.

- Textbaserade hjälpavsnitt, till exempel om ämnen.

Den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifierar CAB-innehållet när det har packats upp rådgivningsnämnden för ändringar. Om `Update-Help` söker efter inkompatibla filtyper i en uppdateringsbar hjälp CAB-fil, genererar ett avslutande fel och åtgärden avbryts. Den installerar inte alla hjälpfiler från rådgivningsnämnden för ändringar, även de filtyper som kompatibla.
Den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifierar CAB-innehållet när det har packats upp rådgivningsnämnden för ändringar. Om `Update-Help` söker efter inkompatibla filtyper i en uppdateringsbar hjälp CAB-fil, genererar ett avslutande fel och åtgärden avbryts. Den installerar inte alla hjälpfiler från rådgivningsnämnden för ändringar, även de filtyper som kompatibla.