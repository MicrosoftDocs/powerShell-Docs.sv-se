---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxEnvironment-resurs
ms.openlocfilehash: 763ec560faa6adaf42aef3c21c9045be95f780bc
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048855"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>DSC för Linux nxEnvironment-resurs

Den **nxEnvironment** resursen i PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera systemmiljövariabler på en Linux-nod.

## <a name="syntax"></a>Syntax

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Egenskaper

|  Egenskap |  Beskrivning |
|---|---|
| Namn| Anger namnet på den miljövariabel som du vill se till att ett visst tillstånd.|
| Värde| Värdet som tilldelas miljövariabeln.|
| Se till att| Anger om du vill kontrollera om variabeln. Ange egenskapen ”aktuella” så variabeln finns. Ange den till ”” så variabeln inte finns. Standardvärdet är ”tillgänglig”.|
| Sökväg| Definierar miljövariabeln som konfigureras. Den här egenskapen **$true** om variabeln är den **sökväg** variabeln, i annat fall väljer **$false**. Standardvärdet är **$false**. Om variabeln som konfigureras är den **sökväg** variabeln, värdet tillhandahålls via de **värdet** egenskapen kommer att läggas till det befintliga värdet.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Ytterligare information

* Om **sökväg** saknas eller är inställd på **$false**, miljövariabler hanteras i `/etc/environment`. Ditt program eller skript som kan kräva konfiguration källa den `/etc/environment` filen för att komma åt de hanterade miljövariablerna.
* Om **sökväg** är inställd på **$true**, miljövariabeln hanteras i filen `/etc/profile.d/DSCenvironment.sh`. Den här filen kommer att skapas om det inte finns. Om **Kontrollera** anges till ”saknas” och **sökväg** är inställd på **$true**, en befintlig miljövariabel endast tas bort från `/etc/profile.d/DSCenvironment.sh` och inte från andra filer.

## <a name="example"></a>Exempel

I följande exempel visas hur du använder den **nxEnvironment** resursen för att se till att **TestEnvironmentVariable** finns och har värdet ”Test-Value”. Om **TestEnvironmentVariable** är inte finns skapas den.

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```