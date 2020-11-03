---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-wmimethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WmiMethod
ms.openlocfilehash: e9743488e86429e5cc3252162e51268a7978b79d
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/09/2020
ms.locfileid: "93268029"
---
# <span data-ttu-id="925bb-103">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="925bb-103">Invoke-WmiMethod</span></span>

## <span data-ttu-id="925bb-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="925bb-104">SYNOPSIS</span></span>
<span data-ttu-id="925bb-105">Anropar WMI-metoder.</span><span class="sxs-lookup"><span data-stu-id="925bb-105">Calls WMI methods.</span></span>

## <span data-ttu-id="925bb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="925bb-106">SYNTAX</span></span>

### <span data-ttu-id="925bb-107">klass (standard)</span><span class="sxs-lookup"><span data-stu-id="925bb-107">class (Default)</span></span>

```
Invoke-WmiMethod [-Class] <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="925bb-108">objekt</span><span class="sxs-lookup"><span data-stu-id="925bb-108">object</span></span>

```
Invoke-WmiMethod -InputObject <ManagementObject> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="925bb-109">path</span><span class="sxs-lookup"><span data-stu-id="925bb-109">path</span></span>

```
Invoke-WmiMethod -Path <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="925bb-110">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="925bb-110">WQLQuery</span></span>

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="925bb-111">DocumentDB</span><span class="sxs-lookup"><span data-stu-id="925bb-111">query</span></span>

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="925bb-112">lista</span><span class="sxs-lookup"><span data-stu-id="925bb-112">list</span></span>

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="925bb-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="925bb-113">DESCRIPTION</span></span>

<span data-ttu-id="925bb-114">`Invoke-WmiMethod`Cmdleten anropar metoder för Windows Management Instrumentation (WMI)-objekt.</span><span class="sxs-lookup"><span data-stu-id="925bb-114">The `Invoke-WmiMethod` cmdlet calls the methods of Windows Management Instrumentation (WMI) objects.</span></span>

<span data-ttu-id="925bb-115">Nya Common Information Model CIM-cmdletar, som introducerades i Windows PowerShell 3,0, utför samma uppgifter som WMI-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="925bb-115">New Common Information Model (CIM) cmdlets, introduced in Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span> <span data-ttu-id="925bb-116">CIM-cmdlets följer WS-Management (WSMan)-standarder och med CIM-standarden, som gör att cmdlets kan använda samma metoder för att hantera Windows-datorer och de som kör andra operativ system.</span><span class="sxs-lookup"><span data-stu-id="925bb-116">The CIM cmdlets comply with WS-Management (WSMan) standards and with the CIM standard, which enables the cmdlets to use the same techniques to manage Windows computers and those running other operating systems.</span></span> <span data-ttu-id="925bb-117">Använd `Invoke-WmiMethod` [Invoke-CimMethod](../cimcmdlets/invoke-cimmethod.md)i stället för att använda.</span><span class="sxs-lookup"><span data-stu-id="925bb-117">Instead of using `Invoke-WmiMethod`, consider using [Invoke-CimMethod](../cimcmdlets/invoke-cimmethod.md).</span></span>

## <span data-ttu-id="925bb-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="925bb-118">EXAMPLES</span></span>

### <span data-ttu-id="925bb-119">Exempel 1: Ange den nödvändiga ordningen för WMI-objekt</span><span class="sxs-lookup"><span data-stu-id="925bb-119">Example 1: List the required order of WMI objects</span></span>

```powershell
([wmiclass]'Win32_Volume').GetMethodParameters('Format')
```

```Output
__GENUS           : 2
__CLASS           : __PARAMETERS
__SUPERCLASS      :
__DYNASTY         : __PARAMETERS
__RELPATH         :
__PROPERTY_COUNT  : 6
__DERIVATION      : {}
__SERVER          :
__NAMESPACE       :
__PATH            :
ClusterSize       : 0
EnableCompression : False
FileSystem        : NTFS
Label             :
QuickFormat       : False
Version           : 0
PSComputerName    :
```

<span data-ttu-id="925bb-120">Det här kommandot visar den ordning som krävs för objekten.</span><span class="sxs-lookup"><span data-stu-id="925bb-120">This command lists the required order of the objects.</span></span> <span data-ttu-id="925bb-121">Att anropa WMI i PowerShell 3,0 skiljer sig från alternativa metoder och kräver att objekt värden anges i en speciell ordning.</span><span class="sxs-lookup"><span data-stu-id="925bb-121">To invoke WMI in PowerShell 3.0 differs from alternate methods, and requires that object values are entered in a specific order.</span></span>

### <span data-ttu-id="925bb-122">Exempel 2: starta en instans av ett program</span><span class="sxs-lookup"><span data-stu-id="925bb-122">Example 2: Start an instance of an application</span></span>

```powershell
([Wmiclass]'Win32_Process').GetMethodParameters('Create')
```

```Output
__GENUS                   : 2
__CLASS                   : __PARAMETERS
__SUPERCLASS              :
__DYNASTY                 : __PARAMETERS
__RELPATH                 :
__PROPERTY_COUNT          : 3
__DERIVATION              : {}
__SERVER                  :
__NAMESPACE               :
__PATH                    :
CommandLine               :
CurrentDirectory          :
ProcessStartupInformation :
PSComputerName            :
```

```powershell
Invoke-WmiMethod -Path win32_process -Name create -ArgumentList notepad.exe
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 2
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ProcessId        : 11312
ReturnValue      : 0
PSComputerName   :
```

<span data-ttu-id="925bb-123">Det här kommandot startar en instans av anteckningar genom `Create` att anropa metoden i **Win32_Process** -klassen.</span><span class="sxs-lookup"><span data-stu-id="925bb-123">This command starts an instance of Notepad by calling the `Create` method of the **Win32_Process** class.</span></span>

<span data-ttu-id="925bb-124">Egenskapen **returnValue** fylls med en 0 och **ProcessID** -egenskapen fylls med ett heltal (nästa process-ID-nummer) om kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="925bb-124">The **ReturnValue** property is populated with a 0, and the **ProcessId** property is populated with an integer (the next process ID number) if the command is completed.</span></span>

### <span data-ttu-id="925bb-125">Exempel 3: Byt namn på en fil</span><span class="sxs-lookup"><span data-stu-id="925bb-125">Example 3: Rename a file</span></span>

```powershell
Invoke-WmiMethod -Path "CIM_DataFile.Name='C:\scripts\test.txt'" -Name Rename -ArgumentList "C:\scripts\test_bu.txt"
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ReturnValue      : 0
```

<span data-ttu-id="925bb-126">Det här kommandot byter namn på en fil.</span><span class="sxs-lookup"><span data-stu-id="925bb-126">This command renames a file.</span></span> <span data-ttu-id="925bb-127">Parametern **Path** används för att referera till en instans av klassen **cim_datafile** .</span><span class="sxs-lookup"><span data-stu-id="925bb-127">It uses the **Path** parameter to reference an instance of the **CIM_DataFile** class.</span></span> <span data-ttu-id="925bb-128">Sedan tillämpar den metoden Rename på den specifika instansen.</span><span class="sxs-lookup"><span data-stu-id="925bb-128">Then, it applies the Rename method to that particular instance.</span></span>

<span data-ttu-id="925bb-129">Egenskapen **returnValue** fylls med en 0 om kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="925bb-129">The **ReturnValue** property is populated with a 0 if the command is completed.</span></span>

### <span data-ttu-id="925bb-130">Exempel 4: skicka en matris med värden med hjälp av `-ArgumentList`</span><span class="sxs-lookup"><span data-stu-id="925bb-130">Example 4: Passing an array of values using `-ArgumentList`</span></span>

<span data-ttu-id="925bb-131">Ett exempel som använder en matris med objekt `$binSD` följt av ett `$null` värde.</span><span class="sxs-lookup"><span data-stu-id="925bb-131">An example using an array of objects `$binSD` followed by a `$null` value.</span></span>

```powershell
$acl = get-acl test.txt
$binSD = $acl.GetSecurityDescriptorBinaryForm()
Invoke-WmiMethod -class Win32_SecurityDescriptorHelper -Name BinarySDToSDDL -ArgumentList $binSD, $null
```

## <span data-ttu-id="925bb-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="925bb-132">PARAMETERS</span></span>

### <span data-ttu-id="925bb-133">– Argument List</span><span class="sxs-lookup"><span data-stu-id="925bb-133">-ArgumentList</span></span>

<span data-ttu-id="925bb-134">Anger de parametrar som ska skickas till den anropade metoden.</span><span class="sxs-lookup"><span data-stu-id="925bb-134">Specifies the parameters to pass to the called method.</span></span> <span data-ttu-id="925bb-135">Värdet för den här parametern måste vara en matris med objekt, och de måste visas i den ordning som den anropade metoden kräver.</span><span class="sxs-lookup"><span data-stu-id="925bb-135">The value of this parameter must be an array of objects, and they must appear in the order required by the called method.</span></span> <span data-ttu-id="925bb-136">`Invoke-CimCommand`Cmdleten har inte de här begränsningarna.</span><span class="sxs-lookup"><span data-stu-id="925bb-136">The `Invoke-CimCommand` cmdlet does not have these limitations.</span></span>

<span data-ttu-id="925bb-137">Om du vill fastställa i vilken ordning dessa objekt ska visas kör du `GetMethodParameters()` metoden i WMI-klassen, som visas i exempel 1, nära slutet av det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="925bb-137">To determine the order in which to list those objects, run the `GetMethodParameters()` method on the WMI class, as illustrated in Example 1, near the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="925bb-138">Om det första värdet är en matris som innehåller mer än ett element, krävs ett andra värde för $null.</span><span class="sxs-lookup"><span data-stu-id="925bb-138">If the first value is an array that contains more than one element, a second value of $null is required.</span></span> <span data-ttu-id="925bb-139">Annars genererar kommandot ett fel, till exempel "det går inte att omvandla objekt av typen system. byte" till typen "system. array". ".</span><span class="sxs-lookup"><span data-stu-id="925bb-139">Otherwise, the command generates an error, such as "Unable to cast object of type 'System.Byte' to type 'System.Array'.".</span></span> <span data-ttu-id="925bb-140">Se exempel 4 ovan.</span><span class="sxs-lookup"><span data-stu-id="925bb-140">See example 4 above.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: class, object, path
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="925bb-141">– AsJob</span><span class="sxs-lookup"><span data-stu-id="925bb-141">-AsJob</span></span>

<span data-ttu-id="925bb-142">Anger att denna cmdlet kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="925bb-142">Indicates that this cmdlet runs the command as a background job.</span></span> <span data-ttu-id="925bb-143">Använd den här parametern för att köra kommandon som tar lång tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="925bb-143">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="925bb-144">När du använder parametern **AsJob** returnerar kommandot ett objekt som representerar bakgrunds jobbet och visar sedan kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="925bb-144">When you use the **AsJob** parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span> <span data-ttu-id="925bb-145">Du kan fortsätta att arbeta i sessionen medan jobbet är klart.</span><span class="sxs-lookup"><span data-stu-id="925bb-145">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="925bb-146">Om `Invoke-WmiMethod` används mot en fjärrdator skapas jobbet på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="925bb-146">If `Invoke-WmiMethod` is used against a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="925bb-147">Om du vill hantera jobbet använder du de cmdlet: ar som innehåller jobbet Substantiv (jobb-cmdletarna).</span><span class="sxs-lookup"><span data-stu-id="925bb-147">To manage the job, use the cmdlets that contain the Job noun (the Job cmdlets).</span></span> <span data-ttu-id="925bb-148">Använd Receive-Job-cmdleten för att hämta jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="925bb-148">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="925bb-149">Om du vill använda den här parametern med fjärrdatorer måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="925bb-149">To use this parameter with remote computers, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="925bb-150">Dessutom måste du starta Windows PowerShell med alternativet Kör som administratör i Windows Vista och senare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="925bb-150">Additionally, you must start Windows PowerShell by using the Run as administrator option in Windows Vista and later versions of Windows.</span></span> <span data-ttu-id="925bb-151">Mer information finns i about_Remote_Requirements.</span><span class="sxs-lookup"><span data-stu-id="925bb-151">For more information, see about_Remote_Requirements.</span></span>

<span data-ttu-id="925bb-152">Mer information om bakgrunds jobb i Windows PowerShell finns i about_Jobs och about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="925bb-152">For more information about Windows PowerShell background jobs, see about_Jobs and about_Remote_Jobs.</span></span>

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

### <span data-ttu-id="925bb-153">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="925bb-153">-Authentication</span></span>

<span data-ttu-id="925bb-154">Anger den autentiseringsnivå som ska användas med WMI-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="925bb-154">Specifies the authentication level to be used with the WMI connection.</span></span> <span data-ttu-id="925bb-155">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="925bb-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="925bb-156">-1: oförändrad</span><span class="sxs-lookup"><span data-stu-id="925bb-156">-1: Unchanged</span></span>
- <span data-ttu-id="925bb-157">0: standard</span><span class="sxs-lookup"><span data-stu-id="925bb-157">0: Default</span></span>
- <span data-ttu-id="925bb-158">1: ingen (ingen autentisering utförs)</span><span class="sxs-lookup"><span data-stu-id="925bb-158">1: None (No authentication in performed.)</span></span>
- <span data-ttu-id="925bb-159">2: Anslut (autentisering utförs endast när klienten upprättar en relation med programmet.)</span><span class="sxs-lookup"><span data-stu-id="925bb-159">2: Connect (Authentication is performed only when the client establishes a relationship with the application.)</span></span>
- <span data-ttu-id="925bb-160">3: anrop (autentisering utförs endast i början av varje anrop när programmet tar emot begäran.)</span><span class="sxs-lookup"><span data-stu-id="925bb-160">3: Call (Authentication is performed only at the beginning of each call when the application receives the request.)</span></span>
- <span data-ttu-id="925bb-161">4: paket (autentisering utförs på alla data som tas emot från klienten).</span><span class="sxs-lookup"><span data-stu-id="925bb-161">4: Packet (Authentication is performed on all the data that is received from the client.)</span></span>
- <span data-ttu-id="925bb-162">5: PacketIntegrity (alla data som överförs mellan klienten och programmet autentiseras och verifieras.)</span><span class="sxs-lookup"><span data-stu-id="925bb-162">5: PacketIntegrity (All the data that is transferred between the client and the application is authenticated and verified.)</span></span>
- <span data-ttu-id="925bb-163">6: PacketPrivacy (egenskaperna för de andra autentiseringsnivåer används och alla data krypteras.)</span><span class="sxs-lookup"><span data-stu-id="925bb-163">6: PacketPrivacy (The properties of the other authentication levels are used, and all the data is encrypted.)</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="925bb-164">-Authority</span><span class="sxs-lookup"><span data-stu-id="925bb-164">-Authority</span></span>

<span data-ttu-id="925bb-165">Anger den auktoritet som ska användas för att autentisera WMI-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="925bb-165">Specifies the authority to use to authenticate the WMI connection.</span></span> <span data-ttu-id="925bb-166">Du kan ange standard för Windows NT LAN Manager (NTLM) eller Kerberos-autentisering.</span><span class="sxs-lookup"><span data-stu-id="925bb-166">You can specify standard Windows NT LAN Manager (NTLM) or Kerberos authentication.</span></span> <span data-ttu-id="925bb-167">Om du vill använda NTLM ställer du in inställningen auktoritet på ntlmdomain: \<DomainName\> , där \<DomainName\> identifierar ett giltigt NTLM-domännamn.</span><span class="sxs-lookup"><span data-stu-id="925bb-167">To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.</span></span> <span data-ttu-id="925bb-168">Ange Kerberos om du vill använda Kerberos: \<DomainName\ServerName\> .</span><span class="sxs-lookup"><span data-stu-id="925bb-168">To use Kerberos, specify kerberos:\<DomainName\ServerName\>.</span></span> <span data-ttu-id="925bb-169">Du kan inte inkludera auktoritets inställningen när du ansluter till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="925bb-169">You cannot include the authority setting when you connect to the local computer.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="925bb-170">– Klass</span><span class="sxs-lookup"><span data-stu-id="925bb-170">-Class</span></span>

<span data-ttu-id="925bb-171">Anger den WMI-klass som innehåller en statisk metod som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="925bb-171">Specifies the WMI class that contains a static method to call.</span></span>

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="925bb-172">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="925bb-172">-ComputerName</span></span>

<span data-ttu-id="925bb-173">Anger, som en sträng mat ris, de datorer som denna cmdlet kör kommandot på.</span><span class="sxs-lookup"><span data-stu-id="925bb-173">Specifies, as a string array, the computers that this cmdlet runs the command on.</span></span> <span data-ttu-id="925bb-174">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="925bb-174">The default is the local computer.</span></span>

<span data-ttu-id="925bb-175">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera datorer.</span><span class="sxs-lookup"><span data-stu-id="925bb-175">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.</span></span> <span data-ttu-id="925bb-176">Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller localhost.</span><span class="sxs-lookup"><span data-stu-id="925bb-176">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="925bb-177">Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="925bb-177">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="925bb-178">Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="925bb-178">You can use the **ComputerName** parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="925bb-179">-Credential</span><span class="sxs-lookup"><span data-stu-id="925bb-179">-Credential</span></span>

<span data-ttu-id="925bb-180">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="925bb-180">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="925bb-181">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="925bb-181">The default is the current user.</span></span> <span data-ttu-id="925bb-182">Ange ett användar namn, till exempel `User01` , `Domain01\User01` eller `User@Contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="925bb-182">Type a user name, such as `User01`, `Domain01\User01`, or `User@Contoso.com`.</span></span> <span data-ttu-id="925bb-183">Eller ange ett **PSCredential** -objekt, till exempel ett objekt som returneras av Get-Credential-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="925bb-183">Or, enter a **PSCredential** object, such as an object that is returned by the Get-Credential cmdlet.</span></span> <span data-ttu-id="925bb-184">När du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="925bb-184">When you type a user name, you will be prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="925bb-185">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="925bb-185">-EnableAllPrivileges</span></span>

