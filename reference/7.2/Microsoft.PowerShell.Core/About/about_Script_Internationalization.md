---
description: Beskriver skriptets internationaliserings funktioner som gör det enkelt för skript att visa meddelanden och instruktioner till användare i användar gränssnittets språk.
Locale: en-US
ms.date: 03/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_internationalization?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Internationalization
ms.openlocfilehash: 283ea6788e76b481c912fc5672350efd2e8bafaa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710933"
---
# <a name="about-script-internationalization"></a><span data-ttu-id="92d94-103">Om skript internationalisering</span><span class="sxs-lookup"><span data-stu-id="92d94-103">About Script Internationalization</span></span>

## <a name="short-description"></a><span data-ttu-id="92d94-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="92d94-104">Short Description</span></span>
<span data-ttu-id="92d94-105">Beskriver skriptets internationaliserings funktioner som gör det enkelt för skript att visa meddelanden och instruktioner till användare i användar gränssnittets språk.</span><span class="sxs-lookup"><span data-stu-id="92d94-105">Describes the script internationalization features that make it easy for scripts to display messages and instructions to users in their user interface (UI) language.</span></span>

## <a name="long-description"></a><span data-ttu-id="92d94-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="92d94-106">Long Description</span></span>

<span data-ttu-id="92d94-107">Med PowerShell-skriptets internationella funktioner kan du bättre betjäna användare i hela världen genom att visa hjälp och användar meddelanden på användarens språk.</span><span class="sxs-lookup"><span data-stu-id="92d94-107">The PowerShell script internationalization features allow you to better serve users throughout the world by displaying help and user messages in the user's language.</span></span>

<span data-ttu-id="92d94-108">Skriptets internationaliserings funktioner frågar användar GRÄNSSNITTs kulturen för operativ systemet under körningen, importerar lämpliga översatta text strängar och visar dem för användaren.</span><span class="sxs-lookup"><span data-stu-id="92d94-108">The script internationalization features query the UI culture of the operating system during execution, import the appropriate translated text strings, and display them to the user.</span></span> <span data-ttu-id="92d94-109">Med data avsnittet kan du lagra text strängar separat från kod så att de enkelt kan identifieras och extraheras.</span><span class="sxs-lookup"><span data-stu-id="92d94-109">The Data section lets you store text strings separate from code so they are easily identified and extracted.</span></span> <span data-ttu-id="92d94-110">En ny cmdlet, `ConvertFrom-StringData` konverterar text strängar till ord listor, till exempel hash-tabeller, för att under lätta översättning.</span><span class="sxs-lookup"><span data-stu-id="92d94-110">A new cmdlet, `ConvertFrom-StringData`, converts text strings into dictionary-like hash tables to facilitate translation.</span></span>

<span data-ttu-id="92d94-111">För att stödja internationell hjälp text innehåller PowerShell följande funktioner:</span><span class="sxs-lookup"><span data-stu-id="92d94-111">To support international Help text, PowerShell includes the following features:</span></span>

- <span data-ttu-id="92d94-112">Ett data avsnitt som avgränsar text strängar från kod instruktioner.</span><span class="sxs-lookup"><span data-stu-id="92d94-112">A Data section that separates text strings from code instructions.</span></span> <span data-ttu-id="92d94-113">Mer information om data avsnittet finns [about_Data_Sections](about_Data_Sections.md).</span><span class="sxs-lookup"><span data-stu-id="92d94-113">For more information about the Data section, see [about_Data_Sections](about_Data_Sections.md).</span></span>

- <span data-ttu-id="92d94-114">Nya automatiska variabler `$PSCulture` och `$PSUICulture` .</span><span class="sxs-lookup"><span data-stu-id="92d94-114">New automatic variables, `$PSCulture` and `$PSUICulture`.</span></span> <span data-ttu-id="92d94-115">`$PSCulture` lagrar namnet på det GRÄNSSNITTs språk som används i systemet för element som datum, tid och valuta.</span><span class="sxs-lookup"><span data-stu-id="92d94-115">`$PSCulture` stores the name of the UI language used on the system for elements such as the date, time, and currency.</span></span> <span data-ttu-id="92d94-116">`$PSUICulture`Variabeln lagrar namnet på det gränssnitts språk som används i systemet för användar gränssnitts element som menyer och text strängar.</span><span class="sxs-lookup"><span data-stu-id="92d94-116">The `$PSUICulture` variable stores the name of the UI language used on the system for user interface elements such as menus and text strings.</span></span>

