---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/connect-wsman?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-WSMan
ms.openlocfilehash: 5dfd0b355a3589bf45ea92b92ae8778023132bcd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710398"
---
# <span data-ttu-id="56983-102">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="56983-102">Connect-WSMan</span></span>

## <span data-ttu-id="56983-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="56983-103">SYNOPSIS</span></span>
<span data-ttu-id="56983-104">Ansluter till WinRM-tjänsten på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="56983-104">Connects to the WinRM service on a remote computer.</span></span>

## <span data-ttu-id="56983-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="56983-105">SYNTAX</span></span>

### <span data-ttu-id="56983-106">ComputerName (standard)</span><span class="sxs-lookup"><span data-stu-id="56983-106">ComputerName (Default)</span></span>

```
Connect-WSMan [-ApplicationName <String>] [[-ComputerName] <String>] [-OptionSet <Hashtable>] [-Port <Int32>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="56983-107">URI</span><span class="sxs-lookup"><span data-stu-id="56983-107">URI</span></span>

```
Connect-WSMan [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-Port <Int32>] [-SessionOption <SessionOption>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="56983-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="56983-108">DESCRIPTION</span></span>
<span data-ttu-id="56983-109">Cmdleten **Connect-WSMan** ansluter till WinRM-tjänsten på en fjärrdator och upprättar en permanent anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="56983-109">The **Connect-WSMan** cmdlet connects to the WinRM service on a remote computer, and it establishes a persistent connection to the remote computer.</span></span>
<span data-ttu-id="56983-110">Du kan använda denna cmdlet i kontexten för WSMan-providern för att ansluta till WinRM-tjänsten på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="56983-110">You can use this cmdlet in the context of the WSMan provider to connect to the WinRM service on a remote computer.</span></span>
<span data-ttu-id="56983-111">Du kan dock även använda denna cmdlet för att ansluta till WinRM-tjänsten på en fjärrdator innan du ändrar till WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="56983-111">However, you can also use this cmdlet to connect to the WinRM service on a remote computer before you change to the WSMan provider.</span></span>
<span data-ttu-id="56983-112">Den fjärranslutna datorn visas i rot katalogen för WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="56983-112">The remote computer appears in the root directory of the WSMan provider.</span></span>

<span data-ttu-id="56983-113">Explicita autentiseringsuppgifter krävs när klient-och serverdatorer finns i olika domäner eller arbets grupper.</span><span class="sxs-lookup"><span data-stu-id="56983-113">Explicit credentials are required when the client and server computers are in different domains or workgroups.</span></span>

<span data-ttu-id="56983-114">Information om hur du kopplar från tjänsten WinRM på en fjärrdator finns i Disconnect-WSMan-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="56983-114">For information about how to disconnect from the WinRM service on a remote computer, see the Disconnect-WSMan cmdlet.</span></span>

## <span data-ttu-id="56983-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="56983-115">EXAMPLES</span></span>

### <span data-ttu-id="56983-116">Exempel 1: Anslut till en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="56983-116">Example 1: Connect to a remote computer</span></span>

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

<span data-ttu-id="56983-117">Det här kommandot skapar en anslutning till den fjärranslutna Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="56983-117">This command creates a connection to the remote server01 computer.</span></span>

<span data-ttu-id="56983-118">Cmdleten **Connect-WSMan** används vanligt vis i kontexten för WSMan-providern för att ansluta till en fjärrdator, i det här fallet Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="56983-118">The **Connect-WSMan** cmdlet is generally used in the context of the WSMan provider to connect to a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="56983-119">Du kan dock använda cmdleten för att upprätta anslutningar till fjärrdatorer innan du byter till WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="56983-119">However, you can use the cmdlet to establish connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="56983-120">Dessa anslutningar visas i listan **dator namn** .</span><span class="sxs-lookup"><span data-stu-id="56983-120">Those connections appear in the **ComputerName** list.</span></span>

### <span data-ttu-id="56983-121">Exempel 2: Anslut till en fjärrdator med hjälp av administratörsautentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="56983-121">Example 2: Connect to a remote computer by using Administrator credentials</span></span>

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

<span data-ttu-id="56983-122">Det här kommandot skapar en anslutning till fjärrsystemet Server01 med hjälp av autentiseringsuppgifter för administratörs kontot.</span><span class="sxs-lookup"><span data-stu-id="56983-122">This command creates a connection to the remote system server01 using the Administrator account credentials.</span></span>

<span data-ttu-id="56983-123">Det första kommandot använder Get-Credential-cmdlet för att hämta autentiseringsuppgifter för administratören och lagrar dem i $cred-variabeln.</span><span class="sxs-lookup"><span data-stu-id="56983-123">The first command uses the Get-Credential cmdlet to get the Administrator credentials and then stores them in the $cred variable.</span></span>
<span data-ttu-id="56983-124">**Get-Credential** uppmanas att ange ett lösen ord för användar namn och lösen ord via en dialog ruta eller på kommando raden, beroende på systemets register inställningar.</span><span class="sxs-lookup"><span data-stu-id="56983-124">**Get-Credential** prompts you for a password of username and password through a dialog box or at the command line, depending on system registry settings.</span></span>

<span data-ttu-id="56983-125">Det andra kommandot använder parametern *Credential* för att skicka autentiseringsuppgifterna som lagras i $cred till **Connect-WSMan**.</span><span class="sxs-lookup"><span data-stu-id="56983-125">The second command uses the *Credential* parameter to pass the credentials stored in $cred to **Connect-WSMan**.</span></span>
<span data-ttu-id="56983-126">**Anslut-WSMan** ansluter sedan till Server01 för fjärrsystemet med hjälp av administratörs behörighet.</span><span class="sxs-lookup"><span data-stu-id="56983-126">**Connect-WSMan** then connects to the remote system server01 by using the Administrator credentials.</span></span>

### <span data-ttu-id="56983-127">Exempel 3: Anslut till en fjärran sluten dator över en angiven port</span><span class="sxs-lookup"><span data-stu-id="56983-127">Example 3: Connect to a remote computer over a specified port</span></span>

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

<span data-ttu-id="56983-128">Det här kommandot skapar en anslutning till fjärran Server01-datorn via port 80.</span><span class="sxs-lookup"><span data-stu-id="56983-128">This command creates a connection to the remote server01 computer over port 80.</span></span>

### <span data-ttu-id="56983-129">Exempel 4: Anslut till en fjärrdator med hjälp av anslutnings alternativ</span><span class="sxs-lookup"><span data-stu-id="56983-129">Example 4: Connect to a remote computer by using connection options</span></span>

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

<span data-ttu-id="56983-130">I det här exemplet skapas en anslutning till den fjärranslutna Server01-datorn med hjälp av anslutnings alternativen som definieras i kommandot **New-WSManSessionOption** .</span><span class="sxs-lookup"><span data-stu-id="56983-130">This example creates a connection to the remote server01 computer by using the connection options that are defined in the **New-WSManSessionOption** command.</span></span>

<span data-ttu-id="56983-131">Det första kommandot använder **New-WSManSessionOption** för att lagra en uppsättning anslutnings inställnings alternativ i variabeln $a.</span><span class="sxs-lookup"><span data-stu-id="56983-131">The first command uses **New-WSManSessionOption** to store a set of connection setting options in the $a variable.</span></span>
<span data-ttu-id="56983-132">I det här fallet har sessions alternativen en anslutnings tid på 30 sekunder (30 000 millisekunder).</span><span class="sxs-lookup"><span data-stu-id="56983-132">In this case, the session options set a connection time out of 30 seconds (30,000 milliseconds).</span></span>

<span data-ttu-id="56983-133">Det andra kommandot använder parametern *SessionOption* för att skicka de autentiseringsuppgifter som lagras i variabeln $a för att **ansluta-WSMan**.</span><span class="sxs-lookup"><span data-stu-id="56983-133">The second command uses the *SessionOption* parameter to pass the credentials that are stored in the $a variable to **Connect-WSMan**.</span></span>
<span data-ttu-id="56983-134">Sedan ansluter **-WSMan** till den fjärranslutna Server01-datorn med hjälp av de angivna session alternativen.</span><span class="sxs-lookup"><span data-stu-id="56983-134">Then, **Connect-WSMan** connects to the remote server01 computer by using the specified session options.</span></span>

## <span data-ttu-id="56983-135">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="56983-135">PARAMETERS</span></span>

### <span data-ttu-id="56983-136">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="56983-136">-ApplicationName</span></span>
<span data-ttu-id="56983-137">Anger program namnet i anslutningen.</span><span class="sxs-lookup"><span data-stu-id="56983-137">Specifies the application name in the connection.</span></span>
<span data-ttu-id="56983-138">Standardvärdet för parametern *ApplicationName* är WSMan.</span><span class="sxs-lookup"><span data-stu-id="56983-138">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="56983-139">Den fullständiga identifieraren för Fjärrslutpunkten har följande format:</span><span class="sxs-lookup"><span data-stu-id="56983-139">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="56983-140">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="56983-140">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="56983-141">Exempel: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="56983-141">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="56983-142">Internet Information Services (IIS), som är värd för sessionen, vidarebefordrar begär Anden med den här slut punkten till det angivna programmet.</span><span class="sxs-lookup"><span data-stu-id="56983-142">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="56983-143">Den här standardinställningen för WSMAN är lämplig för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="56983-143">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="56983-144">Den här parametern är avsedd att användas om många datorer upprättar fjärr anslutningar till en dator som kör PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56983-144">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="56983-145">I det här fallet är IIS värd för webb tjänster för hantering (WS-Management) för effektivitet.</span><span class="sxs-lookup"><span data-stu-id="56983-145">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="56983-146">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="56983-146">-Authentication</span></span>
<span data-ttu-id="56983-147">Anger vilken autentiseringsmekanism som ska användas på servern.</span><span class="sxs-lookup"><span data-stu-id="56983-147">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="56983-148">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="56983-148">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="56983-149">Frö.</span><span class="sxs-lookup"><span data-stu-id="56983-149">Basic.</span></span>
<span data-ttu-id="56983-150">Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.</span><span class="sxs-lookup"><span data-stu-id="56983-150">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="56983-151">Standard.</span><span class="sxs-lookup"><span data-stu-id="56983-151">Default.</span></span>
<span data-ttu-id="56983-152">Använd autentiseringsmetoden som implementeras av WS-Management-protokollet.</span><span class="sxs-lookup"><span data-stu-id="56983-152">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="56983-153">Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="56983-153">This is the default.</span></span>
- <span data-ttu-id="56983-154">Nedbrytning.</span><span class="sxs-lookup"><span data-stu-id="56983-154">Digest.</span></span>
<span data-ttu-id="56983-155">Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.</span><span class="sxs-lookup"><span data-stu-id="56983-155">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="56983-156">Paket.</span><span class="sxs-lookup"><span data-stu-id="56983-156">Kerberos.</span></span>
<span data-ttu-id="56983-157">Klient datorn och servern autentiseras ömsesidigt med hjälp av Kerberos-certifikat.</span><span class="sxs-lookup"><span data-stu-id="56983-157">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="56983-158">Fram.</span><span class="sxs-lookup"><span data-stu-id="56983-158">Negotiate.</span></span>
<span data-ttu-id="56983-159">Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="56983-159">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="56983-160">Detta parameter värde kan till exempel användas för förhandling för att avgöra om Kerberos-protokollet eller NTLM används.</span><span class="sxs-lookup"><span data-stu-id="56983-160">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="56983-161">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="56983-161">CredSSP.</span></span>
<span data-ttu-id="56983-162">Använd CredSSP-autentisering (Credential Security Support Provider), vilket gör att användaren kan delegera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="56983-162">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="56983-163">Det här alternativet är utformat för kommandon som körs på en fjärrdator men samlar in data från eller kör ytterligare kommandon på andra fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="56983-163">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="56983-164">Varning! CredSSP delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="56983-164">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="56983-165">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="56983-165">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="56983-166">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="56983-166">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="56983-167">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="56983-167">-CertificateThumbprint</span></span>
<span data-ttu-id="56983-168">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="56983-168">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="56983-169">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="56983-169">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="56983-170">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="56983-170">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="56983-171">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="56983-171">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="56983-172">Om du vill hämta ett tumavtryck för certifikatet använder du kommandot Get-Item eller Get-ChildItem i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="56983-172">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="56983-173">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="56983-173">-ComputerName</span></span>
<span data-ttu-id="56983-174">Anger den dator som hanterings åtgärden ska köras mot.</span><span class="sxs-lookup"><span data-stu-id="56983-174">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="56983-175">Värdet kan vara ett fullständigt kvalificerat domän namn, ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="56983-175">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="56983-176">Använd namnet på den lokala datorn, Använd localhost eller Använd en punkt (.) för att ange den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="56983-176">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="56983-177">Den lokala datorn är standard.</span><span class="sxs-lookup"><span data-stu-id="56983-177">The local computer is the default.</span></span>
<span data-ttu-id="56983-178">Om fjärrdatorn finns i en annan domän än användaren måste du använda ett fullständigt kvalificerat domän namn.</span><span class="sxs-lookup"><span data-stu-id="56983-178">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="56983-179">Du kan skicka ett värde för den här parametern till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="56983-179">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="56983-180">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="56983-180">-ConnectionURI</span></span>
<span data-ttu-id="56983-181">Anger anslutnings slut punkten.</span><span class="sxs-lookup"><span data-stu-id="56983-181">Specifies the connection endpoint.</span></span>
<span data-ttu-id="56983-182">Formatet för den här strängen är följande:</span><span class="sxs-lookup"><span data-stu-id="56983-182">The format of this string is as follows:</span></span>

<span data-ttu-id="56983-183">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="56983-183">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="56983-184">Följande sträng är ett korrekt formaterat värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="56983-184">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="56983-185">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="56983-185">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="56983-186">-Credential</span><span class="sxs-lookup"><span data-stu-id="56983-186">-Credential</span></span>
<span data-ttu-id="56983-187">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="56983-187">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="56983-188">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="56983-188">The default is the current user.</span></span>
<span data-ttu-id="56983-189">Ange ett användar namn, till exempel user01, Domain01\User01 eller User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="56983-189">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="56983-190">Eller ange ett **PSCredential** -objekt, till exempel ett som returneras av Get-Credential-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="56983-190">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="56983-191">När du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="56983-191">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="56983-192">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="56983-192">-OptionSet</span></span>
<span data-ttu-id="56983-193">Anger en uppsättning växlar till en tjänst för att ändra eller förfina begärans typ.</span><span class="sxs-lookup"><span data-stu-id="56983-193">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="56983-194">Dessa liknar växlar som används i kommando rads gränssnitt eftersom de är specifika för specifika tjänster.</span><span class="sxs-lookup"><span data-stu-id="56983-194">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="56983-195">Valfritt antal alternativ kan anges.</span><span class="sxs-lookup"><span data-stu-id="56983-195">Any number of options can be specified.</span></span>

<span data-ttu-id="56983-196">I följande exempel visas syntaxen som skickar värdena 1, 2 och 3 för parametrarna a, b och c:</span><span class="sxs-lookup"><span data-stu-id="56983-196">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="56983-197">-Port</span><span class="sxs-lookup"><span data-stu-id="56983-197">-Port</span></span>
<span data-ttu-id="56983-198">Anger vilken port som ska användas när klienten ansluter till WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="56983-198">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="56983-199">När transporten är HTTP är standard porten 80.</span><span class="sxs-lookup"><span data-stu-id="56983-199">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="56983-200">När transporten är HTTPS är standard porten 443.</span><span class="sxs-lookup"><span data-stu-id="56983-200">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="56983-201">När du använder HTTPS som transport måste värdet för parametern *computername* matcha serverns certifikats eget namn (CN).</span><span class="sxs-lookup"><span data-stu-id="56983-201">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="56983-202">Men om parametern *SkipCNCheck* anges som en del av parametern *SessionOption* , behöver inte Certifikatets gemensamma namn matcha serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="56983-202">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="56983-203">Parametern *SkipCNCheck* ska endast användas för betrodda datorer.</span><span class="sxs-lookup"><span data-stu-id="56983-203">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="56983-204">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="56983-204">-SessionOption</span></span>
<span data-ttu-id="56983-205">Anger utökade alternativ för WS-Management-sessionen.</span><span class="sxs-lookup"><span data-stu-id="56983-205">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="56983-206">Ange ett **SessionOption** -objekt som du skapar med hjälp av New-WSManSessionOption-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="56983-206">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="56983-207">Om du vill ha mer information om vilka alternativ som är tillgängliga skriver du `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="56983-207">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="56983-208">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="56983-208">-UseSSL</span></span>
<span data-ttu-id="56983-209">Anger att Secure Sockets Layer-protokollet (SSL) används för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="56983-209">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="56983-210">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="56983-210">By default, SSL is not used.</span></span>

<span data-ttu-id="56983-211">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="56983-211">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="56983-212">Med parametern *UseSSL* kan du ange ytterligare skydd av https i stället för http.</span><span class="sxs-lookup"><span data-stu-id="56983-212">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="56983-213">Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="56983-213">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="56983-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="56983-214">CommonParameters</span></span>
<span data-ttu-id="56983-215">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="56983-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="56983-216">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="56983-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="56983-217">INDATA</span><span class="sxs-lookup"><span data-stu-id="56983-217">INPUTS</span></span>

### <span data-ttu-id="56983-218">Inga</span><span class="sxs-lookup"><span data-stu-id="56983-218">None</span></span>
<span data-ttu-id="56983-219">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="56983-219">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="56983-220">UTDATA</span><span class="sxs-lookup"><span data-stu-id="56983-220">OUTPUTS</span></span>

### <span data-ttu-id="56983-221">Inga</span><span class="sxs-lookup"><span data-stu-id="56983-221">None</span></span>
<span data-ttu-id="56983-222">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="56983-222">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="56983-223">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="56983-223">NOTES</span></span>

* <span data-ttu-id="56983-224">Du kan köra hanterings kommandon eller fråga hanterings data på en fjärrdator utan att skapa en WS-Management session.</span><span class="sxs-lookup"><span data-stu-id="56983-224">You can run management commands or query management data on a remote computer without creating a WS-Management session.</span></span> <span data-ttu-id="56983-225">Du kan göra detta med hjälp av *computername* -parametrarna för Invoke-WSManAction och get-WSManInstance.</span><span class="sxs-lookup"><span data-stu-id="56983-225">You can do this by using the *ComputerName* parameters of Invoke-WSManAction and Get-WSManInstance.</span></span> <span data-ttu-id="56983-226">När du använder parametern *computername* skapar PowerShell en tillfällig anslutning som används för det enskilda kommandot.</span><span class="sxs-lookup"><span data-stu-id="56983-226">When you use the *ComputerName* parameter, PowerShell creates a temporary connection that is used for the single command.</span></span> <span data-ttu-id="56983-227">När kommandot har körts stängs anslutningen.</span><span class="sxs-lookup"><span data-stu-id="56983-227">After the command runs, the connection is closed.</span></span>

*

## <span data-ttu-id="56983-228">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="56983-228">RELATED LINKS</span></span>

[<span data-ttu-id="56983-229">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="56983-229">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="56983-230">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="56983-230">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="56983-231">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="56983-231">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="56983-232">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="56983-232">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="56983-233">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="56983-233">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="56983-234">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="56983-234">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="56983-235">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="56983-235">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="56983-236">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="56983-236">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="56983-237">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="56983-237">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="56983-238">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="56983-238">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="56983-239">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="56983-239">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="56983-240">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="56983-240">Test-WSMan</span></span>](Test-WSMan.md)

