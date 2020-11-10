---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-PSSession
ms.openlocfilehash: 11533a9b127dc6d088258392c0e142bfbe5c070c
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388033"
---
# <span data-ttu-id="c830c-103">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="c830c-103">Export-PSSession</span></span>

## <span data-ttu-id="c830c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c830c-104">SYNOPSIS</span></span>

<span data-ttu-id="c830c-105">Exporterar kommandon från en annan session och sparar dem i en PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="c830c-105">Exports commands from another session and saves them in a PowerShell module.</span></span>

## <span data-ttu-id="c830c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c830c-106">SYNTAX</span></span>

```
Export-PSSession [-Session] <PSSession> [-OutputModule] <string> [[-CommandName] <string[]>]
 [[-FormatTypeName] <string[]>] [-Force] [-Encoding <string>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <string[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-Certificate <X509Certificate2>]
 [<CommonParameters>]
```

## <span data-ttu-id="c830c-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c830c-107">DESCRIPTION</span></span>

<span data-ttu-id="c830c-108">`Export-PSSession`Cmdlet: en hämtar cmdlets, functions, alias och andra kommando typer från en annan PowerShell-session (PSSession) på en lokal eller fjärran sluten dator och sparar dem i en PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="c830c-108">The `Export-PSSession` cmdlet gets cmdlets, functions, aliases, and other command types from another PowerShell session (PSSession) on a local or remote computer and saves them in a PowerShell module.</span></span> <span data-ttu-id="c830c-109">Använd cmdleten om du vill lägga till kommandon från modulen till den aktuella sessionen `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="c830c-109">To add the commands from the module to the current session, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="c830c-110">Till skillnad `Import-PSSession` från, som importerar kommandon från en annan PSSession till den aktuella sessionen, `Export-PSSession` sparar kommandona i en modul.</span><span class="sxs-lookup"><span data-stu-id="c830c-110">Unlike `Import-PSSession`, which imports commands from another PSSession into the current session, `Export-PSSession` saves the commands in a module.</span></span> <span data-ttu-id="c830c-111">Kommandona importeras inte till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c830c-111">The commands are not imported into the current session.</span></span>

<span data-ttu-id="c830c-112">Om du vill exportera kommandon använder du `New-PSSession` cmdleten för att skapa en PSSession som har de kommandon som du vill exportera.</span><span class="sxs-lookup"><span data-stu-id="c830c-112">To export commands, use the `New-PSSession` cmdlet to create a PSSession that has the commands that you want to export.</span></span> <span data-ttu-id="c830c-113">Använd sedan `Export-PSSession` cmdlet: en för att exportera kommandona.</span><span class="sxs-lookup"><span data-stu-id="c830c-113">Then use the `Export-PSSession` cmdlet to export the commands.</span></span>

<span data-ttu-id="c830c-114">För att förhindra kommando namns konflikter, är standardvärdet för `Export-PSSession` att exportera alla kommandon, förutom kommandon som finns i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c830c-114">To prevent command name conflicts, the default for `Export-PSSession` is to export all commands, except for commands that exist in the current session.</span></span> <span data-ttu-id="c830c-115">Du kan använda parametern **commandname** för att ange vilka kommandon som ska exporteras.</span><span class="sxs-lookup"><span data-stu-id="c830c-115">You can use the **CommandName** parameter to specify the commands to export.</span></span>

<span data-ttu-id="c830c-116">`Export-PSSession`Cmdleten använder funktionen implicit fjärr kommunikation i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c830c-116">The `Export-PSSession` cmdlet uses the implicit remoting feature of PowerShell.</span></span> <span data-ttu-id="c830c-117">När du importerar kommandon till den aktuella sessionen körs de implicit i den ursprungliga sessionen eller i en liknande session på den ursprungliga datorn.</span><span class="sxs-lookup"><span data-stu-id="c830c-117">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

## <span data-ttu-id="c830c-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c830c-118">EXAMPLES</span></span>

### <span data-ttu-id="c830c-119">Exempel 1: exportera kommandon från en PSSession</span><span class="sxs-lookup"><span data-stu-id="c830c-119">Example 1: Export commands from a PSSession</span></span>

<span data-ttu-id="c830c-120">I det här exemplet skapas en ny PSSession från den lokala datorn till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="c830c-120">This example creates a new PSSession from the local computer to the Server01 computer.</span></span> <span data-ttu-id="c830c-121">Alla kommandon, förutom de som finns i den aktuella sessionen, exporteras till modulen med namnet Server01 på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c830c-121">All of the commands, except those that exist in the current session, are exported to the module named Server01 on the local computer.</span></span> <span data-ttu-id="c830c-122">Exporten innehåller formaterings data för kommandona.</span><span class="sxs-lookup"><span data-stu-id="c830c-122">The export includes the formatting data for the commands.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01
Export-PSSession -Session $S -OutputModule Server01
```

<span data-ttu-id="c830c-123">`New-PSSession`Kommandot skapar en PSSession på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="c830c-123">The `New-PSSession` command creates a PSSession on the Server01 computer.</span></span> <span data-ttu-id="c830c-124">PSSession lagras i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c830c-124">The PSSession is stored in the `$S` variable.</span></span> <span data-ttu-id="c830c-125">`Export-PSSession`Kommandot exporterar `$S` variabelns kommandon och formaterar data till Server01-modulen.</span><span class="sxs-lookup"><span data-stu-id="c830c-125">The `Export-PSSession` command exports the `$S` variable's commands and formatting data into the Server01 module.</span></span>

