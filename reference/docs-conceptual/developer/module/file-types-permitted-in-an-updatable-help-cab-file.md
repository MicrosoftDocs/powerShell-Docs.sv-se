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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357507"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="04299-102">Filtyper som tillåts i en CAB-fil för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="04299-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="04299-103">Det här avsnittet innehåller information om innehålls kraven för uppdaterings bara CAB-filer för hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="04299-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="04299-104">Uppdaterings bara fil krav för CAB-filen</span><span class="sxs-lookup"><span data-stu-id="04299-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="04299-105">Okomprimerat innehåll i CAB-filen är begränsat till 1 GB som standard.</span><span class="sxs-lookup"><span data-stu-id="04299-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="04299-106">För att kringgå den här gränsen måste användarna använda **Force** -parametern för cmdletarna [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .</span><span class="sxs-lookup"><span data-stu-id="04299-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="04299-107">För att garantera säkerheten för hjälpfiler som hämtas från Internet, kan en uppdaterings bar hjälp CAB-fil endast innehålla de filtyper som anges nedan.</span><span class="sxs-lookup"><span data-stu-id="04299-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="04299-108">Cmdlet: en [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifierar alla filer mot hjälp avsnittets scheman.</span><span class="sxs-lookup"><span data-stu-id="04299-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="04299-109">Om `Update-Help` cmdlet påträffar en fil som är ogiltig eller inte är en tillåten typ, installerar den inte den ogiltiga filen och slutar att installera filer från CAB-filen på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="04299-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="04299-110">XML-baserade hjälp avsnitt för cmdletar.</span><span class="sxs-lookup"><span data-stu-id="04299-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="04299-111">XML-baserade hjälp avsnitt för skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="04299-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="04299-112">XML-baserade hjälp avsnitt för Windows PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="04299-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="04299-113">Textbaserade hjälp avsnitt, till exempel om ämnen.</span><span class="sxs-lookup"><span data-stu-id="04299-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="04299-114">[Uppdaterings hjälpen](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifierar innehållet i CAB-filen när den packar upp CAB-filen.</span><span class="sxs-lookup"><span data-stu-id="04299-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="04299-115">Om `Update-Help` hittar icke-kompatibla filtyper i en uppdaterings bar CAB-fil, genererar den ett avslutande fel och stoppar åtgärden.</span><span class="sxs-lookup"><span data-stu-id="04299-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="04299-116">Det installerar inte några hjälpfiler från CAB-filen, även de som är kompatibla med filtyper.</span><span class="sxs-lookup"><span data-stu-id="04299-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>