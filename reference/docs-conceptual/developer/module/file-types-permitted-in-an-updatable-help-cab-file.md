---
title: Filtyper som tillåts i en uppdaterings bar CAB-fil | Microsoft Docs
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
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357507"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Filtyper som tillåts i en CAB-fil för uppdateringsbar hjälp

Det här avsnittet innehåller information om innehålls kraven för uppdaterings bara CAB-filer för hjälpfiler.

## <a name="updatable-help-cab-file-requirements"></a>Uppdaterings bara fil krav för CAB-filen

Okomprimerat innehåll i CAB-filen är begränsat till 1 GB som standard. För att kringgå den här gränsen måste användarna använda **Force** -parametern för cmdletarna [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .

För att garantera säkerheten för hjälpfiler som hämtas från Internet, kan en uppdaterings bar hjälp CAB-fil endast innehålla de filtyper som anges nedan. Cmdlet: en [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifierar alla filer mot hjälp avsnittets scheman. Om cmdleten `Update-Help` påträffar en fil som är ogiltig eller inte är en tillåten typ, installerar den inte den ogiltiga filen och slutar att installera filer från CAB-filen på användarens dator.

- XML-baserade hjälp avsnitt för cmdletar.

- XML-baserade hjälp avsnitt för skript och funktioner.

- XML-baserade hjälp avsnitt för Windows PowerShell-leverantörer.

- Textbaserade hjälp avsnitt, till exempel om ämnen.

[Uppdaterings hjälpen](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifierar innehållet i CAB-filen när den packar upp CAB-filen. Om `Update-Help` hittar icke-kompatibla filtyper i en uppdaterings bar CAB-fil, genererar den ett avslutande fel och stoppar åtgärden. Det installerar inte några hjälpfiler från CAB-filen, även de som är kompatibla med filtyper.