### <span data-ttu-id="c830c-126">Exempel 2: exportera get-och set-kommandona</span><span class="sxs-lookup"><span data-stu-id="c830c-126">Example 2: Export the Get and Set commands</span></span>

<span data-ttu-id="c830c-127">I det här exemplet exporteras alla `Get` `Set` kommandon från en server.</span><span class="sxs-lookup"><span data-stu-id="c830c-127">This example exports all of the `Get` and `Set` commands from a server.</span></span>

```powershell
$S = New-PSSession -ConnectionUri https://exchange.microsoft.com/mailbox -Credential exchangeadmin01@hotmail.com -Authentication Negotiate
Export-PSSession -Session $S -Module exch* -CommandName Get-*, Set-* -FormatTypeName * -OutputModule $PSHOME\Modules\Exchange -Encoding ASCII
```

<span data-ttu-id="c830c-128">Dessa kommandon exporterar `Get` och- `Set` kommandon från en Microsoft Exchange Server-snapin-modul på en fjärrdator till en Exchange-modul i `$PSHOME\Modules` katalogen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c830c-128">These commands export the `Get` and `Set` commands from a Microsoft Exchange Server snap-in on a remote computer to an Exchange module in the `$PSHOME\Modules` directory on the local computer.</span></span>
<span data-ttu-id="c830c-129">Att placera modulen i `$PSHOME\Modules` katalogen gör den tillgänglig för alla användare av datorn.</span><span class="sxs-lookup"><span data-stu-id="c830c-129">Placing the module in the `$PSHOME\Modules` directory makes it accessible to all users of the computer.</span></span>

### <span data-ttu-id="c830c-130">Exempel 3: exportera kommandon från en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="c830c-130">Example 3: Export commands from a remote computer</span></span>

