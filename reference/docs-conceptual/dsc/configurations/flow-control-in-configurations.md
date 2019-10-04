---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Villkorssatser och slingor i konfigurationer
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942036"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>Villkorssatser och slingor i konfigurationer

Du kan göra dina [konfigurationer](configurations.md) mer dynamiska med PowerShell-flödes kontroll nyckelord. I den här artikeln visas hur du kan använda villkors satser och slingor för att göra dina konfigurationer mer dynamiska. Genom att kombinera villkorliga och slingor med [parametrar](add-parameters-to-a-configuration.md) och [konfigurations data](configData.md) kan du öka flexibiliteten och kontrollen när du kompilerar dina konfigurationer.

Precis som en funktion eller ett skript block kan du använda valfritt PowerShell-språk i en konfiguration. De instruktioner du använder utvärderas bara när du anropar konfigurationen för att kompilera en ". MOF"-fil. I exemplen nedan visas enkla scenarier för att demonstrera koncept. Villkorliger är slingor som ofta används med parametrar och konfigurations data.

I det här enkla exemplet hämtar **tjänst** resurs blocket det aktuella läget för en tjänst vid kompileringen för att generera en ". MOF"-fil som upprätthåller dess aktuella tillstånd.

> [!NOTE]
> Om du använder dynamiska resurs block blockeras effektiviteten i IntelliSense. PowerShell-parsern kan inte avgöra om de angivna värdena är acceptabla tills konfigurationen kompileras.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

Dessutom kan du skapa en **tjänst** block resurs för varje tjänst på den aktuella datorn med hjälp av en `foreach`-loop.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

Du kan också bara skapa konfigurationer för datorer som är online genom att använda ett enkelt `if`-uttryck.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> De dynamiska resurs blocken i ovanstående exempel hänvisar till den aktuella datorn. I den här instansen skulle det vara den dator du redigerar konfigurationen på, inte målnoden.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Sammanfattning

I sammanfattning kan du använda valfritt PowerShell-språk i en konfiguration.

Detta inkluderar sådant som:

- Anpassade objekt
- Hash
- Sträng manipulering
- Tjänst
- WMI och CIM
- ActiveDirectory-objekt
- med mera...

Alla PowerShell-koder som definierats i en konfiguration utvärderas som en kompileringstid, men du kan också placera kod i skriptet som innehåller konfigurationen. All kod utanför konfigurations blocket körs när du importerar konfigurationen.

## <a name="see-also"></a>Se även

- [Lägga till parametrar till en konfiguration](add-parameters-to-a-configuration.md)
- [Separera konfigurations data från konfigurationer](configData.md)
