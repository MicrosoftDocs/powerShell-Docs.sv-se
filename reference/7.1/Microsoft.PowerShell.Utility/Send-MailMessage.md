---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Send-MailMessage
ms.openlocfilehash: e100189b6c7fa128c373d9f2b9e1d6029162c0ed
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263468"
---
# <span data-ttu-id="5769f-103">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="5769f-103">Send-MailMessage</span></span>

## <span data-ttu-id="5769f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5769f-104">SYNOPSIS</span></span>
<span data-ttu-id="5769f-105">Skickar ett e-postmeddelande.</span><span class="sxs-lookup"><span data-stu-id="5769f-105">Sends an email message.</span></span>

## <span data-ttu-id="5769f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5769f-106">SYNTAX</span></span>

### <span data-ttu-id="5769f-107">Alla</span><span class="sxs-lookup"><span data-stu-id="5769f-107">All</span></span>

```
Send-MailMessage [-Attachments <String[]>] [-Bcc <String[]>] [[-Body] <String>] [-BodyAsHtml]
 [-Encoding <Encoding>] [-Cc <String[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 -From <String> [[-SmtpServer] <String>] [-Priority <MailPriority>] [-ReplyTo <String[]>]
 [[-Subject] <String>] [-To] <String[]> [-Credential <PSCredential>] [-UseSsl] [-Port <Int32>]
 [<CommonParameters>]
```

## <span data-ttu-id="5769f-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5769f-108">DESCRIPTION</span></span>

<span data-ttu-id="5769f-109">`Send-MailMessage`Cmdleten skickar ett e-postmeddelande inifrån PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5769f-109">The `Send-MailMessage` cmdlet sends an email message from within PowerShell.</span></span>

<span data-ttu-id="5769f-110">Du måste ange en Simple Mail Transfer Protocol-server (SMTP) eller `Send-MailMessage` kommandot fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="5769f-110">You must specify a Simple Mail Transfer Protocol (SMTP) server or the `Send-MailMessage` command fails.</span></span> <span data-ttu-id="5769f-111">Använd parametern **SmtpServer** eller Ställ in `$PSEmailServer` variabeln på en giltig SMTP-server.</span><span class="sxs-lookup"><span data-stu-id="5769f-111">Use the **SmtpServer** parameter or set the `$PSEmailServer` variable to a valid SMTP server.</span></span>
<span data-ttu-id="5769f-112">Värdet som tilldelas `$PSEmailServer` är standard SMTP-inställningen för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5769f-112">The value assigned to `$PSEmailServer` is the default SMTP setting for PowerShell.</span></span> <span data-ttu-id="5769f-113">Mer information finns i [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="5769f-113">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

> [!WARNING]
> <span data-ttu-id="5769f-114">`Send-MailMessage`Cmdleten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="5769f-114">The `Send-MailMessage` cmdlet is obsolete.</span></span> <span data-ttu-id="5769f-115">Denna cmdlet garanterar inte säkra anslutningar till SMTP-servrar.</span><span class="sxs-lookup"><span data-stu-id="5769f-115">This cmdlet does not guarantee secure connections to SMTP servers.</span></span> <span data-ttu-id="5769f-116">Det finns ingen omedelbar ersättning tillgänglig i PowerShell, men vi rekommenderar att du inte använder `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="5769f-116">While there is no immediate replacement available in PowerShell, we recommend you do not use `Send-MailMessage`.</span></span> <span data-ttu-id="5769f-117">Mer information finns i [Platform Compatibility NOTE DE0005](https://aka.ms/SendMailMessage).</span><span class="sxs-lookup"><span data-stu-id="5769f-117">For more information, see [Platform Compatibility note DE0005](https://aka.ms/SendMailMessage).</span></span>

## <span data-ttu-id="5769f-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5769f-118">EXAMPLES</span></span>

### <span data-ttu-id="5769f-119">Exempel 1: Skicka ett e-postmeddelande från en person till en annan person</span><span class="sxs-lookup"><span data-stu-id="5769f-119">Example 1: Send an email from one person to another person</span></span>

<span data-ttu-id="5769f-120">I det här exemplet skickas ett e-postmeddelande från en person till en annan person.</span><span class="sxs-lookup"><span data-stu-id="5769f-120">This example sends an email message from one person to another person.</span></span>

<span data-ttu-id="5769f-121">Parametrarna **from** , **to** och **subject** krävs av `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="5769f-121">The **From** , **To** , and **Subject** parameters are required by `Send-MailMessage`.</span></span> <span data-ttu-id="5769f-122">I det här exemplet används standard `$PSEmailServer` variabeln för SMTP-servern, så **SmtpServer** -parametern behövs inte.</span><span class="sxs-lookup"><span data-stu-id="5769f-122">This example uses the default `$PSEmailServer` variable for the SMTP server, so the **SmtpServer** parameter is not needed.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

