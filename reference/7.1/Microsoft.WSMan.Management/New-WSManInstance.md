---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 03/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmaninstance?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManInstance
ms.openlocfilehash: 696bce9c1a578b054e5f9a7877f2195273ab8e8b
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268575"
---
# <span data-ttu-id="69298-103">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="69298-103">New-WSManInstance</span></span>

## <span data-ttu-id="69298-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="69298-104">SYNOPSIS</span></span>
<span data-ttu-id="69298-105">Skapar en ny instans av en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="69298-105">Creates a new instance of a management resource.</span></span>

## <span data-ttu-id="69298-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="69298-106">SYNTAX</span></span>

### <span data-ttu-id="69298-107">ComputerName (standard)</span><span class="sxs-lookup"><span data-stu-id="69298-107">ComputerName (Default)</span></span>

```
New-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable>
 [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="69298-108">URI</span><span class="sxs-lookup"><span data-stu-id="69298-108">URI</span></span>

```
New-WSManInstance [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="69298-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="69298-109">DESCRIPTION</span></span>

<span data-ttu-id="69298-110">`New-WSManInstance`Cmdleten skapar en ny instans av en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="69298-110">The `New-WSManInstance` cmdlet creates a new instance of a management resource.</span></span> <span data-ttu-id="69298-111">Den använder en resurs-URI och en värde uppsättning eller indatafil för att skapa den nya instansen av hanterings resursen.</span><span class="sxs-lookup"><span data-stu-id="69298-111">It uses a resource URI and a value set or input file to create the new instance of the management resource.</span></span>

<span data-ttu-id="69298-112">Denna cmdlet använder WinRM-anslutningen/transport lagret för att skapa hanterings resurs instansen.</span><span class="sxs-lookup"><span data-stu-id="69298-112">This cmdlet uses the WinRM connection/transport layer to create the management resource instance.</span></span>

## <span data-ttu-id="69298-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="69298-113">EXAMPLES</span></span>

### <span data-ttu-id="69298-114">Exempel 1: skapa en HTTPS-lyssnare</span><span class="sxs-lookup"><span data-stu-id="69298-114">Example 1: Create a HTTPS listener</span></span>

<span data-ttu-id="69298-115">Det här kommandot skapar en instans av en WS-Management HTTPS-lyssnare på alla IP-adresser.</span><span class="sxs-lookup"><span data-stu-id="69298-115">This command creates an instance of a WS-Management HTTPS listener on all IP addresses.</span></span>

```powershell
New-WSManInstance winrm/config/Listener -SelectorSet @{Transport='HTTPS'; Address='*'} -ValueSet @{Hostname="HOST";CertificateThumbprint="XXXXXXXXXX"}
```

## <span data-ttu-id="69298-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="69298-116">PARAMETERS</span></span>

### <span data-ttu-id="69298-117">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="69298-117">-ApplicationName</span></span>

<span data-ttu-id="69298-118">Anger program namnet i anslutningen.</span><span class="sxs-lookup"><span data-stu-id="69298-118">Specifies the application name in the connection.</span></span> <span data-ttu-id="69298-119">Standardvärdet för parametern **ApplicationName** är **WSMan**.</span><span class="sxs-lookup"><span data-stu-id="69298-119">The default value of the **ApplicationName** parameter is **WSMAN**.</span></span> <span data-ttu-id="69298-120">Den fullständiga identifieraren för Fjärrslutpunkten har följande format:</span><span class="sxs-lookup"><span data-stu-id="69298-120">The complete identifier for the remote endpoint is in the following format:</span></span>

`<transport>://<server>:<port>/<ApplicationName>`

<span data-ttu-id="69298-121">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="69298-121">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="69298-122">Internet Information Services (IIS), som är värd för sessionen, vidarebefordrar begär Anden med den här slut punkten till det angivna programmet.</span><span class="sxs-lookup"><span data-stu-id="69298-122">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span> <span data-ttu-id="69298-123">Den här standardinställningen för **WSMan** är lämplig för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="69298-123">This default setting of **WSMAN** is appropriate for most uses.</span></span> <span data-ttu-id="69298-124">Den här parametern är avsedd att användas när flera datorer upprättar fjärr anslutningar till en dator som kör Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69298-124">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span> <span data-ttu-id="69298-125">I det här fallet är IIS värd för webb tjänster för hantering (WS-Management) för effektivitet.</span><span class="sxs-lookup"><span data-stu-id="69298-125">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="69298-126">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="69298-126">-Authentication</span></span>

<span data-ttu-id="69298-127">Anger vilken autentiseringsmekanism som ska användas på servern.</span><span class="sxs-lookup"><span data-stu-id="69298-127">Specifies the authentication mechanism to be used at the server.</span></span> <span data-ttu-id="69298-128">Möjliga värden:</span><span class="sxs-lookup"><span data-stu-id="69298-128">Possible values are:</span></span>

- <span data-ttu-id="69298-129">Basic: Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.</span><span class="sxs-lookup"><span data-stu-id="69298-129">Basic: Basic is a scheme in which the username and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="69298-130">Standard: Använd autentiseringsmetoden som implementeras av WS-Management-protokollet.</span><span class="sxs-lookup"><span data-stu-id="69298-130">Default: Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="69298-131">Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="69298-131">This is the default.</span></span>
- <span data-ttu-id="69298-132">Digest: Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.</span><span class="sxs-lookup"><span data-stu-id="69298-132">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="69298-133">Kerberos: klient datorn och servern autentiseras ömsesidigt med hjälp av Kerberos-certifikat.</span><span class="sxs-lookup"><span data-stu-id="69298-133">Kerberos: The client computer and the server mutually authenticate using Kerberos certificates.</span></span>
- <span data-ttu-id="69298-134">Förhandla: Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="69298-134">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="69298-135">Detta parameter värde tillåter till exempel förhandling för att avgöra om Kerberos-protokollet eller NTLM används.</span><span class="sxs-lookup"><span data-stu-id="69298-135">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="69298-136">CredSSP: Använd CredSSP-autentisering (Credential Security Support Provider), vilket gör att användaren kan delegera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="69298-136">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="69298-137">Det här alternativet är utformat för kommandon som körs på en fjärrdator men samlar in data från eller kör ytterligare kommandon på andra fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="69298-137">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

> [!CAUTION]
> <span data-ttu-id="69298-138">CredSSP delegerar användarens autentiseringsuppgifter från den lokala datorn till en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="69298-138">CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span> <span data-ttu-id="69298-139">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="69298-139">This practice increases the security risk of the remote operation.</span></span> <span data-ttu-id="69298-140">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="69298-140">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="69298-141">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="69298-141">-CertificateThumbprint</span></span>

<span data-ttu-id="69298-142">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="69298-142">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="69298-143">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="69298-143">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="69298-144">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="69298-144">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="69298-145">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="69298-145">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="69298-146">Om du vill hämta ett tumavtryck för certifikatet använder du `Get-Item` `Get-ChildItem` kommandot eller i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="69298-146">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="69298-147">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="69298-147">-ComputerName</span></span>

<span data-ttu-id="69298-148">Anger den dator som du vill köra hanterings åtgärden mot.</span><span class="sxs-lookup"><span data-stu-id="69298-148">Specifies the computer against which you want to run the management operation.</span></span> <span data-ttu-id="69298-149">Värdet kan vara ett fullständigt kvalificerat domän namn, ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="69298-149">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="69298-150">Använd namnet på den lokala datorn, Använd localhost eller Använd en punkt ( `.` ) för att ange den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="69298-150">Use the local computer name, use localhost, or use a dot (`.`) to specify the local computer.</span></span> <span data-ttu-id="69298-151">Den lokala datorn är standard.</span><span class="sxs-lookup"><span data-stu-id="69298-151">The local computer is the default.</span></span> <span data-ttu-id="69298-152">Om fjärrdatorn finns i en annan domän än användaren måste du använda ett fullständigt kvalificerat domän namn.</span><span class="sxs-lookup"><span data-stu-id="69298-152">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span> <span data-ttu-id="69298-153">Du kan skicka ett värde för den här parametern till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="69298-153">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="69298-154">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="69298-154">-ConnectionURI</span></span>

<span data-ttu-id="69298-155">Anger anslutnings slut punkten.</span><span class="sxs-lookup"><span data-stu-id="69298-155">Specifies the connection endpoint.</span></span>
<span data-ttu-id="69298-156">Formatet för den här strängen är:</span><span class="sxs-lookup"><span data-stu-id="69298-156">The format of this string is:</span></span>

`<Transport>://<Server>:<Port>/<ApplicationName>`

<span data-ttu-id="69298-157">Följande sträng är ett korrekt formaterat värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="69298-157">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="69298-158">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="69298-158">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="69298-159">-Credential</span><span class="sxs-lookup"><span data-stu-id="69298-159">-Credential</span></span>

<span data-ttu-id="69298-160">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="69298-160">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="69298-161">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="69298-161">The default is the current user.</span></span> <span data-ttu-id="69298-162">Ange ett användar namn, till exempel "user01", "Domain01\User01" eller " User@Domain.com ".</span><span class="sxs-lookup"><span data-stu-id="69298-162">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span> <span data-ttu-id="69298-163">Eller ange ett PSCredential-objekt, till exempel ett som returneras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="69298-163">Or, enter a PSCredential object, such as one returned by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="69298-164">När du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="69298-164">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="69298-165">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="69298-165">-FilePath</span></span>

<span data-ttu-id="69298-166">Anger sökvägen till en fil som används för att skapa en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="69298-166">Specifies the path of a file that is used to create a management resource.</span></span> <span data-ttu-id="69298-167">Du anger hanterings resursen med hjälp av parametern **ResourceURI** och parametern **SelectorSet** .</span><span class="sxs-lookup"><span data-stu-id="69298-167">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter .</span></span> <span data-ttu-id="69298-168">Till exempel använder följande kommando parametern **File** :</span><span class="sxs-lookup"><span data-stu-id="69298-168">For example, the following command uses the **File** parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmi/cimv2/Win32_Service -SelectorSet @{Name="spooler"} -File c:\input.xml -Authentication Default`

<span data-ttu-id="69298-169">Det här kommandot anropar metoden **Stop** service på Spooler-tjänsten med indata från en fil.</span><span class="sxs-lookup"><span data-stu-id="69298-169">This command calls the **StopService** method on the Spooler service using input from a file.</span></span> <span data-ttu-id="69298-170">Filen, `Input.xml` innehåller följande innehåll:</span><span class="sxs-lookup"><span data-stu-id="69298-170">The file, `Input.xml`, contains the following content:</span></span>

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

### <span data-ttu-id="69298-171">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="69298-171">-OptionSet</span></span>

<span data-ttu-id="69298-172">Skickar en uppsättning växlar till en tjänst för att ändra eller förfina begärans natur.</span><span class="sxs-lookup"><span data-stu-id="69298-172">Passes a set of switches to a service to modify or refine the nature of the request.</span></span> <span data-ttu-id="69298-173">Dessa liknar växlar som används i kommando rads gränssnitt eftersom de är specifika för specifika tjänster.</span><span class="sxs-lookup"><span data-stu-id="69298-173">These are similar to switches used in command-line shells because they are service specific.</span></span> <span data-ttu-id="69298-174">Valfritt antal alternativ kan anges.</span><span class="sxs-lookup"><span data-stu-id="69298-174">Any number of options can be specified.</span></span>

<span data-ttu-id="69298-175">I följande exempel visas syntaxen som skickar värdena 1, 2 och 3 för parametrarna a, b och c:</span><span class="sxs-lookup"><span data-stu-id="69298-175">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="69298-176">-Port</span><span class="sxs-lookup"><span data-stu-id="69298-176">-Port</span></span>

<span data-ttu-id="69298-177">Anger vilken port som ska användas när klienten ansluter till WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="69298-177">Specifies the port to use when the client connects to the WinRM service.</span></span> <span data-ttu-id="69298-178">När transporten är HTTP är standard porten 80.</span><span class="sxs-lookup"><span data-stu-id="69298-178">When the transport is HTTP, the default port is 80.</span></span> <span data-ttu-id="69298-179">När transporten är HTTPS är standard porten 443.</span><span class="sxs-lookup"><span data-stu-id="69298-179">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="69298-180">När du använder HTTPS som transport måste värdet för parametern **computername** matcha serverns certifikats eget namn (CN).</span><span class="sxs-lookup"><span data-stu-id="69298-180">When you use HTTPS as the transport, the value of the **ComputerName** parameter must match the server's certificate common name (CN).</span></span> <span data-ttu-id="69298-181">Men om parametern **SkipCNCheck** anges som en del av parametern **SessionOption** , behöver inte Certifikatets gemensamma namn matcha serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="69298-181">However, if the **SkipCNCheck** parameter is specified as part of the **SessionOption** parameter, the certificate common name of the server does not have to match the host name of the server.</span></span> <span data-ttu-id="69298-182">Parametern **SkipCNCheck** ska endast användas för betrodda datorer.</span><span class="sxs-lookup"><span data-stu-id="69298-182">The **SkipCNCheck** parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="69298-183">– ResourceURI</span><span class="sxs-lookup"><span data-stu-id="69298-183">-ResourceURI</span></span>

<span data-ttu-id="69298-184">Innehåller Uniform Resource Identifier (URI) för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="69298-184">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="69298-185">URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="69298-185">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="69298-186">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="69298-186">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="69298-187">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="69298-187">For example:</span></span>

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

### <span data-ttu-id="69298-188">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="69298-188">-SelectorSet</span></span>

<span data-ttu-id="69298-189">Anger en uppsättning värdepar som används för att välja specifika hanterings resurs instanser.</span><span class="sxs-lookup"><span data-stu-id="69298-189">Specifies a set of value pairs that are used to select particular management resource instances.</span></span> <span data-ttu-id="69298-190">Parametern **SelectorSet** används när det finns mer än en instans av resursen.</span><span class="sxs-lookup"><span data-stu-id="69298-190">The **SelectorSet** parameter is used when more than one instance of the resource exists.</span></span> <span data-ttu-id="69298-191">Värdet för parametern **SelectorSet** måste vara en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="69298-191">The value of the **SelectorSet** parameter must be a hash table.</span></span>

<span data-ttu-id="69298-192">I följande exempel visas hur du anger ett värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="69298-192">The following example shows how to enter a value for this parameter:</span></span>

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

### <span data-ttu-id="69298-193">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="69298-193">-SessionOption</span></span>

<span data-ttu-id="69298-194">Definierar en uppsättning utökade alternativ för WS-Management-sessionen.</span><span class="sxs-lookup"><span data-stu-id="69298-194">Defines a set of extended options for the WS-Management session.</span></span> <span data-ttu-id="69298-195">Ange ett **SessionOption** -objekt som du skapar med hjälp av `New-WSManSessionOption` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="69298-195">Enter a **SessionOption** object that you create using the `New-WSManSessionOption` cmdlet.</span></span> <span data-ttu-id="69298-196">Mer information om vilka alternativ som är tillgängliga finns i `New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="69298-196">For more information about the options that are available, see `New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="69298-197">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="69298-197">-UseSSL</span></span>

<span data-ttu-id="69298-198">Anger att Secure Sockets Layer (SSL)-protokollet ska användas för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="69298-198">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span> <span data-ttu-id="69298-199">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="69298-199">By default, SSL is not used.</span></span>

<span data-ttu-id="69298-200">WS-Management krypterar allt Windows PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="69298-200">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="69298-201">Med parametern **UseSSL** kan du ange ytterligare skydd av https i stället för http.</span><span class="sxs-lookup"><span data-stu-id="69298-201">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="69298-202">Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="69298-202">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="69298-203">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="69298-203">-ValueSet</span></span>

<span data-ttu-id="69298-204">Anger en hash-tabell som hjälper dig att ändra en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="69298-204">Specifies a hash table that helps modify a management resource.</span></span> <span data-ttu-id="69298-205">Du anger hanterings resursen med hjälp av parametern **ResourceURI** och parametern **SelectorSet** .</span><span class="sxs-lookup"><span data-stu-id="69298-205">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter.</span></span> <span data-ttu-id="69298-206">Värdet för parametern **ValueSet** måste vara en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="69298-206">The value of the **ValueSet** parameter must be a hash table.</span></span>

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

### <span data-ttu-id="69298-207">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="69298-207">CommonParameters</span></span>

<span data-ttu-id="69298-208">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="69298-208">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="69298-209">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="69298-209">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="69298-210">INDATA</span><span class="sxs-lookup"><span data-stu-id="69298-210">INPUTS</span></span>

### <span data-ttu-id="69298-211">Inget</span><span class="sxs-lookup"><span data-stu-id="69298-211">None</span></span>

<span data-ttu-id="69298-212">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="69298-212">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="69298-213">UTDATA</span><span class="sxs-lookup"><span data-stu-id="69298-213">OUTPUTS</span></span>

### <span data-ttu-id="69298-214">Inget</span><span class="sxs-lookup"><span data-stu-id="69298-214">None</span></span>

<span data-ttu-id="69298-215">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="69298-215">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="69298-216">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="69298-216">NOTES</span></span>

<span data-ttu-id="69298-217">`Set-WmiInstance`Cmdleten, en Windows Management Instrumentation (WMI)-cmdleten, liknar.</span><span class="sxs-lookup"><span data-stu-id="69298-217">The `Set-WmiInstance` cmdlet, a Windows Management Instrumentation (WMI) cmdlet, is similar.</span></span>
<span data-ttu-id="69298-218">`Set-WmiInstance` använder DCOM-anslutningen/transport lagret för att skapa eller uppdatera WMI-instanser.</span><span class="sxs-lookup"><span data-stu-id="69298-218">`Set-WmiInstance` uses the DCOM connection/transport layer to create or update WMI instances.</span></span>

## <span data-ttu-id="69298-219">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="69298-219">RELATED LINKS</span></span>

[<span data-ttu-id="69298-220">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="69298-220">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="69298-221">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="69298-221">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="69298-222">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="69298-222">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="69298-223">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="69298-223">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="69298-224">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="69298-224">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="69298-225">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="69298-225">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="69298-226">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="69298-226">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="69298-227">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="69298-227">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="69298-228">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="69298-228">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="69298-229">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="69298-229">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="69298-230">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="69298-230">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="69298-231">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="69298-231">Test-WSMan</span></span>](Test-WSMan.md)

