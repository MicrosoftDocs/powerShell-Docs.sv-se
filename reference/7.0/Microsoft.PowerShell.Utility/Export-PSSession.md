---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-PSSession
ms.openlocfilehash: ff1b709b363684e27a1f4eb8fdeada2d5ae1d588
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262892"
---
# <span data-ttu-id="877ef-103">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="877ef-103">Export-PSSession</span></span>

## <span data-ttu-id="877ef-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="877ef-104">SYNOPSIS</span></span>

<span data-ttu-id="877ef-105">Exporterar kommandon från en annan session och sparar dem i en PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="877ef-105">Exports commands from another session and saves them in a PowerShell module.</span></span>

## <span data-ttu-id="877ef-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="877ef-106">SYNTAX</span></span>

### <span data-ttu-id="877ef-107">Alla</span><span class="sxs-lookup"><span data-stu-id="877ef-107">All</span></span>

```
Export-PSSession [-OutputModule] <String> [-Force] [-Encoding <Encoding>]
 [[-CommandName] <String[]>] [-AllowClobber] [-ArgumentList <Object[]>]
 [-CommandType <CommandTypes>] [-Module <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-FormatTypeName] <String[]>] [-Certificate <X509Certificate2>] [-Session] <PSSession>
 [<CommonParameters>]
```

## <span data-ttu-id="877ef-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="877ef-108">DESCRIPTION</span></span>

<span data-ttu-id="877ef-109">`Export-PSSession`Cmdlet: en hämtar cmdlets, functions, alias och andra kommando typer från en annan PowerShell-session (PSSession) på en lokal eller fjärran sluten dator och sparar dem i en PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="877ef-109">The `Export-PSSession` cmdlet gets cmdlets, functions, aliases, and other command types from another PowerShell session (PSSession) on a local or remote computer and saves them in a PowerShell module.</span></span> <span data-ttu-id="877ef-110">Använd cmdleten om du vill lägga till kommandon från modulen till den aktuella sessionen `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="877ef-110">To add the commands from the module to the current session, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="877ef-111">Till skillnad `Import-PSSession` från, som importerar kommandon från en annan PSSession till den aktuella sessionen, `Export-PSSession` sparar kommandona i en modul.</span><span class="sxs-lookup"><span data-stu-id="877ef-111">Unlike `Import-PSSession`, which imports commands from another PSSession into the current session, `Export-PSSession` saves the commands in a module.</span></span> <span data-ttu-id="877ef-112">Kommandona importeras inte till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="877ef-112">The commands are not imported into the current session.</span></span>

<span data-ttu-id="877ef-113">Om du vill exportera kommandon använder du `New-PSSession` cmdleten för att skapa en PSSession som har de kommandon som du vill exportera.</span><span class="sxs-lookup"><span data-stu-id="877ef-113">To export commands, use the `New-PSSession` cmdlet to create a PSSession that has the commands that you want to export.</span></span> <span data-ttu-id="877ef-114">Använd sedan `Export-PSSession` cmdlet: en för att exportera kommandona.</span><span class="sxs-lookup"><span data-stu-id="877ef-114">Then use the `Export-PSSession` cmdlet to export the commands.</span></span>

<span data-ttu-id="877ef-115">För att förhindra kommando namns konflikter, är standardvärdet för `Export-PSSession` att exportera alla kommandon, förutom kommandon som finns i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="877ef-115">To prevent command name conflicts, the default for `Export-PSSession` is to export all commands, except for commands that exist in the current session.</span></span> <span data-ttu-id="877ef-116">Du kan använda parametern **commandname** för att ange vilka kommandon som ska exporteras.</span><span class="sxs-lookup"><span data-stu-id="877ef-116">You can use the **CommandName** parameter to specify the commands to export.</span></span>

<span data-ttu-id="877ef-117">`Export-PSSession`Cmdleten använder funktionen implicit fjärr kommunikation i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="877ef-117">The `Export-PSSession` cmdlet uses the implicit remoting feature of PowerShell.</span></span> <span data-ttu-id="877ef-118">När du importerar kommandon till den aktuella sessionen körs de implicit i den ursprungliga sessionen eller i en liknande session på den ursprungliga datorn.</span><span class="sxs-lookup"><span data-stu-id="877ef-118">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

## <span data-ttu-id="877ef-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="877ef-119">EXAMPLES</span></span>

### <span data-ttu-id="877ef-120">Exempel 1: exportera kommandon från en PSSession</span><span class="sxs-lookup"><span data-stu-id="877ef-120">Example 1: Export commands from a PSSession</span></span>

<span data-ttu-id="877ef-121">I det här exemplet skapas en ny PSSession från den lokala datorn till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="877ef-121">This example creates a new PSSession from the local computer to the Server01 computer.</span></span> <span data-ttu-id="877ef-122">Alla kommandon, förutom de som finns i den aktuella sessionen, exporteras till modulen med namnet Server01 på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="877ef-122">All of the commands, except those that exist in the current session, are exported to the module named Server01 on the local computer.</span></span> <span data-ttu-id="877ef-123">Exporten innehåller formaterings data för kommandona.</span><span class="sxs-lookup"><span data-stu-id="877ef-123">The export includes the formatting data for the commands.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01
Export-PSSession -Session $S -OutputModule Server01
```

