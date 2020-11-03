---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Send-MailMessage
ms.openlocfilehash: 6f98c95e6c0144f76393e9d28454833097894512
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264861"
---
# <span data-ttu-id="14396-103">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="14396-103">Send-MailMessage</span></span>

## <span data-ttu-id="14396-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="14396-104">SYNOPSIS</span></span>
<span data-ttu-id="14396-105">Skickar ett e-postmeddelande.</span><span class="sxs-lookup"><span data-stu-id="14396-105">Sends an email message.</span></span>

## <span data-ttu-id="14396-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="14396-106">SYNTAX</span></span>

### <span data-ttu-id="14396-107">Alla</span><span class="sxs-lookup"><span data-stu-id="14396-107">All</span></span>

```
Send-MailMessage [-To] <string[]> [-Subject] <string> [[-Body] <string>] [[-SmtpServer] <string>]
 -From <string> [-Attachments <string[]>] [-Bcc <string[]>] [-BodyAsHtml] [-Encoding <Encoding>]
 [-Cc <string[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 [-Priority <MailPriority>] [-Credential <pscredential>] [-UseSsl] [-Port <int>]
 [<CommonParameters>]
```

## <span data-ttu-id="14396-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="14396-108">DESCRIPTION</span></span>

<span data-ttu-id="14396-109">`Send-MailMessage`Cmdleten skickar ett e-postmeddelande inifrån PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14396-109">The `Send-MailMessage` cmdlet sends an email message from within PowerShell.</span></span>

<span data-ttu-id="14396-110">Du måste ange en Simple Mail Transfer Protocol-server (SMTP) eller `Send-MailMessage` kommandot fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="14396-110">You must specify a Simple Mail Transfer Protocol (SMTP) server or the `Send-MailMessage` command fails.</span></span> <span data-ttu-id="14396-111">Använd parametern **SmtpServer** eller Ställ in `$PSEmailServer` variabeln på en giltig SMTP-server.</span><span class="sxs-lookup"><span data-stu-id="14396-111">Use the **SmtpServer** parameter or set the `$PSEmailServer` variable to a valid SMTP server.</span></span>
<span data-ttu-id="14396-112">Värdet som tilldelas `$PSEmailServer` är standard SMTP-inställningen för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14396-112">The value assigned to `$PSEmailServer` is the default SMTP setting for PowerShell.</span></span> <span data-ttu-id="14396-113">Mer information finns i [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="14396-113">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

> [!WARNING]
> <span data-ttu-id="14396-114">`Send-MailMessage`Cmdleten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="14396-114">The `Send-MailMessage` cmdlet is obsolete.</span></span> <span data-ttu-id="14396-115">Denna cmdlet garanterar inte säkra anslutningar till SMTP-servrar.</span><span class="sxs-lookup"><span data-stu-id="14396-115">This cmdlet does not guarantee secure connections to SMTP servers.</span></span> <span data-ttu-id="14396-116">Det finns ingen omedelbar ersättning tillgänglig i PowerShell, men vi rekommenderar att du inte använder `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="14396-116">While there is no immediate replacement available in PowerShell, we recommend you do not use `Send-MailMessage`.</span></span> <span data-ttu-id="14396-117">Mer information finns i [Platform Compatibility NOTE DE0005](https://aka.ms/SendMailMessage).</span><span class="sxs-lookup"><span data-stu-id="14396-117">For more information, see [Platform Compatibility note DE0005](https://aka.ms/SendMailMessage).</span></span>

## <span data-ttu-id="14396-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="14396-118">EXAMPLES</span></span>

### <span data-ttu-id="14396-119">Exempel 1: Skicka ett e-postmeddelande från en person till en annan person</span><span class="sxs-lookup"><span data-stu-id="14396-119">Example 1: Send an email from one person to another person</span></span>

<span data-ttu-id="14396-120">I det här exemplet skickas ett e-postmeddelande från en person till en annan person.</span><span class="sxs-lookup"><span data-stu-id="14396-120">This example sends an email message from one person to another person.</span></span>

<span data-ttu-id="14396-121">Parametrarna **from** , **to** och **subject** krävs av `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="14396-121">The **From** , **To** , and **Subject** parameters are required by `Send-MailMessage`.</span></span> <span data-ttu-id="14396-122">I det här exemplet används standard `$PSEmailServer` variabeln för SMTP-servern, så **SmtpServer** -parametern behövs inte.</span><span class="sxs-lookup"><span data-stu-id="14396-122">This example uses the default `$PSEmailServer` variable for the SMTP server, so the **SmtpServer** parameter is not needed.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

