# CUSTOM CHANGES, in branch custom-release-3.0.5

## Middle mouse button
Clicking on middle mouse button sets the Zoom level back to 'Normal' (a.k.a. Default Zoom)

## Mouse scroll wheel

Have mouse scroll wheel directly scroll the current track, instead of requiring a shift to also be pressed. Also, whatever the previous mouse scroll wheel behavior was should now be swapped with the Shift-mouse scroll wheel behavior.

## Page Backward/Forward

Adding Page Backward (same functionality as PageUp key) and Page Forward (same functionality as PageDown key) to the menu system allows us to customize/redefine keys to have PageUp/PageDown functionality. e.g. you could redefine the keystroke combo Shift-Left to do a Page Backward and the keystroke combo Shift-Right to do a Page Forward. Also, it allows 'Page Backward' and 'Page Forward' to be used in Macros.

## Default Directories - default to import path

If default directories are NOT specified (i.e. left blank) for "Open", "Save", "Import", "Export", "Macro Output", instead of defaulting to last used, default to the  initial import path directory. So, if you imported /home/gino/work/chapter-03/foobar.wav , and you then want to export as an mp3, the export file dialog will use /home/gino/work/chapter-03 as the default directory, for the export. etc.. Note that if you DO specify a directory for any of the above types ("Open", "Save", "Import", "Export", "Macro Output"), that directory will TAKE PRECEDENCE over the initial import path, for that type.

## Import and UndoManager's save state

Prevent Imports from changing the save state of the UndoManager (save state of the UndoManager determines whether Audacity asks us if we want to save the project, when we close the project window).

## Export and UndoManager's save state

After a successful export, tell UndoManager that we have no unsaved changes (save state of the UndoManager determines whether Audacity asks us if we want to save the project, when we close the project window).

## Decorating project's title

Update title of project,using '**' to denote it has unsaved changes. This is similar to how Emacs shows that an edited file has unsaved changes. Note that an unsaved change may occur even if you run a macro that does not actually change the audio file.

## mod-script-pipe.so

I believe the loadable shared library modules, such as mod-script-pipe.so are installed into the 'modules' subdirectory of: installPrefix +"/lib/audacity", by 'make install', so it makes sense to add this path here, so that Audacity can find the loadable shared library modules, at runtime.
