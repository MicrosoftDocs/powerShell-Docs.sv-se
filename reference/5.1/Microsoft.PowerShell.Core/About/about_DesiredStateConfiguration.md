---
description: Innehåller en kort introduktion till DSC-funktionen (Desired State Configuration).
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_desiredstateconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_DesiredStateConfiguration
ms.openlocfilehash: 5d088934ffc953ad19be401bce72f6287f0fde07
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387030"
---
# <a name="about_desiredstateconfiguration"></a>about_DesiredStateConfiguration

## <a name="short-description"></a>KORT BESKRIVNING

Innehåller en kort introduktion till DSC-funktionen (Desired State Configuration).

## <a name="long-description"></a>LÅNG BESKRIVNING

DSC är en hanterings plattform i PowerShell som gör det möjligt att distribuera och hantera konfigurations data för program varu tjänster och hantera miljön där de här tjänsterna körs.

DSC tillhandahåller en uppsättning PowerShell-språktillägg, nya cmdletar och resurser som du kan använda för att ange hur du vill att program varu miljöns tillstånd ska konfigureras. Det är också ett sätt att underhålla och hantera befintliga konfigurationer.

DSC introduceras i PowerShell 4,0.

Detaljerad information om DSC finns i [PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/overview).

## <a name="developing-dsc-resources-with-classes"></a>UTVECKLA DSC-RESURSER MED KLASSER

Från och med PowerShell 5,0 kan du utveckla DSC-resurser med hjälp av klasser.
Mer information finns i [about_Classes](about_Classes.md)och [skriva en anpassad DSC-resurs med PowerShell-klasser](/powershell/scripting/dsc/resources/authoringresourceclass).

## <a name="using-dsc"></a>ANVÄNDA DSC

Om du vill använda DSC för att konfigurera din miljö måste du först definiera ett PowerShell-skript block med hjälp av nyckelordet konfiguration, följt av en identifierare, som i sin tur följs av paret klammerparenteser som avgränsar blocket. I konfigurations blocket kan du definiera Node-block som anger det önskade konfigurations läget för varje nod (dator) i miljön. Ett Node-block börjar med nyckelordet Node, följt av namnet på mål datorn, som kan vara en variabel. Efter datorns namn, kommer klammerparenteser som begränsar Node-blocket. Inuti Node-blocket kan du definiera resurs block för att konfigurera vissa resurser. Ett resurs block börjar med typ namnet för resursen följt av den identifierare som du vill ange för detta block, följt av klammerparenteserna som begränsar blocket, som du ser i följande exempel.

```powershell
Configuration MyWebConfig {
    # Parameters are optional
    param ($MachineName, $WebsiteFilePath)
    # A Configuration block can have one or more Node blocks
    Node $MachineName
    {
        # Next, specify one or more resource blocks
        # WindowsFeature is one of the resources you can use in a Node block
        # This example ensures the Web Server (IIS) role is installed
        WindowsFeature IIS
        {
            # To ensure that the role is not installed, set Ensure to "Absent"
            Ensure = "Present"
            Name = "Web-Server" # Use the Name property from Get-WindowsFeature
        }

        # You can use the File resource to create files and folders
        # "WebDirectory" is the name you want to use to refer to this instance
        File WebDirectory
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File"
            Recurse = $true
            SourcePath = $WebsiteFilePath
            DestinationPath = "C:\inetpub\wwwroot"

            # Ensure that the IIS block is successfully run first before
            # configuring this resource
            DependsOn = "[WindowsFeature]IIS"  # Use for dependencies
        }
    }
}
```

Om du vill skapa en konfiguration anropar du konfigurations blocket på samma sätt som du anropar en PowerShell-funktion, skickar in förväntade parametrar som du kan ha definierat (två i exemplet ovan). I det här fallet kan du till exempel:

```powershell
MyWebConfig -MachineName "TestMachine" -WebsiteFilePath `
  "\\filesrv\WebFiles" -OutputPath "C:\Windows\system32\temp"
