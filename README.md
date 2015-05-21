unity-tags
==========

Geany support for the Unity API


About
-----

The unity-tags project provides tag support (keyword autocomplete and function 
argument hinting) for the Unity Scripting API 
(<http://docs.unity3d.com/ScriptReference/>) in the Geany editor 
(<http://www.geany.org/>). There is a .tags file for use with Unity 5 out of 
the box; in addition, a Python script is provided to generate a .tags file from 
a local installation of Unity.


Installation
------------

Copy unity.cs.tags to the Geany tags config directory, usually in the following 
locations:

*   `C:\Users\UserName\Roaming\geany\tags` (Win 7)
*   `C:\Documents and Settings\UserName\Application Data\geany\tags` (Win XP)
*   `~/.config/geany/tags` (*nix)

The Unity API autocomplete and hinting features will then be available in C# 
files after a restart of Geany.

To use the tags immediately, find *Load Tags* under the *Tools* menu and browse 
to unity.cs.tags. More information can be found at 
<http://www.geany.org/manual/current/#tags>.


Using Geany in Unity
--------------------

To set Geany as your Unity script editor:

1.  Open *Edit > Preferences...* and switch to the *External Tools* tab.

2.  Click on the **External Script Editor** dropdown and browse to Geany.

3.  Set **External Script Editor Args** to `+$(Line) "$(File)"`.

If you are using Unity through Wine or PlayOnLinux, follow these instructions 
instead:

1.  Place the following code in a file called geany.sh:
    
        #!/bin/sh
        /usr/bin/geany +$2 "`wine winepath -u "$1"`"

2.  Open *Edit > Preferences...* and switch to the *External Tools* tab.

2.  Click on the **External Script Editor** dropdown and browse to geany.sh 
    from step 1.

3.  Set **External Script Editor Args** to `"$(File)" $(Line)`.

For more information, see 
<http://wiki.unity3d.com/index.php/Running_Unity_on_Linux_through_Wine#Editing_scripts_with_a_native_Linux_script_editor>.


Generating tags manually
------------------------

The .tags file provided should be accurate for the Unity 5 Scripting API. If 
desired, the Python script generate.py can be used to generate tags for a local 
installation of Unity.

1.  Find the ScriptReference directory of the local Unity installation. On 
    Windows, this is usually `C:\Program 
    Files\Unity\Editor\Data\Documentation\en\ScriptReference`.

2.  Run `python generate.py SCRIPTREFERENCE FILE` where `SCRIPTREFERENCE` in 
    the same directory as generate.py, where `SCRIPTREFERENCE` is the path 
    found in step 1 and `FILE` is the name of the file to output (which should 
    end in .cs.tags).

3.  Install as described in the section above.