<span data-ttu-id="c830c-131">Det här exemplet exporterar cmdletar från en PSSession på en fjärrdator och sparar dem i en modul på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c830c-131">This example exports cmdlets from a PSSession on a remote computer and saves them in a module on the local computer.</span></span> <span data-ttu-id="c830c-132">Cmdletarna från modulen läggs till i den aktuella sessionen så att de kan användas.</span><span class="sxs-lookup"><span data-stu-id="c830c-132">The cmdlets from the module are added to the current session so that they can be used.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01 -Credential Server01\User01
Export-PSSession -Session $S -OutputModule TestCmdlets -Type Cmdlet -CommandName *test* -FormatTypeName *
Remove-PSSession $S
Import-Module TestCmdlets
Get-Help Test*
Test-Files
```

<span data-ttu-id="c830c-133">`New-PSSession`Kommandot skapar en PSSession på Server01-datorn och sparar den i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c830c-133">The `New-PSSession` command creates a PSSession on the Server01 computer and saves it in the `$S` variable.</span></span> <span data-ttu-id="c830c-134">`Export-PSSession`Kommandot exporterar de cmdletar vars namn börjar med test från PSSession i `$S` till TestCmdlets-modulen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c830c-134">The `Export-PSSession` command exports the cmdlets whose names begin with Test from the PSSession in `$S` to the TestCmdlets module on the local computer.</span></span>

<span data-ttu-id="c830c-135">`Remove-PSSession`Cmdleten tar bort PSSession i `$S` från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c830c-135">The `Remove-PSSession` cmdlet deletes the PSSession in `$S` from the current session.</span></span> <span data-ttu-id="c830c-136">Det här kommandot visar att PSSession inte behöver vara aktiv för att använda de kommandon som har importer ATS från sessionen.</span><span class="sxs-lookup"><span data-stu-id="c830c-136">This command shows that the PSSession need not be active to use the commands that were imported from the session.</span></span> <span data-ttu-id="c830c-137">`Import-Module`Cmdleten lägger till cmdletarna i TestCmdlets-modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c830c-137">The `Import-Module` cmdlet adds the cmdlets in the TestCmdlets module to the current session.</span></span> <span data-ttu-id="c830c-138">Kommandot kan köras i alla sessioner när som helst.</span><span class="sxs-lookup"><span data-stu-id="c830c-138">The command can be run in any session at any time.</span></span>

<span data-ttu-id="c830c-139">`Get-Help`Cmdlet: en får hjälp med cmdletar vars namn börjar med test.</span><span class="sxs-lookup"><span data-stu-id="c830c-139">The `Get-Help` cmdlet gets help for cmdlets whose names begin with Test.</span></span> <span data-ttu-id="c830c-140">När du har lagt till kommandon i en modul i den aktuella sessionen kan du använda `Get-Help` `Get-Command` cmdletarna och för att lära dig mer om de importerade kommandona.</span><span class="sxs-lookup"><span data-stu-id="c830c-140">After the commands in a module are added to the current session, you can use the `Get-Help` and `Get-Command` cmdlets to learn about the imported commands.</span></span> <span data-ttu-id="c830c-141">`Test-Files`Cmdleten exporterades från Server01-datorn och lades till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="c830c-141">The `Test-Files` cmdlet was exported from the Server01 computer and added to the session.</span></span> <span data-ttu-id="c830c-142">`Test-Files`Cmdleten körs i en fjärran sluten session på den dator där kommandot importerades.</span><span class="sxs-lookup"><span data-stu-id="c830c-142">The `Test-Files` cmdlet runs in a remote session on the computer from which the command was imported.</span></span> <span data-ttu-id="c830c-143">PowerShell skapar en session med information som lagras i TestCmdlets-modulen.</span><span class="sxs-lookup"><span data-stu-id="c830c-143">PowerShell creates a session from information that is stored in the TestCmdlets module.</span></span>

### <span data-ttu-id="c830c-144">Exempel 4: exportera och clobber kommandon i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="c830c-144">Example 4: Export and clobber commands in the current session</span></span>

<span data-ttu-id="c830c-145">I det här exemplet exporteras kommandon som lagras i en variabel till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c830c-145">This example exports commands that are stored in a variable into the current session.</span></span>

```powershell
Export-PSSession -Session $S -AllowClobber -OutputModule AllCommands
```

<span data-ttu-id="c830c-146">Detta `Export-PSSession` kommando exporterar alla kommandon och all formatering av data från PSSession i `$S` variabeln till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c830c-146">This `Export-PSSession` command exports all commands and all formatting data from the PSSession in the `$S` variable into the current session.</span></span> <span data-ttu-id="c830c-147">Parametern **AllowClobber** innehåller kommandon med samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c830c-147">The **AllowClobber** parameter includes commands with the same names as commands in the current session.</span></span>

### <span data-ttu-id="c830c-148">Exempel 5: exportera kommandon från en stängd PSSession</span><span class="sxs-lookup"><span data-stu-id="c830c-148">Example 5: Export commands from a closed PSSession</span></span>

<span data-ttu-id="c830c-149">Det här exemplet visar hur du kör de exporterade kommandona med särskilda alternativ när PSSession som skapade de exporterade kommandona är stängd.</span><span class="sxs-lookup"><span data-stu-id="c830c-149">This example shows how to run the exported commands with special options when the PSSession that created the exported commands is closed.</span></span>

<span data-ttu-id="c830c-150">Om den ursprungliga fjärrsessionen stängs när en modul importeras, kommer modulen att använda alla öppna fjärrsessioner som ansluter till den ursprungliga datorn.</span><span class="sxs-lookup"><span data-stu-id="c830c-150">If the original remote session is closed when a module is imported, the module will use any open remote session that connects to the originating computer.</span></span> <span data-ttu-id="c830c-151">Om det inte finns någon aktuell session för den ursprungliga datorn kommer modulen att återupprätta en session.</span><span class="sxs-lookup"><span data-stu-id="c830c-151">If there is no current session to the originating computer, the module will reestablish a session.</span></span>

<span data-ttu-id="c830c-152">Om du vill köra exporterade kommandon med särskilda alternativ i en fjärrsession måste du skapa en fjärrsession med dessa alternativ innan du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="c830c-152">To run exported commands with special options in a remote session, you must create a remote session with those options before you import the module.</span></span> <span data-ttu-id="c830c-153">Använd `New-PSSession` cmdleten med parametern **SessionOption**</span><span class="sxs-lookup"><span data-stu-id="c830c-153">Use the `New-PSSession` cmdlet with the **SessionOption** parameter</span></span>

```powershell
$Options = New-PSSessionOption -NoMachineProfile
$S = New-PSSession -ComputerName Server01 -SessionOption $Options
Export-PSSession -Session $S -OutputModule Server01
Remove-PSSession $S
New-PSSession -ComputerName Server01 -SessionOption $Options
Import-Module Server01
```

<span data-ttu-id="c830c-154">`New-PSSessionOption`Cmdleten skapar ett **PSSessionOption** -objekt och sparar objektet i `$Options` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c830c-154">The `New-PSSessionOption` cmdlet creates a **PSSessionOption** object, and it saves the object in the `$Options` variable.</span></span> <span data-ttu-id="c830c-155">`New-PSSession`Kommandot skapar en PSSession på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="c830c-155">The `New-PSSession` command creates a PSSession on the Server01 computer.</span></span>
<span data-ttu-id="c830c-156">Parametern **SessionOption** använder objektet som är lagrat i `$Options` .</span><span class="sxs-lookup"><span data-stu-id="c830c-156">The **SessionOption** parameter uses the object stored in `$Options`.</span></span> <span data-ttu-id="c830c-157">Sessionen lagras i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c830c-157">The session is stored in the `$S` variable.</span></span>

<span data-ttu-id="c830c-158">`Export-PSSession`Cmdleten exporterar kommandon från PSSession i `$S` till Server01-modulen.</span><span class="sxs-lookup"><span data-stu-id="c830c-158">The `Export-PSSession` cmdlet exports commands from the PSSession in `$S` to the Server01 module.</span></span>
<span data-ttu-id="c830c-159">`Remove-PSSession`Cmdleten tar bort PSSession i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c830c-159">The `Remove-PSSession` cmdlet deletes the PSSession in the `$S` variable.</span></span>

<span data-ttu-id="c830c-160">`New-PSSession`Cmdleten skapar en ny PSSession som ansluter till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="c830c-160">The `New-PSSession` cmdlet creates a new PSSession that connects to the Server01 computer.</span></span> <span data-ttu-id="c830c-161">Parametern **SessionOption** använder objektet som är lagrat i `$Options` .</span><span class="sxs-lookup"><span data-stu-id="c830c-161">The **SessionOption** parameter uses the object stored in `$Options`.</span></span> <span data-ttu-id="c830c-162">`Import-Module`Cmdleten importerar kommandona från Server01-modulen.</span><span class="sxs-lookup"><span data-stu-id="c830c-162">The `Import-Module` cmdlet imports the commands from the Server01 module.</span></span> <span data-ttu-id="c830c-163">Kommandona i modulen körs i mappen PSSession på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="c830c-163">The commands in the module are run in the PSSession on the Server01 computer.</span></span>

## <span data-ttu-id="c830c-164">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c830c-164">PARAMETERS</span></span>

### <span data-ttu-id="c830c-165">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="c830c-165">-AllowClobber</span></span>

<span data-ttu-id="c830c-166">Exporterar de angivna kommandona, även om de har samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c830c-166">Exports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="c830c-167">Om du exporterar ett kommando med samma namn som ett kommando i den aktuella sessionen, döljer det exporterade kommandot eller ersätter de ursprungliga kommandona.</span><span class="sxs-lookup"><span data-stu-id="c830c-167">If you export a command with the same name as a command in the current session, the exported command hides or replaces the original commands.</span></span> <span data-ttu-id="c830c-168">Mer information finns i [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="c830c-168">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>

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

### <span data-ttu-id="c830c-169">– Argument List</span><span class="sxs-lookup"><span data-stu-id="c830c-169">-ArgumentList</span></span>

<span data-ttu-id="c830c-170">Exporterar kommandots variant som resulterar från att de angivna argumenten används (parameter värden).</span><span class="sxs-lookup"><span data-stu-id="c830c-170">Exports the variant of the command that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="c830c-171">Till exempel för att exportera `Get-Item` kommandots variant i certifikatet (cert:) enhet i PSSession i `$S` skriver du `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .</span><span class="sxs-lookup"><span data-stu-id="c830c-171">For example, to export the variant of the `Get-Item` command in the certificate (Cert:) drive in the PSSession in `$S`, type `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

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

### <span data-ttu-id="c830c-172">– Certifikat</span><span class="sxs-lookup"><span data-stu-id="c830c-172">-Certificate</span></span>

<span data-ttu-id="c830c-173">Anger det klient certifikat som används för att signera format-filer (\* .Format.ps1XML) eller psm1 (.) i den modul som `Export-PSSession` skapar.</span><span class="sxs-lookup"><span data-stu-id="c830c-173">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the module that `Export-PSSession` creates.</span></span> <span data-ttu-id="c830c-174">Ange en variabel som innehåller ett certifikat eller ett kommando eller uttryck som hämtar certifikatet.</span><span class="sxs-lookup"><span data-stu-id="c830c-174">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="c830c-175">Om du vill söka efter ett certifikat använder du `Get-PfxCertificate` cmdleten eller använder `Get-ChildItem` cmdleten i certifikatet (cert:) kombinationsenhet.</span><span class="sxs-lookup"><span data-stu-id="c830c-175">To find a certificate, use the `Get-PfxCertificate` cmdlet or use the `Get-ChildItem` cmdlet in the Certificate (Cert:) drive.</span></span> <span data-ttu-id="c830c-176">Om certifikatet inte är giltigt eller inte har tillräcklig behörighet, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="c830c-176">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="c830c-177">– CommandName</span><span class="sxs-lookup"><span data-stu-id="c830c-177">-CommandName</span></span>

<span data-ttu-id="c830c-178">Exporterar endast kommandon med angivna namn eller namn mönster.</span><span class="sxs-lookup"><span data-stu-id="c830c-178">Exports only the commands with the specified names or name patterns.</span></span> <span data-ttu-id="c830c-179">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c830c-179">Wildcards are permitted.</span></span> <span data-ttu-id="c830c-180">Använd **commandname** eller dess alias, **namn**.</span><span class="sxs-lookup"><span data-stu-id="c830c-180">Use **CommandName** or its alias, **Name**.</span></span>

<span data-ttu-id="c830c-181">Som standard `Export-PSSession` exporterar alla kommandon från PSSession förutom kommandon som har samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c830c-181">By default, `Export-PSSession` exports all commands from the PSSession except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="c830c-182">Detta förhindrar att kommandon döljs eller ersätts av kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c830c-182">This prevents commands from being hidden or replaced by commands in the current session.</span></span> <span data-ttu-id="c830c-183">Om du vill exportera alla kommandon, även de som döljer eller ersätter andra kommandon, använder du parametern **AllowClobber** .</span><span class="sxs-lookup"><span data-stu-id="c830c-183">To export all commands, even those that hide or replace other commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="c830c-184">Om du använder parametern **commandname** exporteras inte filerna för kommandona om du inte använder parametern **FormatTypeName** .</span><span class="sxs-lookup"><span data-stu-id="c830c-184">If you use the **CommandName** parameter, the formatting files for the commands are not exported unless you use the **FormatTypeName** parameter.</span></span> <span data-ttu-id="c830c-185">Om du använder parametern **FormatTypeName** exporteras inte heller några kommandon om du inte använder parametern **commandname** .</span><span class="sxs-lookup"><span data-stu-id="c830c-185">Similarly, if you use the **FormatTypeName** parameter, no commands are exported unless you use the **CommandName** parameter.</span></span>

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

### <span data-ttu-id="c830c-186">-CommandType</span><span class="sxs-lookup"><span data-stu-id="c830c-186">-CommandType</span></span>

<span data-ttu-id="c830c-187">Exporterar endast de angivna typerna av kommando objekt.</span><span class="sxs-lookup"><span data-stu-id="c830c-187">Exports only the specified types of command objects.</span></span> <span data-ttu-id="c830c-188">Använd **CommandType** eller dess alias och **Skriv**.</span><span class="sxs-lookup"><span data-stu-id="c830c-188">Use **CommandType** or its alias, **Type**.</span></span>

<span data-ttu-id="c830c-189">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="c830c-189">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="c830c-190">Aliasuppsättning.</span><span class="sxs-lookup"><span data-stu-id="c830c-190">Alias.</span></span> <span data-ttu-id="c830c-191">Alla PowerShell-alias i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c830c-191">All PowerShell aliases in the current session.</span></span>
- <span data-ttu-id="c830c-192">Vissa.</span><span class="sxs-lookup"><span data-stu-id="c830c-192">All.</span></span> <span data-ttu-id="c830c-193">Alla kommando typer.</span><span class="sxs-lookup"><span data-stu-id="c830c-193">All command types.</span></span> <span data-ttu-id="c830c-194">Det motsvarar `Get-Command -Name *` .</span><span class="sxs-lookup"><span data-stu-id="c830c-194">It is the equivalent of `Get-Command -Name *`.</span></span>
- <span data-ttu-id="c830c-195">Applicering.</span><span class="sxs-lookup"><span data-stu-id="c830c-195">Application.</span></span> <span data-ttu-id="c830c-196">Alla filer förutom PowerShell-filer i sökvägar som anges i miljövariabeln PATH ( `$env:path` ), inklusive. txt-,. exe-och. dll-filer.</span><span class="sxs-lookup"><span data-stu-id="c830c-196">All files other than PowerShell files in paths listed in the Path environment variable (`$env:path`), including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="c830c-197">Kommandon.</span><span class="sxs-lookup"><span data-stu-id="c830c-197">Cmdlet.</span></span> <span data-ttu-id="c830c-198">Cmdletarna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c830c-198">The cmdlets in the current session.</span></span> <span data-ttu-id="c830c-199">Cmdlet är standard.</span><span class="sxs-lookup"><span data-stu-id="c830c-199">Cmdlet is the default.</span></span>
- <span data-ttu-id="c830c-200">Inställningarna.</span><span class="sxs-lookup"><span data-stu-id="c830c-200">Configuration.</span></span> <span data-ttu-id="c830c-201">En PowerShell-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="c830c-201">A PowerShell configuration.</span></span> <span data-ttu-id="c830c-202">Mer information finns i [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="c830c-202">For more information, see [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span></span>
- <span data-ttu-id="c830c-203">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="c830c-203">ExternalScript.</span></span> <span data-ttu-id="c830c-204">Alla. ps1-filer i Sök vägarna som anges i miljövariabeln PATH ( `$env:path` ).</span><span class="sxs-lookup"><span data-stu-id="c830c-204">All .ps1 files in the paths listed in the Path environment variable (`$env:path`).</span></span>
- <span data-ttu-id="c830c-205">Filter och funktion.</span><span class="sxs-lookup"><span data-stu-id="c830c-205">Filter and Function.</span></span> <span data-ttu-id="c830c-206">Alla PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="c830c-206">All PowerShell functions.</span></span>
- <span data-ttu-id="c830c-207">Över.</span><span class="sxs-lookup"><span data-stu-id="c830c-207">Script.</span></span> <span data-ttu-id="c830c-208">Skript block i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c830c-208">Script blocks in the current session.</span></span>
- <span data-ttu-id="c830c-209">Arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="c830c-209">Workflow.</span></span> <span data-ttu-id="c830c-210">Ett PowerShell-arbetsflöde.</span><span class="sxs-lookup"><span data-stu-id="c830c-210">A PowerShell workflow.</span></span> <span data-ttu-id="c830c-211">Mer information finns i [about_Workflows](../PSWorkflow/About/about_Workflows.md).</span><span class="sxs-lookup"><span data-stu-id="c830c-211">For more information, see [about_Workflows](../PSWorkflow/About/about_Workflows.md).</span></span>

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

### <span data-ttu-id="c830c-212">-Encoding</span><span class="sxs-lookup"><span data-stu-id="c830c-212">-Encoding</span></span>

<span data-ttu-id="c830c-213">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="c830c-213">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="c830c-214">Standardvärdet är `UTF8`.</span><span class="sxs-lookup"><span data-stu-id="c830c-214">The default value is `UTF8`.</span></span>

<span data-ttu-id="c830c-215">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="c830c-215">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="c830c-216">`ASCII` Använder ASCII-teckenuppsättning (7-bitars).</span><span class="sxs-lookup"><span data-stu-id="c830c-216">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="c830c-217">`BigEndianUnicode` Använder UTF-16 med big-endian byte-ordningen.</span><span class="sxs-lookup"><span data-stu-id="c830c-217">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="c830c-218">`Default` Använder den kodning som motsvarar systemets aktiva tecken tabell.</span><span class="sxs-lookup"><span data-stu-id="c830c-218">`Default` Uses the encoding that corresponds to the system's active code page.</span></span>
- <span data-ttu-id="c830c-219">`OEM` Använder kodningen som motsvarar systemets aktuella OEM Code-sida.</span><span class="sxs-lookup"><span data-stu-id="c830c-219">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="c830c-220">`Unicode` Använder UTF-16 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="c830c-220">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="c830c-221">`UTF7` Använder UTF-7.</span><span class="sxs-lookup"><span data-stu-id="c830c-221">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="c830c-222">`UTF8` Använder UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c830c-222">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="c830c-223">`UTF32` Använder UTF-32 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="c830c-223">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: UTF8
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c830c-224">-Force</span><span class="sxs-lookup"><span data-stu-id="c830c-224">-Force</span></span>

<span data-ttu-id="c830c-225">Skriver över en eller flera befintliga utdatafiler, även om filen har attributet skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="c830c-225">Overwrites one or more existing output files, even if the file has the read-only attribute.</span></span>

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

### <span data-ttu-id="c830c-226">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="c830c-226">-FormatTypeName</span></span>

<span data-ttu-id="c830c-227">Exporterar bara formateringsregler för de angivna Microsoft .NET Ramverks typerna.</span><span class="sxs-lookup"><span data-stu-id="c830c-227">Exports formatting instructions only for the specified Microsoft .NET Framework types.</span></span> <span data-ttu-id="c830c-228">Ange typ namn.</span><span class="sxs-lookup"><span data-stu-id="c830c-228">Enter the type names.</span></span> <span data-ttu-id="c830c-229">Som standard `Export-PSSession` exporterar formaterings instruktioner för alla .NET Framework typer som inte finns i namn området **system. Management. Automation** .</span><span class="sxs-lookup"><span data-stu-id="c830c-229">By default, `Export-PSSession` exports formatting instructions for all .NET Framework types that are not in the **System.Management.Automation** namespace.</span></span>

<span data-ttu-id="c830c-230">Värdet för den här parametern måste vara namnet på en typ som returneras av ett `Get-FormatData` kommando i den session som kommandona importeras från.</span><span class="sxs-lookup"><span data-stu-id="c830c-230">The value of this parameter must be the name of a type that is returned by a `Get-FormatData` command in the session from which the commands are being imported.</span></span> <span data-ttu-id="c830c-231">Om du vill hämta alla formaterings data i fjärrsessionen skriver du `*` .</span><span class="sxs-lookup"><span data-stu-id="c830c-231">To get all of the formatting data in the remote session, type `*`.</span></span>

<span data-ttu-id="c830c-232">Om du använder parametern **FormatTypeName** exporteras inga kommandon om du inte använder parametern **commandname** .</span><span class="sxs-lookup"><span data-stu-id="c830c-232">If you use the **FormatTypeName** parameter, no commands are exported unless you use the **CommandName** parameter.</span></span>

<span data-ttu-id="c830c-233">Om du använder parametern **commandname** exporteras inte filerna för kommandona om du inte använder parametern **FormatTypeName** .</span><span class="sxs-lookup"><span data-stu-id="c830c-233">If you use the **CommandName** parameter, the formatting files for the commands are not exported unless you use the **FormatTypeName** parameter.</span></span>

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

### <span data-ttu-id="c830c-234">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="c830c-234">-FullyQualifiedModule</span></span>

<span data-ttu-id="c830c-235">Anger moduler med namn som anges i form av **ModuleSpecification** -objekt.</span><span class="sxs-lookup"><span data-stu-id="c830c-235">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span> <span data-ttu-id="c830c-236">Se avsnittet anmärkningar i [ModuleSpecification-konstruktorn (hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="c830c-236">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="c830c-237">**FullyQualifiedModule** -parametern accepterar till exempel ett modulnamn som anges i något av följande format:</span><span class="sxs-lookup"><span data-stu-id="c830c-237">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="c830c-238">**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="c830c-238">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="c830c-239">Det går inte att ange parametern **FullyQualifiedModule** i samma kommando som en **modul** -parameter.</span><span class="sxs-lookup"><span data-stu-id="c830c-239">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="c830c-240">de två parametrarna kan inte anges samtidigt.</span><span class="sxs-lookup"><span data-stu-id="c830c-240">the two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="c830c-241">– Modul</span><span class="sxs-lookup"><span data-stu-id="c830c-241">-Module</span></span>

<span data-ttu-id="c830c-242">Exporterar endast kommandona i de angivna PowerShell-snapin-modulerna och modulerna.</span><span class="sxs-lookup"><span data-stu-id="c830c-242">Exports only the commands in the specified PowerShell snap-ins and modules.</span></span> <span data-ttu-id="c830c-243">Ange namnet på snapin-modulen och-modulen.</span><span class="sxs-lookup"><span data-stu-id="c830c-243">Enter the snap-in and module names.</span></span> <span data-ttu-id="c830c-244">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c830c-244">Wildcards are not permitted.</span></span>

<span data-ttu-id="c830c-245">Mer information finns i `Import-Module` och [about_PSSnapins](../Microsoft.PowerShell.Core/About/about_PSSnapins.md).</span><span class="sxs-lookup"><span data-stu-id="c830c-245">For more information, see `Import-Module` and [about_PSSnapins](../Microsoft.PowerShell.Core/About/about_PSSnapins.md).</span></span>

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

### <span data-ttu-id="c830c-246">-OutputModule</span><span class="sxs-lookup"><span data-stu-id="c830c-246">-OutputModule</span></span>

<span data-ttu-id="c830c-247">Anger en valfri sökväg och ett namn för modulen som skapats av `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="c830c-247">Specifies an optional path and name for the module created by `Export-PSSession`.</span></span> <span data-ttu-id="c830c-248">Standard Sök vägen är `$home\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="c830c-248">The default path is `$home\Documents\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="c830c-249">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="c830c-249">This parameter is required.</span></span>

