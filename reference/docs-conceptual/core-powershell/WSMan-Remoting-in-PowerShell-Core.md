# <a name="ws-management-wsman-remoting-in-powershell-core"></a>WS-Management (WSMan) fjärrkommunikation i PowerShell Core 

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instruktioner för att skapa en slutpunkt för fjärrkommunikation

Paketet för Windows PowerShell Core innehåller en WinRM plugin-program (`pwrshplugin.dll`) och ett installationsskript (`Install-PowerShellRemoting.ps1`) i `$PSHome`.
De här filerna aktivera PowerShell för att acceptera inkommande PowerShell fjärranslutningar när slutpunkten har angetts.

### <a name="motivation"></a>Syfte

En installation av PowerShell kan upprätta PowerShell-sessioner till fjärrdatorer med hjälp av `New-PSSession` och `Enter-PSSession`.
Om du vill att den ska kunna acceptera inkommande PowerShell fjärranslutningar skapa användaren en slutpunkt för WinRM-fjärrkommunikation.
Det här är ett explicit Anmäl scenario där användaren kör Install-PowerShellRemoting.ps1 för att skapa WinRM-slutpunkten.
Installationen är en kortsiktig lösning förrän vi lägger till ytterligare funktioner för `Enable-PSRemoting` att utföra samma åtgärd.
Mer information finns i problemet [#1193](https://github.com/PowerShell/PowerShell/issues/1193).

### <a name="script-actions"></a>Skriptåtgärder

Skriptet

1. Skapar en katalog för plugin-programmet i %windir%\System32\PowerShell
1. Kopierar pwrshplugin.dll till denna plats
1. Genererar en konfigurationsfil
1. Registrerar som plugin-program med WinRM

### <a name="registration"></a>Registrering

Skriptet måste köras inom en administratörsnivå PowerShell-session och körs i två lägen.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>Utförs av instansen av PowerShell som registreras

``` powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>Körs av en annan instans av PowerShell för den instans som registreras

``` powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>" -PowerShellVersion "<the powershell version tag>"
```

Exempel:

``` powershell
C:\Program Files\PowerShell\6.0.0.9\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0.9\" -PowerShellVersion "6.0.0-alpha.9"
```

**Obs:** fjärrkommunikation registrering skriptet kommer att startas om WinRM, så alla befintliga PSRP sessioner avslutas omedelbart när skriptet har körts. Om du kör under en fjärrsession kommer detta avslutar anslutningen.

## <a name="how-to-connect-to-the-new-endpoint"></a>Hur du ansluter till ny slutpunkt

Skapa en PowerShell-session till den nya PowerShell-slutpunkten genom att ange `-ConfigurationName "some endpoint name"`. Om du vill ansluta till PowerShell-instans från exemplet ovan, använder du antingen:

``` powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0-alpha.9"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0-alpha.9"
```

Observera att `New-PSSession` och `Enter-PSSession` anrop som inte anger `-ConfigurationName` gäller PowerShell standardslutpunkten `microsoft.powershell`.
