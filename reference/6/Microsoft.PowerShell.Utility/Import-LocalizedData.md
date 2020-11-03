---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-localizeddata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-LocalizedData
ms.openlocfilehash: 08f959d38fc8ab861934f9a93004e67c649d9786
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93273633"
---
# <span data-ttu-id="a6297-103">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="a6297-103">Import-LocalizedData</span></span>

## <span data-ttu-id="a6297-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a6297-104">SYNOPSIS</span></span>
<span data-ttu-id="a6297-105">Importerar språkspecifika data till skript och funktioner baserat på den användar gränssnitts kultur som valts för operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="a6297-105">Imports language-specific data into scripts and functions based on the UI culture that is selected for the operating system.</span></span>

## <span data-ttu-id="a6297-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a6297-106">SYNTAX</span></span>

```
Import-LocalizedData [[-BindingVariable] <String>] [[-UICulture] <String>] [-BaseDirectory <String>]
 [-FileName <String>] [-SupportedCommand <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="a6297-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a6297-107">DESCRIPTION</span></span>

<span data-ttu-id="a6297-108">`Import-LocalizedData`Cmdlet: en hämtar dynamiskt strängar från en under katalog vars namn matchar gränssnittets språk uppsättning för den aktuella användaren av operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="a6297-108">The `Import-LocalizedData` cmdlet dynamically retrieves strings from a subdirectory whose name matches the UI language set for the current user of the operating system.</span></span> <span data-ttu-id="a6297-109">Det är utformat för att göra det möjligt för skript att Visa användar meddelanden i det GRÄNSSNITTs språk som valts av den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="a6297-109">It is designed to enable scripts to display user messages in the UI language selected by the current user.</span></span>

<span data-ttu-id="a6297-110">`Import-LocalizedData` importerar data från `.psd1` filer i språkspecifika under kataloger i skript katalogen och sparar dem i en lokal variabel som anges i kommandot.</span><span class="sxs-lookup"><span data-stu-id="a6297-110">`Import-LocalizedData` imports data from `.psd1` files in language-specific subdirectories of the script directory and saves them in a local variable that is specified in the command.</span></span> <span data-ttu-id="a6297-111">Cmdleten väljer under katalogen och filen baserat på värdet för den `$PSUICulture` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="a6297-111">The cmdlet selects the subdirectory and file based on the value of the `$PSUICulture` automatic variable.</span></span> <span data-ttu-id="a6297-112">När du använder den lokala variabeln i skriptet för att visa ett användar meddelande visas meddelandet i användarens GRÄNSSNITTs språk.</span><span class="sxs-lookup"><span data-stu-id="a6297-112">When you use the local variable in the script to display a user message, the message appears in the user's UI language.</span></span>

<span data-ttu-id="a6297-113">Du kan använda parametrarna för `Import-LocalizedData` för att ange en alternativ kultur, sökväg och fil namn för användar gränssnittet för att lägga till kommandon som stöds och för att utelämna det fel meddelande som visas om `.psd1` filerna inte hittas.</span><span class="sxs-lookup"><span data-stu-id="a6297-113">You can use the parameters of `Import-LocalizedData` to specify an alternate UI culture, path, and filename, to add supported commands, and to suppress the error message that appears if the `.psd1` files are not found.</span></span>

<span data-ttu-id="a6297-114">`Import-LocalizedData`Cmdleten stöder skriptet internationaliserings initiativ som introducerades i Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="a6297-114">The `Import-LocalizedData` cmdlet supports the script internationalization initiative that was introduced in Windows PowerShell 2.0.</span></span> <span data-ttu-id="a6297-115">Det här initiativet syftar till att bättre hantera användare i hela världen genom att göra det enkelt för skript att Visa användar meddelanden på användar GRÄNSSNITTs språket för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="a6297-115">This initiative aims to better serve users worldwide by making it easy for scripts to display user messages in the UI language of the current user.</span></span> <span data-ttu-id="a6297-116">Mer information om detta och om formatet för `.psd1` filerna finns [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span><span class="sxs-lookup"><span data-stu-id="a6297-116">For more information about this and about the format of the `.psd1` files, see [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span></span>

## <span data-ttu-id="a6297-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a6297-117">EXAMPLES</span></span>

### <span data-ttu-id="a6297-118">Exempel 1: Importera text strängar</span><span class="sxs-lookup"><span data-stu-id="a6297-118">Example 1: Import text strings</span></span>

<span data-ttu-id="a6297-119">I det här exemplet importeras text strängar till `$Messages` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a6297-119">This example imports text strings into the `$Messages` variable.</span></span> <span data-ttu-id="a6297-120">Standardvärdena för alla andra cmdlet-parametrar används.</span><span class="sxs-lookup"><span data-stu-id="a6297-120">It uses the default values of all other cmdlet parameters.</span></span>

```powershell
Import-LocalizedData -BindingVariable "Messages"
```

<span data-ttu-id="a6297-121">Om kommandot ingår i Archives.ps1-skriptet i `C:\Test` katalogen och värdet för den `$PsUICulture` automatiska variabeln är zh-CN `Import-LocalizedData` importeras `Archives.psd1` filen i `C:\test\zh-CN` katalogen till `$Messages` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a6297-121">If the command is included in the Archives.ps1 script in the `C:\Test` directory, and the value of the `$PsUICulture` automatic variable is zh-CN, `Import-LocalizedData` imports the `Archives.psd1` file in the `C:\test\zh-CN` directory into the `$Messages` variable.</span></span>

### <span data-ttu-id="a6297-122">Exempel 2: importera lokaliserade data strängar</span><span class="sxs-lookup"><span data-stu-id="a6297-122">Example 2: Import localized data strings</span></span>

<span data-ttu-id="a6297-123">Det här exemplet körs på kommando raden som inte är i ett skript.</span><span class="sxs-lookup"><span data-stu-id="a6297-123">This example is run at the command line not in a script.</span></span> <span data-ttu-id="a6297-124">Den hämtar lokaliserade data strängar från filen Test.psd1 och visar dem på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="a6297-124">It gets localized data strings from the Test.psd1 file and displays them at the command line.</span></span> <span data-ttu-id="a6297-125">Eftersom kommandot inte används i ett skript, krävs parametern **filename** .</span><span class="sxs-lookup"><span data-stu-id="a6297-125">Because the command is not used in a script, the **FileName** parameter is required.</span></span> <span data-ttu-id="a6297-126">Kommandot använder parametern **värdet** för att ange en-US-kultur.</span><span class="sxs-lookup"><span data-stu-id="a6297-126">The command uses the **UICulture** parameter to specify the en-US culture.</span></span>

```powershell
Import-LocalizedData -FileName "Test.psd1" -UICulture "en-US"
```

```Output
Name                           Value
----                           -----
Msg3                           "Use $_ to represent the object that is being processed."
Msg2                           "This command requires the credentials of a member of the Administrators group on the...
Msg1                           "The Name parameter is missing from the command."
```

<span data-ttu-id="a6297-127">`Import-LocalizedData` Returnerar en hash-tabell som innehåller de lokaliserade data strängarna.</span><span class="sxs-lookup"><span data-stu-id="a6297-127">`Import-LocalizedData` returns a hash table that contains the localized data strings.</span></span>

### <span data-ttu-id="a6297-128">Exempel 3: importera GRÄNSSNITTs kultur strängar</span><span class="sxs-lookup"><span data-stu-id="a6297-128">Example 3: Import UI culture strings</span></span>

```powershell
Import-LocalizedData -BindingVariable "MsgTbl" -UICulture "ar-SA" -FileName "Simple" -BaseDirectory "C:\Data\Localized"
```

<span data-ttu-id="a6297-129">Det här kommandot importerar text strängar till `$MsgTbl` variabeln för ett skript.</span><span class="sxs-lookup"><span data-stu-id="a6297-129">This command imports text strings into the `$MsgTbl` variable of a script.</span></span>

<span data-ttu-id="a6297-130">Den använder parametern **värdet** för att dirigera cmdleten för att importera data från `Simple.psd1` filen i under `ar-SA` katalogen i `C:\Data\Localized` .</span><span class="sxs-lookup"><span data-stu-id="a6297-130">It uses the **UICulture** parameter to direct the cmdlet to import data from the `Simple.psd1` file in the `ar-SA` subdirectory of `C:\Data\Localized`.</span></span>

### <span data-ttu-id="a6297-131">Exempel 4: importera lokaliserade data till ett skript</span><span class="sxs-lookup"><span data-stu-id="a6297-131">Example 4: Import localized data into a script</span></span>

<span data-ttu-id="a6297-132">Det här exemplet visar hur du använder lokaliserade data i ett enkelt skript.</span><span class="sxs-lookup"><span data-stu-id="a6297-132">This example shows how to use localized data in a simple script.</span></span>

```powershell
PS C:\> # In C:\Test\en-US\Test.psd1:

ConvertFrom-StringData @'

# English strings

Msg1 = "The Name parameter is missing from the command."
Msg2 = "This command requires the credentials of a member of the Administrators group on the computer."
Msg3 = "Use $_ to represent the object that is being processed."
'@

# In C:\Test\Test.ps1

Import-LocalizedData -BindingVariable "Messages"
Write-Host $Messages.Msg2

# In Windows PowerShell

PS C:\> .\Test.ps1

This command requires the credentials of a member of the Administrators group on the computer.
```

<span data-ttu-id="a6297-133">Den första delen av exemplet visar innehållet i `Test.psd1` filen.</span><span class="sxs-lookup"><span data-stu-id="a6297-133">The first part of the example shows the contents of the `Test.psd1` file.</span></span> <span data-ttu-id="a6297-134">Det innehåller ett `ConvertFrom-StringData` kommando som konverterar en serie med namngivna text strängar till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="a6297-134">It contains a `ConvertFrom-StringData` command that converts a series of named text strings into a hash table.</span></span> <span data-ttu-id="a6297-135">`Test.psd1`Filen finns i under katalogen en-us i `C:\Test` katalogen som innehåller skriptet.</span><span class="sxs-lookup"><span data-stu-id="a6297-135">The `Test.psd1` file is located in the en-US subdirectory of the `C:\Test` directory that contains the script.</span></span>

<span data-ttu-id="a6297-136">Den andra delen av exemplet visar innehållet i `Test.ps1` skriptet.</span><span class="sxs-lookup"><span data-stu-id="a6297-136">The second part of the example shows the contents of the `Test.ps1` script.</span></span> <span data-ttu-id="a6297-137">Det innehåller ett `Import-LocalizedData` kommando som importerar data från den matchande `.psd1` filen till `$Messages` variabeln och ett `Write-Host` kommando som skriver ett av meddelandena i `$Messages` variabeln till värd programmet.</span><span class="sxs-lookup"><span data-stu-id="a6297-137">It contains an `Import-LocalizedData` command that imports the data from the matching `.psd1` file into the `$Messages` variable and a `Write-Host` command that writes one of the messages in the `$Messages` variable to the host program.</span></span>

<span data-ttu-id="a6297-138">Den sista delen av exemplet kör skriptet.</span><span class="sxs-lookup"><span data-stu-id="a6297-138">The last part of the example runs the script.</span></span> <span data-ttu-id="a6297-139">Utdata visar att det visar rätt användar meddelande i användar GRÄNSSNITTets språk uppsättning för den aktuella användaren av operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="a6297-139">The output shows that it displays the correct user message in the UI language set for the current user of the operating system.</span></span>

### <span data-ttu-id="a6297-140">Exempel 5: Ersätt standard text strängar i ett skript</span><span class="sxs-lookup"><span data-stu-id="a6297-140">Example 5: Replace default text strings in a script</span></span>

<span data-ttu-id="a6297-141">Det här exemplet visar hur du `Import-LocalizedData` ersätter standard text strängar som definierats i data avsnittet i ett skript.</span><span class="sxs-lookup"><span data-stu-id="a6297-141">This example shows how to use `Import-LocalizedData` to replace default text strings defined in the DATA section of a script.</span></span>

```powershell
PS C:\> # In TestScript.ps1
$UserMessages = DATA

