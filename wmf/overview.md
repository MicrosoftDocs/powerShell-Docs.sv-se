---
ms.date: 04/19/2019
keywords: WMF, powershell, inställning
title: Windows Management Framework (WMF)
ms.openlocfilehash: 6d25b4025bbc86f6be0e5c74db9f1fbe6705d816
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984328"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) ger ett konsekvent gränssnitt för Windows. WMF ger ett sömlöst sätt att hantera olika versioner av Windows-klienten och Windows Server. Installationspaket för WMF innehåller uppdateringar hanteringsfunktioner och är tillgängliga för äldre versioner av Windows.

Installation av WMF lägger till och/eller uppdaterar följande funktioner:

- Windows PowerShell
- Windows PowerShell Desired State Configuration (DSC)
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

|        Operativsystemversion         | [WMF 5.1][]  | WMF 5.0<br>*Support upphör* | [WMF 4.0][]  | [WMF 3.0][]  | [WMF 2.0][]  |
| --------------------------------------- | ------------ | --------------------------- | ------------ | ------------ | ------------ |
| Windows Server 2019                     | Levereras i box |                             |              |              |              |
| Windows Server 2016                     | Levereras i box |                             |              |              |              |
| Windows 10                              | Levereras i box | Levereras i box                |              |              |              |
| Windows Server 2012 R2                  | Ja          | Ja                         | Levereras i box |              |              |
| Windows 8.1                             | Ja          | Ja                         | Levereras i box |              |              |
| Windows Server 2012                     | Ja          | Ja                         | Ja          | Levereras i box |              |
| Windows 8<br>*Support upphör*           |              |                             |              | Levereras i box |              |
| Windows Server 2008 R2 SP1              | Ja          | Ja                         | Ja          | Ja          | Levereras i box |
| Windows 7 SP1                           | Ja          | Ja                         | Ja          | Ja          | Levereras i box |
| Windows Server 2008 SP2                 |              |                             |              | Ja          | Ja          |
| Windows Vista<br>*Support upphör*       |              |                             |              |              | Ja          |
| Windows Server 2003<br>*Support upphör* |              |                             |              |              | Ja          |
| Windows XP<br>*Support upphör*          |              |                             |              | Ja          | Ja          |

- **Levereras i rutan**: Funktionerna i den angivna versionen av WMF levererades i den angivna versionen av Windows klient- eller Windows Server.
- **Support upphör om**: De här produkterna stöds inte längre av Microsoft. Du måste uppgradera till en ny version som stöds. Mer information finns i den [Microsoft livscykelpolicy][] sidan.

> [!NOTE]
> Installationsprogrammet för WMF 5.0 är inte längre tillgängligt eller stöds. Den har ersatts av WMF 5.1.

[Microsoft livscykelpolicy]: https://support.microsoft.com/lifecycle
[WMF 5.1]: https://aka.ms/wmf51download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