<span data-ttu-id="877ef-124">`New-PSSession`Kommandot skapar en PSSession på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="877ef-124">The `New-PSSession` command creates a PSSession on the Server01 computer.</span></span> <span data-ttu-id="877ef-125">PSSession lagras i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="877ef-125">The PSSession is stored in the `$S` variable.</span></span> <span data-ttu-id="877ef-126">`Export-PSSession`Kommandot exporterar `$S` variabelns kommandon och formaterar data till Server01-modulen.</span><span class="sxs-lookup"><span data-stu-id="877ef-126">The `Export-PSSession` command exports the `$S` variable's commands and formatting data into the Server01 module.</span></span>

### <span data-ttu-id="877ef-127">Exempel 2: exportera get-och set-kommandona</span><span class="sxs-lookup"><span data-stu-id="877ef-127">Example 2: Export the Get and Set commands</span></span>

<span data-ttu-id="877ef-128">I det här exemplet exporteras alla `Get` `Set` kommandon från en server.</span><span class="sxs-lookup"><span data-stu-id="877ef-128">This example exports all of the `Get` and `Set` commands from a server.</span></span>

```powershell
$S = New-PSSession -ConnectionUri https://exchange.microsoft.com/mailbox -Credential exchangeadmin01@hotmail.com -Authentication Negotiate
Export-PSSession -Session $S -Module exch* -CommandName Get-*, Set-* -FormatTypeName * -OutputModule $PSHOME\Modules\Exchange -Encoding ASCII
```

<span data-ttu-id="877ef-129">Dessa kommandon exporterar `Get` och- `Set` kommandon från en Microsoft Exchange Server-snapin-modul på en fjärrdator till en Exchange-modul i `$PSHOME\Modules` katalogen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="877ef-129">These commands export the `Get` and `Set` commands from a Microsoft Exchange Server snap-in on a remote computer to an Exchange module in the `$PSHOME\Modules` directory on the local computer.</span></span>
<span data-ttu-id="877ef-130">Att placera modulen i `$PSHOME\Modules` katalogen gör den tillgänglig för alla användare av datorn.</span><span class="sxs-lookup"><span data-stu-id="877ef-130">Placing the module in the `$PSHOME\Modules` directory makes it accessible to all users of the computer.</span></span>

### <span data-ttu-id="877ef-131">Exempel 3: exportera kommandon från en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="877ef-131">Example 3: Export commands from a remote computer</span></span>

