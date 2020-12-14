---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 03/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManInstance
ms.openlocfilehash: dd0343e9b6014e079c322309b699874683bacd6a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708310"
---
# <span data-ttu-id="1a865-102">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="1a865-102">New-WSManInstance</span></span>

## <span data-ttu-id="1a865-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1a865-103">SYNOPSIS</span></span>
<span data-ttu-id="1a865-104">Skapar en ny instans av en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="1a865-104">Creates a new instance of a management resource.</span></span>

## <span data-ttu-id="1a865-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1a865-105">SYNTAX</span></span>

### <span data-ttu-id="1a865-106">ComputerName (standard)</span><span class="sxs-lookup"><span data-stu-id="1a865-106">ComputerName (Default)</span></span>

```
New-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable>
 [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="1a865-107">URI</span><span class="sxs-lookup"><span data-stu-id="1a865-107">URI</span></span>

```
New-WSManInstance [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="1a865-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1a865-108">DESCRIPTION</span></span>

<span data-ttu-id="1a865-109">`New-WSManInstance`Cmdleten skapar en ny instans av en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="1a865-109">The `New-WSManInstance` cmdlet creates a new instance of a management resource.</span></span> <span data-ttu-id="1a865-110">Den använder en resurs-URI och en värde uppsättning eller indatafil för att skapa den nya instansen av hanterings resursen.</span><span class="sxs-lookup"><span data-stu-id="1a865-110">It uses a resource URI and a value set or input file to create the new instance of the management resource.</span></span>

<span data-ttu-id="1a865-111">Denna cmdlet använder WinRM-anslutningen/transport lagret för att skapa hanterings resurs instansen.</span><span class="sxs-lookup"><span data-stu-id="1a865-111">This cmdlet uses the WinRM connection/transport layer to create the management resource instance.</span></span>

## <span data-ttu-id="1a865-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1a865-112">EXAMPLES</span></span>

### <span data-ttu-id="1a865-113">Exempel 1: skapa en HTTPS-lyssnare</span><span class="sxs-lookup"><span data-stu-id="1a865-113">Example 1: Create a HTTPS listener</span></span>

<span data-ttu-id="1a865-114">Det här kommandot skapar en instans av en WS-Management HTTPS-lyssnare på alla IP-adresser.</span><span class="sxs-lookup"><span data-stu-id="1a865-114">This command creates an instance of a WS-Management HTTPS listener on all IP addresses.</span></span>

```powershell
New-WSManInstance winrm/config/Listener -SelectorSet @{Transport='HTTPS'; Address='*'} -ValueSet @{Hostname="HOST";CertificateThumbprint="XXXXXXXXXX"}
```

## <span data-ttu-id="1a865-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1a865-115">PARAMETERS</span></span>

### <span data-ttu-id="1a865-116">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="1a865-116">-ApplicationName</span></span>

<span data-ttu-id="1a865-117">Anger program namnet i anslutningen.</span><span class="sxs-lookup"><span data-stu-id="1a865-117">Specifies the application name in the connection.</span></span> <span data-ttu-id="1a865-118">Standardvärdet för parametern **ApplicationName** är **WSMan**.</span><span class="sxs-lookup"><span data-stu-id="1a865-118">The default value of the **ApplicationName** parameter is **WSMAN**.</span></span> <span data-ttu-id="1a865-119">Den fullständiga identifieraren för Fjärrslutpunkten har följande format:</span><span class="sxs-lookup"><span data-stu-id="1a865-119">The complete identifier for the remote endpoint is in the following format:</span></span>

`<transport>://<server>:<port>/<ApplicationName>`

<span data-ttu-id="1a865-120">Exempel:</span><span class="sxs-lookup"><span data-stu-id="1a865-120">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="1a865-121">Internet Information Services (IIS), som är värd för sessionen, vidarebefordrar begär Anden med den här slut punkten till det angivna programmet.</span><span class="sxs-lookup"><span data-stu-id="1a865-121">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span> <span data-ttu-id="1a865-122">Den här standardinställningen för **WSMan** är lämplig för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="1a865-122">This default setting of **WSMAN** is appropriate for most uses.</span></span> <span data-ttu-id="1a865-123">Den här parametern är avsedd att användas när flera datorer upprättar fjärr anslutningar till en dator som kör Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1a865-123">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span> <span data-ttu-id="1a865-124">I det här fallet är IIS värd för webb tjänster för hantering (WS-Management) för effektivitet.</span><span class="sxs-lookup"><span data-stu-id="1a865-124">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: Wsman
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a865-125">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="1a865-125">-Authentication</span></span>

<span data-ttu-id="1a865-126">Anger vilken autentiseringsmekanism som ska användas på servern.</span><span class="sxs-lookup"><span data-stu-id="1a865-126">Specifies the authentication mechanism to be used at the server.</span></span> <span data-ttu-id="1a865-127">Möjliga värden:</span><span class="sxs-lookup"><span data-stu-id="1a865-127">Possible values are:</span></span>

- <span data-ttu-id="1a865-128">Basic: Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.</span><span class="sxs-lookup"><span data-stu-id="1a865-128">Basic: Basic is a scheme in which the username and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="1a865-129">Standard: Använd autentiseringsmetoden som implementeras av WS-Management-protokollet.</span><span class="sxs-lookup"><span data-stu-id="1a865-129">Default: Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="1a865-130">Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="1a865-130">This is the default.</span></span>
- <span data-ttu-id="1a865-131">Digest: Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.</span><span class="sxs-lookup"><span data-stu-id="1a865-131">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="1a865-132">Kerberos: klient datorn och servern autentiseras ömsesidigt med hjälp av Kerberos-certifikat.</span><span class="sxs-lookup"><span data-stu-id="1a865-132">Kerberos: The client computer and the server mutually authenticate using Kerberos certificates.</span></span>
- <span data-ttu-id="1a865-133">Förhandla: Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="1a865-133">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="1a865-134">Detta parameter värde tillåter till exempel förhandling för att avgöra om Kerberos-protokollet eller NTLM används.</span><span class="sxs-lookup"><span data-stu-id="1a865-134">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="1a865-135">CredSSP: Använd CredSSP-autentisering (Credential Security Support Provider), vilket gör att användaren kan delegera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="1a865-135">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="1a865-136">Det här alternativet är utformat för kommandon som körs på en fjärrdator men samlar in data från eller kör ytterligare kommandon på andra fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="1a865-136">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

> [!CAUTION]
> <span data-ttu-id="1a865-137">CredSSP delegerar användarens autentiseringsuppgifter från den lokala datorn till en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="1a865-137">CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span> <span data-ttu-id="1a865-138">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="1a865-138">This practice increases the security risk of the remote operation.</span></span> <span data-ttu-id="1a865-139">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="1a865-139">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a865-140">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="1a865-140">-CertificateThumbprint</span></span>

<span data-ttu-id="1a865-141">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="1a865-141">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="1a865-142">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="1a865-142">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="1a865-143">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="1a865-143">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="1a865-144">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="1a865-144">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="1a865-145">Om du vill hämta ett tumavtryck för certifikatet använder du `Get-Item` `Get-ChildItem` kommandot eller i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="1a865-145">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="1a865-146">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="1a865-146">-ComputerName</span></span>

<span data-ttu-id="1a865-147">Anger den dator som du vill köra hanterings åtgärden mot.</span><span class="sxs-lookup"><span data-stu-id="1a865-147">Specifies the computer against which you want to run the management operation.</span></span> <span data-ttu-id="1a865-148">Värdet kan vara ett fullständigt kvalificerat domän namn, ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="1a865-148">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="1a865-149">Använd namnet på den lokala datorn, Använd localhost eller Använd en punkt ( `.` ) för att ange den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="1a865-149">Use the local computer name, use localhost, or use a dot (`.`) to specify the local computer.</span></span> <span data-ttu-id="1a865-150">Den lokala datorn är standard.</span><span class="sxs-lookup"><span data-stu-id="1a865-150">The local computer is the default.</span></span> <span data-ttu-id="1a865-151">Om fjärrdatorn finns i en annan domän än användaren måste du använda ett fullständigt kvalificerat domän namn.</span><span class="sxs-lookup"><span data-stu-id="1a865-151">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span> <span data-ttu-id="1a865-152">Du kan skicka ett värde för den här parametern till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="1a865-152">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: Localhost
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a865-153">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="1a865-153">-ConnectionURI</span></span>

<span data-ttu-id="1a865-154">Anger anslutnings slut punkten.</span><span class="sxs-lookup"><span data-stu-id="1a865-154">Specifies the connection endpoint.</span></span>
<span data-ttu-id="1a865-155">Formatet för den här strängen är:</span><span class="sxs-lookup"><span data-stu-id="1a865-155">The format of this string is:</span></span>

`<Transport>://<Server>:<Port>/<ApplicationName>`

<span data-ttu-id="1a865-156">Följande sträng är ett korrekt formaterat värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="1a865-156">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="1a865-157">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="1a865-157">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a865-158">-Credential</span><span class="sxs-lookup"><span data-stu-id="1a865-158">-Credential</span></span>

<span data-ttu-id="1a865-159">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="1a865-159">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="1a865-160">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="1a865-160">The default is the current user.</span></span> <span data-ttu-id="1a865-161">Ange ett användar namn, till exempel "user01", "Domain01\User01" eller " User@Domain.com ".</span><span class="sxs-lookup"><span data-stu-id="1a865-161">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span> <span data-ttu-id="1a865-162">Eller ange ett PSCredential-objekt, till exempel ett som returneras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1a865-162">Or, enter a PSCredential object, such as one returned by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="1a865-163">När du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="1a865-163">When you type a user name, you will be prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1a865-164">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="1a865-164">-FilePath</span></span>

<span data-ttu-id="1a865-165">Anger sökvägen till en fil som används för att skapa en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="1a865-165">Specifies the path of a file that is used to create a management resource.</span></span> <span data-ttu-id="1a865-166">Du anger hanterings resursen med hjälp av parametern **ResourceURI** och parametern **SelectorSet** .</span><span class="sxs-lookup"><span data-stu-id="1a865-166">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter .</span></span> <span data-ttu-id="1a865-167">Till exempel använder följande kommando parametern **File** :</span><span class="sxs-lookup"><span data-stu-id="1a865-167">For example, the following command uses the **File** parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmi/cimv2/Win32_Service -SelectorSet @{Name="spooler"} -File c:\input.xml -Authentication Default`

<span data-ttu-id="1a865-168">Det här kommandot anropar metoden **Stop** service på Spooler-tjänsten med indata från en fil.</span><span class="sxs-lookup"><span data-stu-id="1a865-168">This command calls the **StopService** method on the Spooler service using input from a file.</span></span> <span data-ttu-id="1a865-169">Filen, `Input.xml` innehåller följande innehåll:</span><span class="sxs-lookup"><span data-stu-id="1a865-169">The file, `Input.xml`, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a865-170">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="1a865-170">-OptionSet</span></span>

<span data-ttu-id="1a865-171">Skickar en uppsättning växlar till en tjänst för att ändra eller förfina begärans natur.</span><span class="sxs-lookup"><span data-stu-id="1a865-171">Passes a set of switches to a service to modify or refine the nature of the request.</span></span> <span data-ttu-id="1a865-172">Dessa liknar växlar som används i kommando rads gränssnitt eftersom de är specifika för specifika tjänster.</span><span class="sxs-lookup"><span data-stu-id="1a865-172">These are similar to switches used in command-line shells because they are service specific.</span></span> <span data-ttu-id="1a865-173">Valfritt antal alternativ kan anges.</span><span class="sxs-lookup"><span data-stu-id="1a865-173">Any number of options can be specified.</span></span>

<span data-ttu-id="1a865-174">I följande exempel visas syntaxen som skickar värdena 1, 2 och 3 för parametrarna a, b och c:</span><span class="sxs-lookup"><span data-stu-id="1a865-174">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a865-175">-Port</span><span class="sxs-lookup"><span data-stu-id="1a865-175">-Port</span></span>

<span data-ttu-id="1a865-176">Anger vilken port som ska användas när klienten ansluter till WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1a865-176">Specifies the port to use when the client connects to the WinRM service.</span></span> <span data-ttu-id="1a865-177">När transporten är HTTP är standard porten 80.</span><span class="sxs-lookup"><span data-stu-id="1a865-177">When the transport is HTTP, the default port is 80.</span></span> <span data-ttu-id="1a865-178">När transporten är HTTPS är standard porten 443.</span><span class="sxs-lookup"><span data-stu-id="1a865-178">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="1a865-179">När du använder HTTPS som transport måste värdet för parametern **computername** matcha serverns certifikats eget namn (CN).</span><span class="sxs-lookup"><span data-stu-id="1a865-179">When you use HTTPS as the transport, the value of the **ComputerName** parameter must match the server's certificate common name (CN).</span></span> <span data-ttu-id="1a865-180">Men om parametern **SkipCNCheck** anges som en del av parametern **SessionOption** , behöver inte Certifikatets gemensamma namn matcha serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="1a865-180">However, if the **SkipCNCheck** parameter is specified as part of the **SessionOption** parameter, the certificate common name of the server does not have to match the host name of the server.</span></span> <span data-ttu-id="1a865-181">Parametern **SkipCNCheck** ska endast användas för betrodda datorer.</span><span class="sxs-lookup"><span data-stu-id="1a865-181">The **SkipCNCheck** parameter should be used only for trusted computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a865-182">– ResourceURI</span><span class="sxs-lookup"><span data-stu-id="1a865-182">-ResourceURI</span></span>

<span data-ttu-id="1a865-183">Innehåller Uniform Resource Identifier (URI) för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="1a865-183">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="1a865-184">URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="1a865-184">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="1a865-185">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="1a865-185">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="1a865-186">Exempel:</span><span class="sxs-lookup"><span data-stu-id="1a865-186">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a865-187">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="1a865-187">-SelectorSet</span></span>

<span data-ttu-id="1a865-188">Anger en uppsättning värdepar som används för att välja specifika hanterings resurs instanser.</span><span class="sxs-lookup"><span data-stu-id="1a865-188">Specifies a set of value pairs that are used to select particular management resource instances.</span></span> <span data-ttu-id="1a865-189">Parametern **SelectorSet** används när det finns mer än en instans av resursen.</span><span class="sxs-lookup"><span data-stu-id="1a865-189">The **SelectorSet** parameter is used when more than one instance of the resource exists.</span></span> <span data-ttu-id="1a865-190">Värdet för parametern **SelectorSet** måste vara en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="1a865-190">The value of the **SelectorSet** parameter must be a hash table.</span></span>

<span data-ttu-id="1a865-191">I följande exempel visas hur du anger ett värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="1a865-191">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1a865-192">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="1a865-192">-SessionOption</span></span>

<span data-ttu-id="1a865-193">Definierar en uppsättning utökade alternativ för WS-Management-sessionen.</span><span class="sxs-lookup"><span data-stu-id="1a865-193">Defines a set of extended options for the WS-Management session.</span></span> <span data-ttu-id="1a865-194">Ange ett **SessionOption** -objekt som du skapar med hjälp av `New-WSManSessionOption` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1a865-194">Enter a **SessionOption** object that you create using the `New-WSManSessionOption` cmdlet.</span></span> <span data-ttu-id="1a865-195">Mer information om vilka alternativ som är tillgängliga finns i `New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="1a865-195">For more information about the options that are available, see `New-WSManSessionOption`.</span></span>

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: so

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a865-196">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="1a865-196">-UseSSL</span></span>

<span data-ttu-id="1a865-197">Anger att Secure Sockets Layer (SSL)-protokollet ska användas för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="1a865-197">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span> <span data-ttu-id="1a865-198">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="1a865-198">By default, SSL is not used.</span></span>

<span data-ttu-id="1a865-199">WS-Management krypterar allt Windows PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="1a865-199">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="1a865-200">Med parametern **UseSSL** kan du ange ytterligare skydd av https i stället för http.</span><span class="sxs-lookup"><span data-stu-id="1a865-200">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="1a865-201">Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="1a865-201">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a865-202">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="1a865-202">-ValueSet</span></span>

<span data-ttu-id="1a865-203">Anger en hash-tabell som hjälper dig att ändra en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="1a865-203">Specifies a hash table that helps modify a management resource.</span></span> <span data-ttu-id="1a865-204">Du anger hanterings resursen med hjälp av parametern **ResourceURI** och parametern **SelectorSet** .</span><span class="sxs-lookup"><span data-stu-id="1a865-204">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter.</span></span> <span data-ttu-id="1a865-205">Värdet för parametern **ValueSet** måste vara en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="1a865-205">The value of the **ValueSet** parameter must be a hash table.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a865-206">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1a865-206">CommonParameters</span></span>

<span data-ttu-id="1a865-207">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1a865-207">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1a865-208">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="1a865-208">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1a865-209">INDATA</span><span class="sxs-lookup"><span data-stu-id="1a865-209">INPUTS</span></span>

### <span data-ttu-id="1a865-210">Inga</span><span class="sxs-lookup"><span data-stu-id="1a865-210">None</span></span>

<span data-ttu-id="1a865-211">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="1a865-211">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="1a865-212">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1a865-212">OUTPUTS</span></span>

### <span data-ttu-id="1a865-213">Inga</span><span class="sxs-lookup"><span data-stu-id="1a865-213">None</span></span>

<span data-ttu-id="1a865-214">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="1a865-214">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1a865-215">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1a865-215">NOTES</span></span>

<span data-ttu-id="1a865-216">`Set-WmiInstance`Cmdleten, en Windows Management Instrumentation (WMI)-cmdleten, liknar.</span><span class="sxs-lookup"><span data-stu-id="1a865-216">The `Set-WmiInstance` cmdlet, a Windows Management Instrumentation (WMI) cmdlet, is similar.</span></span>
<span data-ttu-id="1a865-217">`Set-WmiInstance` använder DCOM-anslutningen/transport lagret för att skapa eller uppdatera WMI-instanser.</span><span class="sxs-lookup"><span data-stu-id="1a865-217">`Set-WmiInstance` uses the DCOM connection/transport layer to create or update WMI instances.</span></span>

## <span data-ttu-id="1a865-218">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1a865-218">RELATED LINKS</span></span>

[<span data-ttu-id="1a865-219">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="1a865-219">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="1a865-220">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="1a865-220">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="1a865-221">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="1a865-221">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="1a865-222">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="1a865-222">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="1a865-223">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="1a865-223">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="1a865-224">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="1a865-224">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="1a865-225">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="1a865-225">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="1a865-226">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="1a865-226">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="1a865-227">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="1a865-227">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="1a865-228">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="1a865-228">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="1a865-229">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="1a865-229">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="1a865-230">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="1a865-230">Test-WSMan</span></span>](Test-WSMan.md)