<span data-ttu-id="925bb-186">Anger att denna cmdlet aktiverar alla behörigheter för den aktuella användaren innan kommandot gör WMI-anropet.</span><span class="sxs-lookup"><span data-stu-id="925bb-186">Indicates that this cmdlet enables all the privileges of the current user before the command makes the WMI call.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="925bb-187">-Personifiering</span><span class="sxs-lookup"><span data-stu-id="925bb-187">-Impersonation</span></span>

<span data-ttu-id="925bb-188">Anger personifieringsnivån som ska användas.</span><span class="sxs-lookup"><span data-stu-id="925bb-188">Specifies the impersonation level to use.</span></span> <span data-ttu-id="925bb-189">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="925bb-189">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="925bb-190">0: standard (läser det lokala registret för standard personifieringsnivån, som vanligt vis anges till "3: personifiera".)</span><span class="sxs-lookup"><span data-stu-id="925bb-190">0: Default (Reads the local registry for the default impersonation level, which is usually set to "3: Impersonate".)</span></span>
- <span data-ttu-id="925bb-191">1: Anonym (döljer anroparens autentiseringsuppgifter.)</span><span class="sxs-lookup"><span data-stu-id="925bb-191">1: Anonymous (Hides the credentials of the caller.)</span></span>
- <span data-ttu-id="925bb-192">2: identifiera (tillåter objekt att fråga om autentiseringsuppgifterna för anroparen.)</span><span class="sxs-lookup"><span data-stu-id="925bb-192">2: Identify (Allows objects to query the credentials of the caller.)</span></span>
- <span data-ttu-id="925bb-193">3: personifiera (tillåter att objekt använder autentiseringsuppgifterna för anroparen.)</span><span class="sxs-lookup"><span data-stu-id="925bb-193">3: Impersonate (Allows objects to use the credentials of the caller.)</span></span>
- <span data-ttu-id="925bb-194">4: delegera (tillåter att objekt tillåter andra objekt att använda autentiseringsuppgifterna för anroparen.)</span><span class="sxs-lookup"><span data-stu-id="925bb-194">4: Delegate (Allows objects to permit other objects to use the credentials of the caller.)</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="925bb-195">– InputObject</span><span class="sxs-lookup"><span data-stu-id="925bb-195">-InputObject</span></span>