<span data-ttu-id="c830c-250">Om modulens under katalog eller någon av de filer som `Export-PSSession` skapas redan finns, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="c830c-250">If the module subdirectory or any of the files that `Export-PSSession` creates already exist, the command fails.</span></span> <span data-ttu-id="c830c-251">Använd parametern **Force** om du vill skriva över befintliga filer.</span><span class="sxs-lookup"><span data-stu-id="c830c-251">To overwrite existing files, use the **Force** parameter.</span></span>

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

### <span data-ttu-id="c830c-252">– Session</span><span class="sxs-lookup"><span data-stu-id="c830c-252">-Session</span></span>

<span data-ttu-id="c830c-253">Anger den PSSession som kommandona exporteras från.</span><span class="sxs-lookup"><span data-stu-id="c830c-253">Specifies the PSSession from which the commands are exported.</span></span> <span data-ttu-id="c830c-254">Ange en variabel som innehåller ett session-objekt eller ett kommando som hämtar ett sessionsobjekt, till exempel ett `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="c830c-254">Enter a variable that contains a session object or a command that gets a session object, such as a `Get-PSSession` command.</span></span> <span data-ttu-id="c830c-255">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="c830c-255">This parameter is required.</span></span>

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

### <span data-ttu-id="c830c-256">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c830c-256">CommonParameters</span></span>

<span data-ttu-id="c830c-257">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c830c-257">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c830c-258">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c830c-258">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c830c-259">INDATA</span><span class="sxs-lookup"><span data-stu-id="c830c-259">INPUTS</span></span>

### <span data-ttu-id="c830c-260">Inget</span><span class="sxs-lookup"><span data-stu-id="c830c-260">None</span></span>

<span data-ttu-id="c830c-261">Det går inte att skicka pipe-objekt till `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="c830c-261">You cannot pipe objects to `Export-PSSession`.</span></span>

