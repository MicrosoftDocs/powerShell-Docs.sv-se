---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-PSSessionConfigurationFile
ms.openlocfilehash: b240a66304a2721b1bae67ed2cca669f564e8f66
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264128"
---
# <span data-ttu-id="0cc65-103">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="0cc65-103">Test-PSSessionConfigurationFile</span></span>

## <span data-ttu-id="0cc65-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0cc65-104">SYNOPSIS</span></span>
<span data-ttu-id="0cc65-105">Verifierar nycklar och värden i en sessions konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="0cc65-105">Verifies the keys and values in a session configuration file.</span></span>

## <span data-ttu-id="0cc65-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0cc65-106">SYNTAX</span></span>

```
Test-PSSessionConfigurationFile [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="0cc65-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0cc65-107">DESCRIPTION</span></span>

<span data-ttu-id="0cc65-108">Den här cmdleten verifierar att en konfigurations fil för sessionen innehåller giltiga nycklar och att värdena är av rätt typ.</span><span class="sxs-lookup"><span data-stu-id="0cc65-108">This cmdlet verifies that a session configuration file contains valid keys and the values are of the correct type.</span></span> <span data-ttu-id="0cc65-109">För uppräknade värden verifierar cmdleten att de angivna värdena är giltiga.</span><span class="sxs-lookup"><span data-stu-id="0cc65-109">For enumerated values, the cmdlet verifies that the specified values are valid.</span></span>

<span data-ttu-id="0cc65-110">Cmdleten returnerar `$True` om filen klarar alla tester och `$False` om den inte gör det.</span><span class="sxs-lookup"><span data-stu-id="0cc65-110">The cmdlet returns `$True` if the file passes all tests and `$False` if it does not.</span></span> <span data-ttu-id="0cc65-111">Använd **verbose** -parametern för att hitta eventuella fel.</span><span class="sxs-lookup"><span data-stu-id="0cc65-111">To find any errors, use the **Verbose** parameter.</span></span>

<span data-ttu-id="0cc65-112">`Test-PSSessionConfigurationFile` verifierar konfigurations filerna för sessionen, till exempel de som skapats av `New-PSSessionConfigurationFile` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0cc65-112">`Test-PSSessionConfigurationFile` verifies the session configuration files, such as those created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="0cc65-113">Information om sessionsdata finns [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="0cc65-113">For information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span> <span data-ttu-id="0cc65-114">Information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="0cc65-114">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="0cc65-115">Denna cmdlet introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0cc65-115">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="0cc65-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0cc65-116">EXAMPLES</span></span>

### <span data-ttu-id="0cc65-117">Exempel 1: testa en sessions konfigurations fil</span><span class="sxs-lookup"><span data-stu-id="0cc65-117">Example 1: Test a session configuration file</span></span>

```powershell
Test-PSSessionConfigurationFile -Path "FullLanguage.pssc"
```

```Output
True
```

### <span data-ttu-id="0cc65-118">Exempel 2: testa sessionens konfigurations fil för en sessions konfiguration</span><span class="sxs-lookup"><span data-stu-id="0cc65-118">Example 2: Test the session configuration file of a session configuration</span></span>

<span data-ttu-id="0cc65-119">I det här exemplet testar vi konfigurations filen som används i konfigurationen för den **begränsade** sessionen.</span><span class="sxs-lookup"><span data-stu-id="0cc65-119">In this example, we test the configuration file used in the **Restricted** session configuration.</span></span>
<span data-ttu-id="0cc65-120">Värdet för parametern **Path** är resultatet av `Get-PSSessionConfiguration` kommandot som hämtar konfigurationen för den **begränsade** sessionen.</span><span class="sxs-lookup"><span data-stu-id="0cc65-120">The value of the **Path** parameter is the result of the `Get-PSSessionConfiguration` command that gets the **Restricted** session configuration.</span></span> <span data-ttu-id="0cc65-121">Sökvägen till sessionens konfigurations fil lagras i värdet för **ConfigFilePath** -egenskapen i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="0cc65-121">The path of the session configuration file is stored in the value of the **ConfigFilePath** property of the session configuration.</span></span>

```powershell
Test-PSSessionConfigurationFile -Path (Get-PSSessionConfiguration -Name Restricted).ConfigFilePath
```

### <span data-ttu-id="0cc65-122">Exempel 3: testa alla konfigurationsfiler för sessioner</span><span class="sxs-lookup"><span data-stu-id="0cc65-122">Example 3: Test all session configuration files</span></span>

<span data-ttu-id="0cc65-123">Funktionen i det här exemplet testar alla konfigurationsfiler för sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="0cc65-123">The function in this example tests all session configuration files on the local computer.</span></span> <span data-ttu-id="0cc65-124">Funktionen använder `Get-PSSessionConfiguration` cmdleten för att hämta alla konfigurationer av sessioner.</span><span class="sxs-lookup"><span data-stu-id="0cc65-124">The function uses the `Get-PSSessionConfiguration` cmdlet to get all session configurations.</span></span> <span data-ttu-id="0cc65-125">Koden inuti `ForEach-Object` slingan visar fil Sök vägen och testar var och en av sessionens konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="0cc65-125">The code inside the `ForEach-Object` loop displays the file path and tests each of the session configurations.</span></span>

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

<span data-ttu-id="0cc65-126">Egenskapen **ConfigFilePath** för en session-konfiguration innehåller sökvägen till den session konfigurations fil som används i sessionen, om det finns några.</span><span class="sxs-lookup"><span data-stu-id="0cc65-126">The **ConfigFilePath** property of a session configuration contains the path of the session configuration file that is used in the session configuration, if any.</span></span>

<span data-ttu-id="0cc65-127">Om värdet för egenskapen **ConfigFilePath** är ifyllt (är sant), hämtar kommandot (skriver ut) värdet för egenskapen **ConfigFilePath** .</span><span class="sxs-lookup"><span data-stu-id="0cc65-127">If the value of the **ConfigFilePath** property is populated (is true), the command gets (prints) the **ConfigFilePath** property value.</span></span> <span data-ttu-id="0cc65-128">Sedan använder den `Test-PSSessionConfigurationFile` cmdlet: en för att testa filen i **ConfigFilePath** -värdet.</span><span class="sxs-lookup"><span data-stu-id="0cc65-128">Then it uses the `Test-PSSessionConfigurationFile` cmdlet to test the file in the **ConfigFilePath** value.</span></span> <span data-ttu-id="0cc65-129">Den **utförliga** parametern returnerar fil felet när det inte går att köra filen.</span><span class="sxs-lookup"><span data-stu-id="0cc65-129">The **Verbose** parameter returns the file error when the file fails the test.</span></span>

## <span data-ttu-id="0cc65-130">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0cc65-130">PARAMETERS</span></span>

### <span data-ttu-id="0cc65-131">-Path</span><span class="sxs-lookup"><span data-stu-id="0cc65-131">-Path</span></span>

<span data-ttu-id="0cc65-132">Anger sökväg och fil namn för en sessions konfigurations fil (. PSSC).</span><span class="sxs-lookup"><span data-stu-id="0cc65-132">Specifies the path and filename of a session configuration file (.pssc).</span></span> <span data-ttu-id="0cc65-133">Om du utelämnar sökvägen är standardvärdet den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="0cc65-133">If you omit the path, the default is the current folder.</span></span> <span data-ttu-id="0cc65-134">Jokertecken stöds, men de måste matcha en enda fil.</span><span class="sxs-lookup"><span data-stu-id="0cc65-134">Wildcard characters are supported, but they must resolve to a single file.</span></span> <span data-ttu-id="0cc65-135">Du kan också skicka en sökväg till en sessions konfigurations fil `Test-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="0cc65-135">You can also pipe a session configuration file path to `Test-PSSessionConfigurationFile`.</span></span>

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

