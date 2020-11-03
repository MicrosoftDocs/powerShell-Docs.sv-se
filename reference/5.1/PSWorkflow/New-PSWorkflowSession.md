---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflow
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowSession
ms.openlocfilehash: 995dd8a6df3ac8ebd7a204d2aefef3fa6aa71e14
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264602"
---
# <span data-ttu-id="9594f-103">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="9594f-103">New-PSWorkflowSession</span></span>

## <span data-ttu-id="9594f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9594f-104">SYNOPSIS</span></span>
<span data-ttu-id="9594f-105">Skapar en arbets flödes session.</span><span class="sxs-lookup"><span data-stu-id="9594f-105">Creates a workflow session.</span></span>

## <span data-ttu-id="9594f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9594f-106">SYNTAX</span></span>

```
New-PSWorkflowSession [[-ComputerName] <String[]>] [-Credential <Object>] [-Name <String[]>] [-Port <Int32>]
 [-UseSSL] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-EnableNetworkAccess]
 [<CommonParameters>]
```

## <span data-ttu-id="9594f-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9594f-107">DESCRIPTION</span></span>

<span data-ttu-id="9594f-108">`New-PSWorkflowSession`Cmdlet: en skapar en **PSSession** (User-Managed session) som är särskilt utformad för att köra Windows PowerShell-arbetsflöden.</span><span class="sxs-lookup"><span data-stu-id="9594f-108">The `New-PSWorkflowSession` cmdlet creates a user-managed session ( **PSSession** ) that is especially designed for running Windows PowerShell workflows.</span></span> <span data-ttu-id="9594f-109">Konfigurationen för Microsoft. PowerShell. Workflow-sessionen används, som innehåller skript, typ och formatering av filer och alternativ som krävs för arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="9594f-109">It uses the Microsoft.PowerShell.Workflow session configuration, which includes scripts, type and formatting files, and options that are required for workflows.</span></span>

<span data-ttu-id="9594f-110">Du kan använda `New-PSWorkflowSession` eller dess alias `nwsn` .</span><span class="sxs-lookup"><span data-stu-id="9594f-110">You can use `New-PSWorkflowSession` or its alias, `nwsn`.</span></span>

<span data-ttu-id="9594f-111">Du kan också lägga till gemensamma parametrar för arbets flöden i det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="9594f-111">You can also add workflow common parameters to this command.</span></span> <span data-ttu-id="9594f-112">Mer information om gemensamma parametrar för arbets flöden finns i [about_WorkflowCommonParameters](./about/about_WorkflowCommonParameters.md)</span><span class="sxs-lookup"><span data-stu-id="9594f-112">For more information about workflow common parameters, see [about_WorkflowCommonParameters](./about/about_WorkflowCommonParameters.md)</span></span>

<span data-ttu-id="9594f-113">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9594f-113">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="9594f-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9594f-114">EXAMPLES</span></span>

### <span data-ttu-id="9594f-115">Exempel 1: skapa en arbets flödes session på en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="9594f-115">Example 1: Create a workflow session on a remote computer</span></span>

<span data-ttu-id="9594f-116">I det här exemplet skapas en **WorkflowTests** -session på ServerNode01-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="9594f-116">This example creates the **WorkflowTests** session on the ServerNode01 remote computer.</span></span>

```powershell
$params = @{
    ComputerName = "ServerNode01"
    Name = "WorkflowTests"
    SessionOption = (New-PSSessionOption -OutputBufferingMode Drop)
}
New-PSWorkflowSession @params
```

<span data-ttu-id="9594f-117">Värdet för parametern **SessionOption** är ett `New-PSSessionOption` kommando som ställer in buffrings läget för utdata i sessionen för att **släppa**.</span><span class="sxs-lookup"><span data-stu-id="9594f-117">The value of the **SessionOption** parameter is a `New-PSSessionOption` command that sets the output buffering mode in the session to **Drop**.</span></span>

### <span data-ttu-id="9594f-118">Exempel 2: skapa arbets flödes sessioner på flera fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="9594f-118">Example 2: Create workflow sessions on multiple remote computers</span></span>

