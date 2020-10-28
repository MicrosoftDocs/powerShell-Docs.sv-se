---
ms.date: 06/12/2017
title: Kända problem i WMF 5.0
description: Kända problem i WMF 5.0
ms.openlocfilehash: 3f8dcf0f7aab27ff9d3c3a17377959988844a430
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663370"
---
# <a name="known-issues-in-wmf-50"></a><span data-ttu-id="2bbcc-103">Kända problem i WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="2bbcc-103">Known Issues in WMF 5.0</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="2bbcc-104">PowerShell-genvägar är brutna när de används för första gången</span><span class="sxs-lookup"><span data-stu-id="2bbcc-104">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="2bbcc-105">**Lösning:** Utför någon av följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="2bbcc-105">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="2bbcc-106">Högerklicka på PowerShell-genvägen.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-106">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="2bbcc-107">Välj Windows PowerShell för att starta i ett icke-förhöjd läge.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-107">Select "Windows PowerShell" to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="2bbcc-108">Högerklicka på PowerShell-genvägen.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-108">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="2bbcc-109">Högerklicka på "Windows PowerShell" och välj "kör som administratör" för att starta i ett förhöjd läge.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-109">Right click on "Windows PowerShell" and select "Run As Administrator" to launch in an elevated mode.</span></span>

<span data-ttu-id="2bbcc-110">När du har utfört någon av ovanstående åtgärder kommer PowerShell-genvägar att fungera.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-110">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="2bbcc-111">De här åtgärderna behöver bara utföras en gång.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-111">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="2bbcc-112">PowerShell-moduler och DSC-resurser rapporterar fel om ExecutionPolicy i Windows 7</span><span class="sxs-lookup"><span data-stu-id="2bbcc-112">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="2bbcc-113">I Windows 7 kan använda PowerShell-moduler och DSC-resurser resultera i fel som rapporteras om ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-113">On Windows 7, using PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="2bbcc-114">**Lösning:** Ange ExecutionPolicy till **RemoteSigned** genom att köra följande kommando i en upphöjd PowerShell-session (kör som administratör):</span><span class="sxs-lookup"><span data-stu-id="2bbcc-114">**Resolution:** Set the ExecutionPolicy to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="2bbcc-115">Att ansluta till en gammal fjärrslutpunkt i Exchange orsakar en krasch</span><span class="sxs-lookup"><span data-stu-id="2bbcc-115">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="2bbcc-116">Den gamla Exchange-slutpunkten omdirigeras till en ny slut punkt.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-116">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="2bbcc-117">Det finns ett fel i den omdirigerings logik som resulterar i en krasch.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-117">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="2bbcc-118">**Lösning:** Anslut direkt till den nya slut punkten.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-118">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="2bbcc-119">Funktionen för loggning av program varu inventering stoppades felaktigt efter installationen av WMF 5,0 på Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="2bbcc-119">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="2bbcc-120">När du installerar WMF 5,0 på en Windows Server 2012 R2 som redan kör SIL stoppas loggnings funktionen för program varu inventering felaktigt efter installationen.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-120">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="2bbcc-121">**Lösning:** Kör `Start-SilLogging` cmdleten en gång efter WMF-installationen, som installations processen kommer att felaktigt stoppa funktionen för Software Inventory Logging.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-121">**Resolution:** Run the `Start-SilLogging` cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="2bbcc-122">`Get-ChildItem` fungerar inte om-LiteralPath och-rekursivt används tillsammans</span><span class="sxs-lookup"><span data-stu-id="2bbcc-122">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="2bbcc-123">Om ett katalog namn innehåller ett ogiltigt jokertecken `Get-ChildItem` kommer inte att generera förväntade resultat när både-LiteralPath och-rekursivt används tillsammans.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-123">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="2bbcc-124">**Lösning:** Inte idealisk, men den aktuella lösningen är att implementera rekursion i skriptet i stället för att använda cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-124">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="2bbcc-125">Sysprep Miss lyckas efter installation av WMF 5,0</span><span class="sxs-lookup"><span data-stu-id="2bbcc-125">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="2bbcc-126">Det finns två sätt att lösa problemet, beroende på vilken version av Windows Server du kör.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-126">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="2bbcc-127">**Lösning:**</span><span class="sxs-lookup"><span data-stu-id="2bbcc-127">**Resolution:**</span></span>

