---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
contributor: ryanpu
title: Förbättringar av Enough Administration (jea JUST)
ms.openlocfilehash: 66cbacb78f8a365e9c8556c7c56b3c3525de7395
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055640"
---
# <a name="improvements-to-just-enough-administration-jea"></a>Förbättringar av Enough Administration (jea JUST)

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>Begränsad filkopiering till och från JEA-slutpunkter

Du kan nu via fjärranslutning kopiera filer till/från en JEA-slutpunkt och rest vara säker på att anslutande användaren inte kan kopiera bara *alla* filen på datorn. Detta är möjligt genom att konfigurera din PSSC fil om du vill montera en enheten för att ansluta användare. Användare-enheten är en ny PSDrive som är unik för varje anslutande användaren och bevaras mellan sessioner. När `Copy-Item` är används för att kopiera filer till eller från en JEA-session, den är begränsad till att enbart tillåta åtkomst till enheten. Försök att kopiera filer till andra PSDrive att misslyckas.

Om du vill konfigurera enhet för användaren i konfigurationsfilen JEA-session använder du följande nya fält:

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

Mappen för säkerhetskopiering på enheten kommer att skapas på `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

Om du vill använda enheten och kopiera filer till och från en JEA-slutpunkt som konfigurerats för att exponera enheten, använda den `-ToSession` och `-FromSession` parametrar på `Copy-Item`.

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine.
# You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

Du kan sedan skriva egna funktioner för att bearbeta data som lagras i användarens enhet och gör dem tillgängliga för användare i din roll funktionen-fil.

## <a name="support-for-group-managed-service-accounts"></a>Stöd för en hanterad tjänst konton

I vissa fall kan behöva en uppgift som en användare behöver utföra i en JEA-session att få åtkomst till resurser utanför den lokala datorn. När en JEA-session är konfigurerad för att använda ett virtuellt konto, visas alla försök att nå dessa resurser komma från den lokala datorns identitet, inte virtuellt konto eller anslutna användaren. I TP5, har vi aktiverat stöd för att köra JEA i sammanhang med en [Grupphanterat tjänstkonto](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), vilket gör det enklare att komma åt nätverksresurser med hjälp av en domänidentitet.

Du konfigurerar en JEA-session för att köra under ett gMSA-konto genom att använda följande nya nyckel i filen PSSC:

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> Grupphanterade tjänstkonton inte ge isolering eller begränsad omfattning virtuella konton.
> Varje anslutande användaren kommer att dela samma gMSA-identitet som kan ha behörigheter för hela företaget. Var försiktig när du väljer att använda ett gMSA och föredrar alltid virtuella konton som är begränsade till den lokala datorn när det är möjligt.

## <a name="conditional-access-policies"></a>Principer för villkorlig åtkomst

JEA är duktig på att begränsa vad någon kan göra när de har anslutit till ett system att hantera det, men vad händer om du även vill begränsa *när* någon kan använda JEA? Vi har lagt till konfigurationsalternativ i sessionen configuration-filer (.pssc) så att du kan ange säkerhetsgrupper som en användare måste tillhöra för att upprätta en JEA-session. Detta kan vara särskilt användbart om du har ett precis i tid JIT-system i din miljö och vill göra dina användare utöka sina privilegier innan du använder en JEA-slutpunkt med höga privilegier.

Den nya *RequiredGroups* fält i PSSC-filen kan du ange logik för att avgöra om en användare kan ansluta till JEA. Det består av att ange en hash-tabell (du kan också kapslade) som använder det ”och” och ”eller” för att skapa dina regler. Här följer några exempel på hur du kan använda det här fältet:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>Åtgärdat: Virtuella konton stöds nu på Windows Server 2008 R2

I WMF 5.1 kan du nu använda virtuella konton i Windows Server 2008 R2, aktivera konsekventa konfigurationer och funktionsparitet mellan Windows Server 2008 R2 - 2016. Virtuella konton förblir stöds inte när du använder JEA på Windows 7.