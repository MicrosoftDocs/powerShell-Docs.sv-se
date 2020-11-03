---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/invoke-wsmanaction?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WSManAction
ms.openlocfilehash: 112b4a1e0a790c32b6a3ea2011fbc72ec86a0324
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268574"
---
# <span data-ttu-id="8a39b-103">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="8a39b-103">Invoke-WSManAction</span></span>

## <span data-ttu-id="8a39b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8a39b-104">SYNOPSIS</span></span>
<span data-ttu-id="8a39b-105">Anropar en åtgärd för objektet som anges av resurs-URI och av väljare.</span><span class="sxs-lookup"><span data-stu-id="8a39b-105">Invokes an action on the object that is specified by the Resource URI and by the selectors.</span></span>

## <span data-ttu-id="8a39b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8a39b-106">SYNTAX</span></span>

### <span data-ttu-id="8a39b-107">URI (standard)</span><span class="sxs-lookup"><span data-stu-id="8a39b-107">URI (Default)</span></span>

```
Invoke-WSManAction [-Action] <String> [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>]
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-ValueSet <Hashtable>] [-ResourceURI] <Uri>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="8a39b-108">ComputerName</span><span class="sxs-lookup"><span data-stu-id="8a39b-108">ComputerName</span></span>

```
Invoke-WSManAction [-Action] <String> [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-UseSSL] [-ValueSet <Hashtable>] [-ResourceURI] <Uri> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="8a39b-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8a39b-109">DESCRIPTION</span></span>
<span data-ttu-id="8a39b-110">**Invoke-WSManAction** kör en åtgärd på objektet som anges av RESOURCE_URI, där parametrar anges av nyckel värdes par.</span><span class="sxs-lookup"><span data-stu-id="8a39b-110">The **Invoke-WSManAction** runs an action on the object that is specified by RESOURCE_URI, where parameters are specified by key value pairs.</span></span>

<span data-ttu-id="8a39b-111">Denna cmdlet använder WSMan-anslutningen/transport lagret för att köra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="8a39b-111">This cmdlet uses the WSMan connection/transport layer to run the action.</span></span>

## <span data-ttu-id="8a39b-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8a39b-112">EXAMPLES</span></span>

### <span data-ttu-id="8a39b-113">Exempel 1: anropa en metod</span><span class="sxs-lookup"><span data-stu-id="8a39b-113">Example 1: Invoke a method</span></span>

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

<span data-ttu-id="8a39b-114">Det här kommandot anropar metoden Start **service** för den Win32_Service WMI-klassdrivrutinen som motsvarar Spooler-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="8a39b-114">This command calls the **StartService** method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>

<span data-ttu-id="8a39b-115">Returvärdet indikerar om åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="8a39b-115">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="8a39b-116">I det här fallet indikerar ett retur värde 0 att det är klart.</span><span class="sxs-lookup"><span data-stu-id="8a39b-116">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="8a39b-117">Ett retur värde på 5 anger att tjänsten redan har startats.</span><span class="sxs-lookup"><span data-stu-id="8a39b-117">A return value of 5 indicates that the service is already started.</span></span>

### <span data-ttu-id="8a39b-118">Exempel 2: anropa en metod</span><span class="sxs-lookup"><span data-stu-id="8a39b-118">Example 2: Invoke a method</span></span>

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

<span data-ttu-id="8a39b-119">Det här kommandot anropar metoden **Stop** service i Spooler-tjänsten genom att använda indata från en fil.</span><span class="sxs-lookup"><span data-stu-id="8a39b-119">This command calls the **StopService** method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="8a39b-120">Filen Input.xml innehåller följande innehåll:</span><span class="sxs-lookup"><span data-stu-id="8a39b-120">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

### <span data-ttu-id="8a39b-121">Exempel 3: anropa en metod med angivna parameter värden</span><span class="sxs-lookup"><span data-stu-id="8a39b-121">Example 3: Invoke a method with specified parameter values</span></span>

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