<span data-ttu-id="925bb-196">Anger ett **ManagementObject** -objekt som ska användas som indatamängd.</span><span class="sxs-lookup"><span data-stu-id="925bb-196">Specifies a **ManagementObject** object to use as input.</span></span> <span data-ttu-id="925bb-197">När den här parametern används ignoreras alla andra parametrar förutom parametrarna **flagga** och **argument** .</span><span class="sxs-lookup"><span data-stu-id="925bb-197">When this parameter is used, all other parameters except the **Flag** and **Argument** parameters are ignored.</span></span>

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="925bb-198">-Locale</span><span class="sxs-lookup"><span data-stu-id="925bb-198">-Locale</span></span>

<span data-ttu-id="925bb-199">Anger det önskade språket för WMI-objekt.</span><span class="sxs-lookup"><span data-stu-id="925bb-199">Specifies the preferred locale for WMI objects.</span></span> <span data-ttu-id="925bb-200">Ange värdet för parametern **locale** som en matris i `MS_<LCID>` formatet i önskad ordning.</span><span class="sxs-lookup"><span data-stu-id="925bb-200">Specify the value of the **Locale** parameter as an array in the `MS_<LCID>` format in the preferred order.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="925bb-201">-Name</span><span class="sxs-lookup"><span data-stu-id="925bb-201">-Name</span></span>