## <span data-ttu-id="c830c-262">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c830c-262">OUTPUTS</span></span>

### <span data-ttu-id="c830c-263">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="c830c-263">System.IO.FileInfo</span></span>

<span data-ttu-id="c830c-264">`Export-PSSession` Returnerar en lista med filer som utgör den modul som den skapade.</span><span class="sxs-lookup"><span data-stu-id="c830c-264">`Export-PSSession` returns a list of files that comprise the module that it created.</span></span>

## <span data-ttu-id="c830c-265">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c830c-265">NOTES</span></span>

<span data-ttu-id="c830c-266">`Export-PSSession` förlitar sig på PowerShell-infrastrukturen för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="c830c-266">`Export-PSSession` relies on the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="c830c-267">Om du vill använda denna cmdlet måste datorn konfigureras för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="c830c-267">To use this cmdlet, the computer must be configured for remoting.</span></span> <span data-ttu-id="c830c-268">Mer information finns i [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c830c-268">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="c830c-269">Du kan inte använda `Export-PSSession` för att exportera en PowerShell-Provider.</span><span class="sxs-lookup"><span data-stu-id="c830c-269">You cannot use `Export-PSSession` to export a PowerShell provider.</span></span>

<span data-ttu-id="c830c-270">Exporterade kommandon körs implicit i PSSession som de exporterades från.</span><span class="sxs-lookup"><span data-stu-id="c830c-270">Exported commands run implicitly in the PSSession from which they were exported.</span></span> <span data-ttu-id="c830c-271">Information om hur du kör fjärrkommandona hanteras helt och hållet av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c830c-271">The details of running the commands remotely are handled entirely by PowerShell.</span></span> <span data-ttu-id="c830c-272">Du kan köra de exporterade kommandona på samma sätt som du kör lokala kommandon.</span><span class="sxs-lookup"><span data-stu-id="c830c-272">You can run the exported commands just as you would run local commands.</span></span>

<span data-ttu-id="c830c-273">`Export-ModuleMember` fångar och sparar information om PSSession i den modul som den exporterar.</span><span class="sxs-lookup"><span data-stu-id="c830c-273">`Export-ModuleMember` captures and saves information about the PSSession in the module that it exports.</span></span> <span data-ttu-id="c830c-274">Om PSSession som kommandona exporterades från stängs när du importerar modulen, och det inte finns några aktiva PSSessions på samma dator, försöker kommandona i modulen återskapa PSSession.</span><span class="sxs-lookup"><span data-stu-id="c830c-274">If the PSSession from which the commands were exported is closed when you import the module, and there are no active PSSessions to the same computer, the commands in the module attempt to recreate the PSSession.</span></span> <span data-ttu-id="c830c-275">Om försök att återskapa PSSession Miss lyckas kommer de exporterade kommandona inte att köras.</span><span class="sxs-lookup"><span data-stu-id="c830c-275">If attempts to recreate the PSSession fail, the exported commands will not run.</span></span>

<span data-ttu-id="c830c-276">Sessionsinformation som `Export-ModuleMember` fångar in och sparar i modulen omfattar inte sessionsinställningar, till exempel de som du anger i `$PSSessionOption` variabeln Preference eller med hjälp av parametern **SessionOption** i `New-PSSession` `Enter-PSSession` cmdletarna,, eller `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="c830c-276">The session information that `Export-ModuleMember` captures and saves in the module does not include session options, such as those that you specify in the `$PSSessionOption` preference variable or by using the **SessionOption** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlets.</span></span> <span data-ttu-id="c830c-277">Om den ursprungliga PSSession stängs när du importerar modulen använder modulen en annan PSSession på samma dator, om en sådan finns tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="c830c-277">If the original PSSession is closed when you import the module, the module will use another PSSession to the same computer, if one is available.</span></span> <span data-ttu-id="c830c-278">Om du vill aktivera de importerade kommandona att köras i en korrekt konfigurerad session skapar du en PSSession med de alternativ som du vill använda innan du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="c830c-278">To enable the imported commands to run in a correctly configured session, create a PSSession with the options that you want before you import the module.</span></span>

<span data-ttu-id="c830c-279">För att hitta de kommandon som ska exporteras `Export-PSSession` använder `Invoke-Command` cmdleten för att köra ett `Get-Command` kommando i PSSession.</span><span class="sxs-lookup"><span data-stu-id="c830c-279">To find the commands to export, `Export-PSSession` uses the `Invoke-Command` cmdlet to run a `Get-Command` command in the PSSession.</span></span> <span data-ttu-id="c830c-280">För att hämta och spara formaterings data för kommandona används `Get-FormatData` `Export-FormatData` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="c830c-280">To get and save formatting data for the commands, it uses the `Get-FormatData` and `Export-FormatData` cmdlets.</span></span> <span data-ttu-id="c830c-281">Du kan se fel meddelanden från `Invoke-Command` , `Get-Command` , `Get-FormatData` och `Export-FormatData` när du kör ett `Export-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="c830c-281">You might see error messages from `Invoke-Command`, `Get-Command`, `Get-FormatData`, and `Export-FormatData` when you run an `Export-PSSession` command.</span></span> <span data-ttu-id="c830c-282">`Export-PSSession`Kan inte heller exportera kommandon från en-session som inte innehåller `Get-Command` `Get-FormatData` `Select-Object` cmdletarna,, och `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="c830c-282">Also, `Export-PSSession` cannot export commands from a session that does not include the `Get-Command`, `Get-FormatData`, `Select-Object`, and `Get-Help` cmdlets.</span></span>

<span data-ttu-id="c830c-283">`Export-PSSession` använder `Write-Progress` cmdleten för att visa förloppet för kommandot.</span><span class="sxs-lookup"><span data-stu-id="c830c-283">`Export-PSSession` uses the `Write-Progress` cmdlet to display the progress of the command.</span></span> <span data-ttu-id="c830c-284">Du kan se förlopps indikatorn när kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="c830c-284">You might see the progress bar while the command is running.</span></span>

<span data-ttu-id="c830c-285">Exporterade kommandon har samma begränsningar som andra fjärrkommandon, inklusive möjligheten att starta ett program med ett användar gränssnitt, t. ex. anteckningar.</span><span class="sxs-lookup"><span data-stu-id="c830c-285">Exported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>

<span data-ttu-id="c830c-286">Eftersom PowerShell-profiler inte körs i PSSessions är kommandona som en profil lägger till i en session inte tillgängliga för `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="c830c-286">Because PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to `Export-PSSession`.</span></span> <span data-ttu-id="c830c-287">Om du vill exportera kommandon från en profil använder du ett `Invoke-Command` kommando för att köra profilen i PSSession manuellt innan du exporterar kommandon.</span><span class="sxs-lookup"><span data-stu-id="c830c-287">To export commands from a profile, use an `Invoke-Command` command to run the profile in the PSSession manually before exporting commands.</span></span>

<span data-ttu-id="c830c-288">Modulen som `Export-PSSession` skapar kan innehålla en formateringsinformation, även om kommandot inte importerar formaterings data.</span><span class="sxs-lookup"><span data-stu-id="c830c-288">The module that `Export-PSSession` creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="c830c-289">Om kommandot inte importerar dataformaterade data kommer eventuella filer som skapas inte att innehålla formatering.</span><span class="sxs-lookup"><span data-stu-id="c830c-289">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>

## <span data-ttu-id="c830c-290">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c830c-290">RELATED LINKS</span></span>

[<span data-ttu-id="c830c-291">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="c830c-291">about_Command_Precedence</span></span>](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)

[<span data-ttu-id="c830c-292">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="c830c-292">about_PSSessions</span></span>](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[<span data-ttu-id="c830c-293">about_PSSnapins</span><span class="sxs-lookup"><span data-stu-id="c830c-293">about_PSSnapins</span></span>](../Microsoft.PowerShell.Core/About/about_PSSnapins.md)

[<span data-ttu-id="c830c-294">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="c830c-294">about_Remote_Requirements</span></span>](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)

[<span data-ttu-id="c830c-295">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="c830c-295">Import-Module</span></span>](../Microsoft.PowerShell.Core/Import-Module.md)

[<span data-ttu-id="c830c-296">Importera – PSSession</span><span class="sxs-lookup"><span data-stu-id="c830c-296">Import-PSSession</span></span>](Import-PSSession.md)

[<span data-ttu-id="c830c-297">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="c830c-297">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="c830c-298">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="c830c-298">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="c830c-299">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="c830c-299">New-PSSessionOption</span></span>](../Microsoft.PowerShell.Core/New-PSSessionOption.md)

[<span data-ttu-id="c830c-300">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="c830c-300">Remove-PSSession</span></span>](../Microsoft.PowerShell.Core/Remove-PSSession.md)
