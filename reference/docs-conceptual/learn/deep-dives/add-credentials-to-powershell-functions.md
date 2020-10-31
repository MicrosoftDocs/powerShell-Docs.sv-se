---
title: Lägga till stöd för autentiseringsuppgifter i PowerShell-funktioner
description: Hur du lägger till parametrar för autentiseringsuppgifter i dina PowerShell-skript,-funktioner och-cmdletar.
ms.date: 10/29/2020
ms.custom: contributor-JoshDuffney
ms.openlocfilehash: fb85d47121dc106ae04742254f418e2c727f6157
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143194"
---
# <a name="add-credential-support-to-powershell-functions"></a>Lägga till stöd för autentiseringsuppgifter i PowerShell-funktioner

> [!NOTE]
> Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@joshduffney][] . Den här artikeln har redigerats för inkludering på den här webbplatsen. PowerShell-teamet tack Josh för att dela det här innehållet med oss. Ta en titt på hans blogg på [duffney.io][].

Den här artikeln visar hur du lägger till parametrar för autentiseringsuppgifter till PowerShell-funktioner och varför du vill. En parameter för autentiseringsuppgifter är att du ska kunna köra funktionen eller cmdleten som en annan användare. Den vanligaste användningen är att köra funktionen eller cmdleten som ett upphöjd användar konto.

Till exempel har cmdleten `New-ADUser` en **Credential** -parameter, som du kan ange autentiseringsuppgifter för domän administratörer för att skapa ett konto i en domän. Under förutsättning att det normala kontot som kör PowerShell-sessionen inte redan har den åtkomsten.

## <a name="creating-credential-object"></a>Skapar Credential-objekt

Objektet [PSCredential][] representerar en uppsättning säkerhets referenser, till exempel användar namn och lösen ord. Objektet kan skickas som en parameter till en funktion som körs som användar konto i objektet Credential. Det finns några sätt som du kan skapa ett Credential-objekt på. Det första sättet att skapa ett Credential-objekt är att använda PowerShell-cmdleten `Get-Credential` . När du kör utan parametrar uppmanas du att ange ett användar namn och lösen ord. Du kan också anropa cmdleten med några valfria parametrar.

Om du vill ange domän namn och användar namn i förväg kan du antingen använda parametrarna **Credential** eller **username** . När du använder **användar namns** parametern måste du också ange ett **meddelande** värde. Koden nedan visar hur du använder cmdleten. Du kan också lagra Credential-objektet i en variabel så att du kan använda autentiseringsuppgiften flera gånger. I exemplet nedan lagras Credential-objektet i variabeln `$Cred` .

```powershell
$Cred = Get-Credential
$Cred = Get-Credential -Credential domain\user
$Cred = Get-Credential -UserName domain\user -Message 'Enter Password'
```

Ibland kan du inte använda den interaktiva metoden för att skapa Credential-objekt som visas i föregående exempel. De flesta automatiserings verktyg kräver en icke-interaktiv metod. Om du vill skapa en autentiseringsuppgift utan användar interaktion skapar du en säker sträng som innehåller lösen ordet. Skicka sedan den säkra strängen och användar namnet till- `System.Management.Automation.PSCredential()` metoden.

Använd följande kommando för att skapa en säker sträng som innehåller lösen ordet:

```powershell
ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
```

Både egenskaperna för **klartext** och **Force** måste anges. Utan dessa parametrar får du en varning om att du inte ska skicka oformaterad text till en säker sträng. PowerShell returnerar denna varning eftersom lösen ordet för oformaterad text registreras i olika loggar. När du har skapat en säker sträng måste du skicka den till- `PSCredential()` metoden för att skapa Credential-objektet. I följande exempel innehåller variabeln `$password` den säkra strängen som `$Cred` innehåller objektet Credential.

```powershell
$password = ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("username", $password)
```

Nu när du vet hur du skapar Credential-objekt kan du lägga till inloggnings parametrar till dina PowerShell-funktioner.

## <a name="adding-a-credential-parameter"></a>Lägger till en Credential-parameter

Precis som med andra parametrar börjar du med att lägga till den i `param` blockeringen av din funktion.
Vi rekommenderar att du namnger parametern `$Credential` , eftersom det är det som befintliga PowerShell-cmdletar använder. Parameterns typ ska vara `[System.Management.Automation.PSCredential]` .

I följande exempel visas parameter block för en funktion som kallas `Get-Something` . Det har två parametrar: `$Name` och `$Credential` .

```powershell
function Get-Something {
    param(
        $Name,
        [System.Management.Automation.PSCredential]$Credential
    )
```

Koden i det här exemplet räcker för att ha en fungerande Credential-parameter, men det finns några saker som du kan lägga till för att göra den mer robust.

- Lägg till `[ValidateNotNull()]` attributet verifiering för att kontrol lera att värdet skickas till **autentiseringsuppgiften** . Om parametervärdet är null förhindrar det här attributet funktionen från att köras med ogiltiga autentiseringsuppgifter.

