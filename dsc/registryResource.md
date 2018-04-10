---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Resurs för DSC-registret
ms.openlocfilehash: fcd24b1dd729dbb0abd697a4a628dce01fdd5422
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-registry-resource"></a>Resurs för DSC-registret

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Den **registret** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att hantera registernycklar och värden på målnoden.

## <a name="syntax"></a>Syntax

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Egenskaper
|  Egenskap  |  Beskrivning   |
|---|---|
| Tangent| Anger sökvägen till registernyckeln som du vill se till att ett visst tillstånd. Den här sökvägen måste innehålla strukturen.|
| Värdenamn| Anger namnet på registervärdet. Ange den här egenskapen om du vill lägga till eller ta bort en registernyckel, en tom sträng utan att ange ValueType eller ValueData. Om du vill ändra eller ta bort en registernyckel standardvärdet, anger du den här egenskapen som en tom sträng när du anger också ValueType eller ValueData.|
| Se till att| Anger om nyckel och värde finns. Ange egenskapen ”aktuella” för att säkerställa att de gör. Ange egenskapen till ”saknas” för att säkerställa att de inte finns. Standardvärdet är ”saknas”.|
| Force| Om den angivna registernyckeln finns, __kraft__ skriver över den med det nya värdet. Om du tar bort en registernyckel med undernycklar, det måste vara __$true__|
| Hex| Anger om data ska anges i hexadecimalt format. Om anges visas värdedata DWORD/QWORD i hexadecimalt format. Gäller inte för andra typer. Standardvärdet är __$false__.|
| dependsOn| Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
| ValueData| Data för registervärdet.|
| Värdetyp| Anger vilken typ av värdet. Typerna som stöds är:
<ul><li>String (REG_SZ)</li>


<li>Binary (REG-BINARY)</li>


<li>DWORD 32-bitars (REG_DWORD)</li>


<li>Qword 64-bitars (REG_QWORD)</li>


<li>Multi-string (REG_MULTI_SZ)</li>


<li>Utbyggbara sträng (REG_EXPAND_SZ)</li></ul>

## <a name="example"></a>Exempel
Det här exemplet ser till att det finns en nyckel med namnet ”ExampleKey” i den **HKEY\_lokala\_datorn** hive.
```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

>**Obs:** ändra en registerinställning i den **HKEY\_aktuella\_användaren** hive kräver att konfigurationen körs med autentiseringsuppgifterna för användaren i stället för som system.
>Du kan använda den **PsDscRunAsCredential** att ange autentiseringsuppgifter för konfigurationen. Ett exempel finns [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md)