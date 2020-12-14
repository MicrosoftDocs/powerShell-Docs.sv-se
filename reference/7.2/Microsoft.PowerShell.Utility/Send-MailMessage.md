---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Send-MailMessage
ms.openlocfilehash: 0a68c665e8a0b504cfef416134374c5598ba55a7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708343"
---
# <span data-ttu-id="45468-102">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="45468-102">Send-MailMessage</span></span>

## <span data-ttu-id="45468-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="45468-103">SYNOPSIS</span></span>
<span data-ttu-id="45468-104">Skickar ett e-postmeddelande.</span><span class="sxs-lookup"><span data-stu-id="45468-104">Sends an email message.</span></span>

## <span data-ttu-id="45468-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="45468-105">SYNTAX</span></span>

### <span data-ttu-id="45468-106">Alla</span><span class="sxs-lookup"><span data-stu-id="45468-106">All</span></span>

```
Send-MailMessage [-Attachments <String[]>] [-Bcc <String[]>] [[-Body] <String>] [-BodyAsHtml]
 [-Encoding <Encoding>] [-Cc <String[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 -From <String> [[-SmtpServer] <String>] [-Priority <MailPriority>] [-ReplyTo <String[]>]
 [[-Subject] <String>] [-To] <String[]> [-Credential <PSCredential>] [-UseSsl] [-Port <Int32>]
 [<CommonParameters>]
```

## <span data-ttu-id="45468-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="45468-107">DESCRIPTION</span></span>

<span data-ttu-id="45468-108">`Send-MailMessage`Cmdleten skickar ett e-postmeddelande inifrån PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45468-108">The `Send-MailMessage` cmdlet sends an email message from within PowerShell.</span></span>

<span data-ttu-id="45468-109">Du måste ange en Simple Mail Transfer Protocol-server (SMTP) eller `Send-MailMessage` kommandot fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="45468-109">You must specify a Simple Mail Transfer Protocol (SMTP) server or the `Send-MailMessage` command fails.</span></span> <span data-ttu-id="45468-110">Använd parametern **SmtpServer** eller Ställ in `$PSEmailServer` variabeln på en giltig SMTP-server.</span><span class="sxs-lookup"><span data-stu-id="45468-110">Use the **SmtpServer** parameter or set the `$PSEmailServer` variable to a valid SMTP server.</span></span>
<span data-ttu-id="45468-111">Värdet som tilldelas `$PSEmailServer` är standard SMTP-inställningen för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45468-111">The value assigned to `$PSEmailServer` is the default SMTP setting for PowerShell.</span></span> <span data-ttu-id="45468-112">Mer information finns i [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="45468-112">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

> [!WARNING]
> <span data-ttu-id="45468-113">`Send-MailMessage`Cmdleten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="45468-113">The `Send-MailMessage` cmdlet is obsolete.</span></span> <span data-ttu-id="45468-114">Denna cmdlet garanterar inte säkra anslutningar till SMTP-servrar.</span><span class="sxs-lookup"><span data-stu-id="45468-114">This cmdlet does not guarantee secure connections to SMTP servers.</span></span> <span data-ttu-id="45468-115">Det finns ingen omedelbar ersättning tillgänglig i PowerShell, men vi rekommenderar att du inte använder `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="45468-115">While there is no immediate replacement available in PowerShell, we recommend you do not use `Send-MailMessage`.</span></span> <span data-ttu-id="45468-116">Mer information finns i [Platform Compatibility NOTE DE0005](https://aka.ms/SendMailMessage).</span><span class="sxs-lookup"><span data-stu-id="45468-116">For more information, see [Platform Compatibility note DE0005](https://aka.ms/SendMailMessage).</span></span>

## <span data-ttu-id="45468-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="45468-117">EXAMPLES</span></span>

### <span data-ttu-id="45468-118">Exempel 1: Skicka ett e-postmeddelande från en person till en annan person</span><span class="sxs-lookup"><span data-stu-id="45468-118">Example 1: Send an email from one person to another person</span></span>

<span data-ttu-id="45468-119">I det här exemplet skickas ett e-postmeddelande från en person till en annan person.</span><span class="sxs-lookup"><span data-stu-id="45468-119">This example sends an email message from one person to another person.</span></span>

<span data-ttu-id="45468-120">Parametrarna **from**, **to** och **subject** krävs av `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="45468-120">The **From**, **To**, and **Subject** parameters are required by `Send-MailMessage`.</span></span> <span data-ttu-id="45468-121">I det här exemplet används standard `$PSEmailServer` variabeln för SMTP-servern, så **SmtpServer** -parametern behövs inte.</span><span class="sxs-lookup"><span data-stu-id="45468-121">This example uses the default `$PSEmailServer` variable for the SMTP server, so the **SmtpServer** parameter is not needed.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

