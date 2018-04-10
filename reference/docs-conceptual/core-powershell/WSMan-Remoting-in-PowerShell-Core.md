# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="42ea7-101">WS-Management-fjärrkommunikation (WSMan) i PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="42ea7-101">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="42ea7-102">Instruktioner för att skapa en slutpunkt för fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="42ea7-102">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="42ea7-103">Paketet för Windows PowerShell Core innehåller en WinRM plugin-program (`pwrshplugin.dll`) och ett installationsskript (`Install-PowerShellRemoting.ps1`) i `$PSHome`.</span><span class="sxs-lookup"><span data-stu-id="42ea7-103">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="42ea7-104">De här filerna aktivera PowerShell för att acceptera inkommande PowerShell fjärranslutningar när slutpunkten har angetts.</span><span class="sxs-lookup"><span data-stu-id="42ea7-104">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="42ea7-105">Syfte</span><span class="sxs-lookup"><span data-stu-id="42ea7-105">Motivation</span></span>

<span data-ttu-id="42ea7-106">En installation av PowerShell kan upprätta PowerShell-sessioner till fjärrdatorer med hjälp av `New-PSSession` och `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="42ea7-106">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="42ea7-107">Om du vill att den ska kunna acceptera inkommande PowerShell fjärranslutningar skapa användaren en slutpunkt för WinRM-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="42ea7-107">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="42ea7-108">Det här är ett explicit Anmäl scenario där användaren kör Install-PowerShellRemoting.ps1 för att skapa WinRM-slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="42ea7-108">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="42ea7-109">Installationen är en kortsiktig lösning förrän vi lägger till ytterligare funktioner för `Enable-PSRemoting` att utföra samma åtgärd.</span><span class="sxs-lookup"><span data-stu-id="42ea7-109">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="42ea7-110">Mer information finns i problemet [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="42ea7-110">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="42ea7-111">Skriptåtgärder</span><span class="sxs-lookup"><span data-stu-id="42ea7-111">Script Actions</span></span>

<span data-ttu-id="42ea7-112">Skriptet</span><span class="sxs-lookup"><span data-stu-id="42ea7-112">The script</span></span>

1. <span data-ttu-id="42ea7-113">Skapar en katalog för plugin-programmet i %windir%\System32\PowerShell</span><span class="sxs-lookup"><span data-stu-id="42ea7-113">Creates a directory for the plug-in within %windir%\System32\PowerShell</span></span>
1. <span data-ttu-id="42ea7-114">Kopierar pwrshplugin.dll till denna plats</span><span class="sxs-lookup"><span data-stu-id="42ea7-114">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="42ea7-115">Genererar en konfigurationsfil</span><span class="sxs-lookup"><span data-stu-id="42ea7-115">Generates a configuration file</span></span>
1. <span data-ttu-id="42ea7-116">Registrerar som plugin-program med WinRM</span><span class="sxs-lookup"><span data-stu-id="42ea7-116">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="42ea7-117">Registrering</span><span class="sxs-lookup"><span data-stu-id="42ea7-117">Registration</span></span>

<span data-ttu-id="42ea7-118">Skriptet måste köras inom en administratörsnivå PowerShell-session och körs i två lägen.</span><span class="sxs-lookup"><span data-stu-id="42ea7-118">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="42ea7-119">Utförs av instansen av PowerShell som registreras</span><span class="sxs-lookup"><span data-stu-id="42ea7-119">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="42ea7-120">Körs av en annan instans av PowerShell för den instans som registreras</span><span class="sxs-lookup"><span data-stu-id="42ea7-120">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="42ea7-121">Exempel:</span><span class="sxs-lookup"><span data-stu-id="42ea7-121">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="42ea7-122">**Obs:** fjärrkommunikation registrering skriptet kommer att startas om WinRM, så alla befintliga PSRP sessioner avslutas omedelbart när skriptet har körts.</span><span class="sxs-lookup"><span data-stu-id="42ea7-122">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="42ea7-123">Om du kör under en fjärrsession kommer detta avslutar anslutningen.</span><span class="sxs-lookup"><span data-stu-id="42ea7-123">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="42ea7-124">Hur du ansluter till ny slutpunkt</span><span class="sxs-lookup"><span data-stu-id="42ea7-124">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="42ea7-125">Skapa en PowerShell-session till den nya PowerShell-slutpunkten genom att ange `-ConfigurationName "some endpoint name"`.</span><span class="sxs-lookup"><span data-stu-id="42ea7-125">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="42ea7-126">Om du vill ansluta till PowerShell-instans från exemplet ovan, använder du antingen:</span><span class="sxs-lookup"><span data-stu-id="42ea7-126">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="42ea7-127">Observera att `New-PSSession` och `Enter-PSSession` anrop som inte anger `-ConfigurationName` gäller PowerShell standardslutpunkten `microsoft.powershell`.</span><span class="sxs-lookup"><span data-stu-id="42ea7-127">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>