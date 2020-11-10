---
description: Beskriver snapin-moduler för Windows PowerShell och visar hur du använder och hanterar dem.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSnapins
ms.openlocfilehash: 494b3275e4fe8a3aacdc358317950542962957cf
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388900"
---
# <a name="about-pssnapins"></a><span data-ttu-id="ffdaf-104">Om PSSnapins</span><span class="sxs-lookup"><span data-stu-id="ffdaf-104">About PSSnapins</span></span>

## <a name="short-description"></a><span data-ttu-id="ffdaf-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ffdaf-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="ffdaf-106">Beskriver snapin-moduler för Windows PowerShell och visar hur du använder och hanterar dem.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-106">Describes  Windows PowerShell snap-ins and shows how to use and manage them.</span></span>

## <a name="long-description"></a><span data-ttu-id="ffdaf-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ffdaf-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="ffdaf-108">En Windows PowerShell-snapin-modul är en Microsoft .NET Ramverks sammansättning som innehåller Windows PowerShell-leverantörer och- \/ cmdletar.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-108">A Windows PowerShell snap-in is a Microsoft .NET Framework assembly that contains Windows PowerShell providers and\/or cmdlets.</span></span> <span data-ttu-id="ffdaf-109">Windows PowerShell innehåller en uppsättning grundläggande snapin-moduler, men du kan utöka kraften och värdet i Windows PowerShell genom att lägga till snapin-moduler som innehåller providrar och cmdlets som du skapar eller hämtar från andra.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-109">Windows PowerShell includes a set of basic snap-ins, but you can extend the power and value of Windows PowerShell by adding snap-ins that contain providers and cmdlets that you create or get from others.</span></span>

<span data-ttu-id="ffdaf-110">När du lägger till en snapin-modul är de cmdletar och providrar som den innehåller omedelbart tillgängliga för användning i den aktuella sessionen, men ändringen påverkar bara den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-110">When you add a snap-in, the cmdlets and providers that it contains are immediately available for use in the current session, but the change affects only the current session.</span></span>

<span data-ttu-id="ffdaf-111">Om du vill lägga till snapin-modulen i alla framtida sessioner sparar du den i din Windows PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-111">To add the snap-in to all future sessions, save it in your Windows PowerShell profile.</span></span> <span data-ttu-id="ffdaf-112">Du kan också använda Export-Console-cmdlet: en för att spara namn på snapin-modulen till en konsol fil och sedan använda den i framtida sessioner.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-112">You can also use the Export-Console cmdlet to save the snap-in names to a console file and then use it in future sessions.</span></span> <span data-ttu-id="ffdaf-113">Du kan till och med spara flera konsolfiler, var och en med en annan uppsättning snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-113">You can even save multiple console files, each with a different set of snap-ins.</span></span>

<span data-ttu-id="ffdaf-114">Obs! snapin-moduler för Windows PowerShell (PSSnapins) är tillgängliga för användning i Windows PowerShell 3,0 och Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-114">NOTE: Windows PowerShell snap-ins (PSSnapins) are available for use in Windows PowerShell 3.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="ffdaf-115">De kan vara ändrade eller inte tillgängliga i senare versioner.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-115">They might be altered or unavailable in subsequent versions.</span></span> <span data-ttu-id="ffdaf-116">Använd moduler för att paketera Windows PowerShell-cmdlets och providers.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-116">To package Windows PowerShell cmdlets and providers, use modules.</span></span> <span data-ttu-id="ffdaf-117">Information om hur du skapar moduler och konverterar snapin-moduler till moduler finns i [skriva en Windows PowerShell-modul](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span><span class="sxs-lookup"><span data-stu-id="ffdaf-117">For information about creating modules and converting snap-ins to modules, see [Writing a Windows PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

### <a name="finding-snap-ins"></a><span data-ttu-id="ffdaf-118">HITTA SNAPIN-MODULER</span><span class="sxs-lookup"><span data-stu-id="ffdaf-118">FINDING SNAP-INS</span></span>

<span data-ttu-id="ffdaf-119">Om du vill hämta en lista över Windows PowerShell-snapin-modulerna på datorn skriver du:</span><span class="sxs-lookup"><span data-stu-id="ffdaf-119">To get a list of the  Windows PowerShell snap-ins on your computer, type:</span></span>

```powershell
Get-PSSnapin
```

<span data-ttu-id="ffdaf-120">Om du vill hämta snapin-modulen för varje Windows PowerShell-Provider skriver du:</span><span class="sxs-lookup"><span data-stu-id="ffdaf-120">To get the snap-in for each  Windows PowerShell provider, type:</span></span>