{    ConvertFrom-StringData @'

    # English strings

        Msg1 = "Enter a name."
        Msg2 = "Enter your employee ID."
        Msg3 = "Enter your building number."
'@
}

Import-LocalizedData -BindingVariable "UserMessages"
$UserMessages.Msg1...
```

<span data-ttu-id="a6297-142">I det här exemplet innehåller DATA avsnittet i TestScript.ps1-skriptet ett `ConvertFrom-StringData` kommando som konverterar innehållet i data avsnittet till en hash-tabell och lagrar i värdet för `$UserMessages` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a6297-142">In this example, the DATA section of the TestScript.ps1 script contains a `ConvertFrom-StringData` command that converts the contents of the DATA section to a hash table and stores in the value of the `$UserMessages` variable.</span></span>

<span data-ttu-id="a6297-143">Skriptet innehåller också ett `Import-LocalizedData` kommando, som importerar en hash-tabell med översatta text strängar från filen TestScript.psd1 i den under katalog som anges av `$PsUICulture` variabelns värde.</span><span class="sxs-lookup"><span data-stu-id="a6297-143">The script also includes an `Import-LocalizedData` command, which imports a hash table of translated text strings from the TestScript.psd1 file in the subdirectory specified by the value of the `$PsUICulture` variable.</span></span> <span data-ttu-id="a6297-144">Om kommandot hittar `.psd1` filen sparas de översatta strängarna från filen i värdet för samma `$UserMessages` variabel, vilket skriver över hash-tabellen som sparats av logiken för data avsnitt.</span><span class="sxs-lookup"><span data-stu-id="a6297-144">If the command finds the `.psd1` file, it saves the translated strings from the file in the value of the same `$UserMessages` variable, overwriting the hash table saved by the DATA section logic.</span></span>

<span data-ttu-id="a6297-145">Det tredje kommandot visar det första meddelandet i `$UserMessages` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a6297-145">The third command displays the first message in the `$UserMessages` variable.</span></span>

<span data-ttu-id="a6297-146">Om `Import-LocalizedData` kommandot hittar en `.psd1` fil för `$PsUICulture` språket, innehåller värdet för `$UserMessages` variabeln de översatta text strängarna.</span><span class="sxs-lookup"><span data-stu-id="a6297-146">If the `Import-LocalizedData` command finds a `.psd1` file for the `$PsUICulture` language, the value of the `$UserMessages` variable contains the translated text strings.</span></span> <span data-ttu-id="a6297-147">Om kommandot Miss lyckas av någon anledning visar kommandot de standard text strängar som definierats i DATA avsnittet i skriptet.</span><span class="sxs-lookup"><span data-stu-id="a6297-147">If the command fails for any reason, the command displays the default text strings defined in the DATA section of the script.</span></span>

### <span data-ttu-id="a6297-148">Exempel 6: utelämna fel meddelanden om UI-kulturen inte hittas</span><span class="sxs-lookup"><span data-stu-id="a6297-148">Example 6: Suppress error messages if the UI culture is not found</span></span>

<span data-ttu-id="a6297-149">Det här exemplet visar hur du ignorerar de fel meddelanden som visas när det `Import-LocalizedData` inte går att hitta de kataloger som matchar användarens gränssnitts kultur eller inte kan hitta en `.psd1` fil för skriptet i dessa kataloger.</span><span class="sxs-lookup"><span data-stu-id="a6297-149">This example shows how to suppress the error messages that appear when `Import-LocalizedData` cannot find the directories that match the user's UI culture or cannot find a `.psd1` file for the script in those directories.</span></span>

```powershell
PS C:\> # In Day1.ps1

