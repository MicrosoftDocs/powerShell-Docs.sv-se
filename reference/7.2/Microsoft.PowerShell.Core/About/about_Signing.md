---
description: Förklarar hur du signerar skript så att de följer PowerShell-körnings principerna.
Locale: en-US
ms.date: 07/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_signing?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Signing
ms.openlocfilehash: cc38d7421bb5523a93d4c07d0f0106658184cfc5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710926"
---
# <a name="about-signing"></a><span data-ttu-id="9ad4a-103">Om signering</span><span class="sxs-lookup"><span data-stu-id="9ad4a-103">About Signing</span></span>

## <a name="short-description"></a><span data-ttu-id="9ad4a-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="9ad4a-104">Short description</span></span>
<span data-ttu-id="9ad4a-105">Förklarar hur du signerar skript så att de följer PowerShell-körnings principerna.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-105">Explains how to sign scripts so that they comply with the PowerShell execution policies.</span></span>

## <a name="long-description"></a><span data-ttu-id="9ad4a-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="9ad4a-106">Long description</span></span>

<span data-ttu-id="9ad4a-107">Principen för begränsade körningar tillåter inte att skript körs.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-107">The Restricted execution policy does not permit any scripts to run.</span></span> <span data-ttu-id="9ad4a-108">**AllSigned** -och **RemoteSigned** -körnings principerna förhindrar att PowerShell kör skript som inte har någon digital signatur.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-108">The **AllSigned** and **RemoteSigned** execution policies prevent PowerShell from running scripts that do not have a digital signature.</span></span>

<span data-ttu-id="9ad4a-109">I det här avsnittet beskrivs hur du kör valda skript som inte är signerade, även om körnings principen är **RemoteSigned** och hur du signerar skript för egen användning.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-109">This topic explains how to run selected scripts that are not signed, even while the execution policy is **RemoteSigned**, and how to sign scripts for your own use.</span></span>

