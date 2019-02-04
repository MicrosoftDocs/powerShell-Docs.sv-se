---
ms.date: 06/12/2018
keywords: WMF, powershell, inställning
title: Windows Management Framework (WMF)
ms.openlocfilehash: f279f975527dc198dd9b47ca1dc4258f54fafef5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684439"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) ger ett konsekvent gränssnitt för Windows. WMF ger ett sömlöst sätt att hantera olika versioner av Windows-klienten och Windows Server. Installationspaket för WMF innehåller uppdateringar hanteringsfunktioner och är tillgängliga för äldre versioner av Windows.

Installation av WMF lägger till och/eller uppdaterar följande funktioner:

- Windows PowerShell
- Önskad tillståndskonfiguration i Windows PowerShell
- Windows PowerShell integrerad skriptet Environment (ISE)
- Windows Remote Management (WinRM)
- Windows Management Instrumentation (WMI)
- Windows PowerShell-webbtjänster (Management OData IIS Extension)
- Loggning av programvaruinventering (SIL)
- Serverhanteraren CIM-Provider

## <a name="wmf-release-notes"></a>WMF viktig information

Mer information om flera förbättringar i PowerShell och andra komponenter i en viss WMF, se länkarna nedan om du vill granska viktig information:

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>WMF tillgänglighet över Windows-operativsystem

|Version av operativsystemet  |[WMF 5.1][] |[WMF 5.0][] |[WMF 4.0][] |[WMF 3.0][]  |[WMF 2.0][] |
|--------------------------|------------|------------|------------|-------------|------------|
|Windows Server 2019       |Levereras i box|            |            |             |            |
|Windows Server 2016       |Levereras i box|            |            |             |            |
|Windows 10                |Levereras i box|Levereras i box|            |             |            |
|Windows Server 2012 R2    |Ja         |Ja         |Levereras i box|             |            |
|Windows 8.1               |Ja         |Ja         |Levereras i box|             |            |
|Windows Server 2012       |Ja         |Ja         |Ja         |Levereras i box |            |
|Windows 8                 |            |            |            |Levereras i box |            |
|Windows Server 2008 R2 SP1|Ja         |Ja         |Ja         |Ja          |Levereras i box|
|Windows 7 SP1             |Ja         |Ja         |Ja         |Ja          |Levereras i box|
|Windows Server 2008 SP2   |            |            |            |Ja          |Ja         |
|Windows Vista             |            |            |            |             |Ja         |
|Windows Server 2003       |            |            |            |             |Ja         |
|Windows XP                |            |            |            |Ja          |            |

**Levereras i rutan**: Funktionerna i den angivna versionen av WMF levererades i den angivna versionen av Windows klient- eller Windows Server.

[WMF 5.1]: https://aka.ms/wmf51download
[WMF 5.0]: https://aka.ms/wmf5download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
