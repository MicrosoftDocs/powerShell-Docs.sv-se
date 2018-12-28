---
ms.date: 08/23/2017
keywords: PowerShell cmdlet
title: avinstallera windows powershell-webbåtkomst
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405453"
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="5514f-103">Avinstallera Windows PowerShell-webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="5514f-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="5514f-104">Uppdaterad: 24 juni 2013</span><span class="sxs-lookup"><span data-stu-id="5514f-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="5514f-105">Gäller för: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="5514f-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="5514f-106">Stegen i det här avsnittet Ta bort Windows PowerShell Web Access webbplats och motsvarande program från gateway-servern där den är installerad.</span><span class="sxs-lookup"><span data-stu-id="5514f-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="5514f-107">Meddela användare</span><span class="sxs-lookup"><span data-stu-id="5514f-107">Notify users</span></span>

<span data-ttu-id="5514f-108">Innan du börjar, meddela användare av den webbaserade konsolen att du kommer ta bort webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="5514f-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="5514f-109">Avinstallera Windows PowerShell-webbåtkomst avinstalleras inte IIS eller andra funktioner som installerades automatiskt, eftersom Windows PowerShell-webbåtkomst kräver dem för att köras.</span><span class="sxs-lookup"><span data-stu-id="5514f-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span>
<span data-ttu-id="5514f-110">Avinstallationsprocessen lämnar kvar installerade funktioner som Windows PowerShell-webbåtkomst var beroende; Du kan avinstallera de funktionerna separat, om det behövs.</span><span class="sxs-lookup"><span data-stu-id="5514f-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="5514f-111">Rekommenderad (snabb) avinstallation</span><span class="sxs-lookup"><span data-stu-id="5514f-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="5514f-112">I det här avsnittet hjälper dig att avinstallera både:</span><span class="sxs-lookup"><span data-stu-id="5514f-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="5514f-113">Windows PowerShell-webbåtkomst webbprogrammet, och</span><span class="sxs-lookup"><span data-stu-id="5514f-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="5514f-114">funktionen Windows PowerShell-webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="5514f-114">the Windows PowerShell Web Access feature</span></span>

<span data-ttu-id="5514f-115">med Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="5514f-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="5514f-116">Steg 1: Ta bort webbprogrammet med hjälp av cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="5514f-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="5514f-117">Gör något av följande för att öppna en Windows PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="5514f-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="5514f-118">På Windows-skrivbordet högerklickar du på **Windows PowerShell** i Aktivitetsfältet.</span><span class="sxs-lookup"><span data-stu-id="5514f-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="5514f-119">På Windows **starta** klickar du på **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="5514f-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="5514f-120">Typ `Uninstall-PswaWebApplication`, och tryck sedan på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="5514f-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="5514f-121">Om du har angett ditt eget, anpassade webbplatsnamn, lägg då till `-WebsiteName`-parametern till ditt kommando och ange webbplatsnamnet.</span><span class="sxs-lookup"><span data-stu-id="5514f-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="5514f-122">Om du har använt ett anpassat webbprogram (inte standardprogrammet, **pswa**, lägga till den `-WebApplicationName` parameter i kommandot och ange namnet på webbprogrammet.</span><span class="sxs-lookup"><span data-stu-id="5514f-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="5514f-123">Om du använder ett testcertifikat, lägger du till parametern `DeleteTestCertificate` till cmdleten, på det sätt som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="5514f-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="5514f-124">Steg 2: Avinstallera Windows PowerShell-webbåtkomst med hjälp av cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="5514f-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="5514f-125">Gör något av följande för att öppna en Windows PowerShell-session med utökade användarrättigheter.</span><span class="sxs-lookup"><span data-stu-id="5514f-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="5514f-126">Om en session redan är öppen, går du vidare till nästa steg.</span><span class="sxs-lookup"><span data-stu-id="5514f-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="5514f-127">Högerklicka på Windows-skrivbordet **Windows PowerShell** Aktivitetsfältet och klickar sedan på **Kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="5514f-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="5514f-128">På Windows **starta** högerklickar **Windows PowerShell**, och klicka sedan på **kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="5514f-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="5514f-129">Skriv följande och tryck sedan på **RETUR**, där *computer_name* motsvarar en fjärrserver från vilken du vill ta bort Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="5514f-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="5514f-130">Parametern `-Restart`, startar automatiskt om målservrar om det krävs för borttagningen.</span><span class="sxs-lookup"><span data-stu-id="5514f-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="5514f-131">För att ta bort roller och funktioner från en offline-VHD, behöver du lägga till både `-ComputerName`-parametern och `-VHD`-parametern.</span><span class="sxs-lookup"><span data-stu-id="5514f-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="5514f-132">Parametern `-ComputerName` innehåller namnet på den server som du vill montera VHD:n på och parametern `-VHD` innehåller sökvägen till VHD-filen på den angivna servern.</span><span class="sxs-lookup"><span data-stu-id="5514f-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="5514f-133">När borttagningen är klar kontrollerar du att du tagit bort Windows PowerShell-webbåtkomst genom att öppna den **alla servrar** i Serverhanteraren, välja en server som du tog bort funktionen och sedan visa den **roller och Funktioner** panelen på sidan för den valda servern.</span><span class="sxs-lookup"><span data-stu-id="5514f-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="5514f-134">Du kan också köra den `Get-WindowsFeature` cmdlet riktad mot den valda servern (Get-WindowsFeature - ComputerName &lt; *computer_name*&gt;) att visa en lista över roller och funktioner som är installerade på servern.</span><span class="sxs-lookup"><span data-stu-id="5514f-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="5514f-135">Anpassad avinstallation</span><span class="sxs-lookup"><span data-stu-id="5514f-135">Custom uninstallation</span></span>

