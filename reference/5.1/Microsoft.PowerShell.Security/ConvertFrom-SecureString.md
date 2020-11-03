---
external help file: Microsoft.PowerShell.Security.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: 4dae7806cbec85347a8dfa01348be72061214c6c
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/09/2020
ms.locfileid: "93268028"
---
# <span data-ttu-id="7c4a8-103">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="7c4a8-103">ConvertFrom-SecureString</span></span>

## <span data-ttu-id="7c4a8-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7c4a8-104">SYNOPSIS</span></span>
<span data-ttu-id="7c4a8-105">Konverterar en säker sträng till en krypterad standard sträng.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-105">Converts a secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="7c4a8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7c4a8-106">SYNTAX</span></span>

### <span data-ttu-id="7c4a8-107">Säker (standard)</span><span class="sxs-lookup"><span data-stu-id="7c4a8-107">Secure (Default)</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="7c4a8-108">Öppna</span><span class="sxs-lookup"><span data-stu-id="7c4a8-108">Open</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="7c4a8-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7c4a8-109">DESCRIPTION</span></span>

<span data-ttu-id="7c4a8-110">**ConvertFrom-SecureString-** cmdlet: en konverterar en säker sträng ( **system. Security. SecureString** ) till en krypterad standard sträng ( **system. String** ).</span><span class="sxs-lookup"><span data-stu-id="7c4a8-110">The **ConvertFrom-SecureString** cmdlet converts a secure string ( **System.Security.SecureString** ) into an encrypted standard string ( **System.String** ).</span></span> <span data-ttu-id="7c4a8-111">Till skillnad från en säker sträng kan en krypterad standard sträng sparas i en fil för senare användning.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-111">Unlike a secure string, an encrypted standard string can be saved in a file for later use.</span></span> <span data-ttu-id="7c4a8-112">Den krypterade standard strängen kan konverteras tillbaka till dess skyddade sträng format med hjälp av `ConvertTo-SecureString` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-112">The encrypted standard string can be converted back to its secure string format by using the `ConvertTo-SecureString` cmdlet.</span></span>

<span data-ttu-id="7c4a8-113">Om en krypterings nyckel anges med hjälp av **nyckel** -eller **SecureKey** -parametrarna används krypteringsalgoritmen Advanced Encryption Standard (AES).</span><span class="sxs-lookup"><span data-stu-id="7c4a8-113">If an encryption key is specified by using the **Key** or **SecureKey** parameters, the Advanced Encryption Standard (AES) encryption algorithm is used.</span></span> <span data-ttu-id="7c4a8-114">Den angivna nyckeln måste ha en längd på 128, 192 eller 256 bitar eftersom de är de nyckel längder som stöds av AES-krypteringsalgoritmen.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-114">The specified key must have a length of 128, 192, or 256 bits because those are the key lengths supported by the AES encryption algorithm.</span></span> <span data-ttu-id="7c4a8-115">Om ingen nyckel anges används Windows Data Protection API (DPAPI) för att kryptera standard sträng representationen.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-115">If no key is specified, the Windows Data Protection API (DPAPI) is used to encrypt the standard string representation.</span></span>

## <span data-ttu-id="7c4a8-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7c4a8-116">EXAMPLES</span></span>

### <span data-ttu-id="7c4a8-117">Exempel 1: skapa en säker sträng</span><span class="sxs-lookup"><span data-stu-id="7c4a8-117">Example 1: Create a secure string</span></span>

```powershell
$SecureString = Read-Host -AsSecureString
```

<span data-ttu-id="7c4a8-118">Det här kommandot skapar en säker sträng från tecken som du skriver i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-118">This command creates a secure string from characters that you type at the command prompt.</span></span> <span data-ttu-id="7c4a8-119">När du har angett kommandot skriver du strängen som du vill lagra som en säker sträng.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-119">After entering the command, type the string you want to store as a secure string.</span></span> <span data-ttu-id="7c4a8-120">En asterisk ( `*` ) visas som representerar varje specialtecken som du skriver.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-120">An asterisk (`*`) is displayed to represent each character that you type.</span></span>

### <span data-ttu-id="7c4a8-121">Exempel 2: konvertera en säker sträng till en krypterad standard sträng</span><span class="sxs-lookup"><span data-stu-id="7c4a8-121">Example 2: Convert a secure string to an encrypted standard string</span></span>

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

<span data-ttu-id="7c4a8-122">Det här kommandot konverterar den säkra strängen i `$SecureString` variabeln till en krypterad standard sträng.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-122">This command converts the secure string in the `$SecureString` variable to an encrypted standard string.</span></span> <span data-ttu-id="7c4a8-123">Den resulterande krypterade standard strängen lagras i `$StandardString` variabeln.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-123">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

### <span data-ttu-id="7c4a8-124">Exempel 3: konvertera en säker sträng till en krypterad standard sträng med en 192-bitars nyckel</span><span class="sxs-lookup"><span data-stu-id="7c4a8-124">Example 3: Convert a secure string to an encrypted standard string with a 192-bit key</span></span>

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

<span data-ttu-id="7c4a8-125">Dessa kommandon använder algoritmen Advanced Encryption Standard (AES) för att konvertera den säkra sträng som lagras i `$SecureString` variabeln till en krypterad standard sträng med en 192-bitars nyckel.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-125">These commands use the Advanced Encryption Standard (AES) algorithm to convert the secure string stored in the `$SecureString` variable to an encrypted standard string with a 192-bit key.</span></span> <span data-ttu-id="7c4a8-126">Den resulterande krypterade standard strängen lagras i `$StandardString` variabeln.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-126">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