- Lägg till `[System.Management.Automation.Credential()]` . På så sätt kan du skicka in ett användar namn som en sträng och ha en interaktiv prompt för lösen ordet.

- Ange ett standardvärde för `$Credential` parametern till `[System.Management.Automation.PSCredential]::Empty` . Funktionen du kanske skickar det här `$Credential` objektet till befintliga PowerShell-cmdletar. Om du anger ett null-värde för cmdleten som anropas inuti funktionen uppstår ett fel. Om du anger ett tomt Credential-objekt undviker du det här felet.

> [!TIP]
> Vissa cmdlets som accepterar en Credential-parameter stöder inte `[System.Management.Automation.PSCredential]::Empty` som de ska. En lösning finns i avsnittet [hantera med äldre cmdlets](#dealing-with-legacy-cmdlets) .

## <a name="using-credential-parameters"></a>Använda Credential-parametrar

Följande exempel visar hur du använder Credential-parametrar. I det här exemplet visas en funktion `Set-RemoteRegistryValue` som kallas, som ligger utanför [pester-boken][]. Den här funktionen definierar Credential-parametern med hjälp av metoderna som beskrivs i föregående avsnitt. Funktionen anropar `Invoke-Command` med `$Credential` variabeln som skapats av funktionen. På så sätt kan du ändra den användare som kör `Invoke-Command` . Eftersom standardvärdet för `$Credential` är en tom autentiseringsuppgift kan funktionen köras utan att ange autentiseringsuppgifter.

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )
        $null = Invoke-Command -ComputerName $ComputerName -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } -Credential $Credential
}
```

I följande avsnitt visas olika metoder för att ange autentiseringsuppgifter för `Set-RemoteRegistryValue` .

### <a name="prompting-for-credentials"></a>Fråga efter autentiseringsuppgifter

`Get-Credential`Att använda inom parentes `()` vid körningen gör `Get-credential` att körs först. Du uppmanas att ange ett användar namn och lösen ord. Du kan använda parametrarna **Credential** eller **username** för `Get-credential` att fylla i användar namnet och domänen i förväg. I följande exempel används en teknik som kallas ihopbuntning för att skicka parametrar till `Set-RemoteRegistryValue` funktionen. Mer information om ihopbuntning finns i artikeln [about_Splatting][] .

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential (Get-Credential)
```

![Få en autentiseringsuppgift vid körning](./media/add-credentials-to-powershell-functions/GetCredAtRunTime.gif)

Användningen `(Get-Credential)` verkar vara besvärlig. Normalt uppmanas du att ange lösen ordet när du använder parametern **Credential** med bara ett användar namn. `[System.Management.Automation.Credential()]`Attributet aktiverar det här beteendet.

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential duffney
```

![Fråga efter autentiseringsuppgifter](./media/add-credentials-to-powershell-functions/GetCredsPrompt.gif)

> [!NOTE]
> Dessa exempel förutsätter att du har **webb server** funktionerna i Windows installerat för att ange registervärdet som visas. Kör `Install-WindowsFeature Web-Server` och `Install-WindowsFeature web-mgmt-tools` om det behövs.

### <a name="provide-credentials-in-a-variable"></a>Ange autentiseringsuppgifter i en variabel

Du kan också fylla i en Credential-variabel i förväg och skicka den till parametern **Credential** för `Set-RemoteRegistryValue` funktionen. Använd den här metoden med verktyg för kontinuerlig integrering/kontinuerlig distribution (CI/CD) som Jenkins, TeamCity och Octopus Deploy. Ett exempel på hur du använder Jenkins finns i blogg inlägget om att ta reda på Hodges blogg inlägg [med Jenkins och PowerShell på Windows-del 2][].

I det här exemplet används .NET-metoden för att skapa Credential-objektet och en säker sträng för att skicka lösen ordet.

```powershell
$password = ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("duffney", $password)

$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential $Cred
```

I det här exemplet skapas en säker sträng med ett lösen ord för klartext. Alla tidigare angivna CI/CD-skivor har en säker metod för att ange lösen ordet vid körning. När du använder dessa verktyg ersätter du lösen ordet för klartext med den variabel som definierats i CI/CD-verktyget som du använder.

### <a name="run-without-credentials"></a>Kör utan autentiseringsuppgifter

Eftersom `$Credential` standardvärdet är ett tomt Credential-objekt kan du köra kommandot utan autentiseringsuppgifter, som du ser i det här exemplet:

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams
```

## <a name="dealing-with-legacy-cmdlets"></a>Hantera äldre cmdlets

Alla cmdlets stöder inte Credential-objekt eller Tillåt tomma autentiseringsuppgifter. I stället vill cmdleten användar namn och lösen ord parametrar som strängar. Det finns några sätt att kringgå den här begränsningen.