<span data-ttu-id="5514f-136">I det här avsnittet hjälper dig att avinstallera både Windows PowerShell Web Access-webbprogram och Windows PowerShell Web Access-funktionen med hjälp av ta bort roller och funktioner som guiden i Serverhanteraren och IIS Manager-konsolen.</span><span class="sxs-lookup"><span data-stu-id="5514f-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="5514f-137">Steg 1: Ta bort webbprogrammet med IIS-hanteraren</span><span class="sxs-lookup"><span data-stu-id="5514f-137">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="5514f-138">Öppna konsolen för IIS-hanteraren genom att göra något av följande.</span><span class="sxs-lookup"><span data-stu-id="5514f-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="5514f-139">Om den redan är öppen, går du vidare till nästa steg.</span><span class="sxs-lookup"><span data-stu-id="5514f-139">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="5514f-140">Starta Serverhanteraren genom att klicka på Windows-skrivbordet **Serverhanteraren** i Aktivitetsfältet.</span><span class="sxs-lookup"><span data-stu-id="5514f-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="5514f-141">På den **verktyg** menyn i Serverhanteraren klickar du på **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="5514f-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="5514f-142">På Windows **starta** skärmen, Skriv någon del av namnet **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="5514f-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="5514f-143">Klicka på genvägen när den visas i den **appar** resultat.</span><span class="sxs-lookup"><span data-stu-id="5514f-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="5514f-144">Välj den webbplats som kör Windows PowerShell Web Access-webbprogram i trädvyn för IIS-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="5514f-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="5514f-145">I den **åtgärder** fönstret under **hantera webbplats**, klickar du på **stoppa**.</span><span class="sxs-lookup"><span data-stu-id="5514f-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="5514f-146">Högerklicka på webbprogrammet på webbplatsen som kör Windows PowerShell Web Access-webbprogram i trädvyn och klicka på **ta bort**.</span><span class="sxs-lookup"><span data-stu-id="5514f-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="5514f-147">I trädvyn väljer **programpooler**, Välj Windows PowerShell-webbåtkomst programpools-mappen, klicka på **stoppa** i den **åtgärder** rutan och klicka sedan på  **Ta bort** i innehållsfönstret.</span><span class="sxs-lookup"><span data-stu-id="5514f-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="5514f-148">Stäng IIS-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="5514f-148">Close IIS Manager.</span></span>

> <span data-ttu-id="5514f-149">![Obs varning](images/SecurityNote.jpeg)**Obs**:</span><span class="sxs-lookup"><span data-stu-id="5514f-149">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="5514f-150">Certifikatet tas inte bort under avinstallationen.</span><span class="sxs-lookup"><span data-stu-id="5514f-150">The certificate is not deleted during uninstallation.</span></span>
>
> <span data-ttu-id="5514f-151">Om du skapat ett självsignerat certifikat eller om du använde ett testcertfikat och vill ta bort det, radera certifikatet i IIS-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="5514f-151">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span>

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="5514f-152">Steg 2: Avinstallera Windows PowerShell-webbåtkomst med hjälp av guiden Ta bort roller och funktioner</span><span class="sxs-lookup"><span data-stu-id="5514f-152">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="5514f-153">Gå vidare till nästa steg om Server Manager redan är öppen.</span><span class="sxs-lookup"><span data-stu-id="5514f-153">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="5514f-154">Öppna genom att göra något av följande om Server Manager inte är redan öppen.</span><span class="sxs-lookup"><span data-stu-id="5514f-154">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="5514f-155">Starta Serverhanteraren genom att klicka på Windows-skrivbordet **Serverhanteraren** i Aktivitetsfältet.</span><span class="sxs-lookup"><span data-stu-id="5514f-155">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="5514f-156">På Windows **starta** klickar du på **Serverhanteraren**.</span><span class="sxs-lookup"><span data-stu-id="5514f-156">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="5514f-157">På den **hantera** -menyn klickar du på **ta bort roller och funktioner**.</span><span class="sxs-lookup"><span data-stu-id="5514f-157">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="5514f-158">På den **väljer målservern** väljer du den server eller offline-VHD som du vill ta bort en funktion.</span><span class="sxs-lookup"><span data-stu-id="5514f-158">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="5514f-159">Du kan välja en offline-VHD genom att först välja på vilken server VHD:n ska monteras och sedan välja VHD-filen.</span><span class="sxs-lookup"><span data-stu-id="5514f-159">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="5514f-160">När du har valt målservern, klickar du på **nästa**.</span><span class="sxs-lookup"><span data-stu-id="5514f-160">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="5514f-161">Klicka på **nästa** igen för att gå vidare till den **Borttagningsfunktioner** sidan.</span><span class="sxs-lookup"><span data-stu-id="5514f-161">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="5514f-162">Avmarkera kryssrutan för **Windows PowerShell-webbåtkomst**, och klicka sedan på **nästa**.</span><span class="sxs-lookup"><span data-stu-id="5514f-162">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="5514f-163">På den **Bekräfta borttagningsinställningarna** klickar du på **ta bort**.</span><span class="sxs-lookup"><span data-stu-id="5514f-163">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="5514f-164">Se även</span><span class="sxs-lookup"><span data-stu-id="5514f-164">See Also</span></span>

- [<span data-ttu-id="5514f-165">Installera och använda Windows PowerShell-webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="5514f-165">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="5514f-166">Hjälpen för IIS-hanteraren 7.0</span><span class="sxs-lookup"><span data-stu-id="5514f-166">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)