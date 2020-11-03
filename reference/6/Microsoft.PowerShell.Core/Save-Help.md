---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/save-help?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Help
ms.openlocfilehash: 4b7e74d7b83dbf5128b30e1bbf2c51d69c3a235a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267422"
---
# <span data-ttu-id="45336-103">Save-Help</span><span class="sxs-lookup"><span data-stu-id="45336-103">Save-Help</span></span>

## <span data-ttu-id="45336-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="45336-104">SYNOPSIS</span></span>
<span data-ttu-id="45336-105">Hämtar och sparar de senaste hjälpfilerna till en fil system katalog.</span><span class="sxs-lookup"><span data-stu-id="45336-105">Downloads and saves the newest help files to a file system directory.</span></span>

## <span data-ttu-id="45336-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="45336-106">SYNTAX</span></span>

### <span data-ttu-id="45336-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="45336-107">Path (Default)</span></span>

```
Save-Help [-DestinationPath] <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>]
 [<CommonParameters>]
```

### <span data-ttu-id="45336-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="45336-108">LiteralPath</span></span>

```
Save-Help -LiteralPath <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>]
 [<CommonParameters>]
```

## <span data-ttu-id="45336-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="45336-109">DESCRIPTION</span></span>

<span data-ttu-id="45336-110">Cmdleten **Save-Help** laddar ned de senaste hjälpfilerna för PowerShell-moduler och sparar dem i en katalog som du anger.</span><span class="sxs-lookup"><span data-stu-id="45336-110">The **Save-Help** cmdlet downloads the newest help files for PowerShell modules and saves them to a directory that you specify.</span></span>
<span data-ttu-id="45336-111">Med den här funktionen kan du uppdatera hjälpfilerna på datorer som inte har till gång till Internet, och det gör det enklare att uppdatera hjälpfilerna på flera datorer.</span><span class="sxs-lookup"><span data-stu-id="45336-111">This feature lets you update the help files on computers that do not have access to the Internet, and makes it easier to update the help files on multiple computers.</span></span>

<span data-ttu-id="45336-112">I Windows PowerShell 3,0 har **Spara-hjälpen** endast fungerat för moduler som är installerade på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="45336-112">In Windows PowerShell 3.0, **Save-Help** worked only for modules that are installed on the local computer.</span></span>
<span data-ttu-id="45336-113">Även om det var möjligt att importera en modul från en fjärrdator, eller hämta en referens till ett **PSModuleInfo** -objekt från en fjärrdator med hjälp av PowerShell-fjärrkommunikation, bevaras inte egenskapen **HelpInfoUri** och **Save-Help** fungerar inte för hjälp med fjärrmodulen.</span><span class="sxs-lookup"><span data-stu-id="45336-113">Although it was possible to import a module from a remote computer, or obtain a reference to a **PSModuleInfo** object from a remote computer by using PowerShell remoting, the **HelpInfoUri** property was not preserved, and **Save-Help** would not work for remote module Help.</span></span>

<span data-ttu-id="45336-114">I Windows PowerShell 4,0 bevaras egenskapen **HelpInfoUri** över PowerShell-fjärrkommunikation, som gör att **Spara-Help** fungerar för moduler som är installerade på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="45336-114">In Windows PowerShell 4.0, the **HelpInfoUri** property is preserved over PowerShell remoting, which enables **Save-Help** to work for modules that are installed on remote computers.</span></span>
<span data-ttu-id="45336-115">Det är också möjligt att spara ett **PSModuleInfo** -objekt på disk eller flyttbart medium genom att köra Export-Clixml på en dator som inte har Internet åtkomst, importera objektet på en dator som har Internet åtkomst och sedan köra **Spara-hjälp** på **PSModuleInfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="45336-115">It is also possible to save a **PSModuleInfo** object to disk or removable media by running Export-Clixml on a computer that does not have Internet access, import the object on a computer that does have Internet access, and then run **Save-Help** on the **PSModuleInfo** object.</span></span>
<span data-ttu-id="45336-116">Den sparade hjälpen kan transporteras till fjärrdatorn med hjälp av flyttbara lagrings medier, till exempel en USB-enhet.</span><span class="sxs-lookup"><span data-stu-id="45336-116">The saved help can be transported to the remote computer by using removable storage media, such as a USB drive.</span></span>
<span data-ttu-id="45336-117">Hjälpen kan installeras på fjärrdatorn genom att köra **Update-Help**.</span><span class="sxs-lookup"><span data-stu-id="45336-117">The help can be installed on the remote computer by running **Update-Help**.</span></span>
<span data-ttu-id="45336-118">Den här processen kan användas för att installera hjälp på datorer som inte har någon typ av nätverks åtkomst.</span><span class="sxs-lookup"><span data-stu-id="45336-118">This process can be used to install help on computers that do not have any kind of network access.</span></span>

