---
ms.date: 03/22/2012
ms.topic: reference
title: Filtyper som tillåts i en CAB-fil för uppdateringsbar hjälp
description: Filtyper som tillåts i en CAB-fil för uppdateringsbar hjälp
ms.openlocfilehash: bb69b8b89a9a3a5c8c00059ec404a4d41a5db9a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654733"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="a4ada-103">Filtyper som tillåts i en CAB-fil för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="a4ada-103">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="a4ada-104">Okomprimerat innehåll i CAB-filen är begränsat till 1 GB som standard.</span><span class="sxs-lookup"><span data-stu-id="a4ada-104">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="a4ada-105">För att kringgå den här gränsen måste användarna använda **Force** -parametern för cmdletarna [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .</span><span class="sxs-lookup"><span data-stu-id="a4ada-105">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="a4ada-106">För att garantera säkerheten för hjälpfiler som hämtas från Internet, kan en uppdaterings bar hjälp CAB-fil endast innehålla de filtyper som anges nedan.</span><span class="sxs-lookup"><span data-stu-id="a4ada-106">To assure the security of help files that are downloaded from the internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="a4ada-107">Cmdlet: en [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifierar alla filer mot hjälp avsnittets scheman.</span><span class="sxs-lookup"><span data-stu-id="a4ada-107">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="a4ada-108">Om `Update-Help` cmdleten påträffar en fil som är ogiltig eller inte är en tillåten typ, installerar den inte den ogiltiga filen och slutar att installera filer från CAB-filen på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="a4ada-108">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="a4ada-109">XML-baserade hjälp avsnitt för cmdletar.</span><span class="sxs-lookup"><span data-stu-id="a4ada-109">XML-based help topics for cmdlets.</span></span>
- <span data-ttu-id="a4ada-110">XML-baserade hjälp avsnitt för skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="a4ada-110">XML-based help topics for scripts and functions.</span></span>
- <span data-ttu-id="a4ada-111">XML-baserade hjälp avsnitt för PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="a4ada-111">XML-based help topics for PowerShell providers.</span></span>
- <span data-ttu-id="a4ada-112">Textbaserade hjälp avsnitt, till exempel om ämnen.</span><span class="sxs-lookup"><span data-stu-id="a4ada-112">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="a4ada-113">[Uppdaterings hjälpen](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifierar innehållet i CAB-filen när den packar upp CAB-filen.</span><span class="sxs-lookup"><span data-stu-id="a4ada-113">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="a4ada-114">Om `Update-Help` hittar icke-kompatibla filtyper i en uppdaterings bar CAB-fil, genererar den ett avslutande fel och stoppar åtgärden.</span><span class="sxs-lookup"><span data-stu-id="a4ada-114">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="a4ada-115">Det installerar inte några hjälpfiler från CAB-filen, även de som är kompatibla med filtyper.</span><span class="sxs-lookup"><span data-stu-id="a4ada-115">It does not install any help files from the CAB, even those of compliant file types.</span></span>
