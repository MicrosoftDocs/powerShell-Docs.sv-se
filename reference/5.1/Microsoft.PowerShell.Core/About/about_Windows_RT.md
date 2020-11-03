---
description: I artikeln förklaras begränsningar för Windows PowerShell 4,0 på Windows RT 8,1.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_rt?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_RT
ms.openlocfilehash: 323f06a7a0d8253417510503c1011ac02c20179f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271352"
---
# <a name="about-windows-rt"></a><span data-ttu-id="87f2e-104">Om Windows RT</span><span class="sxs-lookup"><span data-stu-id="87f2e-104">About Windows RT</span></span>

## <a name="short-description"></a><span data-ttu-id="87f2e-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="87f2e-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="87f2e-106">I artikeln förklaras begränsningar för Windows PowerShell 4,0 på Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="87f2e-106">Explains limitations of  Windows PowerShell 4.0 on Windows RT 8.1.</span></span>

## <a name="long-description"></a><span data-ttu-id="87f2e-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="87f2e-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="87f2e-108">Operativ systemet Windows RT 8,1 installeras på datorer och enheter (till exempel Microsoft Surface 2, där det är det operativ system som levereras med datorn) som använder sig av ARM-processorer (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="87f2e-108">The Windows RT 8.1 operating system is installed on computers and devices (such as Microsoft Surface 2, on which it is the operating system that ships with the computer) that use Advanced RISC Machine (ARM) processors.</span></span>

<span data-ttu-id="87f2e-109">Windows PowerShell 4,0 ingår i Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="87f2e-109">Windows PowerShell 4.0 is included in Windows RT 8.1.</span></span> <span data-ttu-id="87f2e-110">Alla cmdletar, providers och moduler, och de flesta skript som har utformats för Windows PowerShell 2,0 och senare versioner körs på Windows RT 8,1 utan ändringar.</span><span class="sxs-lookup"><span data-stu-id="87f2e-110">All cmdlets, providers, and modules, and most scripts designed for Windows PowerShell 2.0 and later releases run on Windows RT 8.1 without changes.</span></span>

<span data-ttu-id="87f2e-111">Eftersom Windows RT 8,1 inte innehåller alla Windows-funktioner fungerar vissa funktioner i Windows PowerShell annorlunda eller fungerar inte på Windows RT-baserade enheter.</span><span class="sxs-lookup"><span data-stu-id="87f2e-111">Because Windows RT 8.1 does not include all Windows features, some Windows PowerShell features work differently or do not work on Windows RT-based devices.</span></span> <span data-ttu-id="87f2e-112">I följande lista beskrivs skillnaderna.</span><span class="sxs-lookup"><span data-stu-id="87f2e-112">The following list explains the differences.</span></span>

- <span data-ttu-id="87f2e-113">Windows PowerShell ISE ingår inte i och kan inte köras på Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="87f2e-113">Windows PowerShell ISE is not included in and cannot run on Windows RT 8.1.</span></span>
  <span data-ttu-id="87f2e-114">Windows PowerShell ISE kräver Windows Presentation Foundation, som inte ingår i Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="87f2e-114">Windows PowerShell ISE requires Windows Presentation Foundation, which is not included in Windows RT 8.1.</span></span>

- <span data-ttu-id="87f2e-115">Windows PowerShell-fjärrkommunikation och WinRM-tjänsten är inaktiverade som standard.</span><span class="sxs-lookup"><span data-stu-id="87f2e-115">Windows PowerShell remoting and the WinRM service are disabled by default.</span></span>
  <span data-ttu-id="87f2e-116">Kör cmdleten Enable-PSRemoting om du vill aktivera fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="87f2e-116">To enable remoting, run the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="87f2e-117">Du kan också köra cmdleten Set-Service för att ställa in start typen för WinRM-tjänsten på automatisk eller automatisk (fördröjd start).</span><span class="sxs-lookup"><span data-stu-id="87f2e-117">Also, run the Set-Service cmdlet to set the startup type of the WinRM service to Automatic, or Automatic (Delayed Start).</span></span>

  <span data-ttu-id="87f2e-118">Fjärr kommunikation är inaktive rad, du kan använda Windows PowerShell-fjärrkommunikation för att köra kommandon på andra datorer, men andra datorer kan inte köra kommandon på Windows RT-enheten.</span><span class="sxs-lookup"><span data-stu-id="87f2e-118">While remoting is disabled, you can use Windows PowerShell remoting to run commands on other computers, but other computers cannot run commands on the Windows RT device.</span></span> <span data-ttu-id="87f2e-119">Även implicit fjärr kommunikation – det vill säga fjärr kommunikation som är inbyggd i en cmdlet eller ett skript, och som inte uttryckligen begärs med tillagda parametrar</span><span class="sxs-lookup"><span data-stu-id="87f2e-119">Also, implicit remoting - that is, remoting that is built in to a cmdlet or script, and not explicitly requested with added parameters</span></span>
  - <span data-ttu-id="87f2e-120">fungerar inte i Windows PowerShell som körs på Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="87f2e-120">does not work in Windows PowerShell running on Windows RT 8.1.</span></span>