<span data-ttu-id="45468-122">`Send-MailMessage`Cmdleten använder parametern **from** för att ange meddelandets avsändare.</span><span class="sxs-lookup"><span data-stu-id="45468-122">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="45468-123">Parametern **to** anger meddelandets mottagare.</span><span class="sxs-lookup"><span data-stu-id="45468-123">The **To** parameter specifies the message's recipient.</span></span> <span data-ttu-id="45468-124">**Ämnes** parametern använder text strängen **Testa e-post** som meddelandet eftersom den valfria **text** parametern inte ingår.</span><span class="sxs-lookup"><span data-stu-id="45468-124">The **Subject** parameter uses the text string **Test mail** as the message because the optional **Body** parameter is not included.</span></span>

### <span data-ttu-id="45468-125">Exempel 2: skicka en bifogad fil</span><span class="sxs-lookup"><span data-stu-id="45468-125">Example 2: Send an attachment</span></span>

<span data-ttu-id="45468-126">Det här exemplet skickar ett e-postmeddelande med en bifogad fil.</span><span class="sxs-lookup"><span data-stu-id="45468-126">This example sends an email message with an attachment.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

<span data-ttu-id="45468-127">`Send-MailMessage`Cmdleten använder parametern **from** för att ange meddelandets avsändare.</span><span class="sxs-lookup"><span data-stu-id="45468-127">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="45468-128">Parametern **to** anger meddelandets mottagare.</span><span class="sxs-lookup"><span data-stu-id="45468-128">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="45468-129">**Ämnes** parametern beskriver meddelandets innehåll.</span><span class="sxs-lookup"><span data-stu-id="45468-129">The **Subject** parameter describes the content of the message.</span></span> <span data-ttu-id="45468-130">**Body** -parametern är meddelandets innehåll.</span><span class="sxs-lookup"><span data-stu-id="45468-130">The **Body** parameter is the content of the message.</span></span>

<span data-ttu-id="45468-131">Parametern **Attachments** anger filen i den aktuella katalogen som är kopplad till e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="45468-131">The **Attachments** parameter specifies the file in the current directory that is attached to the email message.</span></span> <span data-ttu-id="45468-132">**Prioritets** parametern anger meddelandet till **hög** prioritet.</span><span class="sxs-lookup"><span data-stu-id="45468-132">The **Priority** parameter sets the message to **High** priority.</span></span> <span data-ttu-id="45468-133">Parametern **-DeliveryNotificationOption** anger två värden, **OnSuccess** och **onFailure**.</span><span class="sxs-lookup"><span data-stu-id="45468-133">The **-DeliveryNotificationOption** parameter specifies two values, **OnSuccess** and **OnFailure**.</span></span> <span data-ttu-id="45468-134">Avsändaren får e-postaviseringar för att bekräfta att meddelande leveransen har lyckats eller misslyckats.</span><span class="sxs-lookup"><span data-stu-id="45468-134">The sender will receive email notifications to confirm the success or failure of the message delivery.</span></span>
<span data-ttu-id="45468-135">Parametern **SmtpServer** anger SMTP-servern till **SMTP.fabrikam.com**.</span><span class="sxs-lookup"><span data-stu-id="45468-135">The **SmtpServer** parameter sets the SMTP server to **smtp.fabrikam.com**.</span></span>

### <span data-ttu-id="45468-136">Exempel 3: skicka e-post till en distributions lista</span><span class="sxs-lookup"><span data-stu-id="45468-136">Example 3: Send email to a mailing list</span></span>

<span data-ttu-id="45468-137">Det här exemplet skickar ett e-postmeddelande till en distributions lista.</span><span class="sxs-lookup"><span data-stu-id="45468-137">This example sends an email message to a mailing list.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

