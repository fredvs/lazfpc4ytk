Lazarus and fpc patched for using ytk widget in place of gtk2.

The ytk source comes from https://gitlab.com/fifr/fpc/-/tree/ytk?ref_type=heads
and used by fpc-ootb: https://github.com/fredvs/freepascal-ootb/tree/ytk .

The lazarus-ytk source comes from https://gitlab.com/fifr/lazarus/-/tree/ytk?ref_type=heads .

The binary of ytk-fpc libraries comes from https://gitlab.com/fifr/ytk-fpc and added in Lazarus folder.

Download the release then load startlazarus.

For the fpc source, assign directory path-of/freepascal-ootb-ytk

The fpc source (freepascal-ootb-ytk) are in https://github.com/fredvs/lazfpc4ytk/

In menu Tools/Options/Compiler executable insert:

 $(LazarusDir)/fpc-ootb-ytk-64/fpc-ootb-64

Click OK and ignore the warning message.

For your projects, in Project options, Custom options add:

(for static linking)
-Fl$(LazarusDir)/ytk_sta

 or

(for dynamic linking)
-Fl$(LazarusDir)/ytk_dyn
-k"-rpath=$ORIGIN/ytk"

For dynamic linking, copy the dir /lazarus/ytk into the root directory of your executable.