<span data-ttu-id="925bb-202">Anger namnet på den metod som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="925bb-202">Specifies the name of the method to be invoked.</span></span> <span data-ttu-id="925bb-203">Den här parametern är obligatorisk och får inte vara null eller tom.</span><span class="sxs-lookup"><span data-stu-id="925bb-203">This parameter is mandatory and cannot be null or empty.</span></span>

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

### <span data-ttu-id="925bb-204">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="925bb-204">-Namespace</span></span>

<span data-ttu-id="925bb-205">När den används med **klass** parametern anger den här parametern namn området för WMI-lagringsplatsen där den refererade WMI-klassen eller-objektet finns.</span><span class="sxs-lookup"><span data-stu-id="925bb-205">When used with the **Class** parameter, this parameter specifies the WMI repository namespace where the referenced WMI class or object is located.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="925bb-206">-Path</span><span class="sxs-lookup"><span data-stu-id="925bb-206">-Path</span></span>

<span data-ttu-id="925bb-207">Anger WMI-objektets sökväg för en WMI-klass eller anger sökvägen till WMI-objektet för en instans av en WMI-klass.</span><span class="sxs-lookup"><span data-stu-id="925bb-207">Specifies the WMI object path of a WMI class, or specifies the WMI object path of an instance of a WMI class.</span></span> <span data-ttu-id="925bb-208">Den klass eller instans som du anger måste innehålla metoden som anges i parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="925bb-208">The class or the instance that you specify must contain the method that is specified in the **Name** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="925bb-209">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="925bb-209">-ThrottleLimit</span></span>