```powershell
Get-PSProvider | Format-List name, pssnapin
```

<span data-ttu-id="ffdaf-121">Om du vill hämta en lista över cmdletarna i en Windows PowerShell-snapin-modul skriver du:</span><span class="sxs-lookup"><span data-stu-id="ffdaf-121">To get a list of the cmdlets in a  Windows PowerShell snap-in, type:</span></span>

```powershell
Get-Command -Module <snap-in_name>
```

### <a name="installing-a-snap-in"></a><span data-ttu-id="ffdaf-122">INSTALLERA EN SNAPIN-MODUL</span><span class="sxs-lookup"><span data-stu-id="ffdaf-122">INSTALLING A SNAP-IN</span></span>

<span data-ttu-id="ffdaf-123">De inbyggda snapin-modulerna är registrerade i systemet och läggs till i Standardsessionen när du startar Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-123">The built-in snap-ins are registered in the system and added to the default session when you start Windows PowerShell.</span></span> <span data-ttu-id="ffdaf-124">Du måste dock registrera snapin-moduler som du skapar eller hämtar från andra och sedan lägga till snapin-modulerna i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-124">However, you have to register snap-ins that you create or obtain from others and then add the snap-ins to your session.</span></span>

### <a name="registering-a-snap-in"></a><span data-ttu-id="ffdaf-125">REGISTRERA EN SNAPIN-MODUL</span><span class="sxs-lookup"><span data-stu-id="ffdaf-125">REGISTERING A SNAP-IN</span></span>

<span data-ttu-id="ffdaf-126">En Windows PowerShell-snapin-modul är ett program som skrivits i ett .NET Framework språk som är kompilerat i en. dll-fil.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-126">A Windows PowerShell snap-in is a program written in a .NET Framework language that is compiled into a .dll file.</span></span> <span data-ttu-id="ffdaf-127">Om du vill använda providers och cmdlets i en snapin-modul måste du först registrera snapin-modulen (Lägg till i registret).</span><span class="sxs-lookup"><span data-stu-id="ffdaf-127">To use the providers and cmdlets in a snap-in, you must first register the snap-in (add it to the registry).</span></span>

<span data-ttu-id="ffdaf-128">De flesta snapin-moduler innehåller ett installations program (en. exe-eller. msi-fil) som registrerar DLL-filen åt dig.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-128">Most snap-ins include an installation program (an .exe or .msi file) that registers the .dll file for you.</span></span> <span data-ttu-id="ffdaf-129">Men om du får en snapin-modul som en. dll-fil kan du registrera den på systemet.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-129">However, if you receive a snap-in as a .dll file, you can register it on your system.</span></span> <span data-ttu-id="ffdaf-130">Mer information finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="ffdaf-130">For more information, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

<span data-ttu-id="ffdaf-131">Om du vill hämta alla registrerade snapin-moduler i systemet eller kontrol lera att en snapin-modul är registrerad, skriver du:</span><span class="sxs-lookup"><span data-stu-id="ffdaf-131">To get all the registered snap-ins on your system or to verify that a snap-in is registered, type:</span></span>

```powershell
Get-PSSnapin -registered
```

### <a name="adding-the-snap-in-to-the-current-session"></a><span data-ttu-id="ffdaf-132">LÄGGA TILL SNAPIN-MODULEN I DEN AKTUELLA SESSIONEN</span><span class="sxs-lookup"><span data-stu-id="ffdaf-132">ADDING THE SNAP-IN TO THE CURRENT SESSION</span></span>

<span data-ttu-id="ffdaf-133">Använd Add-PsSnapin-cmdleten om du vill lägga till en registrerad snapin-modul till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-133">To add a registered snap-in to the current session, use the Add-PsSnapin cmdlet.</span></span> <span data-ttu-id="ffdaf-134">Om du till exempel vill lägga till Microsoft SQL Server snapin-modulen till sessionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="ffdaf-134">For example, to add the Microsoft SQL Server snap-in to the session, type:</span></span>

```powershell
Add-PSSnapin sql
```

<span data-ttu-id="ffdaf-135">När kommandot har slutförts är leverantörerna och cmdletarna i snapin-modulen tillgängliga i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-135">After the command is completed, the providers and cmdlets in the snap-in are available in the session.</span></span> <span data-ttu-id="ffdaf-136">De är dock bara tillgängliga i den aktuella sessionen om du inte sparar dem.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-136">However, they are available only in the current session unless you save them.</span></span>