<span data-ttu-id="8a39b-122">Det här kommandot anropar **create** -metoden för klassen Win32_Process.</span><span class="sxs-lookup"><span data-stu-id="8a39b-122">This command calls the **Create** method of the Win32_Process class.</span></span>
<span data-ttu-id="8a39b-123">Metoden överför metoden två parameter värden, Notepad.exe och C:\.</span><span class="sxs-lookup"><span data-stu-id="8a39b-123">It passes the method two parameter values, Notepad.exe and C:\.</span></span>
<span data-ttu-id="8a39b-124">Därför skapas en ny process för att köra anteckningar och den aktuella katalogen för den nya processen anges till C:\.</span><span class="sxs-lookup"><span data-stu-id="8a39b-124">As a result, a new process is created to run Notepad, and the current directory of the new process is set to C:\.</span></span>

### <span data-ttu-id="8a39b-125">Exempel 4: anropa en metod på en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="8a39b-125">Example 4: Invoke a method on a remote computer</span></span>

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

<span data-ttu-id="8a39b-126">Det här kommandot anropar metoden Start **service** för den Win32_Service WMI-klassdrivrutinen som motsvarar Spooler-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="8a39b-126">This command calls the **StartService** method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>
<span data-ttu-id="8a39b-127">Eftersom parametern *computername* anges körs kommandot mot den fjärranslutna Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="8a39b-127">Because the *ComputerName* parameter is specified, the command runs against the remote server01 computer.</span></span>

## <span data-ttu-id="8a39b-128">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8a39b-128">PARAMETERS</span></span>

### <span data-ttu-id="8a39b-129">-Åtgärd</span><span class="sxs-lookup"><span data-stu-id="8a39b-129">-Action</span></span>
<span data-ttu-id="8a39b-130">Anger den metod som ska köras på det Management-objekt som anges av ResourceURI och väljare.</span><span class="sxs-lookup"><span data-stu-id="8a39b-130">Specifies the method to run on the management object specified by the ResourceURI and selectors.</span></span>

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