<span data-ttu-id="9594f-119">I det här exemplet skapas arbets flödes sessioner på ServerNode01-och Server12-datorerna.</span><span class="sxs-lookup"><span data-stu-id="9594f-119">This example creates workflow sessions on the ServerNode01 and Server12 computers.</span></span> <span data-ttu-id="9594f-120">Kommandot använder parametern **Credential** för att köras med behörigheterna för domän administratören.</span><span class="sxs-lookup"><span data-stu-id="9594f-120">The command uses the **Credential** parameter to run with the permissions of the domain administrator.</span></span>

```powershell
"ServerNode01", "Server12" |
    New-PSWorkflowSession -Name WorkflowSession -Credential Domain01\Admin01 -ThrottleLimit 150
```

<span data-ttu-id="9594f-121">Kommandot använder parametern **ThrottleLimit** för att öka begränsningen per kommando till 150.</span><span class="sxs-lookup"><span data-stu-id="9594f-121">The command uses the **ThrottleLimit** parameter to increase the per-command throttle limit to 150.</span></span>
<span data-ttu-id="9594f-122">Värdet prioriteras över standard begränsningen på 100 som anges i konfigurationen för **Microsoft. PowerShell. Workflow** -sessionen.</span><span class="sxs-lookup"><span data-stu-id="9594f-122">This value takes precedence over the default throttle limit of 100 that is set in the **Microsoft.PowerShell.Workflow** session configuration.</span></span>

## <span data-ttu-id="9594f-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9594f-123">PARAMETERS</span></span>

### <span data-ttu-id="9594f-124">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="9594f-124">-ApplicationName</span></span>

<span data-ttu-id="9594f-125">Anger program namns segmentet för anslutnings-URI: n.</span><span class="sxs-lookup"><span data-stu-id="9594f-125">Specifies the application name segment of the connection URI.</span></span>

<span data-ttu-id="9594f-126">Standardvärdet är värdet för Preference- `$PSSessionApplicationName` variabeln på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9594f-126">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="9594f-127">Om den här preferens variabeln inte definieras är standardvärdet WSMAN.</span><span class="sxs-lookup"><span data-stu-id="9594f-127">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="9594f-128">Det här värdet är lämpligt för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="9594f-128">This value is appropriate for most uses.</span></span> <span data-ttu-id="9594f-129">Mer information finns i [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="9594f-129">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="9594f-130">WinRM-tjänsten använder program namnet för att välja en lyssnare som ska betjäna anslutningsbegäran.</span><span class="sxs-lookup"><span data-stu-id="9594f-130">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="9594f-131">Värdet för den här parametern ska matcha värdet på egenskapen **URLPrefix** för en lyssnare på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="9594f-131">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9594f-132">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="9594f-132">-Authentication</span></span>

<span data-ttu-id="9594f-133">Anger den mekanism som används för att autentisera användarautentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="9594f-133">Specifies the mechanism that is used to authenticate the user credentials.</span></span>
<span data-ttu-id="9594f-134">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="9594f-134">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9594f-135">Default</span><span class="sxs-lookup"><span data-stu-id="9594f-135">Default</span></span>
- <span data-ttu-id="9594f-136">Basic</span><span class="sxs-lookup"><span data-stu-id="9594f-136">Basic</span></span>
- <span data-ttu-id="9594f-137">CredSSP</span><span class="sxs-lookup"><span data-stu-id="9594f-137">Credssp</span></span>
- <span data-ttu-id="9594f-138">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="9594f-138">Digest</span></span>
- <span data-ttu-id="9594f-139">Kerberos</span><span class="sxs-lookup"><span data-stu-id="9594f-139">Kerberos</span></span>
- <span data-ttu-id="9594f-140">Negotiate</span><span class="sxs-lookup"><span data-stu-id="9594f-140">Negotiate</span></span>
- <span data-ttu-id="9594f-141">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="9594f-141">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="9594f-142">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="9594f-142">The default value is Default.</span></span>

<span data-ttu-id="9594f-143">CredSSP-autentisering är endast tillgängligt i Windows Vista, Windows Server 2008 och senare versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="9594f-143">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="9594f-144">Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="9594f-144">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="9594f-145">Autentisering av Credential Security Service Provider (CredSSP), där användarautentiseringsuppgifterna skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="9594f-145">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="9594f-146">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="9594f-146">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="9594f-147">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="9594f-147">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9594f-148">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="9594f-148">-CertificateThumbprint</span></span>

