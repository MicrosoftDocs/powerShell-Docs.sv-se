---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 3d74217621d00dfd68cad1c45d187a9c2ffb9980
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085290"
---
# <a name="known-issues-and-limitations"></a><span data-ttu-id="e6f9e-102">Kända problem och begränsningar</span><span class="sxs-lookup"><span data-stu-id="e6f9e-102">Known Issues and Limitations</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="e6f9e-103">PowerShell genvägar bryts när den används för första gången</span><span class="sxs-lookup"><span data-stu-id="e6f9e-103">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="e6f9e-104">**Lösning:** Gör något av följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="e6f9e-104">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="e6f9e-105">Högerklicka på genvägen till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-105">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="e6f9e-106">Välj ”Windows PowerShell” för att starta i ett icke-upphöjd-läge.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-106">Select “Windows PowerShell” to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="e6f9e-107">Högerklicka på genvägen till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-107">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="e6f9e-108">Högerklicka på ”Windows PowerShell” och välj ”Kör som administratör” att starta en förhöjd behörighet.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-108">Right click on “Windows PowerShell” and select “Run As Administrator” to launch in an elevated mode.</span></span>

<span data-ttu-id="e6f9e-109">När du har utfört någon av ovanstående åtgärder, fungerar PowerShell-genvägar.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-109">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="e6f9e-110">Dessa åtgärder måste utföras en gång.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-110">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="e6f9e-111">PowerShell-moduler och DSC-resurser rapportera fel om ExecutionPolicy på Windows 7</span><span class="sxs-lookup"><span data-stu-id="e6f9e-111">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="e6f9e-112">Använda PowerShell-moduler och DSC-resurser kan resultera i fel som rapporterats om ExecutionPolicy på Windows 7.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-112">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="e6f9e-113">**Lösning:** Ange körningsprincipen till RemoteSigned genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):</span><span class="sxs-lookup"><span data-stu-id="e6f9e-113">**Resolution:** Set the ExecutionPolicy to RemoteSigned by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="e6f9e-114">Ansluta till en gammal fjärrslutpunkten Exchange orsakar en krasch</span><span class="sxs-lookup"><span data-stu-id="e6f9e-114">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="e6f9e-115">Den gamla Exchange-slutpunkten omdirigerar till en ny slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-115">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="e6f9e-116">Det finns en bugg i omdirigering logik som uppstår i en krasch.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-116">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="e6f9e-117">**Lösning:** Ansluta direkt till den nya slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-117">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="e6f9e-118">Software Inventory Logging funktionen stoppas felaktigt efter installation av WMF 5.0 på Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="e6f9e-118">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="e6f9e-119">När du installerar WMF 5.0 på en Windows Server 2012 R2 som redan kör SIL, stoppas felaktigt funktionen Software Inventory Logging efter installationen.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-119">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="e6f9e-120">**Lösning:** Köra cmdleten Start-SilLogging en gång efter WMF-installationen eftersom installationsprocessen avbryts felaktigt funktionen Software Inventory Logging.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-120">**Resolution:** Run the Start-SilLogging cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="e6f9e-121">`Get-ChildItem` fungerar inte om - LiteralPath och -Recurse används tillsammans</span><span class="sxs-lookup"><span data-stu-id="e6f9e-121">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="e6f9e-122">Om ett katalognamn innehåller ett ogiltigt jokertecken sedan `Get-ChildItem` skapas inte förväntat resultat när både - LiteralPath och -Recurse används tillsammans.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-122">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="e6f9e-123">**Lösning:** Inte den bästa lösningen, men aktuella lösningen är att implementera rekursion i skriptet i stället för att förlita dig på cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-123">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="e6f9e-124">Sysprep misslyckas efter installationen av WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="e6f9e-124">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="e6f9e-125">Det finns två lösningar på problemet beroende på vilken version av Windows Server du kör.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-125">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="e6f9e-126">**Lösning:**</span><span class="sxs-lookup"><span data-stu-id="e6f9e-126">**Resolution:**</span></span>

- <span data-ttu-id="e6f9e-127">För system som kör **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="e6f9e-127">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="e6f9e-128">Öppna PowerShell som administratör</span><span class="sxs-lookup"><span data-stu-id="e6f9e-128">Open PowerShell as an administrator</span></span>
  2. <span data-ttu-id="e6f9e-129">Kör följande kommando</span><span class="sxs-lookup"><span data-stu-id="e6f9e-129">Run the following command</span></span>

     ```powershell
     Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="e6f9e-130">Kör kommandot och ignorera felet, som de är förväntat.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-130">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="e6f9e-131">Ta bort filer i \Windows\System32\Logfiles\SIL\ katalog</span><span class="sxs-lookup"><span data-stu-id="e6f9e-131">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="e6f9e-132">Installera alla tillgängliga viktiga Windows uppdateringar och börja Sysyprep åtgärden normalt.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-132">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="e6f9e-133">För system som kör **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="e6f9e-133">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="e6f9e-134">När du har installerat WMF 5.0 på servern för att d Sysprep, logga in som administratör.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-134">After installing WMF 5.0 on the server to be Sysprep’d, login as administrator.</span></span>
  2. <span data-ttu-id="e6f9e-135">Kopiera Generize.xml från katalogen \Windows\System32\Sysprep\ActionFiles\ till en plats utanför Windows-katalogen, C:\ till exempel.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-135">Copy Generize.xml from directory \Windows\System32\Sysprep\ActionFiles\ to a location outside of the Windows directory, C:\ for example.</span></span>
  3. <span data-ttu-id="e6f9e-136">Öppna din Generalize.xml kopia i anteckningar.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-136">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="e6f9e-137">Hitta och ta bort följande text, en instans av varje behov som ska tas bort (de är slutet av dokumentet).</span><span class="sxs-lookup"><span data-stu-id="e6f9e-137">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="e6f9e-138">Spara den redigerade kopian av Generalize.xml och stäng filen.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-138">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="e6f9e-139">Öppna en kommandotolk som administratör</span><span class="sxs-lookup"><span data-stu-id="e6f9e-139">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="e6f9e-140">Kör följande kommando för att bli ägare av filen Generalize.xml i system32-mapp:</span><span class="sxs-lookup"><span data-stu-id="e6f9e-140">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="e6f9e-141">Kör följande kommando för att ange rätt behörighet för filen:</span><span class="sxs-lookup"><span data-stu-id="e6f9e-141">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="e6f9e-142">Svara Ja i Kommandotolken för bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-142">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="e6f9e-143">Observera att `<AdministratorUserName>` ska ersättas med det användarnamn som är administratör på datorn.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-143">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="e6f9e-144">Till exempel ”administratör”.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-144">For example, "Administrator".</span></span>

  9. <span data-ttu-id="e6f9e-145">Kopiera filen du redigeras och sparas över i Sysprep-katalogen med följande kommando:</span><span class="sxs-lookup"><span data-stu-id="e6f9e-145">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="e6f9e-146">Svara Ja om du vill skriva över (Observera att om det finns ingen uppmaning om att skriva över, kontrollera den angivna sökvägen).</span><span class="sxs-lookup"><span data-stu-id="e6f9e-146">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="e6f9e-147">Förutsätter att den redigerade kopian av Generalize.xml kopierades till C:\.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-147">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="e6f9e-148">Generalize.XML har uppdaterats med lösningen.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-148">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="e6f9e-149">Kör Sysprep med alternativet generalize aktiverat.</span><span class="sxs-lookup"><span data-stu-id="e6f9e-149">Please run Sysprep with the generalize option enabled.</span></span>