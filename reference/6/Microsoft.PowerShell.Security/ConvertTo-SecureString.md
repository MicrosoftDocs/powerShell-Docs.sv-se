---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-SecureString
ms.openlocfilehash: 71b2a36601281d148bed6742ce3f3cb78e11acf4
ms.sourcegitcommit: df80c558e9a4b89c9798f084bd04012ece15155c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/23/2020
ms.locfileid: "93273393"
---
# <span data-ttu-id="75c38-103">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="75c38-103">ConvertTo-SecureString</span></span>

## <span data-ttu-id="75c38-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="75c38-104">SYNOPSIS</span></span>
<span data-ttu-id="75c38-105">Konverterar oformaterad text eller krypterade strängar för att skydda strängar.</span><span class="sxs-lookup"><span data-stu-id="75c38-105">Converts plain text or encrypted strings to secure strings.</span></span>

## <span data-ttu-id="75c38-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="75c38-106">SYNTAX</span></span>

### <span data-ttu-id="75c38-107">Säker (standard)</span><span class="sxs-lookup"><span data-stu-id="75c38-107">Secure (Default)</span></span>

```
ConvertTo-SecureString [-String] <String> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="75c38-108">PlainText</span><span class="sxs-lookup"><span data-stu-id="75c38-108">PlainText</span></span>

```
ConvertTo-SecureString [-String] <String> [-AsPlainText] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="75c38-109">Öppna</span><span class="sxs-lookup"><span data-stu-id="75c38-109">Open</span></span>