<span data-ttu-id="9594f-149">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="9594f-149">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="9594f-150">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="9594f-150">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="9594f-151">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="9594f-151">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="9594f-152">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="9594f-152">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="9594f-153">Om du vill hämta ett tumavtryck för certifikatet använder du `Get-Item` cmdleten eller `Get-ChildItem` cmdleten i Windows PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="9594f-153">To get a certificate thumbprint, use the `Get-Item` cmdlet or the `Get-ChildItem` cmdlet in the Windows PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9594f-154">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="9594f-154">-ComputerName</span></span>

<span data-ttu-id="9594f-155">Skapar en permanent anslutning ( **PSSession** ) till den angivna datorn.</span><span class="sxs-lookup"><span data-stu-id="9594f-155">Creates a persistent connection ( **PSSession** ) to the specified computer.</span></span> <span data-ttu-id="9594f-156">Om du anger flera dator namn skapar Windows PowerShell flera **PSSessions** , en för varje dator.</span><span class="sxs-lookup"><span data-stu-id="9594f-156">If you enter multiple computer names, Windows PowerShell creates multiple **PSSessions** , one for each computer.</span></span> <span data-ttu-id="9594f-157">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9594f-157">The default is the local computer.</span></span>

<span data-ttu-id="9594f-158">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="9594f-158">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span> <span data-ttu-id="9594f-159">Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.).</span><span class="sxs-lookup"><span data-stu-id="9594f-159">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span> <span data-ttu-id="9594f-160">När datorn finns i en annan domän än användaren, krävs det fullständigt kvalificerade domän namnet.</span><span class="sxs-lookup"><span data-stu-id="9594f-160">When the computer is in a different domain than the user, the fully qualified domain name is required.</span></span> <span data-ttu-id="9594f-161">Du kan också skicka ett dator namn inom citat tecken till `New-PSWorkflowSession` .</span><span class="sxs-lookup"><span data-stu-id="9594f-161">You can also pipe a computer name, in quotation marks to `New-PSWorkflowSession`.</span></span>

<span data-ttu-id="9594f-162">Om du vill använda en IP-adress i värdet för parametern **computername** måste kommandot innehålla parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="9594f-162">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="9594f-163">Dessutom måste datorn konfigureras för HTTPS-transport eller fjärrdatorns IP-adress måste ingå i listan WinRM TrustedHosts på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9594f-163">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="9594f-164">Instruktioner för att lägga till ett dator namn i listan TrustedHosts finns i avsnittet om hur du lägger till en dator i listan över betrodda värdar i [about_Remote_Troubleshooting](../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="9594f-164">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9594f-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="9594f-165">-Credential</span></span>

<span data-ttu-id="9594f-166">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="9594f-166">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="9594f-167">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="9594f-167">The default is the current user.</span></span> <span data-ttu-id="9594f-168">Ange ett användar namn, till exempel user01, Domain01\User01 eller User@Domain.com , eller ange ett **PSCredential** -objekt, till exempel ett som returneras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9594f-168">Type a user name, such as User01, Domain01\User01, or User@Domain.com, or enter a **PSCredential** object, such as one returned by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="9594f-169">När du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9594f-169">When you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9594f-170">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="9594f-170">-EnableNetworkAccess</span></span>

<span data-ttu-id="9594f-171">Anger att denna cmdlet lägger till en interaktiv säkerhetstoken till loopback-sessioner.</span><span class="sxs-lookup"><span data-stu-id="9594f-171">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="9594f-172">Med den interaktiva token kan du köra kommandon i loopback-sessionen som hämtar data från andra datorer.</span><span class="sxs-lookup"><span data-stu-id="9594f-172">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="9594f-173">Du kan till exempel köra ett kommando i sessionen som kopierar XML-filer från en fjärrdator till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9594f-173">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="9594f-174">En loopback-session är en **PSSession** som kommer från och slutar på samma dator.</span><span class="sxs-lookup"><span data-stu-id="9594f-174">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="9594f-175">Om du vill skapa en loopback-session ska du inte ange parametern **computername** eller ange värdet för punkt, localhost eller namnet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9594f-175">To create a loopback session, do not specify the **ComputerName** parameter or set its value to dot, localhost, or the name of the local computer.</span></span>

