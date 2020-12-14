---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-WSMan
ms.openlocfilehash: a29a9ef1e35f0c0f802952b99d853c617614a97b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708311"
---
# <span data-ttu-id="9dffc-102">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="9dffc-102">Test-WSMan</span></span>

## <span data-ttu-id="9dffc-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9dffc-103">SYNOPSIS</span></span>
<span data-ttu-id="9dffc-104">Testar om WinRM-tjänsten körs på en lokal dator eller fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="9dffc-104">Tests whether the WinRM service is running on a local or remote computer.</span></span>

## <span data-ttu-id="9dffc-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9dffc-105">SYNTAX</span></span>

```
Test-WSMan [[-ComputerName] <String>] [-Authentication <AuthenticationMechanism>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-Credential <PSCredential>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="9dffc-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9dffc-106">DESCRIPTION</span></span>

<span data-ttu-id="9dffc-107">Cmdleten **test-WSMan** skickar en identifierings förfrågan som avgör om WinRM-tjänsten körs på en lokal dator eller fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="9dffc-107">The **Test-WSMan** cmdlet submits an identification request that determines whether the WinRM service is running on a local or remote computer.</span></span>
<span data-ttu-id="9dffc-108">Om den testade datorn kör tjänsten visar cmdleten WS-Management identitets schema, protokoll version, produkt leverantör och produkt version för den testade tjänsten.</span><span class="sxs-lookup"><span data-stu-id="9dffc-108">If the tested computer is running the service, the cmdlet displays the WS-Management identity schema, the protocol version, the product vendor, and the product version of the tested service.</span></span>

## <span data-ttu-id="9dffc-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9dffc-109">EXAMPLES</span></span>

### <span data-ttu-id="9dffc-110">Exempel 1: Fastställ statusen för WinRM-tjänsten</span><span class="sxs-lookup"><span data-stu-id="9dffc-110">Example 1: Determine the status of the WinRM service</span></span>

```
PS C:\> Test-WSMan
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="9dffc-111">Det här kommandot avgör om WinRM-tjänsten körs på den lokala datorn eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="9dffc-111">This command determines whether the WinRM service is running on the local computer or on a remote computer.</span></span>

### <span data-ttu-id="9dffc-112">Exempel 2: Fastställ statusen för WinRM-tjänsten på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="9dffc-112">Example 2: Determine the status of the WinRM service on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01"
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="9dffc-113">Det här kommandot avgör om WinRM-tjänsten körs på den Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="9dffc-113">This command determines whether the WinRM service is running on the server01 computer.</span></span>

### <span data-ttu-id="9dffc-114">Exempel 3: Fastställ status för WinRM-tjänsten och operativ system versionen</span><span class="sxs-lookup"><span data-stu-id="9dffc-114">Example 3: Determine the status of the WinRM service and the operating system version</span></span>

```
PS C:\> Test-WSMan -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.0.6001 SP: 1.0 Stack: 2.0
```

<span data-ttu-id="9dffc-115">Det här kommandot testar för att se om tjänsten WS-Management (WinRM) körs på den lokala datorn med hjälp av parametern Authentication.</span><span class="sxs-lookup"><span data-stu-id="9dffc-115">This command tests to see whether the WS-Management (WinRM) service is running on the local computer by using the authentication parameter.</span></span>

<span data-ttu-id="9dffc-116">Med parametern Authentication kan **test-WSMan** returnera operativ systemets version.</span><span class="sxs-lookup"><span data-stu-id="9dffc-116">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

### <span data-ttu-id="9dffc-117">Exempel 4: Fastställ status för WinRM-tjänsten och operativ system versionen på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="9dffc-117">Example 4: Determine the status of the WinRM service and the operating system version on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01" -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.1.7021 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="9dffc-118">Det här kommandot testar för att se om tjänsten WS-Management (WinRM) körs på datorn med namnet Server01 med hjälp av parametern Authentication.</span><span class="sxs-lookup"><span data-stu-id="9dffc-118">This command tests to see whether the WS-Management (WinRM) service is running on the computer named server01 using the authentication parameter.</span></span>

<span data-ttu-id="9dffc-119">Med parametern Authentication kan **test-WSMan** returnera operativ systemets version.</span><span class="sxs-lookup"><span data-stu-id="9dffc-119">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

## <span data-ttu-id="9dffc-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9dffc-120">PARAMETERS</span></span>

### <span data-ttu-id="9dffc-121">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="9dffc-121">-ApplicationName</span></span>

