---
title: Riktlinjer för rådgivande utveckling | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 871a74a084da3c7ec36767b7195461e0e7290cb9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056574"
---
# <a name="advisory-development-guidelines"></a><span data-ttu-id="14c2b-102">Rekommenderade riktlinjer för utveckling</span><span class="sxs-lookup"><span data-stu-id="14c2b-102">Advisory Development Guidelines</span></span>

<span data-ttu-id="14c2b-103">Det här avsnittet beskriver riktlinjer som du bör överväga för att säkerställa bra upplevelser för utveckling och användare.</span><span class="sxs-lookup"><span data-stu-id="14c2b-103">This section describes guidelines that you should consider to ensure good development and user experiences.</span></span> <span data-ttu-id="14c2b-104">Ibland kan de gäller, och ibland kan de inte.</span><span class="sxs-lookup"><span data-stu-id="14c2b-104">Sometimes they might apply, and sometimes they might not.</span></span>

## <a name="design-guidelines"></a><span data-ttu-id="14c2b-105">Designriktlinjer</span><span class="sxs-lookup"><span data-stu-id="14c2b-105">Design Guidelines</span></span>

- [<span data-ttu-id="14c2b-106">Stöd för en InputObject-Parameter (AD01)</span><span class="sxs-lookup"><span data-stu-id="14c2b-106">Support an InputObject Parameter (AD01)</span></span>](./advisory-development-guidelines.md#AD01)

- [<span data-ttu-id="14c2b-107">Stöd för parametern Force (AD02)</span><span class="sxs-lookup"><span data-stu-id="14c2b-107">Support the Force Parameter (AD02)</span></span>](./advisory-development-guidelines.md#AD02)

- [<span data-ttu-id="14c2b-108">Hantera autentiseringsuppgifter via Windows PowerShell (AD03)</span><span class="sxs-lookup"><span data-stu-id="14c2b-108">Handle Credentials Through Windows PowerShell (AD03)</span></span>](./advisory-development-guidelines.md#AD03)

- [<span data-ttu-id="14c2b-109">Stöd för kodning parametrar (AD04)</span><span class="sxs-lookup"><span data-stu-id="14c2b-109">Support Encoding Parameters (AD04)</span></span>](./advisory-development-guidelines.md#AD04)

- [<span data-ttu-id="14c2b-110">Test-cmdlet: ar ska returnera ett booleskt värde (AD05)</span><span class="sxs-lookup"><span data-stu-id="14c2b-110">Test Cmdlets Should Return a Boolean (AD05)</span></span>](./advisory-development-guidelines.md#AD05)

## <a name="code-guidelines"></a><span data-ttu-id="14c2b-111">Riktlinjer för kod</span><span class="sxs-lookup"><span data-stu-id="14c2b-111">Code Guidelines</span></span>

- [<span data-ttu-id="14c2b-112">Följ namnkonventioner för cmdlet: en klass (AC01)</span><span class="sxs-lookup"><span data-stu-id="14c2b-112">Follow Cmdlet Class Naming Conventions (AC01)</span></span>](./advisory-development-guidelines.md#AC01)

- [<span data-ttu-id="14c2b-113">Om inga indata från Pipeline åsidosätter metoden BeginProcessing (AC02)</span><span class="sxs-lookup"><span data-stu-id="14c2b-113">If No Pipeline Input Override the BeginProcessing Method (AC02)</span></span>](./advisory-development-guidelines.md#AC02)

- [<span data-ttu-id="14c2b-114">För att hantera åsidosätta stoppbegäran metoden StopProcessing (AC03)</span><span class="sxs-lookup"><span data-stu-id="14c2b-114">To Handle Stop Requests Override the StopProcessing Method (AC03)</span></span>](./advisory-development-guidelines.md#AC03)

- [<span data-ttu-id="14c2b-115">Implementera gränssnittet IDisposable (AC04)</span><span class="sxs-lookup"><span data-stu-id="14c2b-115">Implement the IDisposable Interface (AC04)</span></span>](./advisory-development-guidelines.md#AC04)

- [<span data-ttu-id="14c2b-116">Använda serialisering-vänlig parametertyper (AC05)</span><span class="sxs-lookup"><span data-stu-id="14c2b-116">Use Serialization-friendly Parameter Types (AC05)</span></span>](./advisory-development-guidelines.md#AC05)

- [<span data-ttu-id="14c2b-117">Använd SecureString för känsliga Data (AC06)</span><span class="sxs-lookup"><span data-stu-id="14c2b-117">Use SecureString for Sensitive Data (AC06)</span></span>](./advisory-development-guidelines.md#AC06)

## <a name="design-guidelines"></a><span data-ttu-id="14c2b-118">Designriktlinjer</span><span class="sxs-lookup"><span data-stu-id="14c2b-118">Design Guidelines</span></span>

<span data-ttu-id="14c2b-119">Följande riktlinjer bör övervägas när du utformar cmdletar.</span><span class="sxs-lookup"><span data-stu-id="14c2b-119">The following guidelines should be considered when designing cmdlets.</span></span> <span data-ttu-id="14c2b-120">När du har hittat en Design riktlinje som gäller för din situation bör du titta på koden riktlinjer för liknande riktlinjer.</span><span class="sxs-lookup"><span data-stu-id="14c2b-120">When you find a Design guideline that applies to your situation, be sure to look at the Code guidelines for similar guidelines.</span></span>

### <a name="support-an-inputobject-parameter-ad01"></a><span data-ttu-id="14c2b-121">Stöd för en InputObject-Parameter (AD01)</span><span class="sxs-lookup"><span data-stu-id="14c2b-121">Support an InputObject Parameter (AD01)</span></span>

<span data-ttu-id="14c2b-122">Eftersom Windows PowerShell fungerar direkt med Microsoft .NET Framework-objekt, finns ett .NET Framework-objekt ofta att exakt matchar typ du behöver utföra en viss åtgärd.</span><span class="sxs-lookup"><span data-stu-id="14c2b-122">Because Windows PowerShell works directly with Microsoft .NET Framework objects, a .NET Framework object is often available that exactly matches the type the user needs to perform a particular operation.</span></span> <span data-ttu-id="14c2b-123">`InputObject` är standardnamnet för en parameter som tar ett objekt som som indata.</span><span class="sxs-lookup"><span data-stu-id="14c2b-123">`InputObject` is the standard name for a parameter that takes such an object as input.</span></span> <span data-ttu-id="14c2b-124">Till exempel exemplet **stoppa Proc** cmdlet i den [StopProc självstudien](./stopproc-tutorial.md) definierar en `InputObject` parameter av typen Process som har stöd för indata från pipeline.</span><span class="sxs-lookup"><span data-stu-id="14c2b-124">For example, the sample **Stop-Proc** cmdlet in the [StopProc Tutorial](./stopproc-tutorial.md) defines an `InputObject` parameter of type Process that supports the input from the pipeline.</span></span> <span data-ttu-id="14c2b-125">Användaren kan få en uppsättning processen objekt, ändra dem för att välja exakt vilka objekt att stoppa och sedan skicka dem till den **stoppa Proc** cmdlet direkt.</span><span class="sxs-lookup"><span data-stu-id="14c2b-125">The user can get a set of process objects, manipulate them to select the exact objects to stop, and then pass them to the **Stop-Proc** cmdlet directly.</span></span>

### <a name="support-the-force-parameter-ad02"></a><span data-ttu-id="14c2b-126">Stöd för parametern Force (AD02)</span><span class="sxs-lookup"><span data-stu-id="14c2b-126">Support the Force Parameter (AD02)</span></span>

<span data-ttu-id="14c2b-127">Ibland kan måste en cmdlet skydda användaren från att utföra en begärd åtgärd.</span><span class="sxs-lookup"><span data-stu-id="14c2b-127">Occasionally, a cmdlet needs to protect the user from performing a requested operation.</span></span> <span data-ttu-id="14c2b-128">Ska ha stöd för sådana en cmdlet en `Force` parametern så att användaren att åsidosätta det skyddet om användaren har behörighet att utföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="14c2b-128">Such a cmdlet should support a `Force` parameter to allow the user to override that protection if the user has permissions to perform the operation.</span></span>

<span data-ttu-id="14c2b-129">Till exempel den [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet tar normalt inte bort en skrivskyddad fil.</span><span class="sxs-lookup"><span data-stu-id="14c2b-129">For example, the [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet does not normally remove a read-only file.</span></span> <span data-ttu-id="14c2b-130">Denna cmdlet stöder dock en `Force` parametern så att en användare kan Framtvinga borttagning av en skrivskyddad fil.</span><span class="sxs-lookup"><span data-stu-id="14c2b-130">However, this cmdlet supports a `Force` parameter so a user can force removal of a read-only file.</span></span> <span data-ttu-id="14c2b-131">Om användaren har redan behörighet att ändra attributet skrivskyddad och användaren tar bort filen, användning av den `Force` parametern förenklar igen.</span><span class="sxs-lookup"><span data-stu-id="14c2b-131">If the user already has permission to modify the read-only attribute, and the user removes the file, use of the `Force` parameter simplifies the operation.</span></span> <span data-ttu-id="14c2b-132">Men om användaren inte har behörighet att ta bort filen, den `Force` parametern har ingen effekt.</span><span class="sxs-lookup"><span data-stu-id="14c2b-132">However, if the user does not have permission to remove the file, the `Force` parameter has no effect.</span></span>

### <a name="handle-credentials-through-windows-powershell-ad03"></a><span data-ttu-id="14c2b-133">Hantera autentiseringsuppgifter via Windows PowerShell (AD03)</span><span class="sxs-lookup"><span data-stu-id="14c2b-133">Handle Credentials Through Windows PowerShell (AD03)</span></span>

<span data-ttu-id="14c2b-134">En cmdlet bör definiera en `Credential` parameter för att representera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="14c2b-134">A cmdlet should define a `Credential` parameter to represent credentials.</span></span> <span data-ttu-id="14c2b-135">Den här parametern måste vara av typen [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) och måste definieras med hjälp av en deklaration av autentiseringsuppgift attribut.</span><span class="sxs-lookup"><span data-stu-id="14c2b-135">This parameter must be of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) and must be defined using a Credential attribute declaration.</span></span> <span data-ttu-id="14c2b-136">Det här stödet meddelanderuta automatiskt för användarnamnet, lösenordet eller båda när en fullständig autentiseringsuppgift anges direkt.</span><span class="sxs-lookup"><span data-stu-id="14c2b-136">This support automatically prompts the user for the user name, for the password, or for both when a full credential is not supplied directly.</span></span> <span data-ttu-id="14c2b-137">Mer information om attributet autentiseringsuppgifter finns i [Credential attributet deklarationen](./credential-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="14c2b-137">For more information about the Credential attribute, see [Credential Attribute Declaration](./credential-attribute-declaration.md).</span></span>

### <a name="support-encoding-parameters-ad04"></a><span data-ttu-id="14c2b-138">Stöd för kodning parametrar (AD04)</span><span class="sxs-lookup"><span data-stu-id="14c2b-138">Support Encoding Parameters (AD04)</span></span>

<span data-ttu-id="14c2b-139">Om cmdlet: läser eller skriver ut text till eller från en binär form, till exempel skriva till eller läsa från en fil i ett filsystem har cmdlet: ha Encoding-parameter som anger hur texten är kodat i binär form.</span><span class="sxs-lookup"><span data-stu-id="14c2b-139">If your cmdlet reads or writes text to or from a binary form, such as writing to or reading from a file in a filesystem, then your cmdlet has to have Encoding parameter that specifies how the text is encoded in the binary form.</span></span>

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a><span data-ttu-id="14c2b-140">Test-cmdlet: ar ska returnera ett booleskt värde (AD05)</span><span class="sxs-lookup"><span data-stu-id="14c2b-140">Test Cmdlets Should Return a Boolean (AD05)</span></span>

<span data-ttu-id="14c2b-141">Cmdlet: ar som utför testerna mot sina resurser ska returnera en [System.Boolean](/dotnet/api/System.Boolean) skriver till pipelinen så att de kan användas i villkorsuttryck.</span><span class="sxs-lookup"><span data-stu-id="14c2b-141">Cmdlets that perform tests against their resources should return a [System.Boolean](/dotnet/api/System.Boolean) type to the pipeline so that they can be used in conditional expressions.</span></span>

## <a name="code-guidelines"></a><span data-ttu-id="14c2b-142">Riktlinjer för kod</span><span class="sxs-lookup"><span data-stu-id="14c2b-142">Code Guidelines</span></span>

<span data-ttu-id="14c2b-143">Följande riktlinjer bör övervägas när du skriver kod för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="14c2b-143">The following guidelines should be considered when writing cmdlet code.</span></span> <span data-ttu-id="14c2b-144">När du har hittat en riktlinje som gäller för din situation bör du titta på designriktlinjer för liknande riktlinjer.</span><span class="sxs-lookup"><span data-stu-id="14c2b-144">When you find a guideline that applies to your situation, be sure to look at the Design guidelines for similar guidelines.</span></span>

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a><span data-ttu-id="14c2b-145">Följ namnkonventioner för cmdlet: en klass (AC01)</span><span class="sxs-lookup"><span data-stu-id="14c2b-145">Follow Cmdlet Class Naming Conventions (AC01)</span></span>

<span data-ttu-id="14c2b-146">Du gör dina cmdlets enklare genom att följande namngivningsregler, och du hjälpa användaren förstå exakt vad cmdletarna som gör.</span><span class="sxs-lookup"><span data-stu-id="14c2b-146">By following standard naming conventions, you make your cmdlets more discoverable, and you help the user understand exactly what the cmdlets do.</span></span> <span data-ttu-id="14c2b-147">Den här metoden är särskilt viktigt för andra utvecklare som använder Windows PowerShell eftersom cmdlet: ar är offentliga typer.</span><span class="sxs-lookup"><span data-stu-id="14c2b-147">This practice is particularly important for other developers using Windows PowerShell because cmdlets are public types.</span></span>

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a><span data-ttu-id="14c2b-148">Definiera en Cmdlet i rätt Namespace</span><span class="sxs-lookup"><span data-stu-id="14c2b-148">Define a Cmdlet in the Correct Namespace</span></span>

<span data-ttu-id="14c2b-149">Du vanligtvis definierar klassen för en cmdlet i en .NET Framework-namnområde som lägger till ”. -Kommandon ”till namnområdet som representerar produkten där cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="14c2b-149">You normally define the class for a cmdlet in a .NET Framework namespace that appends ".Commands" to the namespace that represents the product in which the cmdlet runs.</span></span> <span data-ttu-id="14c2b-150">Till exempel cmdletar som ingår i Windows PowerShell har definierats i den `Microsoft.PowerShell.Commands` namnområde.</span><span class="sxs-lookup"><span data-stu-id="14c2b-150">For example, cmdlets that are included with Windows PowerShell are defined in the `Microsoft.PowerShell.Commands` namespace.</span></span>

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a><span data-ttu-id="14c2b-151">Namnge Cmdlet-klassen för att matcha Cmdlet-namn</span><span class="sxs-lookup"><span data-stu-id="14c2b-151">Name the Cmdlet Class to Match the Cmdlet Name</span></span>

<span data-ttu-id="14c2b-152">När du namnger .NET Framework-klass som implementerar en cmdlet, ge klassen namnet ”*\<Verb >**\<substantiv >**\<kommando >*”, där du ersätter  *\<Verb >* och  *\<substantiv >* platshållare med verb och substantiv som används för cmdlet-namn.</span><span class="sxs-lookup"><span data-stu-id="14c2b-152">When you name the .NET Framework class that implements a cmdlet, name the class "*\<Verb>**\<Noun>**\<Command>*", where you replace the *\<Verb>* and *\<Noun>* placeholders with the verb and noun used for the cmdlet name.</span></span> <span data-ttu-id="14c2b-153">Till exempel den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet implementeras av en klass med namnet `GetProcessCommand`.</span><span class="sxs-lookup"><span data-stu-id="14c2b-153">For example, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet is implemented by a class called `GetProcessCommand`.</span></span>

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a><span data-ttu-id="14c2b-154">Om inga indata från Pipeline åsidosätter metoden BeginProcessing (AC02)</span><span class="sxs-lookup"><span data-stu-id="14c2b-154">If No Pipeline Input Override the BeginProcessing Method (AC02)</span></span>

<span data-ttu-id="14c2b-155">Om din cmdlet inte tar emot indata från pipeline, bearbetning bör implementeras inom den [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metod.</span><span class="sxs-lookup"><span data-stu-id="14c2b-155">If your cmdlet does not accept input from the pipeline, processing should be implemented in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span> <span data-ttu-id="14c2b-156">Användning av den här metoden gör att Windows PowerShell för att underhålla sortering mellan cmdlets.</span><span class="sxs-lookup"><span data-stu-id="14c2b-156">Use of this method allows Windows PowerShell to maintain ordering between cmdlets.</span></span> <span data-ttu-id="14c2b-157">Den första cmdlet: i pipelinen returnerar alltid dess objekt innan de återstående cmdletarna i pipelinen prova att starta bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="14c2b-157">The first cmdlet in the pipeline always returns its objects before the remaining cmdlets in the pipeline get a chance to start their processing.</span></span>

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a><span data-ttu-id="14c2b-158">För att hantera åsidosätta stoppbegäran metoden StopProcessing (AC03)</span><span class="sxs-lookup"><span data-stu-id="14c2b-158">To Handle Stop Requests Override the StopProcessing Method (AC03)</span></span>

<span data-ttu-id="14c2b-159">Åsidosätta den [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) metod så att din cmdlet kan hantera stoppsignal.</span><span class="sxs-lookup"><span data-stu-id="14c2b-159">Override the [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) method so that your cmdlet can handle stop signal.</span></span> <span data-ttu-id="14c2b-160">Vissa cmdlets ta lång tid att slutföra deras funktion och de gör det lång tid skickar mellan anrop till Windows PowerShell-körning, till exempel när cmdleten blockerar tråd i tidskrävande RPC-anrop.</span><span class="sxs-lookup"><span data-stu-id="14c2b-160">Some cmdlets take a long time to complete their operation, and they let a long time pass between calls to the Windows PowerShell runtime, such as when the cmdlet blocks the thread in long-running RPC calls.</span></span> <span data-ttu-id="14c2b-161">Detta inkluderar cmdletar som göra anrop till den [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metod till den [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metoden och annan feedback mekanismer som kan ta lång tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="14c2b-161">This includes cmdlets that make calls to the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method, to the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, and to other feedback mechanisms that may take a long time to complete.</span></span> <span data-ttu-id="14c2b-162">För dessa fall kan användaren behöva skicka en stoppsignal till dessa cmdletar.</span><span class="sxs-lookup"><span data-stu-id="14c2b-162">For these cases the user might need to send a stop signal to these cmdlets.</span></span>

### <a name="implement-the-idisposable-interface-ac04"></a><span data-ttu-id="14c2b-163">Implementera gränssnittet IDisposable (AC04)</span><span class="sxs-lookup"><span data-stu-id="14c2b-163">Implement the IDisposable Interface (AC04)</span></span>

<span data-ttu-id="14c2b-164">Om din cmdlet har objekt som inte kasseras (skrivna till pipelinen) av den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoden cmdlet: kan kräva ytterligare objekt borttagning.</span><span class="sxs-lookup"><span data-stu-id="14c2b-164">If your cmdlet has objects that are not disposed of (written to the pipeline) by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, your cmdlet might require additional object disposal.</span></span> <span data-ttu-id="14c2b-165">Exempel: om cmdlet: öppnar en filreferens i dess [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metod och ser referensen öppna för användning av den [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoden, den här referensen har stängs i slutet av bearbetning.</span><span class="sxs-lookup"><span data-stu-id="14c2b-165">For example, if your cmdlet opens a file handle in its [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, this handle has to be closed at the end of processing.</span></span>

<span data-ttu-id="14c2b-166">Windows PowerShell-runtime anropar alltid inte den [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod.</span><span class="sxs-lookup"><span data-stu-id="14c2b-166">The Windows PowerShell runtime does not always call the  [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="14c2b-167">Till exempel den [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metoden kan inte anropas om cmdlet: en har avbrutits mitt via dess drift eller om avslutande fel uppstår i någon del av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="14c2b-167">For example, the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method might not be called if the cmdlet is canceled midway through its operation or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="14c2b-168">Därför .NET Framework-klass för en cmdlet som kräver att objektet rensningen ska implementera hela [System.IDisposable](/dotnet/api/System.IDisposable) gränssnittet mönstret, inklusive finaliserare, så att Windows PowerShell-runtime kan anropa både den [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) och [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) metoder i slutet av bearbetning.</span><span class="sxs-lookup"><span data-stu-id="14c2b-168">Therefore, the .NET Framework class for a cmdlet that requires object cleanup should implement the complete  [System.IDisposable](/dotnet/api/System.IDisposable) interface pattern, including the finalizer, so that the Windows PowerShell runtime can call both the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>

### <a name="use-serialization-friendly-parameter-types-ac05"></a><span data-ttu-id="14c2b-169">Använda serialisering-vänlig parametertyper (AC05)</span><span class="sxs-lookup"><span data-stu-id="14c2b-169">Use Serialization-friendly Parameter Types (AC05)</span></span>

<span data-ttu-id="14c2b-170">Om du vill kan du köra cmdlet: på fjärrdatorer, använda typer som kan enkelt serialiseras på klientdatorn och sedan extraheras på serverdatorn.</span><span class="sxs-lookup"><span data-stu-id="14c2b-170">To support running your cmdlet on remote computers, use types that can be easily serialized on the client computer and then rehydrated on the server computer.</span></span> <span data-ttu-id="14c2b-171">Följ typerna är serialisering-vänlig.</span><span class="sxs-lookup"><span data-stu-id="14c2b-171">The follow types are serialization-friendly.</span></span>

<span data-ttu-id="14c2b-172">Primitiva typer:</span><span class="sxs-lookup"><span data-stu-id="14c2b-172">Primitive types:</span></span>

- <span data-ttu-id="14c2b-173">Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32 och UInt64.</span><span class="sxs-lookup"><span data-stu-id="14c2b-173">Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32, and UInt64.</span></span>

- <span data-ttu-id="14c2b-174">Booleskt värde, Guid, Byte [], tidsintervall, DateTime, Uri och Version.</span><span class="sxs-lookup"><span data-stu-id="14c2b-174">Boolean, Guid, Byte[], TimeSpan, DateTime, Uri, and Version.</span></span>

- <span data-ttu-id="14c2b-175">Char, String, XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="14c2b-175">Char, String, XmlDocument.</span></span>

<span data-ttu-id="14c2b-176">Inbyggda rehydratable typer:</span><span class="sxs-lookup"><span data-stu-id="14c2b-176">Built-in rehydratable types:</span></span>

- <span data-ttu-id="14c2b-177">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="14c2b-177">PSPrimitiveDictionary</span></span>

- <span data-ttu-id="14c2b-178">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="14c2b-178">SwitchParameter</span></span>

- <span data-ttu-id="14c2b-179">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="14c2b-179">PSListModifier</span></span>

- <span data-ttu-id="14c2b-180">PSCredential</span><span class="sxs-lookup"><span data-stu-id="14c2b-180">PSCredential</span></span>

- <span data-ttu-id="14c2b-181">IPAddress, MailAddress</span><span class="sxs-lookup"><span data-stu-id="14c2b-181">IPAddress, MailAddress</span></span>

- <span data-ttu-id="14c2b-182">CultureInfo</span><span class="sxs-lookup"><span data-stu-id="14c2b-182">CultureInfo</span></span>

- <span data-ttu-id="14c2b-183">X509Certificate2, X500DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="14c2b-183">X509Certificate2, X500DistinguishedName</span></span>

- <span data-ttu-id="14c2b-184">DirectorySecurity, FileSecurity, RegistrySecurity</span><span class="sxs-lookup"><span data-stu-id="14c2b-184">DirectorySecurity, FileSecurity, RegistrySecurity</span></span>

<span data-ttu-id="14c2b-185">Andra typer:</span><span class="sxs-lookup"><span data-stu-id="14c2b-185">Other types:</span></span>

- <span data-ttu-id="14c2b-186">SecureString</span><span class="sxs-lookup"><span data-stu-id="14c2b-186">SecureString</span></span>

- <span data-ttu-id="14c2b-187">Behållare (listor och ordlistor av ovanstående typ.)</span><span class="sxs-lookup"><span data-stu-id="14c2b-187">Containers (lists and dictionaries of the above type)</span></span>

### <a name="use-securestring-for-sensitive-data-ac06"></a><span data-ttu-id="14c2b-188">Använd SecureString för känsliga Data (AC06)</span><span class="sxs-lookup"><span data-stu-id="14c2b-188">Use SecureString for Sensitive Data (AC06)</span></span>

<span data-ttu-id="14c2b-189">Vid hantering av känsliga data alltid använda den [System.Security.Securestring](/dotnet/api/System.Security.SecureString) datatyp.</span><span class="sxs-lookup"><span data-stu-id="14c2b-189">When handling sensitive data always use the [System.Security.Securestring](/dotnet/api/System.Security.SecureString) data type.</span></span> <span data-ttu-id="14c2b-190">Detta kan omfatta pipeline-indata till parametrar, samt returnera känsliga data till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="14c2b-190">This could include pipeline input to parameters, as well as returning sensitive data to the pipeline.</span></span>

## <a name="see-also"></a><span data-ttu-id="14c2b-191">Se även</span><span class="sxs-lookup"><span data-stu-id="14c2b-191">See Also</span></span>

[<span data-ttu-id="14c2b-192">Riktlinjer för nödvändiga utveckling</span><span class="sxs-lookup"><span data-stu-id="14c2b-192">Required Development Guidelines</span></span>](./required-development-guidelines.md)

[<span data-ttu-id="14c2b-193">Vi rekommenderar utveckling riktlinjer</span><span class="sxs-lookup"><span data-stu-id="14c2b-193">Strongly Encouraged Development Guidelines</span></span>](./strongly-encouraged-development-guidelines.md)

[<span data-ttu-id="14c2b-194">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="14c2b-194">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