<span data-ttu-id="45468-138">`Send-MailMessage`Cmdleten använder parametern **from** för att ange meddelandets avsändare.</span><span class="sxs-lookup"><span data-stu-id="45468-138">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="45468-139">Parametern **to** anger meddelandets mottagare.</span><span class="sxs-lookup"><span data-stu-id="45468-139">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="45468-140">Parametern **CC** skickar en kopia av meddelandet till den angivna mottagaren.</span><span class="sxs-lookup"><span data-stu-id="45468-140">The **Cc** parameter sends a copy of the message to the specified recipient.</span></span> <span data-ttu-id="45468-141">Parametern **hemlig** kopia skickar en hemlig kopia av meddelandet.</span><span class="sxs-lookup"><span data-stu-id="45468-141">The **Bcc** parameter sends a blind copy of the message.</span></span> <span data-ttu-id="45468-142">En hemlig kopia är en e-postadress som är dold från de andra mottagarna.</span><span class="sxs-lookup"><span data-stu-id="45468-142">A blind copy is an email address that is hidden from the other recipients.</span></span> <span data-ttu-id="45468-143">**Subject** -parametern är meddelandet eftersom den valfria **text** parametern inte ingår.</span><span class="sxs-lookup"><span data-stu-id="45468-143">The **Subject** parameter is the message because the optional **Body** parameter is not included.</span></span>

<span data-ttu-id="45468-144">Parametern **Credential** anger en domän administratörs autentiseringsuppgifter som används för att skicka meddelandet.</span><span class="sxs-lookup"><span data-stu-id="45468-144">The **Credential** parameter specifies a domain administrator's credentials are used to send the message.</span></span> <span data-ttu-id="45468-145">Parametern **UseSsl** anger att SSL (Secure Socket Layer) skapar en säker anslutning.</span><span class="sxs-lookup"><span data-stu-id="45468-145">The **UseSsl** parameter specifies that Secure Socket Layer (SSL) creates a secure connection.</span></span>

## <span data-ttu-id="45468-146">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="45468-146">PARAMETERS</span></span>

### <span data-ttu-id="45468-147">-Bilagor</span><span class="sxs-lookup"><span data-stu-id="45468-147">-Attachments</span></span>

<span data-ttu-id="45468-148">Anger sökväg och fil namn för de filer som ska bifogas i e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="45468-148">Specifies the path and file names of files to be attached to the email message.</span></span> <span data-ttu-id="45468-149">Du kan använda den här parametern eller Ange sökvägar och fil namn till `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="45468-149">You can use this parameter or pipe the paths and file names to `Send-MailMessage`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PsPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-150">– Hemlig kopia</span><span class="sxs-lookup"><span data-stu-id="45468-150">-Bcc</span></span>

<span data-ttu-id="45468-151">Anger e-postadresserna som får en kopia av e-postmeddelandet men som inte visas som mottagare av meddelandet.</span><span class="sxs-lookup"><span data-stu-id="45468-151">Specifies the email addresses that receive a copy of the mail but are not listed as recipients of the message.</span></span> <span data-ttu-id="45468-152">Ange namn (valfritt) och e-postadressen, till exempel `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="45468-152">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-153">-Body</span><span class="sxs-lookup"><span data-stu-id="45468-153">-Body</span></span>

<span data-ttu-id="45468-154">Anger e-postmeddelandets innehåll.</span><span class="sxs-lookup"><span data-stu-id="45468-154">Specifies the content of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-155">-BodyAsHtml</span><span class="sxs-lookup"><span data-stu-id="45468-155">-BodyAsHtml</span></span>

<span data-ttu-id="45468-156">Anger att värdet för **text** parametern innehåller HTML.</span><span class="sxs-lookup"><span data-stu-id="45468-156">Specifies that the value of the **Body** parameter contains HTML.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: BAH

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-157">-CC</span><span class="sxs-lookup"><span data-stu-id="45468-157">-Cc</span></span>

<span data-ttu-id="45468-158">Anger e-postadresserna som en kopia av e-postmeddelandet skickas till.</span><span class="sxs-lookup"><span data-stu-id="45468-158">Specifies the email addresses to which a carbon copy (CC) of the email message is sent.</span></span> <span data-ttu-id="45468-159">Ange namn (valfritt) och e-postadressen, till exempel `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="45468-159">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-160">-Credential</span><span class="sxs-lookup"><span data-stu-id="45468-160">-Credential</span></span>

<span data-ttu-id="45468-161">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="45468-161">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="45468-162">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="45468-162">The default is the current user.</span></span>

<span data-ttu-id="45468-163">Ange ett användar namn, till exempel **user01** eller **Domain01\User01**.</span><span class="sxs-lookup"><span data-stu-id="45468-163">Type a user name, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="45468-164">Eller ange ett **PSCredential** -objekt, till exempel ett från `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="45468-164">Or, enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="45468-165">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="45468-165">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="45468-166">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="45468-166">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-167">-DeliveryNotificationOption</span><span class="sxs-lookup"><span data-stu-id="45468-167">-DeliveryNotificationOption</span></span>

