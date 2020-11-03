---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/invoke-wsmanaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WSManAction
ms.openlocfilehash: 1eeeb912ab32ec5334959daba1e352f20fec15b1
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273123"
---
# <span data-ttu-id="4a0be-103">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="4a0be-103">Invoke-WSManAction</span></span>

## <span data-ttu-id="4a0be-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4a0be-104">SYNOPSIS</span></span>
<span data-ttu-id="4a0be-105">Anropar en åtgärd för objektet som anges av resurs-URI och av väljare.</span><span class="sxs-lookup"><span data-stu-id="4a0be-105">Invokes an action on the object that is specified by the Resource URI and by the selectors.</span></span>

## <span data-ttu-id="4a0be-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4a0be-106">SYNTAX</span></span>

### <span data-ttu-id="4a0be-107">URI (standard)</span><span class="sxs-lookup"><span data-stu-id="4a0be-107">URI (Default)</span></span>

```
Invoke-WSManAction [-Action] <String> [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>]
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-ValueSet <Hashtable>] [-ResourceURI] <Uri>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="4a0be-108">ComputerName</span><span class="sxs-lookup"><span data-stu-id="4a0be-108">ComputerName</span></span>

```
Invoke-WSManAction [-Action] <String> [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-UseSSL] [-ValueSet <Hashtable>] [-ResourceURI] <Uri> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="4a0be-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4a0be-109">DESCRIPTION</span></span>

<span data-ttu-id="4a0be-110">Invoke-WSManAction kör en åtgärd på objektet som anges av RESOURCE_URI, där parametrar anges med nyckel värdes par.</span><span class="sxs-lookup"><span data-stu-id="4a0be-110">The Invoke-WSManAction runs an action on the object that is specified by RESOURCE_URI, where parameters are specified by key value pairs.</span></span>

<span data-ttu-id="4a0be-111">Denna cmdlet använder WSMan-anslutningen/transport lagret för att köra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="4a0be-111">This cmdlet uses the WSMan connection/transport layer to run the action.</span></span>

## <span data-ttu-id="4a0be-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4a0be-112">EXAMPLES</span></span>

### <span data-ttu-id="4a0be-113">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="4a0be-113">Example 1</span></span>

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="4a0be-114">Det här kommandot anropar metoden start service för den Win32_Service WMI-klassdrivrutinen som motsvarar Spooler-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4a0be-114">This command calls the StartService method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>

<span data-ttu-id="4a0be-115">Returvärdet indikerar om åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="4a0be-115">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="4a0be-116">I det här fallet indikerar ett retur värde 0 att det är klart.</span><span class="sxs-lookup"><span data-stu-id="4a0be-116">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="4a0be-117">Ett retur värde på 5 anger att tjänsten redan har startats.</span><span class="sxs-lookup"><span data-stu-id="4a0be-117">A return value of 5 indicates that the service is already started.</span></span>

### <span data-ttu-id="4a0be-118">Exempel 2</span><span class="sxs-lookup"><span data-stu-id="4a0be-118">Example 2</span></span>