# OutputPath is optional
```

Detta genererar en MOF-fil per nod på den sökväg som du anger. Dessa MOF-filer anger önskad konfiguration för varje nod. Använd sedan följande cmdlet för att parsa konfigurations-MOF-filerna, skicka varje nod till motsvarande konfiguration och tillämpar dessa konfigurationer. Observera att du inte behöver skapa en separat MOF-fil för klassbaserade DSC-resurser.

```powershell
Start-DscConfiguration -Verbose -Wait -Path "C:\Windows\system32\temp"
```

## <a name="using-dsc-to-maintain-configuration-state"></a>ANVÄNDA DSC FÖR ATT UNDERHÅLLA KONFIGURATIONS STATUS

Med DSC är konfigurationen idempotenta. Det innebär att om du använder DSC för att införa samma konfiguration mer än en gång, blir det resulterande konfigurations statusen alltid densamma. På grund av detta kan du använda samma DSC-konfiguration igen för att återställa dem till önskat tillstånd om du misstänker att alla noder i din miljö kan ha varit i det önskade konfigurations läget. Du behöver inte ändra konfigurations skriptet för att bara hantera de resurser vars tillstånd har varit i önskat tillstånd.

I följande exempel visas hur du kan kontrol lera om det faktiska konfigurations läget på en nod har inträffat från den senaste DSC-konfigurationen som har angivits på noden. I det här exemplet kontrollerar vi konfigurationen av den lokala datorn.

```powershell
$session = New-CimSession -ComputerName "localhost"
Test-DscConfiguration -CimSession $session
```

## <a name="built-in-dsc-resources"></a>INBYGGDA DSC-RESURSER

Du kan använda följande inbyggda resurser i konfigurations skripten:

|Name                  |Egenskaper                                         |
|----------------------|---------------------------------------------------|
|Fil                  |{DestinationPath, attribut, kontroll summa, innehåll...}|
|Arkiv               |{Destination, sökväg, kontroll summa, autentiseringsuppgift...}       |
|Miljö           |{Name, DependsOn, se sökväg...}                 |
|Group                 |{GroupName, Credential, DependsOn, Description...} |
|Loggas                   |{Message, DependsOn, PsDscRunAsCredential}         |
|Paket               |{Namn, sökväg, ProductId, argument...}              |
|Register              |{Key, ValueName, DependsOn, se...}             |
|Skript                |{GetScript, SetScript, TestScript, Credential...}  |
|Tjänst               |{Name, BuiltInAccount, Credential,-beroenden...}|
|Användare                  |{UserName, DependsOn, beskrivning, inaktive rad...}    |
|WaitForAll            |{Nodnamn, ResourceName, DependsOn, PsDscRunAsC...}|
|WaitForAny            |{Nodnamn, ResourceName, DependsOn, PsDscRunAsC...}|
|WaitForSome           |{NodeCount, nodnamn, ResourceName, DependsOn...}  |
|WindowsFeature        |{Name, Credential, DependsOn, se...}           |
|WindowsOptionalFeature|{Name, DependsOn, se, LogLevel...}             |
|WindowsProcess        |{Argument, sökväg, autentiseringsuppgift, DependsOn...}        |

Kör cmdleten om du vill hämta en lista över tillgängliga DSC-resurser i systemet `Get-DscResource` .

> [!NOTE]
> I PowerShell-versioner under 7,0 `Get-DscResource` hittar du inte klassbaserade DSC-resurser.

Exemplet i det här avsnittet visar hur du använder fil-och WindowsFeature-resurserna. Om du vill se alla egenskaper som du kan använda med en resurs, infogar du markören i nyckelordet resurs (till exempel fil) i konfigurations skriptet i PowerShell ISE, håller ned <kbd>CTRL</kbd>- + <kbd>blanksteg</kbd>

## <a name="find-more-resources"></a>HITTA FLER RESURSER

Du kan ladda ned, installera och lära dig mer om många andra tillgängliga DSC-resurser som har skapats av PowerShell-och DSC-användarens community, och av Microsoft. Besök [PowerShell-galleriet](https://www.powershellgallery.com/) för att söka efter och lära dig mer om tillgängliga DSC-resurser.

## <a name="see-also"></a>SE ÄVEN

[Översikt över Desired State Configuration för PowerShell](/powershell/scripting/dsc/overview/overview)

[Inbyggda PowerShell-resurser för önskad tillstånds konfiguration](/powershell/scripting/dsc/resources/resources)

[Bygg anpassade PowerShell-resurser för Desired State Configuration](/powershell/scripting/dsc/resources/authoringResource)