<span data-ttu-id="9ad4a-110">Mer information om körnings principer för PowerShell finns i [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="9ad4a-110">For more information about PowerShell execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

## <a name="to-permit-signed-scripts-to-run"></a><span data-ttu-id="9ad4a-111">Tillåta att signerade skript körs</span><span class="sxs-lookup"><span data-stu-id="9ad4a-111">To permit signed scripts to run</span></span>

<span data-ttu-id="9ad4a-112">När du startar PowerShell på en dator för första gången är den **begränsade** körnings principen (standard) förmodligen aktiv.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-112">When you start PowerShell on a computer for the first time, the **Restricted** execution policy (the default) is likely to be in effect.</span></span>

<span data-ttu-id="9ad4a-113">Den **begränsade** principen tillåter inte att skript körs.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-113">The **Restricted** policy does not permit any scripts to run.</span></span>

<span data-ttu-id="9ad4a-114">Du hittar den effektiva körnings principen på datorn genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="9ad4a-114">To find the effective execution policy on your computer, type:</span></span>

```powershell
Get-ExecutionPolicy
```

<span data-ttu-id="9ad4a-115">Om du vill köra osignerade skript som du skriver på din lokala dator och signerade skript från andra användare, startar du PowerShell med alternativet Kör som administratör och använder sedan följande kommando för att ändra körnings principen på datorn till **RemoteSigned**:</span><span class="sxs-lookup"><span data-stu-id="9ad4a-115">To run unsigned scripts that you write on your local computer and signed scripts from other users, start PowerShell with the Run as Administrator option and then use the following command to change the execution policy on the computer to **RemoteSigned**:</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<span data-ttu-id="9ad4a-116">Mer information finns i hjälp avsnittet för `Set-ExecutionPolicy` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-116">For more information, see the help topic for the `Set-ExecutionPolicy` cmdlet.</span></span>

## <a name="running-unsigned-scripts-using-the-remotesigned-execution-policy"></a><span data-ttu-id="9ad4a-117">Köra osignerade skript med körnings principen för RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="9ad4a-117">Running unsigned scripts using the RemoteSigned execution policy</span></span>

<span data-ttu-id="9ad4a-118">Om din PowerShell-körnings princip är **RemoteSigned** kör PowerShell inte osignerade skript som hämtas från Internet, inklusive osignerade skript som du får via e-post och snabb meddelande program.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-118">If your PowerShell execution policy is **RemoteSigned**, PowerShell will not run unsigned scripts that are downloaded from the internet, including unsigned scripts you receive through email and instant messaging programs.</span></span>

<span data-ttu-id="9ad4a-119">Om du försöker köra ett nedladdat skript visas följande fel meddelande i PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9ad4a-119">If you try to run a downloaded script, PowerShell displays the following error message:</span></span>

```Output
The file <file-name> cannot be loaded. The file <file-name> is not digitally
signed. The script will not execute on the system. Please see "Get-Help
about_Signing" for more details.
```

<span data-ttu-id="9ad4a-120">Innan du kör skriptet bör du granska koden för att vara säker på att du litar på den.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-120">Before you run the script, review the code to be sure that you trust it.</span></span>
<span data-ttu-id="9ad4a-121">Skript har samma resultat som alla körbara program.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-121">Scripts have the same effect as any executable program.</span></span>

<span data-ttu-id="9ad4a-122">Om du vill köra ett osignerat skript använder du Unblock-File-cmdleten eller så använder du följande procedur.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-122">To run an unsigned script, use the Unblock-File cmdlet or use the following procedure.</span></span>

1. <span data-ttu-id="9ad4a-123">Spara skript filen på datorn.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-123">Save the script file on your computer.</span></span>
2. <span data-ttu-id="9ad4a-124">Klicka på Start, klicka på den här datorn och leta upp den sparade skript filen.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-124">Click Start, click My Computer, and locate the saved script file.</span></span>
3. <span data-ttu-id="9ad4a-125">Högerklicka på skript filen och klicka sedan på egenskaper.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-125">Right-click the script file, and then click Properties.</span></span>
4. <span data-ttu-id="9ad4a-126">Klicka på avblockera.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-126">Click Unblock.</span></span>

<span data-ttu-id="9ad4a-127">Om ett skript som hämtades från Internet har signerats digitalt, men du ännu inte har valt att lita på utgivaren, visas följande meddelande i PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9ad4a-127">If a script that was downloaded from the internet is digitally signed, but you have not yet chosen to trust its publisher, PowerShell displays the following message:</span></span>

```Output
Do you want to run software from this untrusted publisher?
The file <file-name> is published by CN=<publisher-name>. This
publisher is not trusted on your system. Only run scripts
from trusted publishers.

[V] Never run  [D] Do not run  [R] Run once  [A] Always run
[?] Help (default is "D"):
```

<span data-ttu-id="9ad4a-128">Om du litar på utgivaren väljer du kör en gång eller kör alltid.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-128">If you trust the publisher, select "Run once" or "Always run."</span></span> <span data-ttu-id="9ad4a-129">Om du inte litar på utgivaren väljer du antingen "Kör aldrig" eller "kör inte".</span><span class="sxs-lookup"><span data-stu-id="9ad4a-129">If you do not trust the publisher, select either "Never run" or "Do not run."</span></span> <span data-ttu-id="9ad4a-130">Om du väljer "aldrig körning" eller "kör alltid" uppmanas du inte att göra det igen för den här utgivaren.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-130">If you select "Never run" or "Always run," PowerShell will not prompt you again for this publisher.</span></span>

## <a name="methods-of-signing-scripts"></a><span data-ttu-id="9ad4a-131">Metoder för signering av skript</span><span class="sxs-lookup"><span data-stu-id="9ad4a-131">Methods of signing scripts</span></span>

<span data-ttu-id="9ad4a-132">Du kan signera de skript som du skriver och skript som du hämtar från andra källor.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-132">You can sign the scripts that you write and the scripts that you obtain from other sources.</span></span> <span data-ttu-id="9ad4a-133">Innan du signerar ett skript kontrollerar du varje kommando för att kontrol lera att det är säkert att köra.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-133">Before you sign any script, examine each command to verify that it is safe to run.</span></span>

<span data-ttu-id="9ad4a-134">Bästa praxis om kod signering finns i [metod tips för kod signering](/previous-versions/windows/hardware/design/dn653556(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="9ad4a-134">For best practices about code signing, see [Code-Signing Best Practices](/previous-versions/windows/hardware/design/dn653556(v=vs.85)).</span></span>

<span data-ttu-id="9ad4a-135">Mer information om hur du signerar en skript fil finns i [set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature).</span><span class="sxs-lookup"><span data-stu-id="9ad4a-135">For more information about how to sign a script file, see [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature).</span></span>

<span data-ttu-id="9ad4a-136">`New-SelfSignedCertificate`Cmdleten, som introducerades i PKI-modulen i PowerShell 3,0, skapar ett självsignerat certifikat som är lämpligt för testning.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-136">The `New-SelfSignedCertificate` cmdlet, introduced in the PKI module in PowerShell 3.0, creates a self-signed certificate that is Appropriate for testing.</span></span> <span data-ttu-id="9ad4a-137">Mer information finns i hjälp avsnittet för New-SelfSignedCertificate-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-137">For more information, see the help topic for the New-SelfSignedCertificate cmdlet.</span></span>

<span data-ttu-id="9ad4a-138">Om du vill lägga till en digital signatur i ett skript måste du signera den med ett kod signerings certifikat.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-138">To add a digital signature to a script, you must sign it with a code signing certificate.</span></span> <span data-ttu-id="9ad4a-139">Två typer av certifikat är lämpliga för signering av en skript fil:</span><span class="sxs-lookup"><span data-stu-id="9ad4a-139">Two types of certificates are suitable for signing a script file:</span></span>

- <span data-ttu-id="9ad4a-140">Certifikat som har skapats av en certifikat utfärdare: för en avgift verifierar en offentlig certifikat utfärdare din identitet och ger dig ett kod signerings certifikat.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-140">Certificates that are created by a certification authority: For a fee, a public certification authority verifies your identity and gives you a code signing certificate.</span></span> <span data-ttu-id="9ad4a-141">När du köper ditt certifikat från en betrodd certifikat utfärdare kan du dela ditt skript med användare på andra datorer som kör Windows eftersom de andra datorerna litar på certifikat utfärdaren.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-141">When you purchase your certificate from a reputable certification authority, you are able to share your script with users on other computers that are running Windows because those other computers trust the certification authority.</span></span>

- <span data-ttu-id="9ad4a-142">Certifikat som du skapar: du kan skapa ett självsignerat certifikat för vilket datorn är den myndighet som skapar certifikatet.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-142">Certificates that you create: You can create a self-signed certificate for which your computer is the authority that creates the certificate.</span></span> <span data-ttu-id="9ad4a-143">Det här certifikatet är kostnads fritt och du kan skriva, signera och köra skript på din dator.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-143">This certificate is free of charge and enables you to write, sign, and run scripts on your computer.</span></span> <span data-ttu-id="9ad4a-144">Ett skript som signerats av ett självsignerat certifikat kommer dock inte att köras på andra datorer.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-144">However, a script signed by a self-signed certificate will not run on other computers.</span></span>

<span data-ttu-id="9ad4a-145">Normalt använder du bara ett självsignerat certifikat för att signera skript som du skriver för eget bruk och för att signera skript som du får från andra källor som du har kontrollerat är säkra.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-145">Typically, you would use a self-signed certificate only to sign scripts that you write for your own use and to sign scripts that you get from other sources that you have verified to be safe.</span></span> <span data-ttu-id="9ad4a-146">Det är inte lämpligt för skript som ska delas, även inom ett företag.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-146">It is not appropriate for scripts that will be shared, even within an enterprise.</span></span>

<span data-ttu-id="9ad4a-147">Om du skapar ett självsignerat certifikat måste du Aktivera starkt skydd av den privata nyckeln på ditt certifikat.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-147">If you create a self-signed certificate, be sure to enable strong private key protection on your certificate.</span></span> <span data-ttu-id="9ad4a-148">Detta förhindrar att skadliga program signerar skript åt dig.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-148">This prevents malicious programs from signing scripts on your behalf.</span></span> <span data-ttu-id="9ad4a-149">Anvisningarna finns i slutet av det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-149">The instructions are included at the end of this topic.</span></span>

## <a name="create-a-self-signed-certificate"></a><span data-ttu-id="9ad4a-150">Skapa ett självsignerat certifikat</span><span class="sxs-lookup"><span data-stu-id="9ad4a-150">Create a self-signed certificate</span></span>

<span data-ttu-id="9ad4a-151">Om du vill skapa ett självsignerat certifikat i använder du `New-SelfSignedCertificate` cmdleten i PKI-modulen.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-151">To create a self-signed certificate in use the `New-SelfSignedCertificate` cmdlet in the PKI module.</span></span> <span data-ttu-id="9ad4a-152">Den här modulen introduceras i PowerShell 3,0 och ingår i Windows 8 och Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-152">This module is introduced in PowerShell 3.0 and is included in Windows 8 and Windows Server 2012.</span></span> <span data-ttu-id="9ad4a-153">Mer information finns i hjälp avsnittet för `New-SelfSignedCertificate` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-153">For more information, see the help topic for the `New-SelfSignedCertificate` cmdlet.</span></span>

<span data-ttu-id="9ad4a-154">Om du vill skapa ett självsignerat certifikat i tidigare versioner av Windows använder du verktyget för att skapa certifikat `MakeCert.exe` .</span><span class="sxs-lookup"><span data-stu-id="9ad4a-154">To create a self-signed certificate in earlier versions of Windows, use the Certificate Creation tool `MakeCert.exe`.</span></span> <span data-ttu-id="9ad4a-155">Det här verktyget ingår i Microsoft .NET SDK (version 1,1 och senare) och i Microsoft Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-155">This tool is included in the Microsoft .NET SDK (versions 1.1 and later) and in the Microsoft Windows SDK.</span></span>

<span data-ttu-id="9ad4a-156">Mer information om syntaxen och parameter beskrivningarna för MakeCert.exe-verktyget finns i verktyget för att [Skapa certifikat (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80)).</span><span class="sxs-lookup"><span data-stu-id="9ad4a-156">For more information about the syntax and the parameter descriptions of the MakeCert.exe tool, see [Certificate Creation Tool (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80)).</span></span>

<span data-ttu-id="9ad4a-157">Om du vill använda MakeCert.exe-verktyget för att skapa ett certifikat kör du följande kommandon i ett kommando tolks fönster för SDK.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-157">To use the MakeCert.exe tool to create a certificate, run the following commands in an SDK Command Prompt window.</span></span>

<span data-ttu-id="9ad4a-158">Obs: det första kommandot skapar en lokal certifikat utfärdare för datorn.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-158">Note: The first command creates a local certification authority for your computer.</span></span> <span data-ttu-id="9ad4a-159">Det andra kommandot genererar ett personligt certifikat från certifikat utfärdaren.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-159">The second command generates a personal certificate from the certification authority.</span></span>

<span data-ttu-id="9ad4a-160">Obs: du kan kopiera eller skriva kommandon exakt som de visas.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-160">Note: You can copy or type the commands exactly as they appear.</span></span> <span data-ttu-id="9ad4a-161">Inga ersättningar krävs, men du kan ändra certifikat namnet.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-161">No substitutions are necessary, although you can change the certificate name.</span></span>

```powershell
makecert -n "CN=PowerShell Local Certificate Root" -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -r -sv root.pvk root.cer `
-ss Root -sr localMachine

makecert -pe -n "CN=PowerShell User" -ss MY -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -iv root.pvk -ic root.cer
```

<span data-ttu-id="9ad4a-162">I MakeCert.exes verktyget uppmanas du att ange ett lösen ord för den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-162">The MakeCert.exe tool will prompt you for a private key password.</span></span> <span data-ttu-id="9ad4a-163">Lösen ordet garanterar att ingen kan använda eller komma åt certifikatet utan ditt medgivande.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-163">The password ensures that no one can use or access the certificate without your consent.</span></span>
<span data-ttu-id="9ad4a-164">Skapa och ange ett lösen ord som du kan komma ihåg.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-164">Create and enter a password that you can remember.</span></span> <span data-ttu-id="9ad4a-165">Du kommer att använda det här lösen ordet senare för att hämta certifikatet.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-165">You will use this password later to retrieve the certificate.</span></span>

<span data-ttu-id="9ad4a-166">Kontrol lera att certifikatet har genererats korrekt genom att använda följande kommando för att hämta certifikatet i certifikat arkivet på datorn.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-166">To verify that the certificate was generated correctly, use the following command to get the certificate in the certificate store on the computer.</span></span> <span data-ttu-id="9ad4a-167">Du kommer inte att hitta någon certifikat fil i fil system katalogen.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-167">You will not find a certificate file in the file system directory.</span></span>

<span data-ttu-id="9ad4a-168">I PowerShell-prompten skriver du:</span><span class="sxs-lookup"><span data-stu-id="9ad4a-168">At the PowerShell prompt, type:</span></span>

```powershell
Get-ChildItem cert:\CurrentUser\my -codesigning
```

<span data-ttu-id="9ad4a-169">Detta kommando använder PowerShell-certifikat leverantören för att visa information om certifikatet.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-169">This command uses the PowerShell Certificate provider to view information about the certificate.</span></span>

<span data-ttu-id="9ad4a-170">Om certifikatet har skapats visar utdata det **tumavtryck** som identifierar certifikatet i en bildskärm som liknar följande:</span><span class="sxs-lookup"><span data-stu-id="9ad4a-170">If the certificate was created, the output shows the **thumbprint** that identifies the certificate in a display that resembles the following:</span></span>

```Output
Directory: Microsoft.PowerShell.Security\Certificate::CurrentUser\My

Thumbprint                                Subject
----------                                -------
4D4917CB140714BA5B81B96E0B18AAF2C4564FDF  CN=PowerShell User ]
```

## <a name="sign-a-script"></a><span data-ttu-id="9ad4a-171">Signera ett skript</span><span class="sxs-lookup"><span data-stu-id="9ad4a-171">Sign a script</span></span>

<span data-ttu-id="9ad4a-172">När du har skapat ett självsignerat certifikat kan du signera skript.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-172">After you create a self-signed certificate, you can sign scripts.</span></span> <span data-ttu-id="9ad4a-173">Om du använder **AllSigned** körnings princip kan du signera ett skript för att köra skriptet på datorn.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-173">If you use the **AllSigned** execution policy, signing a script permits you to run the script on your computer.</span></span>

<span data-ttu-id="9ad4a-174">Följande exempel skript, `Add-Signature.ps1` signerar ett skript.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-174">The following sample script, `Add-Signature.ps1`, signs a script.</span></span> <span data-ttu-id="9ad4a-175">Om du använder **AllSigned** körnings princip måste du dock signera `Add-Signature.ps1` skriptet innan du kör det.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-175">However, if you are using the **AllSigned** execution policy, you must sign the `Add-Signature.ps1` script before you run it.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ad4a-176">Skriptet måste sparas med ASCII-eller UTF8NoBOM-kodning. Du kan signera en skript fil som använder en annan kodning.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-176">The script must be saved using ASCII or UTF8NoBOM encoding.You can sign a script file that uses a different encoding.</span></span> <span data-ttu-id="9ad4a-177">Men skriptet kan inte köras eller också går det inte att importera den modul som innehåller skriptet.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-177">But the script fails to run or the module containing the script fails to import.</span></span>

<span data-ttu-id="9ad4a-178">Om du vill använda det här skriptet kopierar du följande text till en textfil och namnger den `Add-Signature.ps1` .</span><span class="sxs-lookup"><span data-stu-id="9ad4a-178">To use this script, copy the following text into a text file, and name it `Add-Signature.ps1`.</span></span>

```powershell
## Signs a file
param([string] $file=$(throw "Please specify a filename."))
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature $file $cert
```

<span data-ttu-id="9ad4a-179">Om du vill signera `Add-Signature.ps1` skript filen skriver du följande kommandon i PowerShell-kommando tolken:</span><span class="sxs-lookup"><span data-stu-id="9ad4a-179">To sign the `Add-Signature.ps1` script file, type the following commands at the PowerShell command prompt:</span></span>

```powershell
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature add-signature.ps1 $cert
```

<span data-ttu-id="9ad4a-180">När skriptet har signerats kan du köra det på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-180">After the script is signed, you can run it on the local computer.</span></span> <span data-ttu-id="9ad4a-181">Men skriptet kan inte köras på datorer där PowerShell-körnings principen kräver en digital signatur från en betrodd utfärdare.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-181">However, the script will not run on computers on which the PowerShell execution policy requires a digital signature from a trusted authority.</span></span> <span data-ttu-id="9ad4a-182">Om du försöker igen visas följande fel meddelande i PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9ad4a-182">If you try, PowerShell displays the following error message:</span></span>

```Output
The file C:\remote_file.ps1 cannot be loaded. The signature of the
certificate cannot be verified.
At line:1 char:15
+ .\ remote_file.ps1 <<<<
```

<span data-ttu-id="9ad4a-183">Om PowerShell visar det här meddelandet när du kör ett skript som du inte har skrivit, behandla filen som du skulle behandla alla osignerade skript.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-183">If PowerShell displays this message when you run a script that you did not write, treat the file as you would treat any unsigned script.</span></span> <span data-ttu-id="9ad4a-184">Granska koden för att avgöra om du kan lita på skriptet.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-184">Review the code to determine whether you can trust the script.</span></span>

## <a name="enable-strong-private-key-protection-for-your-certificate"></a><span data-ttu-id="9ad4a-185">Aktivera starkt skydd av den privata nyckeln för ditt certifikat</span><span class="sxs-lookup"><span data-stu-id="9ad4a-185">Enable strong private key protection for your certificate</span></span>

<span data-ttu-id="9ad4a-186">Om du har ett privat certifikat på datorn kan skadliga program kunna signera skript åt dig, vilket ger PowerShell möjlighet att köra dem.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-186">If you have a private certificate on your computer, malicious programs might be able to sign scripts on your behalf, which authorizes PowerShell to run them.</span></span>

<span data-ttu-id="9ad4a-187">Använd Certificate Manager `Certmgr.exe` för att exportera ditt signerings certifikat till en fil för att förhindra automatisk signering för din räkning `.pfx` .</span><span class="sxs-lookup"><span data-stu-id="9ad4a-187">To prevent automated signing on your behalf, use Certificate Manager `Certmgr.exe` to export your signing certificate to a `.pfx` file.</span></span> <span data-ttu-id="9ad4a-188">Certifikat hanteraren ingår i Microsoft .NET SDK, Microsoft Windows SDK och i Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-188">Certificate Manager is included in the Microsoft .NET SDK, the Microsoft Windows SDK, and in internet Explorer.</span></span>

<span data-ttu-id="9ad4a-189">Så här exporterar du certifikatet:</span><span class="sxs-lookup"><span data-stu-id="9ad4a-189">To export the certificate:</span></span>

1. <span data-ttu-id="9ad4a-190">Starta certifikat hanteraren.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-190">Start Certificate Manager.</span></span>
2. <span data-ttu-id="9ad4a-191">Välj det certifikat som utfärdats av den lokala PowerShell-certifikat roten.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-191">Select the certificate issued by PowerShell Local Certificate Root.</span></span>
3. <span data-ttu-id="9ad4a-192">Klicka på Exportera för att starta guiden Exportera certifikat.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-192">Click Export to start the Certificate Export Wizard.</span></span>
4. <span data-ttu-id="9ad4a-193">Välj "Ja, exportera den privata nyckeln" och klicka sedan på Nästa.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-193">Select "Yes, export the private key", and then click Next.</span></span>
5. <span data-ttu-id="9ad4a-194">Välj "Aktivera starkt skydd".</span><span class="sxs-lookup"><span data-stu-id="9ad4a-194">Select "Enable strong protection."</span></span>
6. <span data-ttu-id="9ad4a-195">Skriv ett lösen ord och skriv det igen för att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-195">Type a password, and then type it again to confirm.</span></span>
7. <span data-ttu-id="9ad4a-196">Ange ett fil namn som har fil namns tillägget. pfx.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-196">Type a file name that has the .pfx file name extension.</span></span>
8. <span data-ttu-id="9ad4a-197">Klicka på Slutför.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-197">Click Finish.</span></span>

<span data-ttu-id="9ad4a-198">Så här importerar du certifikatet på nytt:</span><span class="sxs-lookup"><span data-stu-id="9ad4a-198">To re-import the certificate:</span></span>

1. <span data-ttu-id="9ad4a-199">Starta certifikat hanteraren.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-199">Start Certificate Manager.</span></span>
2. <span data-ttu-id="9ad4a-200">Klicka på Importera för att starta guiden Importera certifikat.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-200">Click Import to start the Certificate Import Wizard.</span></span>
3. <span data-ttu-id="9ad4a-201">Öppna till platsen för den. pfx-fil som du skapade under export processen.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-201">Open to the location of the .pfx file that you created during the export process.</span></span>
4. <span data-ttu-id="9ad4a-202">På sidan lösen ord väljer du Aktivera starkt skydd av den privata nyckeln och anger sedan det lösen ord som du tilldelade under export processen.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-202">On the Password page, select "Enable strong private key protection", and then enter the password that you assigned during the export process.</span></span>
5. <span data-ttu-id="9ad4a-203">Välj det personliga certifikat arkivet.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-203">Select the Personal certificate store.</span></span>
6. <span data-ttu-id="9ad4a-204">Klicka på Slutför.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-204">Click Finish.</span></span>

## <a name="prevent-the-signature-from-expiring"></a><span data-ttu-id="9ad4a-205">Förhindra att signaturen upphör att gälla</span><span class="sxs-lookup"><span data-stu-id="9ad4a-205">Prevent the signature from expiring</span></span>

<span data-ttu-id="9ad4a-206">Den digitala signaturen i ett skript är giltig tills signerings certifikatet upphör att gälla eller så länge en tids stämplings Server kan verifiera att skriptet signerades medan signerings certifikatet var giltigt.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-206">The digital signature in a script is valid until the signing certificate expires or as long as a timestamp server can verify that the script was signed while the signing certificate was valid.</span></span>

<span data-ttu-id="9ad4a-207">Eftersom de flesta signerings certifikaten endast är giltiga i ett år, garanterar att användarna kan använda ditt skript i flera år för att komma åt dem med hjälp av en tids stämplings Server.</span><span class="sxs-lookup"><span data-stu-id="9ad4a-207">Because most signing certificates are valid for one year only, using a time stamp server ensures that users can use your script for many years to come.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ad4a-208">Se även</span><span class="sxs-lookup"><span data-stu-id="9ad4a-208">See also</span></span>

[<span data-ttu-id="9ad4a-209">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="9ad4a-209">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="9ad4a-210">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="9ad4a-210">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="9ad4a-211">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="9ad4a-211">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="9ad4a-212">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="9ad4a-212">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="9ad4a-213">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="9ad4a-213">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

<span data-ttu-id="9ad4a-214">[Introduktion till kod signering](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="9ad4a-214">[Introduction to Code Signing](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))</span></span>