### <span data-ttu-id="8a39b-131">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="8a39b-131">-ApplicationName</span></span>
<span data-ttu-id="8a39b-132">Anger program namnet i anslutningen.</span><span class="sxs-lookup"><span data-stu-id="8a39b-132">Specifies the application name in the connection.</span></span>
<span data-ttu-id="8a39b-133">Standardvärdet för parametern *ApplicationName* är WSMan.</span><span class="sxs-lookup"><span data-stu-id="8a39b-133">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="8a39b-134">Den fullständiga identifieraren för Fjärrslutpunkten har följande format:</span><span class="sxs-lookup"><span data-stu-id="8a39b-134">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="8a39b-135">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="8a39b-135">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="8a39b-136">Exempelvis: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="8a39b-136">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="8a39b-137">Internet Information Services (IIS), som är värd för sessionen, vidarebefordrar begär Anden med den här slut punkten till det angivna programmet.</span><span class="sxs-lookup"><span data-stu-id="8a39b-137">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="8a39b-138">Den här standardinställningen för WSMAN är lämplig för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="8a39b-138">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="8a39b-139">Den här parametern är avsedd att användas om många datorer upprättar fjärr anslutningar till en dator som kör PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a39b-139">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="8a39b-140">I det här fallet är IIS värd för webb tjänster för hantering (WS-Management) för effektivitet.</span><span class="sxs-lookup"><span data-stu-id="8a39b-140">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="8a39b-141">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="8a39b-141">-Authentication</span></span>
<span data-ttu-id="8a39b-142">Anger vilken autentiseringsmekanism som ska användas på servern.</span><span class="sxs-lookup"><span data-stu-id="8a39b-142">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="8a39b-143">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="8a39b-143">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8a39b-144">Frö.</span><span class="sxs-lookup"><span data-stu-id="8a39b-144">Basic.</span></span>
<span data-ttu-id="8a39b-145">Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.</span><span class="sxs-lookup"><span data-stu-id="8a39b-145">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="8a39b-146">Standard.</span><span class="sxs-lookup"><span data-stu-id="8a39b-146">Default.</span></span>
<span data-ttu-id="8a39b-147">Använd autentiseringsmetoden som implementeras av WS-Management-protokollet.</span><span class="sxs-lookup"><span data-stu-id="8a39b-147">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="8a39b-148">Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="8a39b-148">This is the default.</span></span>
- <span data-ttu-id="8a39b-149">Nedbrytning.</span><span class="sxs-lookup"><span data-stu-id="8a39b-149">Digest.</span></span>
<span data-ttu-id="8a39b-150">Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.</span><span class="sxs-lookup"><span data-stu-id="8a39b-150">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="8a39b-151">Paket.</span><span class="sxs-lookup"><span data-stu-id="8a39b-151">Kerberos.</span></span>
<span data-ttu-id="8a39b-152">Klient datorn och servern autentiseras ömsesidigt med hjälp av Kerberos-certifikat.</span><span class="sxs-lookup"><span data-stu-id="8a39b-152">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="8a39b-153">Fram.</span><span class="sxs-lookup"><span data-stu-id="8a39b-153">Negotiate.</span></span>
<span data-ttu-id="8a39b-154">Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8a39b-154">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="8a39b-155">Detta parameter värde kan till exempel användas för förhandling för att avgöra om Kerberos-protokollet eller NTLM används.</span><span class="sxs-lookup"><span data-stu-id="8a39b-155">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="8a39b-156">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="8a39b-156">CredSSP.</span></span>
<span data-ttu-id="8a39b-157">Använd CredSSP-autentisering (Credential Security Support Provider), vilket gör att användaren kan delegera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="8a39b-157">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="8a39b-158">Det här alternativet är utformat för kommandon som körs på en fjärrdator men samlar in data från eller kör ytterligare kommandon på andra fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="8a39b-158">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="8a39b-159">Varning! CredSSP delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="8a39b-159">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="8a39b-160">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="8a39b-160">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="8a39b-161">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="8a39b-161">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="8a39b-162">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="8a39b-162">-CertificateThumbprint</span></span>
<span data-ttu-id="8a39b-163">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="8a39b-163">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="8a39b-164">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="8a39b-164">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="8a39b-165">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="8a39b-165">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="8a39b-166">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="8a39b-166">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="8a39b-167">Om du vill hämta ett tumavtryck för certifikatet använder du kommandot Get-Item eller Get-ChildItem i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="8a39b-167">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="8a39b-168">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="8a39b-168">-ComputerName</span></span>
<span data-ttu-id="8a39b-169">Anger den dator som hanterings åtgärden ska köras mot.</span><span class="sxs-lookup"><span data-stu-id="8a39b-169">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="8a39b-170">Värdet kan vara ett fullständigt kvalificerat domän namn, ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="8a39b-170">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="8a39b-171">Använd namnet på den lokala datorn, Använd localhost eller Använd en punkt (.) för att ange den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8a39b-171">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="8a39b-172">Den lokala datorn är standard.</span><span class="sxs-lookup"><span data-stu-id="8a39b-172">The local computer is the default.</span></span>
<span data-ttu-id="8a39b-173">Om fjärrdatorn finns i en annan domän än användaren måste du använda ett fullständigt kvalificerat domän namn.</span><span class="sxs-lookup"><span data-stu-id="8a39b-173">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="8a39b-174">Du kan skicka ett värde för den här parametern till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="8a39b-174">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="8a39b-175">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="8a39b-175">-ConnectionURI</span></span>
<span data-ttu-id="8a39b-176">Anger anslutnings slut punkten.</span><span class="sxs-lookup"><span data-stu-id="8a39b-176">Specifies the connection endpoint.</span></span>
<span data-ttu-id="8a39b-177">Formatet för den här strängen är följande:</span><span class="sxs-lookup"><span data-stu-id="8a39b-177">The format of this string is as follows:</span></span>