### <span data-ttu-id="0cc65-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0cc65-136">CommonParameters</span></span>

<span data-ttu-id="0cc65-137">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0cc65-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0cc65-138">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0cc65-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0cc65-139">INDATA</span><span class="sxs-lookup"><span data-stu-id="0cc65-139">INPUTS</span></span>

### <span data-ttu-id="0cc65-140">System. String</span><span class="sxs-lookup"><span data-stu-id="0cc65-140">System.String</span></span>

<span data-ttu-id="0cc65-141">Du kan skicka en sökväg till en fil Sök väg för sessionen `Test-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="0cc65-141">You can pipe a session configuration file path to `Test-PSSessionConfigurationFile`.</span></span>

## <span data-ttu-id="0cc65-142">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0cc65-142">OUTPUTS</span></span>

### <span data-ttu-id="0cc65-143">System. Boolean</span><span class="sxs-lookup"><span data-stu-id="0cc65-143">System.Boolean</span></span>

## <span data-ttu-id="0cc65-144">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0cc65-144">NOTES</span></span>

## <span data-ttu-id="0cc65-145">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0cc65-145">RELATED LINKS</span></span>

[<span data-ttu-id="0cc65-146">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0cc65-146">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="0cc65-147">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0cc65-147">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="0cc65-148">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0cc65-148">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="0cc65-149">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="0cc65-149">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="0cc65-150">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="0cc65-150">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="0cc65-151">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0cc65-151">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="0cc65-152">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0cc65-152">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="0cc65-153">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="0cc65-153">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="0cc65-154">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0cc65-154">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="0cc65-155">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="0cc65-155">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="0cc65-156">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="0cc65-156">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="0cc65-157">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="0cc65-157">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
