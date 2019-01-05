---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-Registerresurser
ms.openlocfilehash: e0ae1a4a27edc08c4e6ccd47786426917eb1ccb4
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048725"
---
# <a name="dsc-registry-resource"></a>DSC-Registerresurser

_Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0_

Den **registret** resursen i Windows PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera registernycklar och värden på målnoden.

## <a name="syntax"></a>Syntax

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Egenskaper

| Egenskap | Beskrivning |
| --- | --- |
| Tangent| Anger sökvägen till registernyckeln som du vill se till att ett visst tillstånd. Den här sökvägen måste innehålla hive.|
| Värdenamn| Anger namnet på registervärdet. Om du vill lägga till eller ta bort en registernyckel, anger du den här egenskapen som en tom sträng utan att ange ValueType eller ValueData. Om du vill ändra eller ta bort en registernyckel standardvärdet, anger du den här egenskapen som en tom sträng när du anger också ValueType eller ValueData.|
| Se till att| Anger om nyckeln och värdet finns. Säkerställ att de gör det genom att ange egenskapen ”aktuella”. För att säkerställa att de inte finns, ange egenskapen till ””. Standardvärdet är ”tillgänglig”.|
| Force| Om den angivna registernyckeln finns, **kraft** skrivs över med det nya värdet. Om du tar bort en registernyckel med undernycklar, det här måste vara **$true** |
| Hex| Anger om data anges i hexadecimalt format. Om anges visas värdedata DWORD/QWORD i hexadecimalt format. Gäller inte för andra typer. Standardvärdet är **$false**.|
| DependsOn| Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
| ValueData| Data för registervärdet.|
| Värdetyp| Anger vilken typ av värdet. Typerna som stöds är: Sträng (REG_SZ), Binary (REG-BINARY), Dword 32-bitars (REG_DWORD), Qword 64-bitars (REG_QWORD), multisträng (REG_MULTI_SZ), utbyggbara sträng (REG_EXPAND_SZ) |

## <a name="example"></a>Exempel

Det här exemplet ser du till att det finns en nyckel med namnet ”ExampleKey” i den **HKEY\_lokala\_datorn** hive.

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

> [!NOTE]
> Ändra en registerinställning i den `HKEY\CURRENT\USER` hive kräver att konfigurationen körs med autentiseringsuppgifterna för användaren, i stället för systemet. Du kan använda den **PsDscRunAsCredential** egenskapen att ange autentiseringsuppgifter för konfigurationen. Ett exempel finns i [kör DSC med autentiseringsuppgifterna för användaren](../../../configurations/runAsUser.md).
