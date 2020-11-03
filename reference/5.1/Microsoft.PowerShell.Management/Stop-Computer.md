---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: 8062210aa94cb46d5e5557ede1bac672cae39622
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268227"
---
# <span data-ttu-id="cdefc-103">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="cdefc-103">Stop-Computer</span></span>

## <span data-ttu-id="cdefc-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="cdefc-104">SYNOPSIS</span></span>
<span data-ttu-id="cdefc-105">Stoppar (stänger av) lokala och fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="cdefc-105">Stops (shuts down) local and remote computers.</span></span>

## <span data-ttu-id="cdefc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cdefc-106">SYNTAX</span></span>

### <span data-ttu-id="cdefc-107">Alla</span><span class="sxs-lookup"><span data-stu-id="cdefc-107">All</span></span>

```
Stop-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="cdefc-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cdefc-108">DESCRIPTION</span></span>

<span data-ttu-id="cdefc-109">`Stop-Computer`Cmdleten stänger av den lokala datorn och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="cdefc-109">The `Stop-Computer` cmdlet shuts down the local computer and remote computers.</span></span>

<span data-ttu-id="cdefc-110">Du kan använda parametrarna för `Stop-Computer` för att köra avstängnings åtgärderna som ett bakgrunds jobb, för att ange autentiseringsnivåer och alternativa autentiseringsuppgifter, för att begränsa de samtidiga anslutningar som skapas för att köra kommandot och framtvinga en omedelbar avstängning.</span><span class="sxs-lookup"><span data-stu-id="cdefc-110">You can use the parameters of `Stop-Computer` to run the shutdown operations as a background job, to specify the authentication levels and alternate credentials, to limit the concurrent connections that are created to run the command, and to force an immediate shut down.</span></span>

<span data-ttu-id="cdefc-111">Denna cmdlet kräver inte PowerShell-fjärrkommunikation om du inte använder parametern **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="cdefc-111">This cmdlet doesn't require PowerShell remoting unless you use the **AsJob** parameter.</span></span>

## <span data-ttu-id="cdefc-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="cdefc-112">EXAMPLES</span></span>

### <span data-ttu-id="cdefc-113">Exempel 1: Stäng av den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="cdefc-113">Example 1: Shut down the local computer</span></span>

<span data-ttu-id="cdefc-114">I det här exemplet stängs den lokala datorn av.</span><span class="sxs-lookup"><span data-stu-id="cdefc-114">This example shuts down the local computer.</span></span>

```powershell
Stop-Computer -ComputerName localhost
```

### <span data-ttu-id="cdefc-115">Exempel 2: Stäng av två fjärranslutna datorer och den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="cdefc-115">Example 2: Shut down two remote computers and the local computer</span></span>

<span data-ttu-id="cdefc-116">I det här exemplet stoppas två fjärranslutna datorer och den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cdefc-116">This example stops two remote computers and the local computer.</span></span>

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="cdefc-117">`Stop-Computer` använder parametern **computername** för att ange två fjärranslutna datorer och den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cdefc-117">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers and the local computer.</span></span> <span data-ttu-id="cdefc-118">Varje dator stängs av.</span><span class="sxs-lookup"><span data-stu-id="cdefc-118">Each computer is shut down.</span></span>

### <span data-ttu-id="cdefc-119">Exempel 3: Stäng av fjärrdatorer som bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="cdefc-119">Example 3: Shut down remote computers as a background job</span></span>

<span data-ttu-id="cdefc-120">I det här exemplet `Stop-Computer` körs som ett bakgrunds jobb på två fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="cdefc-120">In this example, `Stop-Computer` runs as a background job on two remote computers.</span></span>

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" -AsJob
$results = $j | Receive-Job
$results
```

