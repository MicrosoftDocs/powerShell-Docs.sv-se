---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-psdrive?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSDrive
ms.openlocfilehash: df5f335780ad04b2d833180c30cc46a06f85d850
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265521"
---
# <span data-ttu-id="a2bb9-103">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="a2bb9-103">New-PSDrive</span></span>

## <span data-ttu-id="a2bb9-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a2bb9-104">SYNOPSIS</span></span>
<span data-ttu-id="a2bb9-105">Skapar tillfälliga och beständiga mappade nätverks enheter.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-105">Creates temporary and persistent mapped network drives.</span></span>

## <span data-ttu-id="a2bb9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a2bb9-106">SYNTAX</span></span>

### <span data-ttu-id="a2bb9-107">Alla</span><span class="sxs-lookup"><span data-stu-id="a2bb9-107">All</span></span>

```
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Description <String>]
 [-Scope <String>] [-Persist] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="a2bb9-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a2bb9-108">DESCRIPTION</span></span>

<span data-ttu-id="a2bb9-109">`New-PSDrive`Cmdleten skapar temporära och beständiga enheter som mappas till eller associeras med en plats i ett data lager, till exempel en nätverks enhet, en katalog på den lokala datorn eller en register nyckel och beständiga Windows-anslutna nätverks enheter som är associerade med en fil system plats på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-109">The `New-PSDrive` cmdlet creates temporary and persistent drives that are mapped to or associated with a location in a data store, such as a network drive, a directory on the local computer, or a registry key, and persistent Windows mapped network drives that are associated with a file system location on a remote computer.</span></span>

<span data-ttu-id="a2bb9-110">Tillfälliga enheter finns bara i den aktuella PowerShell-sessionen och i sessioner som du skapar i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-110">Temporary drives exist only in the current PowerShell session and in sessions that you create in the current session.</span></span> <span data-ttu-id="a2bb9-111">De kan ha ett namn som är giltigt i PowerShell och som kan mappas till en lokal eller fjärran sluten resurs.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-111">They can have any name that is valid in PowerShell and can be mapped to any local or remote resource.</span></span> <span data-ttu-id="a2bb9-112">Du kan använda tillfälliga PowerShell-enheter för att komma åt data i det associerade data lagret, precis som du gör med en mappad nätverks enhet.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-112">You can use temporary PowerShell drives to access data in the associated data store, just as you would do with any mapped network drive.</span></span> <span data-ttu-id="a2bb9-113">Du kan ändra platser till enheten, genom att använda `Set-Location` och komma åt enhetens innehåll med hjälp av `Get-Item` eller `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="a2bb9-113">You can change locations into the drive, by using `Set-Location`, and access the contents of the drive by using `Get-Item` or `Get-ChildItem`.</span></span>

<span data-ttu-id="a2bb9-114">Eftersom temporära enheter bara känner till PowerShell kan du inte komma åt dem med hjälp av Utforskaren, Windows Management Instrumentation (WMI), Component Object Model (COM), Microsoft .NET Framework eller med verktyg som t. ex. **net use**.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-114">Because temporary drives are known only to PowerShell, you can't access them by using File Explorer, Windows Management Instrumentation (WMI), Component Object Model (COM), Microsoft .NET Framework, or with tools such as **net use**.</span></span>

<span data-ttu-id="a2bb9-115">Följande funktioner har lagts till `New-PSDrive` i PowerShell 3,0:</span><span class="sxs-lookup"><span data-stu-id="a2bb9-115">The following features were added to `New-PSDrive` in PowerShell 3.0:</span></span>

