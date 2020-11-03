---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WmiObject
ms.openlocfilehash: 287eb02e7de2f4182e0ecfd7f6b6a7cafb66969e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265473"
---
# <span data-ttu-id="7bdb0-103">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="7bdb0-103">Remove-WmiObject</span></span>

## <span data-ttu-id="7bdb0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7bdb0-104">SYNOPSIS</span></span>
<span data-ttu-id="7bdb0-105">Tar bort en instans av en befintlig Windows Management Instrumentation (WMI)-klass.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-105">Deletes an instance of an existing Windows Management Instrumentation (WMI) class.</span></span>

## <span data-ttu-id="7bdb0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7bdb0-106">SYNTAX</span></span>

### <span data-ttu-id="7bdb0-107">klass (standard)</span><span class="sxs-lookup"><span data-stu-id="7bdb0-107">class (Default)</span></span>

```
Remove-WmiObject [-Class] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7bdb0-108">objekt</span><span class="sxs-lookup"><span data-stu-id="7bdb0-108">object</span></span>

```
Remove-WmiObject -InputObject <ManagementObject> [-AsJob] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="7bdb0-109">path</span><span class="sxs-lookup"><span data-stu-id="7bdb0-109">path</span></span>

```
Remove-WmiObject -Path <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7bdb0-110">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="7bdb0-110">WQLQuery</span></span>

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="7bdb0-111">DocumentDB</span><span class="sxs-lookup"><span data-stu-id="7bdb0-111">query</span></span>

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="7bdb0-112">lista</span><span class="sxs-lookup"><span data-stu-id="7bdb0-112">list</span></span>

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="7bdb0-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7bdb0-113">DESCRIPTION</span></span>
<span data-ttu-id="7bdb0-114">Cmdlet: en **Remove-WmiObject** tar bort en instans av en befintlig Windows Management INSTRUMENTATION (WMI)-klass.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-114">The **Remove-WmiObject** cmdlet deletes an instance of an existing Windows Management Instrumentation (WMI)class.</span></span>

## <span data-ttu-id="7bdb0-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7bdb0-115">EXAMPLES</span></span>

### <span data-ttu-id="7bdb0-116">Exempel 1: Stäng alla instanser av en Win32-process</span><span class="sxs-lookup"><span data-stu-id="7bdb0-116">Example 1: Close all instances of a Win32 process</span></span>

```
PS C:\> notepad
PS C:\> $np = Get-WmiObject -Query "select * from win32_process where name='notepad.exe'"
PS C:\> $np | Remove-WmiObject
```

<span data-ttu-id="7bdb0-117">I det här exemplet stängs alla instanser av Notepad.exe.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-117">This example closes all the instances of Notepad.exe.</span></span>

<span data-ttu-id="7bdb0-118">Det första kommandot startar en instans av Notepad.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-118">The first command starts an instance of Notepad.</span></span>

<span data-ttu-id="7bdb0-119">Det andra kommandot använder cmdleten Get-WmiObject för att hämta instanserna av Win32_Process som motsvarar Notepad.exe och lagrar dem sedan i $np variabeln.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-119">The second command uses the Get-WmiObject cmdlet to retrieve the instances of the Win32_Process that correspond to Notepad.exe, and then stores them in the $np variable.</span></span>

<span data-ttu-id="7bdb0-120">Det tredje kommandot skickar objektet i $np-variabeln till **Remove-WmiObject** , som tar bort alla instanser av Notepad.exe.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-120">The third command passes the object in the $np variable to **Remove-WmiObject** , which deletes all the instances of Notepad.exe.</span></span>

### <span data-ttu-id="7bdb0-121">Exempel 2: ta bort en mapp</span><span class="sxs-lookup"><span data-stu-id="7bdb0-121">Example 2: Delete a folder</span></span>

```
PS C:\> $a = Get-WMIObject -Query "Select * From Win32_Directory Where Name ='C:\\Test'"
PS C:\> $a | Remove-WMIObject
```

<span data-ttu-id="7bdb0-122">Detta kommando tar bort mappen C:\Test.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-122">This command deletes the C:\Test folder.</span></span>

<span data-ttu-id="7bdb0-123">Det första kommandot använder **Get-WMIObject** för att fråga efter mappen C:\Test och lagrar sedan objektet i variabeln $a.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-123">The first command uses **Get-WMIObject** to query for the C:\Test folder, and then stores the object in the $a variable.</span></span>

<span data-ttu-id="7bdb0-124">Det andra kommandot rör $a-variabeln som **Remove-WMIObject** , som tar bort mappen.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-124">The second command pipes the $a variable to **Remove-WMIObject** , which deletes the folder.</span></span>

## <span data-ttu-id="7bdb0-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7bdb0-125">PARAMETERS</span></span>

### <span data-ttu-id="7bdb0-126">– AsJob</span><span class="sxs-lookup"><span data-stu-id="7bdb0-126">-AsJob</span></span>
<span data-ttu-id="7bdb0-127">Anger att denna cmdlet körs som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-127">Indicates that this cmdlet run as a background job.</span></span>
<span data-ttu-id="7bdb0-128">Använd den här parametern för att köra kommandon som tar lång tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-128">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="7bdb0-129">Nya CIM-cmdletar, introducerade Windows PowerShell 3,0, utför samma uppgifter som WMI-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-129">New CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span>
<span data-ttu-id="7bdb0-130">CIM-cmdlets följer WS-Management (WSMan)-standarder och med Common Information Model (CIM) standard, vilket gör att cmdletarna kan använda samma metoder för att hantera datorer som kör Windows-operativsystemet och de som kör andra operativ system.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-130">The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard, which enables the cmdlets to use the same techniques to manage computers that run the Windows operating system and those running other operating systems.</span></span>
<span data-ttu-id="7bdb0-131">Överväg att använda cmdleten Remove-CimInstance i stället för att använda **Remove-WmiObject** https://go.microsoft.com/fwlink/?LinkId=227964 .</span><span class="sxs-lookup"><span data-stu-id="7bdb0-131">Instead of using **Remove-WmiObject** , consider using the Remove-CimInstancehttps://go.microsoft.com/fwlink/?LinkId=227964 cmdlet.</span></span>

<span data-ttu-id="7bdb0-132">När du använder parametern *AsJob* returnerar kommandot ett objekt som representerar bakgrunds jobbet och visar sedan kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-132">When you use the *AsJob* parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span>
<span data-ttu-id="7bdb0-133">Du kan fortsätta att arbeta i sessionen medan jobbet är klart.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-133">You can continue to work in the session while the job finishes.</span></span>
<span data-ttu-id="7bdb0-134">Om **Remove-WmiObject** används mot en fjärrdator, skapas jobbet på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-134">If **Remove-WmiObject** is used against a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="7bdb0-135">Om du vill hantera jobbet använder du de cmdlet: ar som innehåller **jobbet** Substantiv ( **jobb** -cmdletarna).</span><span class="sxs-lookup"><span data-stu-id="7bdb0-135">To manage the job, use the cmdlets that contain the **Job** noun (the **Job** cmdlets).</span></span>
<span data-ttu-id="7bdb0-136">Använd Receive-Job-cmdleten för att hämta jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-136">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="7bdb0-137">Om du vill använda den här parametern för fjärrdatorer måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-137">To use this parameter for remote computers, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="7bdb0-138">Starta Windows PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-138">Start Windows PowerShell by using the Run as administrator option.</span></span>
<span data-ttu-id="7bdb0-139">Mer information finns i about_Remote_Requirements.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-139">For more information, see about_Remote_Requirements.</span></span>

<span data-ttu-id="7bdb0-140">Mer information om bakgrunds jobb i Windows PowerShell finns i about_Jobs och about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-140">For more information about Windows PowerShell background jobs, see about_Jobs and about_Remote_Jobs.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bdb0-141">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="7bdb0-141">-Authentication</span></span>
<span data-ttu-id="7bdb0-142">Anger den autentiseringsnivå som ska användas för WMI-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-142">Specifies the authentication level to use for the WMI connection.</span></span>
<span data-ttu-id="7bdb0-143">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="7bdb0-143">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7bdb0-144">-1: oförändrad.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-144">-1: Unchanged.</span></span>
- <span data-ttu-id="7bdb0-145">0: standard.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-145">0: Default.</span></span>
- <span data-ttu-id="7bdb0-146">1: ingen.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-146">1: None.</span></span>
<span data-ttu-id="7bdb0-147">Ingen autentisering utförs.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-147">No authentication in performed.</span></span>
- <span data-ttu-id="7bdb0-148">2: Anslut.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-148">2: Connect.</span></span>
<span data-ttu-id="7bdb0-149">Autentisering utförs endast när klienten upprättar en relation med programmet.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-149">Authentication is performed only when the client establishes a relationship with the application.</span></span>
- <span data-ttu-id="7bdb0-150">3: anropa.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-150">3: Call.</span></span>
<span data-ttu-id="7bdb0-151">Autentisering utförs endast i början av varje anrop när programmet tar emot begäran.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-151">Authentication is performed only at the start of each call when the application receives the request.</span></span>
- <span data-ttu-id="7bdb0-152">4: paket.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-152">4: Packet.</span></span>
<span data-ttu-id="7bdb0-153">Autentisering utförs på alla data som tas emot från klienten.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-153">Authentication is performed on all the data that is received from the client.</span></span>
- <span data-ttu-id="7bdb0-154">5: PacketIntegrity.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-154">5: PacketIntegrity.</span></span>
<span data-ttu-id="7bdb0-155">Alla data som överförs mellan klienten och programmet autentiseras och verifieras.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-155">All the data that is transferred between the client and the application is authenticated and verified.</span></span>
- <span data-ttu-id="7bdb0-156">6: PacketPrivacy.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-156">6: PacketPrivacy.</span></span>
<span data-ttu-id="7bdb0-157">Egenskaperna för de andra autentiseringsnivåer används och alla data krypteras.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-157">The properties of the other authentication levels are used, and all the data is encrypted.</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bdb0-158">-Authority</span><span class="sxs-lookup"><span data-stu-id="7bdb0-158">-Authority</span></span>
<span data-ttu-id="7bdb0-159">Anger den auktoritet som ska användas för att autentisera WMI-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-159">Specifies the authority to use to authenticate the WMI connection.</span></span>
<span data-ttu-id="7bdb0-160">Du kan ange standard-NTLM eller Kerberos-autentisering.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-160">You can specify standard NTLM or Kerberos authentication.</span></span>
<span data-ttu-id="7bdb0-161">Om du vill använda NTLM ställer du in inställningen auktoritet på ntlmdomain: \<DomainName\> , där \<DomainName\> identifierar ett giltigt NTLM-domännamn.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-161">To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.</span></span>
<span data-ttu-id="7bdb0-162">Ange Kerberos om du vill använda Kerberos: \<DomainName\> \\ \<ServerName\> .</span><span class="sxs-lookup"><span data-stu-id="7bdb0-162">To use Kerberos, specify kerberos:\<DomainName\>\\\<ServerName\>.</span></span>
<span data-ttu-id="7bdb0-163">Du kan inte inkludera auktoritets inställningen när du ansluter till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-163">You cannot include the authority setting when you connect to the local computer.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bdb0-164">– Klass</span><span class="sxs-lookup"><span data-stu-id="7bdb0-164">-Class</span></span>
<span data-ttu-id="7bdb0-165">Anger namnet på en WMI-klass som denna cmdlet tar bort.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-165">Specifies the name of a WMI class that this cmdlet deletes.</span></span>

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bdb0-166">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="7bdb0-166">-ComputerName</span></span>
<span data-ttu-id="7bdb0-167">Anger namnet på den dator där cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-167">Specifies the name of the computer on which this cmdlet runs.</span></span>
<span data-ttu-id="7bdb0-168">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-168">The default is the local computer.</span></span>

<span data-ttu-id="7bdb0-169">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera datorer.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-169">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.</span></span>
<span data-ttu-id="7bdb0-170">Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller localhost.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-170">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="7bdb0-171">Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-171">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="7bdb0-172">Du kan använda parametern *computername* även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-172">You can use the *ComputerName* parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bdb0-173">-Credential</span><span class="sxs-lookup"><span data-stu-id="7bdb0-173">-Credential</span></span>
<span data-ttu-id="7bdb0-174">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-174">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="7bdb0-175">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-175">The default is the current user.</span></span>

<span data-ttu-id="7bdb0-176">Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, till exempel ett som genereras av Get-Credential cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-176">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="7bdb0-177">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-177">If you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bdb0-178">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="7bdb0-178">-EnableAllPrivileges</span></span>
<span data-ttu-id="7bdb0-179">Anger att denna cmdlet aktiverar alla behörigheter för den aktuella användaren innan det kommando som gör WMI-anropet.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-179">Indicates that this cmdlet enables all the permissions of the current user before the command it makes the WMI call.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bdb0-180">-Personifiering</span><span class="sxs-lookup"><span data-stu-id="7bdb0-180">-Impersonation</span></span>
<span data-ttu-id="7bdb0-181">Anger personifieringsnivån som ska användas.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-181">Specifies the impersonation level to use.</span></span>
<span data-ttu-id="7bdb0-182">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="7bdb0-182">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7bdb0-183">0: standard.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-183">0: Default.</span></span>
<span data-ttu-id="7bdb0-184">Läser det lokala registret för standard personifieringsnivån, som vanligt vis anges till 3: personifiera.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-184">Reads the local registry for the default impersonation level, which is usually set to 3: Impersonate.</span></span>
- <span data-ttu-id="7bdb0-185">1: Anonym.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-185">1: Anonymous.</span></span>
<span data-ttu-id="7bdb0-186">Döljer anroparens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-186">Hides the credentials of the caller.</span></span>
- <span data-ttu-id="7bdb0-187">2: identifiera.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-187">2: Identify.</span></span>
<span data-ttu-id="7bdb0-188">Tillåter att objekt frågar efter anroparens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-188">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="7bdb0-189">3: personifiera.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-189">3: Impersonate.</span></span>
<span data-ttu-id="7bdb0-190">Tillåter att objekt använder autentiseringsuppgifterna för anroparen.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-190">Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="7bdb0-191">4: delegera.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-191">4: Delegate.</span></span>
<span data-ttu-id="7bdb0-192">Tillåter objekt att tillåta att andra objekt använder autentiseringsuppgifterna för anroparen.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-192">Allows objects to permit other objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bdb0-193">– InputObject</span><span class="sxs-lookup"><span data-stu-id="7bdb0-193">-InputObject</span></span>
<span data-ttu-id="7bdb0-194">Anger ett **ManagementObject** -objekt som ska användas som indatamängd.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-194">Specifies a **ManagementObject** object to use as input.</span></span>
<span data-ttu-id="7bdb0-195">När den här parametern används ignoreras alla andra parametrar.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-195">When this parameter is used, all other parameters are ignored.</span></span>

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7bdb0-196">-Locale</span><span class="sxs-lookup"><span data-stu-id="7bdb0-196">-Locale</span></span>
<span data-ttu-id="7bdb0-197">Anger det önskade språket för WMI-objekt.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-197">Specifies the preferred locale for WMI objects.</span></span>
<span data-ttu-id="7bdb0-198">Parametern *locale* anges som en matris i MS_ \<LCID\> formatet i den ordning som du föredrar.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-198">The *Locale* parameter is specified as an array in the MS_\<LCID\> format in the preferred order.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bdb0-199">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="7bdb0-199">-Namespace</span></span>
<span data-ttu-id="7bdb0-200">Anger namn området för WMI-lagringsplatsen där den refererade WMI-klassen finns när den används med *klass* parametern.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-200">Specifies the WMI repository namespace where the referenced WMI class is located when it is used with the *Class* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bdb0-201">-Path</span><span class="sxs-lookup"><span data-stu-id="7bdb0-201">-Path</span></span>
<span data-ttu-id="7bdb0-202">Anger WMI-objektets sökväg för en WMI-klass, eller anger sökvägen till WMI-objektet för en instans av en WMI-klass som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-202">Specifies the WMI object path of a WMI class, or specifies the WMI object path of an instance of a WMI class to delete.</span></span>

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7bdb0-203">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="7bdb0-203">-ThrottleLimit</span></span>
<span data-ttu-id="7bdb0-204">Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-204">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="7bdb0-205">Den här parametern används tillsammans med parametern *AsJob* .</span><span class="sxs-lookup"><span data-stu-id="7bdb0-205">This parameter is used together with the *AsJob* parameter.</span></span>
<span data-ttu-id="7bdb0-206">Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-206">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="7bdb0-207">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7bdb0-207">-Confirm</span></span>
<span data-ttu-id="7bdb0-208">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-208">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7bdb0-209">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7bdb0-209">-WhatIf</span></span>
<span data-ttu-id="7bdb0-210">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-210">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7bdb0-211">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-211">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7bdb0-212">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7bdb0-212">CommonParameters</span></span>
<span data-ttu-id="7bdb0-213">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-213">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7bdb0-214">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7bdb0-214">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7bdb0-215">INDATA</span><span class="sxs-lookup"><span data-stu-id="7bdb0-215">INPUTS</span></span>

### <span data-ttu-id="7bdb0-216">System. Management. ManagementObject</span><span class="sxs-lookup"><span data-stu-id="7bdb0-216">System.Management.ManagementObject</span></span>
<span data-ttu-id="7bdb0-217">Du kan skicka vidare ett hanterings objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-217">You can pipe a management object to this cmdlet.</span></span>

## <span data-ttu-id="7bdb0-218">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7bdb0-218">OUTPUTS</span></span>

### <span data-ttu-id="7bdb0-219">Ingen, system. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="7bdb0-219">None, System.Management.Automation.RemotingJob</span></span>
<span data-ttu-id="7bdb0-220">Den här cmdleten returnerar ett jobb objekt, om du anger parametern *AsJob* .</span><span class="sxs-lookup"><span data-stu-id="7bdb0-220">This cmdlet returns a job object, if you specify the *AsJob* parameter.</span></span>
<span data-ttu-id="7bdb0-221">Annars genererar den inga utdata.</span><span class="sxs-lookup"><span data-stu-id="7bdb0-221">Otherwise, it does not generate any output.</span></span>

## <span data-ttu-id="7bdb0-222">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7bdb0-222">NOTES</span></span>

## <span data-ttu-id="7bdb0-223">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7bdb0-223">RELATED LINKS</span></span>

[<span data-ttu-id="7bdb0-224">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="7bdb0-224">Get-WmiObject</span></span>](Get-WmiObject.md)

[<span data-ttu-id="7bdb0-225">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="7bdb0-225">Invoke-WmiMethod</span></span>](Invoke-WmiMethod.md)

[<span data-ttu-id="7bdb0-226">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="7bdb0-226">Set-WmiInstance</span></span>](Set-WmiInstance.md)