<span data-ttu-id="7c4a8-127">Det första kommandot lagrar en nyckel i `$Key` variabeln.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-127">The first command stores a key in the `$Key` variable.</span></span> <span data-ttu-id="7c4a8-128">Nyckeln är en matris med 24 decimaler som var och en måste vara mindre än 256 för att få plats i en ensignd byte.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-128">The key is an array of 24 decimal numerals, each of which must be less than 256 to fit within a single unsigned byte.</span></span>

<span data-ttu-id="7c4a8-129">Eftersom varje decimal tal representerar en enda byte (8 bitar) har nyckeln 24 siffror för totalt 192 bitar (8 x 24).</span><span class="sxs-lookup"><span data-stu-id="7c4a8-129">Because each decimal numeral represents a single byte (8 bits), the key has 24 digits for a total of 192 bits (8 x 24).</span></span> <span data-ttu-id="7c4a8-130">Detta är en giltig nyckel längd för AES-algoritmen.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-130">This is a valid key length for the AES algorithm.</span></span>

<span data-ttu-id="7c4a8-131">Det andra kommandot använder nyckeln i `$Key` variabeln för att konvertera den säkra strängen till en krypterad standard sträng.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-131">The second command uses the key in the `$Key` variable to convert the secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="7c4a8-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7c4a8-132">PARAMETERS</span></span>

### <span data-ttu-id="7c4a8-133">-Nyckel</span><span class="sxs-lookup"><span data-stu-id="7c4a8-133">-Key</span></span>

<span data-ttu-id="7c4a8-134">Anger krypterings nyckeln som en byte mat ris.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-134">Specifies the encryption key as a byte array.</span></span>

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

### <span data-ttu-id="7c4a8-135">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="7c4a8-135">-SecureKey</span></span>

<span data-ttu-id="7c4a8-136">Anger krypterings nyckeln som en säker sträng.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-136">Specifies the encryption key as a secure string.</span></span> <span data-ttu-id="7c4a8-137">Värdet för den säkra strängen konverteras till en byte mat ris innan det används som nyckel.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-137">The secure string value is converted to a byte array before being used as the key.</span></span>

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

### <span data-ttu-id="7c4a8-138">– SecureString</span><span class="sxs-lookup"><span data-stu-id="7c4a8-138">-SecureString</span></span>

<span data-ttu-id="7c4a8-139">Anger den säkra sträng som ska konverteras till en krypterad standard sträng.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-139">Specifies the secure string to convert to an encrypted standard string.</span></span>

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

### <span data-ttu-id="7c4a8-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7c4a8-140">CommonParameters</span></span>

<span data-ttu-id="7c4a8-141">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7c4a8-142">Mer information finns i about_CommonParameters ( https://go.microsoft.com/fwlink/?LinkID=113216) .</span><span class="sxs-lookup"><span data-stu-id="7c4a8-142">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7c4a8-143">INDATA</span><span class="sxs-lookup"><span data-stu-id="7c4a8-143">INPUTS</span></span>

### <span data-ttu-id="7c4a8-144">System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="7c4a8-144">System.Security.SecureString</span></span>

<span data-ttu-id="7c4a8-145">Du kan skicka ett **SecureString** -objekt till ConvertFrom-SecureString.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-145">You can pipe a **SecureString** object to ConvertFrom-SecureString.</span></span>

## <span data-ttu-id="7c4a8-146">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7c4a8-146">OUTPUTS</span></span>

### <span data-ttu-id="7c4a8-147">System. String</span><span class="sxs-lookup"><span data-stu-id="7c4a8-147">System.String</span></span>

<span data-ttu-id="7c4a8-148">ConvertFrom-SecureString returnerar ett standard sträng objekt.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-148">ConvertFrom-SecureString returns a standard string object.</span></span>

## <span data-ttu-id="7c4a8-149">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7c4a8-149">NOTES</span></span>

- <span data-ttu-id="7c4a8-150">Om du vill skapa en säker sträng från tecken som skrivs i kommando tolken använder du parametern **AsSecureString** för `Read-Host` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-150">To create a secure string from characters that are typed at the command prompt, use the **AsSecureString** parameter of the `Read-Host` cmdlet.</span></span>
- <span data-ttu-id="7c4a8-151">När du använder **Key** -eller **SecureKey** -parametrarna för att ange en nyckel måste nyckel längden vara korrekt.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-151">When you use the **Key** or **SecureKey** parameters to specify a key, the key length must be correct.</span></span> <span data-ttu-id="7c4a8-152">Till exempel kan en nyckel på 128 bitar anges som en byte-matris med 16 decimal siffror.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-152">For example, a key of 128 bits can be specified as a byte array of 16 decimal numerals.</span></span>
  <span data-ttu-id="7c4a8-153">På samma sätt motsvarar 192-bitars-och 256-bitars nycklar byte mat ris med 24 respektive 32 decimal siffror.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-153">Similarly, 192-bit and 256-bit keys correspond to byte arrays of 24 and 32 decimal numerals, respectively.</span></span>
- <span data-ttu-id="7c4a8-154">Vissa tecken, till exempel uttrycks symboler, motsvarar flera kod punkter i den sträng som innehåller dem.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-154">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="7c4a8-155">Undvik att använda dessa tecken eftersom de kan orsaka problem och fel som är felförstå när de används i ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="7c4a8-155">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="7c4a8-156">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7c4a8-156">RELATED LINKS</span></span>

[<span data-ttu-id="7c4a8-157">ConvertTo – SecureString</span><span class="sxs-lookup"><span data-stu-id="7c4a8-157">ConvertTo-SecureString</span></span>](ConvertTo-SecureString.md)

[<span data-ttu-id="7c4a8-158">Read-Host</span><span class="sxs-lookup"><span data-stu-id="7c4a8-158">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)
