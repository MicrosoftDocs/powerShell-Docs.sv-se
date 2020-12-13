---
title: Arbeta med WMI
description: PowerShell har haft cmdletar för att arbeta med WMI sedan början.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 243685efa1f976ddb46a0d0efc4ed0635844606d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "84436521"
---
# <a name="chapter-7---working-with-wmi"></a><span data-ttu-id="7aa38-103">Kapitel 7 – arbeta med WMI</span><span class="sxs-lookup"><span data-stu-id="7aa38-103">Chapter 7 - Working with WMI</span></span>

## <a name="wmi-and-cim"></a><span data-ttu-id="7aa38-104">WMI och CIM</span><span class="sxs-lookup"><span data-stu-id="7aa38-104">WMI and CIM</span></span>

<span data-ttu-id="7aa38-105">PowerShell levereras som standard med cmdlets för att arbeta med andra tekniker som Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="7aa38-105">PowerShell ships by default with cmdlets for working with other technologies such as Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="7aa38-106">Det finns flera inbyggda WMI-cmdletar som finns i PowerShell utan att behöva installera ytterligare program vara eller moduler.</span><span class="sxs-lookup"><span data-stu-id="7aa38-106">There are several native WMI cmdlets that exist in PowerShell without having to install any additional software or modules.</span></span>

<span data-ttu-id="7aa38-107">PowerShell har haft cmdletar för att arbeta med WMI sedan början.</span><span class="sxs-lookup"><span data-stu-id="7aa38-107">PowerShell has had cmdlets for working with WMI since the beginning.</span></span> <span data-ttu-id="7aa38-108">`Get-Command` kan användas för att avgöra vilka WMI-cmdletar som finns i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7aa38-108">`Get-Command` can be used to determine what WMI cmdlets exist in PowerShell.</span></span> <span data-ttu-id="7aa38-109">Följande resultat är från min Windows 10 Lab Environment-dator som kör PowerShell version 5,1.</span><span class="sxs-lookup"><span data-stu-id="7aa38-109">The following results are from my Windows 10 lab environment computer that is running PowerShell version 5.1.</span></span> <span data-ttu-id="7aa38-110">Resultaten kan variera beroende på vilken PowerShell-version som körs.</span><span class="sxs-lookup"><span data-stu-id="7aa38-110">Your results may differ depending on what PowerShell version you're running.</span></span>

```powershell
Get-Command -Noun WMI*
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-WmiObject                                      3.1.0.0    Microsof...
Cmdlet          Invoke-WmiMethod                                   3.1.0.0    Microsof...
Cmdlet          Register-WmiEvent                                  3.1.0.0    Microsof...
Cmdlet          Remove-WmiObject                                   3.1.0.0    Microsof...
Cmdlet          Set-WmiInstance                                    3.1.0.0    Microsof...
```

<span data-ttu-id="7aa38-111">CIM-cmdlets (Common Information Model) introducerades i PowerShell version 3,0.</span><span class="sxs-lookup"><span data-stu-id="7aa38-111">Common Information Model (CIM) cmdlets were introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="7aa38-112">CIM-cmdletarna är utformade så att de kan användas på både Windows-och icke-Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="7aa38-112">The CIM cmdlets are designed so they can be used on both Windows and non-Windows machines.</span></span> <span data-ttu-id="7aa38-113">WMI-cmdletarna är inaktuella, så min rekommendation är att använda CIM-cmdlets i stället för de äldre WMI-datorerna.</span><span class="sxs-lookup"><span data-stu-id="7aa38-113">The WMI cmdlets are deprecated so my recommendation is to use the CIM cmdlets instead of the older WMI ones.</span></span>

<span data-ttu-id="7aa38-114">CIM-cmdletarna finns i en modul.</span><span class="sxs-lookup"><span data-stu-id="7aa38-114">The CIM cmdlets are all contained within a module.</span></span> <span data-ttu-id="7aa38-115">Om du vill hämta en lista över CIM-cmdletar använder du `Get-Command` med parametern **modul** som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="7aa38-115">To obtain a list of the CIM cmdlets, use `Get-Command` with the **Module** parameter as shown in the following example.</span></span>

