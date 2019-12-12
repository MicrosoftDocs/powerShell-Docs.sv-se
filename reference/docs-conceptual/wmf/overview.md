---
ms.date: 04/19/2019
keywords: WMF, powershell, inställning
title: Windows Management Framework (WMF)
ms.openlocfilehash: d581370fd602e03c86aa549eb8b273ff4d01b4e5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71145252"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) tillhandahåller ett konsekvent hanterings gränssnitt för Windows. WMF är ett smidigt sätt att hantera olika versioner av Windows-klienten och Windows Server. WMF Installer-paket innehåller uppdateringar av hanterings funktionerna och är tillgängliga för äldre versioner av Windows.

WMF-installationen lägger till och/eller uppdaterar följande funktioner:

- Windows PowerShell
- Önskad tillståndskonfiguration i Windows PowerShell
- Windows PowerShell ISE (Integrated Scripting Environment)
- Windows Remote Management (WinRM)
- Windows Management Instrumentation (WMI)
- Windows PowerShell-webbtjänster (hantering OData IIS-tillägg)
- Loggning av programvaruinventering (SIL)
- Serverhanteraren CIM-provider

## <a name="wmf-release-notes"></a>Versions anmärkningar för WMF

Om du vill veta mer om olika förbättringar i PowerShell och andra komponenter i en specifik WMF, se länkarna nedan för att granska viktig information:

- [WMF 5.1](whats-new/release-notes.md#wmf-51-changes)
- [WMF 5.0](whats-new/release-notes.md#wmf-50-changes)
- [WMF 4,0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3,0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>WMF-tillgänglighet över Windows-operativsystem

|        Operativsystemversion         | [WMF 5.1][]  | WMF 5.0<br>*Stöds inte* | [WMF 4,0][]  | [WMF 3,0][]  | [WMF 2,0][]  |
| --------------------------------------- | ------------ | --------------------------- | ------------ | ------------ | ------------ |
| Windows Server 2019                     | Box-inlevereras |                             |              |              |              |
| Windows Server 2016                     | Box-inlevereras |                             |              |              |              |
| Windows 10                              | Box-inlevereras | Box-inlevereras                |              |              |              |
| Windows Server 2012 R2                  | Ja          | Ja                         | Box-inlevereras |              |              |
| Windows 8.1                             | Ja          | Ja                         | Box-inlevereras |              |              |
| Windows Server 2012                     | Ja          | Ja                         | Ja          | Box-inlevereras |              |
| Windows 8<br>*Stöds inte*           |              |                             |              | Box-inlevereras |              |
| Windows Server 2008 R2 SP1              | Ja          | Ja                         | Ja          | Ja          | Box-inlevereras |
| Windows 7 SP1                           | Ja          | Ja                         | Ja          | Ja          | Box-inlevereras |
| Windows Server 2008 SP2                 |              |                             |              | Ja          | Ja          |
| Windows Vista<br>*Stöds inte*       |              |                             |              |              | Ja          |
| Windows Server 2003<br>*Stöds inte* |              |                             |              |              | Ja          |
| Windows XP<br>*Stöds inte*          |              |                             |              | Ja          | Ja          |

- **Levereras i Box**: funktionerna i den angivna versionen av WMF levererades i den angivna versionen av Windows-klienten eller Windows Server.
- **Out-of-support**: de här produkterna stöds inte längre av Microsoft. Du måste uppgradera till en ny version som stöds. Mer information finns på sidan [Microsofts livs cykel princip][] .

> [!NOTE]
> Installations programmet för WMF 5,0 är inte längre tillgängligt eller stöds inte längre. Den har ersatts av WMF 5,1.

[Microsofts livs cykel princip]: https://support.microsoft.com/lifecycle
[WMF 5.1]: https://aka.ms/wmf51download
[WMF 4,0]: https://aka.ms/wmf4download
[WMF 3,0]: https://aka.ms/wmf3download
[WMF 2,0]: https://aka.ms/wmf2download