<span data-ttu-id="45336-119">Om du vill installera sparade hjälpfiler kör du cmdleten Update-Help.</span><span class="sxs-lookup"><span data-stu-id="45336-119">To install saved help files, run the Update-Help cmdlet.</span></span>
<span data-ttu-id="45336-120">Lägg till dess *SourcePath* -parameter för att ange mappen där du sparade hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="45336-120">Add its *SourcePath* parameter to specify the folder in which you saved the Help files.</span></span>

<span data-ttu-id="45336-121">Utan parametrar laddar kommandot **Save-Help** ned den senaste hjälpen för alla moduler i sessionen och för moduler som är installerade på datorn på en plats som anges i **PSModulePath** -miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="45336-121">Without parameters, a **Save-Help** command downloads the newest help for all modules in the session and for modules that are installed on the computer in a location listed in the **PSModulePath** environment variable.</span></span>
<span data-ttu-id="45336-122">Den här åtgärden hoppar över moduler som inte stöder uppdaterbar hjälp utan varning.</span><span class="sxs-lookup"><span data-stu-id="45336-122">This action skips modules that do not support Updatable Help without warning.</span></span>

<span data-ttu-id="45336-123">Cmdleten **Save-Help** kontrollerar versionen för eventuella hjälpfiler i målmappen.</span><span class="sxs-lookup"><span data-stu-id="45336-123">The **Save-Help** cmdlet checks the version of any help files in the destination folder.</span></span>
<span data-ttu-id="45336-124">Om det finns nyare hjälpfiler, laddar denna cmdlet ned de senaste hjälpfilerna från Internet och sparar dem sedan i mappen.</span><span class="sxs-lookup"><span data-stu-id="45336-124">If newer help files are available, this cmdlet downloads the newest help files from the Internet, and then saves them in the folder.</span></span>
<span data-ttu-id="45336-125">Cmdleten **Save-Help** fungerar precis som Update-Help-cmdlet, förutom att den sparar de hämtade CAB-filerna, i stället för att extrahera hjälpfilerna från CAB-filerna och installera dem på datorn.</span><span class="sxs-lookup"><span data-stu-id="45336-125">The **Save-Help** cmdlet works just like the Update-Help cmdlet, except that it saves the downloaded cabinet (.cab) files, instead of extracting the help files from the cabinet files and installing them on the computer.</span></span>

<span data-ttu-id="45336-126">Den sparade hjälpen för varje modul består av en HelpInfo XML-fil (hjälp information) och en kabinett fil (. cab) för hjälpfilerna för varje GRÄNSSNITTs kultur.</span><span class="sxs-lookup"><span data-stu-id="45336-126">The saved help for each module consists of one help information (HelpInfo XML) file and one cabinet (.cab) file for the help files each UI culture.</span></span>
<span data-ttu-id="45336-127">Du behöver inte extrahera hjälpfilerna från CAB-filen.</span><span class="sxs-lookup"><span data-stu-id="45336-127">You do not have to extract the help files from the cabinet file.</span></span>
<span data-ttu-id="45336-128">Cmdlet: en **Update-Help** extraherar hjälpfilerna, validerar XML för säkerhet och installerar sedan hjälpfilerna och hjälp informations filen i en språkspecifik undermapp i mappen module.</span><span class="sxs-lookup"><span data-stu-id="45336-128">The **Update-Help** cmdlet extracts the help files, validates the XML for safety, and then installs the help files and the help information file in a language-specific subfolder of the module folder.</span></span>

<span data-ttu-id="45336-129">Om du vill spara hjälpfilerna för moduler i PowerShell-installationsmappen ($pshome \Modules) startar du PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="45336-129">To save the help files for modules in the PowerShell installation folder ($pshome\Modules), start PowerShell by using the Run as administrator option.</span></span>
<span data-ttu-id="45336-130">Du måste vara medlem i gruppen Administratörer på datorn för att kunna hämta hjälpfilerna för dessa moduler.</span><span class="sxs-lookup"><span data-stu-id="45336-130">You must be a member of the Administrators group on the computer to download the help files for these modules.</span></span>

<span data-ttu-id="45336-131">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="45336-131">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="45336-132">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="45336-132">EXAMPLES</span></span>

### <span data-ttu-id="45336-133">Exempel 1: Spara hjälpen för modulen DHCP server</span><span class="sxs-lookup"><span data-stu-id="45336-133">Example 1: Save the help for the DhcpServer module</span></span>

```powershell
# Option 1: Run Invoke-Command to get the PSModuleInfo object for the remote DHCP Server module, save the PSModuleInfo object in the variable $m, and then run Save-Help.

$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock { Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 2: Open a PSSession--targeted at the remote computer that is running the DhcpServer module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$s = New-PSSession -ComputerName "RemoteServer"
$m = Get-Module -PSSession $s -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 3: Open a CIM session--targeted at the remote computer that is running the DhcpServer module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$c = New-CimSession -ComputerName "RemoteServer"
$m = Get-Module -CimSession $c -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"
```