```powershell
Get-Command -Module CimCmdlets
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Export-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Get-CimAssociatedInstance                          1.0.0.0    CimCmdlets
Cmdlet          Get-CimClass                                       1.0.0.0    CimCmdlets
Cmdlet          Get-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          Get-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          Import-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Invoke-CimMethod                                   1.0.0.0    CimCmdlets
Cmdlet          New-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          New-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          New-CimSessionOption                               1.0.0.0    CimCmdlets
Cmdlet          Register-CimIndicationEvent                        1.0.0.0    CimCmdlets
Cmdlet          Remove-CimInstance                                 1.0.0.0    CimCmdlets
Cmdlet          Remove-CimSession                                  1.0.0.0    CimCmdlets
Cmdlet          Set-CimInstance                                    1.0.0.0    CimCmdlets
```

<span data-ttu-id="7aa38-116">CIM-cmdletarna tillåter fortfarande att du arbetar med WMI, så du kan inte förväxlas när någon gör instruktionen "när jag frågar WMI med PowerShell CIM-cmdletar..."</span><span class="sxs-lookup"><span data-stu-id="7aa38-116">The CIM cmdlets still allow you to work with WMI so don't be confused when someone makes the statement "When I query WMI with the PowerShell CIM cmdlets..."</span></span>

<span data-ttu-id="7aa38-117">Som tidigare nämnts är WMI en separat teknik från PowerShell och du använder bara CIM-cmdletar för att få åtkomst till WMI.</span><span class="sxs-lookup"><span data-stu-id="7aa38-117">As I previously mentioned, WMI is a separate technology from PowerShell and you're just using the CIM cmdlets for accessing WMI.</span></span> <span data-ttu-id="7aa38-118">Du kan hitta en gammal VBScript som använder WMI Query Language (WQL) för att fråga WMI, som i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="7aa38-118">You may find an old VBScript that uses WMI Query Language (WQL) to query WMI such as in the following example.</span></span>

```vb
strComputer = "."
Set objWMIService = GetObject("winmgmts:" _
    & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\cimv2")

Set colBIOS = objWMIService.ExecQuery _
    ("Select * from Win32_BIOS")

For each objBIOS in colBIOS
    Wscript.Echo "Manufacturer: " & objBIOS.Manufacturer
    Wscript.Echo "Name: " & objBIOS.Name
    Wscript.Echo "Serial Number: " & objBIOS.SerialNumber
    Wscript.Echo "SMBIOS Version: " & objBIOS.SMBIOSBIOSVersion
    Wscript.Echo "Version: " & objBIOS.Version
Next
```

<span data-ttu-id="7aa38-119">Du kan ta WQL-frågan från den VBScript-filen och använda den med `Get-CimInstance` cmdleten utan några ändringar.</span><span class="sxs-lookup"><span data-stu-id="7aa38-119">You can take the WQL query from that VBScript and use it with the `Get-CimInstance` cmdlet without any modifications.</span></span>