<span data-ttu-id="9594f-176">Som standard skapas loopback-sessioner som har en nätverks-token som kanske inte ger behörighet att autentisera till fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="9594f-176">By default, loopback sessions are created that have a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="9594f-177">Parametern **EnableNetworkAccess** är endast effektiv i loopback-sessioner.</span><span class="sxs-lookup"><span data-stu-id="9594f-177">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="9594f-178">Om du anger parametern **EnableNetworkAccess** när du skapar en session på en fjärrdator, lyckas kommandot, men parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="9594f-178">If you specify the **EnableNetworkAccess** parameter when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="9594f-179">Du kan också tillåta fjärråtkomst i en loopback-session med hjälp av **CredSSP** -värdet för parametern **Authentication** , som delegerar autentiseringsuppgifterna för sessionen till andra datorer.</span><span class="sxs-lookup"><span data-stu-id="9594f-179">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="9594f-180">För att skydda datorn från skadlig åtkomst, frånkopplade loopback-sessioner som har interaktiva tokens, kan de som skapats med hjälp av parametern **EnableNetworkAccess** bara återanslutas från den dator där sessionen skapades.</span><span class="sxs-lookup"><span data-stu-id="9594f-180">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, those created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="9594f-181">Frånkopplade sessioner som använder CredSSP-autentisering kan återanslutas från andra datorer.</span><span class="sxs-lookup"><span data-stu-id="9594f-181">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="9594f-182">Mer information finns i `Disconnect-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9594f-182">For more information, see the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="9594f-183">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9594f-183">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="9594f-184">-Name</span><span class="sxs-lookup"><span data-stu-id="9594f-184">-Name</span></span>

<span data-ttu-id="9594f-185">Anger ett eget namn för arbets flödes sessionen.</span><span class="sxs-lookup"><span data-stu-id="9594f-185">Specifies a friendly name for the workflow session.</span></span> <span data-ttu-id="9594f-186">Du kan använda namnet med andra cmdletar, till exempel `Get-PSSession` och `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="9594f-186">You can use the name with other cmdlets, such as `Get-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="9594f-187">Namnet måste inte vara unikt för datorn eller den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9594f-187">The name is not required to be unique to the computer or the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Session#
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9594f-188">-Port</span><span class="sxs-lookup"><span data-stu-id="9594f-188">-Port</span></span>

<span data-ttu-id="9594f-189">Anger nätverks porten på den fjärrdator som används för den här anslutningen.</span><span class="sxs-lookup"><span data-stu-id="9594f-189">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="9594f-190">Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder.</span><span class="sxs-lookup"><span data-stu-id="9594f-190">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="9594f-191">Standard portarna är 5985 (WinRM-port för HTTP) och 5986 (WinRM-port för HTTPS).</span><span class="sxs-lookup"><span data-stu-id="9594f-191">The default ports are 5985 (WinRM port for HTTP) and 5986 (WinRM port for HTTPS).</span></span>

<span data-ttu-id="9594f-192">Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten.</span><span class="sxs-lookup"><span data-stu-id="9594f-192">Before using another port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="9594f-193">Använd följande kommandon för att konfigurera lyssnaren:</span><span class="sxs-lookup"><span data-stu-id="9594f-193">Use the following commands to configure the listener:</span></span>

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="9594f-194">Använd inte **port** parametern om du inte behöver.</span><span class="sxs-lookup"><span data-stu-id="9594f-194">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="9594f-195">Port inställningen i kommandot gäller för alla datorer eller sessioner där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="9594f-195">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="9594f-196">En alternativ port inställning kan hindra kommandot från att köras på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="9594f-196">An alternate port setting might prevent the command from running on all computers.</span></span>

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

### <span data-ttu-id="9594f-197">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="9594f-197">-SessionOption</span></span>

<span data-ttu-id="9594f-198">Anger avancerade alternativ för sessionen.</span><span class="sxs-lookup"><span data-stu-id="9594f-198">Specifies advanced options for the session.</span></span> <span data-ttu-id="9594f-199">Ange ett **SessionOption** -objekt, till exempel ett som du skapar med hjälp av `New-PSSessionOption` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9594f-199">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet.</span></span>

<span data-ttu-id="9594f-200">Standardvärdena för alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts.</span><span class="sxs-lookup"><span data-stu-id="9594f-200">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="9594f-201">Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="9594f-201">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="9594f-202">Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i `$PSSessionOption` variabeln Preference och i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="9594f-202">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="9594f-203">De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="9594f-203">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span> <span data-ttu-id="9594f-204">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="9594f-204">For more information about session configurations, see [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="9594f-205">En beskrivning av sessions alternativen, inklusive standardvärdena, finns i `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="9594f-205">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="9594f-206">Information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="9594f-206">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9594f-207">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="9594f-207">-ThrottleLimit</span></span>

