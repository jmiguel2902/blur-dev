# Softimage extra instructions #

There are a few extra steps required to use BlurOffline in Softimage.

## Remove the Qt dlls installed with Softimage ##
Newer versions of Softimage come with qt dlls that will prevent the tools from running, they need to be moved outside of the bin folder.
  1. Navigate to the softimage bin directory.
    1. Right click on the desktop icon for Softimage and select Properties.
    1. Click on Open File Location. This should take you to the Application\bin folder
  1. Create a new folder called qt\_backup
  1. Move these files into the newly created folder.
    * QtCore4.dll
    * QtGui4.dll
    * QtOpenGL4.dll
    * QtXml4.dll

## Use python installed with windows ##
In Softimage 2012 and newer you need tell xsi to not use its own python. Skip this step for older versions of Softimage
  1. In Softimage, open the preferences. Select File -> Preferences...
  1. In the preferences dialog select Scripting
  1. Uncheck Use Python Installed with Softimage(Windows Only)
## Connect to the workgroups ##
  1. In Softimage, open the Plug-in Manager. Select File -> Plug-in Manager...
  1. Select the Workgroups tab.
  1. Add the workgroups **in this order**.
    * C:\blur\dev\offline\workgroups\xsi\_blurdev
    * C:\blur\dev\offline\workgroups\xsi\_common
    1. Repeat these steps for each path.
      1. Click Connect...
      1. Paste the folder path in the text box labeled Pick the root location of an existing workgroup. Then click Ok

## Restart Softimage ##

# Offsite Blur Employees #

If you receive the following error when trying to open a file given to you by Blur Studiomax will crash when you try to save.

```
-- Error occurred in PxSetPhysXPanelInterfaceFromGlobalParams(); filename: C:\Program Files\Autodesk\3ds Max 2012\stdplugs\stdscripts\(MassFX)\px_PhysXPanel.ms; position: 32995; line: 1218
--  Frame:
--   called in px_filePostOpen(); filename: C:\Program Files\Autodesk\3ds Max 2012\stdplugs\stdscripts\(MassFX)\px_watcher.ms; position: 1198; line: 64
--  Frame:
--   curType: undefined
--   scale: undefined
--   pxType: undefined
--   called in anonymous codeblock
--  Frame:
>> MAXScript Callback script Exception:
-- Unknown system exception <<
```

To fix this you need to install the Nvidia PhysX plugin.

Unfortunately I cant just provide you with a direct download link. First follow this [link](http://supportcenteronline.com/ics/support/default.asp?deptID=1949) and login/create a account. After that you can click on these links for the installer you need for your install of max. [3ds Max 2012 64bit](http://supportcenteronline.com/ics/support/DLRedirect.asp?fileID=123798) [3ds Max 2012 32bit](http://supportcenteronline.com/ics/support/DLRedirect.asp?fileID=123797)

# Unable to update the path environment variable #

Because of a limitation of the NSIS language we use to compile the installers if your path is longer than 1024 characters or is empty we can not add the path required to install the Qt dlls.

If you received the message:
```
Unable to update the path environment variable automatically.
You will need to add C:\windows\system32\blur64; at the START path environment variable. Including the semi-colon.

You can copy this message using Ctrl+C.
```
or
```
Unable to update the path environment variable automatically.
You will need to add C:\blur\common; at the START path environment variable. Including the semi-colon.

You can copy this message using Ctrl+C.
```

You will need to manually update your system path. You only need to update this the first time you install the 32bit and 64bit installers, after that you can ignore this message.

  1. Click on the start menu.
  1. Type sysdm.cpl in the search area and hit enter.
  1. The System Properties dialog will open, click on the Advanced tab.
  1. Click on the Environment Variables... button
  1. Locate path in the list box under System Variables and select it.
  1. Click the Edit... button.
  1. The Edit System Variable dialog will show up.
  1. **Insert** the correct path at the **Start** of Variable value:. Make sure you don't remove anything unless you know what you are doing.
    * The correct path for 64bit installs of BlurOffline is "C:\windows\system32\blur64;" excluding the quotes. Make sure you include the semi-colon.
    * The correct path for 32bit installs of BlurOffline is "C:\blur\common;" excluding the quotes. Make sure you include the semi-colon.