<span data-ttu-id="14396-123">`Send-MailMessage`Cmdleten använder parametern **from** för att ange meddelandets avsändare.</span><span class="sxs-lookup"><span data-stu-id="14396-123">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="14396-124">Parametern **to** anger meddelandets mottagare.</span><span class="sxs-lookup"><span data-stu-id="14396-124">The **To** parameter specifies the message's recipient.</span></span> <span data-ttu-id="14396-125">**Ämnes** parametern använder text strängen **Testa e-post** som meddelandet eftersom den valfria **text** parametern inte ingår.</span><span class="sxs-lookup"><span data-stu-id="14396-125">The **Subject** parameter uses the text string **Test mail** as the message because the optional **Body** parameter is not included.</span></span>

### <span data-ttu-id="14396-126">Exempel 2: skicka en bifogad fil</span><span class="sxs-lookup"><span data-stu-id="14396-126">Example 2: Send an attachment</span></span>

<span data-ttu-id="14396-127">Det här exemplet skickar ett e-postmeddelande med en bifogad fil.</span><span class="sxs-lookup"><span data-stu-id="14396-127">This example sends an email message with an attachment.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

<span data-ttu-id="14396-128">`Send-MailMessage`Cmdleten använder parametern **from** för att ange meddelandets avsändare.</span><span class="sxs-lookup"><span data-stu-id="14396-128">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="14396-129">Parametern **to** anger meddelandets mottagare.</span><span class="sxs-lookup"><span data-stu-id="14396-129">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="14396-130">**Ämnes** parametern beskriver meddelandets innehåll.</span><span class="sxs-lookup"><span data-stu-id="14396-130">The **Subject** parameter describes the content of the message.</span></span> <span data-ttu-id="14396-131">**Body** -parametern är meddelandets innehåll.</span><span class="sxs-lookup"><span data-stu-id="14396-131">The **Body** parameter is the content of the message.</span></span>

<span data-ttu-id="14396-132">Parametern **Attachments** anger filen i den aktuella katalogen som är kopplad till e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="14396-132">The **Attachments** parameter specifies the file in the current directory that is attached to the email message.</span></span> <span data-ttu-id="14396-133">**Prioritets** parametern anger meddelandet till **hög** prioritet.</span><span class="sxs-lookup"><span data-stu-id="14396-133">The **Priority** parameter sets the message to **High** priority.</span></span> <span data-ttu-id="14396-134">Parametern **-DeliveryNotificationOption** anger två värden, **OnSuccess** och **onFailure**.</span><span class="sxs-lookup"><span data-stu-id="14396-134">The **-DeliveryNotificationOption** parameter specifies two values, **OnSuccess** and **OnFailure**.</span></span> <span data-ttu-id="14396-135">Avsändaren får e-postaviseringar för att bekräfta att meddelande leveransen har lyckats eller misslyckats.</span><span class="sxs-lookup"><span data-stu-id="14396-135">The sender will receive email notifications to confirm the success or failure of the message delivery.</span></span>
<span data-ttu-id="14396-136">Parametern **SmtpServer** anger SMTP-servern till **SMTP.fabrikam.com**.</span><span class="sxs-lookup"><span data-stu-id="14396-136">The **SmtpServer** parameter sets the SMTP server to **smtp.fabrikam.com**.</span></span>

### <span data-ttu-id="14396-137">Exempel 3: skicka e-post till en distributions lista</span><span class="sxs-lookup"><span data-stu-id="14396-137">Example 3: Send email to a mailing list</span></span>

<span data-ttu-id="14396-138">Det här exemplet skickar ett e-postmeddelande till en distributions lista.</span><span class="sxs-lookup"><span data-stu-id="14396-138">This example sends an email message to a mailing list.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

<span data-ttu-id="14396-139">`Send-MailMessage`Cmdleten använder parametern **from** för att ange meddelandets avsändare.</span><span class="sxs-lookup"><span data-stu-id="14396-139">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="14396-140">Parametern **to** anger meddelandets mottagare.</span><span class="sxs-lookup"><span data-stu-id="14396-140">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="14396-141">Parametern **CC** skickar en kopia av meddelandet till den angivna mottagaren.</span><span class="sxs-lookup"><span data-stu-id="14396-141">The **Cc** parameter sends a copy of the message to the specified recipient.</span></span> <span data-ttu-id="14396-142">Parametern **hemlig** kopia skickar en hemlig kopia av meddelandet.</span><span class="sxs-lookup"><span data-stu-id="14396-142">The **Bcc** parameter sends a blind copy of the message.</span></span> <span data-ttu-id="14396-143">En hemlig kopia är en e-postadress som är dold från de andra mottagarna.</span><span class="sxs-lookup"><span data-stu-id="14396-143">A blind copy is an email address that is hidden from the other recipients.</span></span> <span data-ttu-id="14396-144">**Subject** -parametern är meddelandet eftersom den valfria **text** parametern inte ingår.</span><span class="sxs-lookup"><span data-stu-id="14396-144">The **Subject** parameter is the message because the optional **Body** parameter is not included.</span></span>

