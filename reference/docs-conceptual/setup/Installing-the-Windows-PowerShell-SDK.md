---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Installera Windows PowerShell SDK:n
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893546"
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="b0b32-103">Installera Windows PowerShell SDK:n</span><span class="sxs-lookup"><span data-stu-id="b0b32-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="b0b32-104">Följande avsnitt beskriver hur du installerar PowerShell SDK i olika versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="b0b32-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="b0b32-105">Installera Windows PowerShell 3.0 SDK för Windows 8 och Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="b0b32-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="b0b32-106">Windows PowerShell 3.0 installeras automatiskt med Windows 8 och Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="b0b32-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="b0b32-107">Dessutom kan du hämta och installera referenssammansättningar för Windows PowerShell 3.0 ingår i Windows 8 SDK.</span><span class="sxs-lookup"><span data-stu-id="b0b32-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="b0b32-108">Dessa sammansättningar kan du skriva cmdlets och providers värd program för Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="b0b32-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="b0b32-109">När du installerar Windows SDK för Windows 8, Windows PowerShell-sammansättningar installeras automatiskt i i mappen referens sammansättningen i `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.</span><span class="sxs-lookup"><span data-stu-id="b0b32-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.</span></span>
<span data-ttu-id="b0b32-110">Mer information finns i den [hämtningsplats för Windows 8 SDK](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).</span><span class="sxs-lookup"><span data-stu-id="b0b32-110">For more information, see the [Windows 8 SDK download site](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).</span></span>
<span data-ttu-id="b0b32-111">Kodexempel för Windows PowerShell är också tillgängliga på Development Center.</span><span class="sxs-lookup"><span data-stu-id="b0b32-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="b0b32-112">Mer information finns i exemplet för skrivbord teckentabellen på den [Dev center plats](https://code.msdn.microsoft.com:443/windowsdesktop/).</span><span class="sxs-lookup"><span data-stu-id="b0b32-112">For more information, see the Desktop code sample page on the [Dev center site](https://code.msdn.microsoft.com:443/windowsdesktop/).</span></span>

<span data-ttu-id="b0b32-113">Dessutom Windows PowerShell 3.0 är bakåtkompatibla med Windows PowerShell 2.0 SDK, som innehåller ett antal kodexempel.</span><span class="sxs-lookup"><span data-stu-id="b0b32-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="b0b32-114">Mer information om hur du hämtar Windows PowerShell 2.0 SDK finns nedan.</span><span class="sxs-lookup"><span data-stu-id="b0b32-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="b0b32-115">(Observera att du inte kan installera Windows PowerShell 2.0 på en Windows 8-plattformen 2.0 kodexemplen är kompatibelt med Windows 8 och Windows PowerShell 3.0,.)</span><span class="sxs-lookup"><span data-stu-id="b0b32-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="b0b32-116">Installera Windows PowerShell 3.0 SDK för Windows 7 och Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="b0b32-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="b0b32-117">Windows 7 och Windows Server 2008 R2 har automatiskt PowerShell 2.0 är installerat.</span><span class="sxs-lookup"><span data-stu-id="b0b32-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="b0b32-118">Dessutom kan du installera PowerShell 3.0 på dessa system.</span><span class="sxs-lookup"><span data-stu-id="b0b32-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="b0b32-119">(Mer information finns i [installera Windows PowerShell](Installing-Windows-PowerShell.md).).</span><span class="sxs-lookup"><span data-stu-id="b0b32-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="b0b32-120">Enligt beskrivningen ovan, kan du också installera Windows 8 SDK på Windows 7 och Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="b0b32-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="b0b32-121">Installera Windows PowerShell 2.0 SDK för Windows 7, Vista-, XP-, Server 2003- och Server 2008</span><span class="sxs-lookup"><span data-stu-id="b0b32-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="b0b32-122">Windows PowerShell 2.0 SDK innehåller referenssammansättningar som behövs för att skriva cmdlets och providers värdbaserade program och ger C# exempelkod som du kan använda som startpunkt när du börjar skriva kod.</span><span class="sxs-lookup"><span data-stu-id="b0b32-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="b0b32-123">Detta SDK Se [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560).</span><span class="sxs-lookup"><span data-stu-id="b0b32-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="b0b32-124">Referenssammansättningar</span><span class="sxs-lookup"><span data-stu-id="b0b32-124">Reference assemblies</span></span>

<span data-ttu-id="b0b32-125">Referenssammansättningar installeras på följande plats som standard: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span><span class="sxs-lookup"><span data-stu-id="b0b32-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> [!NOTE] 
> <span data-ttu-id="b0b32-126">Kod som kompileras mot Windows PowerShell 2.0-sammansättningar kan inte läsas in i Windows PowerShell 1.0-installationer.</span><span class="sxs-lookup"><span data-stu-id="b0b32-126">Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
> <span data-ttu-id="b0b32-127">Dock kan kod kompileras mot Windows PowerShell 1.0-sammansättningar läsas in i Windows PowerShell 2.0-installationer.</span><span class="sxs-lookup"><span data-stu-id="b0b32-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="b0b32-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="b0b32-128">Samples</span></span>

<span data-ttu-id="b0b32-129">Kodexempel som är installerade på följande plats som standard: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="b0b32-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="b0b32-130">Följande avsnitt innehåller en kort beskrivning av vad varje exempel gör.</span><span class="sxs-lookup"><span data-stu-id="b0b32-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="b0b32-131">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="b0b32-131">Cmdlet samples</span></span>

### <a name="getprocesssample01"></a><span data-ttu-id="b0b32-132">GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="b0b32-132">GetProcessSample01</span></span>

<span data-ttu-id="b0b32-133">Visar hur du skriver en enkel cmdlet som hämtar alla processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="b0b32-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

### <a name="getprocesssample02"></a><span data-ttu-id="b0b32-134">GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="b0b32-134">GetProcessSample02</span></span>

<span data-ttu-id="b0b32-135">Visar hur du lägger till parametrar till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b0b32-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="b0b32-136">Cmdlet: en tar en eller flera processnamn och returnerar de matchande processerna.</span><span class="sxs-lookup"><span data-stu-id="b0b32-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

### <a name="getprocesssample03"></a><span data-ttu-id="b0b32-137">GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="b0b32-137">GetProcessSample03</span></span>

<span data-ttu-id="b0b32-138">Visar hur du lägger till parametrar som accepterar indata från pipeline.</span><span class="sxs-lookup"><span data-stu-id="b0b32-138">Shows how to add parameters that accept input from the pipeline.</span></span>

### <a name="getprocesssample04"></a><span data-ttu-id="b0b32-139">GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="b0b32-139">GetProcessSample04</span></span>

<span data-ttu-id="b0b32-140">Visar hur du hanterar oändliga fel.</span><span class="sxs-lookup"><span data-stu-id="b0b32-140">Shows how to handle nonterminating errors.</span></span>

### <a name="getprocesssample05"></a><span data-ttu-id="b0b32-141">GetProcessSample05</span><span class="sxs-lookup"><span data-stu-id="b0b32-141">GetProcessSample05</span></span>

<span data-ttu-id="b0b32-142">Visar hur du vill visa en lista över angivna processer.</span><span class="sxs-lookup"><span data-stu-id="b0b32-142">Shows how to display a list of specified processes.</span></span>

### <a name="selectobject"></a><span data-ttu-id="b0b32-143">Markera objekt</span><span class="sxs-lookup"><span data-stu-id="b0b32-143">SelectObject</span></span>

<span data-ttu-id="b0b32-144">Visar hur du skriver ett filter för att välja endast vissa objekt.</span><span class="sxs-lookup"><span data-stu-id="b0b32-144">Shows how to write a filter to select only certain objects.</span></span>

### <a name="selectstring"></a><span data-ttu-id="b0b32-145">SelectString</span><span class="sxs-lookup"><span data-stu-id="b0b32-145">SelectString</span></span>

<span data-ttu-id="b0b32-146">Visar hur du söker efter filer för angivna mönster.</span><span class="sxs-lookup"><span data-stu-id="b0b32-146">Shows how to search files for specified patterns.</span></span>

### <a name="stopprocesssample01"></a><span data-ttu-id="b0b32-147">StopProcessSample01</span><span class="sxs-lookup"><span data-stu-id="b0b32-147">StopProcessSample01</span></span>

<span data-ttu-id="b0b32-148">Visar hur du implementerar en *PassThru* parameter och hur du begär Användarfeedback efter anrop till den [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) och [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) metoder.</span><span class="sxs-lookup"><span data-stu-id="b0b32-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) and [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) methods.</span></span>
<span data-ttu-id="b0b32-149">Användarna ange den *PassThru* parametern när de vill tvinga cmdlet för att returnera ett-objekt</span><span class="sxs-lookup"><span data-stu-id="b0b32-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

### <a name="stopprocesssample02"></a><span data-ttu-id="b0b32-150">StopProcessSample02</span><span class="sxs-lookup"><span data-stu-id="b0b32-150">StopProcessSample02</span></span>

<span data-ttu-id="b0b32-151">Visar hur du stoppar en särskild process.</span><span class="sxs-lookup"><span data-stu-id="b0b32-151">Shows how to stop a specific process.</span></span>

### <a name="stopprocesssample03"></a><span data-ttu-id="b0b32-152">StopProcessSample03</span><span class="sxs-lookup"><span data-stu-id="b0b32-152">StopProcessSample03</span></span>

<span data-ttu-id="b0b32-153">Visar hur du deklarera alias för parametrar och ge stöd för jokertecken.</span><span class="sxs-lookup"><span data-stu-id="b0b32-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

### <a name="stopprocesssample04"></a><span data-ttu-id="b0b32-154">StopProcessSample04</span><span class="sxs-lookup"><span data-stu-id="b0b32-154">StopProcessSample04</span></span>

<span data-ttu-id="b0b32-155">Visar hur du deklarera parameteruppsättningar det objekt som cmdlet: en tar som indata och hur du anger standardparametern inställd på att använda.</span><span class="sxs-lookup"><span data-stu-id="b0b32-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="b0b32-156">Fjärrkommunikation-exempel</span><span class="sxs-lookup"><span data-stu-id="b0b32-156">Remoting samples</span></span>

### <a name="remoterunspace01"></a><span data-ttu-id="b0b32-157">RemoteRunspace01</span><span class="sxs-lookup"><span data-stu-id="b0b32-157">RemoteRunspace01</span></span>

<span data-ttu-id="b0b32-158">Visar hur du skapar ett fjärrkörningsutrymme som används för att upprätta en fjärranslutning.</span><span class="sxs-lookup"><span data-stu-id="b0b32-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

### <a name="remoterunspacepool01"></a><span data-ttu-id="b0b32-159">RemoteRunspacePool01</span><span class="sxs-lookup"><span data-stu-id="b0b32-159">RemoteRunspacePool01</span></span>

<span data-ttu-id="b0b32-160">Visar hur du skapar poolen fjärrkörningsutrymme och hur du kör flera kommandon samtidigt med hjälp av den här poolen.</span><span class="sxs-lookup"><span data-stu-id="b0b32-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

### <a name="serialization01"></a><span data-ttu-id="b0b32-161">Serialization01</span><span class="sxs-lookup"><span data-stu-id="b0b32-161">Serialization01</span></span>

<span data-ttu-id="b0b32-162">Visar hur du tittar på en befintlig .NET-klass och se till att information från valda offentliga egenskaper för den här klassen bevaras i serialisering/deserialisering.</span><span class="sxs-lookup"><span data-stu-id="b0b32-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

### <a name="serialization02"></a><span data-ttu-id="b0b32-163">Serialization02</span><span class="sxs-lookup"><span data-stu-id="b0b32-163">Serialization02</span></span>

<span data-ttu-id="b0b32-164">Visar hur du tittar på en befintlig .NET-klass och se till att information från instans av den här klassen bevaras i serialisering/deserialisering när informationen inte är tillgänglig i offentliga egenskaper i klassen.</span><span class="sxs-lookup"><span data-stu-id="b0b32-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

### <a name="serialization03"></a><span data-ttu-id="b0b32-165">Serialization03</span><span class="sxs-lookup"><span data-stu-id="b0b32-165">Serialization03</span></span>

<span data-ttu-id="b0b32-166">Visar hur du tittar på en befintlig .NET-klass och se till att instanser av den här klassen och härledda klasser avserialiseras (extraheras) till live .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="b0b32-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="b0b32-167">Händelse-exempel</span><span class="sxs-lookup"><span data-stu-id="b0b32-167">Event samples</span></span>

### <a name="event01"></a><span data-ttu-id="b0b32-168">Event01</span><span class="sxs-lookup"><span data-stu-id="b0b32-168">Event01</span></span>

<span data-ttu-id="b0b32-169">Visar hur du skapar en cmdlet för Händelseregistrering med som härleds från ObjectEventRegistrationBase.</span><span class="sxs-lookup"><span data-stu-id="b0b32-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

### <a name="event02"></a><span data-ttu-id="b0b32-170">Event02</span><span class="sxs-lookup"><span data-stu-id="b0b32-170">Event02</span></span>

<span data-ttu-id="b0b32-171">Visar hur du visar hur du får meddelanden om Windows PowerShell-händelser som genereras på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="b0b32-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="b0b32-172">Den använder händelsen PSEventReceived exponeras via den [Körningsutrymme](/dotnet/api/system.management.automation.runspaces.runspace) klass.</span><span class="sxs-lookup"><span data-stu-id="b0b32-172">It uses the PSEventReceived event exposed through the [Runspace](/dotnet/api/system.management.automation.runspaces.runspace) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="b0b32-173">Som är värd för program-exempel</span><span class="sxs-lookup"><span data-stu-id="b0b32-173">Hosting application samples</span></span>

### <a name="runspace01"></a><span data-ttu-id="b0b32-174">Runspace01</span><span class="sxs-lookup"><span data-stu-id="b0b32-174">Runspace01</span></span>

<span data-ttu-id="b0b32-175">Visar hur du använder den [PowerShell](/dotnet/api/system.management.automation.powershell) klassen för att köra den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synkront.</span><span class="sxs-lookup"><span data-stu-id="b0b32-175">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span>
<span data-ttu-id="b0b32-176">Den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returnerar [processen](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objekt för varje process som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="b0b32-176">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

### <a name="runspace02"></a><span data-ttu-id="b0b32-177">Runspace02</span><span class="sxs-lookup"><span data-stu-id="b0b32-177">Runspace02</span></span>

<span data-ttu-id="b0b32-178">Visar hur du använder den [PowerShell](/dotnet/api/system.management.automation.powershell) klassen för att köra den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) och [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdletar synkront.</span><span class="sxs-lookup"><span data-stu-id="b0b32-178">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span>
<span data-ttu-id="b0b32-179">Den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returnerar [processen](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objekt för varje process som körs på den lokala datorn och `Sort-Object` sorterar objekt baserat på deras [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) Egenskapen.</span><span class="sxs-lookup"><span data-stu-id="b0b32-179">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="b0b32-180">Resultatet av dessa kommandon visas med hjälp av en [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) kontroll.</span><span class="sxs-lookup"><span data-stu-id="b0b32-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

### <a name="runspace03"></a><span data-ttu-id="b0b32-181">Runspace03</span><span class="sxs-lookup"><span data-stu-id="b0b32-181">Runspace03</span></span>

<span data-ttu-id="b0b32-182">Visar hur du använder den [PowerShell](/dotnet/api/system.management.automation.powershell) klassen för att köra ett skript synkront och hur du hanterar icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="b0b32-182">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="b0b32-183">Skriptet tar emot en lista över processnamn och hämtar sedan dessa processer.</span><span class="sxs-lookup"><span data-stu-id="b0b32-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="b0b32-184">Resultatet av skriptet, inklusive eventuella icke-avslutande fel som genererades när du kör skriptet, visas i ett konsolfönster.</span><span class="sxs-lookup"><span data-stu-id="b0b32-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

### <a name="runspace04"></a><span data-ttu-id="b0b32-185">Runspace04</span><span class="sxs-lookup"><span data-stu-id="b0b32-185">Runspace04</span></span>

<span data-ttu-id="b0b32-186">Visar hur du använder den [PowerShell](/dotnet/api/system.management.automation.powershell) klassen för att köra kommandon, och hur du catch avslutande fel som kan uppkomma när du kör kommandona.</span><span class="sxs-lookup"><span data-stu-id="b0b32-186">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="b0b32-187">Två kommandon körs och det sista kommandot skickas ett argument för parametern som inte är giltig.</span><span class="sxs-lookup"><span data-stu-id="b0b32-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="b0b32-188">Därför kan inga objekt returneras och ett avslutande fel genereras.</span><span class="sxs-lookup"><span data-stu-id="b0b32-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

### <a name="runspace05"></a><span data-ttu-id="b0b32-189">Runspace05</span><span class="sxs-lookup"><span data-stu-id="b0b32-189">Runspace05</span></span>

<span data-ttu-id="b0b32-190">Visar hur du lägger till en snapin-modul till en [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) objektet så att cmdleten av snapin-modulen är tillgänglig när körningsutrymmet öppnas.</span><span class="sxs-lookup"><span data-stu-id="b0b32-190">Shows how to add a snap-in to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="b0b32-191">Snapin-modulen innehåller en cmdlet Get-processen (definieras av den [GetProcessSample01 exempel](https://technet.microsoft.com/library/ff602028.aspx)) som körs synkront med hjälp av en [PowerShell](/dotnet/api/system.management.automation.powershell) objekt.</span><span class="sxs-lookup"><span data-stu-id="b0b32-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace06"></a><span data-ttu-id="b0b32-192">Runspace06</span><span class="sxs-lookup"><span data-stu-id="b0b32-192">Runspace06</span></span>

<span data-ttu-id="b0b32-193">Visar hur du lägger till en modul till en [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) objektet så att modulen läses in när körningsutrymmet öppnas.</span><span class="sxs-lookup"><span data-stu-id="b0b32-193">Shows how to add a module to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="b0b32-194">Modulen innehåller en cmdlet Get-processen (definieras av den [GetProcessSample02 exempel](https://technet.microsoft.com/library/ff602027.aspx)) som körs synkront med hjälp av en [PowerShell](/dotnet/api/system.management.automation.powershell) objekt.</span><span class="sxs-lookup"><span data-stu-id="b0b32-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace07"></a><span data-ttu-id="b0b32-195">Runspace07</span><span class="sxs-lookup"><span data-stu-id="b0b32-195">Runspace07</span></span>

<span data-ttu-id="b0b32-196">Visar hur du skapar ett körningsutrymme och sedan använda den körningsutrymme för körning synkront två cmdlet: ar med hjälp av en [PowerShell](/dotnet/api/system.management.automation.powershell) objekt.</span><span class="sxs-lookup"><span data-stu-id="b0b32-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace08"></a><span data-ttu-id="b0b32-197">Runspace08</span><span class="sxs-lookup"><span data-stu-id="b0b32-197">Runspace08</span></span>

<span data-ttu-id="b0b32-198">Visar hur du lägger till och argument till pipelinen för en [PowerShell](/dotnet/api/system.management.automation.powershell) objekt och hur du kör kommandona synkront.</span><span class="sxs-lookup"><span data-stu-id="b0b32-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the commands synchronously.</span></span>

### <a name="runspace09"></a><span data-ttu-id="b0b32-199">Runspace09</span><span class="sxs-lookup"><span data-stu-id="b0b32-199">Runspace09</span></span>

<span data-ttu-id="b0b32-200">Visar hur du lägger till ett skript till pipelinen för en [PowerShell](/dotnet/api/system.management.automation.powershell) objekt och hur du kör skriptet asynkront.</span><span class="sxs-lookup"><span data-stu-id="b0b32-200">Shows how to add a script to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="b0b32-201">Händelser används för att hantera utdata från skriptet.</span><span class="sxs-lookup"><span data-stu-id="b0b32-201">Events are used to handle the output of the script.</span></span>

### <a name="runspace10"></a><span data-ttu-id="b0b32-202">Runspace10</span><span class="sxs-lookup"><span data-stu-id="b0b32-202">Runspace10</span></span>

<span data-ttu-id="b0b32-203">Visar hur du skapar en standard inledande sessionstillstånd, hur du lägger till en cmdlet för att den [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), hur du skapar ett körningsutrymme som använder det första sessionstillståndet och hur du kör kommandot med hjälp av en [PowerShell](/dotnet/api/system.management.automation.powershell)objekt.</span><span class="sxs-lookup"><span data-stu-id="b0b32-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace11"></a><span data-ttu-id="b0b32-204">Runspace11</span><span class="sxs-lookup"><span data-stu-id="b0b32-204">Runspace11</span></span>

<span data-ttu-id="b0b32-205">Visar hur du använder den [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) klassen för att skapa en proxy-kommando som anropar en befintlig cmdlet, men begränsar uppsättningen av tillgängliga parametrar.</span><span class="sxs-lookup"><span data-stu-id="b0b32-205">Shows how to use the [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="b0b32-206">Kommandot proxy läggs sedan till en inledande sessionstillstånd som används för att skapa ett begränsat körningsutrymme.</span><span class="sxs-lookup"><span data-stu-id="b0b32-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="b0b32-207">Det innebär att användaren har åtkomst till funktionerna i cmdlet: en endast via kommandot proxy.</span><span class="sxs-lookup"><span data-stu-id="b0b32-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

### <a name="powershell01"></a><span data-ttu-id="b0b32-208">PowerShell01</span><span class="sxs-lookup"><span data-stu-id="b0b32-208">PowerShell01</span></span>

<span data-ttu-id="b0b32-209">Visar hur du skapar en begränsad körningsutrymme med hjälp av en [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) objekt.</span><span class="sxs-lookup"><span data-stu-id="b0b32-209">Shows how to create a constrained runspace using an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object.</span></span>

### <a name="powershell02"></a><span data-ttu-id="b0b32-210">PowerShell02</span><span class="sxs-lookup"><span data-stu-id="b0b32-210">PowerShell02</span></span>

<span data-ttu-id="b0b32-211">Visar hur du använder en körningsutrymme pool för att köra flera kommandon samtidigt.</span><span class="sxs-lookup"><span data-stu-id="b0b32-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="b0b32-212">Host-exempel</span><span class="sxs-lookup"><span data-stu-id="b0b32-212">Host samples</span></span>

### <a name="host01"></a><span data-ttu-id="b0b32-213">Host01</span><span class="sxs-lookup"><span data-stu-id="b0b32-213">Host01</span></span>

<span data-ttu-id="b0b32-214">Visar hur du implementerar ett program som använder en anpassad värd.</span><span class="sxs-lookup"><span data-stu-id="b0b32-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="b0b32-215">I det här exemplet skapas ett körningsutrymme som använder den anpassa värden, och sedan den [PowerShell](/dotnet/api/system.management.automation.powershell) API används för att köra ett skript som anropar ”avsluta”.</span><span class="sxs-lookup"><span data-stu-id="b0b32-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](/dotnet/api/system.management.automation.powershell) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="b0b32-216">Värdprogrammet sedan tittar på utdata från skriptet och skriver ut resultaten.</span><span class="sxs-lookup"><span data-stu-id="b0b32-216">The host application then looks at the output of the script and prints out the results.</span></span>

### <a name="host02"></a><span data-ttu-id="b0b32-217">Host02</span><span class="sxs-lookup"><span data-stu-id="b0b32-217">Host02</span></span>

<span data-ttu-id="b0b32-218">Lär dig skriva ett program som använder Windows PowerShell-runtime tillsammans med implementering av anpassade värden.</span><span class="sxs-lookup"><span data-stu-id="b0b32-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="b0b32-219">Värdprogrammet anger kulturen värden till tyska, körs den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet och visar resultat som du ser dem med hjälp av pwrsh.exe och sedan visar du aktuella datum och tidpunkt på tyska.</span><span class="sxs-lookup"><span data-stu-id="b0b32-219">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

### <a name="host03"></a><span data-ttu-id="b0b32-220">Host03</span><span class="sxs-lookup"><span data-stu-id="b0b32-220">Host03</span></span>

<span data-ttu-id="b0b32-221">Visar hur du skapar en interaktiv konsol-baserad värd-App som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen.</span><span class="sxs-lookup"><span data-stu-id="b0b32-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

### <a name="host04"></a><span data-ttu-id="b0b32-222">Host04</span><span class="sxs-lookup"><span data-stu-id="b0b32-222">Host04</span></span>

<span data-ttu-id="b0b32-223">Visar hur du skapar en interaktiv konsol-baserad värd-App som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen.</span><span class="sxs-lookup"><span data-stu-id="b0b32-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="b0b32-224">Den här värdprogrammet stöder också med frågor som används att ange flera val.</span><span class="sxs-lookup"><span data-stu-id="b0b32-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

### <a name="host05"></a><span data-ttu-id="b0b32-225">Host05</span><span class="sxs-lookup"><span data-stu-id="b0b32-225">Host05</span></span>

<span data-ttu-id="b0b32-226">Visar hur du skapar en interaktiv konsol-baserad värd-App som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen.</span><span class="sxs-lookup"><span data-stu-id="b0b32-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="b0b32-227">Den här värdprogrammet stöder också anrop till fjärrdatorer med hjälp av den [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) och [avsluta-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdletar.</span><span class="sxs-lookup"><span data-stu-id="b0b32-227">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets.</span></span>

### <a name="host06"></a><span data-ttu-id="b0b32-228">Host06</span><span class="sxs-lookup"><span data-stu-id="b0b32-228">Host06</span></span>

<span data-ttu-id="b0b32-229">Visar hur du skapar en interaktiv konsol-baserad värd-App som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen.</span><span class="sxs-lookup"><span data-stu-id="b0b32-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="b0b32-230">Det här exemplet använder dessutom Tokenizer-API: er för att ange färgen på texten som anges av användaren.</span><span class="sxs-lookup"><span data-stu-id="b0b32-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="b0b32-231">Provider-exempel</span><span class="sxs-lookup"><span data-stu-id="b0b32-231">Provider samples</span></span>

### <a name="accessdbprovidersample01"></a><span data-ttu-id="b0b32-232">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="b0b32-232">AccessDBProviderSample01</span></span>

<span data-ttu-id="b0b32-233">Visar hur du deklarera en providerklass som härleds direkt från den [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) klass.</span><span class="sxs-lookup"><span data-stu-id="b0b32-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) class.</span></span>
<span data-ttu-id="b0b32-234">Det är här ingår endast för fullständighetens skull.</span><span class="sxs-lookup"><span data-stu-id="b0b32-234">It is included here only for completeness.</span></span>

### <a name="accessdbprovidersample02"></a><span data-ttu-id="b0b32-235">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="b0b32-235">AccessDBProviderSample02</span></span>

<span data-ttu-id="b0b32-236">Visar hur du skriva över den [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) och [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) metoder som stöder anrop till den `New-PSDrive` och `Remove-PSDrive` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="b0b32-236">Shows how to overwrite the [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) and [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span>
<span data-ttu-id="b0b32-237">Providerklass i det här exemplet kommer från den [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) klass.</span><span class="sxs-lookup"><span data-stu-id="b0b32-237">The provider class in this sample derives from the [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) class.</span></span>

### <a name="accessdbprovidersample03"></a><span data-ttu-id="b0b32-238">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="b0b32-238">AccessDBProviderSample03</span></span>

<span data-ttu-id="b0b32-239">Visar hur du skriva över den [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) och [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) metoder som stöder anrop till den `Get-Item` och `Set-Item` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="b0b32-239">Shows how to overwrite the [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) and [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span>
<span data-ttu-id="b0b32-240">Providerklass i det här exemplet kommer från den [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) klass.</span><span class="sxs-lookup"><span data-stu-id="b0b32-240">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample04"></a><span data-ttu-id="b0b32-241">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="b0b32-241">AccessDBProviderSample04</span></span>

<span data-ttu-id="b0b32-242">Visar hur du skriver över behållare metoder för att stödja anrop till den `Copy-Item`, `Get-ChildItem`, `New-Item`, och `Remove-Item` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="b0b32-242">Shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span>
<span data-ttu-id="b0b32-243">Dessa metoder bör implementeras när datalagret innehåller objekt som är behållare.</span><span class="sxs-lookup"><span data-stu-id="b0b32-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="b0b32-244">En behållare är en grupp med underordnade objekt under en gemensam överordnad artikel.</span><span class="sxs-lookup"><span data-stu-id="b0b32-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="b0b32-245">Providerklass i det här exemplet kommer från den [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) klass.</span><span class="sxs-lookup"><span data-stu-id="b0b32-245">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample05"></a><span data-ttu-id="b0b32-246">AccessDBProviderSample05</span><span class="sxs-lookup"><span data-stu-id="b0b32-246">AccessDBProviderSample05</span></span>

<span data-ttu-id="b0b32-247">Visar hur du skriver över behållare metoder för att stödja anrop till den `Move-Item` och `Join-Path` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="b0b32-247">Shows how to overwrite container methods to support calls to the `Move-Item` and `Join-Path` cmdlets.</span></span>
<span data-ttu-id="b0b32-248">Dessa metoder bör implementeras när användaren behöver för att flytta objekt i en behållare och om datalagret innehåller kapslade behållare.</span><span class="sxs-lookup"><span data-stu-id="b0b32-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="b0b32-249">Providerklass i det här exemplet kommer från den [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) klass.</span><span class="sxs-lookup"><span data-stu-id="b0b32-249">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample06"></a><span data-ttu-id="b0b32-250">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="b0b32-250">AccessDBProviderSample06</span></span>

<span data-ttu-id="b0b32-251">Visar hur du skriva över innehållet metoder för att stödja anrop till den `Clear-Content`, `Get-Content`, och `Set-Content` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="b0b32-251">Shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span>
<span data-ttu-id="b0b32-252">Dessa metoder bör implementeras när användaren behöver för att hantera innehåll över hur objekten i datalagret.</span><span class="sxs-lookup"><span data-stu-id="b0b32-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="b0b32-253">Providerklass i det här exemplet kommer från den [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) klass och det implementerar den [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="b0b32-253">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class, and it implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>