<span data-ttu-id="8a39b-178">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="8a39b-178">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="8a39b-179">Följande sträng är ett korrekt formaterat värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="8a39b-179">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="8a39b-180">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="8a39b-180">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="8a39b-181">-Credential</span><span class="sxs-lookup"><span data-stu-id="8a39b-181">-Credential</span></span>
<span data-ttu-id="8a39b-182">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="8a39b-182">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="8a39b-183">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="8a39b-183">The default is the current user.</span></span>
<span data-ttu-id="8a39b-184">Ange ett användar namn, till exempel user01, Domain01\User01 eller User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="8a39b-184">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="8a39b-185">Eller ange ett **PSCredential** -objekt, till exempel ett som returneras av Get-Credential-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8a39b-185">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="8a39b-186">När du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8a39b-186">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="8a39b-187">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="8a39b-187">-FilePath</span></span>
<span data-ttu-id="8a39b-188">Anger sökvägen till en fil som används för att uppdatera en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="8a39b-188">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="8a39b-189">Du anger hanterings resursen med hjälp av parametern *ResourceURI* och parametern *SelectorSet* .</span><span class="sxs-lookup"><span data-stu-id="8a39b-189">You specify the management resource by using the *ResourceURI* parameter and the *SelectorSet* parameter.</span></span>
<span data-ttu-id="8a39b-190">Följande kommando använder till exempel parametern *sökväg* :</span><span class="sxs-lookup"><span data-stu-id="8a39b-190">For example, the following command uses the *FilePath* parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath c:\input.xml -Authentication default`

<span data-ttu-id="8a39b-191">Det här kommandot anropar metoden **Stop** service i **Spooler** -tjänsten genom att använda indata från en fil.</span><span class="sxs-lookup"><span data-stu-id="8a39b-191">This command calls the **StopService** method on the **Spooler** service by using input from a file.</span></span>
<span data-ttu-id="8a39b-192">Filen Input.xml innehåller följande innehåll:</span><span class="sxs-lookup"><span data-stu-id="8a39b-192">The file, Input.xml, contains the following content:</span></span>

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

### <span data-ttu-id="8a39b-193">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="8a39b-193">-OptionSet</span></span>
<span data-ttu-id="8a39b-194">Anger en uppsättning växlar till en tjänst för att ändra eller förfina begärans typ.</span><span class="sxs-lookup"><span data-stu-id="8a39b-194">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="8a39b-195">Dessa liknar växlar som används i kommando rads gränssnitt eftersom de är specifika för specifika tjänster.</span><span class="sxs-lookup"><span data-stu-id="8a39b-195">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="8a39b-196">Valfritt antal alternativ kan anges.</span><span class="sxs-lookup"><span data-stu-id="8a39b-196">Any number of options can be specified.</span></span>

<span data-ttu-id="8a39b-197">I följande exempel visas syntaxen som skickar värdena 1, 2 och 3 för parametrarna a, b och c:</span><span class="sxs-lookup"><span data-stu-id="8a39b-197">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="8a39b-198">-Port</span><span class="sxs-lookup"><span data-stu-id="8a39b-198">-Port</span></span>
<span data-ttu-id="8a39b-199">Anger vilken port som ska användas när klienten ansluter till WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="8a39b-199">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="8a39b-200">När transporten är HTTP är standard porten 80.</span><span class="sxs-lookup"><span data-stu-id="8a39b-200">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="8a39b-201">När transporten är HTTPS är standard porten 443.</span><span class="sxs-lookup"><span data-stu-id="8a39b-201">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="8a39b-202">När du använder HTTPS som transport måste värdet för parametern *computername* matcha serverns certifikats eget namn (CN).</span><span class="sxs-lookup"><span data-stu-id="8a39b-202">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="8a39b-203">Men om parametern *SkipCNCheck* anges som en del av parametern *SessionOption* , behöver inte Certifikatets gemensamma namn matcha serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="8a39b-203">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="8a39b-204">Parametern *SkipCNCheck* ska endast användas för betrodda datorer.</span><span class="sxs-lookup"><span data-stu-id="8a39b-204">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="8a39b-205">– ResourceURI</span><span class="sxs-lookup"><span data-stu-id="8a39b-205">-ResourceURI</span></span>
<span data-ttu-id="8a39b-206">Anger URI för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="8a39b-206">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="8a39b-207">URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="8a39b-207">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="8a39b-208">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="8a39b-208">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="8a39b-209">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="8a39b-209">For example:</span></span>

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

### <span data-ttu-id="8a39b-210">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="8a39b-210">-SelectorSet</span></span>
<span data-ttu-id="8a39b-211">Anger en uppsättning värdepar som används för att välja specifika hanterings resurs instanser.</span><span class="sxs-lookup"><span data-stu-id="8a39b-211">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="8a39b-212">*SelectorSet* används när det finns mer än en instans av resursen.</span><span class="sxs-lookup"><span data-stu-id="8a39b-212">*SelectorSet* is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="8a39b-213">Värdet för *SelectorSet* måste vara en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="8a39b-213">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="8a39b-214">I följande exempel visas hur du anger ett värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="8a39b-214">The following example shows how to enter a value for this parameter:</span></span>

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

### <span data-ttu-id="8a39b-215">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="8a39b-215">-SessionOption</span></span>
<span data-ttu-id="8a39b-216">Anger utökade alternativ för WS-Management-sessionen.</span><span class="sxs-lookup"><span data-stu-id="8a39b-216">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="8a39b-217">Ange ett **SessionOption** -objekt som du skapar med hjälp av New-WSManSessionOption-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8a39b-217">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="8a39b-218">Om du vill ha mer information om vilka alternativ som är tillgängliga skriver du `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="8a39b-218">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="8a39b-219">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="8a39b-219">-UseSSL</span></span>
<span data-ttu-id="8a39b-220">Anger att Secure Sockets Layer-protokollet (SSL) används för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8a39b-220">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="8a39b-221">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="8a39b-221">By default, SSL is not used.</span></span>

