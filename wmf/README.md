---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Windows Management Framework (WMF)
ms.openlocfilehash: ae50e8d1495d7075163714ed873940d2d1d19b8e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) är leveransmekanismen som ger ett konsekvent gränssnitt mellan olika varianter av Windows och Windows Server.
Med installationen av WMF får kunder en sömlös sätt att samverka mellan kombinationer av operativsystem i sina miljöer.
WMF tillgängliggör uppdateringarna till hanteringsfunktioner i en viss version av Windows och Windows Server för installation på lägre versioner (normalt 2 lägre versioner) av Windows och Windows Server.

WMF installationen lägger till eller uppdaterar följande funktioner:

- Windows PowerShell
- Önskad tillståndskonfiguration i Windows PowerShell
- Windows PowerShell Integrated skript Environment (ISE)
- Windows Remote Management (WinRM)
- Windows Management Instrumentation (WMI)
- Windows PowerShell-webbtjänster (Management OData IIS Extension)
- Loggning av programvaruinventering (SIL)
- Serverhanteraren CIM-Provider

## <a name="wmf-release-notes"></a>WMF viktig information

Mer information om olika förbättringar i PowerShell och andra komponenter i en viss WMF, se länkarna nedan för att granska viktig information:

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>WMF tillgänglighet i Windows-operativsystem

| Operativsystemets Version | [WMF 5.1](https://aka.ms/wmf51download) | [WMF 5.0](https://aka.ms/wmf5download) | [WMF 4.0](https://aka.ms/wmf4download) |  [WMF 3.0](https://aka.ms/wmf3download) | [WMF 2.0](https://aka.ms/wmf2download) |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| Windows Server 2016 | Fartyg i rutan |  |  |  |  |
| Windows 10 | Fartyg i rutan | Fartyg i rutan  | | | |
| Windows Server 2012 R2| Ja | Ja | Fartyg i rutan |  |  |
| Windows 8.1 | Ja | Ja |  Fartyg i rutan |  |  |
| Windows Server 2012 | Ja | Ja | Ja |  Fartyg i rutan | |
| Windows 8 |  |  |  | Fartyg i rutan | |
| Windows Server 2008 R2 SP1 | Ja | Ja | Ja |  Ja| Fartyg i rutan |
| Windows 7 SP1  | Ja | Ja | Ja | Ja | Fartyg i rutan |
| Windows Server 2008 SP2 | | | | Ja | Ja |
| Windows Vista | | | | | Ja |
| Windows Server 2003| | | |  | Ja |
| Windows XP | | | |  | Ja |

**”Levereras i box”**: funktionerna i den `specified WMF` levererades i den angivna versionen av Windows och Windows Server.
Därför kan den `specified WMF` behöver inte installeras på de angivna operativsystemversionerna.