```powershell
Get-CimInstance -Query 'Select * from Win32_BIOS'
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

<span data-ttu-id="7aa38-120">Det är inte hur jag normalt frågar WMI med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7aa38-120">That's not how I typically query WMI with PowerShell.</span></span> <span data-ttu-id="7aa38-121">Men det fungerar och gör att du enkelt kan migrera befintliga VBScript till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7aa38-121">But it does work and allows you to easily migrate existing VBScripts to PowerShell.</span></span> <span data-ttu-id="7aa38-122">När jag börjar skriva en one-liner för att fråga WMI använder jag följande syntax.</span><span class="sxs-lookup"><span data-stu-id="7aa38-122">When I start out writing a one-liner to query WMI, I use the following syntax.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

<span data-ttu-id="7aa38-123">Om jag bara vill ha serie numret kan jag lägga till utdata till `Select-Object` och bara ange egenskapen **serialnumber** .</span><span class="sxs-lookup"><span data-stu-id="7aa38-123">If I only want the serial number, I can pipe the output to `Select-Object` and specify only the **SerialNumber** property.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS | Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="7aa38-124">Som standard finns det flera egenskaper som hämtas bakom de scener som aldrig används.</span><span class="sxs-lookup"><span data-stu-id="7aa38-124">By default, there are several properties that are retrieved behind the scenes that are never used.</span></span>
<span data-ttu-id="7aa38-125">Det kanske inte är mycket viktigt när du frågar efter WMI på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="7aa38-125">It may not matter much when querying WMI on the local computer.</span></span> <span data-ttu-id="7aa38-126">Men när du har startat frågor mot fjärrdatorer är det inte bara ytterligare bearbetnings tid att returnera den informationen, utan även ytterligare onödig information att behöva hämta över nätverket.</span><span class="sxs-lookup"><span data-stu-id="7aa38-126">But once you start querying remote computers, it's not only additional processing time to return that information, but also additional unnecessary information to have to pull across the network.</span></span> <span data-ttu-id="7aa38-127">`Get-CimInstance` har en **egenskaps** parameter som begränsar den information som hämtas.</span><span class="sxs-lookup"><span data-stu-id="7aa38-127">`Get-CimInstance` has a **Property** parameter that limits the information that's retrieved.</span></span> <span data-ttu-id="7aa38-128">Detta gör att frågan till WMI är mer effektiv.</span><span class="sxs-lookup"><span data-stu-id="7aa38-128">This makes the query to WMI more efficient.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="7aa38-129">Föregående resultat returnerade ett objekt.</span><span class="sxs-lookup"><span data-stu-id="7aa38-129">The previous results returned an object.</span></span> <span data-ttu-id="7aa38-130">Om du vill returnera en enkel sträng använder du parametern **ExpandProperty** .</span><span class="sxs-lookup"><span data-stu-id="7aa38-130">To return a simple string, use the **ExpandProperty** parameter.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -ExpandProperty SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="7aa38-131">Du kan också använda det punktavgränsade formatet med syntax för att returnera en enkel sträng.</span><span class="sxs-lookup"><span data-stu-id="7aa38-131">You could also use the dotted style of syntax to return a simple string.</span></span> <span data-ttu-id="7aa38-132">Detta eliminerar behovet av att skicka vidare till `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="7aa38-132">This eliminates the need to pipe to `Select-Object`.</span></span>

```powershell
(Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber).SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

## <a name="query-remote-computers-with-the-cim-cmdlets"></a><span data-ttu-id="7aa38-133">Fråga fjärrdatorer med CIM-cmdletar</span><span class="sxs-lookup"><span data-stu-id="7aa38-133">Query Remote Computers with the CIM cmdlets</span></span>

<span data-ttu-id="7aa38-134">Jag kör fortfarande PowerShell som en lokal administratör som är en domän användare.</span><span class="sxs-lookup"><span data-stu-id="7aa38-134">I'm still running PowerShell as a local admin who is a domain user.</span></span> <span data-ttu-id="7aa38-135">När jag försöker fråga efter information från en fjärrdator med hjälp av `Get-CimInstance` cmdleten visas ett fel meddelande om nekad åtkomst.</span><span class="sxs-lookup"><span data-stu-id="7aa38-135">When I try to query information from a remote computer using the `Get-CimInstance` cmdlet, I receive an access denied error message.</span></span>

```powershell
Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
```

```Output
Get-CimInstance : Access is denied.
At line:1 char:1
+ Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
+ ``````````````````````````````````````````````````````~~
    + CategoryInfo          : PermissionDenied: (root\cimv2:Win32_BIOS:String) [Get-CimI
   nstance], CimException
    + FullyQualifiedErrorId : HRESULT 0x80070005,Microsoft.Management.Infrastructure.Cim
   Cmdlets.GetCimInstanceCommand
    + PSComputerName        : dc01
