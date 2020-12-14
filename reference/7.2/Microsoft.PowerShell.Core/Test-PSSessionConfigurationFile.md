---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-PSSessionConfigurationFile
ms.openlocfilehash: c6d6d305b283522215d43b7339683b1617a85804
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710861"
---
# <span data-ttu-id="cae69-102">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="cae69-102">Test-PSSessionConfigurationFile</span></span>

## <span data-ttu-id="cae69-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="cae69-103">SYNOPSIS</span></span>
<span data-ttu-id="cae69-104">Verifierar nycklar och värden i en sessions konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="cae69-104">Verifies the keys and values in a session configuration file.</span></span>

## <span data-ttu-id="cae69-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cae69-105">SYNTAX</span></span>

```
Test-PSSessionConfigurationFile [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="cae69-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cae69-106">DESCRIPTION</span></span>

<span data-ttu-id="cae69-107">Den här cmdleten verifierar att en konfigurations fil för sessionen innehåller giltiga nycklar och att värdena är av rätt typ.</span><span class="sxs-lookup"><span data-stu-id="cae69-107">This cmdlet verifies that a session configuration file contains valid keys and the values are of the correct type.</span></span> <span data-ttu-id="cae69-108">För uppräknade värden verifierar cmdleten att de angivna värdena är giltiga.</span><span class="sxs-lookup"><span data-stu-id="cae69-108">For enumerated values, the cmdlet verifies that the specified values are valid.</span></span>

<span data-ttu-id="cae69-109">Cmdleten returnerar `$True` om filen klarar alla tester och `$False` om den inte gör det.</span><span class="sxs-lookup"><span data-stu-id="cae69-109">The cmdlet returns `$True` if the file passes all tests and `$False` if it does not.</span></span> <span data-ttu-id="cae69-110">Använd **verbose** -parametern för att hitta eventuella fel.</span><span class="sxs-lookup"><span data-stu-id="cae69-110">To find any errors, use the **Verbose** parameter.</span></span>

<span data-ttu-id="cae69-111">`Test-PSSessionConfigurationFile` verifierar konfigurations filerna för sessionen, till exempel de som skapats av `New-PSSessionConfigurationFile` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="cae69-111">`Test-PSSessionConfigurationFile` verifies the session configuration files, such as those created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="cae69-112">Information om sessionsdata finns [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="cae69-112">For information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span> <span data-ttu-id="cae69-113">Information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="cae69-113">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="cae69-114">Denna cmdlet introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cae69-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="cae69-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="cae69-115">EXAMPLES</span></span>

### <span data-ttu-id="cae69-116">Exempel 1: testa en sessions konfigurations fil</span><span class="sxs-lookup"><span data-stu-id="cae69-116">Example 1: Test a session configuration file</span></span>

```powershell
Test-PSSessionConfigurationFile -Path "FullLanguage.pssc"
```

```Output
True
```

### <span data-ttu-id="cae69-117">Exempel 2: testa sessionens konfigurations fil för en sessions konfiguration</span><span class="sxs-lookup"><span data-stu-id="cae69-117">Example 2: Test the session configuration file of a session configuration</span></span>

<span data-ttu-id="cae69-118">I det här exemplet testar vi konfigurations filen som används i konfigurationen för den **begränsade** sessionen.</span><span class="sxs-lookup"><span data-stu-id="cae69-118">In this example, we test the configuration file used in the **Restricted** session configuration.</span></span>
<span data-ttu-id="cae69-119">Värdet för parametern **Path** är resultatet av `Get-PSSessionConfiguration` kommandot som hämtar konfigurationen för den **begränsade** sessionen.</span><span class="sxs-lookup"><span data-stu-id="cae69-119">The value of the **Path** parameter is the result of the `Get-PSSessionConfiguration` command that gets the **Restricted** session configuration.</span></span> <span data-ttu-id="cae69-120">Sökvägen till sessionens konfigurations fil lagras i värdet för **ConfigFilePath** -egenskapen i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="cae69-120">The path of the session configuration file is stored in the value of the **ConfigFilePath** property of the session configuration.</span></span>

```powershell
Test-PSSessionConfigurationFile -Path (Get-PSSessionConfiguration -Name Restricted).ConfigFilePath
```

### <span data-ttu-id="cae69-121">Exempel 3: testa alla konfigurationsfiler för sessioner</span><span class="sxs-lookup"><span data-stu-id="cae69-121">Example 3: Test all session configuration files</span></span>

<span data-ttu-id="cae69-122">Funktionen i det här exemplet testar alla konfigurationsfiler för sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cae69-122">The function in this example tests all session configuration files on the local computer.</span></span> <span data-ttu-id="cae69-123">Funktionen använder `Get-PSSessionConfiguration` cmdleten för att hämta alla konfigurationer av sessioner.</span><span class="sxs-lookup"><span data-stu-id="cae69-123">The function uses the `Get-PSSessionConfiguration` cmdlet to get all session configurations.</span></span> <span data-ttu-id="cae69-124">Koden inuti `ForEach-Object` slingan visar fil Sök vägen och testar var och en av sessionens konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="cae69-124">The code inside the `ForEach-Object` loop displays the file path and tests each of the session configurations.</span></span>

```powershell
function Test-AllConfigFiles
{
    Get-PSSessionConfiguration | ForEach-Object {
        if ($_.ConfigFilePath) {
            $_.ConfigFilePath
            Test-PSSessionConfigurationFile -Verbose -Path $_.ConfigFilePath
        }
    }
}
Test-AllConfigFiles
```

```Output
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Empty_6fd77bf6-e084-4372-bd8a-af3e207354d3.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
VERBOSE: The member 'AliasDefinitions' must contain the required key 'Description'. Add the require key
to the fileC:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc.
False
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RestrictedLang_b6bd9474-0a6c-4e06-8722-c2c95bb10d3e.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RRS_3fb29420-2c87-46e5-a402-e21436331efc.pssc
True
```

<span data-ttu-id="cae69-125">Egenskapen **ConfigFilePath** för en session-konfiguration innehåller sökvägen till den session konfigurations fil som används i sessionen, om det finns några.</span><span class="sxs-lookup"><span data-stu-id="cae69-125">The **ConfigFilePath** property of a session configuration contains the path of the session configuration file that is used in the session configuration, if any.</span></span>

<span data-ttu-id="cae69-126">Om värdet för egenskapen **ConfigFilePath** är ifyllt (är sant), hämtar kommandot (skriver ut) värdet för egenskapen **ConfigFilePath** .</span><span class="sxs-lookup"><span data-stu-id="cae69-126">If the value of the **ConfigFilePath** property is populated (is true), the command gets (prints) the **ConfigFilePath** property value.</span></span> <span data-ttu-id="cae69-127">Sedan använder den `Test-PSSessionConfigurationFile` cmdlet: en för att testa filen i **ConfigFilePath** -värdet.</span><span class="sxs-lookup"><span data-stu-id="cae69-127">Then it uses the `Test-PSSessionConfigurationFile` cmdlet to test the file in the **ConfigFilePath** value.</span></span> <span data-ttu-id="cae69-128">Den **utförliga** parametern returnerar fil felet när det inte går att köra filen.</span><span class="sxs-lookup"><span data-stu-id="cae69-128">The **Verbose** parameter returns the file error when the file fails the test.</span></span>

## <span data-ttu-id="cae69-129">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="cae69-129">PARAMETERS</span></span>

### <span data-ttu-id="cae69-130">-Path</span><span class="sxs-lookup"><span data-stu-id="cae69-130">-Path</span></span>

<span data-ttu-id="cae69-131">Anger sökväg och fil namn för en sessions konfigurations fil (. PSSC).</span><span class="sxs-lookup"><span data-stu-id="cae69-131">Specifies the path and filename of a session configuration file (.pssc).</span></span> <span data-ttu-id="cae69-132">Om du utelämnar sökvägen är standardvärdet den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="cae69-132">If you omit the path, the default is the current folder.</span></span> <span data-ttu-id="cae69-133">Jokertecken stöds, men de måste matcha en enda fil.</span><span class="sxs-lookup"><span data-stu-id="cae69-133">Wildcard characters are supported, but they must resolve to a single file.</span></span> <span data-ttu-id="cae69-134">Du kan också skicka en sökväg till en sessions konfigurations fil `Test-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="cae69-134">You can also pipe a session configuration file path to `Test-PSSessionConfigurationFile`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="cae69-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cae69-135">CommonParameters</span></span>