<span data-ttu-id="877ef-132">Det här exemplet exporterar cmdletar från en PSSession på en fjärrdator och sparar dem i en modul på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="877ef-132">This example exports cmdlets from a PSSession on a remote computer and saves them in a module on the local computer.</span></span> <span data-ttu-id="877ef-133">Cmdletarna från modulen läggs till i den aktuella sessionen så att de kan användas.</span><span class="sxs-lookup"><span data-stu-id="877ef-133">The cmdlets from the module are added to the current session so that they can be used.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01 -Credential Server01\User01
Export-PSSession -Session $S -OutputModule TestCmdlets -Type Cmdlet -CommandName *test* -FormatTypeName *
Remove-PSSession $S
Import-Module TestCmdlets
Get-Help Test*
Test-Files
```

<span data-ttu-id="877ef-134">`New-PSSession`Kommandot skapar en PSSession på Server01-datorn och sparar den i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="877ef-134">The `New-PSSession` command creates a PSSession on the Server01 computer and saves it in the `$S` variable.</span></span> <span data-ttu-id="877ef-135">`Export-PSSession`Kommandot exporterar de cmdletar vars namn börjar med test från PSSession i `$S` till TestCmdlets-modulen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="877ef-135">The `Export-PSSession` command exports the cmdlets whose names begin with Test from the PSSession in `$S` to the TestCmdlets module on the local computer.</span></span>

<span data-ttu-id="877ef-136">`Remove-PSSession`Cmdleten tar bort PSSession i `$S` från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="877ef-136">The `Remove-PSSession` cmdlet deletes the PSSession in `$S` from the current session.</span></span> <span data-ttu-id="877ef-137">Det här kommandot visar att PSSession inte behöver vara aktiv för att använda de kommandon som har importer ATS från sessionen.</span><span class="sxs-lookup"><span data-stu-id="877ef-137">This command shows that the PSSession need not be active to use the commands that were imported from the session.</span></span> <span data-ttu-id="877ef-138">`Import-Module`Cmdleten lägger till cmdletarna i TestCmdlets-modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="877ef-138">The `Import-Module` cmdlet adds the cmdlets in the TestCmdlets module to the current session.</span></span> <span data-ttu-id="877ef-139">Kommandot kan köras i alla sessioner när som helst.</span><span class="sxs-lookup"><span data-stu-id="877ef-139">The command can be run in any session at any time.</span></span>

<span data-ttu-id="877ef-140">`Get-Help`Cmdlet: en får hjälp med cmdletar vars namn börjar med test.</span><span class="sxs-lookup"><span data-stu-id="877ef-140">The `Get-Help` cmdlet gets help for cmdlets whose names begin with Test.</span></span> <span data-ttu-id="877ef-141">När du har lagt till kommandon i en modul i den aktuella sessionen kan du använda `Get-Help` `Get-Command` cmdletarna och för att lära dig mer om de importerade kommandona.</span><span class="sxs-lookup"><span data-stu-id="877ef-141">After the commands in a module are added to the current session, you can use the `Get-Help` and `Get-Command` cmdlets to learn about the imported commands.</span></span> <span data-ttu-id="877ef-142">`Test-Files`Cmdleten exporterades från Server01-datorn och lades till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="877ef-142">The `Test-Files` cmdlet was exported from the Server01 computer and added to the session.</span></span> <span data-ttu-id="877ef-143">`Test-Files`Cmdleten körs i en fjärran sluten session på den dator där kommandot importerades.</span><span class="sxs-lookup"><span data-stu-id="877ef-143">The `Test-Files` cmdlet runs in a remote session on the computer from which the command was imported.</span></span> <span data-ttu-id="877ef-144">PowerShell skapar en session med information som lagras i TestCmdlets-modulen.</span><span class="sxs-lookup"><span data-stu-id="877ef-144">PowerShell creates a session from information that is stored in the TestCmdlets module.</span></span>

### <span data-ttu-id="877ef-145">Exempel 4: exportera och clobber kommandon i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="877ef-145">Example 4: Export and clobber commands in the current session</span></span>

<span data-ttu-id="877ef-146">I det här exemplet exporteras kommandon som lagras i en variabel till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="877ef-146">This example exports commands that are stored in a variable into the current session.</span></span>

```powershell
Export-PSSession -Session $S -AllowClobber -OutputModule AllCommands
```

<span data-ttu-id="877ef-147">Detta `Export-PSSession` kommando exporterar alla kommandon och all formatering av data från PSSession i `$S` variabeln till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="877ef-147">This `Export-PSSession` command exports all commands and all formatting data from the PSSession in the `$S` variable into the current session.</span></span> <span data-ttu-id="877ef-148">Parametern **AllowClobber** innehåller kommandon med samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="877ef-148">The **AllowClobber** parameter includes commands with the same names as commands in the current session.</span></span>

### <span data-ttu-id="877ef-149">Exempel 5: exportera kommandon från en stängd PSSession</span><span class="sxs-lookup"><span data-stu-id="877ef-149">Example 5: Export commands from a closed PSSession</span></span>

<span data-ttu-id="877ef-150">Det här exemplet visar hur du kör de exporterade kommandona med särskilda alternativ när PSSession som skapade de exporterade kommandona är stängd.</span><span class="sxs-lookup"><span data-stu-id="877ef-150">This example shows how to run the exported commands with special options when the PSSession that created the exported commands is closed.</span></span>

<span data-ttu-id="877ef-151">Om den ursprungliga fjärrsessionen stängs när en modul importeras, kommer modulen att använda alla öppna fjärrsessioner som ansluter till den ursprungliga datorn.</span><span class="sxs-lookup"><span data-stu-id="877ef-151">If the original remote session is closed when a module is imported, the module will use any open remote session that connects to the originating computer.</span></span> <span data-ttu-id="877ef-152">Om det inte finns någon aktuell session för den ursprungliga datorn kommer modulen att återupprätta en session.</span><span class="sxs-lookup"><span data-stu-id="877ef-152">If there is no current session to the originating computer, the module will reestablish a session.</span></span>

<span data-ttu-id="877ef-153">Om du vill köra exporterade kommandon med särskilda alternativ i en fjärrsession måste du skapa en fjärrsession med dessa alternativ innan du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="877ef-153">To run exported commands with special options in a remote session, you must create a remote session with those options before you import the module.</span></span> <span data-ttu-id="877ef-154">Använd `New-PSSession` cmdleten med parametern **SessionOption**</span><span class="sxs-lookup"><span data-stu-id="877ef-154">Use the `New-PSSession` cmdlet with the **SessionOption** parameter</span></span>

```powershell
$Options = New-PSSessionOption -NoMachineProfile
$S = New-PSSession -ComputerName Server01 -SessionOption $Options
Export-PSSession -Session $S -OutputModule Server01
Remove-PSSession $S
New-PSSession -ComputerName Server01 -SessionOption $Options
Import-Module Server01
```

<span data-ttu-id="877ef-155">`New-PSSessionOption`Cmdleten skapar ett **PSSessionOption** -objekt och sparar objektet i `$Options` variabeln.</span><span class="sxs-lookup"><span data-stu-id="877ef-155">The `New-PSSessionOption` cmdlet creates a **PSSessionOption** object, and it saves the object in the `$Options` variable.</span></span> <span data-ttu-id="877ef-156">`New-PSSession`Kommandot skapar en PSSession på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="877ef-156">The `New-PSSession` command creates a PSSession on the Server01 computer.</span></span>
<span data-ttu-id="877ef-157">Parametern **SessionOption** använder objektet som är lagrat i `$Options` .</span><span class="sxs-lookup"><span data-stu-id="877ef-157">The **SessionOption** parameter uses the object stored in `$Options`.</span></span> <span data-ttu-id="877ef-158">Sessionen lagras i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="877ef-158">The session is stored in the `$S` variable.</span></span>

<span data-ttu-id="877ef-159">`Export-PSSession`Cmdleten exporterar kommandon från PSSession i `$S` till Server01-modulen.</span><span class="sxs-lookup"><span data-stu-id="877ef-159">The `Export-PSSession` cmdlet exports commands from the PSSession in `$S` to the Server01 module.</span></span>
<span data-ttu-id="877ef-160">`Remove-PSSession`Cmdleten tar bort PSSession i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="877ef-160">The `Remove-PSSession` cmdlet deletes the PSSession in the `$S` variable.</span></span>

<span data-ttu-id="877ef-161">`New-PSSession`Cmdleten skapar en ny PSSession som ansluter till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="877ef-161">The `New-PSSession` cmdlet creates a new PSSession that connects to the Server01 computer.</span></span> <span data-ttu-id="877ef-162">Parametern **SessionOption** använder objektet som är lagrat i `$Options` .</span><span class="sxs-lookup"><span data-stu-id="877ef-162">The **SessionOption** parameter uses the object stored in `$Options`.</span></span> <span data-ttu-id="877ef-163">`Import-Module`Cmdleten importerar kommandona från Server01-modulen.</span><span class="sxs-lookup"><span data-stu-id="877ef-163">The `Import-Module` cmdlet imports the commands from the Server01 module.</span></span> <span data-ttu-id="877ef-164">Kommandona i modulen körs i mappen PSSession på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="877ef-164">The commands in the module are run in the PSSession on the Server01 computer.</span></span>

## <span data-ttu-id="877ef-165">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="877ef-165">PARAMETERS</span></span>

### <span data-ttu-id="877ef-166">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="877ef-166">-AllowClobber</span></span>

<span data-ttu-id="877ef-167">Exporterar de angivna kommandona, även om de har samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="877ef-167">Exports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="877ef-168">Om du exporterar ett kommando med samma namn som ett kommando i den aktuella sessionen, döljer det exporterade kommandot eller ersätter de ursprungliga kommandona.</span><span class="sxs-lookup"><span data-stu-id="877ef-168">If you export a command with the same name as a command in the current session, the exported command hides or replaces the original commands.</span></span> <span data-ttu-id="877ef-169">Mer information finns i [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="877ef-169">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>

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

### <span data-ttu-id="877ef-170">– Argument List</span><span class="sxs-lookup"><span data-stu-id="877ef-170">-ArgumentList</span></span>

<span data-ttu-id="877ef-171">Exporterar kommandots variant som resulterar från att de angivna argumenten används (parameter värden).</span><span class="sxs-lookup"><span data-stu-id="877ef-171">Exports the variant of the command that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="877ef-172">Till exempel för att exportera `Get-Item` kommandots variant i certifikatet (cert:) enhet i PSSession i `$S` skriver du `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .</span><span class="sxs-lookup"><span data-stu-id="877ef-172">For example, to export the variant of the `Get-Item` command in the certificate (Cert:) drive in the PSSession in `$S`, type `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="877ef-173">– Certifikat</span><span class="sxs-lookup"><span data-stu-id="877ef-173">-Certificate</span></span>

<span data-ttu-id="877ef-174">Anger det klient certifikat som används för att signera format-filer (\* .Format.ps1XML) eller psm1 (.) i den modul som `Export-PSSession` skapar.</span><span class="sxs-lookup"><span data-stu-id="877ef-174">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the module that `Export-PSSession` creates.</span></span> <span data-ttu-id="877ef-175">Ange en variabel som innehåller ett certifikat eller ett kommando eller uttryck som hämtar certifikatet.</span><span class="sxs-lookup"><span data-stu-id="877ef-175">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="877ef-176">Om du vill söka efter ett certifikat använder du `Get-PfxCertificate` cmdleten eller använder `Get-ChildItem` cmdleten i certifikatet (cert:) kombinationsenhet.</span><span class="sxs-lookup"><span data-stu-id="877ef-176">To find a certificate, use the `Get-PfxCertificate` cmdlet or use the `Get-ChildItem` cmdlet in the Certificate (Cert:) drive.</span></span> <span data-ttu-id="877ef-177">Om certifikatet inte är giltigt eller inte har tillräcklig behörighet, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="877ef-177">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="877ef-178">– CommandName</span><span class="sxs-lookup"><span data-stu-id="877ef-178">-CommandName</span></span>

<span data-ttu-id="877ef-179">Exporterar endast kommandon med angivna namn eller namn mönster.</span><span class="sxs-lookup"><span data-stu-id="877ef-179">Exports only the commands with the specified names or name patterns.</span></span> <span data-ttu-id="877ef-180">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="877ef-180">Wildcards are permitted.</span></span> <span data-ttu-id="877ef-181">Använd **commandname** eller dess alias, **namn**.</span><span class="sxs-lookup"><span data-stu-id="877ef-181">Use **CommandName** or its alias, **Name**.</span></span>

<span data-ttu-id="877ef-182">Som standard `Export-PSSession` exporterar alla kommandon från PSSession förutom kommandon som har samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="877ef-182">By default, `Export-PSSession` exports all commands from the PSSession except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="877ef-183">Detta förhindrar att kommandon döljs eller ersätts av kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="877ef-183">This prevents commands from being hidden or replaced by commands in the current session.</span></span> <span data-ttu-id="877ef-184">Om du vill exportera alla kommandon, även de som döljer eller ersätter andra kommandon, använder du parametern **AllowClobber** .</span><span class="sxs-lookup"><span data-stu-id="877ef-184">To export all commands, even those that hide or replace other commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="877ef-185">Om du använder parametern **commandname** exporteras inte filerna för kommandona om du inte använder parametern **FormatTypeName** .</span><span class="sxs-lookup"><span data-stu-id="877ef-185">If you use the **CommandName** parameter, the formatting files for the commands are not exported unless you use the **FormatTypeName** parameter.</span></span> <span data-ttu-id="877ef-186">Om du använder parametern **FormatTypeName** exporteras inte heller några kommandon om du inte använder parametern **commandname** .</span><span class="sxs-lookup"><span data-stu-id="877ef-186">Similarly, if you use the **FormatTypeName** parameter, no commands are exported unless you use the **CommandName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="877ef-187">-CommandType</span><span class="sxs-lookup"><span data-stu-id="877ef-187">-CommandType</span></span>

<span data-ttu-id="877ef-188">Exporterar endast de angivna typerna av kommando objekt.</span><span class="sxs-lookup"><span data-stu-id="877ef-188">Exports only the specified types of command objects.</span></span> <span data-ttu-id="877ef-189">Använd **CommandType** eller dess alias och **Skriv**.</span><span class="sxs-lookup"><span data-stu-id="877ef-189">Use **CommandType** or its alias, **Type**.</span></span>

<span data-ttu-id="877ef-190">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="877ef-190">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="877ef-191">Aliasuppsättning.</span><span class="sxs-lookup"><span data-stu-id="877ef-191">Alias.</span></span> <span data-ttu-id="877ef-192">Alla PowerShell-alias i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="877ef-192">All PowerShell aliases in the current session.</span></span>
- <span data-ttu-id="877ef-193">Vissa.</span><span class="sxs-lookup"><span data-stu-id="877ef-193">All.</span></span> <span data-ttu-id="877ef-194">Alla kommando typer.</span><span class="sxs-lookup"><span data-stu-id="877ef-194">All command types.</span></span> <span data-ttu-id="877ef-195">Det motsvarar `Get-Command -Name *` .</span><span class="sxs-lookup"><span data-stu-id="877ef-195">It is the equivalent of `Get-Command -Name *`.</span></span>
- <span data-ttu-id="877ef-196">Applicering.</span><span class="sxs-lookup"><span data-stu-id="877ef-196">Application.</span></span> <span data-ttu-id="877ef-197">Alla filer förutom PowerShell-filer i sökvägar som anges i miljövariabeln PATH ( `$env:path` ), inklusive. txt-,. exe-och. dll-filer.</span><span class="sxs-lookup"><span data-stu-id="877ef-197">All files other than PowerShell files in paths listed in the Path environment variable (`$env:path`), including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="877ef-198">Kommandon.</span><span class="sxs-lookup"><span data-stu-id="877ef-198">Cmdlet.</span></span> <span data-ttu-id="877ef-199">Cmdletarna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="877ef-199">The cmdlets in the current session.</span></span> <span data-ttu-id="877ef-200">Cmdlet är standard.</span><span class="sxs-lookup"><span data-stu-id="877ef-200">Cmdlet is the default.</span></span>
- <span data-ttu-id="877ef-201">Inställningarna.</span><span class="sxs-lookup"><span data-stu-id="877ef-201">Configuration.</span></span> <span data-ttu-id="877ef-202">En PowerShell-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="877ef-202">A PowerShell configuration.</span></span> <span data-ttu-id="877ef-203">Mer information finns i [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="877ef-203">For more information, see [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span></span>
- <span data-ttu-id="877ef-204">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="877ef-204">ExternalScript.</span></span> <span data-ttu-id="877ef-205">Alla. ps1-filer i Sök vägarna som anges i miljövariabeln PATH ( `$env:path` ).</span><span class="sxs-lookup"><span data-stu-id="877ef-205">All .ps1 files in the paths listed in the Path environment variable (`$env:path`).</span></span>
- <span data-ttu-id="877ef-206">Filter och funktion.</span><span class="sxs-lookup"><span data-stu-id="877ef-206">Filter and Function.</span></span> <span data-ttu-id="877ef-207">Alla PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="877ef-207">All PowerShell functions.</span></span>
- <span data-ttu-id="877ef-208">Över.</span><span class="sxs-lookup"><span data-stu-id="877ef-208">Script.</span></span> <span data-ttu-id="877ef-209">Skript block i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="877ef-209">Script blocks in the current session.</span></span>
- <span data-ttu-id="877ef-210">Arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="877ef-210">Workflow.</span></span> <span data-ttu-id="877ef-211">Ett PowerShell-arbetsflöde.</span><span class="sxs-lookup"><span data-stu-id="877ef-211">A PowerShell workflow.</span></span> <span data-ttu-id="877ef-212">Mer information finns i [about_Workflows](/powershell/module/psworkflow/about/about_workflows?view=powershell-5.1).</span><span class="sxs-lookup"><span data-stu-id="877ef-212">For more information, see [about_Workflows](/powershell/module/psworkflow/about/about_workflows?view=powershell-5.1).</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, All, Application, Cmdlet, Configuration, ExternalScript, Filter, Function, Script, Workflow

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="877ef-213">-Encoding</span><span class="sxs-lookup"><span data-stu-id="877ef-213">-Encoding</span></span>

<span data-ttu-id="877ef-214">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="877ef-214">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="877ef-215">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="877ef-215">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="877ef-216">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="877ef-216">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="877ef-217">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="877ef-217">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="877ef-218">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="877ef-218">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="877ef-219">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="877ef-219">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="877ef-220">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="877ef-220">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="877ef-221">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="877ef-221">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="877ef-222">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="877ef-222">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="877ef-223">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="877ef-223">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="877ef-224">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="877ef-224">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="877ef-225">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="877ef-225">`utf32`: Encodes in UTF-32 format.</span></span>


<span data-ttu-id="877ef-226">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="877ef-226">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="877ef-227">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="877ef-227">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="877ef-228">-Force</span><span class="sxs-lookup"><span data-stu-id="877ef-228">-Force</span></span>

<span data-ttu-id="877ef-229">Skriver över en eller flera befintliga utdatafiler, även om filen har attributet skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="877ef-229">Overwrites one or more existing output files, even if the file has the read-only attribute.</span></span>

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

### <span data-ttu-id="877ef-230">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="877ef-230">-FormatTypeName</span></span>

<span data-ttu-id="877ef-231">Exporterar bara formateringsregler för de angivna Microsoft .NET Ramverks typerna.</span><span class="sxs-lookup"><span data-stu-id="877ef-231">Exports formatting instructions only for the specified Microsoft .NET Framework types.</span></span> <span data-ttu-id="877ef-232">Ange typ namn.</span><span class="sxs-lookup"><span data-stu-id="877ef-232">Enter the type names.</span></span> <span data-ttu-id="877ef-233">Som standard `Export-PSSession` exporterar formaterings instruktioner för alla .NET Framework typer som inte finns i namn området **system. Management. Automation** .</span><span class="sxs-lookup"><span data-stu-id="877ef-233">By default, `Export-PSSession` exports formatting instructions for all .NET Framework types that are not in the **System.Management.Automation** namespace.</span></span>

<span data-ttu-id="877ef-234">Värdet för den här parametern måste vara namnet på en typ som returneras av ett `Get-FormatData` kommando i den session som kommandona importeras från.</span><span class="sxs-lookup"><span data-stu-id="877ef-234">The value of this parameter must be the name of a type that is returned by a `Get-FormatData` command in the session from which the commands are being imported.</span></span> <span data-ttu-id="877ef-235">Om du vill hämta alla formaterings data i fjärrsessionen skriver du `*` .</span><span class="sxs-lookup"><span data-stu-id="877ef-235">To get all of the formatting data in the remote session, type `*`.</span></span>

<span data-ttu-id="877ef-236">Om du använder parametern **FormatTypeName** exporteras inga kommandon om du inte använder parametern **commandname** .</span><span class="sxs-lookup"><span data-stu-id="877ef-236">If you use the **FormatTypeName** parameter, no commands are exported unless you use the **CommandName** parameter.</span></span>

<span data-ttu-id="877ef-237">Om du använder parametern **commandname** exporteras inte filerna för kommandona om du inte använder parametern **FormatTypeName** .</span><span class="sxs-lookup"><span data-stu-id="877ef-237">If you use the **CommandName** parameter, the formatting files for the commands are not exported unless you use the **FormatTypeName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="877ef-238">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="877ef-238">-FullyQualifiedModule</span></span>

<span data-ttu-id="877ef-239">Anger moduler med namn som anges i form av **ModuleSpecification** -objekt.</span><span class="sxs-lookup"><span data-stu-id="877ef-239">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="877ef-240">Se avsnittet anmärkningar i [ModuleSpecification-konstruktorn (hash)](https://msdn.microsoft.com/library/jj136290).</span><span class="sxs-lookup"><span data-stu-id="877ef-240">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290).</span></span>

<span data-ttu-id="877ef-241">**FullyQualifiedModule** -parametern accepterar till exempel ett modulnamn som anges i något av följande format:</span><span class="sxs-lookup"><span data-stu-id="877ef-241">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="877ef-242">**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="877ef-242">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="877ef-243">Det går inte att ange parametern **FullyQualifiedModule** i samma kommando som en **modul** parameter. de två parametrarna kan inte anges samtidigt.</span><span class="sxs-lookup"><span data-stu-id="877ef-243">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter; the two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="877ef-244">– Modul</span><span class="sxs-lookup"><span data-stu-id="877ef-244">-Module</span></span>

<span data-ttu-id="877ef-245">Exporterar endast kommandona i de angivna PowerShell-snapin-modulerna och modulerna.</span><span class="sxs-lookup"><span data-stu-id="877ef-245">Exports only the commands in the specified PowerShell snap-ins and modules.</span></span> <span data-ttu-id="877ef-246">Ange namnet på snapin-modulen och-modulen.</span><span class="sxs-lookup"><span data-stu-id="877ef-246">Enter the snap-in and module names.</span></span> <span data-ttu-id="877ef-247">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="877ef-247">Wildcards are not permitted.</span></span>

<span data-ttu-id="877ef-248">Mer information finns i `Import-Module` och [about_PSSnapins](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1).</span><span class="sxs-lookup"><span data-stu-id="877ef-248">For more information, see `Import-Module` and [about_PSSnapins](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="877ef-249">-OutputModule</span><span class="sxs-lookup"><span data-stu-id="877ef-249">-OutputModule</span></span>

<span data-ttu-id="877ef-250">Anger en valfri sökväg och ett namn för modulen som skapats av `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="877ef-250">Specifies an optional path and name for the module created by `Export-PSSession`.</span></span> <span data-ttu-id="877ef-251">Standard Sök vägen är `$home\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="877ef-251">The default path is `$home\Documents\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="877ef-252">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="877ef-252">This parameter is required.</span></span>

