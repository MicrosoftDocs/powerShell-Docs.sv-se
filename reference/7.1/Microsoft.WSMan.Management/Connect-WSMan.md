---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/connect-wsman?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-WSMan
ms.openlocfilehash: 43fb3ce70ced5f228f27031b013cc1589a3634a8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263409"
---
# <span data-ttu-id="027cf-103">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="027cf-103">Connect-WSMan</span></span>

## <span data-ttu-id="027cf-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="027cf-104">SYNOPSIS</span></span>
<span data-ttu-id="027cf-105">Ansluter till WinRM-tjänsten på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="027cf-105">Connects to the WinRM service on a remote computer.</span></span>

## <span data-ttu-id="027cf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="027cf-106">SYNTAX</span></span>

### <span data-ttu-id="027cf-107">ComputerName (standard)</span><span class="sxs-lookup"><span data-stu-id="027cf-107">ComputerName (Default)</span></span>

```
Connect-WSMan [-ApplicationName <String>] [[-ComputerName] <String>] [-OptionSet <Hashtable>] [-Port <Int32>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="027cf-108">URI</span><span class="sxs-lookup"><span data-stu-id="027cf-108">URI</span></span>

```
Connect-WSMan [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-Port <Int32>] [-SessionOption <SessionOption>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="027cf-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="027cf-109">DESCRIPTION</span></span>
<span data-ttu-id="027cf-110">Cmdleten **Connect-WSMan** ansluter till WinRM-tjänsten på en fjärrdator och upprättar en permanent anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="027cf-110">The **Connect-WSMan** cmdlet connects to the WinRM service on a remote computer, and it establishes a persistent connection to the remote computer.</span></span>
<span data-ttu-id="027cf-111">Du kan använda denna cmdlet i kontexten för WSMan-providern för att ansluta till WinRM-tjänsten på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="027cf-111">You can use this cmdlet in the context of the WSMan provider to connect to the WinRM service on a remote computer.</span></span>
<span data-ttu-id="027cf-112">Du kan dock även använda denna cmdlet för att ansluta till WinRM-tjänsten på en fjärrdator innan du ändrar till WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="027cf-112">However, you can also use this cmdlet to connect to the WinRM service on a remote computer before you change to the WSMan provider.</span></span>
<span data-ttu-id="027cf-113">Den fjärranslutna datorn visas i rot katalogen för WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="027cf-113">The remote computer appears in the root directory of the WSMan provider.</span></span>

<span data-ttu-id="027cf-114">Explicita autentiseringsuppgifter krävs när klient-och serverdatorer finns i olika domäner eller arbets grupper.</span><span class="sxs-lookup"><span data-stu-id="027cf-114">Explicit credentials are required when the client and server computers are in different domains or workgroups.</span></span>

<span data-ttu-id="027cf-115">Information om hur du kopplar från tjänsten WinRM på en fjärrdator finns i Disconnect-WSMan-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="027cf-115">For information about how to disconnect from the WinRM service on a remote computer, see the Disconnect-WSMan cmdlet.</span></span>

## <span data-ttu-id="027cf-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="027cf-116">EXAMPLES</span></span>

### <span data-ttu-id="027cf-117">Exempel 1: Anslut till en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="027cf-117">Example 1: Connect to a remote computer</span></span>

```
PS C:\> Connect-WSMan -ComputerName "server01"
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="027cf-118">Det här kommandot skapar en anslutning till den fjärranslutna Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="027cf-118">This command creates a connection to the remote server01 computer.</span></span>

<span data-ttu-id="027cf-119">Cmdleten **Connect-WSMan** används vanligt vis i kontexten för WSMan-providern för att ansluta till en fjärrdator, i det här fallet Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="027cf-119">The **Connect-WSMan** cmdlet is generally used in the context of the WSMan provider to connect to a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="027cf-120">Du kan dock använda cmdleten för att upprätta anslutningar till fjärrdatorer innan du byter till WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="027cf-120">However, you can use the cmdlet to establish connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="027cf-121">Dessa anslutningar visas i listan **dator namn** .</span><span class="sxs-lookup"><span data-stu-id="027cf-121">Those connections appear in the **ComputerName** list.</span></span>

### <span data-ttu-id="027cf-122">Exempel 2: Anslut till en fjärrdator med hjälp av administratörsautentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="027cf-122">Example 2: Connect to a remote computer by using Administrator credentials</span></span>

```
PS C:\> $cred = Get-Credential Administrator
PS C:\> Connect-WSMan -ComputerName "server01" -Credential $cred
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="027cf-123">Det här kommandot skapar en anslutning till fjärrsystemet Server01 med hjälp av autentiseringsuppgifter för administratörs kontot.</span><span class="sxs-lookup"><span data-stu-id="027cf-123">This command creates a connection to the remote system server01 using the Administrator account credentials.</span></span>

<span data-ttu-id="027cf-124">Det första kommandot använder Get-Credential-cmdlet för att hämta autentiseringsuppgifter för administratören och lagrar dem i $cred-variabeln.</span><span class="sxs-lookup"><span data-stu-id="027cf-124">The first command uses the Get-Credential cmdlet to get the Administrator credentials and then stores them in the $cred variable.</span></span>
<span data-ttu-id="027cf-125">**Get-Credential** uppmanas att ange ett lösen ord för användar namn och lösen ord via en dialog ruta eller på kommando raden, beroende på systemets register inställningar.</span><span class="sxs-lookup"><span data-stu-id="027cf-125">**Get-Credential** prompts you for a password of username and password through a dialog box or at the command line, depending on system registry settings.</span></span>

<span data-ttu-id="027cf-126">Det andra kommandot använder parametern *Credential* för att skicka autentiseringsuppgifterna som lagras i $cred till **Connect-WSMan**.</span><span class="sxs-lookup"><span data-stu-id="027cf-126">The second command uses the *Credential* parameter to pass the credentials stored in $cred to **Connect-WSMan**.</span></span>
<span data-ttu-id="027cf-127">**Anslut-WSMan** ansluter sedan till Server01 för fjärrsystemet med hjälp av administratörs behörighet.</span><span class="sxs-lookup"><span data-stu-id="027cf-127">**Connect-WSMan** then connects to the remote system server01 by using the Administrator credentials.</span></span>

### <span data-ttu-id="027cf-128">Exempel 3: Anslut till en fjärran sluten dator över en angiven port</span><span class="sxs-lookup"><span data-stu-id="027cf-128">Example 3: Connect to a remote computer over a specified port</span></span>

```
PS C:\> Connect-WSMan -ComputerName "server01" -Port 80
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="027cf-129">Det här kommandot skapar en anslutning till fjärran Server01-datorn via port 80.</span><span class="sxs-lookup"><span data-stu-id="027cf-129">This command creates a connection to the remote server01 computer over port 80.</span></span>

### <span data-ttu-id="027cf-130">Exempel 4: Anslut till en fjärrdator med hjälp av anslutnings alternativ</span><span class="sxs-lookup"><span data-stu-id="027cf-130">Example 4: Connect to a remote computer by using connection options</span></span>

```
PS C:\> $a = New-WSManSessionOption -OperationTimeout 30000
PS C:\> Connect-WSMan -ComputerName "server01" -SessionOption $a
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="027cf-131">I det här exemplet skapas en anslutning till den fjärranslutna Server01-datorn med hjälp av anslutnings alternativen som definieras i kommandot **New-WSManSessionOption** .</span><span class="sxs-lookup"><span data-stu-id="027cf-131">This example creates a connection to the remote server01 computer by using the connection options that are defined in the **New-WSManSessionOption** command.</span></span>

<span data-ttu-id="027cf-132">Det första kommandot använder **New-WSManSessionOption** för att lagra en uppsättning anslutnings inställnings alternativ i variabeln $a.</span><span class="sxs-lookup"><span data-stu-id="027cf-132">The first command uses **New-WSManSessionOption** to store a set of connection setting options in the $a variable.</span></span>
<span data-ttu-id="027cf-133">I det här fallet har sessions alternativen en anslutnings tid på 30 sekunder (30 000 millisekunder).</span><span class="sxs-lookup"><span data-stu-id="027cf-133">In this case, the session options set a connection time out of 30 seconds (30,000 milliseconds).</span></span>

<span data-ttu-id="027cf-134">Det andra kommandot använder parametern *SessionOption* för att skicka de autentiseringsuppgifter som lagras i variabeln $a för att **ansluta-WSMan**.</span><span class="sxs-lookup"><span data-stu-id="027cf-134">The second command uses the *SessionOption* parameter to pass the credentials that are stored in the $a variable to **Connect-WSMan**.</span></span>
<span data-ttu-id="027cf-135">Sedan ansluter **-WSMan** till den fjärranslutna Server01-datorn med hjälp av de angivna session alternativen.</span><span class="sxs-lookup"><span data-stu-id="027cf-135">Then, **Connect-WSMan** connects to the remote server01 computer by using the specified session options.</span></span>

## <span data-ttu-id="027cf-136">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="027cf-136">PARAMETERS</span></span>

### <span data-ttu-id="027cf-137">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="027cf-137">-ApplicationName</span></span>
<span data-ttu-id="027cf-138">Anger program namnet i anslutningen.</span><span class="sxs-lookup"><span data-stu-id="027cf-138">Specifies the application name in the connection.</span></span>
<span data-ttu-id="027cf-139">Standardvärdet för parametern *ApplicationName* är WSMan.</span><span class="sxs-lookup"><span data-stu-id="027cf-139">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="027cf-140">Den fullständiga identifieraren för Fjärrslutpunkten har följande format:</span><span class="sxs-lookup"><span data-stu-id="027cf-140">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="027cf-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="027cf-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="027cf-142">Exempelvis: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="027cf-142">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="027cf-143">Internet Information Services (IIS), som är värd för sessionen, vidarebefordrar begär Anden med den här slut punkten till det angivna programmet.</span><span class="sxs-lookup"><span data-stu-id="027cf-143">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="027cf-144">Den här standardinställningen för WSMAN är lämplig för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="027cf-144">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="027cf-145">Den här parametern är avsedd att användas om många datorer upprättar fjärr anslutningar till en dator som kör PowerShell.</span><span class="sxs-lookup"><span data-stu-id="027cf-145">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="027cf-146">I det här fallet är IIS värd för webb tjänster för hantering (WS-Management) för effektivitet.</span><span class="sxs-lookup"><span data-stu-id="027cf-146">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="027cf-147">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="027cf-147">-Authentication</span></span>
<span data-ttu-id="027cf-148">Anger vilken autentiseringsmekanism som ska användas på servern.</span><span class="sxs-lookup"><span data-stu-id="027cf-148">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="027cf-149">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="027cf-149">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="027cf-150">Frö.</span><span class="sxs-lookup"><span data-stu-id="027cf-150">Basic.</span></span>
<span data-ttu-id="027cf-151">Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.</span><span class="sxs-lookup"><span data-stu-id="027cf-151">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="027cf-152">Standard.</span><span class="sxs-lookup"><span data-stu-id="027cf-152">Default.</span></span>
<span data-ttu-id="027cf-153">Använd autentiseringsmetoden som implementeras av WS-Management-protokollet.</span><span class="sxs-lookup"><span data-stu-id="027cf-153">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="027cf-154">Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="027cf-154">This is the default.</span></span>
- <span data-ttu-id="027cf-155">Nedbrytning.</span><span class="sxs-lookup"><span data-stu-id="027cf-155">Digest.</span></span>
<span data-ttu-id="027cf-156">Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.</span><span class="sxs-lookup"><span data-stu-id="027cf-156">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="027cf-157">Paket.</span><span class="sxs-lookup"><span data-stu-id="027cf-157">Kerberos.</span></span>
<span data-ttu-id="027cf-158">Klient datorn och servern autentiseras ömsesidigt med hjälp av Kerberos-certifikat.</span><span class="sxs-lookup"><span data-stu-id="027cf-158">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="027cf-159">Fram.</span><span class="sxs-lookup"><span data-stu-id="027cf-159">Negotiate.</span></span>
<span data-ttu-id="027cf-160">Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="027cf-160">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="027cf-161">Detta parameter värde kan till exempel användas för förhandling för att avgöra om Kerberos-protokollet eller NTLM används.</span><span class="sxs-lookup"><span data-stu-id="027cf-161">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="027cf-162">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="027cf-162">CredSSP.</span></span>
<span data-ttu-id="027cf-163">Använd CredSSP-autentisering (Credential Security Support Provider), vilket gör att användaren kan delegera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="027cf-163">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="027cf-164">Det här alternativet är utformat för kommandon som körs på en fjärrdator men samlar in data från eller kör ytterligare kommandon på andra fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="027cf-164">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="027cf-165">Varning! CredSSP delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="027cf-165">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="027cf-166">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="027cf-166">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="027cf-167">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="027cf-167">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="027cf-168">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="027cf-168">-CertificateThumbprint</span></span>
<span data-ttu-id="027cf-169">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="027cf-169">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="027cf-170">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="027cf-170">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="027cf-171">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="027cf-171">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="027cf-172">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="027cf-172">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="027cf-173">Om du vill hämta ett tumavtryck för certifikatet använder du kommandot Get-Item eller Get-ChildItem i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="027cf-173">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="027cf-174">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="027cf-174">-ComputerName</span></span>
<span data-ttu-id="027cf-175">Anger den dator som hanterings åtgärden ska köras mot.</span><span class="sxs-lookup"><span data-stu-id="027cf-175">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="027cf-176">Värdet kan vara ett fullständigt kvalificerat domän namn, ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="027cf-176">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="027cf-177">Använd namnet på den lokala datorn, Använd localhost eller Använd en punkt (.) för att ange den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="027cf-177">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="027cf-178">Den lokala datorn är standard.</span><span class="sxs-lookup"><span data-stu-id="027cf-178">The local computer is the default.</span></span>
<span data-ttu-id="027cf-179">Om fjärrdatorn finns i en annan domän än användaren måste du använda ett fullständigt kvalificerat domän namn.</span><span class="sxs-lookup"><span data-stu-id="027cf-179">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="027cf-180">Du kan skicka ett värde för den här parametern till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="027cf-180">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="027cf-181">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="027cf-181">-ConnectionURI</span></span>
<span data-ttu-id="027cf-182">Anger anslutnings slut punkten.</span><span class="sxs-lookup"><span data-stu-id="027cf-182">Specifies the connection endpoint.</span></span>
<span data-ttu-id="027cf-183">Formatet för den här strängen är följande:</span><span class="sxs-lookup"><span data-stu-id="027cf-183">The format of this string is as follows:</span></span>

<span data-ttu-id="027cf-184">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="027cf-184">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="027cf-185">Följande sträng är ett korrekt formaterat värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="027cf-185">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="027cf-186">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="027cf-186">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="027cf-187">-Credential</span><span class="sxs-lookup"><span data-stu-id="027cf-187">-Credential</span></span>
<span data-ttu-id="027cf-188">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="027cf-188">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="027cf-189">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="027cf-189">The default is the current user.</span></span>
<span data-ttu-id="027cf-190">Ange ett användar namn, till exempel user01, Domain01\User01 eller User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="027cf-190">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="027cf-191">Eller ange ett **PSCredential** -objekt, till exempel ett som returneras av Get-Credential-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="027cf-191">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="027cf-192">När du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="027cf-192">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="027cf-193">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="027cf-193">-OptionSet</span></span>
<span data-ttu-id="027cf-194">Anger en uppsättning växlar till en tjänst för att ändra eller förfina begärans typ.</span><span class="sxs-lookup"><span data-stu-id="027cf-194">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="027cf-195">Dessa liknar växlar som används i kommando rads gränssnitt eftersom de är specifika för specifika tjänster.</span><span class="sxs-lookup"><span data-stu-id="027cf-195">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="027cf-196">Valfritt antal alternativ kan anges.</span><span class="sxs-lookup"><span data-stu-id="027cf-196">Any number of options can be specified.</span></span>

<span data-ttu-id="027cf-197">I följande exempel visas syntaxen som skickar värdena 1, 2 och 3 för parametrarna a, b och c:</span><span class="sxs-lookup"><span data-stu-id="027cf-197">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="027cf-198">-Port</span><span class="sxs-lookup"><span data-stu-id="027cf-198">-Port</span></span>
<span data-ttu-id="027cf-199">Anger vilken port som ska användas när klienten ansluter till WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="027cf-199">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="027cf-200">När transporten är HTTP är standard porten 80.</span><span class="sxs-lookup"><span data-stu-id="027cf-200">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="027cf-201">När transporten är HTTPS är standard porten 443.</span><span class="sxs-lookup"><span data-stu-id="027cf-201">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="027cf-202">När du använder HTTPS som transport måste värdet för parametern *computername* matcha serverns certifikats eget namn (CN).</span><span class="sxs-lookup"><span data-stu-id="027cf-202">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="027cf-203">Men om parametern *SkipCNCheck* anges som en del av parametern *SessionOption* , behöver inte Certifikatets gemensamma namn matcha serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="027cf-203">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="027cf-204">Parametern *SkipCNCheck* ska endast användas för betrodda datorer.</span><span class="sxs-lookup"><span data-stu-id="027cf-204">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="027cf-205">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="027cf-205">-SessionOption</span></span>
<span data-ttu-id="027cf-206">Anger utökade alternativ för WS-Management-sessionen.</span><span class="sxs-lookup"><span data-stu-id="027cf-206">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="027cf-207">Ange ett **SessionOption** -objekt som du skapar med hjälp av New-WSManSessionOption-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="027cf-207">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="027cf-208">Om du vill ha mer information om vilka alternativ som är tillgängliga skriver du `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="027cf-208">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="027cf-209">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="027cf-209">-UseSSL</span></span>
<span data-ttu-id="027cf-210">Anger att Secure Sockets Layer-protokollet (SSL) används för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="027cf-210">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="027cf-211">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="027cf-211">By default, SSL is not used.</span></span>

<span data-ttu-id="027cf-212">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="027cf-212">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="027cf-213">Med parametern *UseSSL* kan du ange ytterligare skydd av https i stället för http.</span><span class="sxs-lookup"><span data-stu-id="027cf-213">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="027cf-214">Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="027cf-214">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="027cf-215">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="027cf-215">CommonParameters</span></span>
<span data-ttu-id="027cf-216">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="027cf-216">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="027cf-217">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="027cf-217">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="027cf-218">INDATA</span><span class="sxs-lookup"><span data-stu-id="027cf-218">INPUTS</span></span>

### <span data-ttu-id="027cf-219">Inget</span><span class="sxs-lookup"><span data-stu-id="027cf-219">None</span></span>
<span data-ttu-id="027cf-220">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="027cf-220">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="027cf-221">UTDATA</span><span class="sxs-lookup"><span data-stu-id="027cf-221">OUTPUTS</span></span>

### <span data-ttu-id="027cf-222">Inget</span><span class="sxs-lookup"><span data-stu-id="027cf-222">None</span></span>
<span data-ttu-id="027cf-223">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="027cf-223">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="027cf-224">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="027cf-224">NOTES</span></span>

* <span data-ttu-id="027cf-225">Du kan köra hanterings kommandon eller fråga hanterings data på en fjärrdator utan att skapa en WS-Management session.</span><span class="sxs-lookup"><span data-stu-id="027cf-225">You can run management commands or query management data on a remote computer without creating a WS-Management session.</span></span> <span data-ttu-id="027cf-226">Du kan göra detta med hjälp av *computername* -parametrarna för Invoke-WSManAction och get-WSManInstance.</span><span class="sxs-lookup"><span data-stu-id="027cf-226">You can do this by using the *ComputerName* parameters of Invoke-WSManAction and Get-WSManInstance.</span></span> <span data-ttu-id="027cf-227">När du använder parametern *computername* skapar PowerShell en tillfällig anslutning som används för det enskilda kommandot.</span><span class="sxs-lookup"><span data-stu-id="027cf-227">When you use the *ComputerName* parameter, PowerShell creates a temporary connection that is used for the single command.</span></span> <span data-ttu-id="027cf-228">När kommandot har körts stängs anslutningen.</span><span class="sxs-lookup"><span data-stu-id="027cf-228">After the command runs, the connection is closed.</span></span>

*

## <span data-ttu-id="027cf-229">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="027cf-229">RELATED LINKS</span></span>

[<span data-ttu-id="027cf-230">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="027cf-230">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="027cf-231">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="027cf-231">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="027cf-232">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="027cf-232">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="027cf-233">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="027cf-233">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="027cf-234">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="027cf-234">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="027cf-235">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="027cf-235">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="027cf-236">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="027cf-236">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="027cf-237">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="027cf-237">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="027cf-238">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="027cf-238">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="027cf-239">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="027cf-239">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="027cf-240">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="027cf-240">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="027cf-241">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="027cf-241">Test-WSMan</span></span>](Test-WSMan.md)

