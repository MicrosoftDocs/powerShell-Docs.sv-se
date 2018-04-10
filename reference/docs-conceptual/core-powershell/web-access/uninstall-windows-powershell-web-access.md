---
ms.date: 08/23/2017
keywords: PowerShell-cmdlet
title: avinstallera windows powershell-webbåtkomst
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="56364-103">Avinstallera Windows PowerShell-webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="56364-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="56364-104">Uppdaterad: Juni 24 2013</span><span class="sxs-lookup"><span data-stu-id="56364-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="56364-105">Gäller för: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="56364-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="56364-106">Stegen i det här avsnittet Ta bort Windows PowerShell Web Access webbplats och motsvarande program från gateway-servern där den är installerad.</span><span class="sxs-lookup"><span data-stu-id="56364-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="56364-107">Meddela användare</span><span class="sxs-lookup"><span data-stu-id="56364-107">Notify users</span></span>

<span data-ttu-id="56364-108">Innan du börjar, meddela användare av den webbaserade konsolen att du kommer ta bort webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="56364-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="56364-109">Avinstallera Windows PowerShell Web Access avinstallerar inte IIS eller andra funktioner som installerades automatiskt eftersom Windows PowerShell Web Access kräver dem att köra.</span><span class="sxs-lookup"><span data-stu-id="56364-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span>
<span data-ttu-id="56364-110">Avinstallationsprocessen lämnar kvar installerade funktioner som Windows PowerShell Web Access var beroende; Du kan avinstallera de funktionerna separat, om det behövs.</span><span class="sxs-lookup"><span data-stu-id="56364-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="56364-111">Rekommenderad (snabb) avinstallation</span><span class="sxs-lookup"><span data-stu-id="56364-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="56364-112">Procedurerna i det här avsnittet hjälper dig att avinstallera både:</span><span class="sxs-lookup"><span data-stu-id="56364-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="56364-113">webbprogrammet för Windows PowerShell Web Access och</span><span class="sxs-lookup"><span data-stu-id="56364-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="56364-114">funktionen Windows PowerShell-webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="56364-114">the Windows PowerShell Web Access feature</span></span>

<span data-ttu-id="56364-115">med hjälp av Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="56364-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="56364-116">Steg 1: Ta bort webbprogrammet med hjälp av cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="56364-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="56364-117">Gör något av följande för att öppna en Windows PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="56364-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="56364-118">Högerklicka på Windows-skrivbordet **Windows PowerShell** i Aktivitetsfältet.</span><span class="sxs-lookup"><span data-stu-id="56364-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="56364-119">På Windows **starta** klickar du på **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="56364-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="56364-120">Typen `Uninstall-PswaWebApplication`, och tryck sedan på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="56364-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="56364-121">Om du har angett ditt eget, anpassade webbplatsnamn, lägg då till `-WebsiteName`-parametern till ditt kommando och ange webbplatsnamnet.</span><span class="sxs-lookup"><span data-stu-id="56364-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="56364-122">Om du har använt ett anpassat webbprogram (inte standardprogrammet, **pswa**, lägga till den `-WebApplicationName` parametern i kommandot och ange namnet på webbprogrammet.</span><span class="sxs-lookup"><span data-stu-id="56364-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="56364-123">Om du använder ett testcertifikat, lägger du till parametern `DeleteTestCertificate` till cmdleten, på det sätt som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="56364-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="56364-124">Steg 2: Avinstallera Windows PowerShell-webbåtkomst med hjälp av cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="56364-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="56364-125">Gör något av följande för att öppna en Windows PowerShell-session med utökade användarrättigheter.</span><span class="sxs-lookup"><span data-stu-id="56364-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="56364-126">Om en session redan är öppen, går du vidare till nästa steg.</span><span class="sxs-lookup"><span data-stu-id="56364-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="56364-127">Högerklicka på Windows-skrivbordet **Windows PowerShell** Aktivitetsfältet och klickar sedan på **Kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="56364-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="56364-128">På Windows **starta** , högerklicka på **Windows PowerShell**, och klicka sedan på **kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="56364-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="56364-129">Skriv följande och tryck sedan på **RETUR**, där *computer_name* motsvarar en fjärrserver som du vill ta bort Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="56364-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="56364-130">Parametern `-Restart`, startar automatiskt om målservrar om det krävs för borttagningen.</span><span class="sxs-lookup"><span data-stu-id="56364-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="56364-131">För att ta bort roller och funktioner från en offline-VHD, behöver du lägga till både `-ComputerName`-parametern och `-VHD`-parametern.</span><span class="sxs-lookup"><span data-stu-id="56364-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="56364-132">Parametern `-ComputerName` innehåller namnet på den server som du vill montera VHD:n på och parametern `-VHD` innehåller sökvägen till VHD-filen på den angivna servern.</span><span class="sxs-lookup"><span data-stu-id="56364-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="56364-133">När borttagningen är klar kontrollerar du att du tagit bort Windows PowerShell Web Access genom att öppna den **alla servrar** i Serverhanteraren, välja en server som du tog bort funktionen och sedan visa den **roller och Funktioner** på sidan för den valda servern.</span><span class="sxs-lookup"><span data-stu-id="56364-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="56364-134">Du kan också köra den `Get-WindowsFeature` med den valda servern som mål (Get-WindowsFeature - ComputerName &lt; *computer_name*&gt;) att visa en lista över roller och funktioner som är installerade på servern.</span><span class="sxs-lookup"><span data-stu-id="56364-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="56364-135">Anpassad avinstallation</span><span class="sxs-lookup"><span data-stu-id="56364-135">Custom uninstallation</span></span>

