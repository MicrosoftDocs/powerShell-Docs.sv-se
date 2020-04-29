---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Villkorssatser och slingor i konfigurationer
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736904"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a>Villkors uttryck och slingor i en konfiguration

Du kan göra [konfigurationen](configurations.md) mer dynamisk med hjälp av PowerShell Flow-Control-nyckelord. Den här artikeln visar hur du kan använda villkors satser och slingor för att göra `Configuration` mer dynamiska. Genom att kombinera villkorliga uttryck och slingor med [parametrar](add-parameters-to-a-configuration.md) och [konfigurations data](configData.md) kan du öka flexibiliteten och `Configuration`kontrollen när du kompilerar.

Precis som en funktion eller ett skript block kan du använda valfri PowerShell-språkfunktion i en `Configuration`.
De instruktioner du använder utvärderas bara när du anropar `Configuration` för att kompilera en `.mof` fil. I exemplen nedan visas scenarier för att demonstrera koncept. Villkors uttryck och slingor används oftare med parametrar och konfigurations data.

I det här exemplet hämtar **tjänst** resurs blocket det aktuella läget för en tjänst vid kompileringen för att skapa en `.mof` fil som upprätthåller dess aktuella tillstånd.

> [!NOTE]
> Om du använder dynamiska resurs block blockeras effektiviteten i IntelliSense. PowerShell-parsern kan inte avgöra om de angivna värdena är acceptabla `Configuration` tills kompileraren kompileras.

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

Dessutom kan du skapa ett **tjänst** resurs block för varje tjänst på den aktuella datorn med en `foreach` loop.

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

Du kan också skapa en `Configuration` endast för datorer som är online med hjälp av `if` en instruktion.

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
> De dynamiska resurs blocken i ovanstående exempel hänvisar till den aktuella datorn. I den här instansen skulle det vara den dator som du redigerar `Configuration` på, inte målnoden.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Sammanfattning

Sammanfattnings vis kan du använda valfri PowerShell-språkfunktion i `Configuration`en.

Detta inkluderar sådant som:

- Anpassade objekt
- Hash
- Sträng manipulering
- Tjänst
- WMI och CIM
- ActiveDirectory-objekt
- med flera...

Alla PowerShell-koder som definieras `Configuration` i a utvärderas vid kompilering, men du kan också placera kod i skriptet som innehåller din `Configuration`. All kod utanför `Configuration` blocket körs när du importerar din `Configuration`.

## <a name="see-also"></a>Se även

- [Lägga till parametrar till en konfiguration](add-parameters-to-a-configuration.md)
- [Separera konfigurationsdata från konfigurationer](configData.md)
