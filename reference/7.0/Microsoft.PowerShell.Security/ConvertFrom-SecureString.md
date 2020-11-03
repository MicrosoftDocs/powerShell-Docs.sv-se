---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 07/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: 4bbdab62168a7306bb02d0ac47b5513d23920814
ms.sourcegitcommit: b7ff031a12afd04910aeb98345ebee92f5845b0c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/28/2020
ms.locfileid: "93268797"
---
# <span data-ttu-id="a61d9-103">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="a61d9-103">ConvertFrom-SecureString</span></span>

## <span data-ttu-id="a61d9-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a61d9-104">SYNOPSIS</span></span>
<span data-ttu-id="a61d9-105">Konverterar en säker sträng till en krypterad standard sträng.</span><span class="sxs-lookup"><span data-stu-id="a61d9-105">Converts a secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="a61d9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a61d9-106">SYNTAX</span></span>

### <span data-ttu-id="a61d9-107">Säker (standard)</span><span class="sxs-lookup"><span data-stu-id="a61d9-107">Secure (Default)</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="a61d9-108">Klar text</span><span class="sxs-lookup"><span data-stu-id="a61d9-108">AsPlainText</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-AsPlainText] [<CommonParameters>]
```

### <span data-ttu-id="a61d9-109">Öppna</span><span class="sxs-lookup"><span data-stu-id="a61d9-109">Open</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="a61d9-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a61d9-110">DESCRIPTION</span></span>

<span data-ttu-id="a61d9-111">**ConvertFrom-SecureString-** cmdlet: en konverterar en säker sträng ( **system. Security. SecureString** ) till en krypterad standard sträng ( **system. String** ).</span><span class="sxs-lookup"><span data-stu-id="a61d9-111">The **ConvertFrom-SecureString** cmdlet converts a secure string ( **System.Security.SecureString** ) into an encrypted standard string ( **System.String** ).</span></span> <span data-ttu-id="a61d9-112">Till skillnad från en säker sträng kan en krypterad standard sträng sparas i en fil för senare användning.</span><span class="sxs-lookup"><span data-stu-id="a61d9-112">Unlike a secure string, an encrypted standard string can be saved in a file for later use.</span></span> <span data-ttu-id="a61d9-113">Den krypterade standard strängen kan konverteras tillbaka till dess skyddade sträng format med hjälp av `ConvertTo-SecureString` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a61d9-113">The encrypted standard string can be converted back to its secure string format by using the `ConvertTo-SecureString` cmdlet.</span></span>

<span data-ttu-id="a61d9-114">Om en krypterings nyckel anges med hjälp av **nyckel** -eller **SecureKey** -parametrarna används krypteringsalgoritmen Advanced Encryption Standard (AES).</span><span class="sxs-lookup"><span data-stu-id="a61d9-114">If an encryption key is specified by using the **Key** or **SecureKey** parameters, the Advanced Encryption Standard (AES) encryption algorithm is used.</span></span> <span data-ttu-id="a61d9-115">Den angivna nyckeln måste ha en längd på 128, 192 eller 256 bitar eftersom de är de nyckel längder som stöds av AES-krypteringsalgoritmen.</span><span class="sxs-lookup"><span data-stu-id="a61d9-115">The specified key must have a length of 128, 192, or 256 bits because those are the key lengths supported by the AES encryption algorithm.</span></span> <span data-ttu-id="a61d9-116">Om ingen nyckel anges används Windows Data Protection API (DPAPI) för att kryptera standard sträng representationen.</span><span class="sxs-lookup"><span data-stu-id="a61d9-116">If no key is specified, the Windows Data Protection API (DPAPI) is used to encrypt the standard string representation.</span></span>

> [!NOTE]
> <span data-ttu-id="a61d9-117">Observera att innehållet i en SecureString inte krypteras på andra datorer än Windows-datorer per [dotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks).</span><span class="sxs-lookup"><span data-stu-id="a61d9-117">Note that per [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks), the contents of a SecureString are not encrypted on non-Windows systems.</span></span>

## <span data-ttu-id="a61d9-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a61d9-118">EXAMPLES</span></span>

### <span data-ttu-id="a61d9-119">Exempel 1: skapa en säker sträng</span><span class="sxs-lookup"><span data-stu-id="a61d9-119">Example 1: Create a secure string</span></span>

```powershell
$SecureString = Read-Host -AsSecureString
```

<span data-ttu-id="a61d9-120">Det här kommandot skapar en säker sträng från tecken som du skriver i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="a61d9-120">This command creates a secure string from characters that you type at the command prompt.</span></span> <span data-ttu-id="a61d9-121">När du har angett kommandot skriver du strängen som du vill lagra som en säker sträng.</span><span class="sxs-lookup"><span data-stu-id="a61d9-121">After entering the command, type the string you want to store as a secure string.</span></span> <span data-ttu-id="a61d9-122">En asterisk ( `*` ) visas som representerar varje specialtecken som du skriver.</span><span class="sxs-lookup"><span data-stu-id="a61d9-122">An asterisk (`*`) is displayed to represent each character that you type.</span></span>

### <span data-ttu-id="a61d9-123">Exempel 2: konvertera en säker sträng till en krypterad standard sträng</span><span class="sxs-lookup"><span data-stu-id="a61d9-123">Example 2: Convert a secure string to an encrypted standard string</span></span>

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

<span data-ttu-id="a61d9-124">Det här kommandot konverterar den säkra strängen i `$SecureString` variabeln till en krypterad standard sträng.</span><span class="sxs-lookup"><span data-stu-id="a61d9-124">This command converts the secure string in the `$SecureString` variable to an encrypted standard string.</span></span> <span data-ttu-id="a61d9-125">Den resulterande krypterade standard strängen lagras i `$StandardString` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a61d9-125">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

### <span data-ttu-id="a61d9-126">Exempel 3: konvertera en säker sträng till en krypterad standard sträng med en 192-bitars nyckel</span><span class="sxs-lookup"><span data-stu-id="a61d9-126">Example 3: Convert a secure string to an encrypted standard string with a 192-bit key</span></span>

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

<span data-ttu-id="a61d9-127">Dessa kommandon använder algoritmen Advanced Encryption Standard (AES) för att konvertera den säkra sträng som lagras i `$SecureString` variabeln till en krypterad standard sträng med en 192-bitars nyckel.</span><span class="sxs-lookup"><span data-stu-id="a61d9-127">These commands use the Advanced Encryption Standard (AES) algorithm to convert the secure string stored in the `$SecureString` variable to an encrypted standard string with a 192-bit key.</span></span> <span data-ttu-id="a61d9-128">Den resulterande krypterade standard strängen lagras i `$StandardString` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a61d9-128">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

<span data-ttu-id="a61d9-129">Det första kommandot lagrar en nyckel i `$Key` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a61d9-129">The first command stores a key in the `$Key` variable.</span></span> <span data-ttu-id="a61d9-130">Nyckeln är en matris med 24 decimaler som var och en måste vara mindre än 256 för att få plats i en ensignd byte.</span><span class="sxs-lookup"><span data-stu-id="a61d9-130">The key is an array of 24 decimal numerals, each of which must be less than 256 to fit within a single unsigned byte.</span></span>

<span data-ttu-id="a61d9-131">Eftersom varje decimal tal representerar en enda byte (8 bitar) har nyckeln 24 siffror för totalt 192 bitar (8 x 24).</span><span class="sxs-lookup"><span data-stu-id="a61d9-131">Because each decimal numeral represents a single byte (8 bits), the key has 24 digits for a total of 192 bits (8 x 24).</span></span> <span data-ttu-id="a61d9-132">Detta är en giltig nyckel längd för AES-algoritmen.</span><span class="sxs-lookup"><span data-stu-id="a61d9-132">This is a valid key length for the AES algorithm.</span></span>

<span data-ttu-id="a61d9-133">Det andra kommandot använder nyckeln i `$Key` variabeln för att konvertera den säkra strängen till en krypterad standard sträng.</span><span class="sxs-lookup"><span data-stu-id="a61d9-133">The second command uses the key in the `$Key` variable to convert the secure string to an encrypted standard string.</span></span>

### <span data-ttu-id="a61d9-134">Exempel 4: konvertera en säker sträng direkt till en oformaterad text sträng</span><span class="sxs-lookup"><span data-stu-id="a61d9-134">Example 4: Convert a secure string directly to a plaintext string</span></span>

```powershell
$secureString = ConvertTo-SecureString -String 'Example' -AsPlainText
$secureString # 'System.Security.SecureString'
ConvertFrom-SecureString -SecureString $secureString -AsPlainText # 'Example'
```

## <span data-ttu-id="a61d9-135">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a61d9-135">PARAMETERS</span></span>

### <span data-ttu-id="a61d9-136">-Klar text</span><span class="sxs-lookup"><span data-stu-id="a61d9-136">-AsPlainText</span></span>

<span data-ttu-id="a61d9-137">När det här alternativet är inställt `ConvertFrom-SecureString` konverteras säkra strängar till den dekrypterade klartext-strängen som utdata.</span><span class="sxs-lookup"><span data-stu-id="a61d9-137">When set, `ConvertFrom-SecureString` will convert secure strings to the decrypted plaintext string as output.</span></span>

<span data-ttu-id="a61d9-138">Den här parameter lades till i PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="a61d9-138">This paramater was added in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsPlainText
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a61d9-139">-Nyckel</span><span class="sxs-lookup"><span data-stu-id="a61d9-139">-Key</span></span>

<span data-ttu-id="a61d9-140">Anger krypterings nyckeln som en byte mat ris.</span><span class="sxs-lookup"><span data-stu-id="a61d9-140">Specifies the encryption key as a byte array.</span></span>

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

### <span data-ttu-id="a61d9-141">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="a61d9-141">-SecureKey</span></span>

<span data-ttu-id="a61d9-142">Anger krypterings nyckeln som en säker sträng.</span><span class="sxs-lookup"><span data-stu-id="a61d9-142">Specifies the encryption key as a secure string.</span></span> <span data-ttu-id="a61d9-143">Värdet för den säkra strängen konverteras till en byte mat ris innan det används som nyckel.</span><span class="sxs-lookup"><span data-stu-id="a61d9-143">The secure string value is converted to a byte array before being used as the key.</span></span>

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

### <span data-ttu-id="a61d9-144">– SecureString</span><span class="sxs-lookup"><span data-stu-id="a61d9-144">-SecureString</span></span>

<span data-ttu-id="a61d9-145">Anger den säkra sträng som ska konverteras till en krypterad standard sträng.</span><span class="sxs-lookup"><span data-stu-id="a61d9-145">Specifies the secure string to convert to an encrypted standard string.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a61d9-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a61d9-146">CommonParameters</span></span>

<span data-ttu-id="a61d9-147">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="a61d9-147">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`,`-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span>
<span data-ttu-id="a61d9-148">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a61d9-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a61d9-149">INDATA</span><span class="sxs-lookup"><span data-stu-id="a61d9-149">INPUTS</span></span>

### <span data-ttu-id="a61d9-150">System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="a61d9-150">System.Security.SecureString</span></span>

<span data-ttu-id="a61d9-151">Du kan skicka ett **SecureString** -objekt till ConvertFrom-SecureString.</span><span class="sxs-lookup"><span data-stu-id="a61d9-151">You can pipe a **SecureString** object to ConvertFrom-SecureString.</span></span>

## <span data-ttu-id="a61d9-152">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a61d9-152">OUTPUTS</span></span>

### <span data-ttu-id="a61d9-153">System. String</span><span class="sxs-lookup"><span data-stu-id="a61d9-153">System.String</span></span>

<span data-ttu-id="a61d9-154">ConvertFrom-SecureString returnerar ett standard sträng objekt.</span><span class="sxs-lookup"><span data-stu-id="a61d9-154">ConvertFrom-SecureString returns a standard string object.</span></span>

## <span data-ttu-id="a61d9-155">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a61d9-155">NOTES</span></span>

- <span data-ttu-id="a61d9-156">Om du vill skapa en säker sträng från tecken som skrivs i kommando tolken använder du parametern **AsSecureString** för `Read-Host` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a61d9-156">To create a secure string from characters that are typed at the command prompt, use the **AsSecureString** parameter of the `Read-Host` cmdlet.</span></span>
- <span data-ttu-id="a61d9-157">När du använder **Key** -eller **SecureKey** -parametrarna för att ange en nyckel måste nyckel längden vara korrekt.</span><span class="sxs-lookup"><span data-stu-id="a61d9-157">When you use the **Key** or **SecureKey** parameters to specify a key, the key length must be correct.</span></span> <span data-ttu-id="a61d9-158">Till exempel kan en nyckel på 128 bitar anges som en byte-matris med 16 decimal siffror.</span><span class="sxs-lookup"><span data-stu-id="a61d9-158">For example, a key of 128 bits can be specified as a byte array of 16 decimal numerals.</span></span>
  <span data-ttu-id="a61d9-159">På samma sätt motsvarar 192-bitars-och 256-bitars nycklar byte mat ris med 24 respektive 32 decimal siffror.</span><span class="sxs-lookup"><span data-stu-id="a61d9-159">Similarly, 192-bit and 256-bit keys correspond to byte arrays of 24 and 32 decimal numerals, respectively.</span></span>
- <span data-ttu-id="a61d9-160">Vissa tecken, till exempel uttrycks symboler, motsvarar flera kod punkter i den sträng som innehåller dem.</span><span class="sxs-lookup"><span data-stu-id="a61d9-160">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="a61d9-161">Undvik att använda dessa tecken eftersom de kan orsaka problem och fel som är felförstå när de används i ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="a61d9-161">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="a61d9-162">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a61d9-162">RELATED LINKS</span></span>

[<span data-ttu-id="a61d9-163">ConvertTo – SecureString</span><span class="sxs-lookup"><span data-stu-id="a61d9-163">ConvertTo-SecureString</span></span>](ConvertTo-SecureString.md)

[<span data-ttu-id="a61d9-164">Read-Host</span><span class="sxs-lookup"><span data-stu-id="a61d9-164">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)