<span data-ttu-id="45468-168">Anger alternativ för leverans meddelande för e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="45468-168">Specifies the delivery notification options for the email message.</span></span> <span data-ttu-id="45468-169">Du kan ange flera värden.</span><span class="sxs-lookup"><span data-stu-id="45468-169">You can specify multiple values.</span></span>
<span data-ttu-id="45468-170">Inget värde är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="45468-170">None is the default value.</span></span> <span data-ttu-id="45468-171">Aliaset för den här parametern är **DNO**.</span><span class="sxs-lookup"><span data-stu-id="45468-171">The alias for this parameter is **DNO**.</span></span>

<span data-ttu-id="45468-172">Leverans meddelandena skickas till adressen i **från** -parametern.</span><span class="sxs-lookup"><span data-stu-id="45468-172">The delivery notifications are sent to the address in the **From** parameter.</span></span>

<span data-ttu-id="45468-173">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="45468-173">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="45468-174">`None`: Ingen avisering.</span><span class="sxs-lookup"><span data-stu-id="45468-174">`None`: No notification.</span></span>
- <span data-ttu-id="45468-175">`OnSuccess`: Meddela om leveransen lyckades.</span><span class="sxs-lookup"><span data-stu-id="45468-175">`OnSuccess`: Notify if the delivery is successful.</span></span>
- <span data-ttu-id="45468-176">`OnFailure`: Meddela om leveransen Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="45468-176">`OnFailure`: Notify if the delivery is unsuccessful.</span></span>
- <span data-ttu-id="45468-177">`Delay`: Meddela om leveransen är försenad.</span><span class="sxs-lookup"><span data-stu-id="45468-177">`Delay`: Notify if the delivery is delayed.</span></span>
- <span data-ttu-id="45468-178">`Never`: Meddela aldrig.</span><span class="sxs-lookup"><span data-stu-id="45468-178">`Never`: Never notify.</span></span>

```yaml
Type: System.Net.Mail.DeliveryNotificationOptions
Parameter Sets: (All)
Aliases: DNO
Accepted values: None, OnSuccess, OnFailure, Delay, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-179">-Encoding</span><span class="sxs-lookup"><span data-stu-id="45468-179">-Encoding</span></span>

<span data-ttu-id="45468-180">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="45468-180">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="45468-181">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="45468-181">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="45468-182">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="45468-182">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="45468-183">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="45468-183">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="45468-184">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="45468-184">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="45468-185">`bigendianutf32`: Kodar i UTF-32-format med big-endian-dataordningen.</span><span class="sxs-lookup"><span data-stu-id="45468-185">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="45468-186">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="45468-186">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="45468-187">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="45468-187">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="45468-188">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="45468-188">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="45468-189">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="45468-189">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="45468-190">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="45468-190">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="45468-191">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="45468-191">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="45468-192">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="45468-192">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="45468-193">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="45468-193">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="45468-194">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="45468-194">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases: BE
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-195">– Från</span><span class="sxs-lookup"><span data-stu-id="45468-195">-From</span></span>

<span data-ttu-id="45468-196">Parametern **from** måste anges.</span><span class="sxs-lookup"><span data-stu-id="45468-196">The **From** parameter is required.</span></span> <span data-ttu-id="45468-197">Den här parametern anger avsändarens e-postadress.</span><span class="sxs-lookup"><span data-stu-id="45468-197">This parameter specifies the sender's email address.</span></span> <span data-ttu-id="45468-198">Ange ett namn (valfritt) och en e-postadress, till exempel `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="45468-198">Enter a name (optional) and email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-199">-Port</span><span class="sxs-lookup"><span data-stu-id="45468-199">-Port</span></span>

<span data-ttu-id="45468-200">Anger en alternativ port på SMTP-servern.</span><span class="sxs-lookup"><span data-stu-id="45468-200">Specifies an alternate port on the SMTP server.</span></span> <span data-ttu-id="45468-201">Standardvärdet är 25, vilket är standard-SMTP-porten.</span><span class="sxs-lookup"><span data-stu-id="45468-201">The default value is 25, which is the default SMTP port.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 25
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-202">-Prioritet</span><span class="sxs-lookup"><span data-stu-id="45468-202">-Priority</span></span>

<span data-ttu-id="45468-203">Anger e-postmeddelandets prioritet.</span><span class="sxs-lookup"><span data-stu-id="45468-203">Specifies the priority of the email message.</span></span> <span data-ttu-id="45468-204">Normal är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="45468-204">Normal is the default.</span></span> <span data-ttu-id="45468-205">De acceptabla värdena för den här parametern är normal, hög och låg.</span><span class="sxs-lookup"><span data-stu-id="45468-205">The acceptable values for this parameter are Normal, High, and Low.</span></span>

