---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: e8620cdeb90792e86d091d3e19a169f9dfa690f9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="known-issues-and-limitations"></a><span data-ttu-id="e5cab-102">Kända problem och begränsningar</span><span class="sxs-lookup"><span data-stu-id="e5cab-102">Known Issues and Limitations</span></span>

<a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="e5cab-103">PowerShell genvägar bryts när den används för första gången</span><span class="sxs-lookup"><span data-stu-id="e5cab-103">PowerShell Shortcuts are broken when used for the first time</span></span>
------------------------------------------------------------

<span data-ttu-id="e5cab-104">**Lösning:** utför något av följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="e5cab-104">**Resolution:** Perform one of the following actions:</span></span>

1.  <span data-ttu-id="e5cab-105">Högerklicka på genvägen för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e5cab-105">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="e5cab-106">Välj ”Windows PowerShell” för att starta i ett icke-upphöjd-läge.</span><span class="sxs-lookup"><span data-stu-id="e5cab-106">Select “Windows PowerShell” to launch in a non-elevated mode.</span></span>
2.  <span data-ttu-id="e5cab-107">Högerklicka på genvägen för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e5cab-107">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="e5cab-108">Högerklicka på ”Windows PowerShell” och välj ”Kör som administratör” att starta en förhöjd behörighet.</span><span class="sxs-lookup"><span data-stu-id="e5cab-108">Right click on “Windows PowerShell” and select “Run As Administrator” to launch in an elevated mode.</span></span>

<span data-ttu-id="e5cab-109">När du har utfört någon av ovanstående åtgärder fungerar PowerShell genvägar.</span><span class="sxs-lookup"><span data-stu-id="e5cab-109">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="e5cab-110">Dessa åtgärder måste utföras en gång.</span><span class="sxs-lookup"><span data-stu-id="e5cab-110">These actions need to be performed only once.</span></span>


<a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="e5cab-111">PowerShell-moduler och DSC resurser rapportera fel om körningsprincipen på Windows 7</span><span class="sxs-lookup"><span data-stu-id="e5cab-111">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>
-------------------------------------------------------------------------------------
<span data-ttu-id="e5cab-112">Användningen av PowerShell-moduler och DSC-resurser kan resultera i fel som rapporteras om körningsprincipen på Windows 7.</span><span class="sxs-lookup"><span data-stu-id="e5cab-112">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="e5cab-113">**Lösning:** inställd på körningsprincipen på RemoteSigned genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):</span><span class="sxs-lookup"><span data-stu-id="e5cab-113">**Resolution:** Set the ExecutionPolicy to RemoteSigned by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="e5cab-114">Ansluter till en gammal fjärrslutpunkten Exchange orsakar en krasch</span><span class="sxs-lookup"><span data-stu-id="e5cab-114">Connecting to an old remote Exchange endpoint causes a crash</span></span>
------------------------------------------------------------

<span data-ttu-id="e5cab-115">Den gamla Exchange-slutpunkten omdirigerar till en ny slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="e5cab-115">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="e5cab-116">Det finns ett fel i omdirigering av logik som uppstår i en krasch.</span><span class="sxs-lookup"><span data-stu-id="e5cab-116">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="e5cab-117">**Lösning:** Anslut direkt till ny slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="e5cab-117">**Resolution:** Connect directly to the new endpoint.</span></span>


<a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="e5cab-118">Software Inventory Logging funktionen stoppas felaktigt efter installationen av WMF 5.0 på Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="e5cab-118">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>
-------------------------------------------------------------------------------------------------------------

<span data-ttu-id="e5cab-119">När du installerar WMF 5.0 på en Windows Server 2012 R2 som redan kör SIL stoppas felaktigt funktionen Software Inventory Logging efter installationen.</span><span class="sxs-lookup"><span data-stu-id="e5cab-119">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="e5cab-120">**Lösning:** köra cmdleten Start-SilLogging en gång efter WMF-installationen som installationen avbryts felaktigt funktionen Software Inventory Logging.</span><span class="sxs-lookup"><span data-stu-id="e5cab-120">**Resolution:** Run the Start-SilLogging cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

<a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="e5cab-121">Get-ChildItem fungerar inte om - LiteralPath och -Recurse används tillsammans</span><span class="sxs-lookup"><span data-stu-id="e5cab-121">Get-ChildItem does not work if -LiteralPath and -Recurse are used together</span></span>
--------------------------------------------------------------------------

<span data-ttu-id="e5cab-122">Om ett katalognamn innehåller ett ogiltigt jokertecken, sedan Get-ChildItem kommer inte att generera förväntat resultat när både - LiteralPath och -Recurse används tillsammans.</span><span class="sxs-lookup"><span data-stu-id="e5cab-122">If a directory name contains an invalid wildcard character, then Get-ChildItem will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="e5cab-123">**Lösning:** inte den bästa lösningen, men aktuella lösningen är att implementera rekursion i skriptet i stället för att förlita dig på cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e5cab-123">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>


<a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="e5cab-124">Sysprep misslyckas efter installationen av WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="e5cab-124">Sysprep fails after WMF 5.0 installation</span></span>
----------------------------------------