### <a name="using-if-else-to-handle-empty-credentials"></a>Använda if-else för att hantera tomma autentiseringsuppgifter

I det här scenariot accepterar inte den cmdlet som du vill köra ett tomt Credential-objekt. I det här exemplet läggs parametern **Credential** till `Invoke-Command` endast om den inte är tom. Annars körs den `Invoke-Command` utan parametern **Credential** .

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

    if($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
        Invoke-Command -ComputerName:$ComputerName -Credential:$Credential  {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    } else {
        Invoke-Command -ComputerName:$ComputerName {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    }
}
```

### <a name="using-splatting-to-handle-empty-credentials"></a>Använda ihopbuntning för att hantera tomma autentiseringsuppgifter

I det här exemplet används parametern ihopbuntning för att anropa den äldre cmdleten. `$Credential`Objektet läggs villkorligt till i hash-tabellen för ihopbuntning och gör att du inte behöver upprepa `Invoke-Command` skript blocket. Mer information om ihopbuntning inuti Functions finns i [ihopbuntning-parametrarna inuti avancerade funktioner][] blogg inlägg.

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $Splat = @{
            ComputerName = $ComputerName
        }

        if ($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
            $Splat['Credential'] = $Credential
        }

        $null = Invoke-Command -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } @splat
}
```

### <a name="working-with-string-passwords"></a>Arbeta med sträng lösen ord

`Invoke-Sqlcmd`Cmdlet är ett exempel på en cmdlet som accepterar en sträng som ett lösen ord.
`Invoke-Sqlcmd` gör att du kan köra enkla SQL INSERT-, Update-och Delete-instruktioner. `Invoke-Sqlcmd` kräver ett användar namn och lösen ord i klartext i stället för ett säkrare Credential-objekt. Det här exemplet visar hur du extraherar användar namnet och lösen ordet från ett Credential-objekt.

`Get-AllSQLDatabases`Funktionen i det här exemplet anropar `Invoke-Sqlcmd` cmdleten för att fråga en SQL-Server för alla dess databaser. Funktionen definierar en **Credential** -parameter med samma attribut som användes i föregående exempel. Eftersom användar namnet och lösen ordet finns i `$Credential` variabeln kan du extrahera dessa värden för användning med `Invoke-Sqlcmd` .

Användar namnet är tillgängligt från egenskapen **username** för `$Credential` variabeln. För att få lösen ordet måste du använda- `GetNetworkCredential()` metoden för `$Credential` objektet. Värdena extraheras till variabler som läggs till i en hash-tabell som används för ihopbuntning-parametrar till `Invoke-Sqlcmd` .

```powershell
function Get-AllSQLDatabases {
    param(
        $SQLServer,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $UserName = $Credential.UserName
        $Password = $Credential.GetNetworkCredential().Password

        $splat = @{
            UserName = $UserName
            Password = $Password
            ServerInstance = 'SQLServer'
            Query = "Select * from Sys.Databases"
        }

        Invoke-Sqlcmd @splat
}

$credSplat = @{
    TypeName = 'System.Management.Automation.PSCredential'
    ArgumentList = 'duffney',('P@ssw0rd' | ConvertTo-SecureString -AsPlainText -Force)
}
$Credential= New-Object @credSplat
ConvertTo-SecureString -AsPlainText -Force)

Get-AllSQLDatabases -SQLServer SQL01 -Credential $Credential
```

## <a name="continued-learning-credential-management"></a>Hantering av fortsatt inlärning av autentiseringsuppgifter

Det kan vara svårt att skapa och lagra Credential-objekt på ett säkert sätt. Följande resurser kan hjälpa dig att underhålla PowerShell-autentiseringsuppgifter.

- [BetterCredentials][]
- [Azure Key Vault][]
- [Valv projekt][]
- [SecretManagement-modul][]

<!-- link references -->
[ursprunglig version]: https://duffney.io/addcredentialstopowershellfunctions/
[@joshduffney]: https://twitter.com/joshduffney
[duffney.io]: https://duffney.io/posts/
[BetterCredentials]: https://www.powershellgallery.com/packages/BetterCredentials/
[Azure Key Vault]: https://azure.microsoft.com/services/key-vault/
[Valv projekt]: https://www.vaultproject.io/
[Ihopbuntning-parametrar inuti avancerade funktioner]: http://duffney.io/Splatting-Parameters-Within-AdvancedFunctions
[Automatisera med Jenkins och PowerShell i Windows-del 2]: https://hodgkins.io/automating-with-jenkins-and-powershell-on-windows-part-2
[PSCredential]: /dotnet/api/system.management.automation.pscredential
[Pester-boken]: https://leanpub.com/the-pester-book
[about_Splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[SecretManagement-modul]: https://devblogs.microsoft.com/powershell/secretmanagement-and-secretstore-updates/
