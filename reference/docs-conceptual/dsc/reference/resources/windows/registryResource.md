---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC register resurs
ms.openlocfilehash: be2f9134368784ad2d208362104ce046c49492e0
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941336"
---
# <a name="dsc-registry-resource"></a>DSC register resurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**Register** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera register nycklar och värden på en målnod.

## <a name="syntax"></a>Syntax

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Nyckel |Anger sökvägen till den register nyckel för vilken du vill säkerställa ett angivet tillstånd. Den här sökvägen måste innehålla Hive. |
|Värdets namn |Anger namnet på registervärdet. Om du vill lägga till eller ta bort en register nyckel anger du den här egenskapen som en tom sträng utan att ange **ValueType** eller **ValueData**. Om du vill ändra eller ta bort standardvärdet för en register nyckel anger du den här egenskapen som en tom sträng och även anger **ValueType** eller **ValueData**. |
|Force |Om den angivna register nyckeln **finns skrivs den** över med det nya värdet. Om du tar bort en register nyckel med under nycklar måste detta vara `$true`. |
|Hexadecimal |Anger om data ska uttryckas i hexadecimalt format. Om det här alternativet anges visas DWORD/QWORD-värdet i hexadecimalt format. Inte giltigt för andra typer. Standardvärdet är `$false`. |
|ValueData |Data för registervärdet. |
|Värdetyp |Anger typen för värdet. De typer som stöds är **: sträng** (REG_SZ), **binärt** (REG-Binary), **Dword** (32-bitars REG_DWORD), **QWORD** (64-bitars REG_QWORD), **Multistring** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ). |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. |
|Kontrol |Anger om nyckeln och värdet finns. För att se till att de gör det anger du att den här egenskapen är **tillgänglig**. För att säkerställa att de inte finns, ställer du in egenskapen på **saknas**. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

Det här exemplet ser till att en nyckel med namnet "ExampleKey" finns **i\_den\_lokala** datahive-datorns Hive.

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
> Att ändra en register inställning i `HKEY_CURRENT_USER` Hive kräver att konfigurationen körs med användarautentiseringsuppgifter, i stället för som systemet. Du kan använda egenskapen **PsDscRunAsCredential** för att ange användarautentiseringsuppgifter för konfigurationen. Ett exempel finns i [köra DSC med](../../../configurations/runAsUser.md)användarautentiseringsuppgifter.