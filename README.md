# NativeScript 5.3 problem with Unicode characters on the first page

This app is a demonstration of a bug in NativeScript 5.3 on iOS.

If the XML of the app's first page (the one defined in the frame's `defaultPage`) includes Unicode characters outside of the basic ASCII set (for example Polish `Ł`) then some of the properties defined in the XML would get set to `undefined` instead of their actual value. So far I observed this behavior with `returnKeyType` and `autocapitalizationType` on `TextField`. If the properties are present in XML, NativeScript tries to set their values to `undefined` (instead of the actual values defined in XML), resulting in the app crashing. The problem doesn't occur if there is no extended Unicode character present in the same XML file and only occurs with the very first page, only on iOS.

This demo is based on NativeScript Hello World template (NativeScript+TypeScript). The only file that was modified to demonstrate the problem is `app/main-page.xml`. I left all other files untouched. The app should immiedietly crash after launching. Removing the `Ł` should stop the crashing.