<span data-ttu-id="5769f-123">`Send-MailMessage`Cmdleten använder parametern **from** för att ange meddelandets avsändare.</span><span class="sxs-lookup"><span data-stu-id="5769f-123">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="5769f-124">Parametern **to** anger meddelandets mottagare.</span><span class="sxs-lookup"><span data-stu-id="5769f-124">The **To** parameter specifies the message's recipient.</span></span> <span data-ttu-id="5769f-125">**Ämnes** parametern använder text strängen **Testa e-post** som meddelandet eftersom den valfria **text** parametern inte ingår.</span><span class="sxs-lookup"><span data-stu-id="5769f-125">The **Subject** parameter uses the text string **Test mail** as the message because the optional **Body** parameter is not included.</span></span>

### <span data-ttu-id="5769f-126">Exempel 2: skicka en bifogad fil</span><span class="sxs-lookup"><span data-stu-id="5769f-126">Example 2: Send an attachment</span></span>

<span data-ttu-id="5769f-127">Det här exemplet skickar ett e-postmeddelande med en bifogad fil.</span><span class="sxs-lookup"><span data-stu-id="5769f-127">This example sends an email message with an attachment.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

<span data-ttu-id="5769f-128">`Send-MailMessage`Cmdleten använder parametern **from** för att ange meddelandets avsändare.</span><span class="sxs-lookup"><span data-stu-id="5769f-128">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="5769f-129">Parametern **to** anger meddelandets mottagare.</span><span class="sxs-lookup"><span data-stu-id="5769f-129">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="5769f-130">**Ämnes** parametern beskriver meddelandets innehåll.</span><span class="sxs-lookup"><span data-stu-id="5769f-130">The **Subject** parameter describes the content of the message.</span></span> <span data-ttu-id="5769f-131">**Body** -parametern är meddelandets innehåll.</span><span class="sxs-lookup"><span data-stu-id="5769f-131">The **Body** parameter is the content of the message.</span></span>

<span data-ttu-id="5769f-132">Parametern **Attachments** anger filen i den aktuella katalogen som är kopplad till e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="5769f-132">The **Attachments** parameter specifies the file in the current directory that is attached to the email message.</span></span> <span data-ttu-id="5769f-133">**Prioritets** parametern anger meddelandet till **hög** prioritet.</span><span class="sxs-lookup"><span data-stu-id="5769f-133">The **Priority** parameter sets the message to **High** priority.</span></span> <span data-ttu-id="5769f-134">Parametern **-DeliveryNotificationOption** anger två värden, **OnSuccess** och **onFailure**.</span><span class="sxs-lookup"><span data-stu-id="5769f-134">The **-DeliveryNotificationOption** parameter specifies two values, **OnSuccess** and **OnFailure**.</span></span> <span data-ttu-id="5769f-135">Avsändaren får e-postaviseringar för att bekräfta att meddelande leveransen har lyckats eller misslyckats.</span><span class="sxs-lookup"><span data-stu-id="5769f-135">The sender will receive email notifications to confirm the success or failure of the message delivery.</span></span>
<span data-ttu-id="5769f-136">Parametern **SmtpServer** anger SMTP-servern till **SMTP.fabrikam.com**.</span><span class="sxs-lookup"><span data-stu-id="5769f-136">The **SmtpServer** parameter sets the SMTP server to **smtp.fabrikam.com**.</span></span>

