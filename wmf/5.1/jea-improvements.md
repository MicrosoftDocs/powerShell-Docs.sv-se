---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
contributor: ryanpu
title: Förbättringar av Just Enough Administration JEA)
ms.openlocfilehash: 47a58a6fae9f3a41ec527ec1f77ac1c196336669
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="improvements-to-just-enough-administration-jea"></a>Förbättringar av Just Enough Administration JEA)

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>Begränsad filkopiering till eller från JEA slutpunkter

Du kan nu via fjärranslutning kopiera filer till/från en JEA slutpunkt och resten vara säker på att den anslutande användaren inte kan kopiera bara *alla* filen på datorn.
Detta är möjligt genom att konfigurera din PSSC fil om du vill montera en enhet för användaren för att ansluta användare.
Användarens enhet är en ny PSDrive som är unik för varje anslutande användaren och kvarstår mellan sessioner.
När du kopiera objekt för att kopiera filer till eller från en JEA session, är den begränsad till att bara tillåta åtkomst till användarens enhet.
Försök att kopiera filer till andra PSDrive misslyckas.

Använd följande nya fält om du vill konfigurera enheten för användaren i konfigurationsfilen JEA session:

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

Mappen säkerhetskopiering enhetens användare kommer att skapas på `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

Om du vill använda enheten och kopiera filer till/från en JEA slutpunkt som konfigurerats för att exponera enhetens användare, Använd den `-ToSession` och `-FromSession` parametrar på Kopiera-objekt.

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

Du kan sedan skriva anpassade funktioner för att bearbeta de data som lagras i enhetens användare och göra dem tillgängliga för användare i rollen kapaciteten filen.

## <a name="support-for-group-managed-service-accounts"></a>Stöd för gruppen hanterade konton

I vissa fall kan en aktivitet som en användare behöver genomföra i en session JEA behöver åtkomst till resurser utanför den lokala datorn.
När en session JEA är konfigurerad för att använda ett virtuellt konto, visas alla försök att nå dessa resurser kan komma från den lokala datorns identitet, inte virtuellt konto eller anslutna användaren.
I TP5, finns det stöd för att köra JEA i en [Grupphanterat tjänstkonto](https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx) kontext, vilket gör det enklare att komma åt nätverksresurser med hjälp av en domän-identitet.

Om du vill konfigurera en JEA session ska köras under ett konto för gMSA använder du följande nya nyckel i filen PSSC:

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> **Obs:** Grupphanterade tjänstkonton som inte ger isolering eller begränsad omfattning virtuella konton.
> Varje anslutande användaren kommer att dela samma gMSA-identitet som kan ha behörigheter för hela företaget.
> Var försiktig när du väljer att använda ett gMSA och föredrar alltid virtuella konton som är begränsade till den lokala datorn när det är möjligt.

## <a name="conditional-access-policies"></a>Principer för villkorlig åtkomst

JEA är bra på att begränsa vad någon kan göra när de har anslutit till ett system för att hantera den, men vad händer om du även vill begränsa *när* någon kan använda JEA?
Vi har lagt till konfigurationsalternativ i sessionen configuration-filer (.pssc) så att du kan ange säkerhetsgrupper som en användare måste tillhöra för att upprätta en session JEA.
Detta kan vara särskilt användbart om du har ett precis i tid (JIT) i din miljö och vill göra användarna Windows innan du använder en hög behörighetsnivå JEA slutpunkt.

Den nya *RequiredGroups* fält i PSSC-filen kan du ange logik för att avgöra om en användare kan ansluta till JEA.
Det består av att ange en hash-tabell (du kan också kapslade) som använder den 'Och' och 'Eller' för att skapa dina regler.
Här följer några exempel på hur du använder det här fältet:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>Fast: Virtuella konton stöds nu i Windows Server 2008 R2
I WMF 5.1 är du nu kunna använda virtuella konton på Windows Server 2008 R2, aktivera konsekventa konfigurationer och funktionsparitet via Windows Server 2008 R2 - 2016.
Virtuella konton förblir stöds inte när du använder JEA i Windows 7.
