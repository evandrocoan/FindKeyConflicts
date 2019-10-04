# FindKeyConflicts
Assist in finding key conflicts between various plugins. This plugin will report back shortcut keys that are mapped to more than one package. This does not guarantee that the listed plugins are necessarily in conflict, as details, such as context, are ignored. This is simply a tool to help assist what plugins may be conflicting.


## Installation

### By Package Control

1. Download & Install **`Sublime Text 3`** (https://www.sublimetext.com/3)
1. Go to the menu **`Tools -> Install Package Control`**, then,
   wait few seconds until the installation finishes up
1. Now,
   Go to the menu **`Preferences -> Package Control`**
1. Type **`Add Channel`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
   input the following address and press <kbd>Enter</kbd>
   ```
   https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json
   ```
1. Go to the menu **`Tools -> Command Palette...
   (Ctrl+Shift+P)`**
1. Type **`Preferences:
   Package Control Settings – User`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
   find the following setting on your **`Package Control.sublime-settings`** file:
   ```js
       "channels":
       [
           "https://packagecontrol.io/channel_v3.json",
           "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
       ],
   ```
1. And,
   change it to the following, i.e.,
   put the **`https://raw.githubusercontent...`** line as first:
   ```js
       "channels":
       [
           "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
           "https://packagecontrol.io/channel_v3.json",
       ],
   ```
   * The **`https://raw.githubusercontent...`** line must to be added before the **`https://packagecontrol.io...`** one, otherwise,
     you will not install this forked version of the package,
     but the original available on the Package Control default channel **`https://packagecontrol.io...`**
1. Now,
   go to the menu **`Preferences -> Package Control`**
1. Type **`Install Package`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
search for **`FindKeyConflicts`** and press <kbd>Enter</kbd>

See also:
1. [ITE - Integrated Toolset Environment](https://github.com/evandrocoan/ITE)
1. [Package control docs](https://packagecontrol.io/docs/usage) for details.


## Usage
This plugin can be run through specifying commands on the command palette. The commands are listed in alphabetical order, beginning with modifiers (alt, cntl, shift, super), followed by keys. The commands are as follows:

`FindKeyConflicts: All Key Maps to Quick Panel`:

Displays all key mappings in a quick panel. Selecting an entry will open a buffer with additional details about the key binding.

`FindKeyConflicts: All Key Maps to Buffer`:

Displays all key mappings in a buffer.

`FindKeyConflicts: (Direct) Conflicts to Quick Panel`:

This command finds all direct key conflicts, and displays them on the quick panel. The last package listed under the command is the source for the command being run, if it is not limited by context. Selecting a particular entry will open a buffer with details about that key binding.

`FindKeyConflicts: (Direct) Conflicts to Buffer`:

Display key direct conflicts in a view. Using this will give a better idea of how commands conflict, as the context for the commands will be included in the output. The last package listed for a particular binding is the command that is used, if it is not limited by context.

`FindKeyConflicts: Overlap Conflicts`:

Displays key bindings that overlap with mutli part key bindings in a buffer. For example, if `["ctrl+t"]` exists as one binding and `["ctrl+t", "t"]`, exists as another binding, this will be displayed.

`FindKeyConflicts: All Conflicts`:

Displays all conflicts in a buffer. This option will include both direct and overlapping conflicts.

`FindKeyConflicts: Single Package Conflicts`:

Displays conflicts that involve the selected package.

`FindKeyConflicts: Multiple Package Conflicts`:

Displays conflicts that involve the selected packages. Select `(Done)` when you are done selecting packages. You may use `(View Selected)` and `(View Packages)` to view the selected packages and the package list respsectively.  Also, you may remove packages from the selected list by pressing `enter` when viewing the selected packages list.

`FindKeyConflicts: Command Search`:

Display a list of the packages containing keymap files. After selecting a package, a list of commands will be displayed in the quick panel. Selecting a command from the subsequent list will run the command.

## Settings
`ignored_packages`:

An array containing packages to ignore. Note that the `ignored_packages` in the Preferences are automatically added to this list.

`ignore_single_key`:

Boolean value specifying if single key bindings should be ignored. False by default.

`ignore_patterns`:

Array containing key patterns to ignore. These should follow the same guidelines as specifying key bindings.

`display_internal_conflicts`:

Boolean value used to determine if internal command conflicts to a package should be displayed.

## Notes
Thanks to [bizoo](https://github.com/bizoo) for sharing their work with me.
Thanks to [getify](https://github.com/getify) for the json minifier.
Thanks to [facelessuser](https://github.com/facelessuser) for the strip dangling commas work.