### <span data-ttu-id="5769f-137">Exempel 3: skicka e-post till en distributions lista</span><span class="sxs-lookup"><span data-stu-id="5769f-137">Example 3: Send email to a mailing list</span></span>

<span data-ttu-id="5769f-138">Det här exemplet skickar ett e-postmeddelande till en distributions lista.</span><span class="sxs-lookup"><span data-stu-id="5769f-138">This example sends an email message to a mailing list.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

<span data-ttu-id="5769f-139">`Send-MailMessage`Cmdleten använder parametern **from** för att ange meddelandets avsändare.</span><span class="sxs-lookup"><span data-stu-id="5769f-139">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="5769f-140">Parametern **to** anger meddelandets mottagare.</span><span class="sxs-lookup"><span data-stu-id="5769f-140">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="5769f-141">Parametern **CC** skickar en kopia av meddelandet till den angivna mottagaren.</span><span class="sxs-lookup"><span data-stu-id="5769f-141">The **Cc** parameter sends a copy of the message to the specified recipient.</span></span> <span data-ttu-id="5769f-142">Parametern **hemlig** kopia skickar en hemlig kopia av meddelandet.</span><span class="sxs-lookup"><span data-stu-id="5769f-142">The **Bcc** parameter sends a blind copy of the message.</span></span> <span data-ttu-id="5769f-143">En hemlig kopia är en e-postadress som är dold från de andra mottagarna.</span><span class="sxs-lookup"><span data-stu-id="5769f-143">A blind copy is an email address that is hidden from the other recipients.</span></span> <span data-ttu-id="5769f-144">**Subject** -parametern är meddelandet eftersom den valfria **text** parametern inte ingår.</span><span class="sxs-lookup"><span data-stu-id="5769f-144">The **Subject** parameter is the message because the optional **Body** parameter is not included.</span></span>

<span data-ttu-id="5769f-145">Parametern **Credential** anger en domän administratörs autentiseringsuppgifter som används för att skicka meddelandet.</span><span class="sxs-lookup"><span data-stu-id="5769f-145">The **Credential** parameter specifies a domain administrator's credentials are used to send the message.</span></span> <span data-ttu-id="5769f-146">Parametern **UseSsl** anger att SSL (Secure Socket Layer) skapar en säker anslutning.</span><span class="sxs-lookup"><span data-stu-id="5769f-146">The **UseSsl** parameter specifies that Secure Socket Layer (SSL) creates a secure connection.</span></span>

## <span data-ttu-id="5769f-147">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5769f-147">PARAMETERS</span></span>

### <span data-ttu-id="5769f-148">-Bilagor</span><span class="sxs-lookup"><span data-stu-id="5769f-148">-Attachments</span></span>

<span data-ttu-id="5769f-149">Anger sökväg och fil namn för de filer som ska bifogas i e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="5769f-149">Specifies the path and file names of files to be attached to the email message.</span></span> <span data-ttu-id="5769f-150">Du kan använda den här parametern eller Ange sökvägar och fil namn till `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="5769f-150">You can use this parameter or pipe the paths and file names to `Send-MailMessage`.</span></span>

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

### <span data-ttu-id="5769f-151">– Hemlig kopia</span><span class="sxs-lookup"><span data-stu-id="5769f-151">-Bcc</span></span>

<span data-ttu-id="5769f-152">Anger e-postadresserna som får en kopia av e-postmeddelandet men som inte visas som mottagare av meddelandet.</span><span class="sxs-lookup"><span data-stu-id="5769f-152">Specifies the email addresses that receive a copy of the mail but are not listed as recipients of the message.</span></span> <span data-ttu-id="5769f-153">Ange namn (valfritt) och e-postadressen, till exempel `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="5769f-153">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

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