- <span data-ttu-id="a2bb9-116">Mappade nätverks enheter.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-116">Mapped network drives.</span></span> <span data-ttu-id="a2bb9-117">Du kan använda **persist** -parametern för `New-PSDrive` för att skapa Windows-mappade nätverks enheter.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-117">You can use the **Persist** parameter of `New-PSDrive` to create Windows mapped network drives.</span></span> <span data-ttu-id="a2bb9-118">Till skillnad från tillfälliga PowerShell-enheter är Windows-mappade nätverks enheter inte sessionsbaserade.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-118">Unlike temporary PowerShell drives, Windows mapped network drives aren't session-specific.</span></span> <span data-ttu-id="a2bb9-119">De sparas i Windows och de kan hanteras med hjälp av standard verktyg för Windows, till exempel Utforskaren och **net use**.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-119">They're saved in Windows and they can be managed by using standard Windows tools, such as File Explorer and **net use**.</span></span> <span data-ttu-id="a2bb9-120">Mappade nätverks enheter måste ha ett enhets betecknings namn och vara anslutet till en fjärrplats i fil systemet.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-120">Mapped network drives must have a drive-letter name and be connected to a remote file system location.</span></span> <span data-ttu-id="a2bb9-121">När ditt kommando omfattas lokalt, ingen punkt-källa, behålls inte den **kvarhållna** parametern när en **PSDrive** har skapats utanför den omfattning där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-121">When your command is scoped locally, no dot-sourcing, the **Persist** parameter doesn't persist the creation of a **PSDrive** beyond the scope in which the command is running.</span></span> <span data-ttu-id="a2bb9-122">Om du kör `New-PSDrive` i ett skript och du vill att enheten ska vara oändlig, måste du punkt-källa skriptet.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-122">If you're running `New-PSDrive` inside a script, and you want the drive to persist indefinitely, you must dot-source the script.</span></span> <span data-ttu-id="a2bb9-123">För bästa resultat bör du lägga till parametern **scope** i kommandot och ange värdet **Global** för att tvinga en ny enhet att kvarstå i oändlighet.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-123">For best results, to force a new drive to persist indefinitely, add the **Scope** parameter to your command, and set its value to **Global**.</span></span> <span data-ttu-id="a2bb9-124">Mer information om punkt-källa finns [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="a2bb9-124">For more information about dot-sourcing, see [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing).</span></span>
- <span data-ttu-id="a2bb9-125">Externa enheter.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-125">External drives.</span></span> <span data-ttu-id="a2bb9-126">När en extern enhet är ansluten till datorn lägger PowerShell automatiskt till en **PSDrive** i fil systemet som representerar den nya enheten.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-126">When an external drive is connected to the computer, PowerShell automatically adds a **PSDrive** to the file system that represents the new drive.</span></span> <span data-ttu-id="a2bb9-127">Du behöver inte starta om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-127">You don't have to restart PowerShell.</span></span> <span data-ttu-id="a2bb9-128">När en extern enhet kopplas bort från datorn tar PowerShell automatiskt bort den **PSDrive** som representerar den borttagna enheten.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-128">Similarly, when an external drive is disconnected from the computer, PowerShell automatically deletes the **PSDrive** that represents the removed drive.</span></span>
- <span data-ttu-id="a2bb9-129">Autentiseringsuppgifter för Universal Naming Convention (UNC) sökvägar.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-129">Credentials for Universal Naming Convention (UNC) paths.</span></span>

<span data-ttu-id="a2bb9-130">När värdet för **rot** parametern är en UNC-sökväg, till exempel `\\Server\Share` , används den autentiseringsuppgift som anges i värdet för parametern **Credential** för att skapa **PSDrive**.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-130">When the value of the **Root** parameter is a UNC path, such as `\\Server\Share`, the credential specified in the value of the **Credential** parameter is used to create the **PSDrive**.</span></span> <span data-ttu-id="a2bb9-131">Annars gäller inte **autentiseringsuppgiften** när du skapar nya fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-131">Otherwise, **Credential** isn't effective when you're creating new file system drives.</span></span>

<span data-ttu-id="a2bb9-132">I vissa kod exempel används ihopbuntning för att minska rad längden och förbättra läsbarheten.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-132">Some code samples use splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="a2bb9-133">Mer information finns i [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="a2bb9-133">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="a2bb9-134">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a2bb9-134">EXAMPLES</span></span>

### <span data-ttu-id="a2bb9-135">Exempel 1: skapa en tillfällig enhet som är mappad till en nätverks resurs</span><span class="sxs-lookup"><span data-stu-id="a2bb9-135">Example 1: Create a temporary drive mapped to a network share</span></span>

<span data-ttu-id="a2bb9-136">I det här exemplet skapas en tillfällig PowerShell-enhet som är mappad till en nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-136">This example creates a temporary PowerShell drive that's mapped to a network share.</span></span>

```powershell
New-PSDrive -Name "Public" -PSProvider "FileSystem" -Root "\\Server01\Public"
```

```Output
Name       Provider      Root
----       --------      ----
Public     FileSystem    \\Server01\Public
```

<span data-ttu-id="a2bb9-137">`New-PSDrive` använder **Name** -parametern för att ange PowerShell-enhet med namnet `Public` och parametern **PSProvider** för att ange PowerShell- `FileSystem` providern.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-137">`New-PSDrive` uses the **Name** parameter to specify PowerShell drive named `Public` and the **PSProvider** parameter to specify the PowerShell `FileSystem` provider.</span></span> <span data-ttu-id="a2bb9-138">**Rot** parametern anger nätverks RESURSens UNC-sökväg.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-138">The **Root** parameter specifies the network share's UNC path.</span></span>

<span data-ttu-id="a2bb9-139">Så här visar du innehållet från en PowerShell-session: `Get-ChildItem -Path Public:`</span><span class="sxs-lookup"><span data-stu-id="a2bb9-139">To view the contents from a PowerShell session: `Get-ChildItem -Path Public:`</span></span>

### <span data-ttu-id="a2bb9-140">Exempel 2: skapa en tillfällig enhet som är mappad till en lokal katalog</span><span class="sxs-lookup"><span data-stu-id="a2bb9-140">Example 2: Create a temporary drive mapped to a local directory</span></span>

<span data-ttu-id="a2bb9-141">I det här exemplet skapas en tillfällig PowerShell-enhet som ger åtkomst till en katalog på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-141">This example creates a temporary PowerShell drive that provides access to a directory on the local computer.</span></span>

```powershell
$parameters = @{
    Name = "MyDocs"
    PSProvider = "FileSystem"
    Root = "C:\Users\User01\Documents"
    Description = "Maps to my My Documents folder."
}
New-PSDrive @parameters
```

```Output
Name        Provider      Root
----        --------      ----
MyDocs      FileSystem    C:\Users\User01\Documents
```

<span data-ttu-id="a2bb9-142">Ihopbuntning skapar parameter nycklar och-värden.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-142">Splatting creates the parameter keys and values.</span></span> <span data-ttu-id="a2bb9-143">Parametern **Name** anger enhets namnet, mina **dokument**.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-143">The **Name** parameter specifies the drive name, **MyDocs**.</span></span> <span data-ttu-id="a2bb9-144">Parametern **PSProvider** anger PowerShell- `FileSystem` providern.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-144">The **PSProvider** parameter specifies the PowerShell `FileSystem` provider.</span></span> <span data-ttu-id="a2bb9-145">**Root** anger den lokala datorns katalog.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-145">**Root** specifies the local computer's directory.</span></span> <span data-ttu-id="a2bb9-146">Parametern **Description** beskriver enhetens syfte.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-146">The **Description** parameter describes the drive's purpose.</span></span> <span data-ttu-id="a2bb9-147">`New-PSDrive` använder splatted-parametrarna för att skapa `MyDocs` enheten.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-147">`New-PSDrive` uses the splatted parameters to create the `MyDocs` drive.</span></span>

<span data-ttu-id="a2bb9-148">Så här visar du innehållet från en PowerShell-session: `Get-ChildItem -Path MyDocs:`</span><span class="sxs-lookup"><span data-stu-id="a2bb9-148">To view the contents from a PowerShell session: `Get-ChildItem -Path MyDocs:`</span></span>

### <span data-ttu-id="a2bb9-149">Exempel 3: skapa en tillfällig enhet för en register nyckel</span><span class="sxs-lookup"><span data-stu-id="a2bb9-149">Example 3: Create a temporary drive for a registry key</span></span>

<span data-ttu-id="a2bb9-150">I det här exemplet skapas en tillfällig PowerShell-enhet som ger åtkomst till en register nyckel.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-150">This example creates a temporary PowerShell drive that provides access to a registry key.</span></span> <span data-ttu-id="a2bb9-151">Den skapar en enhet med namnet Company som är mappad till `HKLM:\Software\MyCompany` register nyckeln.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-151">It creates a drive named MyCompany that is mapped to the `HKLM:\Software\MyCompany` registry key.</span></span>

```powershell
New-PSDrive -Name "MyCompany" -PSProvider "Registry" -Root "HKLM:\Software\MyCompany"
```

```Output
Name           Provider      Root
----           --------      ----
MyCompany      Registry      HKLM:\Software\MyCompany
```

<span data-ttu-id="a2bb9-152">`New-PSDrive` använder **Name** -parametern för att ange PowerShell-enhet med namnet `MyCompany` och parametern **PSProvider** för att ange PowerShell- `Registry` providern.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-152">`New-PSDrive` uses the **Name** parameter to specify PowerShell drive named `MyCompany` and the **PSProvider** parameter to specify the PowerShell `Registry` provider.</span></span> <span data-ttu-id="a2bb9-153">**Rot** parametern anger register platsen.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-153">The **Root** parameter specifies the registry location.</span></span>

<span data-ttu-id="a2bb9-154">Så här visar du innehållet från en PowerShell-session: `Get-ChildItem -Path MyCompany:`</span><span class="sxs-lookup"><span data-stu-id="a2bb9-154">To view the contents from a PowerShell session: `Get-ChildItem -Path MyCompany:`</span></span>

### <span data-ttu-id="a2bb9-155">Exempel 4: skapa en beständig mappad nätverks enhet med hjälp av autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="a2bb9-155">Example 4: Create a persistent mapped network drive using credentials</span></span>

<span data-ttu-id="a2bb9-156">Det här exemplet mappar en nätverks enhet som autentiseras med ett domän tjänst kontos autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-156">This example maps a network drive that's authenticated with a domain service account's credentials.</span></span>
<span data-ttu-id="a2bb9-157">Mer information om **PSCredential** -objektet som lagrar autentiseringsuppgifter och hur lösen ord lagras som en **SecureString** finns i Beskrivning av **Credential** -parametern.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-157">For more information about the **PSCredential** object that stores credentials and how passwords are stored as a **SecureString** , see the **Credential** parameter's description.</span></span>

```powershell
$cred = Get-Credential -Credential Contoso\ServiceAccount
New-PSDrive -Name "S" -Root "\\Server01\Scripts" -Persist -PSProvider "FileSystem" -Credential $cred
Net Use
```

```Output
Status       Local     Remote                    Network
---------------------------------------------------------
OK           S:        \\Server01\Scripts        Microsoft Windows Network
```

> [!NOTE]
> <span data-ttu-id="a2bb9-158">Kom ihåg att om du använder ovanstående kodfragment i ett skript, ställer du in värdet för **scope** -parametern till "global" för att se till att enheten fortfarande befinner sig utanför det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-158">Remember, if you use the above snippet in a script, set the **Scope** parameter value to "Global" to ensure the drive persists outside the current scope.</span></span>

<span data-ttu-id="a2bb9-159">`$cred`Variabeln lagrar ett **PSCredential** -objekt som innehåller tjänst kontots autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-159">The `$cred` variable stores a **PSCredential** object that contains the service account's credentials.</span></span> <span data-ttu-id="a2bb9-160">`Get-Credential` du blir ombedd att ange lösen ordet som lagras i en **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-160">`Get-Credential` prompts you to enter the password that's stored in a **SecureString**.</span></span>

<span data-ttu-id="a2bb9-161">`New-PSDrive` skapar den mappade nätverks enheten genom att använda flera parametrar.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-161">`New-PSDrive` creates the mapped network drive by using several parameters.</span></span> <span data-ttu-id="a2bb9-162">**Namn** anger `S` enhets beteckningen som Windows accepterar.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-162">**Name** specifies the `S` drive letter that Windows accepts.</span></span> <span data-ttu-id="a2bb9-163">och **rot** definierar `\\Server01\Scripts` som plats på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-163">and **Root** defines `\\Server01\Scripts` as the location on a remote computer.</span></span> <span data-ttu-id="a2bb9-164">**Behåll** skapar en Windows-mappad nätverks enhet som sparas på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-164">**Persist** creates a Windows mapped network drive that's saved on the local computer.</span></span> <span data-ttu-id="a2bb9-165">**PSProvider** anger `FileSystem` providern.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-165">**PSProvider** specifies the `FileSystem` provider.</span></span> <span data-ttu-id="a2bb9-166">**Autentiseringsuppgiften** använder `$cred` variabeln för att hämta autentiseringsuppgifterna för tjänst kontot för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-166">**Credential** uses the `$cred` variable to get the service account credentials for authentication.</span></span>

<span data-ttu-id="a2bb9-167">Den mappade enheten kan visas på den lokala datorn i PowerShell-sessioner, Utforskaren och med verktyg som t. ex. **net use**.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-167">The mapped drive can be viewed on the local computer in PowerShell sessions, File Explorer, and with tools such as **net use**.</span></span> <span data-ttu-id="a2bb9-168">Så här visar du innehållet från en PowerShell-session: `Get-ChildItem -Path S:`</span><span class="sxs-lookup"><span data-stu-id="a2bb9-168">To view the contents from a PowerShell session: `Get-ChildItem -Path S:`</span></span>

### <span data-ttu-id="a2bb9-169">Exempel 5: skapa beständiga och temporära enheter</span><span class="sxs-lookup"><span data-stu-id="a2bb9-169">Example 5: Create persistent and temporary drives</span></span>

<span data-ttu-id="a2bb9-170">I det här exemplet visas skillnaden mellan en beständig mappad nätverks enhet och en tillfällig PowerShell-enhet som är mappad till samma nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-170">This example shows the difference between a persistent mapped network drive and a temporary PowerShell drive that is mapped to the same network share.</span></span>

<span data-ttu-id="a2bb9-171">Om du stänger PowerShell-sessionen och sedan öppnar en ny session, är den tillfälliga `PSDrive:` inte tillgänglig, men den permanenta `X:` enheten är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-171">If you close the PowerShell session and then open a new session, the temporary `PSDrive:` isn't available, but the persistent `X:` drive is available.</span></span> <span data-ttu-id="a2bb9-172">När du bestämmer vilken metod som ska användas för att mappa nätverks enheter bör du tänka på hur du ska använda enheten.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-172">When deciding which method to use to map network drives, consider how you'll use the drive.</span></span> <span data-ttu-id="a2bb9-173">Till exempel om det måste vara beständigt och om enheten ska vara synlig för andra Windows-funktioner.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-173">For example, whether it has to be persistent, and whether the drive has to be visible to other Windows features.</span></span>

```powershell
# Create a temporary PowerShell drive called PSDrive:
# that's mapped to the \\Server01\Public network share.
New-PSDrive -Name "PSDrive" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Use the Persist parameter of New-PSDrive to create the X: mapped network drive,
# which is also mapped to the \\Server01\Public network share.
New-PSDrive -Persist -Name "X" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Now, you can use the Get-PSDrive drive cmdlet to examine the two drives.
# The drives appear to be the same, although the network share name appears only
# in the root of the PSDrive: drive.
Get-PSDrive -Name "PSDrive", "X"
```

```Output
Name       Provider      Root
----       --------      ----

PsDrive    FileSystem    \\Server01\public
X          FileSystem    X:\
```

```powershell
# Get-Member cmdlet shows that the drives have the same object type,
# System.Management.Automation.PSDriveInfo.
Get-PSDrive "PSDrive", "x" | Get-Member
```

```Output
TypeName: System.Management.Automation.PSDriveInfo

Name                MemberType   Definition
----                ----------   ----------
CompareTo           Method       System.Int32 CompareTo(PSDriveInfo drive),
Equals              Method       System.Boolean Equals(Object obj),
GetHashCode         Method       System.Int32 GetHashCode()
...
```

```powershell
# Net Use and Get-CimInstance for the Win32_LogicalDisk class,
# and Win32_NetworkConnection class find only the persistent X: drive.
# PowerShell temporary drives are known only to PowerShell.
Net Use
Get-CimInstance Win32_LogicalDisk | Format-Table -Property DeviceID
Get-CimInstance Win32_NetworkConnection
```

```Output
Status       Local     Remote                    Network
--------------------------------------------------------
OK           X:        \\contoso-pc\data         Microsoft Windows Network

deviceid
--------
C:
D:
X:

LocalName    RemoteName              ConnectionState          Status
---------    ----------              ---------------          ------
X:           \\products\public       Disconnected             Unavailable
```

## <span data-ttu-id="a2bb9-174">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a2bb9-174">PARAMETERS</span></span>

### <span data-ttu-id="a2bb9-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a2bb9-175">-Confirm</span></span>

<span data-ttu-id="a2bb9-176">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-176">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a2bb9-177">-Credential</span><span class="sxs-lookup"><span data-stu-id="a2bb9-177">-Credential</span></span>

<span data-ttu-id="a2bb9-178">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-178">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="a2bb9-179">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-179">The default is the current user.</span></span>

<span data-ttu-id="a2bb9-180">Eftersom PowerShell 3,0, när värdet för **rot** parametern är en UNC-sökväg, kan du använda autentiseringsuppgifter för att skapa fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-180">Since PowerShell 3.0, when the value of the **Root** parameter is a UNC path, you can use credentials to create file system drives.</span></span>

<span data-ttu-id="a2bb9-181">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-181">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="a2bb9-182">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-182">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="a2bb9-183">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="a2bb9-183">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="a2bb9-184">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="a2bb9-184">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a2bb9-185">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a2bb9-185">-Description</span></span>

<span data-ttu-id="a2bb9-186">Anger en kort text Beskrivning av enheten.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-186">Specifies a brief text description of the drive.</span></span> <span data-ttu-id="a2bb9-187">Skriv valfri sträng.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-187">Type any string.</span></span>

<span data-ttu-id="a2bb9-188">Om du vill se beskrivningar av alla enheter i sessionen `Get-PSDrive | Format-Table Name, Description` .</span><span class="sxs-lookup"><span data-stu-id="a2bb9-188">To see the descriptions of all the session's drives, `Get-PSDrive | Format-Table Name, Description`.</span></span>

<span data-ttu-id="a2bb9-189">Om du vill se en beskrivning av en viss enhet skriver du `(Get-PSDrive <DriveName>).Description` .</span><span class="sxs-lookup"><span data-stu-id="a2bb9-189">To see the description of a particular drive, type `(Get-PSDrive <DriveName>).Description`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a2bb9-190">-Name</span><span class="sxs-lookup"><span data-stu-id="a2bb9-190">-Name</span></span>

<span data-ttu-id="a2bb9-191">Anger ett namn på den nya enheten.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-191">Specifies a name for the new drive.</span></span> <span data-ttu-id="a2bb9-192">Använd en enhets beteckning för beständiga mappade nätverks enheter.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-192">For persistent mapped network drives, use a drive letter.</span></span> <span data-ttu-id="a2bb9-193">För temporära PowerShell-enheter är du inte begränsad till enhets beteckningar, Använd en giltig sträng.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-193">For temporary PowerShell drives, you aren't limited to drive letters, use any valid string.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a2bb9-194">-Behåll</span><span class="sxs-lookup"><span data-stu-id="a2bb9-194">-Persist</span></span>

<span data-ttu-id="a2bb9-195">Anger att denna cmdlet skapar en Windows-mappad nätverks enhet.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-195">Indicates that this cmdlet creates a Windows mapped network drive.</span></span> <span data-ttu-id="a2bb9-196">**Persist** -parametern är endast tillgänglig i Windows.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-196">The **Persist** parameter is only available on Windows.</span></span>

<span data-ttu-id="a2bb9-197">Mappade nätverks enheter sparas i Windows på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-197">Mapped network drives are saved in Windows on the local computer.</span></span> <span data-ttu-id="a2bb9-198">De är beständiga, inte sessionsbaserade, och kan visas och hanteras i Utforskaren och andra verktyg.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-198">They're persistent, not session-specific, and can be viewed and managed in File Explorer and other tools.</span></span>

<span data-ttu-id="a2bb9-199">När du omfångerar kommandot lokalt, utan punkt-källa, behålls inte den **kvarhållna** parametern skapandet av en **PSDrive** utanför den omfattning där du kör kommandot.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-199">When you scope the command locally, without dot-sourcing, the **Persist** parameter doesn't persist the creation of a **PSDrive** beyond the scope in which you run the command.</span></span> <span data-ttu-id="a2bb9-200">Om du kör `New-PSDrive` inuti ett skript och du vill att den nya enheten ska vara oändlig, måste du punkt-källa skriptet.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-200">If you run `New-PSDrive` inside a script, and you want the new drive to persist indefinitely, you must dot-source the script.</span></span> <span data-ttu-id="a2bb9-201">För bästa resultat bör du, för att tvinga en ny enhet att behållas, ange **Global** som värde för **omfattnings** parametern och inkludera **Spara** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-201">For best results, to force a new drive to persist, specify **Global** as the value of the **Scope** parameter and include **Persist** in your command.</span></span>

<span data-ttu-id="a2bb9-202">Namnet på enheten måste vara en bokstav, till exempel `D` eller `E` .</span><span class="sxs-lookup"><span data-stu-id="a2bb9-202">The name of the drive must be a letter, such as `D` or `E`.</span></span> <span data-ttu-id="a2bb9-203">Värdet för **rot** parametern måste vara en UNC-sökväg till en annan dator.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-203">The value of **Root** parameter must be a UNC path of a different computer.</span></span> <span data-ttu-id="a2bb9-204">Värdet för parametern **PSProvider** måste vara `FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="a2bb9-204">The **PSProvider** parameter's value must be `FileSystem`.</span></span>

<span data-ttu-id="a2bb9-205">Använd cmdleten om du vill koppla från en Windows-mappad nätverks enhet `Remove-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="a2bb9-205">To disconnect a Windows mapped network drive, use the `Remove-PSDrive` cmdlet.</span></span> <span data-ttu-id="a2bb9-206">När du kopplar från en Windows-mappad nätverks enhet tas mappningen bort permanent från datorn och tas inte bort från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-206">When you disconnect a Windows mapped network drive, the mapping is permanently deleted from the computer, not just deleted from the current session.</span></span>

<span data-ttu-id="a2bb9-207">Mappade nätverks enheter är speciella för ett användar konto.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-207">Mapped network drives are specific to a user account.</span></span> <span data-ttu-id="a2bb9-208">Mappade enheter som har skapats i utökade sessioner eller sessioner som använder autentiseringsuppgifter för en annan användare är inte synliga i sessioner som har startats med andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-208">Mapped drives created in elevated sessions or sessions using the credential of another user aren't visible in sessions started using different credentials.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a2bb9-209">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="a2bb9-209">-PSProvider</span></span>

<span data-ttu-id="a2bb9-210">Anger den PowerShell-provider som stöder enheter av den här typen.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-210">Specifies the PowerShell provider that supports drives of this kind.</span></span>

<span data-ttu-id="a2bb9-211">Om enheten till exempel är kopplad till en nätverks resurs eller fil system katalog är PowerShell-providern `FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="a2bb9-211">For example, if the drive is associated with a network share or file system directory, the PowerShell provider is `FileSystem`.</span></span> <span data-ttu-id="a2bb9-212">Om enheten är associerad med en register nyckel är providern `Registry` .</span><span class="sxs-lookup"><span data-stu-id="a2bb9-212">If the drive is associated with a registry key, the provider is `Registry`.</span></span>

<span data-ttu-id="a2bb9-213">Tillfälliga PowerShell-enheter kan associeras med valfri PowerShell-Provider.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-213">Temporary PowerShell drives can be associated with any PowerShell provider.</span></span> <span data-ttu-id="a2bb9-214">Mappade nätverks enheter kan endast kopplas till `FileSystem` providern.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-214">Mapped network drives can be associated only with the `FileSystem` provider.</span></span>

<span data-ttu-id="a2bb9-215">Om du vill se en lista över providers i PowerShell-sessionen använder du `Get-PSProvider` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-215">To see a list of the providers in your PowerShell session, use the `Get-PSProvider` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a2bb9-216">– Rot</span><span class="sxs-lookup"><span data-stu-id="a2bb9-216">-Root</span></span>

<span data-ttu-id="a2bb9-217">Anger den data lager plats som en PowerShell-enhet mappas till.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-217">Specifies the data store location to which a PowerShell drive is mapped.</span></span>

<span data-ttu-id="a2bb9-218">Du kan till exempel ange en nätverks resurs, till exempel `\\Server01\Public` en lokal katalog, till exempel `C:\Program Files` eller en register nyckel, till exempel `HKLM:\Software\Microsoft` .</span><span class="sxs-lookup"><span data-stu-id="a2bb9-218">For example, specify a network share, such as `\\Server01\Public`, a local directory, such as `C:\Program Files`, or a registry key, such as `HKLM:\Software\Microsoft`.</span></span>

<span data-ttu-id="a2bb9-219">Tillfälliga PowerShell-enheter kan associeras med en lokal plats eller en annan plats på en leverantörs enhet som stöds.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-219">Temporary PowerShell drives can be associated with a local or remote location on any supported provider drive.</span></span> <span data-ttu-id="a2bb9-220">Mappade nätverks enheter kan bara kopplas till en fil system plats på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-220">Mapped network drives can be associated only with a file system location on a remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a2bb9-221">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="a2bb9-221">-Scope</span></span>

<span data-ttu-id="a2bb9-222">Anger ett omfång för enheten.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-222">Specifies a scope for the drive.</span></span> <span data-ttu-id="a2bb9-223">De acceptabla värdena för den här parametern är: **globalt** , **lokalt** och **skript** , eller ett tal i förhållande till det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-223">The acceptable values for this parameter are: **Global** , **Local** , and **Script** , or a number relative to the current scope.</span></span> <span data-ttu-id="a2bb9-224">Omfattnings nummer 0 till och med antalet omfattningar.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-224">Scopes number 0 through the number of scopes.</span></span> <span data-ttu-id="a2bb9-225">Det aktuella omfångs numret är 0 och dess överordnade är 1.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-225">The current scope number is 0 and its parent is 1.</span></span> <span data-ttu-id="a2bb9-226">Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="a2bb9-226">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a2bb9-227">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="a2bb9-227">-UseTransaction</span></span>

<span data-ttu-id="a2bb9-228">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-228">Includes the command in the active transaction.</span></span> <span data-ttu-id="a2bb9-229">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-229">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="a2bb9-230">Mer information finns i [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="a2bb9-230">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a2bb9-231">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a2bb9-231">-WhatIf</span></span>

<span data-ttu-id="a2bb9-232">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-232">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a2bb9-233">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-233">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="a2bb9-234">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a2bb9-234">CommonParameters</span></span>

<span data-ttu-id="a2bb9-235">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="a2bb9-235">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="a2bb9-236">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a2bb9-236">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a2bb9-237">INDATA</span><span class="sxs-lookup"><span data-stu-id="a2bb9-237">INPUTS</span></span>

### <span data-ttu-id="a2bb9-238">Inget</span><span class="sxs-lookup"><span data-stu-id="a2bb9-238">None</span></span>

<span data-ttu-id="a2bb9-239">Du kan inte pipeline-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-239">You can't pipeline input to this cmdlet.</span></span>

## <span data-ttu-id="a2bb9-240">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a2bb9-240">OUTPUTS</span></span>

### <span data-ttu-id="a2bb9-241">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="a2bb9-241">System.Management.Automation.PSDriveInfo</span></span>

## <span data-ttu-id="a2bb9-242">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a2bb9-242">NOTES</span></span>

<span data-ttu-id="a2bb9-243">`New-PSDrive` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-243">`New-PSDrive` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a2bb9-244">Om du vill visa en lista över tillgängliga providers i sessionen använder du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="a2bb9-244">To list the providers available in your session, use `Get-PSProvider`.</span></span> <span data-ttu-id="a2bb9-245">Mer information om providrar finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="a2bb9-245">For more information about providers, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="a2bb9-246">Mappade nätverks enheter är speciella för ett användar konto.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-246">Mapped network drives are specific to a user account.</span></span> <span data-ttu-id="a2bb9-247">Mappade enheter som har skapats i utökade sessioner eller sessioner som använder autentiseringsuppgifter för en annan användare är inte synliga i sessioner som har startats med andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="a2bb9-247">Mapped drives created in elevated sessions or sessions using the credential of another user aren't visible in sessions started using different credentials.</span></span>

## <span data-ttu-id="a2bb9-248">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a2bb9-248">RELATED LINKS</span></span>

[<span data-ttu-id="a2bb9-249">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a2bb9-249">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="a2bb9-250">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="a2bb9-250">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="a2bb9-251">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="a2bb9-251">Get-PSDrive</span></span>](Get-PSDrive.md)

[<span data-ttu-id="a2bb9-252">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="a2bb9-252">Remove-PSDrive</span></span>](Remove-PSDrive.md)