<span data-ttu-id="cdefc-121">`Stop-Computer` använder parametern **computername** för att ange två fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="cdefc-121">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers.</span></span> <span data-ttu-id="cdefc-122">Parametern **AsJob** kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="cdefc-122">The **AsJob** parameter runs the command as a background job.</span></span> <span data-ttu-id="cdefc-123">Jobb objekten lagras i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="cdefc-123">The job objects are stored in the `$j` variable.</span></span>

<span data-ttu-id="cdefc-124">Jobb objekt i `$j` variabeln skickas ned till pipelinen till `Receive-Job` , som hämtar jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="cdefc-124">The job objects in the `$j` variable are sent down the pipeline to `Receive-Job`, which gets the job results.</span></span> <span data-ttu-id="cdefc-125">Objekten lagras i `$results` variabeln.</span><span class="sxs-lookup"><span data-stu-id="cdefc-125">The objects are stored in the `$results` variable.</span></span> <span data-ttu-id="cdefc-126">`$results`Variabeln visar jobb informationen i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="cdefc-126">The `$results` variable displays the job information in the PowerShell console.</span></span>

<span data-ttu-id="cdefc-127">Eftersom **AsJob** skapar jobbet på den lokala datorn och automatiskt returnerar resultaten till den lokala datorn, kan du köra `Receive-Job` som ett lokalt kommando.</span><span class="sxs-lookup"><span data-stu-id="cdefc-127">Because **AsJob** creates the job on the local computer and automatically returns the results to the local computer, you can run `Receive-Job` as a local command.</span></span>

### <span data-ttu-id="cdefc-128">Exempel 4: Stäng av en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="cdefc-128">Example 4: Shut down a remote computer</span></span>

<span data-ttu-id="cdefc-129">I det här exemplet stängs en fjärrdator med angiven autentisering.</span><span class="sxs-lookup"><span data-stu-id="cdefc-129">This example shuts down a remote computer using specified authentication.</span></span>

```powershell
Stop-Computer -ComputerName "Server01" -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

<span data-ttu-id="cdefc-130">`Stop-Computer` använder parametern **computername** för att ange fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="cdefc-130">`Stop-Computer` uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="cdefc-131">**Personifiering** -parametern anger en anpassad personifiering och **DcomAuthentication** -parametern anger inställningar på autentiserings nivå.</span><span class="sxs-lookup"><span data-stu-id="cdefc-131">The **Impersonation** parameter specifies a customized impersonation and the **DcomAuthentication** parameter specifies authentication-level settings.</span></span>

### <span data-ttu-id="cdefc-132">Exempel 5: Stäng av datorer i en domän</span><span class="sxs-lookup"><span data-stu-id="cdefc-132">Example 5: Shut down computers in a domain</span></span>

<span data-ttu-id="cdefc-133">I det här exemplet tvingar kommandon en omedelbar avstängning av alla datorer i en angiven domän.</span><span class="sxs-lookup"><span data-stu-id="cdefc-133">In this example, the commands force an immediate shut down of all computers in a specified domain.</span></span>

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -ThrottleLimit 10 -Credential $c
```

<span data-ttu-id="cdefc-134">`Get-Content` använder parametern **Path** för att hämta en fil i den aktuella katalogen med listan över domän datorer.</span><span class="sxs-lookup"><span data-stu-id="cdefc-134">`Get-Content` uses the **Path** parameter to get a file in the current directory with the list of domain computers.</span></span> <span data-ttu-id="cdefc-135">Objekten lagras i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="cdefc-135">The objects are stored in the `$s` variable.</span></span>

<span data-ttu-id="cdefc-136">`Get-Credential` använder parametern **Credential** för att ange autentiseringsuppgifter för en domän administratör.</span><span class="sxs-lookup"><span data-stu-id="cdefc-136">`Get-Credential` uses the **Credential** parameter to specify the credentials of a domain administrator.</span></span> <span data-ttu-id="cdefc-137">Autentiseringsuppgifterna lagras i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="cdefc-137">The credentials are stored in the `$c` variable.</span></span>

