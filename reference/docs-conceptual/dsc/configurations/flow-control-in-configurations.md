---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Villkorssatser och slingor i konfigurationer
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736904"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a>Villkors uttryck och slingor i en konfiguration

Du kan göra [konfigurationen](configurations.md) mer dynamisk med hjälp av PowerShell Flow-Control-nyckelord. Den här artikeln visar hur du kan använda villkorliga uttryck och slingor för att göra `Configuration` mer dynamisk. Genom att kombinera villkorliga uttryck och slingor med [parametrar](add-parameters-to-a-configuration.md) och [konfigurations data](configData.md) kan du öka flexibiliteten och kontrollen när du kompilerar `Configuration`.

Precis som en funktion eller ett skript block kan du använda valfri PowerShell-språkfunktion i en `Configuration`.
De instruktioner du använder utvärderas bara när du anropar `Configuration` för att kompilera en `.mof`-fil. I exemplen nedan visas scenarier för att demonstrera koncept. Villkors uttryck och slingor används oftare med parametrar och konfigurations data.

I det här exemplet hämtar **tjänst** resurs blocket det aktuella läget för en tjänst vid kompileringen för att skapa en `.mof`-fil som upprätthåller dess aktuella tillstånd.

> [!NOTE]
> Om du använder dynamiska resurs block blockeras effektiviteten i IntelliSense. PowerShell-parsern kan inte avgöra om de angivna värdena är acceptabla tills `Configuration` kompileras.

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

Dessutom kan du skapa ett **tjänst** resurs block för varje tjänst på den aktuella datorn med hjälp av en `foreach`-slinga.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
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

Du kan också skapa en `Configuration` endast för datorer som är online genom att använda en `if`-instruktion.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> De dynamiska resurs blocken i ovanstående exempel hänvisar till den aktuella datorn. I den här instansen skulle det vara den dator du redigerar `Configuration` på, inte målnoden.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Sammanfattning

Sammanfattnings vis kan du använda valfri PowerShell-språkfunktion i en `Configuration`.

Detta inkluderar sådant som:

- Anpassade objekt
- Hash
- Sträng manipulering
- Tjänst
- WMI och CIM
- ActiveDirectory-objekt
- med flera...

Alla PowerShell-koder som definieras i en `Configuration` utvärderas vid kompilering, men du kan också placera kod i skriptet som innehåller din `Configuration`. All kod utanför `Configuration` blocket körs när du importerar `Configuration`.

## <a name="see-also"></a>Se även

- [Lägga till parametrar till en konfiguration](add-parameters-to-a-configuration.md)
- [Separera konfigurations data från konfigurationer](configData.md)