<span data-ttu-id="9dffc-122">Anger program namnet i anslutningen.</span><span class="sxs-lookup"><span data-stu-id="9dffc-122">Specifies the application name in the connection.</span></span>
<span data-ttu-id="9dffc-123">Standardvärdet för parametern *ApplicationName* är WSMan.</span><span class="sxs-lookup"><span data-stu-id="9dffc-123">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="9dffc-124">Den fullständiga identifieraren för Fjärrslutpunkten har följande format:</span><span class="sxs-lookup"><span data-stu-id="9dffc-124">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="9dffc-125">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="9dffc-125">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="9dffc-126">Exempel: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="9dffc-126">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="9dffc-127">Internet Information Services (IIS), som är värd för sessionen, vidarebefordrar begär Anden med den här slut punkten till det angivna programmet.</span><span class="sxs-lookup"><span data-stu-id="9dffc-127">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="9dffc-128">Den här standardinställningen för WSMAN är lämplig för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="9dffc-128">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="9dffc-129">Den här parametern är avsedd att användas om många datorer upprättar fjärr anslutningar till en dator som kör PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9dffc-129">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="9dffc-130">I det här fallet är IIS värd för webb tjänster för hantering (WS-Management) för effektivitet.</span><span class="sxs-lookup"><span data-stu-id="9dffc-130">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="9dffc-131">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="9dffc-131">-Authentication</span></span>

<span data-ttu-id="9dffc-132">Anger vilken autentiseringsmekanism som ska användas på servern.</span><span class="sxs-lookup"><span data-stu-id="9dffc-132">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="9dffc-133">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="9dffc-133">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9dffc-134">Frö.</span><span class="sxs-lookup"><span data-stu-id="9dffc-134">Basic.</span></span>
<span data-ttu-id="9dffc-135">Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.</span><span class="sxs-lookup"><span data-stu-id="9dffc-135">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="9dffc-136">Standard.</span><span class="sxs-lookup"><span data-stu-id="9dffc-136">Default.</span></span>
<span data-ttu-id="9dffc-137">Använd autentiseringsmetoden som implementeras av WS-Management-protokollet.</span><span class="sxs-lookup"><span data-stu-id="9dffc-137">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="9dffc-138">Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="9dffc-138">This is the default.</span></span>
- <span data-ttu-id="9dffc-139">Nedbrytning.</span><span class="sxs-lookup"><span data-stu-id="9dffc-139">Digest.</span></span>
<span data-ttu-id="9dffc-140">Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.</span><span class="sxs-lookup"><span data-stu-id="9dffc-140">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="9dffc-141">Paket.</span><span class="sxs-lookup"><span data-stu-id="9dffc-141">Kerberos.</span></span>
<span data-ttu-id="9dffc-142">Klient datorn och servern autentiseras ömsesidigt med hjälp av Kerberos-certifikat.</span><span class="sxs-lookup"><span data-stu-id="9dffc-142">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="9dffc-143">Fram.</span><span class="sxs-lookup"><span data-stu-id="9dffc-143">Negotiate.</span></span>
<span data-ttu-id="9dffc-144">Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="9dffc-144">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="9dffc-145">Detta parameter värde kan till exempel användas för förhandling för att avgöra om Kerberos-protokollet eller NTLM används.</span><span class="sxs-lookup"><span data-stu-id="9dffc-145">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="9dffc-146">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="9dffc-146">CredSSP.</span></span>
<span data-ttu-id="9dffc-147">Använd CredSSP-autentisering (Credential Security Support Provider), vilket gör att användaren kan delegera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="9dffc-147">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="9dffc-148">Det här alternativet är utformat för kommandon som körs på en fjärrdator men samlar in data från eller kör ytterligare kommandon på andra fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="9dffc-148">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="9dffc-149">Varning! CredSSP delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="9dffc-149">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="9dffc-150">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="9dffc-150">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="9dffc-151">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="9dffc-151">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

<span data-ttu-id="9dffc-152">Viktigt: om du inte anger parametern *Authentication* skickas **test-WSMan-** begäran till fjärrdatorn anonymt, utan att autentisering används.</span><span class="sxs-lookup"><span data-stu-id="9dffc-152">Important: If you do not specify the *Authentication* parameter,, the **Test-WSMan** request is sent to the remote computer anonymously, without using authentication.</span></span>
<span data-ttu-id="9dffc-153">Om begäran görs anonymt returneras ingen information som är speciell för operativ systemets version.</span><span class="sxs-lookup"><span data-stu-id="9dffc-153">If the request is made anonymously, it returns no information that is specific to the operating-system version.</span></span>
<span data-ttu-id="9dffc-154">I stället visar denna cmdlet null-värden för operativ systemets version och service pack nivå (OS: 0.0.0 SP: 0,0).</span><span class="sxs-lookup"><span data-stu-id="9dffc-154">Instead, this cmdlet displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

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

### <span data-ttu-id="9dffc-155">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="9dffc-155">-CertificateThumbprint</span></span>

<span data-ttu-id="9dffc-156">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="9dffc-156">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="9dffc-157">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="9dffc-157">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="9dffc-158">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="9dffc-158">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="9dffc-159">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="9dffc-159">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="9dffc-160">Om du vill hämta ett tumavtryck för certifikatet använder du kommandot Get-Item eller Get-ChildItem i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="9dffc-160">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="9dffc-161">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="9dffc-161">-ComputerName</span></span>