### <span data-ttu-id="5769f-154">-Body</span><span class="sxs-lookup"><span data-stu-id="5769f-154">-Body</span></span>

<span data-ttu-id="5769f-155">Anger e-postmeddelandets innehåll.</span><span class="sxs-lookup"><span data-stu-id="5769f-155">Specifies the content of the email message.</span></span>

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

### <span data-ttu-id="5769f-156">-BodyAsHtml</span><span class="sxs-lookup"><span data-stu-id="5769f-156">-BodyAsHtml</span></span>

<span data-ttu-id="5769f-157">Anger att värdet för **text** parametern innehåller HTML.</span><span class="sxs-lookup"><span data-stu-id="5769f-157">Specifies that the value of the **Body** parameter contains HTML.</span></span>

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

### <span data-ttu-id="5769f-158">-CC</span><span class="sxs-lookup"><span data-stu-id="5769f-158">-Cc</span></span>

<span data-ttu-id="5769f-159">Anger e-postadresserna som en kopia av e-postmeddelandet skickas till.</span><span class="sxs-lookup"><span data-stu-id="5769f-159">Specifies the email addresses to which a carbon copy (CC) of the email message is sent.</span></span> <span data-ttu-id="5769f-160">Ange namn (valfritt) och e-postadressen, till exempel `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="5769f-160">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

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

### <span data-ttu-id="5769f-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="5769f-161">-Credential</span></span>

<span data-ttu-id="5769f-162">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="5769f-162">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="5769f-163">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="5769f-163">The default is the current user.</span></span>

<span data-ttu-id="5769f-164">Ange ett användar namn, till exempel **user01** eller **Domain01\User01**.</span><span class="sxs-lookup"><span data-stu-id="5769f-164">Type a user name, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="5769f-165">Eller ange ett **PSCredential** -objekt, till exempel ett från `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5769f-165">Or, enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="5769f-166">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="5769f-166">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="5769f-167">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="5769f-167">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="5769f-168">-DeliveryNotificationOption</span><span class="sxs-lookup"><span data-stu-id="5769f-168">-DeliveryNotificationOption</span></span>

<span data-ttu-id="5769f-169">Anger alternativ för leverans meddelande för e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="5769f-169">Specifies the delivery notification options for the email message.</span></span> <span data-ttu-id="5769f-170">Du kan ange flera värden.</span><span class="sxs-lookup"><span data-stu-id="5769f-170">You can specify multiple values.</span></span>
<span data-ttu-id="5769f-171">Inget värde är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="5769f-171">None is the default value.</span></span> <span data-ttu-id="5769f-172">Aliaset för den här parametern är **DNO**.</span><span class="sxs-lookup"><span data-stu-id="5769f-172">The alias for this parameter is **DNO**.</span></span>

<span data-ttu-id="5769f-173">Leverans meddelandena skickas till adressen i **från** -parametern.</span><span class="sxs-lookup"><span data-stu-id="5769f-173">The delivery notifications are sent to the address in the **From** parameter.</span></span>

<span data-ttu-id="5769f-174">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="5769f-174">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="5769f-175">`None`: Ingen avisering.</span><span class="sxs-lookup"><span data-stu-id="5769f-175">`None`: No notification.</span></span>
- <span data-ttu-id="5769f-176">`OnSuccess`: Meddela om leveransen lyckades.</span><span class="sxs-lookup"><span data-stu-id="5769f-176">`OnSuccess`: Notify if the delivery is successful.</span></span>
- <span data-ttu-id="5769f-177">`OnFailure`: Meddela om leveransen Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="5769f-177">`OnFailure`: Notify if the delivery is unsuccessful.</span></span>
- <span data-ttu-id="5769f-178">`Delay`: Meddela om leveransen är försenad.</span><span class="sxs-lookup"><span data-stu-id="5769f-178">`Delay`: Notify if the delivery is delayed.</span></span>
- <span data-ttu-id="5769f-179">`Never`: Meddela aldrig.</span><span class="sxs-lookup"><span data-stu-id="5769f-179">`Never`: Never notify.</span></span>

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