<span data-ttu-id="8a39b-222">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="8a39b-222">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="8a39b-223">Med parametern *UseSSL* kan du ange ytterligare skydd av https i stället för http.</span><span class="sxs-lookup"><span data-stu-id="8a39b-223">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="8a39b-224">Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="8a39b-224">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="8a39b-225">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="8a39b-225">-ValueSet</span></span>
<span data-ttu-id="8a39b-226">Anger en hash-tabell som hjälper dig att ändra en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="8a39b-226">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="8a39b-227">Du anger hanterings resursen genom att använda *ResourceURI* -och *SelectorSet*.</span><span class="sxs-lookup"><span data-stu-id="8a39b-227">You specify the management resource by using *ResourceURI* and *SelectorSet*.</span></span>
<span data-ttu-id="8a39b-228">Värdet för parametern *ValueSet* måste vara en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="8a39b-228">The value of the *ValueSet* parameter must be a hash table.</span></span>

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

### <span data-ttu-id="8a39b-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8a39b-229">CommonParameters</span></span>
<span data-ttu-id="8a39b-230">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8a39b-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8a39b-231">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8a39b-231">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8a39b-232">INDATA</span><span class="sxs-lookup"><span data-stu-id="8a39b-232">INPUTS</span></span>

### <span data-ttu-id="8a39b-233">Inget</span><span class="sxs-lookup"><span data-stu-id="8a39b-233">None</span></span>
<span data-ttu-id="8a39b-234">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="8a39b-234">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="8a39b-235">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8a39b-235">OUTPUTS</span></span>

### <span data-ttu-id="8a39b-236">Inget</span><span class="sxs-lookup"><span data-stu-id="8a39b-236">None</span></span>
<span data-ttu-id="8a39b-237">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="8a39b-237">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8a39b-238">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8a39b-238">NOTES</span></span>

## <span data-ttu-id="8a39b-239">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8a39b-239">RELATED LINKS</span></span>

[<span data-ttu-id="8a39b-240">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="8a39b-240">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="8a39b-241">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="8a39b-241">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="8a39b-242">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="8a39b-242">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="8a39b-243">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="8a39b-243">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="8a39b-244">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="8a39b-244">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="8a39b-245">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8a39b-245">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="8a39b-246">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8a39b-246">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="8a39b-247">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="8a39b-247">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="8a39b-248">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8a39b-248">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="8a39b-249">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8a39b-249">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="8a39b-250">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="8a39b-250">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="8a39b-251">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="8a39b-251">Test-WSMan</span></span>](Test-WSMan.md)

