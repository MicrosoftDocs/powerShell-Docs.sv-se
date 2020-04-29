---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Förbättringar i JEA (Just Enough Administration)
ms.openlocfilehash: 847ae92a6225023bcd0ee3dfe7c7058bdc356836
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71145035"
---
# <a name="improvements-to-just-enough-administration-jea"></a>Förbättringar i JEA (Just Enough Administration)

Bara tillräckligt med administration är en ny funktion i WMF 5,0 som möjliggör rollbaserad administration via PowerShell-fjärrkommunikation. Den utökar den befintliga begränsade slut punkts infrastrukturen genom att tillåta icke-administratörer att köra vissa kommandon, skript och körbara filer som administratör. På så sätt kan du minska antalet fullständiga administratörer i din miljö och förbättra säkerheten.

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>Begränsad fil kopiering till/från JEA-slutpunkter

Du kan nu fjärrkopiera filer till/från en JEA-slutpunkt och vara säker på att den anslutande användaren inte kan kopiera bara *några* filer i systemet. Detta är möjligt genom att konfigurera din PSSC-fil för att montera en användar enhet för att ansluta användare. Användar enheten är en ny PSDrive som är unik för varje användare som ansluter och behålls mellan sessioner. När `Copy-Item` används för att kopiera filer till eller från en Jea-session är det begränsat att endast tillåta åtkomst till användar enheten. Försök att kopiera filer till andra PSDrive kommer att Miss lyckas.

Använd följande nya fält för att konfigurera användar enheten i JEA-sessionens konfigurations fil:

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

Mappen som används för att återställa användar enheten skapas på`$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

Om du vill använda användar enheten och kopiera filer till/från en JEA-slutpunkt som kon figurer ATS för att exponera `-ToSession` användar `-FromSession` enheten använder `Copy-Item`du parametrarna och på.

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

Du kan sedan skriva anpassade funktioner för att bearbeta de data som lagras i användar enheten och göra dem tillgängliga för användare i din roll funktions fil.

## <a name="support-for-group-managed-service-accounts"></a>Stöd för grupphanterade tjänst konton

I vissa fall kan en uppgift som en användare behöver utföra i en JEA-session behöva komma åt resurser bortom den lokala datorn. När en JEA-session har kon figurer ATS för att använda ett virtuellt konto, kommer alla försök att komma åt sådana resurser att komma från den lokala datorns identitet, inte det virtuella kontot eller den anslutna användaren. I TP5 har vi aktiverat stöd för att köra JEA under kontexten för ett [grupphanterat tjänst konto](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), vilket gör det mycket enklare att komma åt nätverks resurser med hjälp av en domän identitet.

Om du vill konfigurera en JEA-session att köras under ett gMSA-konto, använder du följande nya nyckel i din PSSC-fil:

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> Grupphanterade tjänst konton ger inte isolering eller begränsat omfång för virtuella konton.
> Alla anslutna användare delar samma gMSA-identitet, som kan ha behörigheter i hela företaget. Var försiktig när du väljer att använda en gMSA och föredra alltid virtuella konton som är begränsade till den lokala datorn när det är möjligt.

## <a name="conditional-access-policies"></a>Principer för villkorsstyrd åtkomst

JEA är bra om du begränsar vad någon kan göra när de har anslutit till ett system för att hantera det, men vad du vill begränsa *när* någon kan använda Jea? Vi har lagt till konfigurations alternativen i sessionens konfigurationsfiler (. PSSC) så att du kan ange säkerhets grupper som en användare måste tillhöra för att kunna upprätta en JEA-session. Detta är särskilt användbart om du har ett JIT-system (just in Time) i din miljö och vill göra det möjligt för dina användare att öka sina privilegier innan de får åtkomst till en JEA-slutpunkt med hög privilegier.

I fältet nytt *RequiredGroups* i PSSC-filen kan du ange logiken för att avgöra om en användare kan ansluta till Jea. Det består av att ange en hash (eventuellt kapslad) som använder-och-och-eller-nycklar för att skapa regler. Här följer några exempel på hur du använder det här fältet:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>Åtgärdat: virtuella konton stöds nu på Windows Server 2008 R2

I WMF 5,1 kan du nu använda virtuella konton på Windows Server 2008 R2, vilket möjliggör konsekventa konfigurationer och funktions paritet över Windows Server 2008 R2-2016. Virtuella konton är inte stödda när du använder JEA i Windows 7.