<span data-ttu-id="45336-134">Det här exemplet visar tre olika sätt att använda **Save-Help** för att spara hjälpen för modulen **DHCP** Server från en Internet-ansluten klient dator, **utan att installera modulen DHCP** Server eller DHCP-serverrollen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="45336-134">This example shows three different ways to use **Save-Help** to save the help for the **DhcpServer** module from an Internet-connected client computer, without installing the **DhcpServer** module or the DHCP Server role on the local computer.</span></span>

### <span data-ttu-id="45336-135">Exempel 2: installera hjälp för modulen DHCP server</span><span class="sxs-lookup"><span data-stu-id="45336-135">Example 2: Install help for the DhcpServer module</span></span>

```powershell
# First, run Export-CliXml to export the PSModuleInfo object to a shared folder or to removable media.

$m = Get-Module -Name "DhcpServer" -ListAvailable
Export-CliXml -Path "E:\UsbFlashDrive\DhcpModule.xml" -InputObject $m

# Next, transport the removable media to a computer that has Internet access, and then import the PSModuleInfo object with Import-CliXml. Run Save-Help to save the Help for the imported DhcpServer module PSModuleInfo object.

$deserialized_m = Import-CliXml "E:\UsbFlashDrive\DhcpModule.xml"
Save-Help -Module $deserialized_m -DestinationPath "E:\UsbFlashDrive\SavedHelp"

# Finally, transport the removable media back to the computer that does not have network access, and then install the help by running Update-Help.

Update-Help -Module DhcpServer -SourcePath "E:\UsbFlashDrive\SavedHelp"
```

<span data-ttu-id="45336-136">Det här exemplet visar hur du installerar hjälp som du sparade i exempel 1 för modulen **DHCP** server på en dator som inte har Internet åtkomst.</span><span class="sxs-lookup"><span data-stu-id="45336-136">This example shows how to install help that you saved in Example 1 for the **DhcpServer** module on a computer that does not have Internet access.</span></span>

### <span data-ttu-id="45336-137">Exempel 3: Spara hjälp för alla moduler</span><span class="sxs-lookup"><span data-stu-id="45336-137">Example 3: Save help for all modules</span></span>

```powershell
Save-Help -DestinationPath "\\Server01\FileShare01"
```

<span data-ttu-id="45336-138">Det här kommandot laddar ned de senaste hjälpfilerna för alla moduler i användar gränssnitts kulturen som angetts för Windows på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="45336-138">This command downloads the newest help files for all modules in the UI culture set for Windows on the local computer.</span></span>
<span data-ttu-id="45336-139">Hjälp filen sparas i \\ \\ mappen Server01\Fileshare01</span><span class="sxs-lookup"><span data-stu-id="45336-139">It saves the help files in the \\\\Server01\Fileshare01 folder.</span></span>

### <span data-ttu-id="45336-140">Exempel 4: Spara hjälp för en modul på datorn</span><span class="sxs-lookup"><span data-stu-id="45336-140">Example 4: Save help for a module on the computer</span></span>

```powershell
Save-Help -Module ServerManager -DestinationPath "\\Server01\FileShare01" -Credential Domain01/Admin01
```

<span data-ttu-id="45336-141">Det här kommandot laddar ned de senaste hjälpfilerna för **servermanager** -modulen och sparar dem sedan i \\ \\ mappen Server01\Fileshare01.</span><span class="sxs-lookup"><span data-stu-id="45336-141">This command downloads the newest help files for the **ServerManager** module, and then saves them in the \\\\Server01\Fileshare01 folder.</span></span>

<span data-ttu-id="45336-142">När en modul installeras på datorn kan du ange modulnamnet som värde för parametern *module* , även om modulen inte har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="45336-142">When a module is installed on the computer, you can type the module name as the value of the *Module* parameter, even if the module is not imported into the current session.</span></span>

<span data-ttu-id="45336-143">Kommandot använder parametern *Credential* för att ange autentiseringsuppgifterna för en användare som har behörighet att skriva till fil resursen.</span><span class="sxs-lookup"><span data-stu-id="45336-143">The command uses the *Credential* parameter to supply the credentials of a user who has permission to write to the file share.</span></span>

### <span data-ttu-id="45336-144">Exempel 5: Spara hjälp för en modul på en annan dator</span><span class="sxs-lookup"><span data-stu-id="45336-144">Example 5: Save help for a module on a different computer</span></span>

```powershell
Invoke-Command -ComputerName Server02 {Get-Module -Name CustomSQL -ListAvailable} | Save-Help -DestinationPath \\Server01\FileShare01 -Credential Domain01\Admin01
```

