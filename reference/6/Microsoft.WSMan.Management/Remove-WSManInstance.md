---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/remove-wsmaninstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WSManInstance
ms.openlocfilehash: 9cddfbe90e352b2099a8f999044f20ba4cba5cc4
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268466"
---
# <span data-ttu-id="17b72-103">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="17b72-103">Remove-WSManInstance</span></span>

## <span data-ttu-id="17b72-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="17b72-104">SYNOPSIS</span></span>
<span data-ttu-id="17b72-105">Tar bort en hanterings resurs instans.</span><span class="sxs-lookup"><span data-stu-id="17b72-105">Deletes a management resource instance.</span></span>

## <span data-ttu-id="17b72-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="17b72-106">SYNTAX</span></span>

### <span data-ttu-id="17b72-107">ComputerName (standard)</span><span class="sxs-lookup"><span data-stu-id="17b72-107">ComputerName (Default)</span></span>

```
Remove-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-UseSSL]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="17b72-108">URI</span><span class="sxs-lookup"><span data-stu-id="17b72-108">URI</span></span>

```
Remove-WSManInstance [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="17b72-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="17b72-109">DESCRIPTION</span></span>

<span data-ttu-id="17b72-110">Cmdlet: en **Remove-WSManInstance** tar bort en instans av en hanterings resurs som anges i parametrarna *ResourceURI* och *SelectorSet* .</span><span class="sxs-lookup"><span data-stu-id="17b72-110">The **Remove-WSManInstance** cmdlet deletes an instance of a management resource that is specified in the *ResourceURI* and *SelectorSet* parameters.</span></span>

<span data-ttu-id="17b72-111">Denna cmdlet använder WinRM-anslutningen/transport lagret för att ta bort hanterings resurs instansen.</span><span class="sxs-lookup"><span data-stu-id="17b72-111">This cmdlet uses the WinRM connection/transport layer to delete the management resource instance.</span></span>

## <span data-ttu-id="17b72-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="17b72-112">EXAMPLES</span></span>

### <span data-ttu-id="17b72-113">Exempel 1: ta bort en lyssnare</span><span class="sxs-lookup"><span data-stu-id="17b72-113">Example 1: Delete a listener</span></span>

```
PS C:\> Remove-WSManInstance -ResourceUri winrm/config/Listener -SelectorSet Address=test.fabrikam.com;Transport=http
```

<span data-ttu-id="17b72-114">Detta kommando tar bort WS-Management HTTP-lyssnare på en dator.</span><span class="sxs-lookup"><span data-stu-id="17b72-114">This command deletes the WS-Management HTTP listener on a computer.</span></span>

## <span data-ttu-id="17b72-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="17b72-115">PARAMETERS</span></span>

### <span data-ttu-id="17b72-116">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="17b72-116">-ApplicationName</span></span>

<span data-ttu-id="17b72-117">Anger program namnet i anslutningen.</span><span class="sxs-lookup"><span data-stu-id="17b72-117">Specifies the application name in the connection.</span></span>
<span data-ttu-id="17b72-118">Standardvärdet för parametern *ApplicationName* är WSMan.</span><span class="sxs-lookup"><span data-stu-id="17b72-118">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="17b72-119">Den fullständiga identifieraren för Fjärrslutpunkten har följande format:</span><span class="sxs-lookup"><span data-stu-id="17b72-119">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="17b72-120">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="17b72-120">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="17b72-121">Exempelvis: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="17b72-121">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="17b72-122">Internet Information Services (IIS), som är värd för sessionen, vidarebefordrar begär Anden med den här slut punkten till det angivna programmet.</span><span class="sxs-lookup"><span data-stu-id="17b72-122">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="17b72-123">Den här standardinställningen för WSMAN är lämplig för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="17b72-123">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="17b72-124">Den här parametern är avsedd att användas om många datorer upprättar fjärr anslutningar till en dator som kör PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17b72-124">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="17b72-125">I det här fallet är IIS värd för webb tjänster för hantering (WS-Management) för effektivitet.</span><span class="sxs-lookup"><span data-stu-id="17b72-125">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17b72-126">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="17b72-126">-Authentication</span></span>

<span data-ttu-id="17b72-127">Anger vilken autentiseringsmekanism som ska användas på servern.</span><span class="sxs-lookup"><span data-stu-id="17b72-127">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="17b72-128">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="17b72-128">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="17b72-129">Frö.</span><span class="sxs-lookup"><span data-stu-id="17b72-129">Basic.</span></span>
<span data-ttu-id="17b72-130">Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.</span><span class="sxs-lookup"><span data-stu-id="17b72-130">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="17b72-131">Standard.</span><span class="sxs-lookup"><span data-stu-id="17b72-131">Default.</span></span>
<span data-ttu-id="17b72-132">Använd autentiseringsmetoden som implementeras av WS-Management-protokollet.</span><span class="sxs-lookup"><span data-stu-id="17b72-132">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="17b72-133">Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="17b72-133">This is the default.</span></span>
- <span data-ttu-id="17b72-134">Nedbrytning.</span><span class="sxs-lookup"><span data-stu-id="17b72-134">Digest.</span></span>
<span data-ttu-id="17b72-135">Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.</span><span class="sxs-lookup"><span data-stu-id="17b72-135">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="17b72-136">Paket.</span><span class="sxs-lookup"><span data-stu-id="17b72-136">Kerberos.</span></span>
<span data-ttu-id="17b72-137">Klient datorn och servern autentiseras ömsesidigt med hjälp av Kerberos-certifikat.</span><span class="sxs-lookup"><span data-stu-id="17b72-137">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="17b72-138">Fram.</span><span class="sxs-lookup"><span data-stu-id="17b72-138">Negotiate.</span></span>
<span data-ttu-id="17b72-139">Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="17b72-139">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="17b72-140">Detta parameter värde kan till exempel användas för förhandling för att avgöra om Kerberos-protokollet eller NTLM används.</span><span class="sxs-lookup"><span data-stu-id="17b72-140">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="17b72-141">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="17b72-141">CredSSP.</span></span>
<span data-ttu-id="17b72-142">Använd CredSSP-autentisering (Credential Security Support Provider), vilket gör att användaren kan delegera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="17b72-142">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="17b72-143">Det här alternativet är utformat för kommandon som körs på en fjärrdator men samlar in data från eller kör ytterligare kommandon på andra fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="17b72-143">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="17b72-144">Varning! CredSSP delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="17b72-144">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="17b72-145">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="17b72-145">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="17b72-146">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="17b72-146">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="17b72-147">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="17b72-147">-CertificateThumbprint</span></span>

<span data-ttu-id="17b72-148">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="17b72-148">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="17b72-149">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="17b72-149">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="17b72-150">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="17b72-150">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="17b72-151">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="17b72-151">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="17b72-152">Om du vill hämta ett tumavtryck för certifikatet använder du kommandot Get-Item eller Get-ChildItem i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="17b72-152">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="17b72-153">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="17b72-153">-ComputerName</span></span>

<span data-ttu-id="17b72-154">Anger den dator som hanterings åtgärden ska köras mot.</span><span class="sxs-lookup"><span data-stu-id="17b72-154">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="17b72-155">Värdet kan vara ett fullständigt kvalificerat domän namn, ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="17b72-155">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="17b72-156">Använd namnet på den lokala datorn, Använd localhost eller Använd en punkt (.) för att ange den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="17b72-156">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="17b72-157">Den lokala datorn är standard.</span><span class="sxs-lookup"><span data-stu-id="17b72-157">The local computer is the default.</span></span>
<span data-ttu-id="17b72-158">Om fjärrdatorn finns i en annan domän än användaren måste du använda ett fullständigt kvalificerat domän namn.</span><span class="sxs-lookup"><span data-stu-id="17b72-158">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="17b72-159">Du kan skicka ett värde för den här parametern till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="17b72-159">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17b72-160">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="17b72-160">-ConnectionURI</span></span>

<span data-ttu-id="17b72-161">Anger anslutnings slut punkten.</span><span class="sxs-lookup"><span data-stu-id="17b72-161">Specifies the connection endpoint.</span></span>
<span data-ttu-id="17b72-162">Formatet för den här strängen är följande:</span><span class="sxs-lookup"><span data-stu-id="17b72-162">The format of this string is as follows:</span></span>

<span data-ttu-id="17b72-163">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="17b72-163">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="17b72-164">Följande sträng är ett korrekt formaterat värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="17b72-164">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="17b72-165">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="17b72-165">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17b72-166">-Credential</span><span class="sxs-lookup"><span data-stu-id="17b72-166">-Credential</span></span>

<span data-ttu-id="17b72-167">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="17b72-167">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="17b72-168">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="17b72-168">The default is the current user.</span></span>
<span data-ttu-id="17b72-169">Ange ett användar namn, till exempel user01, Domain01\User01 eller User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="17b72-169">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="17b72-170">Eller ange ett **PSCredential** -objekt, till exempel ett som returneras av Get-Credential-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="17b72-170">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="17b72-171">När du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="17b72-171">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="17b72-172">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="17b72-172">-OptionSet</span></span>

<span data-ttu-id="17b72-173">Anger en uppsättning växlar till en tjänst för att ändra eller förfina begärans typ.</span><span class="sxs-lookup"><span data-stu-id="17b72-173">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="17b72-174">Dessa liknar växlar som används i kommando rads gränssnitt eftersom de är specifika för specifika tjänster.</span><span class="sxs-lookup"><span data-stu-id="17b72-174">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="17b72-175">Valfritt antal alternativ kan anges.</span><span class="sxs-lookup"><span data-stu-id="17b72-175">Any number of options can be specified.</span></span>

<span data-ttu-id="17b72-176">I följande exempel visas syntaxen som skickar värdena 1, 2 och 3 för parametrarna a, b och c:</span><span class="sxs-lookup"><span data-stu-id="17b72-176">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="17b72-177">-Port</span><span class="sxs-lookup"><span data-stu-id="17b72-177">-Port</span></span>

<span data-ttu-id="17b72-178">Anger vilken port som ska användas när klienten ansluter till WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="17b72-178">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="17b72-179">När transporten är HTTP är standard porten 80.</span><span class="sxs-lookup"><span data-stu-id="17b72-179">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="17b72-180">När transporten är HTTPS är standard porten 443.</span><span class="sxs-lookup"><span data-stu-id="17b72-180">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="17b72-181">När du använder HTTPS som transport måste värdet för parametern *computername* matcha serverns certifikats eget namn (CN).</span><span class="sxs-lookup"><span data-stu-id="17b72-181">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="17b72-182">Men om parametern *SkipCNCheck* anges som en del av parametern *SessionOption* , behöver inte Certifikatets gemensamma namn matcha serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="17b72-182">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="17b72-183">Parametern *SkipCNCheck* ska endast användas för betrodda datorer.</span><span class="sxs-lookup"><span data-stu-id="17b72-183">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="17b72-184">– ResourceURI</span><span class="sxs-lookup"><span data-stu-id="17b72-184">-ResourceURI</span></span>

<span data-ttu-id="17b72-185">Anger URI för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="17b72-185">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="17b72-186">URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="17b72-186">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="17b72-187">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="17b72-187">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="17b72-188">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="17b72-188">For example:</span></span>

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

### <span data-ttu-id="17b72-189">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="17b72-189">-SelectorSet</span></span>

<span data-ttu-id="17b72-190">Anger en uppsättning värdepar som används för att välja specifika hanterings resurs instanser.</span><span class="sxs-lookup"><span data-stu-id="17b72-190">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="17b72-191">Parametern *SelectorSet* används när det finns mer än en instans av resursen.</span><span class="sxs-lookup"><span data-stu-id="17b72-191">The *SelectorSet* parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="17b72-192">Värdet för *SelectorSet* måste vara en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="17b72-192">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="17b72-193">I följande exempel visas hur du anger ett värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="17b72-193">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="17b72-194">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="17b72-194">-SessionOption</span></span>

<span data-ttu-id="17b72-195">Anger utökade alternativ för WS-Management-sessionen.</span><span class="sxs-lookup"><span data-stu-id="17b72-195">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="17b72-196">Ange ett **SessionOption** -objekt som du skapar med hjälp av New-WSManSessionOption-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="17b72-196">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="17b72-197">Om du vill ha mer information om vilka alternativ som är tillgängliga skriver du `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="17b72-197">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="17b72-198">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="17b72-198">-UseSSL</span></span>

<span data-ttu-id="17b72-199">Anger att Secure Sockets Layer-protokollet (SSL) används för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="17b72-199">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="17b72-200">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="17b72-200">By default, SSL is not used.</span></span>

<span data-ttu-id="17b72-201">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="17b72-201">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="17b72-202">Med parametern *UseSSL* kan du ange ytterligare skydd av https i stället för http.</span><span class="sxs-lookup"><span data-stu-id="17b72-202">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="17b72-203">Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="17b72-203">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases: ssl

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17b72-204">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="17b72-204">CommonParameters</span></span>

<span data-ttu-id="17b72-205">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="17b72-205">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="17b72-206">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="17b72-206">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="17b72-207">INDATA</span><span class="sxs-lookup"><span data-stu-id="17b72-207">INPUTS</span></span>

### <span data-ttu-id="17b72-208">Inget</span><span class="sxs-lookup"><span data-stu-id="17b72-208">None</span></span>

<span data-ttu-id="17b72-209">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="17b72-209">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="17b72-210">UTDATA</span><span class="sxs-lookup"><span data-stu-id="17b72-210">OUTPUTS</span></span>

### <span data-ttu-id="17b72-211">Inget</span><span class="sxs-lookup"><span data-stu-id="17b72-211">None</span></span>

<span data-ttu-id="17b72-212">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="17b72-212">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="17b72-213">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="17b72-213">NOTES</span></span>

* <span data-ttu-id="17b72-214">Remove-WmiObject cmdlet, en Windows Management Instrumentation (WMI)-cmdlet, liknar.</span><span class="sxs-lookup"><span data-stu-id="17b72-214">The Remove-WmiObject cmdlet, a Windows Management Instrumentation (WMI) cmdlet, is similar.</span></span> <span data-ttu-id="17b72-215">**Remove-WmiObject** använder DCOM-anslutningen/transport lagret för att skapa eller uppdatera WMI-instanser.</span><span class="sxs-lookup"><span data-stu-id="17b72-215">**Remove-WmiObject** uses the DCOM connection/transport layer to create or update WMI instances.</span></span>

*

## <span data-ttu-id="17b72-216">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="17b72-216">RELATED LINKS</span></span>

[<span data-ttu-id="17b72-217">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="17b72-217">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="17b72-218">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="17b72-218">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="17b72-219">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="17b72-219">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="17b72-220">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="17b72-220">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="17b72-221">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="17b72-221">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="17b72-222">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="17b72-222">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="17b72-223">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="17b72-223">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="17b72-224">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="17b72-224">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="17b72-225">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="17b72-225">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="17b72-226">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="17b72-226">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="17b72-227">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="17b72-227">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="17b72-228">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="17b72-228">Test-WSMan</span></span>](Test-WSMan.md)
