# Understanding and Installing VirtualBox Guest Additions

VirtualBox Guest Additions are a package of programs and drivers which are installed onto guest operating systems 
running in virtual machines to improve the guest's performance and usability.  

## VirtualBox Guest Additions Features
When installed on a guest operating system, VirtualBox Guest Additions provide the following enhancements:

* **Host/Guest Time Synchronization** - Ensures that the system times of the guest and host are synchronized at regular intervals thereby preventing the virtualization time drift often encountered with guest operating systems running in virtual machines.  
* **Seamless Window Support** - One of the most compelling features of VirtualBox, seamless windows allow the window of an application running on the desktop of a guest operating system to be placed on the desktop of the host operating system such that it appears to be running directly on the host rather than within a virtual machine.  
* **Shared Folders** - Provides the ability to make folders/directories on the host file system available to guest operating systems running inside VirtualBox virtual machines. This topic is covered in more detail in the VirtualBox Shared Folders chapter.  
* **Shared Clipboard** - Allows the guest and host operating systems to access each others cut and paste clipboards enabling easy transfer of text and objects between the two environments. Control over clipboard access is controlled via the VirtualBox preferences settings, details of which can be found in the Configuring the VirtualBox Environment chapter.  
* **Automated Windows Logon** - Guest additions allow Windows login credentials to be stored in a master repository and used to automatically log into one or more Windows guests.  
* **Mouse Pointer Enhancements** - Without the guest additions installed, clicking in a virtual machine window captures the mouse focus and locks it into the window until the host key (the right hand Ctrl key by default) is pressed. With guest additions installed, it is no longer necessary to click in the virtual machine window to establish focus and press the host key to release focus. Instead, the focus will switch automatically between the guest and host as the pointer travels in and out of the virtual machine window.  
* **Improved Video Support** - The guest additions provide improved video performance and a greater range of video modes and resolutions. In the case of Linux guests, the additions also cause the desktop environment of the guest to resize and change resolution when the virtual machine window is resized.  

## Support Guest Operating Systems
No support Mac OS X
