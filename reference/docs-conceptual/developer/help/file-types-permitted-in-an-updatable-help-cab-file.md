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
ms.openlocfilehash: 6e9e51a50226430465726d27874e02e98ee67672
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810864"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="458b9-102">Filtyper som tillåts i en CAB-fil för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="458b9-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="458b9-103">Det här avsnittet innehåller information om innehålls kraven för uppdaterings bara CAB-filer för hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="458b9-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="458b9-104">Uppdaterings bara fil krav för CAB-filen</span><span class="sxs-lookup"><span data-stu-id="458b9-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="458b9-105">Okomprimerat innehåll i CAB-filen är begränsat till 1 GB som standard.</span><span class="sxs-lookup"><span data-stu-id="458b9-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="458b9-106">För att kringgå den här gränsen måste användarna använda **Force** -parametern för cmdletarna [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .</span><span class="sxs-lookup"><span data-stu-id="458b9-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="458b9-107">För att garantera säkerheten för hjälpfiler som hämtas från Internet, kan en uppdaterings bar hjälp CAB-fil endast innehålla de filtyper som anges nedan.</span><span class="sxs-lookup"><span data-stu-id="458b9-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="458b9-108">Cmdlet: en [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifierar alla filer mot hjälp avsnittets scheman.</span><span class="sxs-lookup"><span data-stu-id="458b9-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="458b9-109">Om `Update-Help` cmdleten påträffar en fil som är ogiltig eller inte är en tillåten typ, installerar den inte den ogiltiga filen och slutar att installera filer från CAB-filen på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="458b9-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="458b9-110">XML-baserade hjälp avsnitt för cmdletar.</span><span class="sxs-lookup"><span data-stu-id="458b9-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="458b9-111">XML-baserade hjälp avsnitt för skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="458b9-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="458b9-112">XML-baserade hjälp avsnitt för Windows PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="458b9-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="458b9-113">Textbaserade hjälp avsnitt, till exempel om ämnen.</span><span class="sxs-lookup"><span data-stu-id="458b9-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="458b9-114">[Uppdaterings hjälpen](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifierar innehållet i CAB-filen när den packar upp CAB-filen.</span><span class="sxs-lookup"><span data-stu-id="458b9-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="458b9-115">Om `Update-Help` hittar icke-kompatibla filtyper i en uppdaterings bar CAB-fil, genererar den ett avslutande fel och stoppar åtgärden.</span><span class="sxs-lookup"><span data-stu-id="458b9-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="458b9-116">Det installerar inte några hjälpfiler från CAB-filen, även de som är kompatibla med filtyper.</span><span class="sxs-lookup"><span data-stu-id="458b9-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>