```

<span data-ttu-id="7aa38-136">Många personer har säkerhets problem när de kommer till PowerShell, men sanningen har exakt samma behörigheter i PowerShell som du gör i det grafiska användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7aa38-136">Many people have security concerns when it comes to PowerShell, but the truth is you have exactly the same permissions in PowerShell as you do in the GUI.</span></span> <span data-ttu-id="7aa38-137">Varken mer eller mindre.</span><span class="sxs-lookup"><span data-stu-id="7aa38-137">No more and no less.</span></span> <span data-ttu-id="7aa38-138">Problemet i föregående exempel är att användaren som kör PowerShell inte har behörighet att fråga WMI-information från DC01-servern.</span><span class="sxs-lookup"><span data-stu-id="7aa38-138">The problem in the previous example is that the user running PowerShell doesn't have rights to query WMI information from the DC01 server.</span></span> <span data-ttu-id="7aa38-139">Jag kan starta om PowerShell som domän administratör eftersom det `Get-CimInstance` inte finns någon **Credential** -parameter.</span><span class="sxs-lookup"><span data-stu-id="7aa38-139">I could relaunch PowerShell as a domain administrator since `Get-CimInstance` doesn't have a **Credential** parameter.</span></span> <span data-ttu-id="7aa38-140">Men litar på mig, som inte är en bra idé, eftersom allt som jag kör från PowerShell skulle köras som en domän administratör. Det kan vara farligt från en säkerhets synpunkt beroende på situationen.</span><span class="sxs-lookup"><span data-stu-id="7aa38-140">But, trust me, that isn't a good idea because then anything that I run from PowerShell would be running as a domain admin. That could be dangerous from a security standpoint depending on the situation.</span></span>

<span data-ttu-id="7aa38-141">Genom att använda principen om minsta behörighet, höjer jag till mitt domän administratörs konto på ett per kommando med hjälp av parametern **Credential** , om ett kommando har ett.</span><span class="sxs-lookup"><span data-stu-id="7aa38-141">Using the principle of least privilege, I elevate to my domain admin account on a per command basis using the **Credential** parameter, if a command has one.</span></span> <span data-ttu-id="7aa38-142">`Get-CimInstance` har inte någon **Credential** -parameter, så lösningen i det här scenariot är att skapa en **CimSession** först.</span><span class="sxs-lookup"><span data-stu-id="7aa38-142">`Get-CimInstance` doesn't have a **Credential** parameter so the solution in this scenario is to create a **CimSession** first.</span></span> <span data-ttu-id="7aa38-143">Använd sedan **CimSession** i stället för ett dator namn för att fråga WMI på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="7aa38-143">Then I use the **CimSession** instead of a computer name to query WMI on the remote computer.</span></span>

```powershell
$CimSession = New-CimSession -ComputerName dc01 -Credential (Get-Credential)
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

<span data-ttu-id="7aa38-144">CIM-sessionen lagrades i en variabel med namnet `$CimSession` .</span><span class="sxs-lookup"><span data-stu-id="7aa38-144">The CIM session was stored in a variable named `$CimSession`.</span></span> <span data-ttu-id="7aa38-145">Observera att jag också har angett `Get-Credential` cmdleten inom parentes så att den körs först, efter fråga mig om alternativa autentiseringsuppgifter innan du skapar den nya sessionen.</span><span class="sxs-lookup"><span data-stu-id="7aa38-145">Notice that I also specified the `Get-Credential` cmdlet in parentheses so that it executes first, prompting me for alternate credentials, before creating the new session.</span></span> <span data-ttu-id="7aa38-146">Jag visar ett annat effektivt sätt att ange alternativa autentiseringsuppgifter senare i det här kapitlet, men det är viktigt att förstå detta grundläggande koncept innan du gör det mer komplicerat.</span><span class="sxs-lookup"><span data-stu-id="7aa38-146">I'll show you another more efficient way to specify alternate credentials later in this chapter, but it's important to understand this basic concept before making it more complicated.</span></span>