```powershell
Invoke-WSManAction -Action stopservice -ResourceURI wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:input.xml -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="4a0be-119">Det här kommandot anropar metoden Stop service i Spooler-tjänsten genom att använda indata från en fil.</span><span class="sxs-lookup"><span data-stu-id="4a0be-119">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="4a0be-120">Filen Input.xml innehåller följande innehåll:</span><span class="sxs-lookup"><span data-stu-id="4a0be-120">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

<span data-ttu-id="4a0be-121">Returvärdet indikerar om åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="4a0be-121">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="4a0be-122">I det här fallet indikerar ett retur värde 0 att det är klart.</span><span class="sxs-lookup"><span data-stu-id="4a0be-122">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="4a0be-123">Ett retur värde på 5 anger att tjänsten redan har startats.</span><span class="sxs-lookup"><span data-stu-id="4a0be-123">A return value of 5 indicates that the service is already started.</span></span>

### <span data-ttu-id="4a0be-124">Exempel 3</span><span class="sxs-lookup"><span data-stu-id="4a0be-124">Example 3</span></span>

```powershell
Invoke-WSManAction -Action create -ResourceURI wmicimv2/win32_process -ValueSet @{commandline="notepad.exe";currentdirectory="C:\"}
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Process
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ProcessId   : 6356
ReturnValue : 0
```

<span data-ttu-id="4a0be-125">Det här kommandot anropar Create-metoden för klassen Win32_Process.</span><span class="sxs-lookup"><span data-stu-id="4a0be-125">This command calls the Create method of the Win32_Process class.</span></span>
<span data-ttu-id="4a0be-126">Metoden överför metoden två parameter värden, Notepad.exe och "C: \" .</span><span class="sxs-lookup"><span data-stu-id="4a0be-126">It passes the method two parameter values, Notepad.exe and "C:\".</span></span>
<span data-ttu-id="4a0be-127">Därför skapas en ny process för att köra anteckningar och den aktuella katalogen för den nya processen anges till "C: \" .</span><span class="sxs-lookup"><span data-stu-id="4a0be-127">As a result, a new process is created to run Notepad, and the current directory of the new process is set to "C:\".</span></span>

### <span data-ttu-id="4a0be-128">Exempel 4</span><span class="sxs-lookup"><span data-stu-id="4a0be-128">Example 4</span></span>

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -ComputerName server01 -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="4a0be-129">Det här kommandot anropar metoden start service för den Win32_Service WMI-klassdrivrutinen som motsvarar Spooler-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4a0be-129">This command calls the StartService method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>
<span data-ttu-id="4a0be-130">Eftersom parametern ComputerName anges körs kommandot mot den fjärranslutna Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="4a0be-130">Because the ComputerName parameter is specified, the command runs against the remote server01 computer.</span></span>

<span data-ttu-id="4a0be-131">Returvärdet indikerar om åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="4a0be-131">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="4a0be-132">I det här fallet indikerar ett retur värde 0 att det är klart.</span><span class="sxs-lookup"><span data-stu-id="4a0be-132">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="4a0be-133">Ett retur värde på 5 anger att tjänsten redan har startats.</span><span class="sxs-lookup"><span data-stu-id="4a0be-133">A return value of 5 indicates that the service is already started.</span></span>

## <span data-ttu-id="4a0be-134">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4a0be-134">PARAMETERS</span></span>

### <span data-ttu-id="4a0be-135">-Åtgärd</span><span class="sxs-lookup"><span data-stu-id="4a0be-135">-Action</span></span>

<span data-ttu-id="4a0be-136">Anger den metod som ska köras på det Management-objekt som anges av ResourceURI och väljare.</span><span class="sxs-lookup"><span data-stu-id="4a0be-136">Specifies the method to run on the management object specified by the ResourceURI and selectors.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a0be-137">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="4a0be-137">-ApplicationName</span></span>

<span data-ttu-id="4a0be-138">Anger program namnet i anslutningen.</span><span class="sxs-lookup"><span data-stu-id="4a0be-138">Specifies the application name in the connection.</span></span>
<span data-ttu-id="4a0be-139">Standardvärdet för parametern ApplicationName är WSMAN.</span><span class="sxs-lookup"><span data-stu-id="4a0be-139">The default value of the ApplicationName parameter is WSMAN.</span></span>
<span data-ttu-id="4a0be-140">Den fullständiga identifieraren för Fjärrslutpunkten har följande format:</span><span class="sxs-lookup"><span data-stu-id="4a0be-140">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="4a0be-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="4a0be-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="4a0be-142">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="4a0be-142">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="4a0be-143">Internet Information Services (IIS), som är värd för sessionen, vidarebefordrar begär Anden med den här slut punkten till det angivna programmet.</span><span class="sxs-lookup"><span data-stu-id="4a0be-143">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="4a0be-144">Den här standardinställningen för "WSMAN" är lämplig för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="4a0be-144">This default setting of "WSMAN" is appropriate for most uses.</span></span>
<span data-ttu-id="4a0be-145">Den här parametern är avsedd att användas när flera datorer upprättar fjärr anslutningar till en dator som kör Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a0be-145">This parameter is designed to be used when numerous computers establish remote connections to one computer running Windows PowerShell.</span></span>
<span data-ttu-id="4a0be-146">I det här fallet är IIS värd för webb tjänster för hantering (WS-Management) för effektivitet.</span><span class="sxs-lookup"><span data-stu-id="4a0be-146">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="4a0be-147">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="4a0be-147">-Authentication</span></span>

<span data-ttu-id="4a0be-148">Anger vilken autentiseringsmekanism som ska användas på servern.</span><span class="sxs-lookup"><span data-stu-id="4a0be-148">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="4a0be-149">Möjliga värden:</span><span class="sxs-lookup"><span data-stu-id="4a0be-149">Possible values are:</span></span>

- <span data-ttu-id="4a0be-150">Basic: Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.</span><span class="sxs-lookup"><span data-stu-id="4a0be-150">Basic: Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="4a0be-151">Standard: Använd autentiseringsmetoden som implementeras av WS-Management-protokollet.</span><span class="sxs-lookup"><span data-stu-id="4a0be-151">Default : Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="4a0be-152">Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="4a0be-152">This is the default.</span></span>
- <span data-ttu-id="4a0be-153">Digest: Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.</span><span class="sxs-lookup"><span data-stu-id="4a0be-153">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="4a0be-154">Kerberos: klient datorn och servern autentiseras ömsesidigt med hjälp av Kerberos-certifikat.</span><span class="sxs-lookup"><span data-stu-id="4a0be-154">Kerberos: The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="4a0be-155">Förhandla: Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="4a0be-155">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="4a0be-156">Detta parameter värde tillåter till exempel förhandling för att avgöra om Kerberos-protokollet eller NTLM används.</span><span class="sxs-lookup"><span data-stu-id="4a0be-156">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="4a0be-157">CredSSP: Använd CredSSP-autentisering (Credential Security Support Provider), vilket gör att användaren kan delegera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="4a0be-157">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="4a0be-158">Det här alternativet är utformat för kommandon som körs på en fjärrdator men samlar in data från eller kör ytterligare kommandon på andra fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="4a0be-158">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="4a0be-159">Varning! CredSSP delegerar användarens autentiseringsuppgifter från den lokala datorn till en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="4a0be-159">Caution: CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="4a0be-160">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="4a0be-160">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="4a0be-161">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="4a0be-161">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="4a0be-162">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="4a0be-162">-CertificateThumbprint</span></span>

<span data-ttu-id="4a0be-163">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="4a0be-163">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="4a0be-164">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="4a0be-164">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="4a0be-165">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="4a0be-165">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="4a0be-166">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="4a0be-166">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="4a0be-167">Om du vill hämta ett tumavtryck för certifikatet använder du kommandot Get-Item eller Get-ChildItem i Windows PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="4a0be-167">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the Windows PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="4a0be-168">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="4a0be-168">-ComputerName</span></span>

<span data-ttu-id="4a0be-169">Anger den dator som du vill köra hanterings åtgärden mot.</span><span class="sxs-lookup"><span data-stu-id="4a0be-169">Specifies the computer against which you want to run the management operation.</span></span>
<span data-ttu-id="4a0be-170">Värdet kan vara ett fullständigt kvalificerat domän namn, ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="4a0be-170">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="4a0be-171">Använd namnet på den lokala datorn, Använd localhost eller Använd en punkt (.) för att ange den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="4a0be-171">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="4a0be-172">Den lokala datorn är standard.</span><span class="sxs-lookup"><span data-stu-id="4a0be-172">The local computer is the default.</span></span>
<span data-ttu-id="4a0be-173">Om fjärrdatorn finns i en annan domän än användaren måste du använda ett fullständigt kvalificerat domän namn.</span><span class="sxs-lookup"><span data-stu-id="4a0be-173">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="4a0be-174">Du kan skicka ett värde för den här parametern till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="4a0be-174">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="4a0be-175">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="4a0be-175">-ConnectionURI</span></span>

<span data-ttu-id="4a0be-176">Anger anslutnings slut punkten.</span><span class="sxs-lookup"><span data-stu-id="4a0be-176">Specifies the connection endpoint.</span></span>
<span data-ttu-id="4a0be-177">Formatet för den här strängen är:</span><span class="sxs-lookup"><span data-stu-id="4a0be-177">The format of this string is:</span></span>

<span data-ttu-id="4a0be-178">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="4a0be-178">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="4a0be-179">Följande sträng är ett korrekt formaterat värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="4a0be-179">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="4a0be-180">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="4a0be-180">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="4a0be-181">-Credential</span><span class="sxs-lookup"><span data-stu-id="4a0be-181">-Credential</span></span>

<span data-ttu-id="4a0be-182">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="4a0be-182">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="4a0be-183">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="4a0be-183">The default is the current user.</span></span>
<span data-ttu-id="4a0be-184">Ange ett användar namn, till exempel "user01", "Domain01\User01" eller User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="4a0be-184">Type a user name, such as "User01", "Domain01\User01", or User@Domain.com.</span></span>
<span data-ttu-id="4a0be-185">Eller ange ett PSCredential-objekt, till exempel ett som returneras av Get-Credential-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4a0be-185">Or, enter a PSCredential object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="4a0be-186">När du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="4a0be-186">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="4a0be-187">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="4a0be-187">-FilePath</span></span>

<span data-ttu-id="4a0be-188">Anger sökvägen till en fil som används för att uppdatera en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="4a0be-188">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="4a0be-189">Du anger hanterings resursen med hjälp av parametern ResourceURI och parametern SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="4a0be-189">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter.</span></span>
<span data-ttu-id="4a0be-190">Följande kommando använder till exempel parametern sökväg:</span><span class="sxs-lookup"><span data-stu-id="4a0be-190">For example, the following command uses the FilePath parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath c:\input.xml -Authentication default`

<span data-ttu-id="4a0be-191">Det här kommandot anropar metoden Stop service i Spooler-tjänsten genom att använda indata från en fil.</span><span class="sxs-lookup"><span data-stu-id="4a0be-191">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="4a0be-192">Filen Input.xml innehåller följande innehåll:</span><span class="sxs-lookup"><span data-stu-id="4a0be-192">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

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

### <span data-ttu-id="4a0be-193">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="4a0be-193">-OptionSet</span></span>

<span data-ttu-id="4a0be-194">Skickar en uppsättning växlar till en tjänst för att ändra eller förfina begärans natur.</span><span class="sxs-lookup"><span data-stu-id="4a0be-194">Passes a set of switches  to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="4a0be-195">Dessa liknar växlar som används i kommando rads gränssnitt eftersom de är specifika för specifika tjänster.</span><span class="sxs-lookup"><span data-stu-id="4a0be-195">These are similar to switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="4a0be-196">Valfritt antal alternativ kan anges.</span><span class="sxs-lookup"><span data-stu-id="4a0be-196">Any number of options  can be specified.</span></span>

<span data-ttu-id="4a0be-197">I följande exempel visas syntaxen som skickar värdena 1, 2 och 3 för parametrarna a, b och c:</span><span class="sxs-lookup"><span data-stu-id="4a0be-197">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4a0be-198">-Port</span><span class="sxs-lookup"><span data-stu-id="4a0be-198">-Port</span></span>

<span data-ttu-id="4a0be-199">Anger vilken port som ska användas när klienten ansluter till WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4a0be-199">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="4a0be-200">När transporten är HTTP är standard porten 80.</span><span class="sxs-lookup"><span data-stu-id="4a0be-200">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="4a0be-201">När transporten är HTTPS är standard porten 443.</span><span class="sxs-lookup"><span data-stu-id="4a0be-201">When the transport is HTTPS, the default port is 443.</span></span>
<span data-ttu-id="4a0be-202">När du använder HTTPS som transport måste värdet för parametern ComputerName matcha serverns certifikats eget namn (CN).</span><span class="sxs-lookup"><span data-stu-id="4a0be-202">When you use HTTPS as the transport, the value of the ComputerName parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="4a0be-203">Men om parametern SkipCNCheck anges som en del av parametern SessionOption, behöver inte Certifikatets gemensamma namn matcha serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="4a0be-203">However, if the SkipCNCheck parameter is specified as part of the SessionOption parameter, then the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="4a0be-204">Parametern SkipCNCheck ska endast användas för betrodda datorer.</span><span class="sxs-lookup"><span data-stu-id="4a0be-204">The SkipCNCheck parameter should be used only for trusted machines.</span></span>

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

### <span data-ttu-id="4a0be-205">– ResourceURI</span><span class="sxs-lookup"><span data-stu-id="4a0be-205">-ResourceURI</span></span>

<span data-ttu-id="4a0be-206">Innehåller Uniform Resource Identifier (URI) för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="4a0be-206">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="4a0be-207">URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="4a0be-207">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="4a0be-208">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="4a0be-208">A URI consists of a prefix and a path to a resource.</span></span>
<span data-ttu-id="4a0be-209">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="4a0be-209">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4a0be-210">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="4a0be-210">-SelectorSet</span></span>

<span data-ttu-id="4a0be-211">Anger en uppsättning värdepar som används för att välja specifika hanterings resurs instanser.</span><span class="sxs-lookup"><span data-stu-id="4a0be-211">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="4a0be-212">*SelectorSet* används när det finns mer än en instans av resursen.</span><span class="sxs-lookup"><span data-stu-id="4a0be-212">*SelectorSet* is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="4a0be-213">Värdet för *SelectorSet* måste vara en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="4a0be-213">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="4a0be-214">I följande exempel visas hur du anger ett värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="4a0be-214">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4a0be-215">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="4a0be-215">-SessionOption</span></span>

<span data-ttu-id="4a0be-216">Definierar en uppsättning utökade alternativ för WS-Management-sessionen.</span><span class="sxs-lookup"><span data-stu-id="4a0be-216">Defines a set of extended options for the WS-Management session.</span></span>
<span data-ttu-id="4a0be-217">Ange ett SessionOption-objekt som du skapar med hjälp av New-WSManSessionOption-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4a0be-217">Enter a SessionOption object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="4a0be-218">Mer information om tillgängliga alternativ finns i New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="4a0be-218">For more information about the options that are available, see New-WSManSessionOption.</span></span>

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

### <span data-ttu-id="4a0be-219">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="4a0be-219">-UseSSL</span></span>

<span data-ttu-id="4a0be-220">Anger att Secure Sockets Layer-protokollet (SSL) används för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="4a0be-220">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="4a0be-221">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="4a0be-221">By default, SSL is not used.</span></span>

<span data-ttu-id="4a0be-222">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="4a0be-222">WS-Management encrypts all the PowerShell content  that is transmitted over the network.</span></span>
<span data-ttu-id="4a0be-223">Med parametern UseSSL kan du ange ytterligare skydd av HTTPS i stället för HTTP.</span><span class="sxs-lookup"><span data-stu-id="4a0be-223">The UseSSL parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="4a0be-224">Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="4a0be-224">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="4a0be-225">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="4a0be-225">-ValueSet</span></span>

<span data-ttu-id="4a0be-226">Anger en hash-tabell som hjälper dig att ändra en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="4a0be-226">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="4a0be-227">Du anger hanterings resursen med parametrarna ResourceURI och SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="4a0be-227">You specify the management resource using the ResourceURI and SelectorSet parameters.</span></span>
<span data-ttu-id="4a0be-228">Värdet för parametern ValueSet måste vara en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="4a0be-228">The value of the ValueSet parameter must be a hash table.</span></span>

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

### <span data-ttu-id="4a0be-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4a0be-229">CommonParameters</span></span>

<span data-ttu-id="4a0be-230">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4a0be-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4a0be-231">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4a0be-231">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4a0be-232">INDATA</span><span class="sxs-lookup"><span data-stu-id="4a0be-232">INPUTS</span></span>

### <span data-ttu-id="4a0be-233">Inget</span><span class="sxs-lookup"><span data-stu-id="4a0be-233">None</span></span>

<span data-ttu-id="4a0be-234">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="4a0be-234">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="4a0be-235">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4a0be-235">OUTPUTS</span></span>

### <span data-ttu-id="4a0be-236">Inget</span><span class="sxs-lookup"><span data-stu-id="4a0be-236">None</span></span>

<span data-ttu-id="4a0be-237">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="4a0be-237">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="4a0be-238">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4a0be-238">NOTES</span></span>

## <span data-ttu-id="4a0be-239">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4a0be-239">RELATED LINKS</span></span>

[<span data-ttu-id="4a0be-240">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="4a0be-240">Invoke-WmiMethod</span></span>](../Microsoft.PowerShell.Management/Invoke-WmiMethod.md)

[<span data-ttu-id="4a0be-241">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="4a0be-241">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="4a0be-242">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="4a0be-242">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="4a0be-243">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="4a0be-243">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="4a0be-244">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="4a0be-244">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="4a0be-245">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="4a0be-245">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="4a0be-246">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="4a0be-246">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="4a0be-247">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="4a0be-247">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="4a0be-248">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="4a0be-248">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="4a0be-249">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="4a0be-249">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="4a0be-250">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="4a0be-250">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="4a0be-251">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="4a0be-251">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="4a0be-252">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="4a0be-252">Test-WSMan</span></span>](Test-WSMan.md)