```
ConvertTo-SecureString [-String] <String> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="75c38-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="75c38-110">DESCRIPTION</span></span>

<span data-ttu-id="75c38-111">`ConvertTo-SecureString`Cmdleten konverterar krypterade standard strängar till säkra strängar.</span><span class="sxs-lookup"><span data-stu-id="75c38-111">The `ConvertTo-SecureString` cmdlet converts encrypted standard strings into secure strings.</span></span> <span data-ttu-id="75c38-112">Den kan också konvertera oformaterad text för att skydda strängar.</span><span class="sxs-lookup"><span data-stu-id="75c38-112">It can also convert plain text to secure strings.</span></span> <span data-ttu-id="75c38-113">Den används med `ConvertFrom-SecureString` och `Read-Host` .</span><span class="sxs-lookup"><span data-stu-id="75c38-113">It is used with `ConvertFrom-SecureString` and `Read-Host`.</span></span> <span data-ttu-id="75c38-114">Den säkra sträng som skapas av cmdleten kan användas med cmdletar eller funktioner som kräver en parameter av typen **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="75c38-114">The secure string created by the cmdlet can be used with cmdlets or functions that require a parameter of type **SecureString**.</span></span> <span data-ttu-id="75c38-115">Den säkra strängen kan konverteras tillbaka till en krypterad standard sträng med hjälp av `ConvertFrom-SecureString` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="75c38-115">The secure string can be converted back to an encrypted, standard string using the `ConvertFrom-SecureString` cmdlet.</span></span> <span data-ttu-id="75c38-116">Detta gör att det kan lagras i en fil för senare användning.</span><span class="sxs-lookup"><span data-stu-id="75c38-116">This enables it to be stored in a file for later use.</span></span>

<span data-ttu-id="75c38-117">Om standard strängen som konverterades har krypterats med `ConvertFrom-SecureString` en angiven nyckel måste samma nyckel anges som värde för parametern **Key** eller parametern **SecureKey** för `ConvertTo-SecureString` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="75c38-117">If the standard string being converted was encrypted with `ConvertFrom-SecureString` using a specified key, that same key must be provided as the value of the **Key** or **SecureKey** parameter of the `ConvertTo-SecureString` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="75c38-118">Observera att innehållet i en SecureString inte krypteras på andra datorer än Windows-datorer per [dotNet](/dotnet/api/system.security.securestring#remarks).</span><span class="sxs-lookup"><span data-stu-id="75c38-118">Note that per [DotNet](/dotnet/api/system.security.securestring#remarks), the contents of a SecureString are not encrypted on non-Windows systems.</span></span>

## <span data-ttu-id="75c38-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="75c38-119">EXAMPLES</span></span>

### <span data-ttu-id="75c38-120">Exempel 1: konvertera en säker sträng till en krypterad sträng</span><span class="sxs-lookup"><span data-stu-id="75c38-120">Example 1: Convert a secure string to an encrypted string</span></span>

<span data-ttu-id="75c38-121">Det här exemplet visar hur du skapar en säker sträng från användarindata, konverterar den säkra strängen till en krypterad standard sträng och sedan konverterar den krypterade standard strängen tillbaka till en säker sträng.</span><span class="sxs-lookup"><span data-stu-id="75c38-121">This example shows how to create a secure string from user input, convert the secure string to an encrypted standard string, and then convert the encrypted standard string back to a secure string.</span></span>

```powershell
PS C:\> $Secure = Read-Host -AsSecureString
PS C:\> $Secure
System.Security.SecureString
PS C:\> $Encrypted = ConvertFrom-SecureString -SecureString $Secure
PS C:\> $Encrypted
01000000d08c9ddf0115d1118c7a00c04fc297eb010000001a114d45b8dd3f4aa11ad7c0abdae98000000000
02000000000003660000a8000000100000005df63cea84bfb7d70bd6842e7efa79820000000004800000a000
000010000000f10cd0f4a99a8d5814d94e0687d7430b100000008bf11f1960158405b2779613e9352c6d1400
0000e6b7bf46a9d485ff211b9b2a2df3bd6eb67aae41
PS C:\> $Secure2 = ConvertTo-SecureString -String $Encrypted
PS C:\> $Secure2
System.Security.SecureString
```

<span data-ttu-id="75c38-122">Det första kommandot använder **AsSecureString** -parametern för `Read-Host` cmdleten för att skapa en säker sträng.</span><span class="sxs-lookup"><span data-stu-id="75c38-122">The first command uses the **AsSecureString** parameter of the `Read-Host` cmdlet to create a secure string.</span></span> <span data-ttu-id="75c38-123">När du har angett kommandot konverteras alla tecken som du skriver till en säker sträng och sparas sedan i `$Secure` variabeln.</span><span class="sxs-lookup"><span data-stu-id="75c38-123">After you enter the command, any characters that you type are converted into a secure string and then saved in the `$Secure` variable.</span></span>

<span data-ttu-id="75c38-124">Det andra kommandot visar innehållet i `$Secure` variabeln.</span><span class="sxs-lookup"><span data-stu-id="75c38-124">The second command displays the contents of the `$Secure` variable.</span></span> <span data-ttu-id="75c38-125">Eftersom `$Secure` variabeln innehåller en säker sträng visar PowerShell endast **system. Security. SecureString** -typen.</span><span class="sxs-lookup"><span data-stu-id="75c38-125">Because the `$Secure` variable contains a secure string, PowerShell displays only the **System.Security.SecureString** type.</span></span>

<span data-ttu-id="75c38-126">Det tredje kommandot använder `ConvertFrom-SecureString` cmdleten för att konvertera den säkra strängen i `$Secure` variabeln till en krypterad standard sträng.</span><span class="sxs-lookup"><span data-stu-id="75c38-126">The third command uses the `ConvertFrom-SecureString` cmdlet to convert the secure string in the `$Secure` variable into an encrypted standard string.</span></span> <span data-ttu-id="75c38-127">Resultatet sparas i `$Encrypted` variabeln.</span><span class="sxs-lookup"><span data-stu-id="75c38-127">It saves the result in the `$Encrypted` variable.</span></span>

<span data-ttu-id="75c38-128">Det fjärde kommandot visar den krypterade strängen i värdet för `$Encrypted` variabeln.</span><span class="sxs-lookup"><span data-stu-id="75c38-128">The fourth command displays the encrypted string in the value of the `$Encrypted` variable.</span></span>

<span data-ttu-id="75c38-129">Det femte kommandot använder `ConvertTo-SecureString` cmdleten för att konvertera den krypterade standard strängen i `$Encrypted` variabeln tillbaka till en säker sträng.</span><span class="sxs-lookup"><span data-stu-id="75c38-129">The fifth command uses the `ConvertTo-SecureString` cmdlet to convert the encrypted standard string in the `$Encrypted` variable back into a secure string.</span></span> <span data-ttu-id="75c38-130">Resultatet sparas i `$Secure2` variabeln.</span><span class="sxs-lookup"><span data-stu-id="75c38-130">It saves the result in the `$Secure2` variable.</span></span>
<span data-ttu-id="75c38-131">Det sjätte kommandot visar värdet för `$Secure2` variabeln.</span><span class="sxs-lookup"><span data-stu-id="75c38-131">The sixth command displays the value of the `$Secure2` variable.</span></span> <span data-ttu-id="75c38-132">Typen SecureString anger att kommandot lyckades.</span><span class="sxs-lookup"><span data-stu-id="75c38-132">The SecureString type indicates that the command was successful.</span></span>

### <span data-ttu-id="75c38-133">Exempel 2: skapa en säker sträng från en krypterad sträng i en fil</span><span class="sxs-lookup"><span data-stu-id="75c38-133">Example 2: Create a secure string from an encrypted string in a file</span></span>

<span data-ttu-id="75c38-134">Det här exemplet visar hur du skapar en säker sträng från en krypterad standard sträng som sparas i en fil.</span><span class="sxs-lookup"><span data-stu-id="75c38-134">This example shows how to create a secure string from an encrypted standard string that is saved in a file.</span></span>

```powershell
$Secure = Read-Host -AsSecureString
$Encrypted = ConvertFrom-SecureString -SecureString $Secure -Key (1..16)
$Encrypted | Set-Content Encrypted.txt
$Secure2 = Get-Content Encrypted.txt | ConvertTo-SecureString -Key (1..16)
```

<span data-ttu-id="75c38-135">Det första kommandot använder **AsSecureString** -parametern för `Read-Host` cmdleten för att skapa en säker sträng.</span><span class="sxs-lookup"><span data-stu-id="75c38-135">The first command uses the **AsSecureString** parameter of the `Read-Host` cmdlet to create a secure string.</span></span> <span data-ttu-id="75c38-136">När du har angett kommandot konverteras alla tecken som du skriver till en säker sträng och sparas sedan i `$Secure` variabeln.</span><span class="sxs-lookup"><span data-stu-id="75c38-136">After you enter the command, any characters that you type are converted into a secure string and then saved in the `$Secure` variable.</span></span>

<span data-ttu-id="75c38-137">Det andra kommandot använder `ConvertFrom-SecureString` cmdleten för att konvertera den säkra strängen i `$Secure` variabeln till en krypterad standard sträng med hjälp av den angivna nyckeln.</span><span class="sxs-lookup"><span data-stu-id="75c38-137">The second command uses the `ConvertFrom-SecureString` cmdlet to convert the secure string in the `$Secure` variable into an encrypted standard string by using the specified key.</span></span> <span data-ttu-id="75c38-138">Innehållet sparas i `$Encrypted` variabeln.</span><span class="sxs-lookup"><span data-stu-id="75c38-138">The contents are saved in the `$Encrypted` variable.</span></span>

<span data-ttu-id="75c38-139">Det tredje kommandot använder en pipeline-operator ( `|` ) för att skicka värdet för `$Encrypted` variabeln till `Set-Content` cmdleten, vilket sparar värdet i Encrypted.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="75c38-139">The third command uses a pipeline operator (`|`) to send the value of the `$Encrypted` variable to the `Set-Content` cmdlet, which saves the value in the Encrypted.txt file.</span></span>

<span data-ttu-id="75c38-140">Det fjärde kommandot använder `Get-Content` cmdleten för att hämta den krypterade standard strängen i Encrypted.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="75c38-140">The fourth command uses the `Get-Content` cmdlet to get the encrypted standard string in the Encrypted.txt file.</span></span> <span data-ttu-id="75c38-141">Kommandot använder en pipeline-operator för att skicka den krypterade strängen till `ConvertTo-SecureString` cmdleten, vilket konverterar den till en säker sträng med hjälp av den angivna nyckeln.</span><span class="sxs-lookup"><span data-stu-id="75c38-141">The command uses a pipeline operator to send the encrypted string to the `ConvertTo-SecureString` cmdlet, which converts it to a secure string by using the specified key.</span></span>
<span data-ttu-id="75c38-142">Resultaten sparas i `$Secure2` variabeln.</span><span class="sxs-lookup"><span data-stu-id="75c38-142">The results are saved in the `$Secure2` variable.</span></span>

### <span data-ttu-id="75c38-143">Exempel 3: konvertera en oformaterad text sträng till en säker sträng</span><span class="sxs-lookup"><span data-stu-id="75c38-143">Example 3: Convert a plain text string to a secure string</span></span>

<span data-ttu-id="75c38-144">Det här kommandot konverterar den oformaterade text strängen `P@ssW0rD!` till en säker sträng och lagrar resultatet i `$Secure_String_Pwd` variabeln.</span><span class="sxs-lookup"><span data-stu-id="75c38-144">This command converts the plain text string `P@ssW0rD!` into a secure string and stores the result in the `$Secure_String_Pwd` variable.</span></span> <span data-ttu-id="75c38-145">Om du vill använda parametern **Disklar text** måste även **Force** -parametern ingå i kommandot.</span><span class="sxs-lookup"><span data-stu-id="75c38-145">To use the **AsPlainText** parameter, the **Force** parameter must also be included in the command.</span></span>

```powershell
$Secure_String_Pwd = ConvertTo-SecureString "P@ssW0rD!" -AsPlainText -Force
```

> [!CAUTION]
> <span data-ttu-id="75c38-146">Undvik att använda oformaterade text strängar i skript eller på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="75c38-146">You should avoid using plain text strings in script or from the command line.</span></span> <span data-ttu-id="75c38-147">Den oformaterade texten kan visas i händelse loggar och kommando historik loggar.</span><span class="sxs-lookup"><span data-stu-id="75c38-147">The plain text can show up in event logs and command history logs.</span></span>

## <span data-ttu-id="75c38-148">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="75c38-148">PARAMETERS</span></span>

### <span data-ttu-id="75c38-149">-Klar text</span><span class="sxs-lookup"><span data-stu-id="75c38-149">-AsPlainText</span></span>

<span data-ttu-id="75c38-150">Anger en oformaterad text sträng som ska konverteras till en säker sträng.</span><span class="sxs-lookup"><span data-stu-id="75c38-150">Specifies a plain text string to convert to a secure string.</span></span> <span data-ttu-id="75c38-151">De säkra sträng-cmdletarna skyddar konfidentiell text.</span><span class="sxs-lookup"><span data-stu-id="75c38-151">The secure string cmdlets help protect confidential text.</span></span> <span data-ttu-id="75c38-152">Texten krypteras för sekretess och tas bort från dator minnet när den har använts.</span><span class="sxs-lookup"><span data-stu-id="75c38-152">The text is encrypted for privacy and is deleted from computer memory after it is used.</span></span> <span data-ttu-id="75c38-153">Om du använder den här parametern för att ange oformaterad text som inmatade kan systemet inte skydda dessa inmatade på det här sättet.</span><span class="sxs-lookup"><span data-stu-id="75c38-153">If you use this parameter to provide plain text as input, the system cannot protect that input in this manner.</span></span> <span data-ttu-id="75c38-154">Om du vill använda den här parametern måste du även ange **Force** -parametern.</span><span class="sxs-lookup"><span data-stu-id="75c38-154">To use this parameter, you must also specify the **Force** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="75c38-155">-Force</span><span class="sxs-lookup"><span data-stu-id="75c38-155">-Force</span></span>

<span data-ttu-id="75c38-156">Bekräftar att du förstår konsekvenserna av att använda parametern **Disklar text** och fortfarande vill använda den.</span><span class="sxs-lookup"><span data-stu-id="75c38-156">Confirms that you understand the implications of using the **AsPlainText** parameter and still want to use it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="75c38-157">-Nyckel</span><span class="sxs-lookup"><span data-stu-id="75c38-157">-Key</span></span>

<span data-ttu-id="75c38-158">Anger den krypterings nyckel som används för att konvertera den ursprungliga säkra strängen till den krypterade standard strängen.</span><span class="sxs-lookup"><span data-stu-id="75c38-158">Specifies the encryption key used to convert the original secure string into the encrypted standard string.</span></span> <span data-ttu-id="75c38-159">Giltiga nyckel längder är 16, 24 och 32 byte.</span><span class="sxs-lookup"><span data-stu-id="75c38-159">Valid key lengths are 16, 24 and 32 bytes.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: Open
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="75c38-160">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="75c38-160">-SecureKey</span></span>

<span data-ttu-id="75c38-161">Anger den krypterings nyckel som används för att konvertera den ursprungliga säkra strängen till den krypterade standard strängen.</span><span class="sxs-lookup"><span data-stu-id="75c38-161">Specifies the encryption key used to convert the original secure string into the encrypted standard string.</span></span> <span data-ttu-id="75c38-162">Nyckeln måste anges i formatet för en säker sträng.</span><span class="sxs-lookup"><span data-stu-id="75c38-162">The key must be provided in the format of a secure string.</span></span> <span data-ttu-id="75c38-163">Den säkra strängen kommer att konverteras till en byte mat ris som ska användas som nyckel.</span><span class="sxs-lookup"><span data-stu-id="75c38-163">The secure string will be converted to a byte array to be used as the key.</span></span> <span data-ttu-id="75c38-164">Giltiga längder för säkra nycklar är 8, 12 och 16 kod punkter.</span><span class="sxs-lookup"><span data-stu-id="75c38-164">Valid secure key lengths are 8, 12 and 16 code points.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: Secure
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="75c38-165">– Sträng</span><span class="sxs-lookup"><span data-stu-id="75c38-165">-String</span></span>

<span data-ttu-id="75c38-166">Anger den sträng som ska konverteras till en säker sträng.</span><span class="sxs-lookup"><span data-stu-id="75c38-166">Specifies the string to convert to a secure string.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="75c38-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="75c38-167">CommonParameters</span></span>

<span data-ttu-id="75c38-168">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="75c38-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="75c38-169">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="75c38-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="75c38-170">INDATA</span><span class="sxs-lookup"><span data-stu-id="75c38-170">INPUTS</span></span>

### <span data-ttu-id="75c38-171">System. String</span><span class="sxs-lookup"><span data-stu-id="75c38-171">System.String</span></span>

<span data-ttu-id="75c38-172">Du kan skicka vidare en krypterad standard sträng till `ConvertTo-SecureString` .</span><span class="sxs-lookup"><span data-stu-id="75c38-172">You can pipe a standard encrypted string to `ConvertTo-SecureString`.</span></span>

## <span data-ttu-id="75c38-173">UTDATA</span><span class="sxs-lookup"><span data-stu-id="75c38-173">OUTPUTS</span></span>

### <span data-ttu-id="75c38-174">System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="75c38-174">System.Security.SecureString</span></span>

<span data-ttu-id="75c38-175">`ConvertTo-SecureString` Returnerar ett **SecureString** -objekt.</span><span class="sxs-lookup"><span data-stu-id="75c38-175">`ConvertTo-SecureString` returns a **SecureString** object.</span></span>

## <span data-ttu-id="75c38-176">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="75c38-176">NOTES</span></span>

<span data-ttu-id="75c38-177">Vissa tecken, till exempel uttrycks symboler, motsvarar flera kod punkter i den sträng som innehåller dem.</span><span class="sxs-lookup"><span data-stu-id="75c38-177">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="75c38-178">Undvik att använda dessa tecken eftersom de kan orsaka problem och fel som är felförstå när de används i ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="75c38-178">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="75c38-179">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="75c38-179">RELATED LINKS</span></span>

[<span data-ttu-id="75c38-180">ConvertFrom – SecureString</span><span class="sxs-lookup"><span data-stu-id="75c38-180">ConvertFrom-SecureString</span></span>](ConvertFrom-SecureString.md)

[<span data-ttu-id="75c38-181">Read-Host</span><span class="sxs-lookup"><span data-stu-id="75c38-181">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)
