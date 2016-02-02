  * .NET 2.0 runtime
  * ComUtilities.dll registration
  * Building ComUtilities in VS 2008
  * Click Once
  * Registeration-free ComUtilities COM interop
  * csExWBDLMan.dll registeration

## ComUtilities COM library ##

ComUtilities.dll is written in VC++ 8.0 (2005) using ATL 8.0 (ATL is not included in the Express edition) and is statically linked to ATL. This control is a replacement for the csExWBDLMan.dll library which was written in VC++ 6.0 using ATL 3.0. In the future, any additional features will be added to this library.

**Before opening the solution or running the demo using ComUtilities.dll**

  * Running Vista, please make sure that you are logged in as admin and running the regsvr32.exe as admin
  * ComUtilities.dll depends on CRT. This can be resolved either by adding C++ feature to your VS installation or installing Microsoft Visual C++ 2005 Redistributable Package
  * Copy ComUtilities.dll located in the Release sub folder to your system directory
  * Register ComUtilities.dll using regsvr32.exe, then Open the solution

Example: Assuming the system dir path is C:\windows\system32\
```
regsvr32.exe C:\windows\system32\ComUtilities.dll
```

To eliminate dependencies on ATL8.dll, go to "Project->ComUtilities Properties". When "ComUtilities Property Page" is displayed, expand "Configuration Properties" node and select "General". In the right pane, change "Use of ATL" option to "Static Link to ATL" choice. Apply changes, and rebuild solution. By default, all ComUtilities builds use "Static Link to ATL" choice.

## Building ComUtilities in VS 2008 ##

  1. Remove IUri and IInternetProtocolEx interface definitions from ComUtilities.idl
  1. In stdafx.h, change define _WIN32\_IE 0x0600 to define_WIN32\_IE 0x0700
  1. Rebuild the project

**Warning D9035**

To remove warning D9035 : option 'Wp64' has been deprecated and will be removed in a future release. Go to Project menu->ComUtilities Properties, in the ComUtilities Proprty Pages, select the C/C++ node in the tree then in the right pane change "Detect 64-bit Portability Issues" to No.

## Click Once ##

ComUtilities project properties is set to embed the manifest file withiin the output. This may cause problems when deployed using click once. To change this setting, go to "Project->ComUtilities Properties". When "ComUtilities Property Page" is displayed, expand "Configuration Properties" node, then expand "Manifest Tool" and select "Input and Output". In the right pane, change "Embed Manifest" option to No. Apply changes, and rebuild solution.

## [Registeration-free ComUtilities COM interop](http://groups.google.com/group/csexwb/web/registeration-free-comutilities-com-interop) ##

## csExWBDLMan COM library ##

csExWBDLMan is written in VC++ 6.0 using ATL 3.0. It is compiled with minimum dependencies, i.e. no MFC, std::, CString. To recompile, you need to Copy AuxCrt.cpp file from csExWB\COM\_Component\_Source\_Binaries\AtlAux\Shared to the VC++6 ATL\Include\ directory.

The library is used to allow the client to employ the IDownloadManager implementation of csExWBDLMan library. In addition, the library implements the PassthroughAPP package by Igor Tandetnik, which enables the client to intercept all HTTP and HTTPS request and responses. The last functionality offered by the library is the ability to set any of the available windows hooks with the option to cancel a call. This functionality is used to stop dialogs launched using the showModelessDialog() and showModalDialog() methods. The library can be used in any other project that needs to set a global windows hook or view HTTP and HTTPS headers, as long as a valid window handle is supplied.

**Before opening the solution or running the demo, you need to register this library**

  * Copy csExWBDLMan.dll located in the csExWB\COM\_Component\_Source\_Binaries\ReleaseMinDependency sub folder to your system directory
  * Register csExWBDLMan.dll using regsvr32.exe
  * Open the solution

Example: Assuming the system dir path is C:\windows\system32\
```
regsvr32.exe C:\windows\system32\csExWBDLMan.dll
```