<span data-ttu-id="7aa38-147">CIM-sessionen som skapades i föregående exempel kan nu användas med `Get-CimInstance` cmdleten för att fråga BIOS-informationen från WMI på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="7aa38-147">The CIM session created in the previous example can now be used with the `Get-CimInstance` cmdlet to query the BIOS information from WMI on the remote computer.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01
```

<span data-ttu-id="7aa38-148">Det finns flera ytterligare fördelar med att använda CIM-sessioner i stället för att bara ange ett dator namn.</span><span class="sxs-lookup"><span data-stu-id="7aa38-148">There are several additional benefits to using CIM sessions instead of just specifying a computer name.</span></span> <span data-ttu-id="7aa38-149">När du kör flera frågor till samma dator är det mer effektivt att använda en CIM-session än att använda dator namnet för varje fråga.</span><span class="sxs-lookup"><span data-stu-id="7aa38-149">When running multiple queries to the same computer, using a CIM session is more efficient than using the computer name for each query.</span></span> <span data-ttu-id="7aa38-150">När du skapar en CIM-session konfigureras bara anslutningen en gång.</span><span class="sxs-lookup"><span data-stu-id="7aa38-150">Creating a CIM session only sets up the connection once.</span></span>
<span data-ttu-id="7aa38-151">Sedan använder flera frågor samma session för att hämta information.</span><span class="sxs-lookup"><span data-stu-id="7aa38-151">Then, multiple queries use that same session to retrieve information.</span></span> <span data-ttu-id="7aa38-152">Om du använder dator namnet måste cmdletarna konfigureras och avskilja anslutningen till varje enskild fråga.</span><span class="sxs-lookup"><span data-stu-id="7aa38-152">Using the computer name requires the cmdlets to set up and tear down the connection with each individual query.</span></span>

<span data-ttu-id="7aa38-153">`Get-CimInstance`Cmdlet: en använder WSMan-protokollet som standard, vilket innebär att fjärrdatorn behöver PowerShell version 3,0 eller senare för att ansluta.</span><span class="sxs-lookup"><span data-stu-id="7aa38-153">The `Get-CimInstance` cmdlet uses the WSMan protocol by default, which means the remote computer needs PowerShell version 3.0 or higher to connect.</span></span> <span data-ttu-id="7aa38-154">Det är faktiskt inte den PowerShell-version som är viktig, den är stack versionen.</span><span class="sxs-lookup"><span data-stu-id="7aa38-154">It's actually not the PowerShell version that matters, it's the stack version.</span></span> <span data-ttu-id="7aa38-155">Stack versionen kan fastställas med hjälp av `Test-WSMan` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7aa38-155">The stack version can be determined using the `Test-WSMan` cmdlet.</span></span>
<span data-ttu-id="7aa38-156">Den måste vara version 3,0.</span><span class="sxs-lookup"><span data-stu-id="7aa38-156">It needs to be version 3.0.</span></span> <span data-ttu-id="7aa38-157">Det är den version du hittar med PowerShell version 3,0 och högre.</span><span class="sxs-lookup"><span data-stu-id="7aa38-157">That's the version you'll find with PowerShell version 3.0 and higher.</span></span>

```powershell
Test-WSMan -ComputerName dc01
```

```Output
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd
ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd
ProductVendor   : Microsoft Corporation
ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 3.0
```

<span data-ttu-id="7aa38-158">Äldre WMI-cmdletar använder DCOM-protokollet, som är kompatibelt med äldre versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="7aa38-158">The older WMI cmdlets use the DCOM protocol, which is compatible with older versions of Windows.</span></span> <span data-ttu-id="7aa38-159">Men DCOM blockeras vanligt vis av brand väggen i nyare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="7aa38-159">But DCOM is typically blocked by the firewall on newer versions of Windows.</span></span> <span data-ttu-id="7aa38-160">`New-CimSessionOption`Med cmdleten kan du skapa en DCOM-protokoll anslutning för användning med `New-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="7aa38-160">The `New-CimSessionOption` cmdlet allows you to create a DCOM protocol connection for use with `New-CimSession`.</span></span> <span data-ttu-id="7aa38-161">Detta gör att `Get-CimInstance` cmdleten kan användas för att kommunicera med Windows-versioner som gamla som Windows Server 2000.</span><span class="sxs-lookup"><span data-stu-id="7aa38-161">This allows the `Get-CimInstance` cmdlet to be used to communicate with versions of Windows as old as Windows Server 2000.</span></span> <span data-ttu-id="7aa38-162">Det innebär också att PowerShell inte krävs på fjärrdatorn när du använder `Get-CimInstance` cmdleten med en CimSession som har kon figurer ATS för att använda DCOM-protokollet.</span><span class="sxs-lookup"><span data-stu-id="7aa38-162">This also means that PowerShell is not required on the remote computer when using the `Get-CimInstance` cmdlet with a CimSession that's configured to use the DCOM protocol.</span></span>

<span data-ttu-id="7aa38-163">Skapa alternativet DCOM-protokoll med hjälp av `New-CimSessionOption` cmdleten och lagra det i en variabel.</span><span class="sxs-lookup"><span data-stu-id="7aa38-163">Create the DCOM protocol option using the `New-CimSessionOption` cmdlet and store it in a variable.</span></span>

```powershell
$DCOM = New-CimSessionOption -Protocol Dcom
```

<span data-ttu-id="7aa38-164">För att vara effektiv kan du lagra domän administratören eller utökade autentiseringsuppgifter i en variabel så att du inte behöver ange dem hela tiden för varje kommando.</span><span class="sxs-lookup"><span data-stu-id="7aa38-164">For efficiency, you can store your domain administrator or elevated credentials in a variable so you don't have to constantly enter them for each command.</span></span>