<span data-ttu-id="cae69-136">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cae69-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cae69-137">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cae69-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cae69-138">INDATA</span><span class="sxs-lookup"><span data-stu-id="cae69-138">INPUTS</span></span>

### <span data-ttu-id="cae69-139">System. String</span><span class="sxs-lookup"><span data-stu-id="cae69-139">System.String</span></span>

<span data-ttu-id="cae69-140">Du kan skicka en sökväg till en fil Sök väg för sessionen `Test-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="cae69-140">You can pipe a session configuration file path to `Test-PSSessionConfigurationFile`.</span></span>

## <span data-ttu-id="cae69-141">UTDATA</span><span class="sxs-lookup"><span data-stu-id="cae69-141">OUTPUTS</span></span>

### <span data-ttu-id="cae69-142">System. Boolean</span><span class="sxs-lookup"><span data-stu-id="cae69-142">System.Boolean</span></span>

## <span data-ttu-id="cae69-143">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="cae69-143">NOTES</span></span>

<span data-ttu-id="cae69-144">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="cae69-144">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="cae69-145">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="cae69-145">RELATED LINKS</span></span>

[<span data-ttu-id="cae69-146">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="cae69-146">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="cae69-147">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="cae69-147">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="cae69-148">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="cae69-148">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="cae69-149">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="cae69-149">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="cae69-150">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="cae69-150">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="cae69-151">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="cae69-151">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="cae69-152">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="cae69-152">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="cae69-153">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="cae69-153">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="cae69-154">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="cae69-154">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="cae69-155">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="cae69-155">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="cae69-156">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="cae69-156">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="cae69-157">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="cae69-157">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