- <span data-ttu-id="92d94-117">En-cmdlet, `ConvertFrom-StringData` som konverterar text strängar till en ordbok, till exempel hash-tabeller, för att under lätta översättning.</span><span class="sxs-lookup"><span data-stu-id="92d94-117">A cmdlet, `ConvertFrom-StringData`, that converts text strings into dictionary-like hash tables to facilitate translation.</span></span> <span data-ttu-id="92d94-118">Mer information finns i [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData).</span><span class="sxs-lookup"><span data-stu-id="92d94-118">For more information, see [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData).</span></span>

- <span data-ttu-id="92d94-119">En ny filtyp, `.psd1` som lagrar översatta text strängar.</span><span class="sxs-lookup"><span data-stu-id="92d94-119">A new file type, `.psd1`, that stores translated text strings.</span></span> <span data-ttu-id="92d94-120">`.psd1`Filerna lagras i språkspecifika under kataloger i skript katalogen.</span><span class="sxs-lookup"><span data-stu-id="92d94-120">The `.psd1` files are stored in language-specific subdirectories of the script directory.</span></span>

- <span data-ttu-id="92d94-121">En cmdlet, `Import-LocalizedData` som importerar översatta text strängar för ett angivet språk till ett skript vid körning.</span><span class="sxs-lookup"><span data-stu-id="92d94-121">A cmdlet, `Import-LocalizedData`, that imports translated text strings for a specified language into a script at runtime.</span></span> <span data-ttu-id="92d94-122">Denna cmdlet känner igen och importerar strängar på ett språk som stöds av Windows.</span><span class="sxs-lookup"><span data-stu-id="92d94-122">This cmdlet recognizes and imports strings in any Windows-supported language.</span></span> <span data-ttu-id="92d94-123">Mer information finns i [import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData).</span><span class="sxs-lookup"><span data-stu-id="92d94-123">For more information see [Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData).</span></span>

### <a name="the-data-section-storing-default-strings"></a><span data-ttu-id="92d94-124">Data avsnittet: lagra standard strängar</span><span class="sxs-lookup"><span data-stu-id="92d94-124">The Data Section: Storing Default Strings</span></span>

<span data-ttu-id="92d94-125">Använd ett data avsnitt i skriptet för att lagra text strängarna på standard språket.</span><span class="sxs-lookup"><span data-stu-id="92d94-125">Use a Data section in the script to store the text strings in the default language.</span></span> <span data-ttu-id="92d94-126">Ordna strängarna i nyckel/värde-par i en här-sträng.</span><span class="sxs-lookup"><span data-stu-id="92d94-126">Arrange the strings in key/value pairs in a here-string.</span></span> <span data-ttu-id="92d94-127">Varje nyckel/värde-par måste finnas på en separat rad.</span><span class="sxs-lookup"><span data-stu-id="92d94-127">Each key/value pair must be on a separate line.</span></span> <span data-ttu-id="92d94-128">Om du inkluderar kommentarer måste kommentarerna finnas på separata rader.</span><span class="sxs-lookup"><span data-stu-id="92d94-128">If you include comments, the comments must be on separate lines.</span></span>

<span data-ttu-id="92d94-129">`ConvertFrom-StringData`Cmdleten konverterar nyckel/värde-par i denna-sträng till en ordbok, t. ex. hash-tabell som lagras i värdet för data avsnitts variabeln.</span><span class="sxs-lookup"><span data-stu-id="92d94-129">The `ConvertFrom-StringData` cmdlet converts the key/value pairs in the here-string into a dictionary-like hash table that is stored in the value of the Data section variable.</span></span>

<span data-ttu-id="92d94-130">I följande exempel innehåller data avsnittet i `World.ps1` skriptet English-United tillstånds uppsättning (en-US) med prompt-meddelanden för ett skript.</span><span class="sxs-lookup"><span data-stu-id="92d94-130">In the following example, the Data section of the `World.ps1` script includes the English-United States (en-US) set of prompt messages for a script.</span></span> <span data-ttu-id="92d94-131">`ConvertFrom-StringData`Cmdleten konverterar strängarna till en hash-tabell och lagrar dem i `$msgtable` variabeln.</span><span class="sxs-lookup"><span data-stu-id="92d94-131">The `ConvertFrom-StringData` cmdlet converts the strings into a hash table and stores them in the `$msgtable` variable.</span></span>

