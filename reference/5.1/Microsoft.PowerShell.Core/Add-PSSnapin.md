---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-PSSnapin
ms.openlocfilehash: a21c2974fd66a9b02929752ae487c8995579b8a7
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388832"
---
# <span data-ttu-id="2149a-103">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="2149a-103">Add-PSSnapin</span></span>

## <span data-ttu-id="2149a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2149a-104">SYNOPSIS</span></span>
<span data-ttu-id="2149a-105">Lägger till en eller flera Windows PowerShell-snapin-moduler i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="2149a-105">Adds one or more Windows PowerShell snap-ins to the current session.</span></span>

## <span data-ttu-id="2149a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2149a-106">SYNTAX</span></span>

```
Add-PSSnapin [-Name] <String[]> [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="2149a-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2149a-107">DESCRIPTION</span></span>

<span data-ttu-id="2149a-108">`Add-PSSnapin`Cmdleten lägger till registrerade Windows PowerShell-snapin-moduler i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="2149a-108">The `Add-PSSnapin` cmdlet adds registered Windows PowerShell snap-ins to the current session.</span></span> <span data-ttu-id="2149a-109">När snapin-modulerna har lagts till kan du använda de cmdlets och providers som snapin-modulerna har stöd för i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="2149a-109">After the snap-ins are added, you can use the cmdlets and providers that the snap-ins support in the current session.</span></span>

<span data-ttu-id="2149a-110">Lägg till ett `Add-PSSnapin` kommando i Windows PowerShell-profilen för att lägga till snapin-modulen i alla framtida Windows PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="2149a-110">To add the snap-in to all future Windows PowerShell sessions, add an `Add-PSSnapin` command to your Windows PowerShell profile.</span></span> <span data-ttu-id="2149a-111">Mer information finns i [about_Profiles](about/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="2149a-111">For more information, see [about_Profiles](about/about_Profiles.md).</span></span>

<span data-ttu-id="2149a-112">Från och med Windows PowerShell 3,0 paketeras de grundläggande kommandon som ingår i Windows PowerShell i moduler.</span><span class="sxs-lookup"><span data-stu-id="2149a-112">Beginning in Windows PowerShell 3.0, the core commands that are included in Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="2149a-113">Undantaget är **Microsoft. PowerShell. Core** , som är en snapin-modul (PSSnapin).</span><span class="sxs-lookup"><span data-stu-id="2149a-113">The exception is **Microsoft.PowerShell.Core** , which is a snap-in (PSSnapin).</span></span>
<span data-ttu-id="2149a-114">Som standard läggs bara snapin-modulen **Microsoft. PowerShell. Core** till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="2149a-114">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span> <span data-ttu-id="2149a-115">Moduler importeras automatiskt vid första användningen och du kan använda Import-Module-cmdlet för att importera dem.</span><span class="sxs-lookup"><span data-stu-id="2149a-115">Modules are imported automatically on first use and you can use the Import-Module cmdlet to import them.</span></span>

## <span data-ttu-id="2149a-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2149a-116">EXAMPLES</span></span>

### <span data-ttu-id="2149a-117">Exempel 1: Lägg till snapin-moduler</span><span class="sxs-lookup"><span data-stu-id="2149a-117">Example 1: Add snap-ins</span></span>

```powershell
PS C:\> Add-PSSnapIn -Name Microsoft.Exchange, Microsoft.Windows.AD
```

<span data-ttu-id="2149a-118">Detta kommando lägger till Microsoft Exchange och Active Directory snapin-moduler till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="2149a-118">This command adds the Microsoft Exchange and Active Directory snap-ins to the current session.</span></span>

### <span data-ttu-id="2149a-119">Exempel 2: Lägg till alla registrerade snapin-moduler</span><span class="sxs-lookup"><span data-stu-id="2149a-119">Example 2: Add all the registered snap-ins</span></span>

```powershell
PS C:\> Get-PSSnapin -Registered | Add-PSSnapin -Passthru
```

<span data-ttu-id="2149a-120">Med det här kommandot läggs alla registrerade Windows PowerShell-snapin-moduler till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="2149a-120">This command adds all of the registered Windows PowerShell snap-ins to the session.</span></span> <span data-ttu-id="2149a-121">Den använder Get-PSSnapin-cmdlet med den **registrerade** parametern för att hämta objekt som representerar var och en av de registrerade snapin-modulerna. Pipeline-operatorn (|) skickar resultatet till `Add-PSSnapin` , som lägger till dem i sessionen.</span><span class="sxs-lookup"><span data-stu-id="2149a-121">It uses the Get-PSSnapin cmdlet with the **Registered** parameter to get objects representing each of the registered snap-ins. The pipeline operator (|) passes the result to `Add-PSSnapin`, which adds them to the session.</span></span> <span data-ttu-id="2149a-122">Parametern **Passthru** returnerar objekt som representerar var och en av de tillagda snapin-modulerna.</span><span class="sxs-lookup"><span data-stu-id="2149a-122">The **PassThru** parameter returns objects that represent each of the added snap-ins.</span></span>

### <span data-ttu-id="2149a-123">Exempel 3: registrera en snapin-modul och Lägg till den</span><span class="sxs-lookup"><span data-stu-id="2149a-123">Example 3: Register a snap-in and add it</span></span>

<span data-ttu-id="2149a-124">Det första kommandot hämtar snapin-moduler som har lagts till i den aktuella sessionen och innehåller snapin-moduler som installeras med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2149a-124">The first command gets snap-ins that have been added to the current session that include the snap-ins that are installed with Windows PowerShell.</span></span> <span data-ttu-id="2149a-125">I det här exemplet returneras inte ManagementFeatures.</span><span class="sxs-lookup"><span data-stu-id="2149a-125">In this example, ManagementFeatures is not returned.</span></span> <span data-ttu-id="2149a-126">Detta anger att den inte har lagts till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="2149a-126">This indicates that it has not been added to the session.</span></span>

<span data-ttu-id="2149a-127">Det andra kommandot hämtar snapin-moduler som har registrerats i systemet, inklusive de som redan har lagts till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="2149a-127">The second command gets snap-ins that have been registered on your system, which includes those that have already been added to the session.</span></span> <span data-ttu-id="2149a-128">Den omfattar inte snapin-modulerna som installeras med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2149a-128">It does not include the snap-ins that are installed with Windows PowerShell.</span></span> <span data-ttu-id="2149a-129">I det här fallet returnerar kommandot inga snapin-moduler. Detta anger att snapin-modulen ManagementFeatures inte har registrerats i systemet.</span><span class="sxs-lookup"><span data-stu-id="2149a-129">In this case, the command does not return any snap-ins. This indicates that the ManagementFeatures snapin has not been registered on the system.</span></span>

<span data-ttu-id="2149a-130">Det tredje kommandot skapar ett alias, InstallUtil, för sökvägen till InstallUtil-verktyget i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2149a-130">The third command creates an alias, installutil, for the path of the InstallUtil tool in .NET Framework.</span></span>

<span data-ttu-id="2149a-131">Det fjärde kommandot använder verktyget InstallUtil för att registrera snapin-modulen.</span><span class="sxs-lookup"><span data-stu-id="2149a-131">The fourth command uses the InstallUtil tool to register the snap-in.</span></span> <span data-ttu-id="2149a-132">Kommandot anger sökvägen till ManagementCmdlets.dll, fil namnet eller modulnamnet för snapin-modulen.</span><span class="sxs-lookup"><span data-stu-id="2149a-132">The command specifies the path of ManagementCmdlets.dll, the filename or module name of the snap-in.</span></span>

<span data-ttu-id="2149a-133">Det femte kommandot är samma som det andra kommandot.</span><span class="sxs-lookup"><span data-stu-id="2149a-133">The fifth command is the same as the second command.</span></span> <span data-ttu-id="2149a-134">Den här gången använder du det för att kontrol lera att snapin-modulen ManagementCmdlets är registrerad.</span><span class="sxs-lookup"><span data-stu-id="2149a-134">This time, you use it to verify that the ManagementCmdlets snap-in is registered.</span></span>

<span data-ttu-id="2149a-135">Det sjätte kommandot använder `Add-PSSnapin` cmdleten för att lägga till snapin-modulen ManagementFeatures i sessionen.</span><span class="sxs-lookup"><span data-stu-id="2149a-135">The sixth command uses the `Add-PSSnapin` cmdlet to add the ManagementFeatures snap-in to the session.</span></span> <span data-ttu-id="2149a-136">Den anger namnet på snapin-modulen, ManagementFeatures, inte fil namnet.</span><span class="sxs-lookup"><span data-stu-id="2149a-136">It specifies the name of the snap-in, ManagementFeatures, not the file name.</span></span>

<span data-ttu-id="2149a-137">För att verifiera att snapin-modulen har lagts till i sessionen använder det sjunde kommandot parametern **module** i Get-Command-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2149a-137">To verify that the snap-in is added to the session, the seventh command uses the **Module** parameter of the Get-Command cmdlet.</span></span> <span data-ttu-id="2149a-138">Den visar de objekt som har lagts till i sessionen av en snapin-modul eller modul.</span><span class="sxs-lookup"><span data-stu-id="2149a-138">It displays the items that were added to the session by a snap-in or module.</span></span>

<span data-ttu-id="2149a-139">Du kan också använda egenskapen **PSSnapin** för objektet som `Get-Command` cmdleten returnerar för att hitta snapin-modulen eller modulen där en cmdlet kommer.</span><span class="sxs-lookup"><span data-stu-id="2149a-139">You can also use the **PSSnapin** property of the object that the `Get-Command` cmdlet returns to find the snap-in or module in which a cmdlet originated.</span></span> <span data-ttu-id="2149a-140">Det åttonde kommandot använder punkt notation för att hitta värdet för egenskapen PSSnapin i Set-Alias-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2149a-140">The eighth command uses dot notation to find the value of the PSSnapin property of the Set-Alias cmdlet.</span></span>

```powershell
PS C:\> Get-PSSnapin
PS C:\> Get-PSSnapin -Registered
PS C:\> Set-Alias installutil $env:windir\Microsoft.NET\Framework\v2.0.50727\installutil.exe
PS C:\> installutil C:\Dev\Management\ManagementCmdlets.dll
PS C:\> Get-PSSnapin -Registered
PS C:\> add-pssnapin ManagementFeatures
PS C:\> Get-Command -Module ManagementFeatures
PS C:\> (Get-Command Set-Alias).pssnapin
```

<span data-ttu-id="2149a-141">Det här exemplet visar hur du registrerar en snapin-modul på systemet och sedan lägger till den i sessionen.</span><span class="sxs-lookup"><span data-stu-id="2149a-141">This example demonstrates the process of registering a snap-in on your system and then adding it to your session.</span></span> <span data-ttu-id="2149a-142">Den använder ManagementFeatures, en fiktiv snapin-modul som implementerats i en fil med namnet ManagementCmdlets.dll.</span><span class="sxs-lookup"><span data-stu-id="2149a-142">It uses ManagementFeatures, a fictitious snap-in implemented in a file that is named ManagementCmdlets.dll.</span></span>

## <span data-ttu-id="2149a-143">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2149a-143">PARAMETERS</span></span>

### <span data-ttu-id="2149a-144">-Name</span><span class="sxs-lookup"><span data-stu-id="2149a-144">-Name</span></span>

<span data-ttu-id="2149a-145">Anger namnet på snapin-modulen.</span><span class="sxs-lookup"><span data-stu-id="2149a-145">Specifies the name of the snap-in.</span></span> <span data-ttu-id="2149a-146">Detta är namnet, inte AssemblyName eller modulnamn.</span><span class="sxs-lookup"><span data-stu-id="2149a-146">This is the Name, not the AssemblyName or ModuleName.</span></span> <span data-ttu-id="2149a-147">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="2149a-147">Wildcards are permitted.</span></span>

<span data-ttu-id="2149a-148">Om du vill hitta namnen på de registrerade snapin-modulerna i systemet skriver du `Get-PSSnapin -Registered` .</span><span class="sxs-lookup"><span data-stu-id="2149a-148">To find the names of the registered snap-ins on your system, type `Get-PSSnapin -Registered`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="2149a-149">– PassThru</span><span class="sxs-lookup"><span data-stu-id="2149a-149">-PassThru</span></span>

<span data-ttu-id="2149a-150">Anger att denna cmdlet returnerar ett objekt som representerar varje tillagd snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="2149a-150">Indicates that this cmdlet returns an object that represents each added snap-in.</span></span> <span data-ttu-id="2149a-151">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="2149a-151">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="2149a-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2149a-152">CommonParameters</span></span>

<span data-ttu-id="2149a-153">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2149a-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2149a-154">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2149a-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2149a-155">INDATA</span><span class="sxs-lookup"><span data-stu-id="2149a-155">INPUTS</span></span>

### <span data-ttu-id="2149a-156">Inget</span><span class="sxs-lookup"><span data-stu-id="2149a-156">None</span></span>
<span data-ttu-id="2149a-157">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2149a-157">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="2149a-158">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2149a-158">OUTPUTS</span></span>

### <span data-ttu-id="2149a-159">Ingen eller system. Management. Automation. PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="2149a-159">None or System.Management.Automation.PSSnapInInfo</span></span>

<span data-ttu-id="2149a-160">Denna cmdlet returnerar ett PSSnapInInfo-objekt som representerar snapin-modulen om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="2149a-160">This cmdlet returns a PSSnapInInfo object that represents the snap-in if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="2149a-161">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="2149a-161">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2149a-162">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2149a-162">NOTES</span></span>

- <span data-ttu-id="2149a-163">Från och med Windows PowerShell 3,0 paketeras de grundläggande kommandon som installeras med Windows PowerShell i moduler.</span><span class="sxs-lookup"><span data-stu-id="2149a-163">Beginning in Windows PowerShell 3.0, the core commands that are installed with Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="2149a-164">I Windows PowerShell 2,0 och i värd program som skapar äldre sessioner i senare versioner av Windows PowerShell är huvud kommandona förpackade i snapin-moduler (PSSnapins).</span><span class="sxs-lookup"><span data-stu-id="2149a-164">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of Windows PowerShell, the core commands are packaged in snap-ins (PSSnapins).</span></span> <span data-ttu-id="2149a-165">Undantaget är **Microsoft. PowerShell. Core** , som alltid är en snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="2149a-165">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="2149a-166">Fjärrsessioner, till exempel de som startas av New-PSSession-cmdleten, är äldre sessioner som inkluderar grundläggande snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="2149a-166">Also, remote sessions, such as those started by the New-PSSession cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="2149a-167">Information om **CreateDefault2** -metoden som skapar nyare sessioner med Core-moduler finns i CreateDefault2- [metoden](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2).</span><span class="sxs-lookup"><span data-stu-id="2149a-167">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2).</span></span>

- <span data-ttu-id="2149a-168">Mer information om snapin-moduler finns i [about_PSSnapins](About/about_PSSnapins.md) och [hur du skapar en Windows PowerShell-snapin-modul](/powershell/scripting/developer/cmdlet/how-to-create-a-windows-powershell-snap-in).</span><span class="sxs-lookup"><span data-stu-id="2149a-168">For more information about snap-ins, see [about_PSSnapins](About/about_PSSnapins.md) and [How to Create a Windows PowerShell Snap-in](/powershell/scripting/developer/cmdlet/how-to-create-a-windows-powershell-snap-in).</span></span>
- <span data-ttu-id="2149a-169">`Add-PSSnapin` lägger bara till snapin-modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="2149a-169">`Add-PSSnapin` adds the snap-in only to the current session.</span></span> <span data-ttu-id="2149a-170">Lägg till snapin-modulen till alla Windows PowerShell-sessioner genom att lägga till den i Windows PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="2149a-170">To add the snap-in to all Windows PowerShell sessions, add it to your Windows PowerShell profile.</span></span> <span data-ttu-id="2149a-171">Mer information finns i about_Profiles.</span><span class="sxs-lookup"><span data-stu-id="2149a-171">For more information, see about_Profiles.</span></span>
- <span data-ttu-id="2149a-172">Du kan lägga till en snapin-modul som har registrerats med installations verktyget för Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2149a-172">You can add any snap-in that has been registered using the Microsoft .NET Framework install utility.</span></span> <span data-ttu-id="2149a-173">Mer information finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="2149a-173">For more information, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>
- <span data-ttu-id="2149a-174">Om du vill hämta en lista över snapin-moduler som är registrerade på datorn skriver du `Get-PSSnapin -Registered` .</span><span class="sxs-lookup"><span data-stu-id="2149a-174">To get a list of snap-ins that are registered on your computer, type `Get-PSSnapin -Registered`.</span></span>
- <span data-ttu-id="2149a-175">Innan du lägger till en snapin-modul `Add-PSSnapin` kontrollerar du vilken version av snapin-modulen som ska användas för att kontrol lera att den är kompatibel med den aktuella versionen av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2149a-175">Before adding a snap-in, `Add-PSSnapin` checks the version of the snap-in to verify that it is compatible with the current version of Windows PowerShell.</span></span> <span data-ttu-id="2149a-176">Om snapin-modulen inte uppfyller versions kontrollen rapporterar Windows PowerShell ett fel.</span><span class="sxs-lookup"><span data-stu-id="2149a-176">If the snap-in fails the version check, Windows PowerShell reports an error.</span></span>

## <span data-ttu-id="2149a-177">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2149a-177">RELATED LINKS</span></span>

[<span data-ttu-id="2149a-178">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="2149a-178">Get-PSSnapin</span></span>](Get-PSSnapin.md)

[<span data-ttu-id="2149a-179">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="2149a-179">Remove-PSSnapin</span></span>](Remove-PSSnapin.md)
