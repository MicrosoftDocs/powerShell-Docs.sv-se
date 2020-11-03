---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-acl?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Acl
ms.openlocfilehash: 3c8f26884ac0eda1ece799bbd49a7863b6d2239c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93263037"
---
# <span data-ttu-id="a0619-103">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="a0619-103">Set-Acl</span></span>

## <span data-ttu-id="a0619-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a0619-104">SYNOPSIS</span></span>
<span data-ttu-id="a0619-105">Ändrar säkerhets beskrivningen för ett angivet objekt, till exempel en fil eller en register nyckel.</span><span class="sxs-lookup"><span data-stu-id="a0619-105">Changes the security descriptor of a specified item, such as a file or a registry key.</span></span>

## <span data-ttu-id="a0619-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a0619-106">SYNTAX</span></span>

### <span data-ttu-id="a0619-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="a0619-107">ByPath (Default)</span></span>

```
Set-Acl [-Path] <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a0619-108">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="a0619-108">ByInputObject</span></span>

```
Set-Acl [-InputObject] <PSObject> [-AclObject] <Object> [-Passthru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a0619-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="a0619-109">ByLiteralPath</span></span>

```
Set-Acl -LiteralPath <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a0619-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a0619-110">DESCRIPTION</span></span>

<span data-ttu-id="a0619-111">`Set-Acl`Cmdleten ändrar säkerhets beskrivningen för ett angivet objekt, till exempel en fil eller en register nyckel, för att matcha värdena i en säkerhets beskrivning som du anger.</span><span class="sxs-lookup"><span data-stu-id="a0619-111">The `Set-Acl` cmdlet changes the security descriptor of a specified item, such as a file or a registry key, to match the values in a security descriptor that you supply.</span></span>

<span data-ttu-id="a0619-112">Använd `Set-Acl` parametern **Path** eller **InputObject** för att identifiera det objekt vars säkerhets Beskrivning du vill ändra.</span><span class="sxs-lookup"><span data-stu-id="a0619-112">To use `Set-Acl`, use the **Path** or **InputObject** parameter to identify the item whose security descriptor you want to change.</span></span> <span data-ttu-id="a0619-113">Använd sedan parametrarna **AclObject** eller **adtagent** för att ange en säkerhets beskrivare som har de värden som du vill använda.</span><span class="sxs-lookup"><span data-stu-id="a0619-113">Then, use the **AclObject** or **SecurityDescriptor** parameters to supply a security descriptor that has the values you want to apply.</span></span> <span data-ttu-id="a0619-114">`Set-Acl` använder den angivna säkerhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="a0619-114">`Set-Acl` applies the security descriptor that is supplied.</span></span> <span data-ttu-id="a0619-115">Värdet för parametern **AclObject** används som en modell och ändrar värdena i objektets säkerhets Beskrivning så att de matchar värdena i parametern **AclObject** .</span><span class="sxs-lookup"><span data-stu-id="a0619-115">It uses the value of the **AclObject** parameter as a model and changes the values in the item's security descriptor to match the values in the **AclObject** parameter.</span></span>

## <span data-ttu-id="a0619-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a0619-116">EXAMPLES</span></span>

### <span data-ttu-id="a0619-117">Exempel 1: kopiera en säkerhets beskrivning från en fil till en annan</span><span class="sxs-lookup"><span data-stu-id="a0619-117">Example 1: Copy a security descriptor from one file to another</span></span>

```powershell
$DogACL = Get-Acl -Path "C:\Dog.txt"
Set-Acl -Path "C:\Cat.txt" -AclObject $DogACL
```

<span data-ttu-id="a0619-118">Dessa kommandon kopierar värdena från den Dog.txt filens säkerhets beskrivning till säkerhets beskrivningen för Cat.txts filen.</span><span class="sxs-lookup"><span data-stu-id="a0619-118">These commands copy the values from the security descriptor of the Dog.txt file to the security descriptor of the Cat.txt file.</span></span> <span data-ttu-id="a0619-119">När kommandona har slutförts är säkerhets beskrivarna för Dog.txt-och Cat.txt-filerna identiska.</span><span class="sxs-lookup"><span data-stu-id="a0619-119">When the commands complete, the security descriptors of the Dog.txt and Cat.txt files are identical.</span></span>

<span data-ttu-id="a0619-120">Det första kommandot använder `Get-Acl` cmdleten för att hämta den Dog.txt filens säkerhets beskrivning.</span><span class="sxs-lookup"><span data-stu-id="a0619-120">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>
<span data-ttu-id="a0619-121">Tilldelnings operatorn ( `=` ) lagrar säkerhets beskrivningen i värdet för variabeln $DogACL.</span><span class="sxs-lookup"><span data-stu-id="a0619-121">The assignment operator (`=`) stores the security descriptor in the value of the $DogACL variable.</span></span>

<span data-ttu-id="a0619-122">Det andra kommandot använder `Set-Acl` för att ändra värdena i ACL: en för Cat.txt till värdena i `$DogACL` .</span><span class="sxs-lookup"><span data-stu-id="a0619-122">The second command uses `Set-Acl` to change the values in the ACL of Cat.txt to the values in `$DogACL`.</span></span>

<span data-ttu-id="a0619-123">Värdet för parametern **Path** är sökvägen till Cat.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="a0619-123">The value of the **Path** parameter is the path to the Cat.txt file.</span></span> <span data-ttu-id="a0619-124">Värdet för parametern **AclObject** är modellens ACL, i det här fallet ACL: en för Dog.txt som sparas i `$DogACL` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a0619-124">The value of the **AclObject** parameter is the model ACL, in this case, the ACL of Dog.txt as saved in the `$DogACL` variable.</span></span>

### <span data-ttu-id="a0619-125">Exempel 2: Använd pipeline-operatorn för att skicka en beskrivning</span><span class="sxs-lookup"><span data-stu-id="a0619-125">Example 2: Use the pipeline operator to pass a descriptor</span></span>

```powershell
Get-Acl -Path "C:\Dog.txt" | Set-Acl -Path "C:\Cat.txt"
```

<span data-ttu-id="a0619-126">Det här kommandot är nästan detsamma som kommandot i föregående exempel, förutom att det använder en pipeline-operator ( `|` ) för att skicka säkerhets beskrivningen från ett `Get-Acl` kommando till ett `Set-Acl` kommando.</span><span class="sxs-lookup"><span data-stu-id="a0619-126">This command is almost the same as the command in the previous example, except that it uses a pipeline operator (`|`) to send the security descriptor from a `Get-Acl` command to a `Set-Acl` command.</span></span>

<span data-ttu-id="a0619-127">Det första kommandot använder `Get-Acl` cmdleten för att hämta den Dog.txt filens säkerhets beskrivning.</span><span class="sxs-lookup"><span data-stu-id="a0619-127">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span> <span data-ttu-id="a0619-128">Pipeline-operatorn ( `|` ) skickar ett objekt som representerar den Dog.txt säkerhets beskrivningen till `Set-Acl` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0619-128">The pipeline operator (`|`) passes an object that represents the Dog.txt security descriptor to the `Set-Acl` cmdlet.</span></span>

<span data-ttu-id="a0619-129">Det andra kommandot använder `Set-Acl` för att tillämpa säkerhets beskrivningen för Dog.txt Cat.txt.</span><span class="sxs-lookup"><span data-stu-id="a0619-129">The second command uses `Set-Acl` to apply the security descriptor of Dog.txt to Cat.txt.</span></span>
<span data-ttu-id="a0619-130">När kommandot har slutförts är ACL: erna för Dog.txt-och Cat.txt-filerna identiska.</span><span class="sxs-lookup"><span data-stu-id="a0619-130">When the command completes, the ACLs of the Dog.txt and Cat.txt files are identical.</span></span>

### <span data-ttu-id="a0619-131">Exempel 3: tillämpa en säkerhets beskrivning på flera filer</span><span class="sxs-lookup"><span data-stu-id="a0619-131">Example 3: Apply a security descriptor to multiple files</span></span>

```powershell
$NewAcl = Get-Acl File0.txt
Get-ChildItem -Path "C:\temp" -Recurse -Include "*.txt" -Force | Set-Acl -AclObject $NewAcl
```

<span data-ttu-id="a0619-132">Dessa kommandon tillämpar säkerhets beskrivningar i File0.txt-filen för alla textfiler i `C:\Temp` katalogen och alla dess under kataloger.</span><span class="sxs-lookup"><span data-stu-id="a0619-132">These commands apply the security descriptors in the File0.txt file to all text files in the `C:\Temp` directory and all of its subdirectories.</span></span>

<span data-ttu-id="a0619-133">Det första kommandot hämtar säkerhets beskrivningen för File0.txt-filen i den aktuella katalogen och använder tilldelnings operatorn ( `=` ) för att lagra den i `$NewACL` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a0619-133">The first command gets the security descriptor of the File0.txt file in the current directory and uses the assignment operator (`=`) to store it in the `$NewACL` variable.</span></span>

<span data-ttu-id="a0619-134">Det första kommandot i pipelinen använder Get-ChildItem-cmdleten för att hämta alla textfiler i `C:\Temp` katalogen.</span><span class="sxs-lookup"><span data-stu-id="a0619-134">The first command in the pipeline uses the Get-ChildItem cmdlet to get all of the text files in the `C:\Temp` directory.</span></span> <span data-ttu-id="a0619-135">Parametern **rekursivt** utökar kommandot till alla under kataloger i `C:\temp` .</span><span class="sxs-lookup"><span data-stu-id="a0619-135">The **Recurse** parameter extends the command to all subdirectories of `C:\temp`.</span></span> <span data-ttu-id="a0619-136">Parametern **include** begränsar de filer som hämtas till dem med `.txt` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="a0619-136">The **Include** parameter limits the files retrieved to those with the `.txt` file name extension.</span></span> <span data-ttu-id="a0619-137">Parametern **Force** hämtar dolda filer, vilket annars skulle uteslutas.</span><span class="sxs-lookup"><span data-stu-id="a0619-137">The **Force** parameter gets hidden files, which would otherwise be excluded.</span></span> <span data-ttu-id="a0619-138">(Du kan inte använda `c:\temp\*.txt` eftersom parametern **rekursivt** fungerar på kataloger, inte på filer.)</span><span class="sxs-lookup"><span data-stu-id="a0619-138">(You cannot use `c:\temp\*.txt`, because the **Recurse** parameter works on directories, not on files.)</span></span>

<span data-ttu-id="a0619-139">Pipelinen ( `|` ) skickar objekten som representerar de hämtade filerna till `Set-Acl` cmdleten, som använder säkerhets beskrivningen i **AclObject** -parametern för alla filer i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a0619-139">The pipeline operator (`|`) sends the objects representing the retrieved files to the `Set-Acl` cmdlet, which applies the security descriptor in the **AclObject** parameter to all of the files in the pipeline.</span></span>

<span data-ttu-id="a0619-140">I praktiken är det bäst att använda parametern **whatIf** med alla `Set-Acl` kommandon som kan påverka fler än ett objekt.</span><span class="sxs-lookup"><span data-stu-id="a0619-140">In practice, it is best to use the **WhatIf** parameter with all `Set-Acl` commands that can affect more than one item.</span></span> <span data-ttu-id="a0619-141">I det här fallet skulle det andra kommandot i pipelinen vara `Set-Acl -AclObject $NewAcl -WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="a0619-141">In this case, the second command in the pipeline would be `Set-Acl -AclObject $NewAcl -WhatIf`.</span></span> <span data-ttu-id="a0619-142">Det här kommandot visar de filer som skulle påverkas av kommandot.</span><span class="sxs-lookup"><span data-stu-id="a0619-142">This command lists the files that would be affected by the command.</span></span> <span data-ttu-id="a0619-143">När du har granskat resultatet kan du köra kommandot igen utan parametern **whatIf** .</span><span class="sxs-lookup"><span data-stu-id="a0619-143">After reviewing the result, you can run the command again without the **WhatIf** parameter.</span></span>

### <span data-ttu-id="a0619-144">Exempel 4: inaktivera arv och bevara ärvda åtkomst regler</span><span class="sxs-lookup"><span data-stu-id="a0619-144">Example 4: Disable inheritance and preserve inherited access rules</span></span>

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
$isProtected = $true
$preserveInheritance = $true
$NewAcl.SetAccessRuleProtection($isProtected, $preserveInheritance)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

<span data-ttu-id="a0619-145">Dessa kommandon inaktiverar åtkomst arv från överordnade mappar, samtidigt som befintliga ärvda åtkomst regler bevaras.</span><span class="sxs-lookup"><span data-stu-id="a0619-145">These commands is will disable access inheritance from parent folders, while still preserving the existing inherited access rules.</span></span>

<span data-ttu-id="a0619-146">Det första kommandot använder `Get-Acl` cmdleten för att hämta den Dog.txt filens säkerhets beskrivning.</span><span class="sxs-lookup"><span data-stu-id="a0619-146">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>

<span data-ttu-id="a0619-147">Sedan skapas variabler för att konvertera de ärvda åtkomst reglerna till explicita åtkomst regler.</span><span class="sxs-lookup"><span data-stu-id="a0619-147">Next, variables are created to convert the inherited access rules to explicit access rules.</span></span> <span data-ttu-id="a0619-148">Om du vill skydda åtkomst reglerna som är kopplade till detta från arv ställer du in `$isProtected` variabeln på `$true` . Tillåt arv genom att ange `$isProtected` till `$false` .</span><span class="sxs-lookup"><span data-stu-id="a0619-148">To protect the access rules associated with this from inheritance, set the `$isProtected` variable to `$true`.to allow inheritance, set `$isProtected` to `$false`.</span></span> <span data-ttu-id="a0619-149">Mer information finns i [Ange skydd för åtkomst regler](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection).</span><span class="sxs-lookup"><span data-stu-id="a0619-149">For more information, see [set access rule protection](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection).</span></span>
<span data-ttu-id="a0619-150">`$preserveInheritance`Variabeln som angetts till `$true` för att bevara ärvda åtkomst regler, falskt för att ta bort ärvda åtkomst regler.</span><span class="sxs-lookup"><span data-stu-id="a0619-150">The `$preserveInheritance` variable set to `$true` to preserve inherited access rules; false to remove inherited access rules.</span></span> <span data-ttu-id="a0619-151">Sedan uppdateras åtkomst regel skyddet med hjälp av metoden **SetAccessRuleProtection ()** .</span><span class="sxs-lookup"><span data-stu-id="a0619-151">Then the access rule protection is updated using the **SetAccessRuleProtection()** method.</span></span>

<span data-ttu-id="a0619-152">Det sista kommandot använder `Set-Acl` för att tillämpa säkerhets beskrivningen för Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="a0619-152">The last command uses `Set-Acl` to apply the security descriptor of to Dog.txt.</span></span> <span data-ttu-id="a0619-153">När kommandot har slutförts kommer ACL: er för de Dog.txt som ärvts från mappen hus djur att tillämpas direkt på Dog.txt, och nya åtkomst principer som läggs till i hus djur kommer inte att ändra åtkomsten till Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="a0619-153">When the command completes, the ACLs of the Dog.txt that were inherited from the Pets folder will be applied directly to Dog.txt, and new access policies added to Pets will not change the access to Dog.txt.</span></span>

### <span data-ttu-id="a0619-154">Exempel 5: bevilja administratörer fullständig kontroll över filen</span><span class="sxs-lookup"><span data-stu-id="a0619-154">Example 5: Grant Administrators Full Control of the file</span></span>

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
# Set properties
$identity = "BUILTIN\Administrators"
$fileSystemRights = "FullControl"
$type = "Allow"
# Create new rule
$fileSystemAccessRuleArgumentList = $identity, $fileSystemRights, $type
$fileSystemAccessRule = New-Object -TypeName System.Security.AccessControl.FileSystemAccessRule -ArgumentList $fileSystemAccessRuleArgumentList
# Apply new rule
$NewAcl.SetAccessRule($fileSystemAccessRule)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

<span data-ttu-id="a0619-155">Det här kommandot ger **BUILTIN\Administrators** -gruppen fullständig kontroll över Dog.txts filen.</span><span class="sxs-lookup"><span data-stu-id="a0619-155">This command will grant the **BUILTIN\Administrators** group Full control of the Dog.txt file.</span></span>

<span data-ttu-id="a0619-156">Det första kommandot använder `Get-Acl` cmdleten för att hämta den Dog.txt filens säkerhets beskrivning.</span><span class="sxs-lookup"><span data-stu-id="a0619-156">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>

<span data-ttu-id="a0619-157">Next-variabler skapas för att ge **BUILTIN\Administrators** -gruppen fullständig kontroll över Dog.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="a0619-157">Next variables are created to grant the **BUILTIN\Administrators** group full control of the Dog.txt file.</span></span> <span data-ttu-id="a0619-158">`$identity`Variabeln anges till namnet på ett [användar konto](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor).</span><span class="sxs-lookup"><span data-stu-id="a0619-158">The `$identity` variable set to the name of a [user account](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor).</span></span>
<span data-ttu-id="a0619-159">`$fileSystemRights`Variabeln inställd på FullControl och kan vara något av [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) -värdena som anger vilken typ av åtgärd som är kopplad till åtkomst regeln.</span><span class="sxs-lookup"><span data-stu-id="a0619-159">The `$fileSystemRights` variable set to FullControl, and can be any one of the [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) values that specifies the type of operation associated with the access rule.</span></span> <span data-ttu-id="a0619-160">`$type`Variabeln anges till Tillåt för att ange om åtgärden ska tillåtas eller nekas.</span><span class="sxs-lookup"><span data-stu-id="a0619-160">The `$type` variable set to "Allow" to specifies whether to allow or deny the operation.</span></span> <span data-ttu-id="a0619-161">`$fileSystemAccessRuleArgumentList`Variabeln är en argument lista som ska skickas när det nya **FileSystemAccessRule** -objektet görs.</span><span class="sxs-lookup"><span data-stu-id="a0619-161">The `$fileSystemAccessRuleArgumentList` variable is an argument list is to be passed when making the new **FileSystemAccessRule** object.</span></span> <span data-ttu-id="a0619-162">Sedan skapas ett nytt **FileSystemAccessRule** -objekt och **FileSystemAccessRule** -objektet skickas till metoden **SetAccessRule ()** lägger till den nya åtkomst regeln.</span><span class="sxs-lookup"><span data-stu-id="a0619-162">Then a new **FileSystemAccessRule** object is created, and the **FileSystemAccessRule** object is passed to the **SetAccessRule()** method, adds the new access rule.</span></span>

<span data-ttu-id="a0619-163">Det sista kommandot använder `Set-Acl` för att tillämpa säkerhets beskrivningen för Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="a0619-163">The last command uses `Set-Acl` to apply the security descriptor of to Dog.txt.</span></span>
<span data-ttu-id="a0619-164">När kommandot har slutförts har **BUILTIN\Administrators** -gruppen fullständig kontroll över den Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="a0619-164">When the command completes, the **BUILTIN\Administrators** group will have full control of the Dog.txt.</span></span>

## <span data-ttu-id="a0619-165">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a0619-165">PARAMETERS</span></span>

### <span data-ttu-id="a0619-166">-AclObject</span><span class="sxs-lookup"><span data-stu-id="a0619-166">-AclObject</span></span>

<span data-ttu-id="a0619-167">Anger en ACL med önskade egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="a0619-167">Specifies an ACL with the desired property values.</span></span> <span data-ttu-id="a0619-168">`Set-Acl` ändrar ACL för objektet som anges av **sökvägen** eller parametern **InputObject** för att matcha värdena i det angivna säkerhets objektet.</span><span class="sxs-lookup"><span data-stu-id="a0619-168">`Set-Acl` changes the ACL of item specified by the **Path** or **InputObject** parameter to match the values in the specified security object.</span></span>

<span data-ttu-id="a0619-169">Du kan spara utdata från ett `Get-Acl` kommando i en variabel och sedan använda parametern **AclObject** för att skicka variabeln eller skriva ett `Get-Acl` kommando.</span><span class="sxs-lookup"><span data-stu-id="a0619-169">You can save the output of a `Get-Acl` command in a variable and then use the **AclObject** parameter to pass the variable, or type a `Get-Acl` command.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a0619-170">-ClearCentralAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="a0619-170">-ClearCentralAccessPolicy</span></span>

<span data-ttu-id="a0619-171">Tar bort principen för central åtkomst från det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="a0619-171">Removes the central access policy from the specified item.</span></span>

<span data-ttu-id="a0619-172">Från och med Windows Server 2012 kan administratörer använda Active Directory och grupprincip för att ange principer för central åtkomst för användare och grupper.</span><span class="sxs-lookup"><span data-stu-id="a0619-172">Beginning in Windows Server 2012, administrators can use Active Directory and Group Policy to set central access policies for users and groups.</span></span> <span data-ttu-id="a0619-173">Mer information finns i [dynamisk Access Control: Scenario översikt](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).</span><span class="sxs-lookup"><span data-stu-id="a0619-173">For more information, see [Dynamic Access Control: Scenario Overview](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).</span></span>

<span data-ttu-id="a0619-174">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a0619-174">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByPath, ByLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0619-175">-Undanta</span><span class="sxs-lookup"><span data-stu-id="a0619-175">-Exclude</span></span>

<span data-ttu-id="a0619-176">Utesluter de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="a0619-176">Omits the specified items.</span></span> <span data-ttu-id="a0619-177">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a0619-177">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a0619-178">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="a0619-178">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a0619-179">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a0619-179">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a0619-180">-Filter</span><span class="sxs-lookup"><span data-stu-id="a0619-180">-Filter</span></span>

<span data-ttu-id="a0619-181">Anger ett filter i providerns format eller språk.</span><span class="sxs-lookup"><span data-stu-id="a0619-181">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="a0619-182">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a0619-182">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a0619-183">Syntaxen för filtret, inklusive användning av jokertecken, beror på providern.</span><span class="sxs-lookup"><span data-stu-id="a0619-183">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="a0619-184">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när objekten hämtas, i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="a0619-184">Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a0619-185">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="a0619-185">-Include</span></span>

<span data-ttu-id="a0619-186">Ändrar endast de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="a0619-186">Changes only the specified items.</span></span> <span data-ttu-id="a0619-187">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a0619-187">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="a0619-188">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="a0619-188">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a0619-189">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a0619-189">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a0619-190">– InputObject</span><span class="sxs-lookup"><span data-stu-id="a0619-190">-InputObject</span></span>

<span data-ttu-id="a0619-191">Ändrar säkerhets beskrivningen för det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="a0619-191">Changes the security descriptor of the specified object.</span></span> <span data-ttu-id="a0619-192">Ange en variabel som innehåller objektet eller ett kommando som hämtar objektet.</span><span class="sxs-lookup"><span data-stu-id="a0619-192">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="a0619-193">Det går inte att skicka ett objekt att ändra till `Set-Acl` .</span><span class="sxs-lookup"><span data-stu-id="a0619-193">You cannot pipe the object to be changed to `Set-Acl`.</span></span> <span data-ttu-id="a0619-194">Använd i stället parametern **InputObject** explicit i kommandot.</span><span class="sxs-lookup"><span data-stu-id="a0619-194">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="a0619-195">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a0619-195">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a0619-196">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a0619-196">-LiteralPath</span></span>

<span data-ttu-id="a0619-197">Ändrar säkerhets beskrivningen för det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="a0619-197">Changes the security descriptor of the specified item.</span></span> <span data-ttu-id="a0619-198">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="a0619-198">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="a0619-199">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="a0619-199">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a0619-200">Om sökvägen innehåller escape-tecken, omger du den med enkla citat tecken ( `'` ).</span><span class="sxs-lookup"><span data-stu-id="a0619-200">If the path includes escape characters, enclose it in single quotation marks (`'`).</span></span>
<span data-ttu-id="a0619-201">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="a0619-201">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="a0619-202">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a0619-202">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a0619-203">– Passthru</span><span class="sxs-lookup"><span data-stu-id="a0619-203">-Passthru</span></span>

<span data-ttu-id="a0619-204">Returnerar ett objekt som representerar säkerhets beskrivningen som ändrades.</span><span class="sxs-lookup"><span data-stu-id="a0619-204">Returns an object that represents the security descriptor that was changed.</span></span> <span data-ttu-id="a0619-205">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="a0619-205">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a0619-206">-Path</span><span class="sxs-lookup"><span data-stu-id="a0619-206">-Path</span></span>

<span data-ttu-id="a0619-207">Ändrar säkerhets beskrivningen för det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="a0619-207">Changes the security descriptor of the specified item.</span></span> <span data-ttu-id="a0619-208">Ange sökvägen till ett objekt, till exempel en sökväg till en fil eller register nyckel.</span><span class="sxs-lookup"><span data-stu-id="a0619-208">Enter the path to an item, such as a path to a file or registry key.</span></span> <span data-ttu-id="a0619-209">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a0619-209">Wildcards are permitted.</span></span>

<span data-ttu-id="a0619-210">Om du skickar ett säkerhets objekt till `Set-Acl` (antingen genom att använda **AclObject** -eller **adtagent** -parametrarna eller genom att skicka ett säkerhets objekt från Get-Acl till `Set-Acl` ) och du utelämnar **Sök vägs** parametern (namn och värde), `Set-Acl` använder den sökväg som ingår i säkerhets objekt.</span><span class="sxs-lookup"><span data-stu-id="a0619-210">If you pass a security object to `Set-Acl` (either by using the **AclObject** or **SecurityDescriptor** parameters or by passing a security object from Get-Acl to `Set-Acl`), and you omit the **Path** parameter (name and value), `Set-Acl` uses the path that is included in the security object.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="a0619-211">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a0619-211">-Confirm</span></span>

<span data-ttu-id="a0619-212">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0619-212">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0619-213">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a0619-213">-WhatIf</span></span>

<span data-ttu-id="a0619-214">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="a0619-214">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a0619-215">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="a0619-215">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0619-216">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a0619-216">CommonParameters</span></span>

<span data-ttu-id="a0619-217">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a0619-217">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a0619-218">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a0619-218">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a0619-219">INDATA</span><span class="sxs-lookup"><span data-stu-id="a0619-219">INPUTS</span></span>

### <span data-ttu-id="a0619-220">System. Security. AccessControl. ObjectSecurity, system. Security. AccessControl. CommonSecurityDescriptor</span><span class="sxs-lookup"><span data-stu-id="a0619-220">System.Security.AccessControl.ObjectSecurity, System.Security.AccessControl.CommonSecurityDescriptor</span></span>

<span data-ttu-id="a0619-221">Du kan skicka ett ACL-objekt eller en säkerhets beskrivning till `Set-Acl` .</span><span class="sxs-lookup"><span data-stu-id="a0619-221">You can pipe an ACL object or a security descriptor to `Set-Acl`.</span></span>

## <span data-ttu-id="a0619-222">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a0619-222">OUTPUTS</span></span>

### <span data-ttu-id="a0619-223">System. Security. AccessControl. FileSecurity</span><span class="sxs-lookup"><span data-stu-id="a0619-223">System.Security.AccessControl.FileSecurity</span></span>

<span data-ttu-id="a0619-224">`Set-Acl`Genererar inga utdata som standard.</span><span class="sxs-lookup"><span data-stu-id="a0619-224">By default, `Set-Acl` does not generate any output.</span></span>
<span data-ttu-id="a0619-225">Men om du använder parametern **Passthru** genereras ett säkerhets objekt.</span><span class="sxs-lookup"><span data-stu-id="a0619-225">However, if you use the **Passthru** parameter, it generates a security object.</span></span>
<span data-ttu-id="a0619-226">Vilken typ av säkerhets objekt som är beror på objektets typ.</span><span class="sxs-lookup"><span data-stu-id="a0619-226">The type of the security object depends on the type of the item.</span></span>

## <span data-ttu-id="a0619-227">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a0619-227">NOTES</span></span>

 <span data-ttu-id="a0619-228">`Set-Acl`Cmdleten stöds av PowerShell-filsystemet och register leverantörerna.</span><span class="sxs-lookup"><span data-stu-id="a0619-228">The `Set-Acl` cmdlet is supported by the PowerShell file system and registry providers.</span></span> <span data-ttu-id="a0619-229">Därför kan du använda den för att ändra säkerhets beskrivare för filer, kataloger och register nycklar.</span><span class="sxs-lookup"><span data-stu-id="a0619-229">As such, you can use it to change the security descriptors of files, directories, and registry keys.</span></span>

## <span data-ttu-id="a0619-230">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a0619-230">RELATED LINKS</span></span>

[<span data-ttu-id="a0619-231">Get-ACL</span><span class="sxs-lookup"><span data-stu-id="a0619-231">Get-Acl</span></span>](Get-Acl.md)

[<span data-ttu-id="a0619-232">FileSystemAccessRule</span><span class="sxs-lookup"><span data-stu-id="a0619-232">FileSystemAccessRule</span></span>](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)

[<span data-ttu-id="a0619-233">ObjectSecurity.SetAccessRuleProtection</span><span class="sxs-lookup"><span data-stu-id="a0619-233">ObjectSecurity.SetAccessRuleProtection</span></span>](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)

[<span data-ttu-id="a0619-234">FileSystemRights</span><span class="sxs-lookup"><span data-stu-id="a0619-234">FileSystemRights</span></span>](/dotnet/api/system.security.accesscontrol.filesystemrights)
