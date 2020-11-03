---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-hotfix?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-HotFix
ms.openlocfilehash: 355257d0e403143d6983886de592d491241c6253
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263948"
---
# <span data-ttu-id="e7db8-103">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="e7db8-103">Get-HotFix</span></span>

## <span data-ttu-id="e7db8-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e7db8-104">SYNOPSIS</span></span>
<span data-ttu-id="e7db8-105">Hämtar snabb korrigeringarna som installeras på lokala eller fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="e7db8-105">Gets the hotfixes that are installed on local or remote computers.</span></span>

## <span data-ttu-id="e7db8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e7db8-106">SYNTAX</span></span>

### <span data-ttu-id="e7db8-107">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="e7db8-107">Default (Default)</span></span>

```
Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

### <span data-ttu-id="e7db8-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e7db8-108">Description</span></span>

```
Get-HotFix [-Description <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

## <span data-ttu-id="e7db8-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e7db8-109">DESCRIPTION</span></span>

<span data-ttu-id="e7db8-110">`Get-Hotfix`Cmdlet: en hämtar snabb korrigeringar eller uppdateringar som är installerade på den lokala datorn eller angivna fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="e7db8-110">The `Get-Hotfix` cmdlet gets hotfixes, or updates, that are installed on the local computer or specified remote computers.</span></span> <span data-ttu-id="e7db8-111">Uppdateringarna kan installeras av Windows Update, Microsoft Update, Windows Server Update Services eller installeras manuellt.</span><span class="sxs-lookup"><span data-stu-id="e7db8-111">The updates can be installed by Windows Update, Microsoft Update, Windows Server Update Services, or manually installed.</span></span>

## <span data-ttu-id="e7db8-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e7db8-112">EXAMPLES</span></span>

### <span data-ttu-id="e7db8-113">Exempel 1: Hämta alla snabb korrigeringar på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="e7db8-113">Example 1: Get all hotfixes on the local computer</span></span>

<span data-ttu-id="e7db8-114">`Get-Hotfix`Cmdlet: en hämtar alla snabb korrigeringar som är installerade på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e7db8-114">The `Get-Hotfix` cmdlet gets all hotfixes installed on the local computer.</span></span>

```powershell
Get-HotFix
```

```output
Source         Description      HotFixID      InstalledBy          InstalledOn
------         -----------      --------      -----------          -----------
Server01       Update           KB4495590     NT AUTHORITY\SYSTEM  5/16/2019 00:00:00
Server01       Security Update  KB4470788     NT AUTHORITY\SYSTEM  1/22/2019 00:00:00
Server01       Update           KB4480056     NT AUTHORITY\SYSTEM  1/24/2019 00:00:00
```

### <span data-ttu-id="e7db8-115">Exempel 2: Hämta snabb korrigeringar från flera datorer som filtrerats med en sträng</span><span class="sxs-lookup"><span data-stu-id="e7db8-115">Example 2: Get hotfixes from multiple computers filtered by a string</span></span>

<span data-ttu-id="e7db8-116">`Get-Hotfix`Kommandot använder parametrar för att hämta snabb korrigeringar som är installerade på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="e7db8-116">The `Get-Hotfix` command uses parameters to get hotfixes installed on remote computers.</span></span> <span data-ttu-id="e7db8-117">Resultaten filtreras efter en angiven beskrivnings sträng.</span><span class="sxs-lookup"><span data-stu-id="e7db8-117">The results are filtered by a specified description string.</span></span>

```
PS> Get-HotFix -Description Security* -ComputerName Server01, Server02 -Credential Domain01\admin01
```

<span data-ttu-id="e7db8-118">`Get-Hotfix` filtrerar utdata med **beskrivnings** parametern och sträng **säkerheten** som innehåller jokertecknet asterisk ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="e7db8-118">`Get-Hotfix` filters the output with the **Description** parameter and the string **Security** that includes the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="e7db8-119">Parametern **computername** innehåller en kommaavgränsad sträng med fjärrdatornamn.</span><span class="sxs-lookup"><span data-stu-id="e7db8-119">The **ComputerName** parameter includes a comma-separated string of remote computer names.</span></span> <span data-ttu-id="e7db8-120">Parametern **Credential** anger ett användar konto som har behörighet att komma åt fjärrdatorerna och köra kommandon.</span><span class="sxs-lookup"><span data-stu-id="e7db8-120">The **Credential** parameter specifies a user account that has permission to access the remote computers and run commands.</span></span>

### <span data-ttu-id="e7db8-121">Exempel 3: kontrol lera om en uppdatering har installerats och skriv dator namn till en fil</span><span class="sxs-lookup"><span data-stu-id="e7db8-121">Example 3: Verify if an update is installed and write computer names to a file</span></span>

<span data-ttu-id="e7db8-122">Kommandona i det här exemplet verifierar om en viss uppdatering har installerats.</span><span class="sxs-lookup"><span data-stu-id="e7db8-122">The commands in this example verify whether a particular update installed.</span></span> <span data-ttu-id="e7db8-123">Om uppdateringen inte är installerad skrivs dator namnet till en textfil.</span><span class="sxs-lookup"><span data-stu-id="e7db8-123">If the update isn't installed, the computer name is written to a text file.</span></span>

```
PS> $A = Get-Content -Path ./Servers.txt
PS> $A | ForEach-Object { if (!(Get-HotFix -Id KB957095 -ComputerName $_))
         { Add-Content $_ -Path ./Missing-KB957095.txt }}
```

<span data-ttu-id="e7db8-124">`$A`Variabeln innehåller dator namn som hämtades `Get-Content` från en textfil.</span><span class="sxs-lookup"><span data-stu-id="e7db8-124">The `$A` variable contains computer names that were obtained by `Get-Content` from a text file.</span></span> <span data-ttu-id="e7db8-125">De objekt som `$A` finns i skickas pipelinen till `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="e7db8-125">The objects in `$A` are sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="e7db8-126">En `if` instruktion använder `Get-Hotfix` cmdleten med **ID-** parametern och ett särskilt ID-nummer för varje dator namn.</span><span class="sxs-lookup"><span data-stu-id="e7db8-126">An `if` statement uses the `Get-Hotfix` cmdlet with the **Id** parameter and a specific Id number for each computer name.</span></span> <span data-ttu-id="e7db8-127">Om en dator inte har angivet snabb korrigerings-ID installerat, `Add-Content` skriver cmdleten dator namnet till en fil.</span><span class="sxs-lookup"><span data-stu-id="e7db8-127">If a computer doesn't have the specified hotfix Id installed, the `Add-Content` cmdlet writes the computer name to a file.</span></span>

### <span data-ttu-id="e7db8-128">Exempel 4: hämta den senaste snabb korrigeringen på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="e7db8-128">Example 4: Get the most recent hotfix on the local computer</span></span>

<span data-ttu-id="e7db8-129">Det här exemplet hämtar den senaste snabb korrigeringen som är installerad på en dator.</span><span class="sxs-lookup"><span data-stu-id="e7db8-129">This example gets the most recent hotfix installed on a computer.</span></span>

```powershell
(Get-HotFix | Sort-Object -Property InstalledOn)[-1]
```

<span data-ttu-id="e7db8-130">`Get-Hotfix` skickar objekten nedåt i pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e7db8-130">`Get-Hotfix` sends the objects down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="e7db8-131">`Sort-Object` sorterar objekt efter stigande ordning och använder **egenskaps** parametern för att utvärdera varje **InstalledOn** datum.</span><span class="sxs-lookup"><span data-stu-id="e7db8-131">`Sort-Object` sorts objects by ascending order and uses the **Property** parameter to evaluate each **InstalledOn** date.</span></span> <span data-ttu-id="e7db8-132">Mat ris notationen `[-1]` väljer den senaste installerade snabb korrigeringen.</span><span class="sxs-lookup"><span data-stu-id="e7db8-132">The array notation `[-1]` selects the most recent installed hotfix.</span></span>

## <span data-ttu-id="e7db8-133">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e7db8-133">PARAMETERS</span></span>

### <span data-ttu-id="e7db8-134">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="e7db8-134">-ComputerName</span></span>

<span data-ttu-id="e7db8-135">Anger en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="e7db8-135">Specifies a remote computer.</span></span> <span data-ttu-id="e7db8-136">Ange NetBIOS-namnet, en Internet Protocol IP-adress eller ett fullständigt kvalificerat domän namn (FQDN) för en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="e7db8-136">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>

<span data-ttu-id="e7db8-137">När parametern **computername** inte anges körs den `Get-Hotfix` på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e7db8-137">When the **ComputerName** parameter isn't specified, `Get-Hotfix` runs on the local computer.</span></span>

<span data-ttu-id="e7db8-138">Parametern **computername** är inte beroende av Windows PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="e7db8-138">The **ComputerName** parameter doesn't rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="e7db8-139">Om datorn inte är konfigurerad för att köra fjärrkommandon använder du parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="e7db8-139">If your computer isn't configured to run remote commands, use the **ComputerName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __Server, IPAddress

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e7db8-140">-Credential</span><span class="sxs-lookup"><span data-stu-id="e7db8-140">-Credential</span></span>

<span data-ttu-id="e7db8-141">Anger ett användar konto som har behörighet att komma åt datorn och köra kommandon.</span><span class="sxs-lookup"><span data-stu-id="e7db8-141">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="e7db8-142">Standardvärdet är den aktuella användaren</span><span class="sxs-lookup"><span data-stu-id="e7db8-142">The default is the current user</span></span>

<span data-ttu-id="e7db8-143">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e7db8-143">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="e7db8-144">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="e7db8-144">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="e7db8-145">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="e7db8-145">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="e7db8-146">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="e7db8-146">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7db8-147">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e7db8-147">-Description</span></span>

<span data-ttu-id="e7db8-148">`Get-HotFix` använder **Description** -parametern för att ange snabb korrigerings typer.</span><span class="sxs-lookup"><span data-stu-id="e7db8-148">`Get-HotFix` uses the **Description** parameter to specify hotfix types.</span></span> <span data-ttu-id="e7db8-149">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e7db8-149">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Description
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e7db8-150">-ID</span><span class="sxs-lookup"><span data-stu-id="e7db8-150">-Id</span></span>

<span data-ttu-id="e7db8-151">Filtrerar `Get-HotFix` resultaten för vissa snabb korrigerings-ID: n.</span><span class="sxs-lookup"><span data-stu-id="e7db8-151">Filters the `Get-HotFix` results for specific hotfix Ids.</span></span> <span data-ttu-id="e7db8-152">Jokertecken accepteras inte.</span><span class="sxs-lookup"><span data-stu-id="e7db8-152">Wildcards aren't accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: HFID

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7db8-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e7db8-153">CommonParameters</span></span>

<span data-ttu-id="e7db8-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e7db8-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e7db8-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e7db8-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e7db8-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="e7db8-156">INPUTS</span></span>

### <span data-ttu-id="e7db8-157">Sträng</span><span class="sxs-lookup"><span data-stu-id="e7db8-157">String</span></span>

<span data-ttu-id="e7db8-158">Du kan skicka ett eller flera dator namn för att få snabb korrigering.</span><span class="sxs-lookup"><span data-stu-id="e7db8-158">You can pipe one or more computer names to Get-HotFix.</span></span>

## <span data-ttu-id="e7db8-159">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e7db8-159">OUTPUTS</span></span>

### <span data-ttu-id="e7db8-160">System. Management. ManagementObject # root\CIMV2\ Win32_QuickFixEngineering</span><span class="sxs-lookup"><span data-stu-id="e7db8-160">System.Management.ManagementObject#root\CIMV2\Win32_QuickFixEngineering</span></span>

<span data-ttu-id="e7db8-161">`Get-HotFix` returnerar objekt som representerar snabb korrigeringarna på datorn.</span><span class="sxs-lookup"><span data-stu-id="e7db8-161">`Get-HotFix` returns objects that represent the hotfixes on the computer.</span></span>

## <span data-ttu-id="e7db8-162">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e7db8-162">NOTES</span></span>

<span data-ttu-id="e7db8-163">**Win32_QuickFixEngineering** [WMI-klassen](/windows/desktop/WmiSdk/retrieving-a-class) representerar en mindre systemomfattande uppdatering, vanligt vis kallat snabb korrigerings teknik (QFE), som tillämpas på det aktuella operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="e7db8-163">The **Win32_QuickFixEngineering** [WMI class](/windows/desktop/WmiSdk/retrieving-a-class) represents a small system-wide update, commonly referred to as a quick-fix engineering (QFE) update, applied to the current operating system.</span></span> <span data-ttu-id="e7db8-164">Den här klassen returnerar endast uppdateringar som tillhandahålls av Component Based Servicing (CBS).</span><span class="sxs-lookup"><span data-stu-id="e7db8-164">This class returns only the updates supplied by Component Based Servicing (CBS).</span></span> <span data-ttu-id="e7db8-165">De här uppdateringarna visas inte i registret.</span><span class="sxs-lookup"><span data-stu-id="e7db8-165">These updates are not listed in the registry.</span></span> <span data-ttu-id="e7db8-166">Uppdateringar som tillhandahålls av Microsoft Windows Installer (MSI) eller [Windows updates](https://update.microsoft.com) platsen returneras inte av **Win32_QuickFixEngineering**.</span><span class="sxs-lookup"><span data-stu-id="e7db8-166">Updates supplied by Microsoft Windows Installer (MSI) or the [Windows Update](https://update.microsoft.com) site are not returned by **Win32_QuickFixEngineering**.</span></span> <span data-ttu-id="e7db8-167">Mer information finns i [Win32_QuickFixEngineering-klass](/windows/desktop/CIMWin32Prov/win32-quickfixengineering).</span><span class="sxs-lookup"><span data-stu-id="e7db8-167">For more information, see [Win32_QuickFixEngineering class](/windows/desktop/CIMWin32Prov/win32-quickfixengineering).</span></span>

<span data-ttu-id="e7db8-168">`Get-HotFix`Utdata kan variera mellan olika operativ system.</span><span class="sxs-lookup"><span data-stu-id="e7db8-168">The `Get-HotFix` output might vary on different operating systems.</span></span>

## <span data-ttu-id="e7db8-169">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e7db8-169">RELATED LINKS</span></span>

[<span data-ttu-id="e7db8-170">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="e7db8-170">about_Arrays</span></span>](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[<span data-ttu-id="e7db8-171">Lägg till innehåll</span><span class="sxs-lookup"><span data-stu-id="e7db8-171">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="e7db8-172">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="e7db8-172">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="e7db8-173">Win32_QuickFixEngineering klass</span><span class="sxs-lookup"><span data-stu-id="e7db8-173">Win32_QuickFixEngineering class</span></span>](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)
