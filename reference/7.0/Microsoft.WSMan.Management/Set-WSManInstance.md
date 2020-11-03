---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmaninstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManInstance
ms.openlocfilehash: 2547efe8c3784d29fe852288a8442ac17335fe52
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268292"
---
# <span data-ttu-id="3fe35-103">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3fe35-103">Set-WSManInstance</span></span>

## <span data-ttu-id="3fe35-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3fe35-104">SYNOPSIS</span></span>
<span data-ttu-id="3fe35-105">Ändrar den hanterings information som är relaterad till en resurs.</span><span class="sxs-lookup"><span data-stu-id="3fe35-105">Modifies the management information that is related to a resource.</span></span>

## <span data-ttu-id="3fe35-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3fe35-106">SYNTAX</span></span>

### <span data-ttu-id="3fe35-107">ComputerName (standard)</span><span class="sxs-lookup"><span data-stu-id="3fe35-107">ComputerName (Default)</span></span>

```
Set-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-Dialect <Uri>] [-FilePath <String>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri>
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="3fe35-108">URI</span><span class="sxs-lookup"><span data-stu-id="3fe35-108">URI</span></span>

```
Set-WSManInstance [-ConnectionURI <Uri>] [-Dialect <Uri>] [-FilePath <String>] [-Fragment <String>]
 [-OptionSet <Hashtable>] [-ResourceURI] <Uri> [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-ValueSet <Hashtable>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="3fe35-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3fe35-109">DESCRIPTION</span></span>

<span data-ttu-id="3fe35-110">Set-WSManInstance-cmdleten ändrar hanterings informationen som är relaterad till en resurs.</span><span class="sxs-lookup"><span data-stu-id="3fe35-110">The Set-WSManInstance cmdlet modifies the management information that is related to a resource.</span></span>

<span data-ttu-id="3fe35-111">Denna cmdlet använder WinRM-anslutningen/transport lagret för att ändra informationen.</span><span class="sxs-lookup"><span data-stu-id="3fe35-111">This cmdlet uses the WinRM connection/transport layer to modify the information.</span></span>

## <span data-ttu-id="3fe35-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3fe35-112">EXAMPLES</span></span>

### <span data-ttu-id="3fe35-113">Exempel 1: inaktivera en lyssnare på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="3fe35-113">Example 1: Disable a listener on the local computer</span></span>

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

<span data-ttu-id="3fe35-114">Detta kommando inaktiverar https-lyssnaren på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3fe35-114">This command disables the https listener on the local computer.</span></span>

<span data-ttu-id="3fe35-115">Viktigt: parametern *ValueSet* är Skift läges känslig när du matchar de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="3fe35-115">Important: The *ValueSet* parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="3fe35-116">I det här kommandot kan du till exempel</span><span class="sxs-lookup"><span data-stu-id="3fe35-116">For example, in this command,</span></span>

<span data-ttu-id="3fe35-117">Detta Miss lyckas: `-ValueSet @{enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="3fe35-117">This fails: `-ValueSet @{enabled="False"}`</span></span>

<span data-ttu-id="3fe35-118">Detta lyckas: `-ValueSet @{Enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="3fe35-118">This succeeds: `-ValueSet @{Enabled="False"}`</span></span>

### <span data-ttu-id="3fe35-119">Exempel 2: Ange Max storlek för kuvert på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="3fe35-119">Example 2: Set the maximum envelope size on the local computer</span></span>

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

<span data-ttu-id="3fe35-120">Detta kommando ställer in värdet för MaxEnvelopeSizekb på 200 på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3fe35-120">This command sets the MaxEnvelopeSizekb value to 200 on the local computer.</span></span>

<span data-ttu-id="3fe35-121">Viktigt: parametern ValueSet är Skift läges känslig när du matchar de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="3fe35-121">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="3fe35-122">Du kan till exempel använda kommandot ovan.</span><span class="sxs-lookup"><span data-stu-id="3fe35-122">For example, using the above command.</span></span>

<span data-ttu-id="3fe35-123">Detta Miss lyckas:-ValueSet @ {MaxEnvelopeSizeKB = "200"}</span><span class="sxs-lookup"><span data-stu-id="3fe35-123">This fails:     -ValueSet @{MaxEnvelopeSizeKB ="200"}</span></span>

<span data-ttu-id="3fe35-124">Detta lyckas:-ValueSet @ {MaxEnvelopeSizekb = "200"}</span><span class="sxs-lookup"><span data-stu-id="3fe35-124">This succeeds:  -ValueSet @{MaxEnvelopeSizekb ="200"}</span></span>

### <span data-ttu-id="3fe35-125">Exempel 3: inaktivera en lyssnare på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="3fe35-125">Example 3: Disable a listener on a remote computer</span></span>

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

<span data-ttu-id="3fe35-126">Med det här kommandot inaktive ras https-lyssnaren på fjärrdatorn SERVER02.</span><span class="sxs-lookup"><span data-stu-id="3fe35-126">This command disables the https listener on the remote computer SERVER02.</span></span>

<span data-ttu-id="3fe35-127">Viktigt: parametern ValueSet är Skift läges känslig när du matchar de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="3fe35-127">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="3fe35-128">Du kan till exempel använda kommandot ovan.</span><span class="sxs-lookup"><span data-stu-id="3fe35-128">For example, using the above command.</span></span>

<span data-ttu-id="3fe35-129">Detta Miss lyckas:-ValueSet @ {Enabled = "false"}</span><span class="sxs-lookup"><span data-stu-id="3fe35-129">This fails:     -ValueSet @{enabled="False"}</span></span>

<span data-ttu-id="3fe35-130">Detta lyckas:-ValueSet @ {Enabled = "false"}</span><span class="sxs-lookup"><span data-stu-id="3fe35-130">This succeeds:  -ValueSet @{Enabled="False"}</span></span>

## <span data-ttu-id="3fe35-131">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3fe35-131">PARAMETERS</span></span>

### <span data-ttu-id="3fe35-132">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="3fe35-132">-ApplicationName</span></span>

<span data-ttu-id="3fe35-133">Anger program namnet i anslutningen.</span><span class="sxs-lookup"><span data-stu-id="3fe35-133">Specifies the application name in the connection.</span></span>
<span data-ttu-id="3fe35-134">Standardvärdet för parametern ApplicationName är "WSMAN".</span><span class="sxs-lookup"><span data-stu-id="3fe35-134">The default value of the ApplicationName parameter is "WSMAN".</span></span>
<span data-ttu-id="3fe35-135">Den fullständiga identifieraren för Fjärrslutpunkten har följande format:</span><span class="sxs-lookup"><span data-stu-id="3fe35-135">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="3fe35-136">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="3fe35-136">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="3fe35-137">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="3fe35-137">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="3fe35-138">Internet Information Services (IIS), som är värd för sessionen, vidarebefordrar begär Anden med den här slut punkten till det angivna programmet.</span><span class="sxs-lookup"><span data-stu-id="3fe35-138">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="3fe35-139">Den här standardinställningen för "WSMAN" är lämplig för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="3fe35-139">This default setting of "WSMAN" is appropriate for most uses.</span></span>
<span data-ttu-id="3fe35-140">Den här parametern är avsedd att användas när flera datorer upprättar fjärr anslutningar till en dator som kör Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3fe35-140">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span>
<span data-ttu-id="3fe35-141">I det här fallet är IIS värd för webb tjänster för hantering (WS-Management) för effektivitet.</span><span class="sxs-lookup"><span data-stu-id="3fe35-141">In this case, IIS hosts Web Services for Management (WS-Management ) for efficiency.</span></span>

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

### <span data-ttu-id="3fe35-142">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="3fe35-142">-Authentication</span></span>

<span data-ttu-id="3fe35-143">Anger vilken autentiseringsmekanism som ska användas på servern.</span><span class="sxs-lookup"><span data-stu-id="3fe35-143">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="3fe35-144">Möjliga värden:</span><span class="sxs-lookup"><span data-stu-id="3fe35-144">Possible values are:</span></span>

- <span data-ttu-id="3fe35-145">Basic: Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.</span><span class="sxs-lookup"><span data-stu-id="3fe35-145">Basic: Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="3fe35-146">Standard: Använd autentiseringsmetoden som implementeras av WS-Management-protokollet.</span><span class="sxs-lookup"><span data-stu-id="3fe35-146">Default : Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="3fe35-147">Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="3fe35-147">This is the default.</span></span>
- <span data-ttu-id="3fe35-148">Digest: Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.</span><span class="sxs-lookup"><span data-stu-id="3fe35-148">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="3fe35-149">Kerberos: klient datorn och servern autentiseras ömsesidigt med hjälp av Kerberos-certifikat.</span><span class="sxs-lookup"><span data-stu-id="3fe35-149">Kerberos: The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="3fe35-150">Förhandla: Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="3fe35-150">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="3fe35-151">Detta parameter värde tillåter till exempel förhandling för att avgöra om Kerberos-protokollet eller NTLM används.</span><span class="sxs-lookup"><span data-stu-id="3fe35-151">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="3fe35-152">CredSSP: Använd CredSSP-autentisering (Credential Security Support Provider), vilket gör att användaren kan delegera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="3fe35-152">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="3fe35-153">Det här alternativet är utformat för kommandon som körs på en fjärrdator men samlar in data från eller kör ytterligare kommandon på andra fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="3fe35-153">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="3fe35-154">Varning! CredSSP delegerar användarens autentiseringsuppgifter från den lokala datorn till en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="3fe35-154">Caution: CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="3fe35-155">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="3fe35-155">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="3fe35-156">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="3fe35-156">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="3fe35-157">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="3fe35-157">-CertificateThumbprint</span></span>

<span data-ttu-id="3fe35-158">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="3fe35-158">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="3fe35-159">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="3fe35-159">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="3fe35-160">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="3fe35-160">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="3fe35-161">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="3fe35-161">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="3fe35-162">Om du vill hämta ett tumavtryck för certifikatet använder du kommandot Get-Item eller Get-ChildItem i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="3fe35-162">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="3fe35-163">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="3fe35-163">-ComputerName</span></span>

<span data-ttu-id="3fe35-164">Anger den dator som du vill köra hanterings åtgärden mot.</span><span class="sxs-lookup"><span data-stu-id="3fe35-164">Specifies the computer against which you want to run the management operation.</span></span>
<span data-ttu-id="3fe35-165">Värdet kan vara ett fullständigt kvalificerat domän namn, ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="3fe35-165">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="3fe35-166">Använd namnet på den lokala datorn, Använd localhost eller Använd en punkt (.) för att ange den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3fe35-166">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="3fe35-167">Den lokala datorn är standard.</span><span class="sxs-lookup"><span data-stu-id="3fe35-167">The local computer is the default.</span></span>
<span data-ttu-id="3fe35-168">Om fjärrdatorn finns i en annan domän än användaren måste du använda ett fullständigt kvalificerat domän namn.</span><span class="sxs-lookup"><span data-stu-id="3fe35-168">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="3fe35-169">Du kan skicka ett värde för den här parametern till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="3fe35-169">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="3fe35-170">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="3fe35-170">-ConnectionURI</span></span>

<span data-ttu-id="3fe35-171">Anger anslutnings slut punkten.</span><span class="sxs-lookup"><span data-stu-id="3fe35-171">Specifies the connection endpoint.</span></span>
<span data-ttu-id="3fe35-172">Formatet för den här strängen är:</span><span class="sxs-lookup"><span data-stu-id="3fe35-172">The format of this string is:</span></span>

<span data-ttu-id="3fe35-173">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="3fe35-173">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="3fe35-174">Följande sträng är ett korrekt formaterat värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="3fe35-174">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="3fe35-175">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="3fe35-175">The URI must be fully qualified .</span></span>

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

### <span data-ttu-id="3fe35-176">-Credential</span><span class="sxs-lookup"><span data-stu-id="3fe35-176">-Credential</span></span>

<span data-ttu-id="3fe35-177">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="3fe35-177">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="3fe35-178">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="3fe35-178">The default is the current user.</span></span>
<span data-ttu-id="3fe35-179">Ange ett användar namn, till exempel "user01", "Domain01\User01" eller " User@Domain.com ".</span><span class="sxs-lookup"><span data-stu-id="3fe35-179">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span>
<span data-ttu-id="3fe35-180">Eller ange ett PSCredential-objekt, till exempel ett som returneras av Get-Credential-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3fe35-180">Or, enter a PSCredential object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="3fe35-181">När du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="3fe35-181">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="3fe35-182">– Dialekt</span><span class="sxs-lookup"><span data-stu-id="3fe35-182">-Dialect</span></span>

<span data-ttu-id="3fe35-183">Anger dialekten som ska användas i filtrets predikat.</span><span class="sxs-lookup"><span data-stu-id="3fe35-183">Specifies the dialect to use in the filter predicate.</span></span>
<span data-ttu-id="3fe35-184">Detta kan vara vilken dialekt som helst som stöds av fjärrtjänsten.</span><span class="sxs-lookup"><span data-stu-id="3fe35-184">This can be any dialect that is supported by the remote service.</span></span>
<span data-ttu-id="3fe35-185">Följande alias kan användas för dialekt-URI: n:</span><span class="sxs-lookup"><span data-stu-id="3fe35-185">The following aliases can be used for the dialect URI:</span></span>

- <span data-ttu-id="3fe35-186">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span><span class="sxs-lookup"><span data-stu-id="3fe35-186">WQL: `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span></span>
- <span data-ttu-id="3fe35-187">Select `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span><span class="sxs-lookup"><span data-stu-id="3fe35-187">Selector: `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span></span>
- <span data-ttu-id="3fe35-188">Föreningar `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span><span class="sxs-lookup"><span data-stu-id="3fe35-188">Association: `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span></span>

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

### <span data-ttu-id="3fe35-189">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="3fe35-189">-FilePath</span></span>

<span data-ttu-id="3fe35-190">Anger sökvägen till en fil som används för att uppdatera en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="3fe35-190">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="3fe35-191">Du anger hanterings resursen med hjälp av parametern ResourceURI och parametern SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="3fe35-191">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter .</span></span>
<span data-ttu-id="3fe35-192">Följande kommando använder till exempel parametern sökväg:</span><span class="sxs-lookup"><span data-stu-id="3fe35-192">For example, the following command uses the FilePath parameter:</span></span>

`Invoke-WSManAction -action StopService -resourceuri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:c:\input.xml -authentication default`

<span data-ttu-id="3fe35-193">Det här kommandot anropar metoden Stop service i Spooler-tjänsten genom att använda indata från en fil.</span><span class="sxs-lookup"><span data-stu-id="3fe35-193">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="3fe35-194">Filen Input.xml innehåller följande innehåll:</span><span class="sxs-lookup"><span data-stu-id="3fe35-194">The file, Input.xml, contains the following content:</span></span>

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

### <span data-ttu-id="3fe35-195">– Fragment</span><span class="sxs-lookup"><span data-stu-id="3fe35-195">-Fragment</span></span>

<span data-ttu-id="3fe35-196">Anger ett avsnitt inuti instansen som ska uppdateras eller hämtas för den angivna åtgärden.</span><span class="sxs-lookup"><span data-stu-id="3fe35-196">Specifies a section inside the instance that is to be updated or retrieved for the specified operation.</span></span>
<span data-ttu-id="3fe35-197">Om du till exempel vill hämta statusen för en Spooler-tjänst anger du "-fragment status".</span><span class="sxs-lookup"><span data-stu-id="3fe35-197">For example, to get the status of a spooler service, specify "-Fragment Status".</span></span>

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

### <span data-ttu-id="3fe35-198">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="3fe35-198">-OptionSet</span></span>

<span data-ttu-id="3fe35-199">Skickar en uppsättning växlar till en tjänst för att ändra eller förfina begärans natur.</span><span class="sxs-lookup"><span data-stu-id="3fe35-199">Passes a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="3fe35-200">Dessa liknar växlar som används i kommando rads gränssnitt eftersom de är specifika för specifika tjänster.</span><span class="sxs-lookup"><span data-stu-id="3fe35-200">These are similar to switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="3fe35-201">Valfritt antal alternativ kan anges.</span><span class="sxs-lookup"><span data-stu-id="3fe35-201">Any number of options can be specified.</span></span>

<span data-ttu-id="3fe35-202">I följande exempel visas syntaxen som skickar värdena 1, 2 och 3 för parametrarna a, b och c:</span><span class="sxs-lookup"><span data-stu-id="3fe35-202">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

<span data-ttu-id="3fe35-203">-OptionSet @ {a = 1; b = 2; c = 3}</span><span class="sxs-lookup"><span data-stu-id="3fe35-203">-OptionSet @{a=1;b=2;c=3}</span></span>

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

### <span data-ttu-id="3fe35-204">-Port</span><span class="sxs-lookup"><span data-stu-id="3fe35-204">-Port</span></span>

<span data-ttu-id="3fe35-205">Anger vilken port som ska användas när klienten ansluter till WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="3fe35-205">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="3fe35-206">När transporten är HTTP är standard porten 80.</span><span class="sxs-lookup"><span data-stu-id="3fe35-206">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="3fe35-207">När transporten är HTTPS är standard porten 443.</span><span class="sxs-lookup"><span data-stu-id="3fe35-207">When the transport is HTTPS, the default port is 443.</span></span>
<span data-ttu-id="3fe35-208">När du använder HTTPS som transport måste värdet för parametern ComputerName matcha serverns certifikats eget namn (CN).</span><span class="sxs-lookup"><span data-stu-id="3fe35-208">When you use HTTPS as the transport, the value of the ComputerName parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="3fe35-209">Men om parametern SkipCNCheck anges som en del av parametern SessionOption, behöver inte Certifikatets gemensamma namn matcha serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="3fe35-209">However, if the SkipCNCheck parameter is specified as part of the SessionOption parameter, then the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="3fe35-210">Parametern SkipCNCheck ska endast användas för betrodda datorer.</span><span class="sxs-lookup"><span data-stu-id="3fe35-210">The SkipCNCheck parameter should be used only for trusted machines.</span></span>

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

### <span data-ttu-id="3fe35-211">– ResourceURI</span><span class="sxs-lookup"><span data-stu-id="3fe35-211">-ResourceURI</span></span>

<span data-ttu-id="3fe35-212">Innehåller Uniform Resource Identifier (URI) för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="3fe35-212">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="3fe35-213">URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="3fe35-213">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="3fe35-214">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="3fe35-214">A URI consists of a prefix and a path to a resource.</span></span>
<span data-ttu-id="3fe35-215">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="3fe35-215">For example:</span></span>

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

### <span data-ttu-id="3fe35-216">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="3fe35-216">-SelectorSet</span></span>

<span data-ttu-id="3fe35-217">Anger en uppsättning värdepar som används för att välja specifika hanterings resurs instanser.</span><span class="sxs-lookup"><span data-stu-id="3fe35-217">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="3fe35-218">Parametern SelectorSet används när det finns mer än en instans av resursen.</span><span class="sxs-lookup"><span data-stu-id="3fe35-218">The SelectorSet parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="3fe35-219">Värdet för parametern SelectorSet måste vara en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="3fe35-219">The value of the SelectorSet parameter must be a hash table.</span></span>
<span data-ttu-id="3fe35-220">I följande exempel visas hur du anger ett värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="3fe35-220">The following example shows how to enter a value for this parameter:</span></span>

<span data-ttu-id="3fe35-221">-SelectorSet @ {Name = "WinRM"; ID = "YYY"}</span><span class="sxs-lookup"><span data-stu-id="3fe35-221">-SelectorSet @{Name="WinRM";ID="yyy"}</span></span>

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

### <span data-ttu-id="3fe35-222">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="3fe35-222">-SessionOption</span></span>

<span data-ttu-id="3fe35-223">Definierar en uppsättning utökade alternativ för WS-Management-sessionen.</span><span class="sxs-lookup"><span data-stu-id="3fe35-223">Defines a set of extended options for the WS-Management session.</span></span>
<span data-ttu-id="3fe35-224">Ange ett SessionOption-objekt som du skapar med hjälp av New-WSManSessionOption-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3fe35-224">Enter a SessionOption object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="3fe35-225">Mer information om tillgängliga alternativ finns i New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="3fe35-225">For more information about the options that are available, see New-WSManSessionOption.</span></span>

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

### <span data-ttu-id="3fe35-226">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="3fe35-226">-UseSSL</span></span>

<span data-ttu-id="3fe35-227">Anger att Secure Sockets Layer (SSL)-protokollet ska användas för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="3fe35-227">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="3fe35-228">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="3fe35-228">By default, SSL is not used.</span></span>

<span data-ttu-id="3fe35-229">WS-Management krypterar allt Windows PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="3fe35-229">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="3fe35-230">Med parametern UseSSL kan du ange ytterligare skydd av HTTPS i stället för HTTP.</span><span class="sxs-lookup"><span data-stu-id="3fe35-230">The UseSSL parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="3fe35-231">Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="3fe35-231">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="3fe35-232">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="3fe35-232">-ValueSet</span></span>

<span data-ttu-id="3fe35-233">Anger en hash-tabell som hjälper dig att ändra en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="3fe35-233">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="3fe35-234">Du anger hanterings resursen med hjälp av parametern ResourceURI och parametern SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="3fe35-234">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter.</span></span>
<span data-ttu-id="3fe35-235">Värdet för parametern ValueSet måste vara en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="3fe35-235">The value of the ValueSet parameter must be a hash table.</span></span>

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

### <span data-ttu-id="3fe35-236">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3fe35-236">CommonParameters</span></span>

<span data-ttu-id="3fe35-237">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3fe35-237">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3fe35-238">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="3fe35-238">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3fe35-239">INDATA</span><span class="sxs-lookup"><span data-stu-id="3fe35-239">INPUTS</span></span>

### <span data-ttu-id="3fe35-240">Inget</span><span class="sxs-lookup"><span data-stu-id="3fe35-240">None</span></span>

<span data-ttu-id="3fe35-241">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="3fe35-241">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="3fe35-242">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3fe35-242">OUTPUTS</span></span>

### <span data-ttu-id="3fe35-243">Inget</span><span class="sxs-lookup"><span data-stu-id="3fe35-243">None</span></span>

<span data-ttu-id="3fe35-244">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="3fe35-244">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3fe35-245">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3fe35-245">NOTES</span></span>

## <span data-ttu-id="3fe35-246">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3fe35-246">RELATED LINKS</span></span>

[<span data-ttu-id="3fe35-247">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="3fe35-247">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="3fe35-248">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="3fe35-248">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="3fe35-249">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="3fe35-249">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="3fe35-250">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="3fe35-250">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="3fe35-251">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="3fe35-251">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="3fe35-252">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3fe35-252">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="3fe35-253">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="3fe35-253">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="3fe35-254">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3fe35-254">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="3fe35-255">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="3fe35-255">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="3fe35-256">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3fe35-256">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="3fe35-257">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="3fe35-257">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="3fe35-258">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="3fe35-258">Test-WSMan</span></span>](Test-WSMan.md)