- <span data-ttu-id="2bbcc-128">För system som kör **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="2bbcc-128">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="2bbcc-129">Öppna PowerShell som administratör</span><span class="sxs-lookup"><span data-stu-id="2bbcc-129">Open PowerShell as an administrator</span></span>
  2. <span data-ttu-id="2bbcc-130">Kör följande kommando</span><span class="sxs-lookup"><span data-stu-id="2bbcc-130">Run the following command</span></span>

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="2bbcc-131">Kör kommandot och Ignorera felet, eftersom det förväntas.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-131">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="2bbcc-132">Ta bort filerna i \Windows\System32\Logfiles\SIL\-katalogen</span><span class="sxs-lookup"><span data-stu-id="2bbcc-132">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="2bbcc-133">Installera alla tillgängliga viktiga Windows-uppdateringar och starta Sysyprep-åtgärden normalt.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-133">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="2bbcc-134">För system som kör **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="2bbcc-134">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="2bbcc-135">Logga in som administratör när du har installerat WMF 5,0 på servern som ska Sysprep.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-135">After installing WMF 5.0 on the server to be Sysprep'd, login as administrator.</span></span>
  2. <span data-ttu-id="2bbcc-136">Kopiera Generize.xml från katalogen `\Windows\System32\Sysprep\ActionFiles\` till en plats utanför Windows-katalogen, till `C:\` exempel.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-136">Copy Generize.xml from directory `\Windows\System32\Sysprep\ActionFiles\` to a location outside of the Windows directory, `C:\` for example.</span></span>
  3. <span data-ttu-id="2bbcc-137">Öppna din Generalize.xml kopia med anteckningar.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-137">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="2bbcc-138">Hitta och ta bort följande text, en instans av varje måste tas bort (de kommer snart i slutet av dokumentet).</span><span class="sxs-lookup"><span data-stu-id="2bbcc-138">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="2bbcc-139">Spara den redigerade kopian av Generalize.xml och Stäng filen.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-139">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="2bbcc-140">Öppna en kommando tolk som administratör</span><span class="sxs-lookup"><span data-stu-id="2bbcc-140">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="2bbcc-141">Kör följande kommando för att bli ägare till Generalize.xml-filen i mappen System32:</span><span class="sxs-lookup"><span data-stu-id="2bbcc-141">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="2bbcc-142">Kör följande kommando för att ange rätt behörighet för filen:</span><span class="sxs-lookup"><span data-stu-id="2bbcc-142">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="2bbcc-143">Svara Ja när du uppmanas att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-143">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="2bbcc-144">Observera att `<AdministratorUserName>` ska ersättas med det användar namn som är administratör på datorn.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-144">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="2bbcc-145">Till exempel "administratör".</span><span class="sxs-lookup"><span data-stu-id="2bbcc-145">For example, "Administrator".</span></span>

  9. <span data-ttu-id="2bbcc-146">Kopiera filen som du redigerade och sparade över till Sysprep-katalogen med följande kommando:</span><span class="sxs-lookup"><span data-stu-id="2bbcc-146">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="2bbcc-147">Svara ja till Skriv över (Observera att om det inte finns någon uppfråga för att skriva över, måste du kontrol lera sökvägen som anges).</span><span class="sxs-lookup"><span data-stu-id="2bbcc-147">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="2bbcc-148">Förutsätter att din redigerade kopia av Generalize.xml har kopierats till C:\.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-148">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="2bbcc-149">Generalize.xml har nu uppdaterats med lösningen.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-149">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="2bbcc-150">Kör Sysprep med generalize-alternativet aktiverat.</span><span class="sxs-lookup"><span data-stu-id="2bbcc-150">Please run Sysprep with the generalize option enabled.</span></span>
