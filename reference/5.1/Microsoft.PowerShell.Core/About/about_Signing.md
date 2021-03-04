---
description: Förklarar hur du signerar skript så att de följer PowerShell-körnings principerna.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_signing?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Signing
ms.openlocfilehash: dc882b4f62a9c08458d9c54ac2defcaad8c7809c
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685973"
---
# <a name="about-signing"></a><span data-ttu-id="e16fc-104">Om signering</span><span class="sxs-lookup"><span data-stu-id="e16fc-104">About Signing</span></span>

## <a name="short-description"></a><span data-ttu-id="e16fc-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="e16fc-105">Short description</span></span>
<span data-ttu-id="e16fc-106">Förklarar hur du signerar skript så att de följer PowerShell-körnings principerna.</span><span class="sxs-lookup"><span data-stu-id="e16fc-106">Explains how to sign scripts so that they comply with the PowerShell execution policies.</span></span>

## <a name="long-description"></a><span data-ttu-id="e16fc-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="e16fc-107">Long description</span></span>

<span data-ttu-id="e16fc-108">Principen för begränsade körningar tillåter inte att skript körs.</span><span class="sxs-lookup"><span data-stu-id="e16fc-108">The Restricted execution policy does not permit any scripts to run.</span></span> <span data-ttu-id="e16fc-109">**AllSigned** -och **RemoteSigned** -körnings principerna förhindrar att PowerShell kör skript som inte har någon digital signatur.</span><span class="sxs-lookup"><span data-stu-id="e16fc-109">The **AllSigned** and **RemoteSigned** execution policies prevent PowerShell from running scripts that do not have a digital signature.</span></span>

<span data-ttu-id="e16fc-110">I det här avsnittet beskrivs hur du kör valda skript som inte är signerade, även om körnings principen är **RemoteSigned** och hur du signerar skript för egen användning.</span><span class="sxs-lookup"><span data-stu-id="e16fc-110">This topic explains how to run selected scripts that are not signed, even while the execution policy is **RemoteSigned**, and how to sign scripts for your own use.</span></span>

