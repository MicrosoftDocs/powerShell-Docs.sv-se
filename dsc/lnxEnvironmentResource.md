---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "DSC för Linux nxEnvironment resurs"
ms.openlocfilehash: 3d09c9642f35627e939460c9c13dfe48d14030c3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>DSC för Linux nxEnvironment resurs

Den **nxEnvironment** resurs i PowerShell önskad tillstånd Configuration (DSC) ger möjlighet till att hantera systemmiljövariabler på en Linux-nod.

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
| Se till att| Anger om du vill kontrollera om det finns variabeln. Ange egenskapen ”aktuella” så variabeln finns. Ange den till ”saknas” så variabeln inte finns. Standardvärdet är ”saknas”.| 
| Sökväg| Definierar miljövariabeln som konfigureras. Den här egenskapen **$true** om variabeln är den **sökväg** variabeln, annars inställd på **$false**. Standardvärdet är **$false**. Om variabeln som konfigureras är den **sökväg** variabel, värdet tillhandahålls via den **värdet** egenskap läggs till det befintliga värdet.| 
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** resursens configuration skriptblock som du vill köra först är **ResourceName** och dess typ är **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="additional-information"></a>Ytterligare information

* Om **sökväg** saknas eller är inställd på **$false**, miljövariabler hanteras i `/etc/environment`. Ditt program eller skript som kan kräva konfiguration till källa den `/etc/environment` filen åtkomst till hanterade miljövariablerna.
* Om **sökväg** är inställd på **$true**, miljövariabeln hanteras i filen `/etc/profile.d/DSCenvironment.sh`. Den här filen kommer att skapas om den inte finns. Om **Kontrollera** anges till ”saknas” och **sökväg** är inställd på **$true**, en befintlig miljövariabel endast tas bort från `/etc/profile.d/DSCenvironment.sh` och inte från andra filer.

## <a name="example"></a>Exempel

I följande exempel visas hur du använder den **nxEnvironment** resurs så att **TestEnvironmentVariable** finns och har värdet ”Test-värde”. Om **TestEnvironmentVariable** är inte finns, skapas den.

```
Import-DSCResource -Module nx 


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```

