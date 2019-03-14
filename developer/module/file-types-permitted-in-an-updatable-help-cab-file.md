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
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794254"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="6292d-102">Filtyper som tillåts i en CAB-fil för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="6292d-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="6292d-103">Detta avsnitt listar och beskriver innehåll för uppdateringsbar hjälp CAB-filer.</span><span class="sxs-lookup"><span data-stu-id="6292d-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="6292d-104">Krav för uppdateringsbar hjälp CAB-filen</span><span class="sxs-lookup"><span data-stu-id="6292d-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="6292d-105">Okomprimerade CAB-filinnehållet är begränsad till 1 GB som standard.</span><span class="sxs-lookup"><span data-stu-id="6292d-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="6292d-106">Om du vill kringgå den här gränsen, användarna behöver använda den **kraft** -parametern för den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdletar.</span><span class="sxs-lookup"><span data-stu-id="6292d-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="6292d-107">För att säkerställa säkerheten för hjälp med att filer som hämtas från Internet, kan en uppdateringsbar hjälp CAB-fil endast de filtyper som anges nedan.</span><span class="sxs-lookup"><span data-stu-id="6292d-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="6292d-108">Den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validerar alla filer mot hjälpavsnitt scheman.</span><span class="sxs-lookup"><span data-stu-id="6292d-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="6292d-109">Om den `Update-Help` cmdlet påträffar en fil som är ogiltig eller är inte en tillåten typ och installerar inte filen ogiltig stoppar installerar filer från CAB-fil på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="6292d-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="6292d-110">XML-baserade hjälpavsnitt för cmdlet: ar.</span><span class="sxs-lookup"><span data-stu-id="6292d-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="6292d-111">XML-baserade hjälpavsnitt för skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="6292d-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="6292d-112">XML-baserade hjälpavsnitt för Windows PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="6292d-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="6292d-113">Textbaserade hjälpavsnitt, till exempel om ämnen.</span><span class="sxs-lookup"><span data-stu-id="6292d-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="6292d-114">Den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifierar CAB-innehållet när det har packats upp rådgivningsnämnden för ändringar.</span><span class="sxs-lookup"><span data-stu-id="6292d-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="6292d-115">Om `Update-Help` söker efter inkompatibla filtyper i en uppdateringsbar hjälp CAB-fil, genererar ett avslutande fel och åtgärden avbryts.</span><span class="sxs-lookup"><span data-stu-id="6292d-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="6292d-116">Den installerar inte alla hjälpfiler från rådgivningsnämnden för ändringar, även de filtyper som kompatibla.</span><span class="sxs-lookup"><span data-stu-id="6292d-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>