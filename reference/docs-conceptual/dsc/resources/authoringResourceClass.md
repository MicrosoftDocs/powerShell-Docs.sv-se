---
ms.date: 07/08/2020
keywords: DSC, PowerShell, konfiguration, installation
title: Skriva en anpassad DSC-resurs med PowerShell-klasser
description: Den här artikeln visar hur du skapar en enkel resurs som hanterar en fil i en angiven sökväg.
ms.openlocfilehash: 72a828795c29e10ff66f164b8871b0fea7a1e0a8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667325"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a>Skriva en anpassad DSC-resurs med PowerShell-klasser

> Gäller för: Windows PowerShell 5,0

Med introduktionen av PowerShell-klasser i Windows PowerShell 5,0 kan du nu definiera en DSC-resurs genom att skapa en klass. Klassen definierar både schemat och implementeringen av resursen, så det finns inget behov av att skapa en separat MOF-fil. Mappstrukturen för en klass baserad resurs är också enklare eftersom det inte behövs någon **DSCResources** -mapp.

I en klass-baserad DSC-resurs definieras schemat som egenskaper för klassen som kan ändras med attribut för att ange egenskaps typen. Resursen implementeras av `Get()` , `Set()` -och `Test()` -metoder (motsvarar `Get-TargetResource` funktionerna, `Set-TargetResource` och `Test-TargetResource` i en skript resurs.

I den här artikeln ska vi skapa en enkel resurs med namnet **FileResource** som hanterar en fil i en angiven sökväg.

Mer information om DSC-resurser finns i avsnittet om att [bygga anpassade konfigurations resurser för önskad tillstånds konfiguration i Windows PowerShell](authoringResource.md)

> [!Note]
> Generiska samlingar stöds inte i klassbaserade resurser.

## <a name="folder-structure-for-a-class-resource"></a>Mappstruktur för en klass resurs

Skapa följande mappstruktur om du vill implementera en anpassad DSC-resurs med en PowerShell-klass.
Klassen definieras i `MyDscResource.psm1` och modul manifestet definieras i `MyDscResource.psd1` .

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        MyDscResource.psm1
        MyDscResource.psd1
```

## <a name="create-the-class"></a>Skapa klassen

Du kan använda nyckelordet class för att skapa en PowerShell-klass. Om du vill ange att en klass är en DSC-resurs använder du- `DscResource()` attributet. Namnet på klassen är namnet på DSC-resursen.

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a>Deklarera egenskaper

DSC-resursschemat definieras som egenskaper för klassen. Vi deklarerar tre egenskaper på följande sätt.

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

Observera att egenskaperna ändras efter attribut. Innebörden av attributen är följande:

- **DscProperty (nyckel)** : egenskapen är obligatorisk. Egenskapen är en nyckel. Värdena för alla egenskaper som har marker ATS som nycklar måste kombineras för att unikt identifiera en resurs instans i en konfiguration.
- **DscProperty (obligatorisk)** : egenskapen är obligatorisk.
- **DscProperty (NotConfigurable)** : egenskapen är skrivskyddad. Egenskaper som marker ATS med det här attributet kan inte ställas in med en konfiguration, men fylls i med `Get()` metoden när de är tillgängliga.
- **DscProperty ()** : egenskapen kan konfigureras, men det är inte obligatoriskt.

`$Path`Egenskaperna och `$SourcePath` är båda strängarna. `$CreationTime`Är en [datetime](/dotnet/api/system.datetime) -egenskap. `$Ensure`Egenskapen är en uppräknings typ som definieras enligt följande.

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a>Implementera metoderna

Metoderna, och `Get()` `Set()` `Test()` är likvärdiga med `Get-TargetResource` `Set-TargetResource` funktionerna, och `Test-TargetResource` i en skript resurs.

Den här koden inkluderar även `CopyFile()` funktionen, en hjälp funktion som kopierar filen från `$SourcePath` till `$Path` .

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

Den fullständiga klass filen följer.

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

Om du vill göra en klass baserad resurs tillgänglig för DSC-motorn måste du inkludera en `DscResourcesToExport` instruktion i manifest filen som instruerar modulen att exportera resursen. Vårt manifest ser ut så här:

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

När du har sparat klass-och manifest filerna i mappstrukturen enligt beskrivningen ovan, kan du skapa en konfiguration som använder den nya resursen. Information om hur du kör en DSC-konfiguration finns i [Konfigurera konfigurationer](../pull-server/enactingConfigurations.md). Följande konfiguration kommer att kontrol lera om filen `c:\test\test.txt` finns och kopierar filen från `c:\test.txt` (du bör skapa `c:\test.txt` innan du kör konfigurationen).

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

> Lägg **PsDscRunAsCredential** stöds i PowerShell 5,0 och senare.

Du kan använda egenskapen **PsDscRunAsCredential** i resurs blocket [DSC-konfigurationer](../configurations/configurations.md) för att ange att resursen ska köras under en angiven uppsättning autentiseringsuppgifter. Mer information finns i [köra DSC med](../configurations/runAsUser.md)användarautentiseringsuppgifter.

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a>Kräv eller Tillåt inte PsDscRunAsCredential för din resurs

`DscResource()`Attributet använder en valfri parameter **RunAsCredential** . Den här parametern använder ett av tre värden:

- `Optional`**PsDscRunAsCredential** är valfritt för konfigurationer som anropar den här resursen. Detta är standardvärdet.
- `Mandatory`**PsDscRunAsCredential** måste användas för alla konfigurationer som anropar den här resursen.
- `NotSupported` Konfigurationer som anropar den här resursen kan inte använda **PsDscRunAsCredential** .
- `Default` Samma som `Optional` .

Använd till exempel följande attribut för att ange att den anpassade resursen inte stöder användning av **PsDscRunAsCredential** :

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="declaring-multiple-class-resources-in-a-module"></a>Deklarera flera klass resurser i en modul

En modul kan definiera flera klassbaserade DSC-resurser. Du kan skapa mappstrukturen på följande sätt:

1. Definiera den första resursen i `<ModuleName>.psm1` filen och efterföljande resurser under **DSCResources** -mappen.

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- SecondResource.psm1
   ```

1. Definiera alla resurser under mappen **DSCResources**

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
> I exemplen ovan lägger du till eventuella PSM1-filer under **DSCResources** till **NestedModules** -nyckeln i PSD1-filen.

### <a name="access-the-user-context"></a>Komma åt användar kontexten

Om du vill komma åt användar kontexten inifrån en anpassad resurs kan du använda den automatiska variabeln `$global:PsDscContext` .

Till exempel kan följande kod skriva användar kontexten som resursen körs till i utförlig utdataström:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Se även

[Bygg anpassade resurser för Desired Configuration för Windows PowerShell](authoringResource.md)