<span data-ttu-id="14396-145">Parametern **Credential** anger en domän administratörs autentiseringsuppgifter som används för att skicka meddelandet.</span><span class="sxs-lookup"><span data-stu-id="14396-145">The **Credential** parameter specifies a domain administrator's credentials are used to send the message.</span></span> <span data-ttu-id="14396-146">Parametern **UseSsl** anger att SSL (Secure Socket Layer) skapar en säker anslutning.</span><span class="sxs-lookup"><span data-stu-id="14396-146">The **UseSsl** parameter specifies that Secure Socket Layer (SSL) creates a secure connection.</span></span>

## <span data-ttu-id="14396-147">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="14396-147">PARAMETERS</span></span>

### <span data-ttu-id="14396-148">-Bilagor</span><span class="sxs-lookup"><span data-stu-id="14396-148">-Attachments</span></span>

<span data-ttu-id="14396-149">Anger sökväg och fil namn för de filer som ska bifogas i e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="14396-149">Specifies the path and file names of files to be attached to the email message.</span></span> <span data-ttu-id="14396-150">Du kan använda den här parametern eller Ange sökvägar och fil namn till `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="14396-150">You can use this parameter or pipe the paths and file names to `Send-MailMessage`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PsPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="14396-151">– Hemlig kopia</span><span class="sxs-lookup"><span data-stu-id="14396-151">-Bcc</span></span>

<span data-ttu-id="14396-152">Anger e-postadresserna som får en kopia av e-postmeddelandet men som inte visas som mottagare av meddelandet.</span><span class="sxs-lookup"><span data-stu-id="14396-152">Specifies the email addresses that receive a copy of the mail but are not listed as recipients of the message.</span></span> <span data-ttu-id="14396-153">Ange namn (valfritt) och e-postadressen, till exempel `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="14396-153">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

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

### <span data-ttu-id="14396-154">-Body</span><span class="sxs-lookup"><span data-stu-id="14396-154">-Body</span></span>

<span data-ttu-id="14396-155">Anger e-postmeddelandets innehåll.</span><span class="sxs-lookup"><span data-stu-id="14396-155">Specifies the content of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14396-156">-BodyAsHtml</span><span class="sxs-lookup"><span data-stu-id="14396-156">-BodyAsHtml</span></span>

<span data-ttu-id="14396-157">Anger att värdet för **text** parametern innehåller HTML.</span><span class="sxs-lookup"><span data-stu-id="14396-157">Specifies that the value of the **Body** parameter contains HTML.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: BAH

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14396-158">-CC</span><span class="sxs-lookup"><span data-stu-id="14396-158">-Cc</span></span>

<span data-ttu-id="14396-159">Anger e-postadresserna som en kopia av e-postmeddelandet skickas till.</span><span class="sxs-lookup"><span data-stu-id="14396-159">Specifies the email addresses to which a carbon copy (CC) of the email message is sent.</span></span> <span data-ttu-id="14396-160">Ange namn (valfritt) och e-postadressen, till exempel `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="14396-160">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

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

### <span data-ttu-id="14396-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="14396-161">-Credential</span></span>

<span data-ttu-id="14396-162">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="14396-162">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="14396-163">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="14396-163">The default is the current user.</span></span>

<span data-ttu-id="14396-164">Ange ett användar namn, till exempel **user01** eller **Domain01\User01**.</span><span class="sxs-lookup"><span data-stu-id="14396-164">Type a user name, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="14396-165">Eller ange ett **PSCredential** -objekt, till exempel ett från `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="14396-165">Or, enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="14396-166">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="14396-166">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="14396-167">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="14396-167">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14396-168">-DeliveryNotificationOption</span><span class="sxs-lookup"><span data-stu-id="14396-168">-DeliveryNotificationOption</span></span>