<span data-ttu-id="9594f-208">Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="9594f-208">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="9594f-209">Om du utelämnar den här parametern eller anger värdet 0 (noll) används standardvärdet för konfigurationen av **Microsoft. PowerShellWorkflow** -sessionen, 100.</span><span class="sxs-lookup"><span data-stu-id="9594f-209">If you omit this parameter or enter a value of 0 (zero), the default value for the **Microsoft.PowerShellWorkflow** session configuration, 100, is used.</span></span>

<span data-ttu-id="9594f-210">Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.</span><span class="sxs-lookup"><span data-stu-id="9594f-210">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9594f-211">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="9594f-211">-UseSSL</span></span>

<span data-ttu-id="9594f-212">Anger att denna cmdlet använder Secure Sockets Layer-protokollet (SSL) för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="9594f-212">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="9594f-213">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="9594f-213">By default, SSL is not used.</span></span>

<span data-ttu-id="9594f-214">WS-Management krypterar allt Windows PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="9594f-214">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="9594f-215">Parametern **UseSSL** är ett ytterligare skydd som skickar data via en HTTPS-anslutning i stället för en HTTP-anslutning.</span><span class="sxs-lookup"><span data-stu-id="9594f-215">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="9594f-216">Om du anger den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="9594f-216">If you specify this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="9594f-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9594f-217">CommonParameters</span></span>

<span data-ttu-id="9594f-218">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9594f-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9594f-219">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9594f-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9594f-220">INDATA</span><span class="sxs-lookup"><span data-stu-id="9594f-220">INPUTS</span></span>

### <span data-ttu-id="9594f-221">System. Management. Automation. körnings utrymmen. PSSession [], system. String</span><span class="sxs-lookup"><span data-stu-id="9594f-221">System.Management.Automation.Runspaces.PSSession[], System.String</span></span>

<span data-ttu-id="9594f-222">Du kan skicka vidare en session eller ett dator namn till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9594f-222">You can pipe a session or a computer name to this cmdlet.</span></span>

## <span data-ttu-id="9594f-223">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9594f-223">OUTPUTS</span></span>

### <span data-ttu-id="9594f-224">System. Management. Automation. körnings utrymmen. PSSession</span><span class="sxs-lookup"><span data-stu-id="9594f-224">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="9594f-225">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9594f-225">NOTES</span></span>

<span data-ttu-id="9594f-226">Ett `New-PSWorkflowSession` kommando motsvarar följande kommando:</span><span class="sxs-lookup"><span data-stu-id="9594f-226">A `New-PSWorkflowSession` command is equivalent to the following command:</span></span>

`New-PSSession -ConfigurationName Microsoft.PowerShell.Workflow`

## <span data-ttu-id="9594f-227">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9594f-227">RELATED LINKS</span></span>

[<span data-ttu-id="9594f-228">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="9594f-228">Disconnect-PSSession</span></span>](../Microsoft.PowerShell.Core/Disconnect-PSSession.md)

[<span data-ttu-id="9594f-229">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="9594f-229">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="9594f-230">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="9594f-230">New-PSTransportOption</span></span>](../Microsoft.PowerShell.Core/New-PSTransportOption.md)

[<span data-ttu-id="9594f-231">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="9594f-231">Register-PSSessionConfiguration</span></span>](../Microsoft.PowerShell.Core/Register-PSSessionConfiguration.md)

[<span data-ttu-id="9594f-232">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="9594f-232">about_PSSessions</span></span>](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[<span data-ttu-id="9594f-233">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="9594f-233">about_Session_Configurations</span></span>](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)

[<span data-ttu-id="9594f-234">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="9594f-234">about_Workflows</span></span>](../PSWorkflow/About/about_Workflows.md)

[<span data-ttu-id="9594f-235">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="9594f-235">about_WorkflowCommonParameters</span></span>](About/about_WorkflowCommonParameters.md)
