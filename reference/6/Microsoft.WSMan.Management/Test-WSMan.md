---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-WSMan
ms.openlocfilehash: 0cf40af09354314a28af216642d09a5c1fa7479d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263979"
---
# <span data-ttu-id="262ab-103">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="262ab-103">Test-WSMan</span></span>

## <span data-ttu-id="262ab-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="262ab-104">SYNOPSIS</span></span>
<span data-ttu-id="262ab-105">Testar om WinRM-tjänsten körs på en lokal dator eller fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="262ab-105">Tests whether the WinRM service is running on a local or remote computer.</span></span>

## <span data-ttu-id="262ab-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="262ab-106">SYNTAX</span></span>

```
Test-WSMan [[-ComputerName] <String>] [-Authentication <AuthenticationMechanism>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-Credential <PSCredential>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="262ab-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="262ab-107">DESCRIPTION</span></span>

<span data-ttu-id="262ab-108">Cmdleten **test-WSMan** skickar en identifierings förfrågan som avgör om WinRM-tjänsten körs på en lokal dator eller fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="262ab-108">The **Test-WSMan** cmdlet submits an identification request that determines whether the WinRM service is running on a local or remote computer.</span></span>
<span data-ttu-id="262ab-109">Om den testade datorn kör tjänsten visar cmdleten WS-Management identitets schema, protokoll version, produkt leverantör och produkt version för den testade tjänsten.</span><span class="sxs-lookup"><span data-stu-id="262ab-109">If the tested computer is running the service, the cmdlet displays the WS-Management identity schema, the protocol version, the product vendor, and the product version of the tested service.</span></span>

## <span data-ttu-id="262ab-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="262ab-110">EXAMPLES</span></span>

### <span data-ttu-id="262ab-111">Exempel 1: Fastställ statusen för WinRM-tjänsten</span><span class="sxs-lookup"><span data-stu-id="262ab-111">Example 1: Determine the status of the WinRM service</span></span>

```
PS C:\> Test-WSMan
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="262ab-112">Det här kommandot avgör om WinRM-tjänsten körs på den lokala datorn eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="262ab-112">This command determines whether the WinRM service is running on the local computer or on a remote computer.</span></span>

### <span data-ttu-id="262ab-113">Exempel 2: Fastställ statusen för WinRM-tjänsten på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="262ab-113">Example 2: Determine the status of the WinRM service on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01"
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="262ab-114">Det här kommandot avgör om WinRM-tjänsten körs på den Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="262ab-114">This command determines whether the WinRM service is running on the server01 computer.</span></span>

### <span data-ttu-id="262ab-115">Exempel 3: Fastställ status för WinRM-tjänsten och operativ system versionen</span><span class="sxs-lookup"><span data-stu-id="262ab-115">Example 3: Determine the status of the WinRM service and the operating system version</span></span>

```
PS C:\> Test-WSMan -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.0.6001 SP: 1.0 Stack: 2.0
```

<span data-ttu-id="262ab-116">Det här kommandot testar för att se om tjänsten WS-Management (WinRM) körs på den lokala datorn med hjälp av parametern Authentication.</span><span class="sxs-lookup"><span data-stu-id="262ab-116">This command tests to see whether the WS-Management (WinRM) service is running on the local computer by using the authentication parameter.</span></span>

<span data-ttu-id="262ab-117">Med parametern Authentication kan **test-WSMan** returnera operativ systemets version.</span><span class="sxs-lookup"><span data-stu-id="262ab-117">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

### <span data-ttu-id="262ab-118">Exempel 4: Fastställ status för WinRM-tjänsten och operativ system versionen på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="262ab-118">Example 4: Determine the status of the WinRM service and the operating system version on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01" -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.1.7021 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="262ab-119">Det här kommandot testar för att se om tjänsten WS-Management (WinRM) körs på datorn med namnet Server01 med hjälp av parametern Authentication.</span><span class="sxs-lookup"><span data-stu-id="262ab-119">This command tests to see whether the WS-Management (WinRM) service is running on the computer named server01 using the authentication parameter.</span></span>

<span data-ttu-id="262ab-120">Med parametern Authentication kan **test-WSMan** returnera operativ systemets version.</span><span class="sxs-lookup"><span data-stu-id="262ab-120">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

## <span data-ttu-id="262ab-121">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="262ab-121">PARAMETERS</span></span>

### <span data-ttu-id="262ab-122">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="262ab-122">-ApplicationName</span></span>