<span data-ttu-id="14396-169">Anger alternativ för leverans meddelande för e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="14396-169">Specifies the delivery notification options for the email message.</span></span> <span data-ttu-id="14396-170">Du kan ange flera värden.</span><span class="sxs-lookup"><span data-stu-id="14396-170">You can specify multiple values.</span></span>
<span data-ttu-id="14396-171">Inget värde är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="14396-171">None is the default value.</span></span> <span data-ttu-id="14396-172">Aliaset för den här parametern är **DNO**.</span><span class="sxs-lookup"><span data-stu-id="14396-172">The alias for this parameter is **DNO**.</span></span>

<span data-ttu-id="14396-173">Leverans meddelandena skickas till adressen i **från** -parametern.</span><span class="sxs-lookup"><span data-stu-id="14396-173">The delivery notifications are sent to the address in the **From** parameter.</span></span>

<span data-ttu-id="14396-174">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="14396-174">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="14396-175">`None`: Ingen avisering.</span><span class="sxs-lookup"><span data-stu-id="14396-175">`None`: No notification.</span></span>
- <span data-ttu-id="14396-176">`OnSuccess`: Meddela om leveransen lyckades.</span><span class="sxs-lookup"><span data-stu-id="14396-176">`OnSuccess`: Notify if the delivery is successful.</span></span>
- <span data-ttu-id="14396-177">`OnFailure`: Meddela om leveransen Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="14396-177">`OnFailure`: Notify if the delivery is unsuccessful.</span></span>
- <span data-ttu-id="14396-178">`Delay`: Meddela om leveransen är försenad.</span><span class="sxs-lookup"><span data-stu-id="14396-178">`Delay`: Notify if the delivery is delayed.</span></span>
- <span data-ttu-id="14396-179">`Never`: Meddela aldrig.</span><span class="sxs-lookup"><span data-stu-id="14396-179">`Never`: Never notify.</span></span>

```yaml
Type: System.Net.Mail.DeliveryNotificationOptions
Parameter Sets: (All)
Aliases: DNO
Accepted values: None, OnSuccess, OnFailure, Delay, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14396-180">-Encoding</span><span class="sxs-lookup"><span data-stu-id="14396-180">-Encoding</span></span>

<span data-ttu-id="14396-181">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="14396-181">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="14396-182">Standardvärdet är `Default`.</span><span class="sxs-lookup"><span data-stu-id="14396-182">The default value is `Default`.</span></span>

<span data-ttu-id="14396-183">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="14396-183">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="14396-184">`ASCII` Använder ASCII-teckenuppsättning (7-bitars).</span><span class="sxs-lookup"><span data-stu-id="14396-184">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="14396-185">`BigEndianUnicode` Använder UTF-16 med big-endian byte-ordningen.</span><span class="sxs-lookup"><span data-stu-id="14396-185">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="14396-186">`Default` Använder kodningen som motsvarar systemets aktiva tecken tabell (vanligt vis ANSI).</span><span class="sxs-lookup"><span data-stu-id="14396-186">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="14396-187">`OEM` Använder kodningen som motsvarar systemets aktuella OEM Code-sida.</span><span class="sxs-lookup"><span data-stu-id="14396-187">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="14396-188">`Unicode` Använder UTF-16 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="14396-188">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="14396-189">`UTF7` Använder UTF-7.</span><span class="sxs-lookup"><span data-stu-id="14396-189">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="14396-190">`UTF8` Använder UTF-8.</span><span class="sxs-lookup"><span data-stu-id="14396-190">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="14396-191">`UTF32` Använder UTF-32 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="14396-191">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases: BE
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14396-192">– Från</span><span class="sxs-lookup"><span data-stu-id="14396-192">-From</span></span>

<span data-ttu-id="14396-193">Parametern **from** måste anges.</span><span class="sxs-lookup"><span data-stu-id="14396-193">The **From** parameter is required.</span></span> <span data-ttu-id="14396-194">Den här parametern anger avsändarens e-postadress.</span><span class="sxs-lookup"><span data-stu-id="14396-194">This parameter specifies the sender's email address.</span></span> <span data-ttu-id="14396-195">Ange ett namn (valfritt) och en e-postadress, till exempel `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="14396-195">Enter a name (optional) and email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14396-196">-Port</span><span class="sxs-lookup"><span data-stu-id="14396-196">-Port</span></span>

<span data-ttu-id="14396-197">Anger en alternativ port på SMTP-servern.</span><span class="sxs-lookup"><span data-stu-id="14396-197">Specifies an alternate port on the SMTP server.</span></span> <span data-ttu-id="14396-198">Standardvärdet är 25, vilket är standard-SMTP-porten.</span><span class="sxs-lookup"><span data-stu-id="14396-198">The default value is 25, which is the default SMTP port.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 25
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14396-199">-Prioritet</span><span class="sxs-lookup"><span data-stu-id="14396-199">-Priority</span></span>

