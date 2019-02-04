---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Skriva en anpassad DSC-resurs med PowerShell-klasser
ms.openlocfilehash: 34356f65bcb83153e7395a16d2a4a5cf2e507332
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688317"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a>Skriva en anpassad DSC-resurs med PowerShell-klasser

> Gäller för: Windows PowerShell 5.0

Med introduktionen av PowerShell-klasser i Windows PowerShell 5.0, kan du nu ange en DSC-resurs genom att skapa en klass. Klassen definierar både schemat och implementeringen av resurs, så du behöver inte skapa en separat MOF-fil. Mappstrukturen för en MOF-baserade resurs är också enklare eftersom en **DSCResources** mappen är inte nödvändigt.

I en klassbaserade DSC resursen definieras schemat som egenskaper för klassen som kan ändras med attribut som ska ange typen av egenskap... Resursen har implementerats av **Get()**, **Set()**, och **Test()** metoder (motsvarar den **Get-TargetResource**, **Set-TargetResource**, och **Test TargetResource** funktioner i en resurs för skript.

I det här avsnittet skapar vi en enkel resurs med namnet **FileResource** som hanterar en fil i en angiven sökväg.

Mer information om DSC-resurser finns i [skapa anpassade Windows PowerShell Desired State Configuration resurser](authoringResource.md)

>**Obs:** Allmän samlingar stöds inte i MOF-baserade resurser.

## <a name="folder-structure-for-a-class-resource"></a>Mappstruktur för en resurs för klass

Skapa följande mappstruktur för att implementera en anpassad DSC-resurs med en PowerShell-klass. Klassen är definierad i **MyDscResource.psm1** och modulmanifestet har definierats i **MyDscResource.psd1**.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        MyDscResource.psm1
        MyDscResource.psd1
```

## <a name="create-the-class"></a>Skapa klassen

Du kan använda nyckelordet class för att skapa en PowerShell-klass. Om du vill ange att en klass är en DSC-resurs, använda den **DscResource()** attribut. Namnet på klassen är namnet på den DSC-resursen.

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a>Deklarera egenskaper

Schema för DSC-resurs har definierats som egenskaper i klassen. Vi deklarera tre egenskaper enligt följande.

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

Observera att egenskaperna ändras av attribut. Enligt attribut är följande:

- **DscProperty(Key)**: Egenskapen krävs. Egenskapen är en nyckel. Värdena för alla egenskaper markerats som nycklar måste kombineras för att unikt identifiera en resursinstans i en konfiguration.
- **DscProperty(Mandatory)**: Egenskapen krävs.
- **DscProperty(NotConfigurable)**: Egenskapen är skrivskyddad. Egenskaper som är markerade med det här attributet kan inte anges av en konfiguration, men fylls med den **Get()** metod när det finns.
- **DscProperty()**: Egenskapen kan konfigureras, men det är inte obligatoriskt.

Den **$Path** och **$SourcePath** egenskaper är båda strängar. Den **$CreationTime** är en [DateTime](/dotnet/api/system.datetime) egenskapen. Den **$Ensure** egenskapen är en uppräkningstyp definieras enligt följande.

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a>Implementera metoderna

Den **Get()**, **Set()**, och **Test()** metoder är detsamma som det **Get-TargetResource**, **Set-TargetResource** , och **Test TargetResource** funktioner i en resurs för skript.

Den här koden innehåller också funktionen CopyFile() en hjälpfunktionen som kopierar filen från **$SourcePath** till **$Path**.

```powershell
    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### <a name="the-complete-file"></a>Den fullständiga filen

Fullständig klassfil följer.

```powershell
enum Ensure
{
    Absent
    Present
}

<#
   This resource manages the file in a specific path.
   [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
       This property is the fully qualified path to the file that is
       expected to be present or absent.

       The [DscProperty(Key)] attribute indicates the property is a
       key and its value uniquely identifies a resource instance.
       Defining this attribute also means the property is required
       and DSC will ensure a value is set before calling the resource.

       A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
       This property defines the fully qualified path to a file that will
       be placed on the system if $Ensure = Present and $Path does not
        exist.

       NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
       This property reports the file's create timestamp.

       [DscProperty(NotConfigurable)] attribute indicates the property is
       not configurable in DSC configuration.  Properties marked this way
       are populated by the Get() method to report additional details
       about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```

## <a name="create-a-manifest"></a>Skapa ett manifest

Om du vill göra en MOF-baserade resurs ska vara tillgängliga för DSC-motorn måste du inkludera en **DscResourcesToExport** instruktionen i manifestfilen som instruerar modulen att exportera resursen. Vår manifest ser ut så här:

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
}
```

## <a name="test-the-resource"></a>Testa resursen

När du har sparat den klass och manifestfiler i mappstrukturen enligt beskrivningen ovan, kan du skapa en konfiguration som använder den nya resursen. Information om hur du kör en DSC-konfiguration finns i [tillämpa konfigurationer](../pull-server/enactingConfigurations.md). Följande konfiguration ska kontrollera om filen vid `c:\test\test.txt` finns och, om inte, kopierar du filen från `c:\test.txt` (du bör skapa `c:\test.txt` innan du kör konfigurationen).

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

## <a name="supporting-psdscrunascredential"></a>Stöd för PsDscRunAsCredential

>**Obs:** **PsDscRunAsCredential** stöds i PowerShell 5.0 och senare.

Den **PsDscRunAsCredential** egenskapen kan användas i [DSC-konfigurationer](../configurations/configurations.md) resource förhindra om du vill ange att resursen ska köras under en angiven uppsättning autentiseringsuppgifter.
Mer information finns i [kör DSC med autentiseringsuppgifterna för användaren](../configurations/runAsUser.md).

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a>Aktivera eller inaktivera PsDscRunAsCredential för din resurs

Den **DscResource()** attributet tar en valfri parameter **RunAsCredential**.
Den här parametern antar ett av tre värden:

- `Optional` **PsDscRunAsCredential** är valfritt för konfigurationer som anropar den här resursen. Det här är standardkonfigurationen.
- `Mandatory` **PsDscRunAsCredential** måste användas för alla konfigurationer som anropar den här resursen.
- `NotSupported` Konfigurationer som anropar den här resursen kan inte använda **PsDscRunAsCredential**.
- `Default` Samma som `Optional`.

Till exempel använda följande attribut för att ange att din anpassade resursen inte stöder användning av **PsDscRunAsCredential**:

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="declaring-multiple-class-resources-in-a-module"></a>Deklarerar flera klass resurser i en modul

En modul kan definiera flera klassbaserade DSC-resurser. Du kan skapa mappstrukturen på följande sätt:

1. Definiera den första resursen i det ”<ModuleName>.psm1” fil- och efterföljande resurser under den **DSCResources** mapp.

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- SecondResource.psm1
   ```

2. Definiera alla resurser under den **DSCResources** mapp.

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- FirstResource.psm1
              SecondResource.psm1
   ```

> [!NOTE]
> I exemplen ovan lägger du till PSM1 filer under den **DSCResources** till den **NestedModules** nyckeln i PSD1-fil.

### <a name="access-the-user-context"></a>Komma åt användarkontexten

Du kan använda automatiska variabeln för att komma åt användarkontext från inom en anpassad resurs `$global:PsDscContext`.

Följande kod skulle till exempel skriva användarkontext där resursen körs till en dataström med utförliga utdata:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Se även

[Skapa anpassade Windows PowerShell Desired State Configuration-resurser](authoringResource.md)
