---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManInstance
ms.openlocfilehash: 2e5d68c2a75ea3040fd3998d2dc469200c054e58
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710752"
---
# <span data-ttu-id="7571d-102">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="7571d-102">Set-WSManInstance</span></span>

## <span data-ttu-id="7571d-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7571d-103">SYNOPSIS</span></span>
<span data-ttu-id="7571d-104">Ändrar den hanterings information som är relaterad till en resurs.</span><span class="sxs-lookup"><span data-stu-id="7571d-104">Modifies the management information that is related to a resource.</span></span>

## <span data-ttu-id="7571d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7571d-105">SYNTAX</span></span>

### <span data-ttu-id="7571d-106">ComputerName (standard)</span><span class="sxs-lookup"><span data-stu-id="7571d-106">ComputerName (Default)</span></span>

```
Set-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-Dialect <Uri>] [-FilePath <String>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri>
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="7571d-107">URI</span><span class="sxs-lookup"><span data-stu-id="7571d-107">URI</span></span>

```
Set-WSManInstance [-ConnectionURI <Uri>] [-Dialect <Uri>] [-FilePath <String>] [-Fragment <String>]
 [-OptionSet <Hashtable>] [-ResourceURI] <Uri> [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-ValueSet <Hashtable>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="7571d-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7571d-108">DESCRIPTION</span></span>

<span data-ttu-id="7571d-109">Set-WSManInstance-cmdleten ändrar hanterings informationen som är relaterad till en resurs.</span><span class="sxs-lookup"><span data-stu-id="7571d-109">The Set-WSManInstance cmdlet modifies the management information that is related to a resource.</span></span>

<span data-ttu-id="7571d-110">Denna cmdlet använder WinRM-anslutningen/transport lagret för att ändra informationen.</span><span class="sxs-lookup"><span data-stu-id="7571d-110">This cmdlet uses the WinRM connection/transport layer to modify the information.</span></span>

## <span data-ttu-id="7571d-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7571d-111">EXAMPLES</span></span>

### <span data-ttu-id="7571d-112">Exempel 1: inaktivera en lyssnare på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="7571d-112">Example 1: Disable a listener on the local computer</span></span>

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.171, ::1, 2001:4898:0:fff:0:5efe:172.30.168.171...}
```

<span data-ttu-id="7571d-113">Detta kommando inaktiverar https-lyssnaren på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="7571d-113">This command disables the https listener on the local computer.</span></span>

<span data-ttu-id="7571d-114">Viktigt: parametern *ValueSet* är Skift läges känslig när du matchar de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="7571d-114">Important: The *ValueSet* parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="7571d-115">I det här kommandot kan du till exempel</span><span class="sxs-lookup"><span data-stu-id="7571d-115">For example, in this command,</span></span>

<span data-ttu-id="7571d-116">Detta Miss lyckas: `-ValueSet @{enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="7571d-116">This fails: `-ValueSet @{enabled="False"}`</span></span>

<span data-ttu-id="7571d-117">Detta lyckas: `-ValueSet @{Enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="7571d-117">This succeeds: `-ValueSet @{Enabled="False"}`</span></span>

### <span data-ttu-id="7571d-118">Exempel 2: Ange Max storlek för kuvert på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="7571d-118">Example 2: Set the maximum envelope size on the local computer</span></span>

```powershell
Set-WSManInstance -ResourceURI winrm/config -ValueSet @{MaxEnvelopeSizekb = "200"}
```

```Output
cfg                 : http://schemas.microsoft.com/wbem/wsman/1/config
lang                : en-US
MaxEnvelopeSizekb   : 200
MaxTimeoutms        : 60000
MaxBatchItems       : 32000
MaxProviderRequests : 4294967295
Client              : Client
Service             : Service
Winrs               : Winrs
```

<span data-ttu-id="7571d-119">Detta kommando ställer in värdet för MaxEnvelopeSizekb på 200 på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="7571d-119">This command sets the MaxEnvelopeSizekb value to 200 on the local computer.</span></span>

<span data-ttu-id="7571d-120">Viktigt: parametern ValueSet är Skift läges känslig när du matchar de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="7571d-120">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="7571d-121">Du kan till exempel använda kommandot ovan.</span><span class="sxs-lookup"><span data-stu-id="7571d-121">For example, using the above command.</span></span>

<span data-ttu-id="7571d-122">Detta Miss lyckas:-ValueSet @ {MaxEnvelopeSizeKB = "200"}</span><span class="sxs-lookup"><span data-stu-id="7571d-122">This fails:     -ValueSet @{MaxEnvelopeSizeKB ="200"}</span></span>

<span data-ttu-id="7571d-123">Detta lyckas:-ValueSet @ {MaxEnvelopeSizekb = "200"}</span><span class="sxs-lookup"><span data-stu-id="7571d-123">This succeeds:  -ValueSet @{MaxEnvelopeSizekb ="200"}</span></span>

### <span data-ttu-id="7571d-124">Exempel 3: inaktivera en lyssnare på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="7571d-124">Example 3: Disable a listener on a remote computer</span></span>

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -ComputerName SERVER02 -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.172, ::1, 2001:4898:0:fff:0:5efe:172.30.168.172...}
```

<span data-ttu-id="7571d-125">Med det här kommandot inaktive ras https-lyssnaren på fjärrdatorn SERVER02.</span><span class="sxs-lookup"><span data-stu-id="7571d-125">This command disables the https listener on the remote computer SERVER02.</span></span>

<span data-ttu-id="7571d-126">Viktigt: parametern ValueSet är Skift läges känslig när du matchar de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="7571d-126">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="7571d-127">Du kan till exempel använda kommandot ovan.</span><span class="sxs-lookup"><span data-stu-id="7571d-127">For example, using the above command.</span></span>

<span data-ttu-id="7571d-128">Detta Miss lyckas:-ValueSet @ {Enabled = "false"}</span><span class="sxs-lookup"><span data-stu-id="7571d-128">This fails:     -ValueSet @{enabled="False"}</span></span>

<span data-ttu-id="7571d-129">Detta lyckas:-ValueSet @ {Enabled = "false"}</span><span class="sxs-lookup"><span data-stu-id="7571d-129">This succeeds:  -ValueSet @{Enabled="False"}</span></span>

## <span data-ttu-id="7571d-130">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7571d-130">PARAMETERS</span></span>

### <span data-ttu-id="7571d-131">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="7571d-131">-ApplicationName</span></span>

<span data-ttu-id="7571d-132">Anger program namnet i anslutningen.</span><span class="sxs-lookup"><span data-stu-id="7571d-132">Specifies the application name in the connection.</span></span>
<span data-ttu-id="7571d-133">Standardvärdet för parametern ApplicationName är "WSMAN".</span><span class="sxs-lookup"><span data-stu-id="7571d-133">The default value of the ApplicationName parameter is "WSMAN".</span></span>
<span data-ttu-id="7571d-134">Den fullständiga identifieraren för Fjärrslutpunkten har följande format:</span><span class="sxs-lookup"><span data-stu-id="7571d-134">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="7571d-135">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="7571d-135">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="7571d-136">Exempel:</span><span class="sxs-lookup"><span data-stu-id="7571d-136">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="7571d-137">Internet Information Services (IIS), som är värd för sessionen, vidarebefordrar begär Anden med den här slut punkten till det angivna programmet.</span><span class="sxs-lookup"><span data-stu-id="7571d-137">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="7571d-138">Den här standardinställningen för "WSMAN" är lämplig för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="7571d-138">This default setting of "WSMAN" is appropriate for most uses.</span></span>
<span data-ttu-id="7571d-139">Den här parametern är avsedd att användas när flera datorer upprättar fjärr anslutningar till en dator som kör Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7571d-139">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span>
<span data-ttu-id="7571d-140">I det här fallet är IIS värd för webb tjänster för hantering (WS-Management) för effektivitet.</span><span class="sxs-lookup"><span data-stu-id="7571d-140">In this case, IIS hosts Web Services for Management (WS-Management ) for efficiency.</span></span>

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

### <span data-ttu-id="7571d-141">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="7571d-141">-Authentication</span></span>

<span data-ttu-id="7571d-142">Anger vilken autentiseringsmekanism som ska användas på servern.</span><span class="sxs-lookup"><span data-stu-id="7571d-142">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="7571d-143">Möjliga värden:</span><span class="sxs-lookup"><span data-stu-id="7571d-143">Possible values are:</span></span>

- <span data-ttu-id="7571d-144">Basic: Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.</span><span class="sxs-lookup"><span data-stu-id="7571d-144">Basic: Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="7571d-145">Standard: Använd autentiseringsmetoden som implementeras av WS-Management-protokollet.</span><span class="sxs-lookup"><span data-stu-id="7571d-145">Default : Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="7571d-146">Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="7571d-146">This is the default.</span></span>
- <span data-ttu-id="7571d-147">Digest: Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.</span><span class="sxs-lookup"><span data-stu-id="7571d-147">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="7571d-148">Kerberos: klient datorn och servern autentiseras ömsesidigt med hjälp av Kerberos-certifikat.</span><span class="sxs-lookup"><span data-stu-id="7571d-148">Kerberos: The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="7571d-149">Förhandla: Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="7571d-149">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="7571d-150">Detta parameter värde tillåter till exempel förhandling för att avgöra om Kerberos-protokollet eller NTLM används.</span><span class="sxs-lookup"><span data-stu-id="7571d-150">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="7571d-151">CredSSP: Använd CredSSP-autentisering (Credential Security Support Provider), vilket gör att användaren kan delegera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7571d-151">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="7571d-152">Det här alternativet är utformat för kommandon som körs på en fjärrdator men samlar in data från eller kör ytterligare kommandon på andra fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="7571d-152">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="7571d-153">Varning! CredSSP delegerar användarens autentiseringsuppgifter från den lokala datorn till en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="7571d-153">Caution: CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="7571d-154">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="7571d-154">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="7571d-155">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="7571d-155">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7571d-156">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="7571d-156">-CertificateThumbprint</span></span>

<span data-ttu-id="7571d-157">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="7571d-157">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="7571d-158">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="7571d-158">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="7571d-159">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="7571d-159">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="7571d-160">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="7571d-160">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="7571d-161">Om du vill hämta ett tumavtryck för certifikatet använder du kommandot Get-Item eller Get-ChildItem i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="7571d-161">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="7571d-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="7571d-162">-ComputerName</span></span>

<span data-ttu-id="7571d-163">Anger den dator som du vill köra hanterings åtgärden mot.</span><span class="sxs-lookup"><span data-stu-id="7571d-163">Specifies the computer against which you want to run the management operation.</span></span>
<span data-ttu-id="7571d-164">Värdet kan vara ett fullständigt kvalificerat domän namn, ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7571d-164">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="7571d-165">Använd namnet på den lokala datorn, Använd localhost eller Använd en punkt (.) för att ange den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="7571d-165">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="7571d-166">Den lokala datorn är standard.</span><span class="sxs-lookup"><span data-stu-id="7571d-166">The local computer is the default.</span></span>
<span data-ttu-id="7571d-167">Om fjärrdatorn finns i en annan domän än användaren måste du använda ett fullständigt kvalificerat domän namn.</span><span class="sxs-lookup"><span data-stu-id="7571d-167">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="7571d-168">Du kan skicka ett värde för den här parametern till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="7571d-168">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="7571d-169">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="7571d-169">-ConnectionURI</span></span>

<span data-ttu-id="7571d-170">Anger anslutnings slut punkten.</span><span class="sxs-lookup"><span data-stu-id="7571d-170">Specifies the connection endpoint.</span></span>
<span data-ttu-id="7571d-171">Formatet för den här strängen är:</span><span class="sxs-lookup"><span data-stu-id="7571d-171">The format of this string is:</span></span>

<span data-ttu-id="7571d-172">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="7571d-172">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="7571d-173">Följande sträng är ett korrekt formaterat värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="7571d-173">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="7571d-174">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="7571d-174">The URI must be fully qualified .</span></span>

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

### <span data-ttu-id="7571d-175">-Credential</span><span class="sxs-lookup"><span data-stu-id="7571d-175">-Credential</span></span>

<span data-ttu-id="7571d-176">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="7571d-176">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="7571d-177">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="7571d-177">The default is the current user.</span></span>
<span data-ttu-id="7571d-178">Ange ett användar namn, till exempel "user01", "Domain01\User01" eller " User@Domain.com ".</span><span class="sxs-lookup"><span data-stu-id="7571d-178">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span>
<span data-ttu-id="7571d-179">Eller ange ett PSCredential-objekt, till exempel ett som returneras av Get-Credential-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7571d-179">Or, enter a PSCredential object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="7571d-180">När du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="7571d-180">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="7571d-181">– Dialekt</span><span class="sxs-lookup"><span data-stu-id="7571d-181">-Dialect</span></span>

<span data-ttu-id="7571d-182">Anger dialekten som ska användas i filtrets predikat.</span><span class="sxs-lookup"><span data-stu-id="7571d-182">Specifies the dialect to use in the filter predicate.</span></span>
<span data-ttu-id="7571d-183">Detta kan vara vilken dialekt som helst som stöds av fjärrtjänsten.</span><span class="sxs-lookup"><span data-stu-id="7571d-183">This can be any dialect that is supported by the remote service.</span></span>
<span data-ttu-id="7571d-184">Följande alias kan användas för dialekt-URI: n:</span><span class="sxs-lookup"><span data-stu-id="7571d-184">The following aliases can be used for the dialect URI:</span></span>

- <span data-ttu-id="7571d-185">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span><span class="sxs-lookup"><span data-stu-id="7571d-185">WQL: `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span></span>
- <span data-ttu-id="7571d-186">Select `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span><span class="sxs-lookup"><span data-stu-id="7571d-186">Selector: `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span></span>
- <span data-ttu-id="7571d-187">Föreningar `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span><span class="sxs-lookup"><span data-stu-id="7571d-187">Association: `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: http://schemas.microsoft.com/wbem/wsman/1/WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7571d-188">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="7571d-188">-FilePath</span></span>

<span data-ttu-id="7571d-189">Anger sökvägen till en fil som används för att uppdatera en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="7571d-189">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="7571d-190">Du anger hanterings resursen med hjälp av parametern ResourceURI och parametern SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="7571d-190">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter .</span></span>
<span data-ttu-id="7571d-191">Följande kommando använder till exempel parametern sökväg:</span><span class="sxs-lookup"><span data-stu-id="7571d-191">For example, the following command uses the FilePath parameter:</span></span>

`Invoke-WSManAction -action StopService -resourceuri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:c:\input.xml -authentication default`

<span data-ttu-id="7571d-192">Det här kommandot anropar metoden Stop service i Spooler-tjänsten genom att använda indata från en fil.</span><span class="sxs-lookup"><span data-stu-id="7571d-192">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="7571d-193">Filen Input.xml innehåller följande innehåll:</span><span class="sxs-lookup"><span data-stu-id="7571d-193">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7571d-194">– Fragment</span><span class="sxs-lookup"><span data-stu-id="7571d-194">-Fragment</span></span>

<span data-ttu-id="7571d-195">Anger ett avsnitt inuti instansen som ska uppdateras eller hämtas för den angivna åtgärden.</span><span class="sxs-lookup"><span data-stu-id="7571d-195">Specifies a section inside the instance that is to be updated or retrieved for the specified operation.</span></span>
<span data-ttu-id="7571d-196">Om du till exempel vill hämta statusen för en Spooler-tjänst anger du "-fragment status".</span><span class="sxs-lookup"><span data-stu-id="7571d-196">For example, to get the status of a spooler service, specify "-Fragment Status".</span></span>

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

### <span data-ttu-id="7571d-197">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="7571d-197">-OptionSet</span></span>

<span data-ttu-id="7571d-198">Skickar en uppsättning växlar till en tjänst för att ändra eller förfina begärans natur.</span><span class="sxs-lookup"><span data-stu-id="7571d-198">Passes a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="7571d-199">Dessa liknar växlar som används i kommando rads gränssnitt eftersom de är specifika för specifika tjänster.</span><span class="sxs-lookup"><span data-stu-id="7571d-199">These are similar to switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="7571d-200">Valfritt antal alternativ kan anges.</span><span class="sxs-lookup"><span data-stu-id="7571d-200">Any number of options can be specified.</span></span>

<span data-ttu-id="7571d-201">I följande exempel visas syntaxen som skickar värdena 1, 2 och 3 för parametrarna a, b och c:</span><span class="sxs-lookup"><span data-stu-id="7571d-201">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

<span data-ttu-id="7571d-202">-OptionSet @ {a = 1; b = 2; c = 3}</span><span class="sxs-lookup"><span data-stu-id="7571d-202">-OptionSet @{a=1;b=2;c=3}</span></span>

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

### <span data-ttu-id="7571d-203">-Port</span><span class="sxs-lookup"><span data-stu-id="7571d-203">-Port</span></span>

<span data-ttu-id="7571d-204">Anger vilken port som ska användas när klienten ansluter till WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7571d-204">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="7571d-205">När transporten är HTTP är standard porten 80.</span><span class="sxs-lookup"><span data-stu-id="7571d-205">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="7571d-206">När transporten är HTTPS är standard porten 443.</span><span class="sxs-lookup"><span data-stu-id="7571d-206">When the transport is HTTPS, the default port is 443.</span></span>
<span data-ttu-id="7571d-207">När du använder HTTPS som transport måste värdet för parametern ComputerName matcha serverns certifikats eget namn (CN).</span><span class="sxs-lookup"><span data-stu-id="7571d-207">When you use HTTPS as the transport, the value of the ComputerName parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="7571d-208">Men om parametern SkipCNCheck anges som en del av parametern SessionOption, behöver inte Certifikatets gemensamma namn matcha serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="7571d-208">However, if the SkipCNCheck parameter is specified as part of the SessionOption parameter, then the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="7571d-209">Parametern SkipCNCheck ska endast användas för betrodda datorer.</span><span class="sxs-lookup"><span data-stu-id="7571d-209">The SkipCNCheck parameter should be used only for trusted machines.</span></span>

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

### <span data-ttu-id="7571d-210">– ResourceURI</span><span class="sxs-lookup"><span data-stu-id="7571d-210">-ResourceURI</span></span>

<span data-ttu-id="7571d-211">Innehåller Uniform Resource Identifier (URI) för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="7571d-211">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="7571d-212">URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="7571d-212">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="7571d-213">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="7571d-213">A URI consists of a prefix and a path to a resource.</span></span>
<span data-ttu-id="7571d-214">Exempel:</span><span class="sxs-lookup"><span data-stu-id="7571d-214">For example:</span></span>

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

### <span data-ttu-id="7571d-215">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="7571d-215">-SelectorSet</span></span>

<span data-ttu-id="7571d-216">Anger en uppsättning värdepar som används för att välja specifika hanterings resurs instanser.</span><span class="sxs-lookup"><span data-stu-id="7571d-216">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="7571d-217">Parametern SelectorSet används när det finns mer än en instans av resursen.</span><span class="sxs-lookup"><span data-stu-id="7571d-217">The SelectorSet parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="7571d-218">Värdet för parametern SelectorSet måste vara en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="7571d-218">The value of the SelectorSet parameter must be a hash table.</span></span>
<span data-ttu-id="7571d-219">I följande exempel visas hur du anger ett värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="7571d-219">The following example shows how to enter a value for this parameter:</span></span>

<span data-ttu-id="7571d-220">-SelectorSet @ {Name = "WinRM"; ID = "YYY"}</span><span class="sxs-lookup"><span data-stu-id="7571d-220">-SelectorSet @{Name="WinRM";ID="yyy"}</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7571d-221">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="7571d-221">-SessionOption</span></span>

<span data-ttu-id="7571d-222">Definierar en uppsättning utökade alternativ för WS-Management-sessionen.</span><span class="sxs-lookup"><span data-stu-id="7571d-222">Defines a set of extended options for the WS-Management session.</span></span>
<span data-ttu-id="7571d-223">Ange ett SessionOption-objekt som du skapar med hjälp av New-WSManSessionOption-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7571d-223">Enter a SessionOption object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="7571d-224">Mer information om tillgängliga alternativ finns i New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="7571d-224">For more information about the options that are available, see New-WSManSessionOption.</span></span>

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

### <span data-ttu-id="7571d-225">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="7571d-225">-UseSSL</span></span>

<span data-ttu-id="7571d-226">Anger att Secure Sockets Layer (SSL)-protokollet ska användas för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="7571d-226">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="7571d-227">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="7571d-227">By default, SSL is not used.</span></span>

<span data-ttu-id="7571d-228">WS-Management krypterar allt Windows PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="7571d-228">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="7571d-229">Med parametern UseSSL kan du ange ytterligare skydd av HTTPS i stället för HTTP.</span><span class="sxs-lookup"><span data-stu-id="7571d-229">The UseSSL parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="7571d-230">Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="7571d-230">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="7571d-231">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="7571d-231">-ValueSet</span></span>

<span data-ttu-id="7571d-232">Anger en hash-tabell som hjälper dig att ändra en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="7571d-232">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="7571d-233">Du anger hanterings resursen med hjälp av parametern ResourceURI och parametern SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="7571d-233">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter.</span></span>
<span data-ttu-id="7571d-234">Värdet för parametern ValueSet måste vara en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="7571d-234">The value of the ValueSet parameter must be a hash table.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7571d-235">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7571d-235">CommonParameters</span></span>

<span data-ttu-id="7571d-236">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7571d-236">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7571d-237">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="7571d-237">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7571d-238">INDATA</span><span class="sxs-lookup"><span data-stu-id="7571d-238">INPUTS</span></span>

### <span data-ttu-id="7571d-239">Inga</span><span class="sxs-lookup"><span data-stu-id="7571d-239">None</span></span>

<span data-ttu-id="7571d-240">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="7571d-240">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="7571d-241">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7571d-241">OUTPUTS</span></span>

### <span data-ttu-id="7571d-242">Inga</span><span class="sxs-lookup"><span data-stu-id="7571d-242">None</span></span>

<span data-ttu-id="7571d-243">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="7571d-243">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7571d-244">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7571d-244">NOTES</span></span>

## <span data-ttu-id="7571d-245">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7571d-245">RELATED LINKS</span></span>

[<span data-ttu-id="7571d-246">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="7571d-246">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="7571d-247">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="7571d-247">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="7571d-248">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="7571d-248">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="7571d-249">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="7571d-249">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="7571d-250">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="7571d-250">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="7571d-251">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="7571d-251">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="7571d-252">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="7571d-252">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="7571d-253">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="7571d-253">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="7571d-254">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="7571d-254">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="7571d-255">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="7571d-255">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="7571d-256">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="7571d-256">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="7571d-257">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="7571d-257">Test-WSMan</span></span>](Test-WSMan.md)

