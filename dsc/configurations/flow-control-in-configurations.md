---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Villkorssatser och slingor i konfigurationer
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404769"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>Villkorssatser och slingor i konfigurationer

Du kan göra din [konfigurationer](configurations.md) mer dynamiskt med hjälp av PowerShell flödesreglering nyckelord. Den här artikeln visar hur du kan använda villkorssatser och slingor du gör dina konfigurationer mer dynamiskt. Kombinera villkorlig och slingor med [parametrar](add-parameters-to-a-configuration.md) och [konfigurationsdata](configData.md) kan du större flexibilitet och kontroll vid kompilering dina konfigurationer.

Du kan använda alla PowerShell-språket i en konfiguration för precis som en funktion eller ett skriptblock. De instruktioner som du använder utvärderas bara när du anropar din konfiguration och kompilera en ”.mof”-fil. Exemplen nedan visar grundläggande scenarier för att demonstrera begreppen. Conditions är slingor används oftare med parametrar och konfigurationsdata.

I den här enkla exemplet skickar den **Service** resource block hämtar det aktuella tillståndet för en tjänst vid kompilering att generera en ”.mof”-fil som underhåller det aktuella tillståndet.

> [!NOTE]
> Med hjälp av dynamisk resurs block kommer åsidosätter effektiviteten i Intellisense. PowerShell-parser kan inte fastställa om värdena som har angetts accepteras tills konfigurationen har kompilerats.

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

Du kan även skapa en **Service** blockera resurs för varje tjänst på den aktuella datorn med hjälp av en `foreach` loop.

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

Du kan också bara skapa konfigurationer för datorer som är online, med hjälp av en enkel `if` instruktionen.

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
> Dynamisk resursen blockerar i ovanstående exempel referensen till den aktuella datorn. I den här instansen, som är den dator som du använder konfigurationen på, inte target noden.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Sammanfattning

Sammanfattningsvis ska använda du alla PowerShell-språket i en konfiguration.

Detta inkluderar:

- Anpassade objekt
- Hash-tabeller
- Manipulering av sträng
- Fjärrkommunikation
- WMI- och CIM
- ActiveDirectory-objekt
- med mera...

Alla PowerShell-kod som definierats i en konfiguration kommer att utvärderas en kompilering, men du kan också placera kod i skriptet som innehåller din konfiguration. Någon kod utanför Configuration blocket körs när du importerar din konfiguration.

## <a name="see-also"></a>Se även

- [Lägg till parametrar till en konfiguration](add-parameters-to-a-configuration.md)
- [Separera konfigurationsdata från konfigurationer](configData.md)