- <span data-ttu-id="87f2e-121">Domänanslutna data behandling och Kerberos-autentisering stöds inte på Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="87f2e-121">Domain-joined computing and Kerberos authentication are not supported on Windows RT 8.1.</span></span> <span data-ttu-id="87f2e-122">Du kan inte använda Windows PowerShell för att lägga till eller hantera dessa funktioner.</span><span class="sxs-lookup"><span data-stu-id="87f2e-122">You cannot use Windows PowerShell to add or manage these features.</span></span>

- <span data-ttu-id="87f2e-123">Microsoft .NET Framework-klasser som inte stöds i Windows RT 8,1 stöds inte heller av Windows PowerShell på Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="87f2e-123">Microsoft .NET Framework classes that are not supported on Windows RT 8.1 are also not supported by Windows PowerShell on Windows RT 8.1.</span></span>

- <span data-ttu-id="87f2e-124">Transaktioner är inte aktiverade på Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="87f2e-124">Transactions are not enabled on Windows RT 8.1.</span></span> <span data-ttu-id="87f2e-125">Transaktions-cmdletar, till exempel start-och transaktions parametrar, t. ex. UseTransaction, fungerar inte som de ska.</span><span class="sxs-lookup"><span data-stu-id="87f2e-125">Transaction cmdlets, such as Start-Transaction, and transaction parameters, such as UseTransaction, do not work properly.</span></span>

- <span data-ttu-id="87f2e-126">Alla Windows PowerShell-sessioner på Windows RT 8,1-enheter använder språk läget ConstrainedLanguage.</span><span class="sxs-lookup"><span data-stu-id="87f2e-126">All Windows PowerShell sessions on Windows RT 8.1 devices use the ConstrainedLanguage language mode.</span></span> <span data-ttu-id="87f2e-127">ConstrainedLanguage-språkläget är en komponent till UMCI (User Mode Code Integrity).</span><span class="sxs-lookup"><span data-stu-id="87f2e-127">ConstrainedLanguage language mode is a companion to User Mode Code Integrity (UMCI).</span></span> <span data-ttu-id="87f2e-128">Den tillåter alla Windows-cmdlets och Windows PowerShell-språkelement, men begränsar typer för att säkerställa att användare inte kan använda Windows PowerShell för att kringgå eller bryta mot UMCI skydd.</span><span class="sxs-lookup"><span data-stu-id="87f2e-128">It permits all Windows cmdlets and Windows PowerShell language elements, but restricts types to ensure that users cannot use Windows PowerShell to circumvent or violate the UMCI protections.</span></span>

<span data-ttu-id="87f2e-129">Mer information om språk läge för ConstrainedLanguage finns i [about_Language_Modes](about_Language_Modes.md).</span><span class="sxs-lookup"><span data-stu-id="87f2e-129">For more information about ConstrainedLanguage language mode, see [about_Language_Modes](about_Language_Modes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="87f2e-130">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="87f2e-130">SEE ALSO</span></span>

[<span data-ttu-id="87f2e-131">about_Language_Modes</span><span class="sxs-lookup"><span data-stu-id="87f2e-131">about_Language_Modes</span></span>](about_Language_Modes.md)

[<span data-ttu-id="87f2e-132">about_Remote</span><span class="sxs-lookup"><span data-stu-id="87f2e-132">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="87f2e-133">about_Windows_PowerShell_ISE</span><span class="sxs-lookup"><span data-stu-id="87f2e-133">about_Windows_PowerShell_ISE</span></span>](about_Windows_PowerShell_ISE.md)