```powershell
$Cred = Get-Credential
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

<span data-ttu-id="7aa38-165">Jag har en server med namnet SQL03 som kör Windows Server 2008 (ej R2).</span><span class="sxs-lookup"><span data-stu-id="7aa38-165">I have a server named SQL03 that runs Windows Server 2008 (non-R2).</span></span> <span data-ttu-id="7aa38-166">Det är det senaste operativ systemet Windows Server som inte har PowerShell installerat som standard.</span><span class="sxs-lookup"><span data-stu-id="7aa38-166">It's the newest Windows Server operating system that doesn't have PowerShell installed by default.</span></span>

<span data-ttu-id="7aa38-167">Skapa en **CimSession** till SQL03 med DCOM-protokollet.</span><span class="sxs-lookup"><span data-stu-id="7aa38-167">Create a **CimSession** to SQL03 using the DCOM protocol.</span></span>

```powershell
$CimSession = New-CimSession -ComputerName sql03 -SessionOption $DCOM -Credential $Cred
```

<span data-ttu-id="7aa38-168">Observera i föregående kommando, den här gången jag angav variabeln med namnet `$Cred` som värde för parametern **Credential** i stället för att behöva ange dem manuellt.</span><span class="sxs-lookup"><span data-stu-id="7aa38-168">Notice in the previous command, this time I specified the variable named `$Cred` as the value for the **Credential** parameter instead of having to enter them manually again.</span></span>

<span data-ttu-id="7aa38-169">Resultatet av frågan är detsamma oavsett vilket underliggande protokoll som används.</span><span class="sxs-lookup"><span data-stu-id="7aa38-169">The output of the query is the same regardless of the underlying protocol being used.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

<span data-ttu-id="7aa38-170">`Get-CimSession`Cmdleten används för att se vilka **CimSessions** som för närvarande är anslutna och vilka protokoll de använder.</span><span class="sxs-lookup"><span data-stu-id="7aa38-170">The `Get-CimSession` cmdlet is used to see what **CimSessions** are currently connected and what protocols they're using.</span></span>

```powershell
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : 80742787-e38e-41b1-a7d7-fa1369cf1402
ComputerName : dc01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : 8fcabd81-43cf-4682-bd53-ccce1e24aecb
ComputerName : sql03
Protocol     : DCOM
```

<span data-ttu-id="7aa38-171">Hämta och lagra båda de tidigare skapade **CimSessions** i en variabel med namnet `$CimSession` .</span><span class="sxs-lookup"><span data-stu-id="7aa38-171">Retrieve and store both of the previously created **CimSessions** in a variable named `$CimSession`.</span></span>

```powershell
$CimSession = Get-CimSession
```

<span data-ttu-id="7aa38-172">Fråga båda datorerna med ett kommando, ett med hjälp av WSMan-protokollet och det andra med DCOM.</span><span class="sxs-lookup"><span data-stu-id="7aa38-172">Query both of the computers with one command, one using the WSMan protocol and the other one with DCOM.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01

SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

<span data-ttu-id="7aa38-173">Jag har skrivit många blogg artiklar om WMI-och CIM-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="7aa38-173">I've written numerous blog articles about the WMI and CIM cmdlets.</span></span> <span data-ttu-id="7aa38-174">En av de mest användbara är om en funktion som jag skapade för att automatiskt avgöra om WSMan eller DCOM ska användas och konfigurera CIM-sessionen automatiskt utan att behöva ta reda på vilken som manuellt.</span><span class="sxs-lookup"><span data-stu-id="7aa38-174">One of the most useful ones is about a function that I created to automatically determine if WSMan or DCOM should be used and set up the CIM session automatically without having to figure out which one manually.</span></span> <span data-ttu-id="7aa38-175">Blogg artikeln heter [PowerShell-funktionen för att skapa CimSessions till fjärrdatorer med fallback till DCOM][].</span><span class="sxs-lookup"><span data-stu-id="7aa38-175">That blog article is titled [PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom][].</span></span>

<span data-ttu-id="7aa38-176">När du är klar med CIM-sessionerna bör du ta bort dem med `Remove-CimSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7aa38-176">When you're finished with the CIM sessions, you should remove them with the `Remove-CimSession` cmdlet.</span></span> <span data-ttu-id="7aa38-177">Ta bort alla CIM-sessioner genom att bara skicka vidare `Get-CimSession` till `Remove-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="7aa38-177">To remove all CIM sessions, simply pipe `Get-CimSession` to `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