### <span data-ttu-id="5769f-180">-Encoding</span><span class="sxs-lookup"><span data-stu-id="5769f-180">-Encoding</span></span>

<span data-ttu-id="5769f-181">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="5769f-181">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="5769f-182">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="5769f-182">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="5769f-183">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="5769f-183">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="5769f-184">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="5769f-184">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="5769f-185">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="5769f-185">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="5769f-186">`bigendianutf32`: Kodar i UTF-32-format med big-endian-dataordningen.</span><span class="sxs-lookup"><span data-stu-id="5769f-186">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="5769f-187">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="5769f-187">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="5769f-188">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="5769f-188">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="5769f-189">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="5769f-189">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="5769f-190">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="5769f-190">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="5769f-191">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="5769f-191">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="5769f-192">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="5769f-192">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="5769f-193">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="5769f-193">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="5769f-194">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="5769f-194">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="5769f-195">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="5769f-195">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

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

### <span data-ttu-id="5769f-196">– Från</span><span class="sxs-lookup"><span data-stu-id="5769f-196">-From</span></span>

<span data-ttu-id="5769f-197">Parametern **from** måste anges.</span><span class="sxs-lookup"><span data-stu-id="5769f-197">The **From** parameter is required.</span></span> <span data-ttu-id="5769f-198">Den här parametern anger avsändarens e-postadress.</span><span class="sxs-lookup"><span data-stu-id="5769f-198">This parameter specifies the sender's email address.</span></span> <span data-ttu-id="5769f-199">Ange ett namn (valfritt) och en e-postadress, till exempel `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="5769f-199">Enter a name (optional) and email address, such as `Name <someone@fabrikam.com>`.</span></span>

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

### <span data-ttu-id="5769f-200">-Port</span><span class="sxs-lookup"><span data-stu-id="5769f-200">-Port</span></span>

<span data-ttu-id="5769f-201">Anger en alternativ port på SMTP-servern.</span><span class="sxs-lookup"><span data-stu-id="5769f-201">Specifies an alternate port on the SMTP server.</span></span> <span data-ttu-id="5769f-202">Standardvärdet är 25, vilket är standard-SMTP-porten.</span><span class="sxs-lookup"><span data-stu-id="5769f-202">The default value is 25, which is the default SMTP port.</span></span>

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

### <span data-ttu-id="5769f-203">-Prioritet</span><span class="sxs-lookup"><span data-stu-id="5769f-203">-Priority</span></span>

<span data-ttu-id="5769f-204">Anger e-postmeddelandets prioritet.</span><span class="sxs-lookup"><span data-stu-id="5769f-204">Specifies the priority of the email message.</span></span> <span data-ttu-id="5769f-205">Normal är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="5769f-205">Normal is the default.</span></span> <span data-ttu-id="5769f-206">De acceptabla värdena för den här parametern är normal, hög och låg.</span><span class="sxs-lookup"><span data-stu-id="5769f-206">The acceptable values for this parameter are Normal, High, and Low.</span></span>

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

### <span data-ttu-id="5769f-207">-ReplyTo</span><span class="sxs-lookup"><span data-stu-id="5769f-207">-ReplyTo</span></span>

