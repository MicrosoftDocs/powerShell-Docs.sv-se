---
ms.date: 06/12/2018
keywords: WMF, powershell, inställning
title: Windows Management Framework (WMF)
ms.openlocfilehash: 17011f88c364cb56a0c87f092873ccd99db450bc
ms.sourcegitcommit: 68093cc12a7a22c53d11ce7d33c18622921a0dd1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2018
ms.locfileid: "36940396"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) erbjuder ett konsekvent gränssnitt för Windows. WMF ger en sömlös sätt att hantera olika versioner av Windows-klienter och Windows Server. Installationspaket för WMF innehåller uppdateringar hanteringsfunktioner och är tillgängliga för äldre versioner av Windows.

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

|Operativsystemets Version  |[WMF 5.1][] |[WMF 5.0][] |[WMF 4.0][] |[WMF 3.0][]  |[WMF 2.0][] |
|--------------------------|------------|------------|------------|-------------|------------|
|Windows Server 2016       |Fartyg i rutan|            |            |             |            |
|Windows 10                |Fartyg i rutan|Fartyg i rutan|            |             |            |
|Windows Server 2012 R2    |Ja         |Ja         |Fartyg i rutan|             |            |
|Windows 8.1               |Ja         |Ja         |Fartyg i rutan|             |            |
|Windows Server 2012       |Ja         |Ja         |Ja         |Fartyg i rutan |            |
|Windows 8                 |            |            |            |Fartyg i rutan |            |
|Windows Server 2008 R2 SP1|Ja         |Ja         |Ja         |Ja          |Fartyg i rutan|
|Windows 7 SP1             |Ja         |Ja         |Ja         |Ja          |Fartyg i rutan|
|Windows Server 2008 SP2   |            |            |            |Ja          |Ja         |
|Windows Vista             |            |            |            |             |Ja         |
|Windows Server 2003       |            |            |            |             |Ja         |
|Windows XP                |            |            |            |Ja          |            |

**Levereras i rutan**: funktionerna i den angivna versionen av WMF levererades i den angivna versionen av windowsklient- eller Windows Server.

[WMF 5.1]: https://aka.ms/wmf51download
[WMF 5.0]: https://aka.ms/wmf5download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