## <a name="summary"></a><span data-ttu-id="7aa38-178">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="7aa38-178">Summary</span></span>

<span data-ttu-id="7aa38-179">I det här kapitlet har du lärt dig att använda PowerShell för att arbeta med WMI på både lokala och fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="7aa38-179">In this chapter, you've learned about using PowerShell to work with WMI on both local and remote computers.</span></span> <span data-ttu-id="7aa38-180">Du har också lärt dig hur du använder CIM-cmdletar för att arbeta med fjärrdatorer med både WSMan-eller DCOM-protokollet.</span><span class="sxs-lookup"><span data-stu-id="7aa38-180">You've also learned how to use the CIM cmdlets to work with remote computers with both the WSMan or DCOM protocol.</span></span>

## <a name="review"></a><span data-ttu-id="7aa38-181">Genomgång</span><span class="sxs-lookup"><span data-stu-id="7aa38-181">Review</span></span>

1. <span data-ttu-id="7aa38-182">Vad är skillnaden i WMI-och CIM-cmdletarna?</span><span class="sxs-lookup"><span data-stu-id="7aa38-182">What is the difference in the WMI and CIM cmdlets?</span></span>
1. <span data-ttu-id="7aa38-183">Som standard använder-protokollet `Get-CimInstance` cmdleten?</span><span class="sxs-lookup"><span data-stu-id="7aa38-183">By default, what protocol does the `Get-CimInstance` cmdlet use?</span></span>
1. <span data-ttu-id="7aa38-184">Vilka är fördelarna med att använda en CIM-session i stället för att ange ett dator namn med `Get-CimInstance` ?</span><span class="sxs-lookup"><span data-stu-id="7aa38-184">What are some of the benefits of using a CIM session instead of specifying a computer name with `Get-CimInstance`?</span></span>
1. <span data-ttu-id="7aa38-185">Hur kan du ange ett annat protokoll än det som är standard som används med `Get-CimInstance` ?</span><span class="sxs-lookup"><span data-stu-id="7aa38-185">How do you specify an alternate protocol other than the default one for use with `Get-CimInstance`?</span></span>
1. <span data-ttu-id="7aa38-186">Hur stänger eller tar du bort CIM-sessioner?</span><span class="sxs-lookup"><span data-stu-id="7aa38-186">How do you close or remove CIM sessions?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="7aa38-187">Rekommenderad läsning</span><span class="sxs-lookup"><span data-stu-id="7aa38-187">Recommended Reading</span></span>

- <span data-ttu-id="7aa38-188">[about_WMI][]</span><span class="sxs-lookup"><span data-stu-id="7aa38-188">[about_WMI][]</span></span>
- <span data-ttu-id="7aa38-189">[about_WMI_Cmdlets][]</span><span class="sxs-lookup"><span data-stu-id="7aa38-189">[about_WMI_Cmdlets][]</span></span>
- <span data-ttu-id="7aa38-190">[about_WQL][]</span><span class="sxs-lookup"><span data-stu-id="7aa38-190">[about_WQL][]</span></span>
- <span data-ttu-id="7aa38-191">[CimCmdlets-modul][]</span><span class="sxs-lookup"><span data-stu-id="7aa38-191">[CimCmdlets Module][]</span></span>
- <span data-ttu-id="7aa38-192">[Video: använda CIM-cmdlets och CIM-sessioner][]</span><span class="sxs-lookup"><span data-stu-id="7aa38-192">[Video: Using CIM Cmdlets and CIM Sessions][]</span></span>

<!-- link references -->
[about_WMI]: /powershell/module/microsoft.powershell.core/about/about_wmi
[about_WMI_Cmdlets]: /powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets
[about_WQL]: /powershell/module/microsoft.powershell.core/about/about_wql
[CimCmdlets-modul]: /powershell/module/cimcmdlets/
[CimCmdlets Module]: /powershell/module/cimcmdlets/
[Video: använda CIM-cmdlets och CIM-sessioner]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[Video: Using CIM Cmdlets and CIM Sessions]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[PowerShell-funktion för att skapa CimSessions till fjärrdatorer med återgång till DCOM]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
[PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