<span data-ttu-id="cdefc-138">`Stop-Computer` stänger av datorerna som anges med parametern **computername** i listan över datorer i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="cdefc-138">`Stop-Computer` shuts down the computers specified with the **ComputerName** parameter's list of computers in the `$s` variable.</span></span> <span data-ttu-id="cdefc-139">**Force** -parametern tvingar en omedelbar avstängning.</span><span class="sxs-lookup"><span data-stu-id="cdefc-139">The **Force** parameter forces an immediate shutdown.</span></span> <span data-ttu-id="cdefc-140">Parametern **ThrottleLimit** begränsar kommandot till 10 samtidiga anslutningar.</span><span class="sxs-lookup"><span data-stu-id="cdefc-140">The **ThrottleLimit** parameter limits the command to 10 concurrent connections.</span></span> <span data-ttu-id="cdefc-141">Parametern **Credential** skickar de autentiseringsuppgifter som sparats i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="cdefc-141">The **Credential** parameter submits the credentials saved in the `$c` variable.</span></span>

## <span data-ttu-id="cdefc-142">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="cdefc-142">PARAMETERS</span></span>

### <span data-ttu-id="cdefc-143">– AsJob</span><span class="sxs-lookup"><span data-stu-id="cdefc-143">-AsJob</span></span>

<span data-ttu-id="cdefc-144">Anger att denna cmdlet körs som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="cdefc-144">Indicates that this cmdlet runs as a background job.</span></span>

