---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-filresurs
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077338"
---
# <a name="dsc-file-resource"></a>DSC-filresurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

File-resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att hantera filer och mappar på målnoden. Den **DestinationPath** och **SourcePath** måste båda vara tillgängliga för målet noden.

## <a name="syntax"></a>Syntax

```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap       |Beskrivning                                                                   |Obligatorisk|Standard|
|---------------|------------------------------------------------------------------------------|--------|-------|
|Målsökväg|Plats på målnoden, som du vill se till att är `Present` eller `Absent`.|Ja|Nej|
|Attribut     |Önskat tillstånd attribut för den aktuella filen eller katalogen. Giltiga värden är **Arkiv**, **Hidden**, **ReadOnly**, och **System**.|Nej|Inga|
|Kontrollsumma      |Typen kontrollsumma ska användas för att fastställa om två filer är lika. Giltiga värden är: SHA-1, SHA-256, SHA-512, createdDate, modifieddate kunde.|Nej|Endast namnet filen eller katalogen jämförs med.|
|Innehåll       |Endast giltigt när det används med `File` typen. Anger att kontrollera att innehållet är `Present` eller `Absent` från den aktuella filen. |Nej|Inga|
|Autentiseringsuppgifter     |De autentiseringsuppgifter som krävs för att komma åt resurser, till exempel källfiler.|Nej|Datorkontot för målnoden. (*se anmärkning*)|
|Se till att         |Önskat tillstånd för målfilen eller katalogen. |Nej|**Närvarande**|
|Force          |Åsidosätter åtgärder för dataåtkomst som skulle resultera i ett fel (till exempel att skriva över en fil eller ta bort en katalog som inte är tom).|Nej|`$false`|
|Recurse        |Endast giltigt när det används med `Directory` typen. Utför tillstånd åtgärden rekursivt på alla underkataloger.|Nej|`$false`|
|DependsOn      |Anger ett beroende för angivna resurserna. Den här resursen körs bara när åtgärden har körts för alla beroende resurser. Du kan ange beroende resurser med hjälp av syntaxen `"[ResourceType]ResourceName"`. See [about_DependsOn](../../../configurations/resource-depends-on.md)|Nej|Inga|
|SourcePath     |Sökvägen som du vill kopiera filen eller mappen resursen från.|Nej|Inga|
|Typ           |Typ av resurs som håller på att konfigureras. Giltiga värden är `Directory` och `File`.|Nej|`File`|
|MatchSource    |Anger om resursen ska övervaka för nya filer som lagts till i källkatalogen efter den första kopian. Värdet `$true` anger att inga nya källfiler efter den inledande kopian ska kopieras till målet. Om inställd `$False`, resursen cachelagrar innehållet i källkatalogen och ignorerar eventuella filer som läggs till efter den första kopian.|Nej|`$false`|

> [!WARNING]
> Om du inte anger ett värde för `Credential` eller `PSRunAsCredential` (PS V.5) resursen använda datorkontot på målnoden att komma åt den `SourcePath`.  När den `SourcePath` är en UNC-resurs, detta kan resultera i ett ”åtkomst nekad”-fel. Kontrollera dina behörigheter är inställda i enlighet med detta eller Använd den `Credential` eller `PSRunAsCredential` egenskaper för att ange det konto som ska användas.

## <a name="present-vs-absent"></a>Presentera vs. Saknas

Varje DSC-resurs utför olika åtgärder baserat på värdet som du anger för den `Ensure` egenskapen. De värden som du anger för ovanstående egenskaper anger tillstånd-åtgärd utförs.

### <a name="existence"></a>Förekomst

Om du bara anger en `DestinationPath`, resursen ser till att sökvägen finns (`Present`) eller så finns inte (`Absent`).

### <a name="copy-operations"></a>Kopieringsåtgärder

När du anger en `SourcePath` och en `DestinationPath` med en `Type` värdet för **Directory**, resursbiblioteket för kopior som källa till målsökväg. Egenskaperna `Recurse`, `Force`, och `MatchSource` ändra typen av kopieringsåtgärden utförs, medan `Credential` avgör vilket konto du använder för att komma åt källkatalogen.

### <a name="limitations"></a>Begränsningar

Om du har angett ett värde av `ReadOnly` för den `Attributes` egenskapen tillsammans med en `DestinationPath`, `Ensure = "Present"` skulle skapa den angivna sökvägen, medan `Contents` skulle ange filens innehåll.  En `Absent` tillstånd-åtgärd skulle ignorera den `Attributes` egenskapen helt och hållet, och ta bort alla filer i den angivna sökvägen.

## <a name="example"></a>Exempel

I följande exempel kopierar en katalog och dess underkataloger från en pull-server till en målnod med hjälp av File-resursen. Om åtgärden lyckas Log-resurs skriver ett bekräftelsemeddelande till händelseloggen.

Källkatalogen är en UNCsökväg (`\\PullServer\DemoSource`) delas från Pull-servern. Den `Recurse` egenskapen säkerställer att alla underkataloger kopieras även.

> [!IMPORTANT]
> LCM på mål-noden körs i kontexten för kontot Lokalt system som standard. Att bevilja åtkomst till den **SourcePath**, ge den målnoden datorkonto behörighet. Den **Credential** och **PSDSCRunAsCredential** (v5) både ändra kontexten LCM-används för att komma åt den **SourcePath**. Du behöver att bevilja åtkomst till det konto som ska användas för att komma åt den **SourcePath**.

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

För mer på med **autentiseringsuppgifter** i DSC Se [kör som användare](../../../configurations/runAsUser.md) eller [Config autentiseringsuppgifter](../../../configurations/configDataCredentials.md).
