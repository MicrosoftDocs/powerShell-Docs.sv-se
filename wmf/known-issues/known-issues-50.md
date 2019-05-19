---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Kända problem i WMF 5.0
ms.openlocfilehash: 91f556cb43ef971107f05c4041b725b1c7e4f1bd
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856359"
---
# <a name="known-issues-in-wmf-50"></a><span data-ttu-id="35b2c-103">Kända problem i WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="35b2c-103">Known Issues in WMF 5.0</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="35b2c-104">PowerShell genvägar bryts när den används för första gången</span><span class="sxs-lookup"><span data-stu-id="35b2c-104">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="35b2c-105">**Lösning:** Gör något av följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="35b2c-105">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="35b2c-106">Högerklicka på genvägen till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35b2c-106">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="35b2c-107">Välj ”Windows PowerShell” för att starta i ett icke-upphöjd-läge.</span><span class="sxs-lookup"><span data-stu-id="35b2c-107">Select "Windows PowerShell" to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="35b2c-108">Högerklicka på genvägen till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35b2c-108">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="35b2c-109">Högerklicka på ”Windows PowerShell” och välj ”Kör som administratör” att starta en förhöjd behörighet.</span><span class="sxs-lookup"><span data-stu-id="35b2c-109">Right click on "Windows PowerShell" and select "Run As Administrator" to launch in an elevated mode.</span></span>

<span data-ttu-id="35b2c-110">När du har utfört någon av ovanstående åtgärder, fungerar PowerShell-genvägar.</span><span class="sxs-lookup"><span data-stu-id="35b2c-110">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="35b2c-111">Dessa åtgärder måste utföras en gång.</span><span class="sxs-lookup"><span data-stu-id="35b2c-111">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="35b2c-112">PowerShell-moduler och DSC-resurser rapportera fel om ExecutionPolicy på Windows 7</span><span class="sxs-lookup"><span data-stu-id="35b2c-112">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="35b2c-113">På Windows 7, kan med hjälp av PowerShell-moduler och DSC-resurser resultera i fel som rapporterats om ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="35b2c-113">On Windows 7, using PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="35b2c-114">**Lösning:** Ange ExecutionPolicy **RemoteSigned** genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):</span><span class="sxs-lookup"><span data-stu-id="35b2c-114">**Resolution:** Set the ExecutionPolicy to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="35b2c-115">Ansluta till en gammal fjärrslutpunkten Exchange orsakar en krasch</span><span class="sxs-lookup"><span data-stu-id="35b2c-115">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="35b2c-116">Den gamla Exchange-slutpunkten omdirigerar till en ny slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="35b2c-116">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="35b2c-117">Det finns en bugg i omdirigering logik som uppstår i en krasch.</span><span class="sxs-lookup"><span data-stu-id="35b2c-117">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="35b2c-118">**Lösning:** Ansluta direkt till den nya slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="35b2c-118">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="35b2c-119">Software Inventory Logging funktionen stoppas felaktigt efter installation av WMF 5.0 på Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="35b2c-119">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="35b2c-120">När du installerar WMF 5.0 på en Windows Server 2012 R2 som redan kör SIL, stoppas felaktigt funktionen Software Inventory Logging efter installationen.</span><span class="sxs-lookup"><span data-stu-id="35b2c-120">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="35b2c-121">**Lösning:** Kör den `Start-SilLogging` cmdlet en gång efter WMF-installationen som installationsprocessen avbryts felaktigt funktionen Software Inventory Logging.</span><span class="sxs-lookup"><span data-stu-id="35b2c-121">**Resolution:** Run the `Start-SilLogging` cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="35b2c-122">`Get-ChildItem` fungerar inte om - LiteralPath och -Recurse används tillsammans</span><span class="sxs-lookup"><span data-stu-id="35b2c-122">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="35b2c-123">Om ett katalognamn innehåller ett ogiltigt jokertecken sedan `Get-ChildItem` skapas inte förväntat resultat när både - LiteralPath och -Recurse används tillsammans.</span><span class="sxs-lookup"><span data-stu-id="35b2c-123">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="35b2c-124">**Lösning:** Inte den bästa lösningen, men aktuella lösningen är att implementera rekursion i skriptet i stället för att förlita dig på cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="35b2c-124">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="35b2c-125">Sysprep misslyckas efter installationen av WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="35b2c-125">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="35b2c-126">Det finns två lösningar på problemet beroende på vilken version av Windows Server du kör.</span><span class="sxs-lookup"><span data-stu-id="35b2c-126">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="35b2c-127">**Lösning:**</span><span class="sxs-lookup"><span data-stu-id="35b2c-127">**Resolution:**</span></span>