<span data-ttu-id="925bb-210">Anger ett begränsnings värde för antalet WMI-åtgärder som kan köras samtidigt.</span><span class="sxs-lookup"><span data-stu-id="925bb-210">Specifies a throttle value for the number of WMI operations that can be executed simultaneously.</span></span>
<span data-ttu-id="925bb-211">Den här parametern används tillsammans med parametern **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="925bb-211">This parameter is used together with the **AsJob** parameter.</span></span> <span data-ttu-id="925bb-212">Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.</span><span class="sxs-lookup"><span data-stu-id="925bb-212">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="925bb-213">-Confirm</span><span class="sxs-lookup"><span data-stu-id="925bb-213">-Confirm</span></span>

<span data-ttu-id="925bb-214">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="925bb-214">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="925bb-215">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="925bb-215">-WhatIf</span></span>

<span data-ttu-id="925bb-216">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="925bb-216">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="925bb-217">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="925bb-217">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="925bb-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="925bb-218">CommonParameters</span></span>

<span data-ttu-id="925bb-219">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="925bb-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="925bb-220">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="925bb-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="925bb-221">INDATA</span><span class="sxs-lookup"><span data-stu-id="925bb-221">INPUTS</span></span>

### <span data-ttu-id="925bb-222">Inget</span><span class="sxs-lookup"><span data-stu-id="925bb-222">None</span></span>

