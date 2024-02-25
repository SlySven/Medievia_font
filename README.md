# Medievia_font
A reworking of the font (see http://www.medievia.com/fonts.html) used by the Medievia MUD Game.

In **[Mudlet](https://github.com/Mudlet/Mudlet.git)** see https://github.com/Mudlet/Mudlet/pull/7161 for the PR that creates a new text *codec* in the `TTextCodec` class to use **this** version of the **Medievia True Type font** [original here](http://www.medievia.com/fonts/MedSansMono.ttf) as modified herein.

Medievia currently seems to use a modification of the [Window-1252](https://en.wikipedia.org/wiki/Windows-1252) encoding; however some additional character codes that are *not* defined by that encoding have been used which are (rightly) rejected by Mudlet.

Work on the new codec has been done by myself and the issue of glyphs having bad Unicode codepoints (e.g. as C1 control characters) should have been resolved. The initial workaround is to ensure copies of the problematic glyphs (at least) are moved up into the Private Use Area in the BMP of the Unicode range and to modify the new codec to use those codepoints instead. However long term it will be desirable to enhance Mudlet so that it can map Extended ASCII characters - like the Medievia specific ones - out of the BMP into one of the Higher [Private Use Areas](https://en.wikipedia.org/wiki/Private_Use_Areas) in Plane 15 or 16. If that is done then the graphemes concerned could even be registered with the [Under-Conscript Unicode Registry](https://www.kreativekorp.com/ucsur/).

When using this font with Mudlet it will be required to:
* Install this font into the system - or place it into the `fonts` or a subdirectory below that of the `mudlet-data` sub-directory of the user's "Home" directory. 
* Select the "m Medievia {Custom codec for that MUD}" option for the "Server data encoding:" setting on the first "General" tab of the preferences dialogue.
* Select the "CP437 (OEM Font)-like" option for the "Display control characters as:" setting on the third "Main display" tab of the preferences dialogue.