<span data-ttu-id="14396-200">Anger e-postmeddelandets prioritet.</span><span class="sxs-lookup"><span data-stu-id="14396-200">Specifies the priority of the email message.</span></span> <span data-ttu-id="14396-201">Normal är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="14396-201">Normal is the default.</span></span> <span data-ttu-id="14396-202">De acceptabla värdena för den här parametern är normal, hög och låg.</span><span class="sxs-lookup"><span data-stu-id="14396-202">The acceptable values for this parameter are Normal, High, and Low.</span></span>

```yaml
Type: System.Net.Mail.MailPriority
Parameter Sets: (All)
Aliases:
Accepted values: Normal, High, Low

Required: False
Position: Named
Default value: Normal
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14396-203">-SmtpServer</span><span class="sxs-lookup"><span data-stu-id="14396-203">-SmtpServer</span></span>

<span data-ttu-id="14396-204">Anger namnet på den SMTP-server som skickar e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="14396-204">Specifies the name of the SMTP server that sends the email message.</span></span>

<span data-ttu-id="14396-205">Standardvärdet är värdet för Preference- `$PSEmailServer` variabeln.</span><span class="sxs-lookup"><span data-stu-id="14396-205">The default value is the value of the `$PSEmailServer` preference variable.</span></span> <span data-ttu-id="14396-206">Om Preference-variabeln inte har angetts och den här parametern inte används, `Send-MailMessage` Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="14396-206">If the preference variable is not set and this parameter is not used, the `Send-MailMessage` command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ComputerName

Required: False
Position: 3
Default value: $PSEmailServer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14396-207">-Subject</span><span class="sxs-lookup"><span data-stu-id="14396-207">-Subject</span></span>

<span data-ttu-id="14396-208">**Ämnes** parametern måste anges.</span><span class="sxs-lookup"><span data-stu-id="14396-208">The **Subject** parameter is required.</span></span> <span data-ttu-id="14396-209">Den här parametern anger ämnet för e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="14396-209">This parameter specifies the subject of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sub

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14396-210">-Till</span><span class="sxs-lookup"><span data-stu-id="14396-210">-To</span></span>

<span data-ttu-id="14396-211">Parametern **to** måste anges.</span><span class="sxs-lookup"><span data-stu-id="14396-211">The **To** parameter is required.</span></span> <span data-ttu-id="14396-212">Den här parametern anger mottagarens e-postadress.</span><span class="sxs-lookup"><span data-stu-id="14396-212">This parameter specifies the recipient's email address.</span></span> <span data-ttu-id="14396-213">Om det finns flera mottagare avgränsar du deras adresser med kommatecken ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="14396-213">If there are multiple recipients, separate their addresses with a comma (`,`).</span></span> <span data-ttu-id="14396-214">Ange namn (valfritt) och e-postadressen, till exempel `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="14396-214">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14396-215">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="14396-215">-UseSsl</span></span>

<span data-ttu-id="14396-216">Secure Sockets Layer-protokollet (SSL) används för att upprätta en säker anslutning till fjärrdatorn för att skicka e-post.</span><span class="sxs-lookup"><span data-stu-id="14396-216">The Secure Sockets Layer (SSL) protocol is used to establish a secure connection to the remote computer to send mail.</span></span> <span data-ttu-id="14396-217">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="14396-217">By default, SSL is not used.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14396-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="14396-218">CommonParameters</span></span>

<span data-ttu-id="14396-219">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="14396-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="14396-220">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="14396-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="14396-221">INDATA</span><span class="sxs-lookup"><span data-stu-id="14396-221">INPUTS</span></span>

### <span data-ttu-id="14396-222">System. String</span><span class="sxs-lookup"><span data-stu-id="14396-222">System.String</span></span>

<span data-ttu-id="14396-223">Du kan skicka vidare sökvägen och fil namnen för bilagor till `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="14396-223">You can pipe the path and file names of attachments to `Send-MailMessage`.</span></span>

## <span data-ttu-id="14396-224">UTDATA</span><span class="sxs-lookup"><span data-stu-id="14396-224">OUTPUTS</span></span>

### <span data-ttu-id="14396-225">Inget</span><span class="sxs-lookup"><span data-stu-id="14396-225">None</span></span>

<span data-ttu-id="14396-226">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="14396-226">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="14396-227">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="14396-227">NOTES</span></span>

## <span data-ttu-id="14396-228">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="14396-228">RELATED LINKS</span></span>

[<span data-ttu-id="14396-229">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="14396-229">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="14396-230">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="14396-230">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)