<span data-ttu-id="262ab-123">Anger program namnet i anslutningen.</span><span class="sxs-lookup"><span data-stu-id="262ab-123">Specifies the application name in the connection.</span></span>
<span data-ttu-id="262ab-124">Standardvärdet för parametern *ApplicationName* är WSMan.</span><span class="sxs-lookup"><span data-stu-id="262ab-124">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="262ab-125">Den fullständiga identifieraren för Fjärrslutpunkten har följande format:</span><span class="sxs-lookup"><span data-stu-id="262ab-125">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="262ab-126">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="262ab-126">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="262ab-127">Exempelvis: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="262ab-127">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="262ab-128">Internet Information Services (IIS), som är värd för sessionen, vidarebefordrar begär Anden med den här slut punkten till det angivna programmet.</span><span class="sxs-lookup"><span data-stu-id="262ab-128">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="262ab-129">Den här standardinställningen för WSMAN är lämplig för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="262ab-129">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="262ab-130">Den här parametern är avsedd att användas om många datorer upprättar fjärr anslutningar till en dator som kör PowerShell.</span><span class="sxs-lookup"><span data-stu-id="262ab-130">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="262ab-131">I det här fallet är IIS värd för webb tjänster för hantering (WS-Management) för effektivitet.</span><span class="sxs-lookup"><span data-stu-id="262ab-131">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="262ab-132">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="262ab-132">-Authentication</span></span>

<span data-ttu-id="262ab-133">Anger vilken autentiseringsmekanism som ska användas på servern.</span><span class="sxs-lookup"><span data-stu-id="262ab-133">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="262ab-134">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="262ab-134">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="262ab-135">Frö.</span><span class="sxs-lookup"><span data-stu-id="262ab-135">Basic.</span></span>
<span data-ttu-id="262ab-136">Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.</span><span class="sxs-lookup"><span data-stu-id="262ab-136">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="262ab-137">Standard.</span><span class="sxs-lookup"><span data-stu-id="262ab-137">Default.</span></span>
<span data-ttu-id="262ab-138">Använd autentiseringsmetoden som implementeras av WS-Management-protokollet.</span><span class="sxs-lookup"><span data-stu-id="262ab-138">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="262ab-139">Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="262ab-139">This is the default.</span></span>
- <span data-ttu-id="262ab-140">Nedbrytning.</span><span class="sxs-lookup"><span data-stu-id="262ab-140">Digest.</span></span>
<span data-ttu-id="262ab-141">Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.</span><span class="sxs-lookup"><span data-stu-id="262ab-141">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="262ab-142">Paket.</span><span class="sxs-lookup"><span data-stu-id="262ab-142">Kerberos.</span></span>
<span data-ttu-id="262ab-143">Klient datorn och servern autentiseras ömsesidigt med hjälp av Kerberos-certifikat.</span><span class="sxs-lookup"><span data-stu-id="262ab-143">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="262ab-144">Fram.</span><span class="sxs-lookup"><span data-stu-id="262ab-144">Negotiate.</span></span>
<span data-ttu-id="262ab-145">Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="262ab-145">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="262ab-146">Detta parameter värde kan till exempel användas för förhandling för att avgöra om Kerberos-protokollet eller NTLM används.</span><span class="sxs-lookup"><span data-stu-id="262ab-146">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="262ab-147">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="262ab-147">CredSSP.</span></span>
<span data-ttu-id="262ab-148">Använd CredSSP-autentisering (Credential Security Support Provider), vilket gör att användaren kan delegera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="262ab-148">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="262ab-149">Det här alternativet är utformat för kommandon som körs på en fjärrdator men samlar in data från eller kör ytterligare kommandon på andra fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="262ab-149">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="262ab-150">Varning! CredSSP delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="262ab-150">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="262ab-151">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="262ab-151">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="262ab-152">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="262ab-152">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

<span data-ttu-id="262ab-153">Viktigt: om du inte anger parametern *Authentication* skickas **test-WSMan-** begäran till fjärrdatorn anonymt, utan att autentisering används.</span><span class="sxs-lookup"><span data-stu-id="262ab-153">Important: If you do not specify the *Authentication* parameter,, the **Test-WSMan** request is sent to the remote computer anonymously, without using authentication.</span></span>
<span data-ttu-id="262ab-154">Om begäran görs anonymt returneras ingen information som är speciell för operativ systemets version.</span><span class="sxs-lookup"><span data-stu-id="262ab-154">If the request is made anonymously, it returns no information that is specific to the operating-system version.</span></span>
<span data-ttu-id="262ab-155">I stället visar denna cmdlet null-värden för operativ systemets version och service pack nivå (OS: 0.0.0 SP: 0,0).</span><span class="sxs-lookup"><span data-stu-id="262ab-155">Instead, this cmdlet displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

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

### <span data-ttu-id="262ab-156">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="262ab-156">-CertificateThumbprint</span></span>

<span data-ttu-id="262ab-157">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="262ab-157">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="262ab-158">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="262ab-158">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="262ab-159">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="262ab-159">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="262ab-160">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="262ab-160">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="262ab-161">Om du vill hämta ett tumavtryck för certifikatet använder du kommandot Get-Item eller Get-ChildItem i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="262ab-161">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="262ab-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="262ab-162">-ComputerName</span></span>