<span data-ttu-id="9dffc-162">Anger den dator som hanterings åtgärden ska köras mot.</span><span class="sxs-lookup"><span data-stu-id="9dffc-162">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="9dffc-163">Värdet kan vara ett fullständigt kvalificerat domän namn, ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="9dffc-163">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="9dffc-164">Använd namnet på den lokala datorn, Använd localhost eller Använd en punkt (.) för att ange den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9dffc-164">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="9dffc-165">Den lokala datorn är standard.</span><span class="sxs-lookup"><span data-stu-id="9dffc-165">The local computer is the default.</span></span>
<span data-ttu-id="9dffc-166">Om fjärrdatorn finns i en annan domän än användaren måste du använda ett fullständigt kvalificerat domän namn.</span><span class="sxs-lookup"><span data-stu-id="9dffc-166">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="9dffc-167">Du kan skicka ett värde för den här parametern till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="9dffc-167">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9dffc-168">-Credential</span><span class="sxs-lookup"><span data-stu-id="9dffc-168">-Credential</span></span>

<span data-ttu-id="9dffc-169">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="9dffc-169">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="9dffc-170">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="9dffc-170">The default is the current user.</span></span>
<span data-ttu-id="9dffc-171">Ange ett användar namn, till exempel user01, Domain01\User01 eller User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="9dffc-171">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="9dffc-172">Eller ange ett **PSCredential** -objekt, till exempel ett som returneras av Get-Credential-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9dffc-172">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="9dffc-173">När du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9dffc-173">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="9dffc-174">-Port</span><span class="sxs-lookup"><span data-stu-id="9dffc-174">-Port</span></span>

<span data-ttu-id="9dffc-175">Anger vilken port som ska användas när klienten ansluter till WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="9dffc-175">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="9dffc-176">När transporten är HTTP är standard porten 80.</span><span class="sxs-lookup"><span data-stu-id="9dffc-176">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="9dffc-177">När transporten är HTTPS är standard porten 443.</span><span class="sxs-lookup"><span data-stu-id="9dffc-177">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="9dffc-178">När du använder HTTPS som transport måste värdet för parametern *computername* matcha serverns certifikats eget namn (CN).</span><span class="sxs-lookup"><span data-stu-id="9dffc-178">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>

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

### <span data-ttu-id="9dffc-179">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="9dffc-179">-UseSSL</span></span>

<span data-ttu-id="9dffc-180">Anger att Secure Sockets Layer-protokollet (SSL) används för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="9dffc-180">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="9dffc-181">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="9dffc-181">By default, SSL is not used.</span></span>

<span data-ttu-id="9dffc-182">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="9dffc-182">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="9dffc-183">Med parametern *UseSSL* kan du ange ytterligare skydd av https i stället för http.</span><span class="sxs-lookup"><span data-stu-id="9dffc-183">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="9dffc-184">Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="9dffc-184">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="9dffc-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9dffc-185">CommonParameters</span></span>

<span data-ttu-id="9dffc-186">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9dffc-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9dffc-187">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9dffc-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9dffc-188">INDATA</span><span class="sxs-lookup"><span data-stu-id="9dffc-188">INPUTS</span></span>

### <span data-ttu-id="9dffc-189">Inga</span><span class="sxs-lookup"><span data-stu-id="9dffc-189">None</span></span>

<span data-ttu-id="9dffc-190">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="9dffc-190">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="9dffc-191">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9dffc-191">OUTPUTS</span></span>

### <span data-ttu-id="9dffc-192">Inga</span><span class="sxs-lookup"><span data-stu-id="9dffc-192">None</span></span>

<span data-ttu-id="9dffc-193">Denna cmdlet genererar inga utdata-objekt.</span><span class="sxs-lookup"><span data-stu-id="9dffc-193">This cmdlet does not generate any output object.</span></span>

## <span data-ttu-id="9dffc-194">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9dffc-194">NOTES</span></span>

* <span data-ttu-id="9dffc-195">Som standard frågar **test-WSMan-** cmdleten WinRM-tjänsten utan att använda autentisering, och den returnerar ingen information som är speciell för operativ systemets version.</span><span class="sxs-lookup"><span data-stu-id="9dffc-195">By default, the **Test-WSMan** cmdlet queries the WinRM service without using authentication, and it returns no information that is specific to the operating-system version.</span></span> <span data-ttu-id="9dffc-196">I stället visas null-värden för operativ system versionen och service pack nivån (OS: 0.0.0 SP: 0,0).</span><span class="sxs-lookup"><span data-stu-id="9dffc-196">Instead, it displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

*

## <span data-ttu-id="9dffc-197">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9dffc-197">RELATED LINKS</span></span>

[<span data-ttu-id="9dffc-198">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="9dffc-198">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="9dffc-199">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="9dffc-199">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="9dffc-200">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="9dffc-200">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="9dffc-201">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="9dffc-201">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="9dffc-202">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="9dffc-202">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="9dffc-203">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="9dffc-203">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="9dffc-204">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="9dffc-204">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="9dffc-205">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="9dffc-205">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="9dffc-206">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="9dffc-206">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="9dffc-207">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="9dffc-207">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="9dffc-208">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="9dffc-208">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="9dffc-209">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="9dffc-209">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

