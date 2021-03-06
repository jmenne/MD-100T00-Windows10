# Practice Lab: Using GPOs

## Summary

In this lab you will use GPOs to configure settings in Windows.

### Scenario

A company policy states that a sign-in disclaimer on the Windows 10-based
computer in the developer area is established that identifies it as a
testing-only computer for A. Datum Corporation. Also the EFS services must be
disabled. You decide to use a domain wide GPO that is scoped to LON-CL2.

### Task 1: Create GPO to configure devices

1. Sign in to **LON-DC1** as **Adatum\\Administrator** with the password
    **Pa55w.rd**

1. On **LON-DC1**, in Server Manager, in the **Tools** list, select **Group
    Policy Management**.

1. Maximize the Group Policy window. In the console tree, expand **Forest:
    Adatum.com**, expand **Domains**, and then expand **Adatum.com**. Select the
    **Group Policy Objects** node.

1. Right-click the **Group Policy Objects** node, and then select **New**.

1. In the **New GPO** dialog box, in the **Name** box, type **Win10 Display**,
    and then select **OK**.

1. In the details pane, right-click **Win10 Display**, and then select
    **Edit**.

1. Maximize the new Group Policy Management Editor window.

1. In the console tree, under **Computer Configuration**, expand **Policies**,
    expand **Windows Settings**, expand **Security Settings**, expand **Local
    Policies**, and then select **Security Options**. In the details pane,
    scroll down, and then double-click

    **Interactive Logon: Message title forusers attempting to log on**.

1. In the **Interactive Logon: Message title for users attempting to log on**
    dialog box, enable the option, type **Attention!** in the box, and then
    select **OK**.

1. In the details pane, double-click **Interactive Logon: Message text for
    users attempting to log on**.  

    _Note: It is just above the item from step 9._

1. In the **Interactive Logon: Message text for users attempting to log on**
    dialog box, select the **Define this policy setting in the template** check
    box, type **This computer is used for Adatum Corporation development and
    testing only! Do not use on the production network!** in the box, and then
    select **OK**.

1. In the console tree, under **Computer Configuration**, expand
    **Preferences**, expand **Control Panel Settings**, and then select
    **Services**.

1. In the details pane, right-click the empty space, select **New**, and then
    select **Service**.

1. In the **New Service Properties** window, select the following by using the
    drop-down arrow:

    - Startup: **Disabled**

    - Service Name: **EFS**

    - Service action: **Stop service**

1. Select the **Common** tab.

1. Select the **Item-level targeting** check box, and then select
    **Targeting**.

1. In the **New Item** list, select **Computer Name**.

1. In the **Computer name** box, type **LON-CL2**, and then select **OK**
    twice.

1. Close the Group Policy Management Editor.

1. In the Group Policy Management Console, in the console tree, right-click **Adatum.com**, and then select **Link an Existing GPO**.

1. In the Select GPO window, select **Win10 Display**, and then select **OK**.

1. Close the Group Policy Management Console and close all open windows.

### Task 2: Test the GPO

1. Sign in to **LON-CL2** as **Adatum\\Administrator** with the password
    **Pa55w.rd**

1. On **LON-CL2** select **Start** and type **`cmd`**. Press **Enter**

1. At the command prompt, type **gpupdate /force**, and then press Enter.

1. After the update reports success, type **`shutdown /r /t 0`** and then press Enter

1. Note that **LON-CL2** restarts.

1. Note that the message "Attention! This computer is used for Adatum
    Corporation development and testing only! Do not use on the production
    network!" appears. Select **OK**, and then sign in as
    **Adatum\\Administrator** with the password **Pa55w.rd**.

    _Note: In the rest of this lab in this module, you must select OK to
    accept the message._

1. On the taskbar, in the **Type here to search** box, type **Services**, and
    then press **Enter**.

1. In the **Services** details pane, scroll down until you see the **Encrypting
    File System (EFS)** service. Confirm that it is disabled.

1. Close all open windows.

**Results:** After completing this exercise you have created a GPO to configure
settings in Windows.

## END OF LAB