<span data-ttu-id="925bb-223">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="925bb-223">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="925bb-224">UTDATA</span><span class="sxs-lookup"><span data-stu-id="925bb-224">OUTPUTS</span></span>

### <span data-ttu-id="925bb-225">Inget</span><span class="sxs-lookup"><span data-stu-id="925bb-225">None</span></span>

<span data-ttu-id="925bb-226">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="925bb-226">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="925bb-227">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="925bb-227">NOTES</span></span>

## <span data-ttu-id="925bb-228">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="925bb-228">RELATED LINKS</span></span>

[<span data-ttu-id="925bb-229">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="925bb-229">Get-WSManInstance</span></span>](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[<span data-ttu-id="925bb-230">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="925bb-230">Invoke-WSManAction</span></span>](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[<span data-ttu-id="925bb-231">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="925bb-231">New-WSManInstance</span></span>](../Microsoft.WsMan.Management/New-WSManInstance.md)

[<span data-ttu-id="925bb-232">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="925bb-232">Remove-WSManInstance</span></span>](../Microsoft.WsMan.Management/Remove-WSManInstance.md)

[<span data-ttu-id="925bb-233">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="925bb-233">Get-WmiObject</span></span>](Get-WmiObject.md)

[<span data-ttu-id="925bb-234">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="925bb-234">Remove-WmiObject</span></span>](Remove-WmiObject.md)

[<span data-ttu-id="925bb-235">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="925bb-235">Set-WmiInstance</span></span>](Set-WmiInstance.md)
