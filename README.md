# SublimeText - File History #

**Sublime Text 2 and 3** plugin to provide access to the history of accessed files - project-wise or globally. The most recently closed file can be instantly re-opened with a keyboard shortcut or the user can search through the entire file history within the quick panel (including file preview and the ability to open multiple files).  

## Features ##

Keeps a history of the files that you have accessed in SublimeText (on both a per-project and global level).  The most recently closed file can be instantly re-opened with a keyboard shortcut or the user can search through the entire file history in the quick panel.  

Overview of features:
* [Settings][settings] file to customize the functionality. 
* When re-opening a file from the history, choose the position to open it in: the ```first``` tab, the ```last``` tab, the ```next``` tab or in the position that it was when it was closed
* Display a preview of the file while looking through the file history in the quick panel (only Sublime Text 3)
* Choose target location where the file history should be saved
* Optionally remove any non-existent files while looking through the file history (when previewed or opened)
* Optionally clean up the history on start-up
* Optionally display the quick panel entries with a monospaced font
* Open multiple history entries from the quick panel with the ```right``` key
* Path exclude and re-include patterns (regex) that can be extended in project settings. 

Originally obtained from a [gist][gist] by Josh Bjornson.


## Installation ##

Install [Package Control][pck-ctrl]. Once installed, bring up the Command Palette (`Command-Shift-P` on OS X, `Ctrl-Shift-P` on Linux/Windows). Select `Package Control: Install Package` and then select `File History` when the list appears. Package Control will automagically keep the plugin up to date with the latest version.


## Usage ##

To use the plugin, open the Command Palette and search for `File History:`.

When you opened a panel you can use the <kbd>right</kbd> key to open the file and keep the panel open, or <kbd>Ctrl/Cmd</kbd> + <kbd>delete</kbd> to remove the selected file from the history.

For default keymap definitions, see [Default.sublime-keymap][keymap] ([OSX][keymap-osx]).

For the available and default settings, see [Settings](#settings).

### Images ###

*The popup for the current project only*
![example1][img1]

*The popup for the global history with text*
![example1][img2]

### Commands ###

**open_recently_closed_file** (Window)

Opens a popup with recently closed files or reopens the lastly closed view if `show_quick_panel == False`.

>   *Parameters*

>   - **show_quick_panel** (bool) - *Default*: `True`

>   - **current_project_only** (bool) - *Default*: `True`

**cleanup_file_history** (Window)

Checks the current project or the whole history for non-existent files and removes them from the history kept.

>   *Parameters*

>   - **current_project_only** (bool) - *Default*: `True`

**reset_file_history** (Window)

Removes all file history data.

### Customization via settings file ###

**Important**: At the moment you need to restart Sublime Text after editing the [settings][settings] file (because the settings are cached by the Sublime Text API).

The following functionality can be customized in the [settings][settings] file:

* `history_file` - Path to store the history entries in (relative to the sublime packages path)
    - default value is `"User/FileHistory.json"`
* `global_max_entries` - Maximum number of history entries we should keep (older entries truncated)
    - default value is `100`
* `project_max_entries` - Maximum number of history entries we should keep (older entries truncated)
    - default value is `50`
* `use_saved_position` - If we should try to use the saved position of the file
    - default value is `true`
* `new_tab_position` - Which position to open a file at when the saved index is no longer valid (or `use_saved_position` is set to `false`)
    - default value is `"next"`
    - available options are  `"next"`, `"first"` and `"last"`
* `show_file_preview` - Should we show a preview of the history entries?
    - default value is `true` *(not available on ST2)*
* `remove_non_existent_files_on_preview` - Remove any non-existent files from the history (when previewed or opened)
    - default value is `false`
* `cleanup_on_startup` - Remove any non-existent files on startup
    - default value is `true`
* `monospace_font` - Should a monospace be used in the quick panel?
    - default value is `false`
* `timestamp_show` - Should the last access's timestamp be shown in the quick panel?
    - default value is `true`
* `timestamp_relative` - Show a relative time value instead of absolute
    - default value is `true`
* `timestamp_format` - The format of the timestamp
    - default value is `%Y-%m-%d @ %H:%M:%S`
* `timestamp_mode` - Which timestamp to display? ("history_access" - last opened/closed timestamp, "filesystem" - the file's last modified timestamp)
    - default value is `filesystem`
* `prettify_history` - Should the file history be saved as nicely formatted json?
    - default value is `false`
* `debug` - Print out the debug text to the console?
    - default value is `false`

You can **extend** the `path_exclude_patterns` and `path_reinclude_patterns` in your project settings.

For this, add a `"file_history"` dictionary to your project's settings and then one or both of the settings to that. Example:

```json
{
    "folders": [
        {
            "path": "."
        }
    ],
    "settings": {
        "file_history": {
            "path_exclude_patterns": ["/bin/"],
            "path_reinclude_patterns": ["\\.compiled$"]
        }
    }
}
```

[gist]: https://gist.github.com/1133602
[github]: https://github.com/FichteFoll/sublimetext-filehistory "Github.com: FichteFoll/sublime-filehistory"
[zipball]: https://github.com/FichteFoll/sublimetext-filehistory/zipball/master
[pck-ctrl]: http://wbond.net/sublime_packages/package_control "Sublime Package Control by wbond"

[settings]: FileHistory.sublime-settings "FileHistory.sublime-settings"

[keymap]: Default.sublime-keymap "Default.sublime-keymap"
[keymap-osx]: Default%20%28OSX%29.sublime-keymap "Default (OSX).sublime-keymap"

[img1]: http://i.imgur.com/B5ViHHv.png
[img2]: http://i.imgur.com/y40CEFo.png