Import-LocalizedData -BindingVariable "Day"

# In Day2.ps1

Import-LocalizedData -BindingVariable "Day" -ErrorAction:SilentlyContinue

PS C:\> .\Day1.ps1
Import-LocalizedData : Cannot find PowerShell data file 'Day1.psd1' in directory 'C:\ps-test\fr-BE\' or any parent culture directories.
At C:\ps-test\Day1.ps1:17 char:21+ Import-LocalizedData <<<<  Day
Today is Tuesday

PS C:\> .\Day2.ps1
Today is Tuesday
```

<span data-ttu-id="a6297-150">Du kan använda den gemensamma parametern **ErrorAction** med värdet SilentlyContinue för att ignorera fel meddelandet.</span><span class="sxs-lookup"><span data-stu-id="a6297-150">You can use the **ErrorAction** common parameter with a value of SilentlyContinue to suppress the error message.</span></span> <span data-ttu-id="a6297-151">Detta är särskilt användbart när du har angett användar meddelanden på ett standard-eller återställnings språk och inget fel meddelande krävs.</span><span class="sxs-lookup"><span data-stu-id="a6297-151">This is especially useful when you have provided user messages in a default or fallback language, and no error message is needed.</span></span>

<span data-ttu-id="a6297-152">I det här exemplet jämförs två skript `Day1.ps1` och Day2.ps1, som innehåller ett `Import-LocalizedData` kommando.</span><span class="sxs-lookup"><span data-stu-id="a6297-152">This example compares two scripts, `Day1.ps1` and Day2.ps1, that include an `Import-LocalizedData` command.</span></span> <span data-ttu-id="a6297-153">Skripten är identiska, förutom att Day2 använder **ErrorAction** common-parametern med värdet `SilentlyContinue` .</span><span class="sxs-lookup"><span data-stu-id="a6297-153">The scripts are identical, except that Day2 uses the **ErrorAction** common parameter with a value of `SilentlyContinue`.</span></span>

<span data-ttu-id="a6297-154">Exempel resultatet visar resultatet av att köra båda skripten när användar gränssnitts kulturen är inställt på `fr-BE` och det inte finns några matchande filer eller kataloger för denna användar gränssnitts kultur.</span><span class="sxs-lookup"><span data-stu-id="a6297-154">The sample output shows the results of running both scripts when the UI culture is set to `fr-BE` and there are no matching files or directories for that UI culture.</span></span> <span data-ttu-id="a6297-155">`Day1.ps1` visar ett fel meddelande och engelska utdata.</span><span class="sxs-lookup"><span data-stu-id="a6297-155">`Day1.ps1` displays an error message and English output.</span></span> <span data-ttu-id="a6297-156">`Day2.ps1` visar bara de engelska utdata.</span><span class="sxs-lookup"><span data-stu-id="a6297-156">`Day2.ps1` just displays the English output.</span></span>

## <span data-ttu-id="a6297-157">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a6297-157">PARAMETERS</span></span>

### <span data-ttu-id="a6297-158">-BaseDirectory</span><span class="sxs-lookup"><span data-stu-id="a6297-158">-BaseDirectory</span></span>

<span data-ttu-id="a6297-159">Anger bas katalogen där filerna finns `.psd1` .</span><span class="sxs-lookup"><span data-stu-id="a6297-159">Specifies the base directory where the `.psd1` files are located.</span></span> <span data-ttu-id="a6297-160">Standardvärdet är den katalog där skriptet finns.</span><span class="sxs-lookup"><span data-stu-id="a6297-160">The default is the directory where the script is located.</span></span> <span data-ttu-id="a6297-161">`Import-LocalizedData` söker efter `.psd1` filen för skriptet i en språkspecifik under katalog i bas katalogen.</span><span class="sxs-lookup"><span data-stu-id="a6297-161">`Import-LocalizedData` searches for the `.psd1` file for the script in a language-specific subdirectory of the base directory.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a6297-162">-BindingVariable</span><span class="sxs-lookup"><span data-stu-id="a6297-162">-BindingVariable</span></span>

<span data-ttu-id="a6297-163">Anger den variabel som text strängarna importeras till.</span><span class="sxs-lookup"><span data-stu-id="a6297-163">Specifies the variable into which the text strings are imported.</span></span> <span data-ttu-id="a6297-164">Ange ett variabel namn utan ett dollar tecken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="a6297-164">Enter a variable name without a dollar sign (`$`).</span></span>

<span data-ttu-id="a6297-165">Den här parametern krävs i Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="a6297-165">In Windows PowerShell 2.0, this parameter is required.</span></span> <span data-ttu-id="a6297-166">Den här parametern är valfri i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a6297-166">In Windows PowerShell 3.0, this parameter is optional.</span></span> <span data-ttu-id="a6297-167">Om du utelämnar den här parametern `Import-LocalizedData` returnerar en hash-tabell för text strängarna.</span><span class="sxs-lookup"><span data-stu-id="a6297-167">If you omit this parameter, `Import-LocalizedData` returns a hash table of the text strings.</span></span> <span data-ttu-id="a6297-168">Hash-tabellen har passerat pipelinen eller visas på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="a6297-168">The hash table is passed down the pipeline or displayed at the command line.</span></span>

<span data-ttu-id="a6297-169">När `Import-LocalizedData` du använder för att ersätta standard text strängar som anges i data avsnittet i ett skript, tilldelar du data avsnittet till en variabel och anger namnet på data sektions variabeln i värdet för parametern **BindingVariable** .</span><span class="sxs-lookup"><span data-stu-id="a6297-169">When using `Import-LocalizedData` to replace default text strings specified in the DATA section of a script, assign the DATA section to a variable and enter the name of the DATA section variable in the value of the **BindingVariable** parameter.</span></span> <span data-ttu-id="a6297-170">När `Import-LocalizedData` sparar det importerade innehållet i **BindingVariable** ersätts standard text strängarna av importerade data.</span><span class="sxs-lookup"><span data-stu-id="a6297-170">Then, when `Import-LocalizedData` saves the imported content in the **BindingVariable** , the imported data will replace the default text strings.</span></span> <span data-ttu-id="a6297-171">Om du inte anger standard text strängar kan du välja ett variabel namn.</span><span class="sxs-lookup"><span data-stu-id="a6297-171">If you are not specifying default text strings, you can select any variable name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Variable

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a6297-172">-FileName</span><span class="sxs-lookup"><span data-stu-id="a6297-172">-FileName</span></span>

<span data-ttu-id="a6297-173">Anger namnet på data filen ( `.psd1)` som ska importeras.</span><span class="sxs-lookup"><span data-stu-id="a6297-173">Specifies the name of the data file (`.psd1)` to be imported.</span></span> <span data-ttu-id="a6297-174">Ange ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="a6297-174">Enter a file name.</span></span> <span data-ttu-id="a6297-175">Du kan ange ett fil namn som inte innehåller `.psd1` fil namns tillägget, eller så kan du ange fil namnet inklusive `.psd1` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="a6297-175">You can specify a file name that does not include its `.psd1` file name extension, or you can specify the file name including the `.psd1` file name extension.</span></span> <span data-ttu-id="a6297-176">Datafiler ska sparas som Unicode eller UTF-8.</span><span class="sxs-lookup"><span data-stu-id="a6297-176">Data files should be saved as Unicode or UTF-8.</span></span>

<span data-ttu-id="a6297-177">Parametern **filename** krävs när används `Import-LocalizedData` inte i ett skript.</span><span class="sxs-lookup"><span data-stu-id="a6297-177">The **FileName** parameter is required when `Import-LocalizedData` is not used in a script.</span></span>
<span data-ttu-id="a6297-178">Annars är parametern valfri och standardvärdet är bas namnet för skriptet.</span><span class="sxs-lookup"><span data-stu-id="a6297-178">Otherwise, the parameter is optional and the default value is the base name of the script.</span></span> <span data-ttu-id="a6297-179">Du kan använda den här parametern för att dirigera för `Import-LocalizedData` att söka efter en annan `.psd1` fil.</span><span class="sxs-lookup"><span data-stu-id="a6297-179">You can use this parameter to direct `Import-LocalizedData` to search for a different `.psd1` file.</span></span>

<span data-ttu-id="a6297-180">Om **fil namnet** exempelvis utelämnas och skript namnet är FindFiles.ps1, `Import-LocalizedData` söker efter data filen FindFiles.psd1.</span><span class="sxs-lookup"><span data-stu-id="a6297-180">For example, if the **FileName** is omitted and the script name is FindFiles.ps1, `Import-LocalizedData` searches for the FindFiles.psd1 data file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a6297-181">-SupportedCommand</span><span class="sxs-lookup"><span data-stu-id="a6297-181">-SupportedCommand</span></span>

<span data-ttu-id="a6297-182">Anger cmdletar och funktioner som endast genererar data.</span><span class="sxs-lookup"><span data-stu-id="a6297-182">Specifies cmdlets and functions that generate only data.</span></span>

<span data-ttu-id="a6297-183">Använd den här parametern om du vill inkludera cmdlets och funktioner som du har skrivit eller testat.</span><span class="sxs-lookup"><span data-stu-id="a6297-183">Use this parameter to include cmdlets and functions that you have written or tested.</span></span> <span data-ttu-id="a6297-184">Mer information finns i [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span><span class="sxs-lookup"><span data-stu-id="a6297-184">For more information, see [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a6297-185">– Värdet</span><span class="sxs-lookup"><span data-stu-id="a6297-185">-UICulture</span></span>

<span data-ttu-id="a6297-186">Anger en alternativ kultur för användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="a6297-186">Specifies an alternate UI culture.</span></span>
<span data-ttu-id="a6297-187">Standardinställningen är värdet för den `$PsUICulture` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="a6297-187">The default is the value of the `$PsUICulture` automatic variable.</span></span>
<span data-ttu-id="a6297-188">Ange en användar gränssnitts kultur i `<language>-<region>` formatet, till exempel, `en-US` `de-DE` eller `ar-SA` .</span><span class="sxs-lookup"><span data-stu-id="a6297-188">Enter a UI culture in `<language>-<region>` format, such as `en-US`, `de-DE`, or `ar-SA`.</span></span>

<span data-ttu-id="a6297-189">Värdet för parametern **värdet** bestämmer den språkspecifika under katalogen (i bas katalogen) från vilken `Import-LocalizedData` hämtar `.psd1` filen för skriptet.</span><span class="sxs-lookup"><span data-stu-id="a6297-189">The value of the **UICulture** parameter determines the language-specific subdirectory (within the base directory) from which `Import-LocalizedData` gets the `.psd1` file for the script.</span></span>

<span data-ttu-id="a6297-190">Cmdleten söker efter en under katalog med samma namn som värdet för parametern **värdet** eller den `$PsUICulture` automatiska variabeln, till exempel `de-DE` eller `ar-SA` .</span><span class="sxs-lookup"><span data-stu-id="a6297-190">The cmdlet searches for a subdirectory with the same name as the value of the **UICulture** parameter or the `$PsUICulture` automatic variable, such as `de-DE` or `ar-SA`.</span></span> <span data-ttu-id="a6297-191">Om det inte går att hitta katalogen, eller om katalogen inte innehåller någon `.psd1` fil för skriptet, söker den efter en under katalog med namnet på språk koden, t. ex. de eller p.a..</span><span class="sxs-lookup"><span data-stu-id="a6297-191">If it cannot find the directory, or the directory does not contain a `.psd1` file for the script, it searches for a subdirectory with the name of the language code, such as de or ar.</span></span> <span data-ttu-id="a6297-192">Om det inte går att hitta under katalogen eller `.psd1` filen, Miss lyckas kommandot och data visas på standard språket som anges i skriptet.</span><span class="sxs-lookup"><span data-stu-id="a6297-192">If it cannot find the subdirectory or `.psd1` file, the command fails and the data is displayed in the default language specified in the script.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a6297-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a6297-193">CommonParameters</span></span>

<span data-ttu-id="a6297-194">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a6297-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a6297-195">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a6297-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a6297-196">INDATA</span><span class="sxs-lookup"><span data-stu-id="a6297-196">INPUTS</span></span>

### <span data-ttu-id="a6297-197">Inget</span><span class="sxs-lookup"><span data-stu-id="a6297-197">None</span></span>

<span data-ttu-id="a6297-198">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a6297-198">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a6297-199">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a6297-199">OUTPUTS</span></span>

### <span data-ttu-id="a6297-200">System. Collections. hash</span><span class="sxs-lookup"><span data-stu-id="a6297-200">System.Collections.Hashtable</span></span>

<span data-ttu-id="a6297-201">`Import-LocalizedData` sparar hash-tabellen i variabeln som anges av värdet för parametern **BindingVariable** .</span><span class="sxs-lookup"><span data-stu-id="a6297-201">`Import-LocalizedData` saves the hash table in the variable that is specified by the value of the **BindingVariable** parameter.</span></span>

## <span data-ttu-id="a6297-202">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a6297-202">NOTES</span></span>

- <span data-ttu-id="a6297-203">`Import-LocalizedData`Lokalisera dina användar meddelanden innan du använder dem.</span><span class="sxs-lookup"><span data-stu-id="a6297-203">Before using `Import-LocalizedData`, localize your user messages.</span></span> <span data-ttu-id="a6297-204">Formatera meddelandena för varje språk (UI-kultur) i en hash-tabell med nyckel/värde-par och spara hash-tabellen i en fil med samma namn som skriptet och ett `.psd1` fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="a6297-204">Format the messages for each locale (UI culture) in a hash table of key-value pairs, and save the hash table in a file with the same name as the script and a `.psd1` file name extension.</span></span> <span data-ttu-id="a6297-205">Skapa en katalog under skript katalogen för varje GRÄNSSNITTs kultur som stöds och spara sedan `.psd1` filen för varje användar gränssnitts kultur i katalogen med kultur namnet för användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="a6297-205">Create a directory under the script directory for each supported UI culture, and then save the `.psd1` file for each UI culture in the directory with the UI culture name.</span></span>

  <span data-ttu-id="a6297-206">Du kan till exempel lokalisera dina användar meddelanden för de nationella inställningarna och formatera dem i en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="a6297-206">For example, localize your user messages for the de-DE locale and format them in a hash table.</span></span>
  <span data-ttu-id="a6297-207">Spara hash-tabellen i en `<ScriptName>.psd1` fil.</span><span class="sxs-lookup"><span data-stu-id="a6297-207">Save the hash table in a `<ScriptName>.psd1` file.</span></span> <span data-ttu-id="a6297-208">Skapa sedan en `de-DE` under katalog under skript katalogen och spara den tyska `<ScriptName\>.psd1` filen i under `de-DE` katalogen.</span><span class="sxs-lookup"><span data-stu-id="a6297-208">Then create a `de-DE` subdirectory under the script directory, and save the German `<ScriptName\>.psd1` file in the `de-DE` subdirectory.</span></span>
  <span data-ttu-id="a6297-209">Upprepa den här metoden för varje språk som du stöder.</span><span class="sxs-lookup"><span data-stu-id="a6297-209">Repeat this method for each locale that you support.</span></span>

- <span data-ttu-id="a6297-210">`Import-LocalizedData` utför en strukturerad sökning efter de lokaliserade användar meddelandena för ett skript.</span><span class="sxs-lookup"><span data-stu-id="a6297-210">`Import-LocalizedData` performs a structured search for the localized user messages for a script.</span></span>

  <span data-ttu-id="a6297-211">`Import-LocalizedData` startar sökningen i den katalog där skript filen finns (eller värdet för parametern **BaseDirectory** ).</span><span class="sxs-lookup"><span data-stu-id="a6297-211">`Import-LocalizedData` begins the search in the directory where the script file is located (or the value of the **BaseDirectory** parameter).</span></span> <span data-ttu-id="a6297-212">Den söker sedan i bas katalogen efter en under katalog med samma namn som `$PsUICulture` variabelns värde (eller värdet för parametern **värdet** ), till exempel `de-DE` eller `ar-SA` .</span><span class="sxs-lookup"><span data-stu-id="a6297-212">It then searches within the base directory for a subdirectory with the same name as the value of the `$PsUICulture` variable (or the value of the **UICulture** parameter), such as `de-DE` or `ar-SA`.</span></span> <span data-ttu-id="a6297-213">Sedan söker den i under katalogen efter en `.psd1` fil med samma namn som skriptet (eller värdet för parametern **filename** ).</span><span class="sxs-lookup"><span data-stu-id="a6297-213">Then, it searches in that subdirectory for a `.psd1` file with the same name as the script (or the value of the **FileName** parameter).</span></span>

  <span data-ttu-id="a6297-214">Om `Import-LocalizedData` det inte går att hitta en under katalog med namnet på användar gränssnitts kulturen, eller om under katalogen inte innehåller någon `.psd1` fil för skriptet, söker den efter en `.psd1` fil för skriptet i en under katalog med namnet på språk koden, t. ex. de eller p.a..</span><span class="sxs-lookup"><span data-stu-id="a6297-214">If `Import-LocalizedData` cannot find a subdirectory with the name of the UI culture, or the subdirectory does not contain a `.psd1` file for the script, it searches for a `.psd1` file for the script in a subdirectory with the name of the language code, such as de or ar.</span></span> <span data-ttu-id="a6297-215">Om det inte går att hitta under katalogen eller `.psd1` filen, Miss lyckas kommandot, data visas på standard språket i skriptet och ett fel meddelande visas som förklarar att det inte gick att importera data.</span><span class="sxs-lookup"><span data-stu-id="a6297-215">If it cannot find the subdirectory or `.psd1` file, the command fails, the data is displayed in the default language in the script, and an error message is displayed explaining that the data could not be imported.</span></span> <span data-ttu-id="a6297-216">Om du inte vill att meddelandet ska ignoreras kan du använda den gemensamma parametern **ErrorAction** med värdet SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="a6297-216">To suppress the message and fail gracefully, use the **ErrorAction** common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="a6297-217">Om `Import-LocalizedData` hittar under katalogen och `.psd1` filen importeras hash-tabellen för användar meddelanden till värdet för parametern **BindingVariable** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="a6297-217">If `Import-LocalizedData` finds the subdirectory and the `.psd1` file, it imports the hash table of user messages into the value of the **BindingVariable** parameter in the command.</span></span> <span data-ttu-id="a6297-218">När du sedan visar ett meddelande från hash-tabellen i variabeln, visas det lokaliserade meddelandet.</span><span class="sxs-lookup"><span data-stu-id="a6297-218">Then, when you display a message from the hash table in the variable, the localized message is displayed.</span></span>

  <span data-ttu-id="a6297-219">Mer information finns i [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md).</span><span class="sxs-lookup"><span data-stu-id="a6297-219">For more information, see [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md).</span></span>

## <span data-ttu-id="a6297-220">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a6297-220">RELATED LINKS</span></span>

[<span data-ttu-id="a6297-221">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="a6297-221">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="a6297-222">Importera – PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="a6297-222">Import-PowerShellDataFile</span></span>](Import-PowerShellDataFile.md)