<span data-ttu-id="5769f-208">Anger ytterligare e-postadresser (förutom från-adressen) som ska användas för att svara på det här meddelandet.</span><span class="sxs-lookup"><span data-stu-id="5769f-208">Specifies additional email addresses (other than the From address) to use to reply to this message.</span></span>
<span data-ttu-id="5769f-209">Ange namn (valfritt) och e-postadressen, till exempel `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="5769f-209">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

<span data-ttu-id="5769f-210">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="5769f-210">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="5769f-211">-SmtpServer</span><span class="sxs-lookup"><span data-stu-id="5769f-211">-SmtpServer</span></span>

<span data-ttu-id="5769f-212">Anger namnet på den SMTP-server som skickar e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="5769f-212">Specifies the name of the SMTP server that sends the email message.</span></span>

<span data-ttu-id="5769f-213">Standardvärdet är värdet för Preference- `$PSEmailServer` variabeln.</span><span class="sxs-lookup"><span data-stu-id="5769f-213">The default value is the value of the `$PSEmailServer` preference variable.</span></span> <span data-ttu-id="5769f-214">Om Preference-variabeln inte har angetts och den här parametern inte används, `Send-MailMessage` Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="5769f-214">If the preference variable is not set and this parameter is not used, the `Send-MailMessage` command fails.</span></span>

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

### <span data-ttu-id="5769f-215">-Subject</span><span class="sxs-lookup"><span data-stu-id="5769f-215">-Subject</span></span>

<span data-ttu-id="5769f-216">**Ämnes** parametern är inte obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="5769f-216">The **Subject** parameter isn't required.</span></span> <span data-ttu-id="5769f-217">Den här parametern anger ämnet för e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="5769f-217">This parameter specifies the subject of the email message.</span></span>

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

### <span data-ttu-id="5769f-218">-Till</span><span class="sxs-lookup"><span data-stu-id="5769f-218">-To</span></span>

<span data-ttu-id="5769f-219">Parametern **to** måste anges.</span><span class="sxs-lookup"><span data-stu-id="5769f-219">The **To** parameter is required.</span></span> <span data-ttu-id="5769f-220">Den här parametern anger mottagarens e-postadress.</span><span class="sxs-lookup"><span data-stu-id="5769f-220">This parameter specifies the recipient's email address.</span></span> <span data-ttu-id="5769f-221">Om det finns flera mottagare avgränsar du deras adresser med kommatecken ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="5769f-221">If there are multiple recipients, separate their addresses with a comma (`,`).</span></span> <span data-ttu-id="5769f-222">Ange namn (valfritt) och e-postadressen, till exempel `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="5769f-222">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

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

### <span data-ttu-id="5769f-223">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="5769f-223">-UseSsl</span></span>

<span data-ttu-id="5769f-224">Secure Sockets Layer-protokollet (SSL) används för att upprätta en säker anslutning till fjärrdatorn för att skicka e-post.</span><span class="sxs-lookup"><span data-stu-id="5769f-224">The Secure Sockets Layer (SSL) protocol is used to establish a secure connection to the remote computer to send mail.</span></span> <span data-ttu-id="5769f-225">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="5769f-225">By default, SSL is not used.</span></span>

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

### <span data-ttu-id="5769f-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5769f-226">CommonParameters</span></span>

<span data-ttu-id="5769f-227">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5769f-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5769f-228">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5769f-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5769f-229">INDATA</span><span class="sxs-lookup"><span data-stu-id="5769f-229">INPUTS</span></span>

### <span data-ttu-id="5769f-230">System. String</span><span class="sxs-lookup"><span data-stu-id="5769f-230">System.String</span></span>

<span data-ttu-id="5769f-231">Du kan skicka vidare sökvägen och fil namnen för bilagor till `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="5769f-231">You can pipe the path and file names of attachments to `Send-MailMessage`.</span></span>

## <span data-ttu-id="5769f-232">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5769f-232">OUTPUTS</span></span>

### <span data-ttu-id="5769f-233">Inget</span><span class="sxs-lookup"><span data-stu-id="5769f-233">None</span></span>

<span data-ttu-id="5769f-234">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5769f-234">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5769f-235">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5769f-235">NOTES</span></span>

## <span data-ttu-id="5769f-236">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5769f-236">RELATED LINKS</span></span>

[<span data-ttu-id="5769f-237">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="5769f-237">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="5769f-238">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="5769f-238">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)
