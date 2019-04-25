---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Kända problem i WMF 5.1
ms.openlocfilehash: e59ea1b9a5282eb5727a37ce605c71724a219827
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084971"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="a6bf5-103">Kända problem i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="a6bf5-103">Known Issues in WMF 5.1</span></span>

> [!Note]
> <span data-ttu-id="a6bf5-104">Den här informationen kan komma att ändras.</span><span class="sxs-lookup"><span data-stu-id="a6bf5-104">This information is subject to change.</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="a6bf5-105">Starta PowerShell-genväg som administratör</span><span class="sxs-lookup"><span data-stu-id="a6bf5-105">Starting PowerShell shortcut as Administrator</span></span>

<span data-ttu-id="a6bf5-106">Om du försöker starta PowerShell som administratör från genvägen till vid installation av WMF, kan du få meddelandet ”okänt fel”.</span><span class="sxs-lookup"><span data-stu-id="a6bf5-106">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span>
<span data-ttu-id="a6bf5-107">Öppna genväg som icke-administratör och genvägen nu fungerar även som administratör.</span><span class="sxs-lookup"><span data-stu-id="a6bf5-107">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="a6bf5-108">Lära</span><span class="sxs-lookup"><span data-stu-id="a6bf5-108">Pester</span></span>

<span data-ttu-id="a6bf5-109">Det finns två problem som du bör känna till när du använder Pester på Nano Server i den här versionen:</span><span class="sxs-lookup"><span data-stu-id="a6bf5-109">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

- <span data-ttu-id="a6bf5-110">Kör tester mot Pester själva kan resultera i några fel på grund av skillnader mellan fullständig CLR- och CORE CLR.</span><span class="sxs-lookup"><span data-stu-id="a6bf5-110">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="a6bf5-111">I synnerhet är verifiera-metoden inte tillgänglig på vilken XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="a6bf5-111">In particular, the Validate method is not available on the XmlDocument type.</span></span> <span data-ttu-id="a6bf5-112">Sex tester som försöker verifiera schemat för utdataloggar NUnit är kända misslyckas.</span><span class="sxs-lookup"><span data-stu-id="a6bf5-112">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
- <span data-ttu-id="a6bf5-113">En kod täckning testet misslyckas just nu eftersom den *WindowsFeature* DSC-resursen finns inte i Nano Server.</span><span class="sxs-lookup"><span data-stu-id="a6bf5-113">One Code Coverage test fails currently because the *WindowsFeature* DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="a6bf5-114">De här felen är vanligtvis ofarlig och på ett säkert sätt kan ignoreras.</span><span class="sxs-lookup"><span data-stu-id="a6bf5-114">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="a6bf5-115">Validering av</span><span class="sxs-lookup"><span data-stu-id="a6bf5-115">Operation Validation</span></span>

- <span data-ttu-id="a6bf5-116">`Update-Help` misslyckas för Microsoft.PowerShell.Operation.Validation modulen på grund av icke-fungerande hjälp URI</span><span class="sxs-lookup"><span data-stu-id="a6bf5-116">`Update-Help` fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="a6bf5-117">DSC efter avinstallera WMF</span><span class="sxs-lookup"><span data-stu-id="a6bf5-117">DSC after uninstall WMF</span></span>

- <span data-ttu-id="a6bf5-118">Avinstallera WMF tar inte bort DSC MOF-dokument från konfigurationsmappen.</span><span class="sxs-lookup"><span data-stu-id="a6bf5-118">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="a6bf5-119">DSC fungerar inte korrekt om MOF-dokument innehåller nyare egenskaper som inte är tillgängliga på de äldre systemen.</span><span class="sxs-lookup"><span data-stu-id="a6bf5-119">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="a6bf5-120">I det här fallet kör följande skript från en upphöjd PowerShell-konsol att rensa DSC-tillstånd.</span><span class="sxs-lookup"><span data-stu-id="a6bf5-120">In this case, run the following script from elevated PowerShell console to clean up the DSC states.</span></span>

  ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )
    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="a6bf5-121">JEA virtuella konton</span><span class="sxs-lookup"><span data-stu-id="a6bf5-121">JEA Virtual Accounts</span></span>

<span data-ttu-id="a6bf5-122">JEA-slutpunkter och sessionskonfigurationer som konfigurerats för att använda virtuella konton i WMF 5.0 ska inte konfigureras för att använda ett virtuellt konto när du har uppgraderat till WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="a6bf5-122">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span>
<span data-ttu-id="a6bf5-123">Det innebär att kommandon som körs i JEA-sessioner kommer att köras under den anslutande användarens identitet i stället för ett tillfälligt administratörskonto, potentiellt hindrar användaren från att köra kommandon som kräver utökade privilegier.</span><span class="sxs-lookup"><span data-stu-id="a6bf5-123">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span>
<span data-ttu-id="a6bf5-124">Om du vill återställa de virtuella kontona, måste du avregistrera och Omregistrera alla sessionskonfigurationer som använder virtuella konton.</span><span class="sxs-lookup"><span data-stu-id="a6bf5-124">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```