```yaml
Type: System.Net.Mail.MailPriority
Parameter Sets: (All)
Aliases:
Accepted values: Normal, High, Low

Required: False
Position: Named
Default value: Normal
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-206">-ReplyTo</span><span class="sxs-lookup"><span data-stu-id="45468-206">-ReplyTo</span></span>

<span data-ttu-id="45468-207">Anger ytterligare e-postadresser (förutom från-adressen) som ska användas för att svara på det här meddelandet.</span><span class="sxs-lookup"><span data-stu-id="45468-207">Specifies additional email addresses (other than the From address) to use to reply to this message.</span></span>
<span data-ttu-id="45468-208">Ange namn (valfritt) och e-postadressen, till exempel `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="45468-208">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

<span data-ttu-id="45468-209">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="45468-209">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-210">-SmtpServer</span><span class="sxs-lookup"><span data-stu-id="45468-210">-SmtpServer</span></span>

<span data-ttu-id="45468-211">Anger namnet på den SMTP-server som skickar e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="45468-211">Specifies the name of the SMTP server that sends the email message.</span></span>

<span data-ttu-id="45468-212">Standardvärdet är värdet för Preference- `$PSEmailServer` variabeln.</span><span class="sxs-lookup"><span data-stu-id="45468-212">The default value is the value of the `$PSEmailServer` preference variable.</span></span> <span data-ttu-id="45468-213">Om Preference-variabeln inte har angetts och den här parametern inte används, `Send-MailMessage` Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="45468-213">If the preference variable is not set and this parameter is not used, the `Send-MailMessage` command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ComputerName

Required: False
Position: 3
Default value: $PSEmailServer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-214">-Subject</span><span class="sxs-lookup"><span data-stu-id="45468-214">-Subject</span></span>

<span data-ttu-id="45468-215">**Ämnes** parametern är inte obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="45468-215">The **Subject** parameter isn't required.</span></span> <span data-ttu-id="45468-216">Den här parametern anger ämnet för e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="45468-216">This parameter specifies the subject of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sub

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-217">-Till</span><span class="sxs-lookup"><span data-stu-id="45468-217">-To</span></span>

<span data-ttu-id="45468-218">Parametern **to** måste anges.</span><span class="sxs-lookup"><span data-stu-id="45468-218">The **To** parameter is required.</span></span> <span data-ttu-id="45468-219">Den här parametern anger mottagarens e-postadress.</span><span class="sxs-lookup"><span data-stu-id="45468-219">This parameter specifies the recipient's email address.</span></span> <span data-ttu-id="45468-220">Om det finns flera mottagare avgränsar du deras adresser med kommatecken ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="45468-220">If there are multiple recipients, separate their addresses with a comma (`,`).</span></span> <span data-ttu-id="45468-221">Ange namn (valfritt) och e-postadressen, till exempel `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="45468-221">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-222">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="45468-222">-UseSsl</span></span>

<span data-ttu-id="45468-223">Secure Sockets Layer-protokollet (SSL) används för att upprätta en säker anslutning till fjärrdatorn för att skicka e-post.</span><span class="sxs-lookup"><span data-stu-id="45468-223">The Secure Sockets Layer (SSL) protocol is used to establish a secure connection to the remote computer to send mail.</span></span> <span data-ttu-id="45468-224">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="45468-224">By default, SSL is not used.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45468-225">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="45468-225">CommonParameters</span></span>

<span data-ttu-id="45468-226">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="45468-226">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="45468-227">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="45468-227">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="45468-228">INDATA</span><span class="sxs-lookup"><span data-stu-id="45468-228">INPUTS</span></span>

### <span data-ttu-id="45468-229">System. String</span><span class="sxs-lookup"><span data-stu-id="45468-229">System.String</span></span>

<span data-ttu-id="45468-230">Du kan skicka vidare sökvägen och fil namnen för bilagor till `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="45468-230">You can pipe the path and file names of attachments to `Send-MailMessage`.</span></span>

## <span data-ttu-id="45468-231">UTDATA</span><span class="sxs-lookup"><span data-stu-id="45468-231">OUTPUTS</span></span>

### <span data-ttu-id="45468-232">Inga</span><span class="sxs-lookup"><span data-stu-id="45468-232">None</span></span>

<span data-ttu-id="45468-233">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="45468-233">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="45468-234">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="45468-234">NOTES</span></span>

## <span data-ttu-id="45468-235">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="45468-235">RELATED LINKS</span></span>

[<span data-ttu-id="45468-236">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="45468-236">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="45468-237">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="45468-237">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