### <a name="saving-the-snap-ins"></a><span data-ttu-id="ffdaf-137">SPARA SNAPIN-MODULERNA</span><span class="sxs-lookup"><span data-stu-id="ffdaf-137">SAVING THE SNAP-INS</span></span>

<span data-ttu-id="ffdaf-138">Om du vill använda en snapin-modul i framtida Windows PowerShell-sessioner lägger du till kommandot Add-PsSnapin i Windows PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-138">To use a snap-in in future Windows PowerShell sessions, add the Add-PsSnapin command to your Windows PowerShell profile.</span></span> <span data-ttu-id="ffdaf-139">Du kan också exportera namnet på snapin-modulen till en konsol fil.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-139">Or, export the snap-in names to a console file.</span></span>

<span data-ttu-id="ffdaf-140">Om du lägger till kommandot Add-PSSnapin i din profil, är det tillgängligt i alla framtida Windows PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-140">If you add the Add-PSSnapin command to your profile, it is available in all future Windows PowerShell sessions.</span></span> <span data-ttu-id="ffdaf-141">Om du exporterar namnen på snapin-modulerna i din session kan du bara använda export filen när du behöver snapin-modulerna.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-141">If you export the names of the snap-ins in your session, you can use the export file only when you need the snap-ins.</span></span>

<span data-ttu-id="ffdaf-142">Om du vill lägga till kommandot Add-PsSnapin till din Windows PowerShell-profil öppnar du din profil, klistrar in eller skriver kommandot och sparar sedan profilen.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-142">To add the Add-PsSnapin command to your Windows PowerShell profile, open your profile, paste or type the command, and then save the profile.</span></span> <span data-ttu-id="ffdaf-143">Mer information finns i about_Profiles.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-143">For more information, see about_Profiles.</span></span>

<span data-ttu-id="ffdaf-144">Använd Export-Console-cmdleten för att spara snapin-modulerna från en session i konsol filen (. psc1).</span><span class="sxs-lookup"><span data-stu-id="ffdaf-144">To save the snap-ins from a session in console file (.psc1), use the Export-Console cmdlet.</span></span> <span data-ttu-id="ffdaf-145">Om du till exempel vill spara snapin-modulerna i den aktuella sessionen till filen NewConsole. psc1 i den aktuella katalogen skriver du:</span><span class="sxs-lookup"><span data-stu-id="ffdaf-145">For example, to save the snap-ins in the current session configuration to the NewConsole.psc1 file in the current directory, type:</span></span>

```powershell
Export-Console NewConsole
```

<span data-ttu-id="ffdaf-146">Mer information finns i export-Console.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-146">For more information, see Export-Console.</span></span>

### <a name="opening-windows-powershell-with-a-console-file"></a><span data-ttu-id="ffdaf-147">ÖPPNA WINDOWS POWERSHELL MED EN KONSOL FIL</span><span class="sxs-lookup"><span data-stu-id="ffdaf-147">OPENING WINDOWS POWERSHELL WITH A CONSOLE FILE</span></span>

<span data-ttu-id="ffdaf-148">Om du vill använda en konsol fil som innehåller snapin-modulen startar du Windows PowerShell (PowerShell.exe) från kommando tolken i Cmd.exe eller i en annan Windows PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-148">To use a console file that includes the snap-in, start Windows PowerShell (PowerShell.exe) from the command prompt in Cmd.exe or in another Windows PowerShell session.</span></span> <span data-ttu-id="ffdaf-149">Använd parametern PsConsoleFile för att ange konsol filen som innehåller snapin-modulen.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-149">Use the PsConsoleFile parameter to specify the console file that includes the snap-in.</span></span> <span data-ttu-id="ffdaf-150">Följande kommando startar till exempel Windows PowerShell med konsol filen NewConsole. psc1:</span><span class="sxs-lookup"><span data-stu-id="ffdaf-150">For example, the following command starts Windows PowerShell with the NewConsole.psc1 console file:</span></span>

```powershell
PowerShell.exe -psconsolefile NewConsole.psc1
```

<span data-ttu-id="ffdaf-151">Providers och cmdlets i snapin-modulen är nu tillgängliga för användning i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-151">The providers and cmdlets in the snapin are now available for use in the session.</span></span>

### <a name="removing-a-snap-in"></a><span data-ttu-id="ffdaf-152">TA BORT EN SNAPIN-MODUL</span><span class="sxs-lookup"><span data-stu-id="ffdaf-152">REMOVING A SNAP-IN</span></span>