<span data-ttu-id="cdefc-145">Om du vill använda den här parametern måste lokal och fjärran sluten dator konfigureras för fjärr kommunikation och, i Windows Vista och senare versioner av Windows-operativsystemet, måste du öppna PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="cdefc-145">To use this parameter, the local and remote computers must be configured for remoting and, on Windows Vista and later versions of the Windows operating system, you must open PowerShell by using the **Run as administrator** option.</span></span> <span data-ttu-id="cdefc-146">Mer information finns i [about_Remote_Requirements](..//microsoft.powershell.core/about/about_remote_requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdefc-146">For more information, see [about_Remote_Requirements](..//microsoft.powershell.core/about/about_remote_requirements.md).</span></span>

<span data-ttu-id="cdefc-147">När du anger parametern **AsJob** returnerar kommandot omedelbart ett objekt som representerar bakgrunds jobbet.</span><span class="sxs-lookup"><span data-stu-id="cdefc-147">When you specify the **AsJob** parameter, the command immediately returns an object that represents the background job.</span></span> <span data-ttu-id="cdefc-148">Du kan fortsätta att arbeta i sessionen medan jobbet är klart.</span><span class="sxs-lookup"><span data-stu-id="cdefc-148">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="cdefc-149">Jobbet skapas på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cdefc-149">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="cdefc-150">Använd cmdleten för att hämta jobb resultatet `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="cdefc-150">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="cdefc-151">Mer information om PowerShell-bakgrunds jobb finns i [about_Jobs](..//microsoft.powershell.core/about/about_jobs.md) och [about_Remote_Jobs](../microsoft.powershell.core/about/about_remote_jobs.md).</span><span class="sxs-lookup"><span data-stu-id="cdefc-151">For more information about PowerShell background jobs, see [about_Jobs](..//microsoft.powershell.core/about/about_jobs.md) and [about_Remote_Jobs](../microsoft.powershell.core/about/about_remote_jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cdefc-152">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="cdefc-152">-ComputerName</span></span>

<span data-ttu-id="cdefc-153">Anger vilka datorer som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="cdefc-153">Specifies the computers to stop.</span></span> <span data-ttu-id="cdefc-154">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cdefc-154">The default is the local computer.</span></span>

<span data-ttu-id="cdefc-155">Ange NETBIOS-namn, IP-adress eller fullständigt kvalificerat domän namn för en eller flera datorer i en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="cdefc-155">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="cdefc-156">Om du vill ange den lokala datorn skriver du datorns namn eller localhost.</span><span class="sxs-lookup"><span data-stu-id="cdefc-156">To specify the local computer, type the computer name or localhost.</span></span>

<span data-ttu-id="cdefc-157">Den här parametern är inte beroende av PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="cdefc-157">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="cdefc-158">Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="cdefc-158">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cdefc-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cdefc-159">-Confirm</span></span>

<span data-ttu-id="cdefc-160">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="cdefc-160">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cdefc-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="cdefc-161">-Credential</span></span>

<span data-ttu-id="cdefc-162">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="cdefc-162">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="cdefc-163">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="cdefc-163">The default is the current user.</span></span>

<span data-ttu-id="cdefc-164">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="cdefc-164">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="cdefc-165">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="cdefc-165">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="cdefc-166">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="cdefc-166">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="cdefc-167">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="cdefc-167">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cdefc-168">-DcomAuthentication</span><span class="sxs-lookup"><span data-stu-id="cdefc-168">-DcomAuthentication</span></span>

<span data-ttu-id="cdefc-169">Anger den autentiseringsnivå som denna cmdlet använder med WMI.</span><span class="sxs-lookup"><span data-stu-id="cdefc-169">Specifies the authentication level that this cmdlet uses with WMI.</span></span> <span data-ttu-id="cdefc-170">`Stop-Computer` använder WMI.</span><span class="sxs-lookup"><span data-stu-id="cdefc-170">`Stop-Computer` uses WMI.</span></span> <span data-ttu-id="cdefc-171">Standardvärdet är **paket**.</span><span class="sxs-lookup"><span data-stu-id="cdefc-171">The default value is **Packet**.</span></span>

<span data-ttu-id="cdefc-172">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="cdefc-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="cdefc-173">**Standard** : Windows-autentisering.</span><span class="sxs-lookup"><span data-stu-id="cdefc-173">**Default** : Windows Authentication.</span></span>
- <span data-ttu-id="cdefc-174">**Ingen** : ingen com-autentisering.</span><span class="sxs-lookup"><span data-stu-id="cdefc-174">**None** : No COM authentication.</span></span>
- <span data-ttu-id="cdefc-175">**Anslut** : com-autentisering på anslutnings nivå.</span><span class="sxs-lookup"><span data-stu-id="cdefc-175">**Connect** : Connect-level COM authentication.</span></span>
- <span data-ttu-id="cdefc-176">**Anropa** : com-autentisering på anrops nivå.</span><span class="sxs-lookup"><span data-stu-id="cdefc-176">**Call** : Call-level COM authentication.</span></span>
- <span data-ttu-id="cdefc-177">**Paket** : com-autentisering på paket nivå.</span><span class="sxs-lookup"><span data-stu-id="cdefc-177">**Packet** : Packet-level COM authentication.</span></span>
- <span data-ttu-id="cdefc-178">**PacketIntegrity** : com-autentisering på paket integritets nivå.</span><span class="sxs-lookup"><span data-stu-id="cdefc-178">**PacketIntegrity** : Packet Integrity-level COM authentication.</span></span>
- <span data-ttu-id="cdefc-179">**PacketPrivacy** : com-autentisering på paket sekretess nivå.</span><span class="sxs-lookup"><span data-stu-id="cdefc-179">**PacketPrivacy** : Packet Privacy-level COM authentication.</span></span>
- <span data-ttu-id="cdefc-180">**Oförändrad** : samma som föregående kommando.</span><span class="sxs-lookup"><span data-stu-id="cdefc-180">**Unchanged** : Same as the previous command.</span></span>

<span data-ttu-id="cdefc-181">Mer information om värdena för den här parametern finns i [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel).</span><span class="sxs-lookup"><span data-stu-id="cdefc-181">For more information about the values of this parameter, see [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel).</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: Packet
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cdefc-182">-Force</span><span class="sxs-lookup"><span data-stu-id="cdefc-182">-Force</span></span>

<span data-ttu-id="cdefc-183">Tvingar fram en omedelbar avstängning av datorn.</span><span class="sxs-lookup"><span data-stu-id="cdefc-183">Forces an immediate shut down of the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cdefc-184">-Personifiering</span><span class="sxs-lookup"><span data-stu-id="cdefc-184">-Impersonation</span></span>

<span data-ttu-id="cdefc-185">Anger personifieringsnivån som ska användas när den här cmdleten anropar WMI.</span><span class="sxs-lookup"><span data-stu-id="cdefc-185">Specifies the impersonation level to use when this cmdlet calls WMI.</span></span> <span data-ttu-id="cdefc-186">Standardvärdet är **personifierat**.</span><span class="sxs-lookup"><span data-stu-id="cdefc-186">The default value is **Impersonate**.</span></span>

<span data-ttu-id="cdefc-187">`Stop-Computer` använder WMI.</span><span class="sxs-lookup"><span data-stu-id="cdefc-187">`Stop-Computer` uses WMI.</span></span> <span data-ttu-id="cdefc-188">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="cdefc-188">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="cdefc-189">**Standard** : standard-personifiering.</span><span class="sxs-lookup"><span data-stu-id="cdefc-189">**Default** : Default impersonation.</span></span>
- <span data-ttu-id="cdefc-190">**Anonym** : döljer anroparens identitet.</span><span class="sxs-lookup"><span data-stu-id="cdefc-190">**Anonymous** : Hides the identity of the caller.</span></span>
- <span data-ttu-id="cdefc-191">**Identifiera** : tillåter objekt att fråga om autentiseringsuppgifterna för anroparen.</span><span class="sxs-lookup"><span data-stu-id="cdefc-191">**Identify** : Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="cdefc-192">**Personifiera** : tillåter att objekt använder autentiseringsuppgifterna för anroparen.</span><span class="sxs-lookup"><span data-stu-id="cdefc-192">**Impersonate** : Allows objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: Impersonate
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cdefc-193">-Protocol</span><span class="sxs-lookup"><span data-stu-id="cdefc-193">-Protocol</span></span>

<span data-ttu-id="cdefc-194">Anger vilket protokoll som ska användas för att starta om datorerna.</span><span class="sxs-lookup"><span data-stu-id="cdefc-194">Specifies which protocol to use to restart the computers.</span></span> <span data-ttu-id="cdefc-195">De acceptabla värdena för den här parametern är: **WSMan** och **DCOM**.</span><span class="sxs-lookup"><span data-stu-id="cdefc-195">The acceptable values for this parameter are: **WSMan** and **DCOM**.</span></span> <span data-ttu-id="cdefc-196">Standardvärdet är **DCOM**.</span><span class="sxs-lookup"><span data-stu-id="cdefc-196">The default value is **DCOM**.</span></span>

<span data-ttu-id="cdefc-197">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cdefc-197">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: DCOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cdefc-198">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="cdefc-198">-ThrottleLimit</span></span>

<span data-ttu-id="cdefc-199">Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="cdefc-199">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="cdefc-200">Om du utelämnar den här parametern eller anger värdet 0, används standardvärdet 32.</span><span class="sxs-lookup"><span data-stu-id="cdefc-200">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="cdefc-201">Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.</span><span class="sxs-lookup"><span data-stu-id="cdefc-201">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cdefc-202">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="cdefc-202">-WsmanAuthentication</span></span>

<span data-ttu-id="cdefc-203">Anger den mekanism som används för att autentisera användarautentiseringsuppgifter när denna cmdlet använder WSMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="cdefc-203">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="cdefc-204">Standardvärdet är **default**.</span><span class="sxs-lookup"><span data-stu-id="cdefc-204">The default value is **Default**.</span></span>

<span data-ttu-id="cdefc-205">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="cdefc-205">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="cdefc-206">Basic</span><span class="sxs-lookup"><span data-stu-id="cdefc-206">Basic</span></span>
- <span data-ttu-id="cdefc-207">CredSSP</span><span class="sxs-lookup"><span data-stu-id="cdefc-207">CredSSP</span></span>
- <span data-ttu-id="cdefc-208">Default</span><span class="sxs-lookup"><span data-stu-id="cdefc-208">Default</span></span>
- <span data-ttu-id="cdefc-209">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="cdefc-209">Digest</span></span>
- <span data-ttu-id="cdefc-210">Kerberos</span><span class="sxs-lookup"><span data-stu-id="cdefc-210">Kerberos</span></span>
- <span data-ttu-id="cdefc-211">Fram.</span><span class="sxs-lookup"><span data-stu-id="cdefc-211">Negotiate.</span></span>

<span data-ttu-id="cdefc-212">Mer information om värdena för den här parametern finns i [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="cdefc-212">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="cdefc-213">Autentisering av Credential Security Service Provider (CredSSP), där användarautentiseringsuppgifterna skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="cdefc-213">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="cdefc-214">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="cdefc-214">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="cdefc-215">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="cdefc-215">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="cdefc-216">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cdefc-216">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cdefc-217">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cdefc-217">-WhatIf</span></span>

<span data-ttu-id="cdefc-218">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="cdefc-218">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="cdefc-219">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="cdefc-219">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cdefc-220">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cdefc-220">CommonParameters</span></span>

<span data-ttu-id="cdefc-221">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cdefc-221">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cdefc-222">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cdefc-222">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cdefc-223">INDATA</span><span class="sxs-lookup"><span data-stu-id="cdefc-223">INPUTS</span></span>

### <span data-ttu-id="cdefc-224">Inget</span><span class="sxs-lookup"><span data-stu-id="cdefc-224">None</span></span>

<span data-ttu-id="cdefc-225">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cdefc-225">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="cdefc-226">UTDATA</span><span class="sxs-lookup"><span data-stu-id="cdefc-226">OUTPUTS</span></span>

### <span data-ttu-id="cdefc-227">Ingen eller system. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="cdefc-227">None or System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="cdefc-228">Cmdleten returnerar ett **system. Management. Automation. RemotingJob** -objekt om du anger parametern **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="cdefc-228">The cmdlet returns a **System.Management.Automation.RemotingJob** object, if you specify the **AsJob** parameter.</span></span> <span data-ttu-id="cdefc-229">Annars genererar den inga utdata.</span><span class="sxs-lookup"><span data-stu-id="cdefc-229">Otherwise, it doesn't generate any output.</span></span>

## <span data-ttu-id="cdefc-230">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="cdefc-230">NOTES</span></span>

<span data-ttu-id="cdefc-231">Denna cmdlet använder metoden **Win32Shutdown** i klassen **Win32_OperatingSystem** WMI.</span><span class="sxs-lookup"><span data-stu-id="cdefc-231">This cmdlet uses the **Win32Shutdown** method of the **Win32_OperatingSystem** WMI class.</span></span> <span data-ttu-id="cdefc-232">Den här metoden kräver att **SeShutdownPrivilege** -behörighet aktive ras för det användar konto som används för att starta om datorn.</span><span class="sxs-lookup"><span data-stu-id="cdefc-232">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

## <span data-ttu-id="cdefc-233">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="cdefc-233">RELATED LINKS</span></span>

[<span data-ttu-id="cdefc-234">Lägg till dator</span><span class="sxs-lookup"><span data-stu-id="cdefc-234">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="cdefc-235">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="cdefc-235">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="cdefc-236">Ta bort dator</span><span class="sxs-lookup"><span data-stu-id="cdefc-236">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="cdefc-237">Byt namn – dator</span><span class="sxs-lookup"><span data-stu-id="cdefc-237">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="cdefc-238">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="cdefc-238">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="cdefc-239">Återställa-dator</span><span class="sxs-lookup"><span data-stu-id="cdefc-239">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="cdefc-240">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="cdefc-240">Test-Connection</span></span>](Test-Connection.md)