<span data-ttu-id="877ef-253">Om modulens under katalog eller någon av de filer som `Export-PSSession` skapas redan finns, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="877ef-253">If the module subdirectory or any of the files that `Export-PSSession` creates already exist, the command fails.</span></span> <span data-ttu-id="877ef-254">Använd parametern **Force** om du vill skriva över befintliga filer.</span><span class="sxs-lookup"><span data-stu-id="877ef-254">To overwrite existing files, use the **Force** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, ModuleName

Required: True
Position: 1
Default value: $home\Documents\WindowsPowerShell\Modules
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="877ef-255">– Session</span><span class="sxs-lookup"><span data-stu-id="877ef-255">-Session</span></span>

<span data-ttu-id="877ef-256">Anger den PSSession som kommandona exporteras från.</span><span class="sxs-lookup"><span data-stu-id="877ef-256">Specifies the PSSession from which the commands are exported.</span></span> <span data-ttu-id="877ef-257">Ange en variabel som innehåller ett session-objekt eller ett kommando som hämtar ett sessionsobjekt, till exempel ett `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="877ef-257">Enter a variable that contains a session object or a command that gets a session object, such as a `Get-PSSession` command.</span></span> <span data-ttu-id="877ef-258">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="877ef-258">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="877ef-259">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="877ef-259">CommonParameters</span></span>

<span data-ttu-id="877ef-260">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="877ef-260">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="877ef-261">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="877ef-261">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="877ef-262">INDATA</span><span class="sxs-lookup"><span data-stu-id="877ef-262">INPUTS</span></span>

### <span data-ttu-id="877ef-263">Inget</span><span class="sxs-lookup"><span data-stu-id="877ef-263">None</span></span>

<span data-ttu-id="877ef-264">Det går inte att skicka pipe-objekt till `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="877ef-264">You cannot pipe objects to `Export-PSSession`.</span></span>