<span data-ttu-id="262ab-163">Anger den dator som hanterings åtgärden ska köras mot.</span><span class="sxs-lookup"><span data-stu-id="262ab-163">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="262ab-164">Värdet kan vara ett fullständigt kvalificerat domän namn, ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="262ab-164">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="262ab-165">Använd namnet på den lokala datorn, Använd localhost eller Använd en punkt (.) för att ange den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="262ab-165">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="262ab-166">Den lokala datorn är standard.</span><span class="sxs-lookup"><span data-stu-id="262ab-166">The local computer is the default.</span></span>
<span data-ttu-id="262ab-167">Om fjärrdatorn finns i en annan domän än användaren måste du använda ett fullständigt kvalificerat domän namn.</span><span class="sxs-lookup"><span data-stu-id="262ab-167">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="262ab-168">Du kan skicka ett värde för den här parametern till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="262ab-168">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="262ab-169">-Credential</span><span class="sxs-lookup"><span data-stu-id="262ab-169">-Credential</span></span>

<span data-ttu-id="262ab-170">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="262ab-170">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="262ab-171">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="262ab-171">The default is the current user.</span></span>
<span data-ttu-id="262ab-172">Ange ett användar namn, till exempel user01, Domain01\User01 eller User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="262ab-172">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="262ab-173">Eller ange ett **PSCredential** -objekt, till exempel ett som returneras av Get-Credential-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="262ab-173">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="262ab-174">När du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="262ab-174">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="262ab-175">-Port</span><span class="sxs-lookup"><span data-stu-id="262ab-175">-Port</span></span>

<span data-ttu-id="262ab-176">Anger vilken port som ska användas när klienten ansluter till WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="262ab-176">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="262ab-177">När transporten är HTTP är standard porten 80.</span><span class="sxs-lookup"><span data-stu-id="262ab-177">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="262ab-178">När transporten är HTTPS är standard porten 443.</span><span class="sxs-lookup"><span data-stu-id="262ab-178">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="262ab-179">När du använder HTTPS som transport måste värdet för parametern *computername* matcha serverns certifikats eget namn (CN).</span><span class="sxs-lookup"><span data-stu-id="262ab-179">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>

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

### <span data-ttu-id="262ab-180">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="262ab-180">-UseSSL</span></span>

<span data-ttu-id="262ab-181">Anger att Secure Sockets Layer-protokollet (SSL) används för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="262ab-181">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="262ab-182">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="262ab-182">By default, SSL is not used.</span></span>

<span data-ttu-id="262ab-183">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="262ab-183">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="262ab-184">Med parametern *UseSSL* kan du ange ytterligare skydd av https i stället för http.</span><span class="sxs-lookup"><span data-stu-id="262ab-184">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="262ab-185">Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="262ab-185">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="262ab-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="262ab-186">CommonParameters</span></span>

<span data-ttu-id="262ab-187">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="262ab-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="262ab-188">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="262ab-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="262ab-189">INDATA</span><span class="sxs-lookup"><span data-stu-id="262ab-189">INPUTS</span></span>

### <span data-ttu-id="262ab-190">Inget</span><span class="sxs-lookup"><span data-stu-id="262ab-190">None</span></span>

<span data-ttu-id="262ab-191">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="262ab-191">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="262ab-192">UTDATA</span><span class="sxs-lookup"><span data-stu-id="262ab-192">OUTPUTS</span></span>

### <span data-ttu-id="262ab-193">Inget</span><span class="sxs-lookup"><span data-stu-id="262ab-193">None</span></span>

<span data-ttu-id="262ab-194">Denna cmdlet genererar inga utdata-objekt.</span><span class="sxs-lookup"><span data-stu-id="262ab-194">This cmdlet does not generate any output object.</span></span>

## <span data-ttu-id="262ab-195">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="262ab-195">NOTES</span></span>

* <span data-ttu-id="262ab-196">Som standard frågar **test-WSMan-** cmdleten WinRM-tjänsten utan att använda autentisering, och den returnerar ingen information som är speciell för operativ systemets version.</span><span class="sxs-lookup"><span data-stu-id="262ab-196">By default, the **Test-WSMan** cmdlet queries the WinRM service without using authentication, and it returns no information that is specific to the operating-system version.</span></span> <span data-ttu-id="262ab-197">I stället visas null-värden för operativ system versionen och service pack nivån (OS: 0.0.0 SP: 0,0).</span><span class="sxs-lookup"><span data-stu-id="262ab-197">Instead, it displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

*

## <span data-ttu-id="262ab-198">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="262ab-198">RELATED LINKS</span></span>

[<span data-ttu-id="262ab-199">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="262ab-199">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="262ab-200">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="262ab-200">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="262ab-201">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="262ab-201">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="262ab-202">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="262ab-202">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="262ab-203">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="262ab-203">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="262ab-204">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="262ab-204">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="262ab-205">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="262ab-205">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="262ab-206">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="262ab-206">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="262ab-207">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="262ab-207">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="262ab-208">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="262ab-208">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="262ab-209">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="262ab-209">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="262ab-210">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="262ab-210">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)