<span data-ttu-id="e16fc-111">Mer information om körnings principer för PowerShell finns i [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="e16fc-111">For more information about PowerShell execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

## <a name="to-permit-signed-scripts-to-run"></a><span data-ttu-id="e16fc-112">Tillåta att signerade skript körs</span><span class="sxs-lookup"><span data-stu-id="e16fc-112">To permit signed scripts to run</span></span>

<span data-ttu-id="e16fc-113">När du startar PowerShell på en dator för första gången är den **begränsade** körnings principen (standard) förmodligen aktiv.</span><span class="sxs-lookup"><span data-stu-id="e16fc-113">When you start PowerShell on a computer for the first time, the **Restricted** execution policy (the default) is likely to be in effect.</span></span>

<span data-ttu-id="e16fc-114">Den **begränsade** principen tillåter inte att skript körs.</span><span class="sxs-lookup"><span data-stu-id="e16fc-114">The **Restricted** policy does not permit any scripts to run.</span></span>

<span data-ttu-id="e16fc-115">Du hittar den effektiva körnings principen på datorn genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="e16fc-115">To find the effective execution policy on your computer, type:</span></span>

```powershell
Get-ExecutionPolicy
```

<span data-ttu-id="e16fc-116">Om du vill köra osignerade skript som du skriver på din lokala dator och signerade skript från andra användare, startar du PowerShell med alternativet Kör som administratör och använder sedan följande kommando för att ändra körnings principen på datorn till **RemoteSigned**:</span><span class="sxs-lookup"><span data-stu-id="e16fc-116">To run unsigned scripts that you write on your local computer and signed scripts from other users, start PowerShell with the Run as Administrator option and then use the following command to change the execution policy on the computer to **RemoteSigned**:</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<span data-ttu-id="e16fc-117">Mer information finns i hjälp avsnittet för `Set-ExecutionPolicy` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e16fc-117">For more information, see the help topic for the `Set-ExecutionPolicy` cmdlet.</span></span>

## <a name="running-unsigned-scripts-using-the-remotesigned-execution-policy"></a><span data-ttu-id="e16fc-118">Köra osignerade skript med körnings principen för RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="e16fc-118">Running unsigned scripts using the RemoteSigned execution policy</span></span>

<span data-ttu-id="e16fc-119">Om din PowerShell-körnings princip är **RemoteSigned** kör PowerShell inte osignerade skript som hämtas från Internet, inklusive osignerade skript som du får via e-post och snabb meddelande program.</span><span class="sxs-lookup"><span data-stu-id="e16fc-119">If your PowerShell execution policy is **RemoteSigned**, PowerShell will not run unsigned scripts that are downloaded from the internet, including unsigned scripts you receive through email and instant messaging programs.</span></span>

<span data-ttu-id="e16fc-120">Om du försöker köra ett nedladdat skript visas följande fel meddelande i PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e16fc-120">If you try to run a downloaded script, PowerShell displays the following error message:</span></span>

```Output
The file <file-name> cannot be loaded. The file <file-name> is not digitally
signed. The script will not execute on the system. Please see "Get-Help
about_Signing" for more details.
```

<span data-ttu-id="e16fc-121">Innan du kör skriptet bör du granska koden för att vara säker på att du litar på den.</span><span class="sxs-lookup"><span data-stu-id="e16fc-121">Before you run the script, review the code to be sure that you trust it.</span></span>
<span data-ttu-id="e16fc-122">Skript har samma resultat som alla körbara program.</span><span class="sxs-lookup"><span data-stu-id="e16fc-122">Scripts have the same effect as any executable program.</span></span>

<span data-ttu-id="e16fc-123">Om du vill köra ett osignerat skript använder du Unblock-File-cmdleten eller så använder du följande procedur.</span><span class="sxs-lookup"><span data-stu-id="e16fc-123">To run an unsigned script, use the Unblock-File cmdlet or use the following procedure.</span></span>

1. <span data-ttu-id="e16fc-124">Spara skript filen på datorn.</span><span class="sxs-lookup"><span data-stu-id="e16fc-124">Save the script file on your computer.</span></span>
2. <span data-ttu-id="e16fc-125">Klicka på Start, klicka på den här datorn och leta upp den sparade skript filen.</span><span class="sxs-lookup"><span data-stu-id="e16fc-125">Click Start, click My Computer, and locate the saved script file.</span></span>
3. <span data-ttu-id="e16fc-126">Högerklicka på skript filen och klicka sedan på egenskaper.</span><span class="sxs-lookup"><span data-stu-id="e16fc-126">Right-click the script file, and then click Properties.</span></span>
4. <span data-ttu-id="e16fc-127">Klicka på avblockera.</span><span class="sxs-lookup"><span data-stu-id="e16fc-127">Click Unblock.</span></span>

<span data-ttu-id="e16fc-128">Om ett skript som hämtades från Internet har signerats digitalt, men du ännu inte har valt att lita på utgivaren, visas följande meddelande i PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e16fc-128">If a script that was downloaded from the internet is digitally signed, but you have not yet chosen to trust its publisher, PowerShell displays the following message:</span></span>

```Output
Do you want to run software from this untrusted publisher?
The file <file-name> is published by CN=<publisher-name>. This
publisher is not trusted on your system. Only run scripts
from trusted publishers.

[V] Never run  [D] Do not run  [R] Run once  [A] Always run
[?] Help (default is "D"):
```

<span data-ttu-id="e16fc-129">Om du litar på utgivaren väljer du kör en gång eller kör alltid.</span><span class="sxs-lookup"><span data-stu-id="e16fc-129">If you trust the publisher, select "Run once" or "Always run."</span></span> <span data-ttu-id="e16fc-130">Om du inte litar på utgivaren väljer du antingen "Kör aldrig" eller "kör inte".</span><span class="sxs-lookup"><span data-stu-id="e16fc-130">If you do not trust the publisher, select either "Never run" or "Do not run."</span></span> <span data-ttu-id="e16fc-131">Om du väljer "aldrig körning" eller "kör alltid" uppmanas du inte att göra det igen för den här utgivaren.</span><span class="sxs-lookup"><span data-stu-id="e16fc-131">If you select "Never run" or "Always run," PowerShell will not prompt you again for this publisher.</span></span>

## <a name="methods-of-signing-scripts"></a><span data-ttu-id="e16fc-132">Metoder för signering av skript</span><span class="sxs-lookup"><span data-stu-id="e16fc-132">Methods of signing scripts</span></span>

<span data-ttu-id="e16fc-133">Du kan signera de skript som du skriver och skript som du hämtar från andra källor.</span><span class="sxs-lookup"><span data-stu-id="e16fc-133">You can sign the scripts that you write and the scripts that you obtain from other sources.</span></span> <span data-ttu-id="e16fc-134">Innan du signerar ett skript kontrollerar du varje kommando för att kontrol lera att det är säkert att köra.</span><span class="sxs-lookup"><span data-stu-id="e16fc-134">Before you sign any script, examine each command to verify that it is safe to run.</span></span>

<span data-ttu-id="e16fc-135">Bästa praxis om kod signering finns i [metod tips för kod signering](/previous-versions/windows/hardware/design/dn653556(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="e16fc-135">For best practices about code signing, see [Code-Signing Best Practices](/previous-versions/windows/hardware/design/dn653556(v=vs.85)).</span></span>

<span data-ttu-id="e16fc-136">Mer information om hur du signerar en skript fil finns i [set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature).</span><span class="sxs-lookup"><span data-stu-id="e16fc-136">For more information about how to sign a script file, see [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature).</span></span>

<span data-ttu-id="e16fc-137">`New-SelfSignedCertificate`Cmdleten, som introducerades i PKI-modulen i PowerShell 3,0, skapar ett självsignerat certifikat som är lämpligt för testning.</span><span class="sxs-lookup"><span data-stu-id="e16fc-137">The `New-SelfSignedCertificate` cmdlet, introduced in the PKI module in PowerShell 3.0, creates a self-signed certificate that is Appropriate for testing.</span></span> <span data-ttu-id="e16fc-138">Mer information finns i hjälp avsnittet för New-SelfSignedCertificate-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e16fc-138">For more information, see the help topic for the New-SelfSignedCertificate cmdlet.</span></span>

<span data-ttu-id="e16fc-139">Om du vill lägga till en digital signatur i ett skript måste du signera den med ett kod signerings certifikat.</span><span class="sxs-lookup"><span data-stu-id="e16fc-139">To add a digital signature to a script, you must sign it with a code signing certificate.</span></span> <span data-ttu-id="e16fc-140">Två typer av certifikat är lämpliga för signering av en skript fil:</span><span class="sxs-lookup"><span data-stu-id="e16fc-140">Two types of certificates are suitable for signing a script file:</span></span>

- <span data-ttu-id="e16fc-141">Certifikat som har skapats av en certifikat utfärdare: för en avgift verifierar en offentlig certifikat utfärdare din identitet och ger dig ett kod signerings certifikat.</span><span class="sxs-lookup"><span data-stu-id="e16fc-141">Certificates that are created by a certification authority: For a fee, a public certification authority verifies your identity and gives you a code signing certificate.</span></span> <span data-ttu-id="e16fc-142">När du köper ditt certifikat från en betrodd certifikat utfärdare kan du dela ditt skript med användare på andra datorer som kör Windows eftersom de andra datorerna litar på certifikat utfärdaren.</span><span class="sxs-lookup"><span data-stu-id="e16fc-142">When you purchase your certificate from a reputable certification authority, you are able to share your script with users on other computers that are running Windows because those other computers trust the certification authority.</span></span>

- <span data-ttu-id="e16fc-143">Certifikat som du skapar: du kan skapa ett självsignerat certifikat för vilket datorn är den myndighet som skapar certifikatet.</span><span class="sxs-lookup"><span data-stu-id="e16fc-143">Certificates that you create: You can create a self-signed certificate for which your computer is the authority that creates the certificate.</span></span> <span data-ttu-id="e16fc-144">Det här certifikatet är kostnads fritt och du kan skriva, signera och köra skript på din dator.</span><span class="sxs-lookup"><span data-stu-id="e16fc-144">This certificate is free of charge and enables you to write, sign, and run scripts on your computer.</span></span> <span data-ttu-id="e16fc-145">Ett skript som signerats av ett självsignerat certifikat kommer dock inte att köras på andra datorer.</span><span class="sxs-lookup"><span data-stu-id="e16fc-145">However, a script signed by a self-signed certificate will not run on other computers.</span></span>

<span data-ttu-id="e16fc-146">Normalt använder du bara ett självsignerat certifikat för att signera skript som du skriver för eget bruk och för att signera skript som du får från andra källor som du har kontrollerat är säkra.</span><span class="sxs-lookup"><span data-stu-id="e16fc-146">Typically, you would use a self-signed certificate only to sign scripts that you write for your own use and to sign scripts that you get from other sources that you have verified to be safe.</span></span> <span data-ttu-id="e16fc-147">Det är inte lämpligt för skript som ska delas, även inom ett företag.</span><span class="sxs-lookup"><span data-stu-id="e16fc-147">It is not appropriate for scripts that will be shared, even within an enterprise.</span></span>

<span data-ttu-id="e16fc-148">Om du skapar ett självsignerat certifikat måste du Aktivera starkt skydd av den privata nyckeln på ditt certifikat.</span><span class="sxs-lookup"><span data-stu-id="e16fc-148">If you create a self-signed certificate, be sure to enable strong private key protection on your certificate.</span></span> <span data-ttu-id="e16fc-149">Detta förhindrar att skadliga program signerar skript åt dig.</span><span class="sxs-lookup"><span data-stu-id="e16fc-149">This prevents malicious programs from signing scripts on your behalf.</span></span> <span data-ttu-id="e16fc-150">Anvisningarna finns i slutet av det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="e16fc-150">The instructions are included at the end of this topic.</span></span>

## <a name="create-a-self-signed-certificate"></a><span data-ttu-id="e16fc-151">Skapa ett självsignerat certifikat</span><span class="sxs-lookup"><span data-stu-id="e16fc-151">Create a self-signed certificate</span></span>

<span data-ttu-id="e16fc-152">Om du vill skapa ett självsignerat certifikat använder du `New-SelfSignedCertificate` cmdleten i PKI-modulen.</span><span class="sxs-lookup"><span data-stu-id="e16fc-152">To create a self-signed certificate, use the `New-SelfSignedCertificate` cmdlet in the PKI module.</span></span> <span data-ttu-id="e16fc-153">Den här modulen introduceras i PowerShell 3,0 och ingår i Windows 8 och Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="e16fc-153">This module is introduced in PowerShell 3.0 and is included in Windows 8 and Windows Server 2012.</span></span> <span data-ttu-id="e16fc-154">Mer information finns i hjälp avsnittet för `New-SelfSignedCertificate` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e16fc-154">For more information, see the help topic for the `New-SelfSignedCertificate` cmdlet.</span></span>

<span data-ttu-id="e16fc-155">Om du vill skapa ett självsignerat certifikat i tidigare versioner av Windows använder du verktyget för att skapa certifikat `MakeCert.exe` .</span><span class="sxs-lookup"><span data-stu-id="e16fc-155">To create a self-signed certificate in earlier versions of Windows, use the Certificate Creation tool `MakeCert.exe`.</span></span> <span data-ttu-id="e16fc-156">Det här verktyget ingår i Microsoft .NET SDK (version 1,1 och senare) och i Microsoft Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="e16fc-156">This tool is included in the Microsoft .NET SDK (versions 1.1 and later) and in the Microsoft Windows SDK.</span></span>

<span data-ttu-id="e16fc-157">Mer information om syntaxen och parameter beskrivningarna för MakeCert.exe-verktyget finns i verktyget för att [Skapa certifikat (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80)).</span><span class="sxs-lookup"><span data-stu-id="e16fc-157">For more information about the syntax and the parameter descriptions of the MakeCert.exe tool, see [Certificate Creation Tool (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80)).</span></span>

<span data-ttu-id="e16fc-158">Om du vill använda MakeCert.exe-verktyget för att skapa ett certifikat kör du följande kommandon i ett kommando tolks fönster för SDK.</span><span class="sxs-lookup"><span data-stu-id="e16fc-158">To use the MakeCert.exe tool to create a certificate, run the following commands in an SDK Command Prompt window.</span></span>

<span data-ttu-id="e16fc-159">Obs: det första kommandot skapar en lokal certifikat utfärdare för datorn.</span><span class="sxs-lookup"><span data-stu-id="e16fc-159">Note: The first command creates a local certification authority for your computer.</span></span> <span data-ttu-id="e16fc-160">Det andra kommandot genererar ett personligt certifikat från certifikat utfärdaren.</span><span class="sxs-lookup"><span data-stu-id="e16fc-160">The second command generates a personal certificate from the certification authority.</span></span>

<span data-ttu-id="e16fc-161">Obs: du kan kopiera eller skriva kommandon exakt som de visas.</span><span class="sxs-lookup"><span data-stu-id="e16fc-161">Note: You can copy or type the commands exactly as they appear.</span></span> <span data-ttu-id="e16fc-162">Inga ersättningar krävs, men du kan ändra certifikat namnet.</span><span class="sxs-lookup"><span data-stu-id="e16fc-162">No substitutions are necessary, although you can change the certificate name.</span></span>

```powershell
makecert -n "CN=PowerShell Local Certificate Root" -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -r -sv root.pvk root.cer `
-ss Root -sr localMachine

makecert -pe -n "CN=PowerShell User" -ss MY -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -iv root.pvk -ic root.cer
```

<span data-ttu-id="e16fc-163">I MakeCert.exes verktyget uppmanas du att ange ett lösen ord för den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="e16fc-163">The MakeCert.exe tool will prompt you for a private key password.</span></span> <span data-ttu-id="e16fc-164">Lösen ordet garanterar att ingen kan använda eller komma åt certifikatet utan ditt medgivande.</span><span class="sxs-lookup"><span data-stu-id="e16fc-164">The password ensures that no one can use or access the certificate without your consent.</span></span>
<span data-ttu-id="e16fc-165">Skapa och ange ett lösen ord som du kan komma ihåg.</span><span class="sxs-lookup"><span data-stu-id="e16fc-165">Create and enter a password that you can remember.</span></span> <span data-ttu-id="e16fc-166">Du kommer att använda det här lösen ordet senare för att hämta certifikatet.</span><span class="sxs-lookup"><span data-stu-id="e16fc-166">You will use this password later to retrieve the certificate.</span></span>

<span data-ttu-id="e16fc-167">Kontrol lera att certifikatet har genererats korrekt genom att använda följande kommando för att hämta certifikatet i certifikat arkivet på datorn.</span><span class="sxs-lookup"><span data-stu-id="e16fc-167">To verify that the certificate was generated correctly, use the following command to get the certificate in the certificate store on the computer.</span></span> <span data-ttu-id="e16fc-168">Du kommer inte att hitta någon certifikat fil i fil system katalogen.</span><span class="sxs-lookup"><span data-stu-id="e16fc-168">You will not find a certificate file in the file system directory.</span></span>

<span data-ttu-id="e16fc-169">I PowerShell-prompten skriver du:</span><span class="sxs-lookup"><span data-stu-id="e16fc-169">At the PowerShell prompt, type:</span></span>

```powershell
Get-ChildItem cert:\CurrentUser\my -codesigning
```

<span data-ttu-id="e16fc-170">Detta kommando använder PowerShell-certifikat leverantören för att visa information om certifikatet.</span><span class="sxs-lookup"><span data-stu-id="e16fc-170">This command uses the PowerShell Certificate provider to view information about the certificate.</span></span>

<span data-ttu-id="e16fc-171">Om certifikatet har skapats visar utdata det **tumavtryck** som identifierar certifikatet i en bildskärm som liknar följande:</span><span class="sxs-lookup"><span data-stu-id="e16fc-171">If the certificate was created, the output shows the **thumbprint** that identifies the certificate in a display that resembles the following:</span></span>

```Output
Directory: Microsoft.PowerShell.Security\Certificate::CurrentUser\My

Thumbprint                                Subject
----------                                -------
4D4917CB140714BA5B81B96E0B18AAF2C4564FDF  CN=PowerShell User ]
```

## <a name="sign-a-script"></a><span data-ttu-id="e16fc-172">Signera ett skript</span><span class="sxs-lookup"><span data-stu-id="e16fc-172">Sign a script</span></span>

<span data-ttu-id="e16fc-173">När du har skapat ett självsignerat certifikat kan du signera skript.</span><span class="sxs-lookup"><span data-stu-id="e16fc-173">After you create a self-signed certificate, you can sign scripts.</span></span> <span data-ttu-id="e16fc-174">Om du använder **AllSigned** körnings princip kan du signera ett skript för att köra skriptet på datorn.</span><span class="sxs-lookup"><span data-stu-id="e16fc-174">If you use the **AllSigned** execution policy, signing a script permits you to run the script on your computer.</span></span>

<span data-ttu-id="e16fc-175">Följande exempel skript, `Add-Signature.ps1` signerar ett skript.</span><span class="sxs-lookup"><span data-stu-id="e16fc-175">The following sample script, `Add-Signature.ps1`, signs a script.</span></span> <span data-ttu-id="e16fc-176">Om du använder **AllSigned** körnings princip måste du dock signera `Add-Signature.ps1` skriptet innan du kör det.</span><span class="sxs-lookup"><span data-stu-id="e16fc-176">However, if you are using the **AllSigned** execution policy, you must sign the `Add-Signature.ps1` script before you run it.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e16fc-177">Skriptet måste sparas med ASCII-eller UTF8NoBOM-kodning.</span><span class="sxs-lookup"><span data-stu-id="e16fc-177">The script must be saved using ASCII or UTF8NoBOM encoding.</span></span> <span data-ttu-id="e16fc-178">Du kan signera en skript fil som använder en annan kodning.</span><span class="sxs-lookup"><span data-stu-id="e16fc-178">You can sign a script file that uses a different encoding.</span></span> <span data-ttu-id="e16fc-179">Men skriptet kan inte köras eller också går det inte att importera den modul som innehåller skriptet.</span><span class="sxs-lookup"><span data-stu-id="e16fc-179">But the script fails to run or the module containing the script fails to import.</span></span>

<span data-ttu-id="e16fc-180">Om du vill använda det här skriptet kopierar du följande text till en textfil och namnger den `Add-Signature.ps1` .</span><span class="sxs-lookup"><span data-stu-id="e16fc-180">To use this script, copy the following text into a text file, and name it `Add-Signature.ps1`.</span></span>

```powershell
## Signs a file
param([string] $file=$(throw "Please specify a filename."))
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature $file $cert
```

<span data-ttu-id="e16fc-181">Om du vill signera `Add-Signature.ps1` skript filen skriver du följande kommandon i PowerShell-kommando tolken:</span><span class="sxs-lookup"><span data-stu-id="e16fc-181">To sign the `Add-Signature.ps1` script file, type the following commands at the PowerShell command prompt:</span></span>

```powershell
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature add-signature.ps1 $cert
```

<span data-ttu-id="e16fc-182">När skriptet har signerats kan du köra det på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e16fc-182">After the script is signed, you can run it on the local computer.</span></span> <span data-ttu-id="e16fc-183">Men skriptet kan inte köras på datorer där PowerShell-körnings principen kräver en digital signatur från en betrodd utfärdare.</span><span class="sxs-lookup"><span data-stu-id="e16fc-183">However, the script will not run on computers on which the PowerShell execution policy requires a digital signature from a trusted authority.</span></span> <span data-ttu-id="e16fc-184">Om du försöker igen visas följande fel meddelande i PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e16fc-184">If you try, PowerShell displays the following error message:</span></span>

```Output
The file C:\remote_file.ps1 cannot be loaded. The signature of the
certificate cannot be verified.
At line:1 char:15
+ .\ remote_file.ps1 <<<<
```

<span data-ttu-id="e16fc-185">Om PowerShell visar det här meddelandet när du kör ett skript som du inte har skrivit, behandla filen som du skulle behandla alla osignerade skript.</span><span class="sxs-lookup"><span data-stu-id="e16fc-185">If PowerShell displays this message when you run a script that you did not write, treat the file as you would treat any unsigned script.</span></span> <span data-ttu-id="e16fc-186">Granska koden för att avgöra om du kan lita på skriptet.</span><span class="sxs-lookup"><span data-stu-id="e16fc-186">Review the code to determine whether you can trust the script.</span></span>

## <a name="enable-strong-private-key-protection-for-your-certificate"></a><span data-ttu-id="e16fc-187">Aktivera starkt skydd av den privata nyckeln för ditt certifikat</span><span class="sxs-lookup"><span data-stu-id="e16fc-187">Enable strong private key protection for your certificate</span></span>

<span data-ttu-id="e16fc-188">Om du har ett privat certifikat på datorn kan skadliga program kunna signera skript åt dig, vilket ger PowerShell möjlighet att köra dem.</span><span class="sxs-lookup"><span data-stu-id="e16fc-188">If you have a private certificate on your computer, malicious programs might be able to sign scripts on your behalf, which authorizes PowerShell to run them.</span></span>

<span data-ttu-id="e16fc-189">Använd Certificate Manager `Certmgr.exe` för att exportera ditt signerings certifikat till en fil för att förhindra automatisk signering för din räkning `.pfx` .</span><span class="sxs-lookup"><span data-stu-id="e16fc-189">To prevent automated signing on your behalf, use Certificate Manager `Certmgr.exe` to export your signing certificate to a `.pfx` file.</span></span> <span data-ttu-id="e16fc-190">Certifikat hanteraren ingår i Microsoft .NET SDK, Microsoft Windows SDK och i Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e16fc-190">Certificate Manager is included in the Microsoft .NET SDK, the Microsoft Windows SDK, and in internet Explorer.</span></span>

<span data-ttu-id="e16fc-191">Så här exporterar du certifikatet:</span><span class="sxs-lookup"><span data-stu-id="e16fc-191">To export the certificate:</span></span>

1. <span data-ttu-id="e16fc-192">Starta certifikat hanteraren.</span><span class="sxs-lookup"><span data-stu-id="e16fc-192">Start Certificate Manager.</span></span>
2. <span data-ttu-id="e16fc-193">Välj det certifikat som utfärdats av den lokala PowerShell-certifikat roten.</span><span class="sxs-lookup"><span data-stu-id="e16fc-193">Select the certificate issued by PowerShell Local Certificate Root.</span></span>
3. <span data-ttu-id="e16fc-194">Klicka på Exportera för att starta guiden Exportera certifikat.</span><span class="sxs-lookup"><span data-stu-id="e16fc-194">Click Export to start the Certificate Export Wizard.</span></span>
4. <span data-ttu-id="e16fc-195">Välj "Ja, exportera den privata nyckeln" och klicka sedan på Nästa.</span><span class="sxs-lookup"><span data-stu-id="e16fc-195">Select "Yes, export the private key", and then click Next.</span></span>
5. <span data-ttu-id="e16fc-196">Välj "Aktivera starkt skydd".</span><span class="sxs-lookup"><span data-stu-id="e16fc-196">Select "Enable strong protection."</span></span>
6. <span data-ttu-id="e16fc-197">Skriv ett lösen ord och skriv det igen för att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="e16fc-197">Type a password, and then type it again to confirm.</span></span>
7. <span data-ttu-id="e16fc-198">Ange ett fil namn som har fil namns tillägget. pfx.</span><span class="sxs-lookup"><span data-stu-id="e16fc-198">Type a file name that has the .pfx file name extension.</span></span>
8. <span data-ttu-id="e16fc-199">Klicka på Slutför.</span><span class="sxs-lookup"><span data-stu-id="e16fc-199">Click Finish.</span></span>

<span data-ttu-id="e16fc-200">Så här importerar du certifikatet på nytt:</span><span class="sxs-lookup"><span data-stu-id="e16fc-200">To re-import the certificate:</span></span>

1. <span data-ttu-id="e16fc-201">Starta certifikat hanteraren.</span><span class="sxs-lookup"><span data-stu-id="e16fc-201">Start Certificate Manager.</span></span>
2. <span data-ttu-id="e16fc-202">Klicka på Importera för att starta guiden Importera certifikat.</span><span class="sxs-lookup"><span data-stu-id="e16fc-202">Click Import to start the Certificate Import Wizard.</span></span>
3. <span data-ttu-id="e16fc-203">Öppna till platsen för den. pfx-fil som du skapade under export processen.</span><span class="sxs-lookup"><span data-stu-id="e16fc-203">Open to the location of the .pfx file that you created during the export process.</span></span>
4. <span data-ttu-id="e16fc-204">På sidan lösen ord väljer du Aktivera starkt skydd av den privata nyckeln och anger sedan det lösen ord som du tilldelade under export processen.</span><span class="sxs-lookup"><span data-stu-id="e16fc-204">On the Password page, select "Enable strong private key protection", and then enter the password that you assigned during the export process.</span></span>
5. <span data-ttu-id="e16fc-205">Välj det personliga certifikat arkivet.</span><span class="sxs-lookup"><span data-stu-id="e16fc-205">Select the Personal certificate store.</span></span>
6. <span data-ttu-id="e16fc-206">Klicka på Slutför.</span><span class="sxs-lookup"><span data-stu-id="e16fc-206">Click Finish.</span></span>

## <a name="prevent-the-signature-from-expiring"></a><span data-ttu-id="e16fc-207">Förhindra att signaturen upphör att gälla</span><span class="sxs-lookup"><span data-stu-id="e16fc-207">Prevent the signature from expiring</span></span>

<span data-ttu-id="e16fc-208">Den digitala signaturen i ett skript är giltig tills signerings certifikatet upphör att gälla eller så länge en tids stämplings Server kan verifiera att skriptet signerades medan signerings certifikatet var giltigt.</span><span class="sxs-lookup"><span data-stu-id="e16fc-208">The digital signature in a script is valid until the signing certificate expires or as long as a timestamp server can verify that the script was signed while the signing certificate was valid.</span></span>

<span data-ttu-id="e16fc-209">Eftersom de flesta signerings certifikaten endast är giltiga i ett år, garanterar att användarna kan använda ditt skript i flera år för att komma åt dem med hjälp av en tids stämplings Server.</span><span class="sxs-lookup"><span data-stu-id="e16fc-209">Because most signing certificates are valid for one year only, using a time stamp server ensures that users can use your script for many years to come.</span></span>

## <a name="see-also"></a><span data-ttu-id="e16fc-210">Se även</span><span class="sxs-lookup"><span data-stu-id="e16fc-210">See also</span></span>

[<span data-ttu-id="e16fc-211">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="e16fc-211">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="e16fc-212">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="e16fc-212">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="e16fc-213">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="e16fc-213">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="e16fc-214">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="e16fc-214">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="e16fc-215">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="e16fc-215">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

<span data-ttu-id="e16fc-216">[Introduktion till kod signering](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="e16fc-216">[Introduction to Code Signing](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))</span></span>