```powershell
$msgTable = Data {
    #culture="en-US"
    ConvertFrom-StringData @'
    helloWorld = Hello, World.
    errorMsg1 = You cannot leave the user name field blank.
    promptMsg = Please enter your user name.
'@
}
```

<span data-ttu-id="92d94-132">Mer information om här – strängar finns [about_Quoting_Rules](about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="92d94-132">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

### <a name="psd1-files-storing-translated-strings"></a><span data-ttu-id="92d94-133">PSD1-filer: lagra översatta strängar</span><span class="sxs-lookup"><span data-stu-id="92d94-133">PSD1 Files: Storing Translated Strings</span></span>

<span data-ttu-id="92d94-134">Spara skript meddelanden för varje GRÄNSSNITTs språk i separata textfiler med samma namn som skriptet och `.psd1` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="92d94-134">Save the script messages for each UI language in separate text files with the same name as the script and the `.psd1` file name extension.</span></span> <span data-ttu-id="92d94-135">Lagra filerna i under kataloger i skript katalogen med namn på kulturer i följande format:</span><span class="sxs-lookup"><span data-stu-id="92d94-135">Store the files in subdirectories of the script directory with names of cultures in the following format:</span></span>

`<language>-<region>`

<span data-ttu-id="92d94-136">Exempel: de-DE, AR-SA och zh-hans</span><span class="sxs-lookup"><span data-stu-id="92d94-136">Examples: de-DE, ar-SA, and zh-Hans</span></span>

<span data-ttu-id="92d94-137">Om skriptet till exempel `World.ps1` lagras i `C:\Scripts` katalogen skapar du en fil katalog struktur som liknar följande:</span><span class="sxs-lookup"><span data-stu-id="92d94-137">For example, if the `World.ps1` script is stored in the `C:\Scripts` directory, you would create a file directory structure that resembles the following:</span></span>

```
C:\Scripts
C:\Scripts\World.ps1
C:\Scripts\de-DE\World.psd1
C:\Scripts\ar-SA\World.psd1
C:\Scripts\zh-CN\World.psd1
...
```

<span data-ttu-id="92d94-138">`World.psd1`Filen i under katalogen indata för skript katalogen kan innehålla följande instruktion:</span><span class="sxs-lookup"><span data-stu-id="92d94-138">The `World.psd1` file in the de-DE subdirectory of the script directory might include the following statement:</span></span>

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = Hallo, Welt.
errorMsg1 = Das Feld Benutzername darf nicht leer sein.
promptMsg = Geben Sie Ihren Benutzernamen ein.
'@
```

<span data-ttu-id="92d94-139">På samma sätt `World.psd1` kan filen i under katalogen ar-sa i skript katalogen innehålla följande instruktion:</span><span class="sxs-lookup"><span data-stu-id="92d94-139">Similarly, the `World.psd1` file in the ar-SA subdirectory of the script directory might includes the following statement:</span></span>

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = مرحبًا أيها العالَم
errorMsg1 = لا يمكنك ترك حقل اسم المستخدم فارغًا
promptMsg = يرجى إدخال اسم المستخدم الخاص بك
'@
```

### <a name="import-localizeddata-dynamic-retrieval-of-translated-strings"></a><span data-ttu-id="92d94-140">Import-LocalizedData: dynamisk hämtning av översatta strängar</span><span class="sxs-lookup"><span data-stu-id="92d94-140">Import-LocalizedData: Dynamic Retrieval of Translated Strings</span></span>

<span data-ttu-id="92d94-141">Använd cmdleten för att hämta strängarna i användar gränssnitts språket för den aktuella användaren `Import-LocalizedData` .</span><span class="sxs-lookup"><span data-stu-id="92d94-141">To retrieve the strings in the UI language of the current user, use the `Import-LocalizedData` cmdlet.</span></span>

<span data-ttu-id="92d94-142">`Import-LocalizedData` söker efter värdet för den `$PSUICulture` automatiska variabeln och importerar innehållet i `<script-name>.psd1` filerna i under katalogen som matchar `$PSUICulture` värdet.</span><span class="sxs-lookup"><span data-stu-id="92d94-142">`Import-LocalizedData` finds the value of the `$PSUICulture` automatic variable and imports the content of the `<script-name>.psd1` files in the subdirectory that matches the `$PSUICulture` value.</span></span> <span data-ttu-id="92d94-143">Sedan sparas det importerade innehållet i variabeln som anges av värdet för parametern **BindingVariable** .</span><span class="sxs-lookup"><span data-stu-id="92d94-143">Then, it saves the imported content in the variable specified by the value of the **BindingVariable** parameter.</span></span>

```powershell
Import-LocalizedData -BindingVariable msgTable
```

<span data-ttu-id="92d94-144">Om kommandot till exempel `Import-LocalizedData` visas i `C:\Scripts\World.ps1` skriptet och värdet för `$PSUICulture` är "ar-sa" `Import-LocalizedData` hittar du följande fil:</span><span class="sxs-lookup"><span data-stu-id="92d94-144">For example, if the `Import-LocalizedData` command appears in the `C:\Scripts\World.ps1` script and the value of `$PSUICulture` is "ar-SA", `Import-LocalizedData` finds the following file:</span></span>

`C:\Scripts\ar-SA\World.psd1`

<span data-ttu-id="92d94-145">Sedan importerar den de arabiska text strängarna från filen till `$msgTable` variabeln och ersätter eventuella standard strängar som kan definieras i data avsnittet i `World.ps1` skriptet.</span><span class="sxs-lookup"><span data-stu-id="92d94-145">Then, it imports the Arabic text strings from the file into the `$msgTable` variable, replacing any default strings that might be defined in the Data section of the `World.ps1` script.</span></span>

<span data-ttu-id="92d94-146">Det innebär att när skriptet använder `$msgTable` variabeln för att Visa användar meddelanden visas meddelandena i arabiska.</span><span class="sxs-lookup"><span data-stu-id="92d94-146">As a result, when the script uses the `$msgTable` variable to display user messages, the messages are displayed in Arabic.</span></span>

<span data-ttu-id="92d94-147">Följande skript visar t. ex. meddelandet "Ange ditt användar namn" i arabiska:</span><span class="sxs-lookup"><span data-stu-id="92d94-147">For example, the following script displays the "Please enter your user name" message in Arabic:</span></span>

```powershell
if (!($username)) { $msgTable.promptMsg }
```

<span data-ttu-id="92d94-148">Om `Import-LocalizedData` det inte går att hitta en `.psd1` fil som matchar värdet för `$PSUIculture` , `$msgTable` ersätts inte värdet för, och anropet `$msgTable.promptMsg` visar en-US-strängar för återställningen.</span><span class="sxs-lookup"><span data-stu-id="92d94-148">If `Import-LocalizedData` cannot find a `.psd1` file that matches the value of `$PSUIculture`, the value of `$msgTable` is not replaced, and the call to `$msgTable.promptMsg` displays the fallback en-US strings.</span></span>

## <a name="examples"></a><span data-ttu-id="92d94-149">Exempel</span><span class="sxs-lookup"><span data-stu-id="92d94-149">Examples</span></span>

<span data-ttu-id="92d94-150">Det här exemplet visar hur skriptets internationaliserings funktioner används i ett skript för att visa en veckodag för användare på det språk som har angetts på datorn.</span><span class="sxs-lookup"><span data-stu-id="92d94-150">This example shows how the script internationalization features are used in a script to display a day of the week to users in the language that is set on the computer.</span></span>

<span data-ttu-id="92d94-151">Följande är en fullständig lista över Sample1.ps1 skript filen.</span><span class="sxs-lookup"><span data-stu-id="92d94-151">The following is a complete listing of the Sample1.ps1 script file.</span></span>

<span data-ttu-id="92d94-152">Skriptet börjar med ett data avsnitt med namnet dag ($Day) som innehåller ett `ConvertFrom-StringData` kommando.</span><span class="sxs-lookup"><span data-stu-id="92d94-152">The script begins with a Data section named Day ($Day) that contains a `ConvertFrom-StringData` command.</span></span> <span data-ttu-id="92d94-153">Uttrycket som skickas till `ConvertFrom-StringData` är en här-sträng som innehåller dag namnen i standard kulturen för användar gränssnittet, en-US, i nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="92d94-153">The expression submitted to `ConvertFrom-StringData` is a here-string that contains the day names in the default UI culture, en-US, in key/value pairs.</span></span> <span data-ttu-id="92d94-154">`ConvertFrom-StringData`Cmdleten konverterar nyckel/värde-par i denna-sträng till en hash-tabell och sparar den i `$Day` variabeln värde.</span><span class="sxs-lookup"><span data-stu-id="92d94-154">The `ConvertFrom-StringData` cmdlet converts the key/value pairs in the here-string into a hash table and then saves it in the value of the `$Day` variable.</span></span>

<span data-ttu-id="92d94-155">`Import-LocalizedData`Kommandot importerar innehållet i `.psd1` filen i katalogen som matchar värdet för den `$PSUICulture` automatiska variabeln och sparar det i `$Day` variabeln och ersätter värdena i `$Day` som definieras i avsnittet data.</span><span class="sxs-lookup"><span data-stu-id="92d94-155">The `Import-LocalizedData` command imports the contents of the `.psd1` file in the directory that matches the value of the `$PSUICulture` automatic variable and then saves it in the `$Day` variable, replacing the values of `$Day` that are defined in the Data section.</span></span>

<span data-ttu-id="92d94-156">De återstående kommandona läser in strängarna i en matris och visar dem.</span><span class="sxs-lookup"><span data-stu-id="92d94-156">The remaining commands load the strings into an array and display them.</span></span>

```powershell
$Day = Data {
#culture="en-US"
ConvertFrom-StringData -StringData @'
    messageDate = Today is
    d0 = Sunday
    d1 = Monday
    d2 = Tuesday
    d3 = Wednesday
    d4 = Thursday
    d5 = Friday
    d6 = Saturday
'@
}

Import-LocalizedData -BindingVariable Day

#Build an array of weekdays.
$a = $Day.d0, $Day.d1, $Day.d2, $Day.d3, $Day.d4, $Day.d5, $Day.d6

# Get the day of the week as a number (Monday = 1).
# Index into $a to get the name of the day.
# Use string formatting to build a sentence.

"{0} {1}" -f $Day.messageDate, $a[(Get-Date -UFormat %u)] | Out-Host
```

<span data-ttu-id="92d94-157">`.psd1`Filerna som stöder skriptet sparas i under kataloger i skript katalogen med namn som matchar `$PSUICulture` värdena.</span><span class="sxs-lookup"><span data-stu-id="92d94-157">The `.psd1` files that support the script are saved in subdirectories of the script directory with names that match the `$PSUICulture` values.</span></span>

<span data-ttu-id="92d94-158">Följande är en komplett lista över `.\de-DE\sample1.psd1` :</span><span class="sxs-lookup"><span data-stu-id="92d94-158">The following is a complete listing of `.\de-DE\sample1.psd1`:</span></span>

```powershell
# culture="de-DE"
ConvertFrom-StringData @'
    messageDate = Heute ist
    d0 = Sonntag
    d1 = Montag
    d2 = Dienstag
    d3 = Mittwoch
    d4 = Donnerstag
    d5 = Freitag
    d6 = Samstag
'@
```

<span data-ttu-id="92d94-159">Det innebär att när du kör Sample.ps1 på ett system där värdet för är inde `$PSUICulture` , är utdata för skriptet:</span><span class="sxs-lookup"><span data-stu-id="92d94-159">As a result, when you run Sample.ps1 on a system on which the value of `$PSUICulture` is de-DE, the output of the script is:</span></span>

```Output
Heute ist Freitag
```

## <a name="see-also"></a><span data-ttu-id="92d94-160">Se även</span><span class="sxs-lookup"><span data-stu-id="92d94-160">See also</span></span>

- [<span data-ttu-id="92d94-161">about_Data_Sections</span><span class="sxs-lookup"><span data-stu-id="92d94-161">about_Data_Sections</span></span>](about_Data_Sections.md)
- [<span data-ttu-id="92d94-162">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="92d94-162">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="92d94-163">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="92d94-163">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="92d94-164">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="92d94-164">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
- [<span data-ttu-id="92d94-165">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="92d94-165">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
- [<span data-ttu-id="92d94-166">Importera – LocalizedData</span><span class="sxs-lookup"><span data-stu-id="92d94-166">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

