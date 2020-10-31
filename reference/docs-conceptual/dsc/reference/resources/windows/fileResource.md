---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-filresurs
description: DSC-filresurs
ms.openlocfilehash: b62b9b80beb1f433715b32b41445dd0a8bb19d84
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142947"
---
# <a name="dsc-file-resource"></a>DSC-filresurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**Fil** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera filer och mappar på målnoden. **DestinationPath** och **SourcePath** måste båda vara tillgängliga för målnoden.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntax

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|DestinationPath |Platsen, på målnoden, du vill se **till att den** **finns** eller **saknas** . |
|Attribut |Det önskade tillstånd för attributen för mål filen eller katalogen. Giltiga värden är _Arkiv_ , _dold_ , _ReadOnly_ och _system_ . |
|Kontrollsumma |Den typ av kontroll summa som ska användas för att avgöra om två filer är identiska. Giltiga värden är: **SHA-1** , **SHA-256** , **SHA-512** , **createdDate** , **modifiedDate** . |
|Innehåll |Endast giltigt när det används med en **typ** **fil** . Anger innehållet som ska **vara** **tillgängligt** eller **saknas** i mål filen. |
|Autentiseringsuppgift |De autentiseringsuppgifter som krävs för att få åtkomst till resurser, till exempel källfiler. |
|Force |Åsidosätter åtkomst åtgärder som resulterar i ett fel (till exempel att skriva över en fil eller ta bort en katalog som inte är tom). Standardvärdet är `$false`. |
|Rekursivt |Endast giltigt när det används med **typ** **katalog** . Utför tillstånds åtgärden rekursivt till alla katalog innehåll, under kataloger och under katalog innehåll. Standardvärdet är `$false`. |
|Sök |Sökvägen som filen eller mappen ska kopieras från. |
|Typ |Typ av resurs som konfigureras. Giltiga värden är **katalog** och **fil** . Standardvärdet är **File** . |
|MatchSource |Anger om resursen ska övervakas för nya filer som har lagts till i käll katalogen efter den första kopian. Värdet `$true` anger att efter den ursprungliga kopian ska alla nya källfiler kopieras till målet. Om värdet `$false` är, cachelagrar resursen innehållet i käll katalogen och ignorerar eventuella filer som lagts till efter den ursprungliga kopian. Standardvärdet är `$false`. |

> [!WARNING]
> Om du inte anger något värde för **Credential** eller **PSRunAsCredential** använder resursen dator kontot för målnoden för att få åtkomst till **SourcePath** . När **SourcePath** är en UNC-resurs kan detta resultera i ett "åtkomst nekad"-fel. Kontrol lera att dina behörigheter har angetts, eller Använd egenskaperna **Credential** eller **PSRunAsCredential** för att ange det konto som ska användas.

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|Kontrol |Anger om filen och **innehållet** på **målet** ska finnas eller inte. Ange att den här egenskapen **finns för att se till att** filen finns. Ange det som **frånvarande** för att se till att de inte finns. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

### <a name="additional-information"></a>Ytterligare information

- Om du bara anger en **DestinationPath** , ser resursen till att sökvägen finns om den **finns eller inte** finns om den **saknas** .
- När du anger en **SourcePath** och en **DestinationPath** med ett **typ** värde för **katalog** , kopieras käll katalogen till mål Sök vägen med resursen. Egenskaperna **rekursivt** , **Force** och **MatchSource** ändrar vilken typ av kopierings åtgärd som utförs, medan **autentiseringsuppgiften** avgör vilket konto som ska användas för åtkomst till käll katalogen.
- Om du inte anger egenskapen **rekursivt** till när du `$true` kopierar en katalog kopieras inget innehåll i den befintliga katalogen. Endast den angivna katalogen kommer att kopieras.
- Om du har angett värdet **ReadOnly** för egenskapen **attribut** tillsammans med en **DestinationPath** , **Se till att** det **finns** en sökväg för att skapa den angivna sökvägen, medan **innehållet** skulle ange innehållet i filen. Inställningen för **att se till att** ingen **kommer att ignorera** egenskapen **attributs** fullständigt och ta bort alla filer på den angivna sökvägen.

## <a name="example"></a>Exempel

I följande exempel kopieras en katalog och dess under kataloger från en pull-server till en målnod med hjälp av fil resursen. Om åtgärden lyckas skriver logg resursen ett bekräftelse meddelande till händelse loggen.

Käll katalogen är en UNC-sökväg ( `\\PullServer\DemoSource` ) som delas från hämtnings servern. Egenskapen **rekursivt** säkerställer att alla under kataloger också kopieras.

> [!IMPORTANT]
> LCM på målnoden körs i kontexten för det lokala system kontot som standard. Om du vill bevilja åtkomst till **SourcePath** , ger du målnoden dator konto rätt behörigheter. Både **autentiseringsuppgiften** och **PSDSCRunAsCredential** ändrar den kontext som LCM använder för att få åtkomst till **SourcePath** . Du måste fortfarande bevilja åtkomst till det konto som ska användas för åtkomst till **SourcePath** .

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

Mer information om hur du använder **autentiseringsuppgifter** i DSC finns i [Kör som-användare](../../../configurations/runAsUser.md) eller [autentiseringsuppgifter för konfigurations data](../../../configurations/configDataCredentials.md).