<span data-ttu-id="ffdaf-153">Använd Remove-PsSnapin-cmdleten om du vill ta bort en Windows PowerShell-snapin-modul från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-153">To remove a Windows PowerShell snap-in from the current session, use the Remove-PsSnapin cmdlet.</span></span> <span data-ttu-id="ffdaf-154">Om du till exempel vill ta bort snapin-modulen SQL Server från den aktuella sessionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="ffdaf-154">For example, to remove the SQL Server snap-in from the current session, type:</span></span>

```powershell
Remove-PSSnapin sql
```

<span data-ttu-id="ffdaf-155">Denna cmdlet tar bort snapin-modulen från sessionen.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-155">This cmdlet removes the snap-in from the session.</span></span> <span data-ttu-id="ffdaf-156">Snapin-modulen är fortfarande inläst, men de providers och cmdlets som stöds inte längre är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-156">The snap-in is still loaded, but the providers and cmdlets that it supports are no longer available.</span></span>

### <a name="built-in-commands"></a><span data-ttu-id="ffdaf-157">INBYGGDA KOMMANDON</span><span class="sxs-lookup"><span data-stu-id="ffdaf-157">BUILT-IN COMMANDS</span></span>

<span data-ttu-id="ffdaf-158">I Windows PowerShell 2,0 och i äldre värd program i Windows PowerShell 3,0 och senare, paketeras de inbyggda kommandon som installeras med Windows PowerShell i snapin-moduler som läggs till automatiskt till alla Windows PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-158">In Windows PowerShell 2.0 and in older-style host programs in Windows PowerShell 3.0 and later, the built-in commands that are installed with Windows PowerShell are packaged in snap-ins that are added automatically to every Windows PowerShell session.</span></span>

<span data-ttu-id="ffdaf-159">Från och med Windows PowerShell 3,0 i nyare typ värd program – de som startar sessioner med hjälp av metoden InitialSessionState. CreateDefault2 – de inbyggda kommandona paketeras i moduler.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-159">Beginning in Windows PowerShell 3.0, in newer-style host programs -- those that start sessions by using the InitialSessionState.CreateDefault2 method -- the built-in commands are packaged in modules.</span></span> <span data-ttu-id="ffdaf-160">Undantaget är Microsoft. PowerShell. Core, som alltid visas som en snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-160">The exception is Microsoft.PowerShell.Core, which always appears as a snap-in.</span></span> <span data-ttu-id="ffdaf-161">Snapin-modulen Core ingår i varje session som standard.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-161">The Core snap-in is included in every session by default.</span></span> <span data-ttu-id="ffdaf-162">De inbyggda modulerna läses in automatiskt vid första användning.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-162">The built-in modules are loaded automatically on first-use.</span></span>

<span data-ttu-id="ffdaf-163">Obs! fjärrsessioner, inklusive sessioner som startas med hjälp av New-PSSession-cmdleten, är äldre sessioner där de inbyggda kommandona paketeras i snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-163">NOTE: Remote sessions, including sessions that are started by using the New-PSSession cmdlet, are older-style sessions in which the built-in commands are packaged in snap-ins.</span></span>

<span data-ttu-id="ffdaf-164">Följande snapin-moduler (eller moduler) installeras med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-164">The following snap-ins (or modules) are installed with Windows PowerShell.</span></span>

- <span data-ttu-id="ffdaf-165">Microsoft. PowerShell. Core – innehåller providrar och cmdlets som används för att hantera de grundläggande funktionerna i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-165">Microsoft.PowerShell.Core - Contains providers and cmdlets used to manage the basic features of Windows PowerShell.</span></span> <span data-ttu-id="ffdaf-166">Det omfattar fil namns-, register-, alias-, miljö-, funktions-och variabel leverantörer och grundläggande cmdlets, till exempel Get-Help, Get-Command och get-History.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-166">It includes the FileSystem, Registry, Alias, Environment, Function, and Variable providers and basic cmdlets like Get-Help, Get-Command, and Get-History.</span></span>

- <span data-ttu-id="ffdaf-167">Microsoft. PowerShell. Host-innehåller cmdletar som används av Windows PowerShell-värden, till exempel Start-Transcript och stopp-avskrift.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-167">Microsoft.PowerShell.Host - Contains cmdlets used by the Windows PowerShell host, such as Start-Transcript and Stop-Transcript.</span></span>

