---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-filresurs
ms.openlocfilehash: 4c6945d4cdcbc64ac6d52db563823efe8fd0247e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942456"
---
# <a name="dsc-file-resource"></a>DSC-filresurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**Fil** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera filer och mappar på målnoden. **DestinationPath** och **SourcePath** måste båda vara tillgängliga för målnoden.

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

## <a name="properties"></a>properties

|Egenskap |Beskrivning |
|---|---|
|DestinationPath |Platsen, på målnoden, du vill se **till att den** **finns** eller **saknas** . |
|Attribut |Det önskade tillstånd för attributen för mål filen eller katalogen. Giltiga värden är _Arkiv_, _dold_, _ReadOnly_och _system_. |
|Kontrollsumma |Den typ av kontroll summa som ska användas för att avgöra om två filer är identiska. Giltiga värden är: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**. |
|Innehåll |Endast giltigt när det används med en **typ** **fil**. Anger innehållet som ska **vara** **tillgängligt** eller **saknas** i mål filen. |
|Certifiering |De autentiseringsuppgifter som krävs för att få åtkomst till resurser, till exempel källfiler. |
|Force |Åsidosätter åtkomst åtgärder som resulterar i ett fel (till exempel att skriva över en fil eller ta bort en katalog som inte är tom). Standardvärdet `$false`är. |
|Rekursivt |Endast giltigt när det används med **typ** **katalog**. Utför tillstånds åtgärden rekursivt till alla under kataloger. Standardvärdet `$false`är. |
|Sök |Sökvägen som filen eller mappen ska kopieras från. |
|type |Typ av resurs som konfigureras. Giltiga värden är **katalog** och **fil**. Standardvärdet är **File**. |
|MatchSource |Anger om resursen ska övervakas för nya filer som har lagts till i käll katalogen efter den första kopian. Värdet `$true` anger att efter den ursprungliga kopian ska alla nya källfiler kopieras till målet. Om värdet `$false`är, cachelagrar resursen innehållet i käll katalogen och ignorerar eventuella filer som lagts till efter den ursprungliga kopian. Standardvärdet `$false`är. |

> [!WARNING]
> Om du inte anger något värde för **Credential** eller **PSRunAsCredential**använder resursen dator kontot för målnoden för att få åtkomst till **SourcePath**. När **SourcePath** är en UNC-resurs kan detta resultera i ett "åtkomst nekad"-fel. Kontrol lera att dina behörigheter har angetts, eller Använd egenskaperna **Credential** eller **PSRunAsCredential** för att ange det konto som ska användas.

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. |
|Kontrol |Anger om filen och **innehållet** på **målet** ska finnas eller inte. Ange att den här egenskapen **finns för att se till att** filen finns. Ange det som **frånvarande** för att se till att de inte finns. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

### <a name="additional-information"></a>Ytterligare information

- Om du bara anger en **DestinationPath**, ser resursen till att sökvägen finns om den **finns eller inte** finns om den **saknas**.
- När du anger en **SourcePath** och en **DestinationPath** med ett **typ** värde för **katalog**, kopieras käll katalogen till mål Sök vägen med resursen. Egenskaperna **rekursivt**, **Force**och **MatchSource** ändrar vilken typ av kopierings åtgärd som utförs, medan **autentiseringsuppgiften** avgör vilket konto som ska användas för åtkomst till käll katalogen.
- Om du har angett värdet **ReadOnly** för egenskapen **attribut** tillsammans med en **DestinationPath**, **Se till att** det **finns** en sökväg för att skapa den angivna sökvägen, medan **innehållet** skulle ange innehållet i filen. Inställningen för **att se till att** ingen **kommer att ignorera** egenskapen **attributs** fullständigt och ta bort alla filer på den angivna sökvägen.

## <a name="example"></a>Exempel

I följande exempel kopieras en katalog och dess under kataloger från en pull-server till en målnod med hjälp av fil resursen. Om åtgärden lyckas skriver logg resursen ett bekräftelse meddelande till händelse loggen.

Käll katalogen är en UNC-sökväg (`\\PullServer\DemoSource`) som delas från hämtnings servern. Egenskapen **rekursivt** säkerställer att alla under kataloger också kopieras.

> [!IMPORTANT]
> LCM på målnoden körs i kontexten för det lokala system kontot som standard. Om du vill bevilja åtkomst till **SourcePath**, ger du målnoden dator konto rätt behörigheter. Både **autentiseringsuppgiften** och **PSDSCRunAsCredential** ändrar den kontext som LCM använder för att få åtkomst till **SourcePath**. Du måste fortfarande bevilja åtkomst till det konto som ska användas för åtkomst till **SourcePath**.

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