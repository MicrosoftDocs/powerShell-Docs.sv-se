---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-hotfix?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-HotFix
ms.openlocfilehash: 5b5b5939d4dcae8a99b1030b533fe6a85bcc601a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708399"
---
# <span data-ttu-id="8d294-102">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="8d294-102">Get-HotFix</span></span>

## <span data-ttu-id="8d294-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8d294-103">SYNOPSIS</span></span>
<span data-ttu-id="8d294-104">Hämtar snabb korrigeringarna som installeras på lokala eller fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="8d294-104">Gets the hotfixes that are installed on local or remote computers.</span></span>

## <span data-ttu-id="8d294-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8d294-105">SYNTAX</span></span>

### <span data-ttu-id="8d294-106">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="8d294-106">Default (Default)</span></span>

```
Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

### <span data-ttu-id="8d294-107">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d294-107">Description</span></span>

```
Get-HotFix [-Description <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

## <span data-ttu-id="8d294-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8d294-108">DESCRIPTION</span></span>

<span data-ttu-id="8d294-109">`Get-Hotfix`Cmdlet: en hämtar snabb korrigeringar eller uppdateringar som är installerade på den lokala datorn eller angivna fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="8d294-109">The `Get-Hotfix` cmdlet gets hotfixes, or updates, that are installed on the local computer or specified remote computers.</span></span> <span data-ttu-id="8d294-110">Uppdateringarna kan installeras av Windows Update, Microsoft Update, Windows Server Update Services eller installeras manuellt.</span><span class="sxs-lookup"><span data-stu-id="8d294-110">The updates can be installed by Windows Update, Microsoft Update, Windows Server Update Services, or manually installed.</span></span>

## <span data-ttu-id="8d294-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8d294-111">EXAMPLES</span></span>

### <span data-ttu-id="8d294-112">Exempel 1: Hämta alla snabb korrigeringar på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="8d294-112">Example 1: Get all hotfixes on the local computer</span></span>

<span data-ttu-id="8d294-113">`Get-Hotfix`Cmdlet: en hämtar alla snabb korrigeringar som är installerade på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8d294-113">The `Get-Hotfix` cmdlet gets all hotfixes installed on the local computer.</span></span>

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

### <span data-ttu-id="8d294-114">Exempel 2: Hämta snabb korrigeringar från flera datorer som filtrerats med en sträng</span><span class="sxs-lookup"><span data-stu-id="8d294-114">Example 2: Get hotfixes from multiple computers filtered by a string</span></span>

<span data-ttu-id="8d294-115">`Get-Hotfix`Kommandot använder parametrar för att hämta snabb korrigeringar som är installerade på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="8d294-115">The `Get-Hotfix` command uses parameters to get hotfixes installed on remote computers.</span></span> <span data-ttu-id="8d294-116">Resultaten filtreras efter en angiven beskrivnings sträng.</span><span class="sxs-lookup"><span data-stu-id="8d294-116">The results are filtered by a specified description string.</span></span>

```
PS> Get-HotFix -Description Security* -ComputerName Server01, Server02 -Credential Domain01\admin01
```

<span data-ttu-id="8d294-117">`Get-Hotfix` filtrerar utdata med **beskrivnings** parametern och sträng **säkerheten** som innehåller jokertecknet asterisk ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="8d294-117">`Get-Hotfix` filters the output with the **Description** parameter and the string **Security** that includes the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="8d294-118">Parametern **computername** innehåller en kommaavgränsad sträng med fjärrdatornamn.</span><span class="sxs-lookup"><span data-stu-id="8d294-118">The **ComputerName** parameter includes a comma-separated string of remote computer names.</span></span> <span data-ttu-id="8d294-119">Parametern **Credential** anger ett användar konto som har behörighet att komma åt fjärrdatorerna och köra kommandon.</span><span class="sxs-lookup"><span data-stu-id="8d294-119">The **Credential** parameter specifies a user account that has permission to access the remote computers and run commands.</span></span>

### <span data-ttu-id="8d294-120">Exempel 3: kontrol lera om en uppdatering har installerats och skriv dator namn till en fil</span><span class="sxs-lookup"><span data-stu-id="8d294-120">Example 3: Verify if an update is installed and write computer names to a file</span></span>

<span data-ttu-id="8d294-121">Kommandona i det här exemplet verifierar om en viss uppdatering har installerats.</span><span class="sxs-lookup"><span data-stu-id="8d294-121">The commands in this example verify whether a particular update installed.</span></span> <span data-ttu-id="8d294-122">Om uppdateringen inte är installerad skrivs dator namnet till en textfil.</span><span class="sxs-lookup"><span data-stu-id="8d294-122">If the update isn't installed, the computer name is written to a text file.</span></span>

```
PS> $A = Get-Content -Path ./Servers.txt
PS> $A | ForEach-Object { if (!(Get-HotFix -Id KB957095 -ComputerName $_))
         { Add-Content $_ -Path ./Missing-KB957095.txt }}
```

<span data-ttu-id="8d294-123">`$A`Variabeln innehåller dator namn som hämtades `Get-Content` från en textfil.</span><span class="sxs-lookup"><span data-stu-id="8d294-123">The `$A` variable contains computer names that were obtained by `Get-Content` from a text file.</span></span> <span data-ttu-id="8d294-124">De objekt som `$A` finns i skickas pipelinen till `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="8d294-124">The objects in `$A` are sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="8d294-125">En `if` instruktion använder `Get-Hotfix` cmdleten med **ID-** parametern och ett särskilt ID-nummer för varje dator namn.</span><span class="sxs-lookup"><span data-stu-id="8d294-125">An `if` statement uses the `Get-Hotfix` cmdlet with the **Id** parameter and a specific Id number for each computer name.</span></span> <span data-ttu-id="8d294-126">Om en dator inte har angivet snabb korrigerings-ID installerat, `Add-Content` skriver cmdleten dator namnet till en fil.</span><span class="sxs-lookup"><span data-stu-id="8d294-126">If a computer doesn't have the specified hotfix Id installed, the `Add-Content` cmdlet writes the computer name to a file.</span></span>

### <span data-ttu-id="8d294-127">Exempel 4: hämta den senaste snabb korrigeringen på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="8d294-127">Example 4: Get the most recent hotfix on the local computer</span></span>

<span data-ttu-id="8d294-128">Det här exemplet hämtar den senaste snabb korrigeringen som är installerad på en dator.</span><span class="sxs-lookup"><span data-stu-id="8d294-128">This example gets the most recent hotfix installed on a computer.</span></span>

```powershell
(Get-HotFix | Sort-Object -Property InstalledOn)[-1]
```

<span data-ttu-id="8d294-129">`Get-Hotfix` skickar objekten nedåt i pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8d294-129">`Get-Hotfix` sends the objects down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="8d294-130">`Sort-Object` sorterar objekt efter stigande ordning och använder **egenskaps** parametern för att utvärdera varje **InstalledOn** datum.</span><span class="sxs-lookup"><span data-stu-id="8d294-130">`Sort-Object` sorts objects by ascending order and uses the **Property** parameter to evaluate each **InstalledOn** date.</span></span> <span data-ttu-id="8d294-131">Mat ris notationen `[-1]` väljer den senaste installerade snabb korrigeringen.</span><span class="sxs-lookup"><span data-stu-id="8d294-131">The array notation `[-1]` selects the most recent installed hotfix.</span></span>

## <span data-ttu-id="8d294-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8d294-132">PARAMETERS</span></span>

### <span data-ttu-id="8d294-133">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="8d294-133">-ComputerName</span></span>

<span data-ttu-id="8d294-134">Anger en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="8d294-134">Specifies a remote computer.</span></span> <span data-ttu-id="8d294-135">Ange NetBIOS-namnet, en Internet Protocol IP-adress eller ett fullständigt kvalificerat domän namn (FQDN) för en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="8d294-135">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>

<span data-ttu-id="8d294-136">När parametern **computername** inte anges körs den `Get-Hotfix` på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8d294-136">When the **ComputerName** parameter isn't specified, `Get-Hotfix` runs on the local computer.</span></span>

<span data-ttu-id="8d294-137">Parametern **computername** är inte beroende av Windows PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="8d294-137">The **ComputerName** parameter doesn't rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="8d294-138">Om datorn inte är konfigurerad för att köra fjärrkommandon använder du parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="8d294-138">If your computer isn't configured to run remote commands, use the **ComputerName** parameter.</span></span>

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

### <span data-ttu-id="8d294-139">-Credential</span><span class="sxs-lookup"><span data-stu-id="8d294-139">-Credential</span></span>

<span data-ttu-id="8d294-140">Anger ett användar konto som har behörighet att komma åt datorn och köra kommandon.</span><span class="sxs-lookup"><span data-stu-id="8d294-140">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="8d294-141">Standardvärdet är den aktuella användaren</span><span class="sxs-lookup"><span data-stu-id="8d294-141">The default is the current user</span></span>

<span data-ttu-id="8d294-142">Ange ett användar namn, till exempel **user01** eller **Domain01\User01**, eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8d294-142">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="8d294-143">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="8d294-143">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="8d294-144">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="8d294-144">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="8d294-145">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="8d294-145">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="8d294-146">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d294-146">-Description</span></span>

<span data-ttu-id="8d294-147">`Get-HotFix` använder **Description** -parametern för att ange snabb korrigerings typer.</span><span class="sxs-lookup"><span data-stu-id="8d294-147">`Get-HotFix` uses the **Description** parameter to specify hotfix types.</span></span> <span data-ttu-id="8d294-148">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="8d294-148">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="8d294-149">-ID</span><span class="sxs-lookup"><span data-stu-id="8d294-149">-Id</span></span>

<span data-ttu-id="8d294-150">Filtrerar `Get-HotFix` resultaten för vissa snabb korrigerings-ID: n.</span><span class="sxs-lookup"><span data-stu-id="8d294-150">Filters the `Get-HotFix` results for specific hotfix Ids.</span></span> <span data-ttu-id="8d294-151">Jokertecken accepteras inte.</span><span class="sxs-lookup"><span data-stu-id="8d294-151">Wildcards aren't accepted.</span></span>

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

### <span data-ttu-id="8d294-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8d294-152">CommonParameters</span></span>

<span data-ttu-id="8d294-153">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8d294-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8d294-154">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8d294-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8d294-155">INDATA</span><span class="sxs-lookup"><span data-stu-id="8d294-155">INPUTS</span></span>

### <span data-ttu-id="8d294-156">Sträng</span><span class="sxs-lookup"><span data-stu-id="8d294-156">String</span></span>

<span data-ttu-id="8d294-157">Du kan skicka ett eller flera dator namn för att få snabb korrigering.</span><span class="sxs-lookup"><span data-stu-id="8d294-157">You can pipe one or more computer names to Get-HotFix.</span></span>

## <span data-ttu-id="8d294-158">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8d294-158">OUTPUTS</span></span>

### <span data-ttu-id="8d294-159">System. Management. ManagementObject # root\CIMV2\ Win32_QuickFixEngineering</span><span class="sxs-lookup"><span data-stu-id="8d294-159">System.Management.ManagementObject#root\CIMV2\Win32_QuickFixEngineering</span></span>

<span data-ttu-id="8d294-160">`Get-HotFix` returnerar objekt som representerar snabb korrigeringarna på datorn.</span><span class="sxs-lookup"><span data-stu-id="8d294-160">`Get-HotFix` returns objects that represent the hotfixes on the computer.</span></span>

## <span data-ttu-id="8d294-161">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8d294-161">NOTES</span></span>

<span data-ttu-id="8d294-162">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="8d294-162">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="8d294-163">**Win32_QuickFixEngineering** [WMI-klassen](/windows/desktop/WmiSdk/retrieving-a-class) representerar en mindre systemomfattande uppdatering, vanligt vis kallat snabb korrigerings teknik (QFE), som tillämpas på det aktuella operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="8d294-163">The **Win32_QuickFixEngineering** [WMI class](/windows/desktop/WmiSdk/retrieving-a-class) represents a small system-wide update, commonly referred to as a quick-fix engineering (QFE) update, applied to the current operating system.</span></span> <span data-ttu-id="8d294-164">Den här klassen returnerar endast uppdateringar som tillhandahålls av Component Based Servicing (CBS).</span><span class="sxs-lookup"><span data-stu-id="8d294-164">This class returns only the updates supplied by Component Based Servicing (CBS).</span></span> <span data-ttu-id="8d294-165">De här uppdateringarna visas inte i registret.</span><span class="sxs-lookup"><span data-stu-id="8d294-165">These updates are not listed in the registry.</span></span> <span data-ttu-id="8d294-166">Uppdateringar som tillhandahålls av Microsoft Windows Installer (MSI) eller [Windows updates](https://update.microsoft.com) platsen returneras inte av **Win32_QuickFixEngineering**.</span><span class="sxs-lookup"><span data-stu-id="8d294-166">Updates supplied by Microsoft Windows Installer (MSI) or the [Windows Update](https://update.microsoft.com) site are not returned by **Win32_QuickFixEngineering**.</span></span> <span data-ttu-id="8d294-167">Mer information finns i [Win32_QuickFixEngineering-klass](/windows/desktop/CIMWin32Prov/win32-quickfixengineering).</span><span class="sxs-lookup"><span data-stu-id="8d294-167">For more information, see [Win32_QuickFixEngineering class](/windows/desktop/CIMWin32Prov/win32-quickfixengineering).</span></span>

<span data-ttu-id="8d294-168">`Get-HotFix`Utdata kan variera mellan olika operativ system.</span><span class="sxs-lookup"><span data-stu-id="8d294-168">The `Get-HotFix` output might vary on different operating systems.</span></span>

## <span data-ttu-id="8d294-169">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8d294-169">RELATED LINKS</span></span>

[<span data-ttu-id="8d294-170">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="8d294-170">about_Arrays</span></span>](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[<span data-ttu-id="8d294-171">Lägg till innehåll</span><span class="sxs-lookup"><span data-stu-id="8d294-171">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="8d294-172">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="8d294-172">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="8d294-173">Win32_QuickFixEngineering klass</span><span class="sxs-lookup"><span data-stu-id="8d294-173">Win32_QuickFixEngineering class</span></span>](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)