- <span data-ttu-id="ffdaf-168">Microsoft. PowerShell. Management – innehåller cmdlets, till exempel Get-Service och Get-ChildItem som används för att hantera Windows-baserade funktioner.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-168">Microsoft.PowerShell.Management - Contains cmdlets such as Get-Service and Get-ChildItem that are used to manage Windows-based features.</span></span>

- <span data-ttu-id="ffdaf-169">Microsoft. PowerShell. Security – innehåller den certifikat leverantör och de cmdletar som används för att hantera Windows PowerShell-säkerhet, till exempel get-ACL, get-AuthenticodeSignature och ConvertTo-SecureString.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-169">Microsoft.PowerShell.Security - Contains the Certificate provider and cmdlets used to manage Windows PowerShell security, such as Get-Acl, Get-AuthenticodeSignature, and ConvertTo-SecureString.</span></span>

- <span data-ttu-id="ffdaf-170">Microsoft. PowerShell. Utility – innehåller cmdletar som används för att manipulera objekt och data, till exempel Get-Member, Write-Host och format-List.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-170">Microsoft.PowerShell.Utility - Contains cmdlets used to manipulate objects and data, such as Get-Member, Write-Host, and Format-List.</span></span>

- <span data-ttu-id="ffdaf-171">Microsoft. WSMan. Management – innehåller WSMan-providern och cmdletar som hanterar tjänsten Windows Remote Management, till exempel Connect-WSMan och enable-WSManCredSSP.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-171">Microsoft.WSMan.Management - Contains the WSMan provider and cmdlets that manage the Windows Remote Management service, such as Connect-WSMan and Enable-WSManCredSSP.</span></span>

## <a name="logging-snap-in-events"></a><span data-ttu-id="ffdaf-172">LOGGA SNAPIN-HÄNDELSER</span><span class="sxs-lookup"><span data-stu-id="ffdaf-172">LOGGING SNAP-IN EVENTS</span></span>

<span data-ttu-id="ffdaf-173">Från och med Windows PowerShell 3,0 kan du registrera körnings händelser för cmdletarna i Windows PowerShell-moduler och snapin-moduler genom att ange egenskapen LogPipelineExecutionDetails för moduler och snapin-moduler till sant.</span><span class="sxs-lookup"><span data-stu-id="ffdaf-173">Beginning in Windows PowerShell 3.0, you can record execution events for the cmdlets in Windows PowerShell modules and snap-ins by setting the LogPipelineExecutionDetails property of modules and snap-ins to TRUE.</span></span> <span data-ttu-id="ffdaf-174">Mer information finns i [about_EventLogs](about_EventLogs.md).</span><span class="sxs-lookup"><span data-stu-id="ffdaf-174">For more information, see [about_EventLogs](about_EventLogs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ffdaf-175">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="ffdaf-175">SEE ALSO</span></span>

[<span data-ttu-id="ffdaf-176">Add-PsSnapin</span><span class="sxs-lookup"><span data-stu-id="ffdaf-176">Add-PsSnapin</span></span>](xref:Microsoft.PowerShell.Core.Add-PSSnapin)

[<span data-ttu-id="ffdaf-177">Get-PsSnapin</span><span class="sxs-lookup"><span data-stu-id="ffdaf-177">Get-PsSnapin</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSnapin)

[<span data-ttu-id="ffdaf-178">Remove-PsSnapin</span><span class="sxs-lookup"><span data-stu-id="ffdaf-178">Remove-PsSnapin</span></span>](xref:Microsoft.PowerShell.Core.Remove-PSSnapin)

[<span data-ttu-id="ffdaf-179">Exportera-konsol</span><span class="sxs-lookup"><span data-stu-id="ffdaf-179">Export-Console</span></span>](xref:Microsoft.PowerShell.Core.Export-Console)

[<span data-ttu-id="ffdaf-180">Get-Command</span><span class="sxs-lookup"><span data-stu-id="ffdaf-180">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)

[<span data-ttu-id="ffdaf-181">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="ffdaf-181">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="ffdaf-182">about_Modules</span><span class="sxs-lookup"><span data-stu-id="ffdaf-182">about_Modules</span></span>](about_Modules.md)

## <a name="keywords"></a><span data-ttu-id="ffdaf-183">RESERVERADE</span><span class="sxs-lookup"><span data-stu-id="ffdaf-183">KEYWORDS</span></span>

<span data-ttu-id="ffdaf-184">about_Snapins, about_Snap_ins, about_Snap-moduler</span><span class="sxs-lookup"><span data-stu-id="ffdaf-184">about_Snapins, about_Snap_ins, about_Snap-ins</span></span>