<span data-ttu-id="45336-145">Dessa kommandon laddar ned de senaste hjälpfilerna för **CustomSQL** -modulen och sparar dem i \\ \\ mappen Server01\Fileshare01.</span><span class="sxs-lookup"><span data-stu-id="45336-145">These commands download the newest help files for the **CustomSQL** module and save them in the \\\\Server01\Fileshare01 folder.</span></span>

<span data-ttu-id="45336-146">Eftersom **CustomSQL** -modulen inte är installerad på datorn, innehåller sekvensen ett Invoke-Command-kommando som hämtar module-objektet för CustomSQL-modulen från Server02-datorn och sedan rör objektet module till cmdleten **Save-Help** .</span><span class="sxs-lookup"><span data-stu-id="45336-146">Because the **CustomSQL** module is not installed on the computer, the sequence includes an Invoke-Command command that gets the module object for the CustomSQL module from the Server02 computer and then pipes the module object to the **Save-Help** cmdlet.</span></span>

<span data-ttu-id="45336-147">Om en modul inte är installerad på datorn behöver **-Hjälp-** objektet module, som innehåller information om platsen för de senaste hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="45336-147">When a module is not installed on the computer, **Save-Help** needs the module object, which includes information about the location of the newest help files.</span></span>

### <span data-ttu-id="45336-148">Exempel 6: Spara hjälp för en modul på flera språk</span><span class="sxs-lookup"><span data-stu-id="45336-148">Example 6: Save help for a module in multiple languages</span></span>

```powershell
Save-Help -Module Microsoft.PowerShell* -UICulture de-DE, en-US, fr-FR, ja-JP -DestinationPath "D:\Help"
```

<span data-ttu-id="45336-149">Det här kommandot sparar hjälpen för PowerShell Core-modulerna i fyra olika användar gränssnitts kulturer.</span><span class="sxs-lookup"><span data-stu-id="45336-149">This command saves help for the PowerShell Core modules in four different UI cultures.</span></span>
<span data-ttu-id="45336-150">Språk paketen för dessa språk måste inte installeras på datorn.</span><span class="sxs-lookup"><span data-stu-id="45336-150">The language packs for these locales do not have to be installed on the computer.</span></span>

<span data-ttu-id="45336-151">**Spara – hjälp** kan hämta hjälpfiler för moduler i olika användar gränssnitts kulturer endast när modulens ägare gör de översatta filerna tillgängliga på Internet.</span><span class="sxs-lookup"><span data-stu-id="45336-151">**Save-Help** can download help files for modules in different UI cultures only when the module owner makes the translated files available on the Internet.</span></span>

### <span data-ttu-id="45336-152">Exempel 7: Spara hjälpen mer än en gången varje dag</span><span class="sxs-lookup"><span data-stu-id="45336-152">Example 7: Save help more than one time each day</span></span>

```powershell
Save-Help -Force -DestinationPath "\\Server3\AdminShare\Help"
```

<span data-ttu-id="45336-153">Det här kommandot sparar hjälpen för alla moduler som är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="45336-153">This command saves help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="45336-154">Kommandot anger *Force* -parametern för att åsidosätta regeln som förhindrar att cmdleten **Save-Help** hämtar hjälpen mer än en gång under varje 24-timmarsperiod.</span><span class="sxs-lookup"><span data-stu-id="45336-154">The command specifies the *Force* parameter to override the rule that prevents the **Save-Help** cmdlet from downloading help more than once in each 24-hour period.</span></span>

<span data-ttu-id="45336-155">Parametern *Force* åsidosätter också begränsningen 1 GB och kringgår versions kontroll.</span><span class="sxs-lookup"><span data-stu-id="45336-155">The *Force* parameter also overrides the 1 GB restriction and circumvents version checking.</span></span>
<span data-ttu-id="45336-156">Därför kan du hämta filer även om versionen inte är senare än versionen i målmappen.</span><span class="sxs-lookup"><span data-stu-id="45336-156">Therefore, you can download files even if the version is not later than the version in the destination folder.</span></span>

<span data-ttu-id="45336-157">Kommandot använder cmdleten **Save-Help** för att ladda ned och spara hjälpfilerna i den angivna mappen.</span><span class="sxs-lookup"><span data-stu-id="45336-157">The command uses the **Save-Help** cmdlet to download and save the help files to the specified folder.</span></span>
<span data-ttu-id="45336-158">Parametern *Force* krävs när du måste köra kommandot **Save-Help** mer än en gång varje dag.</span><span class="sxs-lookup"><span data-stu-id="45336-158">The *Force* parameter is required when you have to run a **Save-Help** command more than one time each day.</span></span>

## <span data-ttu-id="45336-159">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="45336-159">PARAMETERS</span></span>

### <span data-ttu-id="45336-160">-Credential</span><span class="sxs-lookup"><span data-stu-id="45336-160">-Credential</span></span>

