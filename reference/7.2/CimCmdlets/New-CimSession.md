---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSession
ms.openlocfilehash: 59e70f75ac9d822db00419d84055d92a3882c11d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708559"
---
# <span data-ttu-id="74104-102">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="74104-102">New-CimSession</span></span>

## <span data-ttu-id="74104-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="74104-103">SYNOPSIS</span></span>

<span data-ttu-id="74104-104">Skapar en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="74104-104">Creates a CIM session.</span></span>

## <span data-ttu-id="74104-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="74104-105">SYNTAX</span></span>

### <span data-ttu-id="74104-106">CredentialParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="74104-106">CredentialParameterSet (Default)</span></span>

```
New-CimSession [-Authentication <PasswordAuthenticationMechanism>] [[-Credential] <PSCredential>]
 [[-ComputerName] <String[]>] [-Name <String>] [-OperationTimeoutSec <UInt32>] [-SkipTestConnection]
 [-Port <UInt32>] [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

### <span data-ttu-id="74104-107">CertificateParameterSet</span><span class="sxs-lookup"><span data-stu-id="74104-107">CertificateParameterSet</span></span>

```
New-CimSession [-CertificateThumbprint <String>] [[-ComputerName] <String[]>] [-Name <String>]
 [-OperationTimeoutSec <UInt32>] [-SkipTestConnection] [-Port <UInt32>]
 [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

## <span data-ttu-id="74104-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="74104-108">DESCRIPTION</span></span>

<span data-ttu-id="74104-109">`New-CimSession`Cmdleten skapar en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="74104-109">The `New-CimSession` cmdlet creates a CIM session.</span></span> <span data-ttu-id="74104-110">En CIM-session är ett objekt på klient sidan som representerar en anslutning till en lokal dator eller en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="74104-110">A CIM session is a client-side object representing a connection to a local computer or a remote computer.</span></span> <span data-ttu-id="74104-111">CIM-sessionen innehåller information om anslutningen, till exempel **computername**, det använda protokollet eller olika identifierare.</span><span class="sxs-lookup"><span data-stu-id="74104-111">The CIM session contains information about the connection, such as **ComputerName**, the protocol used, or various identifiers.</span></span>

<span data-ttu-id="74104-112">Denna cmdlet returnerar ett CIM-sessionsobjekt som kan användas av alla andra CIM-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="74104-112">This cmdlet returns a CIM session object that can be used by all other CIM cmdlets.</span></span>

## <span data-ttu-id="74104-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="74104-113">EXAMPLES</span></span>

### <span data-ttu-id="74104-114">Exempel 1: skapa en CIM-session med standard alternativ</span><span class="sxs-lookup"><span data-stu-id="74104-114">Example 1: Create a CIM session with default options</span></span>

<span data-ttu-id="74104-115">I det här exemplet skapas en lokal CIM-session med standard alternativ.</span><span class="sxs-lookup"><span data-stu-id="74104-115">This example creates a local CIM session with default options.</span></span> <span data-ttu-id="74104-116">Om **computername** inte anges `New-CimSession` skapar en DCOM-session till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="74104-116">If **ComputerName** is not specified, `New-CimSession` creates a DCOM session to the local computer.</span></span>

```powershell
New-CimSession
```

### <span data-ttu-id="74104-117">Exempel 2: skapa en CIM-session till en angiven dator</span><span class="sxs-lookup"><span data-stu-id="74104-117">Example 2: Create a CIM session to a specific computer</span></span>

<span data-ttu-id="74104-118">I det här exemplet skapas en CIM-session till den dator som anges av **computername**.</span><span class="sxs-lookup"><span data-stu-id="74104-118">This example creates a CIM session to the computer specified by **ComputerName**.</span></span>
<span data-ttu-id="74104-119">Som standard `New-CimSession` skapar en WSMan-session när **computername** anges.</span><span class="sxs-lookup"><span data-stu-id="74104-119">By default, `New-CimSession` creates a WSMan session when **ComputerName** is specified.</span></span>

```powershell
New-CimSession -ComputerName Server01
```

### <span data-ttu-id="74104-120">Exempel 3: skapa en CIM-session till flera datorer</span><span class="sxs-lookup"><span data-stu-id="74104-120">Example 3: Create a CIM session to multiple computers</span></span>

<span data-ttu-id="74104-121">I det här exemplet skapas en CIM-session för varje dator som anges av **computername** i den kommaavgränsade listan.</span><span class="sxs-lookup"><span data-stu-id="74104-121">This example creates a CIM session to each of the computers specified by **ComputerName**, in the comma separated list.</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02,Server03
```

### <span data-ttu-id="74104-122">Exempel 4: skapa en CIM-session med ett eget namn</span><span class="sxs-lookup"><span data-stu-id="74104-122">Example 4: Create a CIM session with a friendly name</span></span>

<span data-ttu-id="74104-123">I det här exemplet skapas en fjärrinstans av CIM till varje dator som anges av **computername**, i den kommaavgränsade listan, och tilldelar de nya sessionerna ett eget namn genom att ange **namn**.</span><span class="sxs-lookup"><span data-stu-id="74104-123">This example creates a remote CIM session to each of the computers specified by **ComputerName**, in the comma separated list, and assigns a friendly name to the new sessions, by specifying **Name**.</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02 -Name FileServers
Get-CimSession -Name File*
```

<span data-ttu-id="74104-124">Du kan använda det egna namnet på en CIM-session för att referera till sessionen i andra CIM-cmdletar, till exempel [Get-CimSession](Get-CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="74104-124">You can use the friendly name of a CIM session to refer to the session in other CIM cmdlets, for example, [Get-CimSession](Get-CimSession.md).</span></span>

### <span data-ttu-id="74104-125">Exempel 5: skapa en CIM-session till en dator med hjälp av ett PSCredential-objekt</span><span class="sxs-lookup"><span data-stu-id="74104-125">Example 5: Create a CIM session to a computer using a PSCredential object</span></span>

<span data-ttu-id="74104-126">I det här exemplet skapas en CIM-session till den dator som anges av **computername**, med hjälp av **PSCredential** -objektet som anges av **Credential** och autentiseringstypen som anges av **autentisering**.</span><span class="sxs-lookup"><span data-stu-id="74104-126">This example creates a CIM session to the computer specified by **ComputerName**, using the **PSCredential** object specified by **Credential**, and the authentication type specified by **Authentication**.</span></span>

```powershell
New-CimSession -ComputerName Server01 -Credential $cred -Authentication Negotiate
```

<span data-ttu-id="74104-127">Du kan skapa ett **PSCredential** -objekt med hjälp av [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdleten.</span><span class="sxs-lookup"><span data-stu-id="74104-127">You can create a **PSCredential** object using the [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdlet.</span></span>

### <span data-ttu-id="74104-128">Exempel 6: skapa en CIM-session till en dator med en angiven port</span><span class="sxs-lookup"><span data-stu-id="74104-128">Example 6: Create a CIM session to a computer using a specific port</span></span>

<span data-ttu-id="74104-129">I det här exemplet skapas en CIM-session till den dator som anges av **computername** med TCP-porten som anges av **port**.</span><span class="sxs-lookup"><span data-stu-id="74104-129">This example creates a CIM session to the computer specified by **ComputerName** using the TCP port specified by **Port**.</span></span>

```powershell
New-CimSession -ComputerName Server01 -Port 1234
```

### <span data-ttu-id="74104-130">Exempel 7: skapa en CIM-session med DCOM</span><span class="sxs-lookup"><span data-stu-id="74104-130">Example 7: Create a CIM session using DCOM</span></span>

<span data-ttu-id="74104-131">I det här exemplet skapas en CIM-session med hjälp av DCOM-protokollet (Distributed COM) i stället för WSMan.</span><span class="sxs-lookup"><span data-stu-id="74104-131">This example creates a CIM session using the Distributed COM (DCOM) protocol instead of WSMan.</span></span>

```powershell
$SessionOption = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server1 -SessionOption $SessionOption
```

## <span data-ttu-id="74104-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="74104-132">PARAMETERS</span></span>

### <span data-ttu-id="74104-133">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="74104-133">-Authentication</span></span>

<span data-ttu-id="74104-134">Anger autentiseringstypen som används för användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="74104-134">Specifies the authentication type used for the user's credentials.</span></span> <span data-ttu-id="74104-135">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="74104-135">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="74104-136">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="74104-136">Default</span></span>
- <span data-ttu-id="74104-137">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="74104-137">Digest</span></span>
- <span data-ttu-id="74104-138">Negotiate</span><span class="sxs-lookup"><span data-stu-id="74104-138">Negotiate</span></span>
- <span data-ttu-id="74104-139">Grundläggande</span><span class="sxs-lookup"><span data-stu-id="74104-139">Basic</span></span>
- <span data-ttu-id="74104-140">Kerberos</span><span class="sxs-lookup"><span data-stu-id="74104-140">Kerberos</span></span>
- <span data-ttu-id="74104-141">NtlmDomain</span><span class="sxs-lookup"><span data-stu-id="74104-141">NtlmDomain</span></span>
- <span data-ttu-id="74104-142">CredSsp</span><span class="sxs-lookup"><span data-stu-id="74104-142">CredSsp</span></span>

<span data-ttu-id="74104-143">Du kan inte använda autentiseringstypen **NtlmDomain** för anslutning till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="74104-143">You cannot use the **NtlmDomain** authentication type for connection to the local computer.</span></span> <span data-ttu-id="74104-144">**CredSSP** -autentisering är endast tillgängligt i Windows Vista, windows Server 2008 och senare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="74104-144">**CredSSP** authentication is available only in Windows Vista, Windows Server 2008, and later versions of Windows.</span></span>

> [!CAUTION]
> <span data-ttu-id="74104-145">Autentisering av Credential Security Service Provider (CredSSP) är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="74104-145">Credential Security Service Provider (CredSSP) authentication is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="74104-146">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="74104-146">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="74104-147">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="74104-147">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: CredentialParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74104-148">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="74104-148">-CertificateThumbprint</span></span>

<span data-ttu-id="74104-149">Anger det digitala offentliga nyckel certifikatet (X. 509) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="74104-149">Specifies the digital public key certificate (X.509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="74104-150">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="74104-150">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="74104-151">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="74104-151">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="74104-152">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="74104-152">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="74104-153">Använd [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) cmdletarna eller i PowerShell-certifikat leverantören för att hämta ett tumavtryck för certifikatet.</span><span class="sxs-lookup"><span data-stu-id="74104-153">To get a certificate thumbprint, use the [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) or [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) cmdlets in the PowerShell Certificate Provider.</span></span>

<span data-ttu-id="74104-154">Mer information finns i [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span><span class="sxs-lookup"><span data-stu-id="74104-154">For more information, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

```yaml
Type: System.String
Parameter Sets: CertificateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74104-155">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="74104-155">-ComputerName</span></span>

<span data-ttu-id="74104-156">Anger namnet på den dator som CIM-sessionen ska skapas till.</span><span class="sxs-lookup"><span data-stu-id="74104-156">Specifies the name of the computer to which to create the CIM session.</span></span> <span data-ttu-id="74104-157">Ange antingen ett enda dator namn eller flera dator namn avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="74104-157">Specify either a single computer name, or multiple computer names separated by a comma.</span></span>

<span data-ttu-id="74104-158">Om **computername** inte anges skapas en CIM-session till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="74104-158">If **ComputerName** is not specified, a CIM session to the local computer is created.</span></span> <span data-ttu-id="74104-159">Du kan ange värdet för dator namn i något av följande format:</span><span class="sxs-lookup"><span data-stu-id="74104-159">You can specify the value for computer name in one of the following formats:</span></span>

- <span data-ttu-id="74104-160">Ett eller flera NetBIOS-namn</span><span class="sxs-lookup"><span data-stu-id="74104-160">One or more NetBIOS names</span></span>
- <span data-ttu-id="74104-161">En eller flera IP-adresser</span><span class="sxs-lookup"><span data-stu-id="74104-161">One or more IP addresses</span></span>
- <span data-ttu-id="74104-162">Ett eller flera fullständigt kvalificerade domän namn.</span><span class="sxs-lookup"><span data-stu-id="74104-162">One or more fully qualified domain names.</span></span>

<span data-ttu-id="74104-163">Om datorn finns i en annan domän än användaren, måste du ange det fullständigt kvalificerade domän namnet.</span><span class="sxs-lookup"><span data-stu-id="74104-163">If the computer is in a different domain than the user, you must specify the fully qualified domain name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74104-164">-Credential</span><span class="sxs-lookup"><span data-stu-id="74104-164">-Credential</span></span>

<span data-ttu-id="74104-165">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="74104-165">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="74104-166">Om **autentiseringsuppgifter** inte anges används det aktuella användar kontot.</span><span class="sxs-lookup"><span data-stu-id="74104-166">If **Credential** is not specified, the current user account is used.</span></span>

<span data-ttu-id="74104-167">Ange värdet för **autentiseringsuppgift** med något av följande format:</span><span class="sxs-lookup"><span data-stu-id="74104-167">Specify the value for **Credential** using one of the following formats:</span></span>

- <span data-ttu-id="74104-168">Ett användar namn: "user01"</span><span class="sxs-lookup"><span data-stu-id="74104-168">A user name: "User01"</span></span>
- <span data-ttu-id="74104-169">Ett domän namn och ett användar namn: "Domain01\User01"</span><span class="sxs-lookup"><span data-stu-id="74104-169">A domain name and a user name: "Domain01\User01"</span></span>
- <span data-ttu-id="74104-170">En User Principal Name: " User@Domain.com "</span><span class="sxs-lookup"><span data-stu-id="74104-170">A user principal name: "User@Domain.com"</span></span>
- <span data-ttu-id="74104-171">Ett PSCredential-objekt, till exempel ett som returneras av [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdleten.</span><span class="sxs-lookup"><span data-stu-id="74104-171">A PSCredential object, such as one returned by the [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdlet.</span></span>

<span data-ttu-id="74104-172">När du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="74104-172">When you type a user name, you are prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialParameterSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74104-173">-Name</span><span class="sxs-lookup"><span data-stu-id="74104-173">-Name</span></span>

<span data-ttu-id="74104-174">Anger ett eget namn för CIM-sessionen.</span><span class="sxs-lookup"><span data-stu-id="74104-174">Specifies a friendly name for the CIM session.</span></span>

<span data-ttu-id="74104-175">Du kan använda namnet för att referera till CIM-sessionen när du använder andra cmdlets, till exempel cmdleten [Get-CimSession](Get-CimSession.md) .</span><span class="sxs-lookup"><span data-stu-id="74104-175">You can use the name to refer to the CIM session when using other cmdlets, such as the [Get-CimSession](Get-CimSession.md) cmdlet.</span></span>
<span data-ttu-id="74104-176">Namnet måste inte vara unikt för datorn eller den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="74104-176">The name is not required to be unique to the computer or the current session.</span></span>

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

### <span data-ttu-id="74104-177">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="74104-177">-OperationTimeoutSec</span></span>

<span data-ttu-id="74104-178">Varaktighet för vilken cmdleten väntar på ett svar från servern.</span><span class="sxs-lookup"><span data-stu-id="74104-178">Duration for which the cmdlet waits for a response from the server.</span></span>

<span data-ttu-id="74104-179">Som standard är värdet för den här parametern 0, vilket innebär att cmdleten använder standardvärdet för timeout för servern.</span><span class="sxs-lookup"><span data-stu-id="74104-179">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="74104-180">Om **OperationTimeoutSec** -parametern har angetts till ett värde som är lägre än det stabila anslutnings försöket på 3 minuter, går det inte att återställa nätverks fel som sist mer än värdet för parametern **OperationTimeoutSec** , eftersom åtgärden på servern överskrider innan klienten kan återansluta.</span><span class="sxs-lookup"><span data-stu-id="74104-180">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74104-181">-Port</span><span class="sxs-lookup"><span data-stu-id="74104-181">-Port</span></span>

<span data-ttu-id="74104-182">Anger nätverks porten på den fjärrdator som används för den här anslutningen.</span><span class="sxs-lookup"><span data-stu-id="74104-182">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="74104-183">Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder.</span><span class="sxs-lookup"><span data-stu-id="74104-183">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="74104-184">Standard portarna är 5985 (WinRM-porten för HTTP) och 5986 (WinRM-porten för HTTPS).</span><span class="sxs-lookup"><span data-stu-id="74104-184">The default ports are 5985 (the WinRM port for HTTP) and 5986 (the WinRM port for HTTPS).</span></span>

<span data-ttu-id="74104-185">Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten.</span><span class="sxs-lookup"><span data-stu-id="74104-185">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="74104-186">Använd följande kommandon för att konfigurera lyssnaren:</span><span class="sxs-lookup"><span data-stu-id="74104-186">Use the following commands to configure the listener:</span></span>

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number>"}`

<span data-ttu-id="74104-187">Använd inte **port** parametern om du inte behöver.</span><span class="sxs-lookup"><span data-stu-id="74104-187">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="74104-188">Port inställningen i kommandot gäller för alla datorer eller sessioner där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="74104-188">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="74104-189">En alternativ port inställning kan hindra kommandot från att köras på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="74104-189">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74104-190">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="74104-190">-SessionOption</span></span>

<span data-ttu-id="74104-191">Anger avancerade alternativ för den nya CIM-sessionen.</span><span class="sxs-lookup"><span data-stu-id="74104-191">Sets advanced options for the new CIM session.</span></span> <span data-ttu-id="74104-192">Ange namnet på ett **CimSessionOption** -objekt som skapats med [`New-CimSessionOption`](New-CimSessionOption.md) cmdleten.</span><span class="sxs-lookup"><span data-stu-id="74104-192">Enter the name of a **CimSessionOption** object created using the [`New-CimSessionOption`](New-CimSessionOption.md) cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.CimSessionOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74104-193">-SkipTestConnection</span><span class="sxs-lookup"><span data-stu-id="74104-193">-SkipTestConnection</span></span>

<span data-ttu-id="74104-194">Som standard `New-CimSession` upprättar cmdleten en anslutning med en fjärrWS-Management slut punkt av två skäl: för att kontrol lera att fjärrservern lyssnar på det port nummer som anges med parametern **port** och för att verifiera de angivna autentiseringsuppgifterna för kontot.</span><span class="sxs-lookup"><span data-stu-id="74104-194">By default, the `New-CimSession` cmdlet establishes a connection with a remote WS-Management endpoint for two reasons: to verify that the remote server is listening on the port number that is specified using the **Port** parameter, and to verify the specified account credentials.</span></span> <span data-ttu-id="74104-195">Verifieringen utförs med hjälp av en standard WS-Identitys åtgärd.</span><span class="sxs-lookup"><span data-stu-id="74104-195">The verification is accomplished using a standard WS-Identity operation.</span></span> <span data-ttu-id="74104-196">Du kan lägga till växeln **SkipTestConnection** om fjär WS-Management slut punkten inte kan använda WS-Identify eller om du vill minska data överförings tiden.</span><span class="sxs-lookup"><span data-stu-id="74104-196">You can add the **SkipTestConnection** switch parameter if the remote WS-Management endpoint cannot use WS-Identify, or to reduce some data transmission time.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74104-197">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="74104-197">CommonParameters</span></span>

<span data-ttu-id="74104-198">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="74104-198">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="74104-199">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="74104-199">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="74104-200">INDATA</span><span class="sxs-lookup"><span data-stu-id="74104-200">INPUTS</span></span>

### <span data-ttu-id="74104-201">Inga</span><span class="sxs-lookup"><span data-stu-id="74104-201">None</span></span>

<span data-ttu-id="74104-202">Denna cmdlet accepterar inga indata.</span><span class="sxs-lookup"><span data-stu-id="74104-202">This cmdlet accepts no inputs.</span></span>

## <span data-ttu-id="74104-203">UTDATA</span><span class="sxs-lookup"><span data-stu-id="74104-203">OUTPUTS</span></span>

### <span data-ttu-id="74104-204">Microsoft. Management. Infrastructure. CimSession</span><span class="sxs-lookup"><span data-stu-id="74104-204">Microsoft.Management.Infrastructure.CimSession</span></span>

## <span data-ttu-id="74104-205">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="74104-205">NOTES</span></span>

## <span data-ttu-id="74104-206">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="74104-206">RELATED LINKS</span></span>

[<span data-ttu-id="74104-207">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="74104-207">Get-ChildItem</span></span>](../Microsoft.Powershell.Management/Get-ChildItem.md)

[<span data-ttu-id="74104-208">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="74104-208">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="74104-209">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="74104-209">Get-Item</span></span>](../Microsoft.Powershell.Management/Get-Item.md)

[<span data-ttu-id="74104-210">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="74104-210">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="74104-211">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="74104-211">Remove-CimSession</span></span>](Remove-CimSession.md)

[<span data-ttu-id="74104-212">New-CimSessionOption</span><span class="sxs-lookup"><span data-stu-id="74104-212">New-CimSessionOption</span></span>](New-CimSessionOption.md)

[<span data-ttu-id="74104-213">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="74104-213">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)

