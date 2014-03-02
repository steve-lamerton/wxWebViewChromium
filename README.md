wxWebViewChromium
=================

wxWebViewChromium is a Chromium backend for wxWebView using the Chromium
Embedded Framework. For more detailed information, please see the project
[wiki][1].

Requirements
------------

* [wxWidgets][2]: r73369 / 2.9.5  or greater
* [Chromium Embedded Framework][3]:  1.963.439, 1.1025.607, 1.1180.832, 
   1.1364.1123, 3.1364.1188, 3.1453.1255 or 3.1547.1412.

Compiling
---------

The backend is made up of five files, a source and header file for CEF1
and CEF3 and a selection header. Simply compile these alongside your
project and add the path to your Chromiumium Embedded Framework
install to your include directory list and link to `libcef_dll_wrapper`
and `libcef`.

Before compiling, you need to install [CMake 3.0][4]. Since the [issue][5], cmake 
supports wxWidgets 2.95 or greater in version 3.0.

Run the following commands:

```
cd your_path_to_wxWebViewChromium
cmake -DCEF_ROOT_DIR=your_path_to_CEF .
```
Then the project files will be generated, open it and build it.

Using
-----

To use wxWebViewChromium first register the backend with wxWidgets

    wxWebView::RegisterFactory(wxWebViewBackendChromium, 
                               wxSharedPtr<wxWebViewFactory>
                               (new wxWebViewFactoryChromium));

It can then be used in a standard `wxWebView::New` call

    wxWebView* webview = wxWebView::New(this, wxID_ANY,
                                        "http://www.wxwidgets.org/",
                                        wxDefaultPosition, wxDefaultSize,
                                        wxWebViewBackendChromium);

[1]: https://github.com/steve-lamerton/wxWebViewChromium/wiki
[2]: http://www.wxwidgets.org
[3]: http://code.google.com/p/chromiumembedded/
[4]: http://www.cmake.org/files/dev/
[5]: http://public.kitware.com/Bug/bug_relationship_graph.php?bug_id=14587&graph=relation