<span data-ttu-id="45336-161">Anger autentiseringsuppgifter för användare.</span><span class="sxs-lookup"><span data-stu-id="45336-161">Specifies a user credential.</span></span> <span data-ttu-id="45336-162">Denna cmdlet kör kommandot genom att använda autentiseringsuppgifter för en användare som har behörighet att komma åt fil system platsen som anges av parametern **DestinationPath** .</span><span class="sxs-lookup"><span data-stu-id="45336-162">This cmdlet runs the command by using credentials of a user who has permission to access the file system location specified by the **DestinationPath** parameter.</span></span> <span data-ttu-id="45336-163">Den här parametern är endast giltig om parametern **DestinationPath** eller **LiteralPath** används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="45336-163">This parameter is valid only when the **DestinationPath** or **LiteralPath** parameter is used in the command.</span></span>

<span data-ttu-id="45336-164">Med den här parametern kan du köra `Save-Help` kommandon som använder parametern **DestinationPath** på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="45336-164">This parameter enables you to run `Save-Help` commands that use the **DestinationPath** parameter on remote computers.</span></span> <span data-ttu-id="45336-165">Genom att ange explicita autentiseringsuppgifter kan du köra kommandot på en fjärrdator och komma åt en fil resurs på en tredje dator utan att ha påträffat ett nekat åtkomst fel eller använda CredSSP-autentisering för att delegera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="45336-165">By providing explicit credentials, you can run the command on a remote computer and access a file share on a third computer without encountering an access denied error or using CredSSP authentication to delegate credentials.</span></span>

<span data-ttu-id="45336-166">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="45336-166">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="45336-167">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="45336-167">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="45336-168">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="45336-168">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="45336-169">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="45336-169">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45336-170">– DestinationPath</span><span class="sxs-lookup"><span data-stu-id="45336-170">-DestinationPath</span></span>

<span data-ttu-id="45336-171">Anger sökvägen till mappen där hjälpfilerna sparas.</span><span class="sxs-lookup"><span data-stu-id="45336-171">Specifies the path of the folder in which the help files are saved.</span></span>
<span data-ttu-id="45336-172">Ange inget fil namn eller fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="45336-172">Do not specify a file name or file name extension.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45336-173">-Force</span><span class="sxs-lookup"><span data-stu-id="45336-173">-Force</span></span>

<span data-ttu-id="45336-174">Anger att denna cmdlet inte följer begränsningen en gång per dag, hoppar över versions kontroll och laddar ned filer som överskrider gränsen på 1 GB.</span><span class="sxs-lookup"><span data-stu-id="45336-174">Indicates that this cmdlet does not follow the once-per-day limitation, skips version checking, and downloads files that exceed the 1 GB limit.</span></span>

<span data-ttu-id="45336-175">Utan den här parametern är endast ett **Save-Help-** kommando för varje modul tillåtet under varje 24-timmarsperiod, och hämtningar är begränsade till 1 GB okomprimerat innehåll per modul och hjälp filer för en modul installeras bara när de är nyare än filerna på datorn.</span><span class="sxs-lookup"><span data-stu-id="45336-175">Without this parameter, only one **Save-Help** command for each module is permitted in each 24-hour period, downloads are limited to 1 GB of uncompressed content per module, and help files for a module are installed only when they are newer than the files on the computer.</span></span>

<span data-ttu-id="45336-176">Gränsen för en gång per dag skyddar de servrar som är värdar för hjälpfilerna och gör det enkelt att lägga till ett kommando för att **Spara hjälp** i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="45336-176">The once-per-day limit protects the servers that host the help files, and makes it practical for you to add a **Save-Help** command to your PowerShell profile.</span></span>