<span data-ttu-id="56364-136">I det här avsnittet hjälper dig att avinstallera både Windows PowerShell Web Access-webbprogram och Windows PowerShell Web Access-funktionen med hjälp av ta bort roller och funktioner guide i Serverhanteraren och IIS Manager-konsolen.</span><span class="sxs-lookup"><span data-stu-id="56364-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="56364-137">Steg 1: Ta bort webbprogrammet med IIS-hanteraren</span><span class="sxs-lookup"><span data-stu-id="56364-137">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="56364-138">Öppna konsolen för IIS-hanteraren genom att göra något av följande.</span><span class="sxs-lookup"><span data-stu-id="56364-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="56364-139">Om den redan är öppen, går du vidare till nästa steg.</span><span class="sxs-lookup"><span data-stu-id="56364-139">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="56364-140">Starta Serverhanteraren genom att klicka på Windows-skrivbordet **Serverhanteraren** i Aktivitetsfältet.</span><span class="sxs-lookup"><span data-stu-id="56364-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="56364-141">På den **verktyg** menyn i Serverhanteraren klickar du på **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="56364-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="56364-142">På Windows **starta** skriver någon del av namnet **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="56364-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="56364-143">Klicka på genvägen när den visas i den **appar** resultat.</span><span class="sxs-lookup"><span data-stu-id="56364-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="56364-144">Välj den webbplats som kör Windows PowerShell Web Access-webbprogrammet i trädvyn för IIS-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="56364-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="56364-145">I den **åtgärder** rutan under **hantera webbplats**, klickar du på **stoppa**.</span><span class="sxs-lookup"><span data-stu-id="56364-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="56364-146">Högerklicka på webbprogrammet på webbplatsen som kör Windows PowerShell Web Access-webbprogrammet i trädvyn och klicka **ta bort**.</span><span class="sxs-lookup"><span data-stu-id="56364-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="56364-147">I trädvyn markerar **programpooler**, väljer programpools-mappen i Windows PowerShell Web Access, klickar du på **stoppa** i den **åtgärder** rutan och klicka sedan på  **Ta bort** i innehållsfönstret.</span><span class="sxs-lookup"><span data-stu-id="56364-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="56364-148">Stäng IIS-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="56364-148">Close IIS Manager.</span></span>

> <span data-ttu-id="56364-149">![Varning Obs](images/SecurityNote.jpeg)**Observera**:</span><span class="sxs-lookup"><span data-stu-id="56364-149">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="56364-150">Certifikatet tas inte bort under avinstallationen.</span><span class="sxs-lookup"><span data-stu-id="56364-150">The certificate is not deleted during uninstallation.</span></span>
>
> <span data-ttu-id="56364-151">Om du skapat ett självsignerat certifikat eller om du använde ett testcertfikat och vill ta bort det, radera certifikatet i IIS-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="56364-151">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span>

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="56364-152">Steg 2: Avinstallera Windows PowerShell-webbåtkomst med hjälp av guiden Ta bort roller och funktioner</span><span class="sxs-lookup"><span data-stu-id="56364-152">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="56364-153">Gå vidare till nästa steg om Server Manager redan är öppen.</span><span class="sxs-lookup"><span data-stu-id="56364-153">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="56364-154">Öppna genom att göra något av följande om Server Manager inte är redan öppen.</span><span class="sxs-lookup"><span data-stu-id="56364-154">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="56364-155">Starta Serverhanteraren genom att klicka på Windows-skrivbordet **Serverhanteraren** i Aktivitetsfältet.</span><span class="sxs-lookup"><span data-stu-id="56364-155">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="56364-156">På Windows **starta** klickar du på **Serverhanteraren**.</span><span class="sxs-lookup"><span data-stu-id="56364-156">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="56364-157">På den **hantera** -menyn klickar du på **ta bort roller och funktioner**.</span><span class="sxs-lookup"><span data-stu-id="56364-157">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="56364-158">På den **väljer målservern** väljer du den server eller offline-VHD som du vill ta bort en funktion.</span><span class="sxs-lookup"><span data-stu-id="56364-158">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="56364-159">Du kan välja en offline-VHD genom att först välja på vilken server VHD:n ska monteras och sedan välja VHD-filen.</span><span class="sxs-lookup"><span data-stu-id="56364-159">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="56364-160">När du har valt målservern klickar du på **nästa**.</span><span class="sxs-lookup"><span data-stu-id="56364-160">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="56364-161">Klicka på **nästa** igen för att hoppa till den **ta bort funktioner** sidan.</span><span class="sxs-lookup"><span data-stu-id="56364-161">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="56364-162">Avmarkera kryssrutan för **Windows PowerShell Web Access**, och klicka sedan på **nästa**.</span><span class="sxs-lookup"><span data-stu-id="56364-162">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="56364-163">På den **Bekräfta borttagningsinställningarna** klickar du på **ta bort**.</span><span class="sxs-lookup"><span data-stu-id="56364-163">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="56364-164">Se även</span><span class="sxs-lookup"><span data-stu-id="56364-164">See Also</span></span>

- [<span data-ttu-id="56364-165">Installera och använda Windows PowerShell-webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="56364-165">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="56364-166">Hjälpen för IIS-hanteraren 7.0</span><span class="sxs-lookup"><span data-stu-id="56364-166">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)