## <span data-ttu-id="877ef-265">UTDATA</span><span class="sxs-lookup"><span data-stu-id="877ef-265">OUTPUTS</span></span>

### <span data-ttu-id="877ef-266">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="877ef-266">System.IO.FileInfo</span></span>

<span data-ttu-id="877ef-267">`Export-PSSession` Returnerar en lista med filer som utgör den modul som den skapade.</span><span class="sxs-lookup"><span data-stu-id="877ef-267">`Export-PSSession` returns a list of files that comprise the module that it created.</span></span>

## <span data-ttu-id="877ef-268">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="877ef-268">NOTES</span></span>

<span data-ttu-id="877ef-269">`Export-PSSession` förlitar sig på PowerShell-infrastrukturen för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="877ef-269">`Export-PSSession` relies on the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="877ef-270">Om du vill använda denna cmdlet måste datorn konfigureras för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="877ef-270">To use this cmdlet, the computer must be configured for remoting.</span></span> <span data-ttu-id="877ef-271">Mer information finns i [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="877ef-271">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="877ef-272">Du kan inte använda `Export-PSSession` för att exportera en PowerShell-Provider.</span><span class="sxs-lookup"><span data-stu-id="877ef-272">You cannot use `Export-PSSession` to export a PowerShell provider.</span></span>

<span data-ttu-id="877ef-273">Exporterade kommandon körs implicit i PSSession som de exporterades från.</span><span class="sxs-lookup"><span data-stu-id="877ef-273">Exported commands run implicitly in the PSSession from which they were exported.</span></span> <span data-ttu-id="877ef-274">Information om hur du kör fjärrkommandona hanteras helt och hållet av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="877ef-274">The details of running the commands remotely are handled entirely by PowerShell.</span></span> <span data-ttu-id="877ef-275">Du kan köra de exporterade kommandona på samma sätt som du kör lokala kommandon.</span><span class="sxs-lookup"><span data-stu-id="877ef-275">You can run the exported commands just as you would run local commands.</span></span>

<span data-ttu-id="877ef-276">`Export-ModuleMember` fångar och sparar information om PSSession i den modul som den exporterar.</span><span class="sxs-lookup"><span data-stu-id="877ef-276">`Export-ModuleMember` captures and saves information about the PSSession in the module that it exports.</span></span> <span data-ttu-id="877ef-277">Om PSSession som kommandona exporterades från stängs när du importerar modulen, och det inte finns några aktiva PSSessions på samma dator, försöker kommandona i modulen återskapa PSSession.</span><span class="sxs-lookup"><span data-stu-id="877ef-277">If the PSSession from which the commands were exported is closed when you import the module, and there are no active PSSessions to the same computer, the commands in the module attempt to recreate the PSSession.</span></span> <span data-ttu-id="877ef-278">Om försök att återskapa PSSession Miss lyckas kommer de exporterade kommandona inte att köras.</span><span class="sxs-lookup"><span data-stu-id="877ef-278">If attempts to recreate the PSSession fail, the exported commands will not run.</span></span>

<span data-ttu-id="877ef-279">Sessionsinformation som `Export-ModuleMember` fångar in och sparar i modulen omfattar inte sessionsinställningar, till exempel de som du anger i `$PSSessionOption` variabeln Preference eller med hjälp av parametern **SessionOption** i `New-PSSession` `Enter-PSSession` cmdletarna,, eller `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="877ef-279">The session information that `Export-ModuleMember` captures and saves in the module does not include session options, such as those that you specify in the `$PSSessionOption` preference variable or by using the **SessionOption** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlets.</span></span> <span data-ttu-id="877ef-280">Om den ursprungliga PSSession stängs när du importerar modulen använder modulen en annan PSSession på samma dator, om en sådan finns tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="877ef-280">If the original PSSession is closed when you import the module, the module will use another PSSession to the same computer, if one is available.</span></span> <span data-ttu-id="877ef-281">Om du vill aktivera de importerade kommandona att köras i en korrekt konfigurerad session skapar du en PSSession med de alternativ som du vill använda innan du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="877ef-281">To enable the imported commands to run in a correctly configured session, create a PSSession with the options that you want before you import the module.</span></span>

<span data-ttu-id="877ef-282">För att hitta de kommandon som ska exporteras `Export-PSSession` använder `Invoke-Command` cmdleten för att köra ett `Get-Command` kommando i PSSession.</span><span class="sxs-lookup"><span data-stu-id="877ef-282">To find the commands to export, `Export-PSSession` uses the `Invoke-Command` cmdlet to run a `Get-Command` command in the PSSession.</span></span> <span data-ttu-id="877ef-283">För att hämta och spara formaterings data för kommandona används `Get-FormatData` `Export-FormatData` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="877ef-283">To get and save formatting data for the commands, it uses the `Get-FormatData` and `Export-FormatData` cmdlets.</span></span> <span data-ttu-id="877ef-284">Du kan se fel meddelanden från `Invoke-Command` , `Get-Command` , `Get-FormatData` och `Export-FormatData` när du kör ett `Export-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="877ef-284">You might see error messages from `Invoke-Command`, `Get-Command`, `Get-FormatData`, and `Export-FormatData` when you run an `Export-PSSession` command.</span></span> <span data-ttu-id="877ef-285">`Export-PSSession`Kan inte heller exportera kommandon från en-session som inte innehåller `Get-Command` `Get-FormatData` `Select-Object` cmdletarna,, och `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="877ef-285">Also, `Export-PSSession` cannot export commands from a session that does not include the `Get-Command`, `Get-FormatData`, `Select-Object`, and `Get-Help` cmdlets.</span></span>

<span data-ttu-id="877ef-286">`Export-PSSession` använder `Write-Progress` cmdleten för att visa förloppet för kommandot.</span><span class="sxs-lookup"><span data-stu-id="877ef-286">`Export-PSSession` uses the `Write-Progress` cmdlet to display the progress of the command.</span></span> <span data-ttu-id="877ef-287">Du kan se förlopps indikatorn när kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="877ef-287">You might see the progress bar while the command is running.</span></span>

<span data-ttu-id="877ef-288">Exporterade kommandon har samma begränsningar som andra fjärrkommandon, inklusive möjligheten att starta ett program med ett användar gränssnitt, t. ex. anteckningar.</span><span class="sxs-lookup"><span data-stu-id="877ef-288">Exported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>

<span data-ttu-id="877ef-289">Eftersom PowerShell-profiler inte körs i PSSessions är kommandona som en profil lägger till i en session inte tillgängliga för `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="877ef-289">Because PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to `Export-PSSession`.</span></span> <span data-ttu-id="877ef-290">Om du vill exportera kommandon från en profil använder du ett `Invoke-Command` kommando för att köra profilen i PSSession manuellt innan du exporterar kommandon.</span><span class="sxs-lookup"><span data-stu-id="877ef-290">To export commands from a profile, use an `Invoke-Command` command to run the profile in the PSSession manually before exporting commands.</span></span>

<span data-ttu-id="877ef-291">Modulen som `Export-PSSession` skapar kan innehålla en formateringsinformation, även om kommandot inte importerar formaterings data.</span><span class="sxs-lookup"><span data-stu-id="877ef-291">The module that `Export-PSSession` creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="877ef-292">Om kommandot inte importerar dataformaterade data kommer eventuella filer som skapas inte att innehålla formatering.</span><span class="sxs-lookup"><span data-stu-id="877ef-292">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>

## <span data-ttu-id="877ef-293">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="877ef-293">RELATED LINKS</span></span>

[<span data-ttu-id="877ef-294">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="877ef-294">about_Command_Precedence</span></span>](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)

[<span data-ttu-id="877ef-295">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="877ef-295">about_PSSessions</span></span>](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[<span data-ttu-id="877ef-296">about_PSSnapins</span><span class="sxs-lookup"><span data-stu-id="877ef-296">about_PSSnapins</span></span>](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1)

[<span data-ttu-id="877ef-297">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="877ef-297">about_Remote_Requirements</span></span>](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)

[<span data-ttu-id="877ef-298">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="877ef-298">Import-Module</span></span>](../Microsoft.PowerShell.Core/Import-Module.md)

[<span data-ttu-id="877ef-299">Importera – PSSession</span><span class="sxs-lookup"><span data-stu-id="877ef-299">Import-PSSession</span></span>](Import-PSSession.md)

[<span data-ttu-id="877ef-300">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="877ef-300">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="877ef-301">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="877ef-301">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="877ef-302">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="877ef-302">New-PSSessionOption</span></span>](../Microsoft.PowerShell.Core/New-PSSessionOption.md)

[<span data-ttu-id="877ef-303">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="877ef-303">Remove-PSSession</span></span>](../Microsoft.PowerShell.Core/Remove-PSSession.md)