- <span data-ttu-id="35b2c-128">För system som kör **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="35b2c-128">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="35b2c-129">Öppna PowerShell som administratör</span><span class="sxs-lookup"><span data-stu-id="35b2c-129">Open PowerShell as an administrator</span></span>
  2. <span data-ttu-id="35b2c-130">Kör följande kommando</span><span class="sxs-lookup"><span data-stu-id="35b2c-130">Run the following command</span></span>

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="35b2c-131">Kör kommandot och ignorera felet, som de är förväntat.</span><span class="sxs-lookup"><span data-stu-id="35b2c-131">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="35b2c-132">Ta bort filer i \Windows\System32\Logfiles\SIL\ katalog</span><span class="sxs-lookup"><span data-stu-id="35b2c-132">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="35b2c-133">Installera alla tillgängliga viktiga Windows uppdateringar och börja Sysyprep åtgärden normalt.</span><span class="sxs-lookup"><span data-stu-id="35b2c-133">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="35b2c-134">För system som kör **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="35b2c-134">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="35b2c-135">När du har installerat WMF 5.0 på servern för att d Sysprep, logga in som administratör.</span><span class="sxs-lookup"><span data-stu-id="35b2c-135">After installing WMF 5.0 on the server to be Sysprep'd, login as administrator.</span></span>
  2. <span data-ttu-id="35b2c-136">Kopiera Generize.xml från katalogen `\Windows\System32\Sysprep\ActionFiles\` till en plats utanför Windows-katalogen `C:\` till exempel.</span><span class="sxs-lookup"><span data-stu-id="35b2c-136">Copy Generize.xml from directory `\Windows\System32\Sysprep\ActionFiles\` to a location outside of the Windows directory, `C:\` for example.</span></span>
  3. <span data-ttu-id="35b2c-137">Öppna din Generalize.xml kopia i anteckningar.</span><span class="sxs-lookup"><span data-stu-id="35b2c-137">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="35b2c-138">Hitta och ta bort följande text, en instans av varje behov som ska tas bort (de är slutet av dokumentet).</span><span class="sxs-lookup"><span data-stu-id="35b2c-138">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="35b2c-139">Spara den redigerade kopian av Generalize.xml och stäng filen.</span><span class="sxs-lookup"><span data-stu-id="35b2c-139">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="35b2c-140">Öppna en kommandotolk som administratör</span><span class="sxs-lookup"><span data-stu-id="35b2c-140">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="35b2c-141">Kör följande kommando för att bli ägare av filen Generalize.xml i system32-mapp:</span><span class="sxs-lookup"><span data-stu-id="35b2c-141">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="35b2c-142">Kör följande kommando för att ange rätt behörighet för filen:</span><span class="sxs-lookup"><span data-stu-id="35b2c-142">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="35b2c-143">Svara Ja i Kommandotolken för bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="35b2c-143">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="35b2c-144">Observera att `<AdministratorUserName>` ska ersättas med det användarnamn som är administratör på datorn.</span><span class="sxs-lookup"><span data-stu-id="35b2c-144">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="35b2c-145">Till exempel ”administratör”.</span><span class="sxs-lookup"><span data-stu-id="35b2c-145">For example, "Administrator".</span></span>

  9. <span data-ttu-id="35b2c-146">Kopiera filen du redigeras och sparas över i Sysprep-katalogen med följande kommando:</span><span class="sxs-lookup"><span data-stu-id="35b2c-146">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="35b2c-147">Svara Ja om du vill skriva över (Observera att om det finns ingen uppmaning om att skriva över, kontrollera den angivna sökvägen).</span><span class="sxs-lookup"><span data-stu-id="35b2c-147">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="35b2c-148">Förutsätter att den redigerade kopian av Generalize.xml kopierades till C:\.</span><span class="sxs-lookup"><span data-stu-id="35b2c-148">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="35b2c-149">Generalize.XML har uppdaterats med lösningen.</span><span class="sxs-lookup"><span data-stu-id="35b2c-149">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="35b2c-150">Kör Sysprep med alternativet generalize aktiverat.</span><span class="sxs-lookup"><span data-stu-id="35b2c-150">Please run Sysprep with the generalize option enabled.</span></span>