<span data-ttu-id="45336-177">Om du vill spara hjälp för en modul i flera användar gränssnitts kulturer utan *Force* -parametern inkluderar du alla användar gränssnitts kulturer i samma kommando, till exempel: `Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`</span><span class="sxs-lookup"><span data-stu-id="45336-177">To save help for a module in multiple UI cultures without the *Force* parameter, include all UI cultures in the same command, such as: `Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45336-178">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="45336-178">-FullyQualifiedModule</span></span>

<span data-ttu-id="45336-179">Anger moduler med namn som anges i form av ModuleSpecification-objekt.</span><span class="sxs-lookup"><span data-stu-id="45336-179">Specifies modules with names that are specified in the form of ModuleSpecification objects.</span></span>
<span data-ttu-id="45336-180">Detta beskrivs i avsnittet anmärkningar i [ModuleSpecification-konstruktorn (hash)](https://msdn.microsoft.com/library/jj136290) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="45336-180">This is described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290) in the MSDN library.</span></span>
<span data-ttu-id="45336-181">*FullyQualifiedModule* -parametern accepterar till exempel ett modulnamn som anges i formatet @ {Modulnamn = "Modulnamn"; ModuleVersion = "version_number"} eller @ {Modulnamn = "Modulnamn"; ModuleVersion = "version_number"; GUID = "GUID"}.</span><span class="sxs-lookup"><span data-stu-id="45336-181">For example, the *FullyQualifiedModule* parameter accepts a module name that is specified in the format @{ModuleName = "modulename"; ModuleVersion = "version_number"} or @{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.</span></span>
<span data-ttu-id="45336-182">**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="45336-182">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="45336-183">Det går inte att ange parametern *FullyQualifiedModule* i samma kommando som en *modul* -parameter.</span><span class="sxs-lookup"><span data-stu-id="45336-183">You cannot specify the *FullyQualifiedModule* parameter in the same command as a *Module* parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45336-184">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="45336-184">-LiteralPath</span></span>

<span data-ttu-id="45336-185">Anger en sökväg till målmappen.</span><span class="sxs-lookup"><span data-stu-id="45336-185">Specifies a path of the destination folder.</span></span>
<span data-ttu-id="45336-186">Till skillnad från värdet för parametern *DestinationPath* används värdet för parametern *LiteralPath* exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="45336-186">Unlike the value of the *DestinationPath* parameter, the value of the *LiteralPath* parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="45336-187">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="45336-187">No characters are interpreted as wildcard characters.</span></span>
<span data-ttu-id="45336-188">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="45336-188">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="45336-189">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="45336-189">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45336-190">– Modul</span><span class="sxs-lookup"><span data-stu-id="45336-190">-Module</span></span>

<span data-ttu-id="45336-191">Anger moduler för vilka denna cmdlet laddar ned hjälp.</span><span class="sxs-lookup"><span data-stu-id="45336-191">Specifies modules for which this cmdlet downloads help.</span></span>
<span data-ttu-id="45336-192">Ange ett eller flera Modulnamn eller namn patters i en kommaavgränsad lista eller i en fil som har ett modulnamn på varje rad.</span><span class="sxs-lookup"><span data-stu-id="45336-192">Enter one or more module names or name patters in a comma-separated list or in a file that has one module name on each line.</span></span>
<span data-ttu-id="45336-193">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="45336-193">Wildcard characters are permitted.</span></span>
<span data-ttu-id="45336-194">Du kan också skicka modul objekt från Get-Module cmdlet för att **Spara-hjälpen**.</span><span class="sxs-lookup"><span data-stu-id="45336-194">You can also pipe module objects from the Get-Module cmdlet to **Save-Help**.</span></span>

<span data-ttu-id="45336-195">Som standard får du hjälp med att **Spara** hjälp för alla moduler som stöder uppdaterbar hjälp och som är installerade på den lokala datorn på en plats som anges i **PSModulePath** -miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="45336-195">By default, **Save-Help** downloads help for all modules that support Updatable Help and are installed on the local computer in a location listed in the **PSModulePath** environment variable.</span></span>

<span data-ttu-id="45336-196">Om du vill spara hjälp för moduler som inte är installerade på datorn kör du kommandot **Get-module** på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="45336-196">To save help for modules that are not installed on the computer, run a **Get-Module** command on a remote computer.</span></span>
<span data-ttu-id="45336-197">Skicka sedan de resulterande modulerna till cmdleten **Save-Help** eller skicka modulens objekt som värde för *modulen* eller *InputObject* -parametrarna.</span><span class="sxs-lookup"><span data-stu-id="45336-197">Then pipe the resulting module objects to the **Save-Help** cmdlet or submit the module objects as the value of the *Module* or *InputObject* parameters.</span></span>

<span data-ttu-id="45336-198">Om den modul som du anger är installerad på datorn kan du ange modulens namn eller ett modul-objekt.</span><span class="sxs-lookup"><span data-stu-id="45336-198">If the module that you specify is installed on the computer, you can enter the module name or a module object.</span></span>
<span data-ttu-id="45336-199">Om modulen inte är installerad på datorn måste du ange ett modul-objekt, till exempel en som returneras av cmdleten **Get-module** .</span><span class="sxs-lookup"><span data-stu-id="45336-199">If the module is not installed on the computer, you must enter a module object, such as one returned by the **Get-Module** cmdlet.</span></span>

<span data-ttu-id="45336-200">Parametern *module* i cmdleten **Save-Help** accepterar inte den fullständiga sökvägen till en modul fil eller modulens manifest fil.</span><span class="sxs-lookup"><span data-stu-id="45336-200">The *Module* parameter of the **Save-Help** cmdlet does not accept the full path of a module file or module manifest file.</span></span>
<span data-ttu-id="45336-201">Om du vill spara hjälp för en modul som inte finns på en **PSModulePath** plats importerar du modulen till den aktuella sessionen innan du kör kommandot **Save-Help** .</span><span class="sxs-lookup"><span data-stu-id="45336-201">To save help for a module that is not in a **PSModulePath** location, import the module into the current session before you run the **Save-Help** command.</span></span>

<span data-ttu-id="45336-202">Värdet "\*" (alla) försöker att uppdatera hjälpen för alla moduler som är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="45336-202">A value of "\*" (all) attempts to update help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="45336-203">Detta inkluderar moduler som inte stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="45336-203">This includes modules that do not support Updatable Help.</span></span>
<span data-ttu-id="45336-204">Det här värdet kan generera fel när kommandot påträffar moduler som inte stöder uppdaterings bar hjälp.</span><span class="sxs-lookup"><span data-stu-id="45336-204">This value might generate errors when the command encounters modules that do not support Updatable Help.</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="45336-205">– Värdet</span><span class="sxs-lookup"><span data-stu-id="45336-205">-UICulture</span></span>

<span data-ttu-id="45336-206">Anger GRÄNSSNITTs kultur värden för vilka denna cmdlet hämtar hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="45336-206">Specifies UI culture values for which this cmdlet gets updated help files.</span></span>
<span data-ttu-id="45336-207">Ange en eller flera språk koder, till exempel es-ES, en variabel som innehåller kultur objekt eller ett kommando som hämtar kultur objekt, till exempel ett Get-Culture-eller Get-UICulture-kommando.</span><span class="sxs-lookup"><span data-stu-id="45336-207">Enter one or more language codes, such as es-ES, a variable that contains culture objects, or a command that gets culture objects, such as a Get-Culture or Get-UICulture command.</span></span>

<span data-ttu-id="45336-208">Jokertecken tillåts inte.</span><span class="sxs-lookup"><span data-stu-id="45336-208">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="45336-209">Ange inte en del språk kod, till exempel "de".</span><span class="sxs-lookup"><span data-stu-id="45336-209">Do not specify a partial language code, such as "de".</span></span>

<span data-ttu-id="45336-210">Som standard hämtar **Spara-hjälp** filer i användar gränssnitts kulturen som angetts för Windows eller dess reserv kultur.</span><span class="sxs-lookup"><span data-stu-id="45336-210">By default, **Save-Help** gets help files in the UI culture set for Windows or its fallback culture.</span></span>
<span data-ttu-id="45336-211">Om du anger parametern *värdet* kan **Spara-Help** bara leta efter hjälp för den angivna användar gränssnitts kulturen, inte i någon återställnings kultur.</span><span class="sxs-lookup"><span data-stu-id="45336-211">If you specify the *UICulture* parameter, **Save-Help** looks for help only for the specified UI culture, not in any fallback culture.</span></span>

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: Current UI culture
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45336-212">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="45336-212">-UseDefaultCredentials</span></span>

<span data-ttu-id="45336-213">Anger att denna cmdlet kör kommandot, inklusive webb hämtning, med autentiseringsuppgifterna för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="45336-213">Indicates that this cmdlet runs the command, including the web download, with the credentials of the current user.</span></span>
<span data-ttu-id="45336-214">Som standard körs kommandot utan explicita autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="45336-214">By default, the command runs without explicit credentials.</span></span>

<span data-ttu-id="45336-215">Den här parametern är endast effektiv när webb hämtningen använder NTLM, Negotiate eller Kerberos-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="45336-215">This parameter is effective only when the web download uses NTLM, negotiate, or Kerberos-based authentication.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45336-216">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="45336-216">-Scope</span></span>

<span data-ttu-id="45336-217">Den här parameter gör ingenting i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="45336-217">This paramater does nothing in this cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45336-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="45336-218">CommonParameters</span></span>

<span data-ttu-id="45336-219">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="45336-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="45336-220">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="45336-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="45336-221">INDATA</span><span class="sxs-lookup"><span data-stu-id="45336-221">INPUTS</span></span>

### <span data-ttu-id="45336-222">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="45336-222">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="45336-223">Du kan skicka ett modul-objekt från cmdleten **Get-module** till *modulen modul* för **Save-Help**.</span><span class="sxs-lookup"><span data-stu-id="45336-223">You can pipe a module object from the **Get-Module** cmdlet to the *Module* parameter of **Save-Help**.</span></span>

## <span data-ttu-id="45336-224">UTDATA</span><span class="sxs-lookup"><span data-stu-id="45336-224">OUTPUTS</span></span>

### <span data-ttu-id="45336-225">Inget</span><span class="sxs-lookup"><span data-stu-id="45336-225">None</span></span>

<span data-ttu-id="45336-226">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="45336-226">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="45336-227">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="45336-227">NOTES</span></span>

* <span data-ttu-id="45336-228">Om du vill spara hjälp för moduler i mappen $pshome \Modules startar du PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="45336-228">To save help for modules in the $pshome\Modules folder, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="45336-229">Endast medlemmar i gruppen Administratörer på datorn kan hämta hjälp för moduler i mappen $pshome \Modules.</span><span class="sxs-lookup"><span data-stu-id="45336-229">Only members of the Administrators group on the computer can download help for modules in the $pshome\Modules folder.</span></span>
* <span data-ttu-id="45336-230">Den sparade hjälpen för varje modul består av en HelpInfo XML-fil (hjälp information) och en kabinett fil (. cab) för hjälpfilerna för varje GRÄNSSNITTs kultur.</span><span class="sxs-lookup"><span data-stu-id="45336-230">The saved help for each module consists of one help information (HelpInfo XML) file and one cabinet (.cab) file for the help files each UI culture.</span></span> <span data-ttu-id="45336-231">Du behöver inte extrahera hjälpfilerna från CAB-filen.</span><span class="sxs-lookup"><span data-stu-id="45336-231">You do not have to extract the help files from the cabinet file.</span></span> <span data-ttu-id="45336-232">Update-Help cmdleten extraherar hjälpfilerna, validerar XML och installerar sedan hjälpfilerna och hjälp informations filen i en språkspecifik undermapp i mappen module.</span><span class="sxs-lookup"><span data-stu-id="45336-232">The Update-Help cmdlet extracts the help files, validates the XML, and then installs the help files and the help information file in a language-specific subfolder of the module folder.</span></span>
* <span data-ttu-id="45336-233">Cmdleten **Save-Help** kan spara hjälp för moduler som inte är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="45336-233">The **Save-Help** cmdlet can save help for modules that are not installed on the computer.</span></span> <span data-ttu-id="45336-234">Eftersom hjälpfiler installeras i modulen modul kan du dock **installera den uppdaterade hjälp filen** endast för moduler som är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="45336-234">However, because help files are installed in the module folder, the **Update-Help** cmdlet can install updated help file only for modules that are installed on the computer.</span></span>
* <span data-ttu-id="45336-235">Om **Spara-Help** inte kan hitta uppdaterade hjälpfiler för en modul, eller om det inte går att hitta uppdaterade hjälpfiler på det angivna språket, fortsätter den tyst utan att ett fel meddelande visas.</span><span class="sxs-lookup"><span data-stu-id="45336-235">If **Save-Help** cannot find updated help files for a module, or cannot find updated help files in the specified language, it continues silently without displaying an error message.</span></span> <span data-ttu-id="45336-236">Om du vill se vilka filer som sparats med kommandot anger du *utförlig* parameter.</span><span class="sxs-lookup"><span data-stu-id="45336-236">To see which files were saved by the command, specify the *Verbose* parameter.</span></span>
* <span data-ttu-id="45336-237">Moduler är den minsta enheten för uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="45336-237">Modules are the smallest unit of updatable help.</span></span> <span data-ttu-id="45336-238">Du kan inte spara hjälp för en viss cmdlet, endast för alla cmdletar i modulen.</span><span class="sxs-lookup"><span data-stu-id="45336-238">You cannot save help for a particular cmdlet, only for all cmdlets in module.</span></span> <span data-ttu-id="45336-239">Om du vill hitta modulen som innehåller en viss cmdlet använder du egenskapen **Modulnamn** tillsammans med Get-Command-cmdlet, till exempel `(Get-Command \<cmdlet-name\>).ModuleName`</span><span class="sxs-lookup"><span data-stu-id="45336-239">To find the module that contains a particular cmdlet, use the **ModuleName** property together with the Get-Command cmdlet, for example, `(Get-Command \<cmdlet-name\>).ModuleName`</span></span>
* <span data-ttu-id="45336-240">**Save – Help** stöder alla moduler och snapin-moduler för PowerShell Core. Den har inte stöd för några andra snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="45336-240">**Save-Help** supports all modules and the PowerShell Core snap-ins. It does not support any other snap-ins.</span></span>
* <span data-ttu-id="45336-241">Cmdletarna **Update-Help** och **Save-Help** använder följande portar för att hämta hjälpfiler: port 80 för http och port 443 för https.</span><span class="sxs-lookup"><span data-stu-id="45336-241">The **Update-Help** and **Save-Help** cmdlets use the following ports to download help files: Port 80 for HTTP and port 443 for HTTPS.</span></span>
* <span data-ttu-id="45336-242">Cmdletarna **Update-Help** och **Save-Help** stöds inte på Windows Preinstallation Environment (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="45336-242">The **Update-Help** and **Save-Help** cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="45336-243">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="45336-243">RELATED LINKS</span></span>

[<span data-ttu-id="45336-244">Get – hjälp</span><span class="sxs-lookup"><span data-stu-id="45336-244">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="45336-245">Hämta modul</span><span class="sxs-lookup"><span data-stu-id="45336-245">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="45336-246">Uppdatera – hjälp</span><span class="sxs-lookup"><span data-stu-id="45336-246">Update-Help</span></span>](Update-Help.md)
