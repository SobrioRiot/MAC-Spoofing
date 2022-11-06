Network adapters come preconfigured from the factory with their own globally unique physical or Media Access Control (MAC) address,
which helps them identify themselves when communicating with other networking components. 
Though you can’t change the permanent MAC address actually stored by the network adapter, 
you can make it provide a different address using your operating system (OS). We’ll see how to do this with Windows.

There are a few reasons you might want to simulate another MAC address,including troubleshooting and testing your network. 
From a security standpoint, it’s a good idea to understand the technique, referred to as “MAC spoofing,” because hackers also find it useful to get around
MAC address filtering. This filtering is used by some network administrators to help control which devices end-users can connect to the network or even 
as another layer of security against hackers. If nothing else, understanding MAC spoofing will help you demonstrate to yourself or others just how easy it
is to change your address and bypass MAC-based security measures.


# Changing Your MAC Address in Windows

Before you change the MAC address, you might want to write down the original one. One way to bring it up is to open the Network Connections window, 
double-click the desired network adapter, and on the Network Connection Status window, click the Details button to look for the Physical Address. 
Another way is to open a Command Prompt, type ipconfig /all, find the desired Network Connection, and look for the Physical Address.

The more user-friendly way to change your MAC address in Windows is via the Network Adapter Properties. You probably want to try this first, 
leaving the Registry method as a last resort. When you’re ready, give it a try:


   >Open the Network Connections window and double-click the desired network adapter.
    On the Network Connection Status window, click the Properties button.
    On the Network Connection Properties window, click the Configure button.
    On the Network Adapter Properties window, select the Advanced tab.
    Choose the Network Address or Locally Administered Address Property, 
    select the Value radio button, and then enter the new MAC address. 
    If using Windows 7, you must use a special format as we’ll note in a moment. 
    Click OK to save changes.

If you don’t have success changing your MAC via the Network Adapter Properties, you might want to try using the Windows Registry.
However, you should first copy down the original address before proceeding so you’ll have it if you want to restore it. 
When you’re ready, here’s how to edit the Windows 
Registry setting:


   >Open the Registry Editor by typing regedit into the Start Menu field or Run prompt.
    Browse to the following key: 
    HKEY_LOCAL_MACHINESYSTEMCurrentControlSetControlClass{4D36E972-E325-11CE-BFC1-08002BE10318}

   >You should see 4-digit sub-keys, such as 0000, 0001, 0002, 0003 and so on. 
    Find the right network adapter by referencing the DriverDesc 
    attribute of each sub-key.
    Once you find the desired adapter, see if it contains a NetworkAddress attribute. 
    If not, create a new String (REG_SZ) and 
    label the Value Name as NetworkAddress.
    To edit the NetworkAddress, double-click it and type the desired MAC address 
    (without separators) in as the Value Data. 
    If using Windows 7, use the special format discussed next.

For either method in Windows 7, the second character of the MAC address must be a 2, 6, A, or E, such as the following examples:

    x2-xx-xx-xx-xx-xx
    x6-xx-xx-xx-xx-xx
    xA-xx-xx-xx-xx-xx
    xE-xx-xx-xx-xx-xx

Now you should double-check you’re using the new MAC address, using one of the methods we discussed in the beginning of the section.