<span data-ttu-id="e5cab-125">Det finns två lösningar på problemet beroende på vilken version av Windows Server körs.</span><span class="sxs-lookup"><span data-stu-id="e5cab-125">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="e5cab-126">**Lösning:**</span><span class="sxs-lookup"><span data-stu-id="e5cab-126">**Resolution:**</span></span>
- <span data-ttu-id="e5cab-127">För datorer som kör **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="e5cab-127">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="e5cab-128">Öppna Powershell som administratör</span><span class="sxs-lookup"><span data-stu-id="e5cab-128">Open Powershell as an administrator</span></span>
  2. <span data-ttu-id="e5cab-129">Kör följande kommando</span><span class="sxs-lookup"><span data-stu-id="e5cab-129">Run the following command</span></span> 
  
  ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
  ```
  3. <span data-ttu-id="e5cab-130">Kör kommandot och ignorera felet, som de är förväntat.</span><span class="sxs-lookup"><span data-stu-id="e5cab-130">Run the command and ignore the error, as they are expected.</span></span>
  
  ```powershell
    Publish-SilData
   ```
  4. <span data-ttu-id="e5cab-131">Ta bort filer i \Windows\System32\Logfiles\SIL\ katalog</span><span class="sxs-lookup"><span data-stu-id="e5cab-131">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>
  
  ```powershell
    Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5. <span data-ttu-id="e5cab-132">Installera alla tillgängliga viktiga uppdateringar för Windows och börja Sysyprep åtgärden normalt.</span><span class="sxs-lookup"><span data-stu-id="e5cab-132">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>
  
- <span data-ttu-id="e5cab-133">För datorer som kör **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="e5cab-133">For systems running **Windows Server 2012**</span></span>
  1.    <span data-ttu-id="e5cab-134">När du har installerat WMF 5.0 på servern för att d Sysprep, logga in som administratör.</span><span class="sxs-lookup"><span data-stu-id="e5cab-134">After installing WMF 5.0 on the server to be Sysprep’d, login as administrator.</span></span>
  2.    <span data-ttu-id="e5cab-135">Kopiera Generize.xml från katalogen \Windows\System32\Sysprep\ActionFiles\ till en plats utanför Windows-katalogen C:\ t.ex.</span><span class="sxs-lookup"><span data-stu-id="e5cab-135">Copy Generize.xml from directory \Windows\System32\Sysprep\ActionFiles\ to a location outside of the Windows directory, C:\ for example.</span></span>
  3.    <span data-ttu-id="e5cab-136">Öppna din Generalize.xml kopia med anteckningar.</span><span class="sxs-lookup"><span data-stu-id="e5cab-136">Open your Generalize.xml copy with notepad.</span></span>
  4.    <span data-ttu-id="e5cab-137">Hitta och ta bort följande text, en instans av varje måste tas bort (de är i slutet av dokumentet).</span><span class="sxs-lookup"><span data-stu-id="e5cab-137">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```

  5.    <span data-ttu-id="e5cab-138">Spara den redigerade kopian av Generalize.xml och stäng filen.</span><span class="sxs-lookup"><span data-stu-id="e5cab-138">Save the edited copy of Generalize.xml and close the file.</span></span>
  6.    <span data-ttu-id="e5cab-139">Öppna en kommandotolk som administratör</span><span class="sxs-lookup"><span data-stu-id="e5cab-139">Open a command prompt as administrator</span></span>
  7.    <span data-ttu-id="e5cab-140">Kör följande kommando för att bli ägare till Generalize.xml-fil i mappen system32:</span><span class="sxs-lookup"><span data-stu-id="e5cab-140">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

    ```
    Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml 
    ```

  8.    <span data-ttu-id="e5cab-141">Kör följande kommando för att ange behörighet för filen:</span><span class="sxs-lookup"><span data-stu-id="e5cab-141">Run the following command to set appropriate permission on the file:</span></span>

    ```
    Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F 
    ```
      * <span data-ttu-id="e5cab-142">Svarar Ja i Kommandotolken för att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="e5cab-142">Answer Yes at the prompt for confirmation.</span></span> 
      * <span data-ttu-id="e5cab-143">Observera att `<AdministratorUserName>` ska ersättas med det användarnamn som är administratör på datorn.</span><span class="sxs-lookup"><span data-stu-id="e5cab-143">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="e5cab-144">Till exempel ”administratör”.</span><span class="sxs-lookup"><span data-stu-id="e5cab-144">For example, "Administrator".</span></span>
      
  9.    <span data-ttu-id="e5cab-145">Kopiera filen du redigeras och sparas över till katalogen Sysprep med följande kommando:</span><span class="sxs-lookup"><span data-stu-id="e5cab-145">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

    ```
    xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml 
    ```
      * <span data-ttu-id="e5cab-146">Svara på Ja om du vill skriva över (Observera att om det finns ingen fråga för att ersätta dubbla Kontrollera den angivna sökvägen).</span><span class="sxs-lookup"><span data-stu-id="e5cab-146">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
      * <span data-ttu-id="e5cab-147">Förutsätter att den redigerade kopian av Generalize.xml kopierades till C:\.</span><span class="sxs-lookup"><span data-stu-id="e5cab-147">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10.   <span data-ttu-id="e5cab-148">Generalize.XML har uppdaterats med lösningen.</span><span class="sxs-lookup"><span data-stu-id="e5cab-148">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="e5cab-149">Kör Sysprep med alternativet generalize aktiverat.</span><span class="sxs-lookup"><span data-stu-id="e5cab-149">Please run Sysprep with the generalize option enabled.</span></span>

