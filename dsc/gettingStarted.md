---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Komma igång med PowerShell önskad Tillståndskonfiguration"
ms.openlocfilehash: 856528f1e52eafa8b2c93b825a60376a0d64cab2
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a>Komma igång med PowerShell önskad Tillståndskonfiguration #

Den här guiden beskriver hur du börjar skapa PowerShell Desired State Configuration-dokument och koppla dem till datorer. Den förutsätter grundläggande kunskaper med PowerShell-cmdlet: ar, moduler och funktioner. 


## <a name="create-a-configuration"></a>Skapa en konfiguration ##

[**Konfigurationer** ](https://msdn.microsoft.com/en-us/powershell/dsc/configurations) är dokument som beskriver en miljö. Miljöer består av ”**noder**”, som ofta är virtuella eller fysiska datorer. 

Konfigurationer kan finnas i olika former. Det enklaste sättet att skapa en ny konfiguration är att skapa en .ps1-fil för (PowerShell-skript). Gör du genom att öppna redigeringsprogram val. PowerShell ISE är ett bra alternativ, eftersom den förstår DSC internt. Spara följande som en PS1:

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }
        
    }

}
```
## <a name="parts-of-a-configuration"></a>Delar av en konfiguration ##
**Konfigurationen** är ett nyckelord som har lagts till i PowerShell 4.0. Det innebär en särskild typ av PowerShell-funktion som används av Desired State Configuration. I det här exemplet heter funktionen myFirstConfiguration. 

Nästa rad är en import-sats, som liknar importera en modul. Den kommer att diskuteras senare.

”Noden” definierar namnet på den här konfigurationen fungerar på den dator. Även om den här konfigurationen redigeras lokalt, kan konfigurationer nå ut till fjärranslutna noder och konfigurera dem. 

Noder kan vara datornamn eller IP-adresser. Du kan ha flera noder i ett enda dokument. Med hjälp av [konfigurationsdata](https://msdn.microsoft.com/en-us/powershell/dsc/configdata), du kan också ha samma konfiguration som gäller för flera noder. I det här fallet är noden ”localhost” - vilket innebär att den lokala datorn. 

Nästa objekt är en [ **resurs**](https://msdn.microsoft.com/en-us/powershell/dsc/resources). Resurser är byggblocken i konfigurationer. Varje resurs är en modul som definierar logik för implementering av en enda aspekt för en dator. Du kan visa alla resurser på din dator genom att köra **Get-DscResource** i PowerShell. Resurser måste finnas på den lokala datorn och det importeras innan de kan användas i en konfiguration med **importera DscResource** som finns på den andra raden i den här konfigurationen. 

**Anta en konfiguration**

Om skriptet ovan sparas och kör, kommer du gav inga utdata. Detta är eftersom en konfiguration är bara en funktion och skriptet ovan har definierats funktionen men ännu inte köra den. När funktionen har definierats, måste det anropas:
```powershell
myFirstConfiguration
```

När den exekveras, configuration funktioner Validera konfigurationen är giltig. Det bör ha inga syntaxfel, resurser bör ha alla obligatoriska parametrar som definierats och alla resurser som ska importeras innan körningen.

När konfigurationen körs skapas en mapp med namnet på den konfiguration som innehåller en **. MOF-filen** för varje nod i konfigurationen. Den. MOF-filen är en standardbaserad hantering-format som används av PowerShell DSC för att kommunicera över nätverket.

Att införa konfigurationen:
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
Detta skapar ett PowerShell-jobb som når till noderna i konfigurationen och konfigurerar dem. Om du vill se resultatet av jobbet, använder du-vänta. 
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```

