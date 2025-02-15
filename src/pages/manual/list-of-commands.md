---
index: 80
category: "hacking"
toc: false
path: "/manual/list-of-commands"
title: "List of Commands"
---

Inkdrop provides a bunch of commands to allow you to associate arbitrary interactions with the features.
You can bind them with [keystrokes](/reference/keymap-manager), [menu](/reference/menu-manager) and [context menu](/reference/context-menu-manager) from [plugins](/manual/plugin-word-count), [the init file](/manual/the-init-file) or [keymap config file](/manual/customizing-keybindings).
Note that some commands like `core:open-note` require parameters so you have to invoke them programmatically with [CommandRegistry](/reference/command-registry) like so:

```js
inkdrop.commands.dispatch(document.body, 'core:open-note', { noteId: 'note:uugSvPq5r' })
```

## Table of Contents

* [Application commands](#application-commands)
* [Core commands](#core-commands)
* [Editor commands](#editor-commands)
* [Export commands](#export-commands)
* [Import commands](#import-commands)
* [View commands](#view-commands)
* [Window commands](#window-commands)

## Application commands

Special commands that run in the main process to control the Inkdrop app.
To invoke them, do like so:

```js
import { ipcRenderer } from 'electron'
ipcRenderer.send('command', 'application:about', {})
```

### application:about

Shows a dialog about Inkdrop.

### application:bring-all-windows-to-front

* macOS only

Arranges windows listed in the Window menu in front of all other windows

### application:hide

* macOS only

Hides Inkdrop windows

### application:hide-other-applications

* macOS only

Hides all apps, except Inkdrop

### application:inspect

Shows a Developer Tools and inspects an element

### application:logout

Logs out from the currently authenticated account

### application:minimize

* macOS only

Minimizes Inkdrop application

### application:open-preferences

Opens up the preference window

### application:open-website

Opens up the Inkdrop website

### application:quit

Quits the app

### application:report-issue

Opens up the Inkdrop forum

### application:show-credits

Opens up the list of software licenses

### application:unhide-all-applications

* macOS only

Unhides all apps, including Inkdrop.

### application:view-help

Opens up the documentation website

### application:zoom

* macOS only

Toggles the size and location of the window between its standard state and its user state

## Core commands

### core:copy

Copy the selected text to clipboard

### core:copy-image

Copy the target element's image to clipboard

### core:copy-note-link

Copy links to notes currently selected on the note list as Markdown

### core:cut

Delete the selected text and copy it to clipboard

### core:delete-note

Move notes currently selected on the note list to trash.
If the notes are already in trash, they will be permanently deleted.

### core:delete-notebook

<div class="ui warning message">It's a private command for now</div>

### core:delete-tag

<div class="ui warning message">It's a private command for now</div>

### core:duplicate-note

Duplicates notes currently selected on the note list

### core:emphasize

* Selector: `.mde-cm-wrapper`

Emphersize currently selected text

### core:empty-trash

Empties trash

### core:filter-notes

Filters current note list items with given keywords

| Argument | Description |
| -------- | ----------- |
| `keyword` | The keywords to filter. |

### core:filter-by-tag

Adds a filter condition with specified tag

| Argument | Description |
| -------- | ----------- |
| `tagId` | The ID of the tag to filter by. |

### core:find

Moves focus to the search bar

### core:find-clear

Clears the search bar text

### core:find-global

Moves focus to the search bar and switch the [search scope to global](/manual/searching-notes#local--global-search-scope).

### core:focus-next

Moves focus to the next focussable UI component

### core:focus-note-list-bar

Moves focus to the note list bar

### core:focus-previous

Moves focus to the previous focussable UI component

### core:indent

* Selector: `.mde-cm-wrapper`

Indents the selected line(s)

### core:insert-code-block

* Selector: `.mde-cm-wrapper`

Inserts a code block

### core:insert-horizontal-rule

* Selector: `.mde-cm-wrapper`

Inserts a horizontal rule: `* * *`

### core:insert-link

* Selector: `.mde-cm-wrapper`

Inserts a link

### core:move-notebook

<div class="ui warning message">It's a private command for now</div>

### core:move-to-notebook

<div class="ui warning message">It's a private command for now</div>

### core:navigate-back

Moves backward through the note open history

### core:navigate-forward

Moves forward through the note open history

### core:new-note

Creates a new note and open it in the editor

### core:new-notebook

Shows up a dialog for creating a new notebook

### core:note-list-show-all-notes

Lists all notes on the note list bar

### core:open-first-note

Opens the first note of the note list bar in the editor

### core:open-next-note

Opens the next note of currently selected note on the note list bar.

### core:open-note

Opens a note with specified note ID

| Argument | Description |
| -------- | ----------- |
| `noteId` | The ID of the note to open. |
| `selectInNoteListBar` | Whether to select the correspond note in the note list bar. |
| `pushState` | Remember it in the navigation history. |
| `newWindow` | Whether to open the note in a separate window. |


### core:open-note-in-separate-window

Opens notes selected on the note list bar in separate windows

### core:open-prev-note

Opens the previous note of currently selected note on the note list bar.

### core:open-tag-settings

Opens up the settings window for the tag with specified ID.

| Argument | Description |
| -------- | ----------- |
| `tagId` | The ID of the tag to set. |

### core:paste

Pastes a text from clipboard

### core:redo

Redoes the last undone change.

### core:rename-notebook

<div class="ui warning message">It's a private command for now</div>

### core:save-image

Saves the target element's image to disk

### core:save-note

Saves the currently editing note to the local database

### core:select-all

Select all text

### core:search-notes

Search notes globally with given keywords

| Argument | Description |
| -------- | ----------- |
| `keyword` | The keywords to search. |

### core:share-note

Shows up a dialog for sharing note with specified ID

| Argument | Description |
| -------- | ----------- |
| `noteId` | The ID of the note to be shared. |

### core:show-note-revisions

Shows up a dialog for viewing note change history with specified ID

| Argument | Description |
| -------- | ----------- |
| `noteId` | The ID of the note to view its revision history. |

### core:sidebar-focus

Moves focus to the side bar

### core:sidebar-select-next-item

Select next item of the side bar menu

### core:sidebar-select-prev-item

Select previous item of the side bar menu

### core:strikethrough

* Selector: `.mde-cm-wrapper`

Toggles strikethrough to the selected text

### core:strong

* Selector: `.mde-cm-wrapper`

Toggles strong emphasis to the selected text

### core:toggle-blockquote

* Selector: `.mde-cm-wrapper`

Toggles blockquote to the selected lines

### core:toggle-bulleted-list

* Selector: `.mde-cm-wrapper`

Toggles bulleted list to the selected lines

### core:toggle-heading-1

* Selector: `.mde-cm-wrapper`

Toggles h1 heading to the selected lines

### core:toggle-heading-2

* Selector: `.mde-cm-wrapper`

Toggles h2 heading to the selected lines

### core:toggle-heading-3

* Selector: `.mde-cm-wrapper`

Toggles h3 heading to the selected lines

### core:toggle-heading-4

* Selector: `.mde-cm-wrapper`

Toggles h4 heading to the selected lines

### core:toggle-heading-bigger

* Selector: `.mde-cm-wrapper`

Decreases heading level of the selected lines

### core:toggle-heading-smaller

* Selector: `.mde-cm-wrapper`

Increases heading level of the selected lines

### core:toggle-numbered-list

* Selector: `.mde-cm-wrapper`

Toggles ordered list to the selected lines

### core:toggle-task-list

* Selector: `.mde-cm-wrapper`

Toggles task list to the selected lines

### core:undo

* Selector: `.mde-cm-wrapper`

Undoes the last change

### core:unindent

* Selector: `.mde-cm-wrapper`

Unindents the current lines

## Editor commands

### editor:clear-find

Clears the text in the editor search bar

### editor:delete-char-after

Deletes the char after the cursor

### editor:delete-char-before

Deletes the char before the cursor

### editor:delete-group-after

Deletes the text group after the cursor

### editor:delete-group-before

Deletes the text group before the cursor

### editor:delete-line

Deletes the line

### editor:delete-word-after

Deletes the word after the cursor

### editor:delete-word-before

Deletes the word before the cursor

### editor:delete-wrapped-line-left

Deletes the wrapped line left

### editor:delete-wrapped-line-right

Deletes the wrapped line right

### editor:find

Toggles the editor search bar

### editor:find-next

Locates the next item in the editor that matches criteria

### editor:find-prev

Locates the previous item in the editor that matches criteria

### editor:find-text

Finds given text in the editor

| Argument | Description |
| -------- | ----------- |
| `text` | String, the text to find. |

### editor:focus

If the editor mode is `'edit'` or `'side-by-side'`, it focuses to the MDE.
If the editor mode is `'preview'`, it focuses to the preview pane.

### editor:focus-mde

Moves focus to the MDE.

### editor:focus-preview

Moves focus to the preview pane.

### editor:go-char-left

* Selector: `.mde-cm-wrapper`

Moves the cursor to one character left

### editor:go-char-right

* Selector: `.mde-cm-wrapper`

Moves the cursor to one character right

### editor:go-doc-end

* Selector: `.mde-cm-wrapper`

Moves the cursor to the end of the document

### editor:go-doc-start

* Selector: `.mde-cm-wrapper`

Moves the cursor to the start of the document

### editor:go-group-left

* Selector: `.mde-cm-wrapper`

Moves the cursor to one group left

### editor:go-group-right

* Selector: `.mde-cm-wrapper`

Moves the cursor to one group right

### editor:go-line-down

* Selector: `.mde-cm-wrapper`

Moves the cursor to one line down

### editor:go-line-end

* Selector: `.mde-cm-wrapper`

Moves the cursor to the line end

### editor:go-line-left

* Selector: `.mde-cm-wrapper`

Moves the cursor to the line left

### editor:go-line-right

* Selector: `.mde-cm-wrapper`

Moves the cursor to the line right

### editor:go-line-start

* Selector: `.mde-cm-wrapper`

Moves the cursor to the line start

### editor:go-line-up

* Selector: `.mde-cm-wrapper`

Moves the cursor to one line up

### editor:go-page-down

* Selector: `.mde-cm-wrapper`

Moves the cursor to one page down

### editor:go-page-up

* Selector: `.mde-cm-wrapper`

Moves the cursor to one page up

### editor:go-word-left

* Selector: `.mde-cm-wrapper`

Moves the cursor to one word left

### editor:go-word-right

* Selector: `.mde-cm-wrapper`

Moves the cursor to one word right

### editor:indent

* Selector: `.mde-cm-wrapper`

Indents the currently selected line(s)

### editor:indent-less

* Selector: `.mde-cm-wrapper`

Unindents the currently selected line(s)

### editor:indent-more

* Selector: `.mde-cm-wrapper`

Indents one more the currently selected line(s)

### editor:insert-images

Inserts image files at the cursor to the editing note

| Argument | Description |
| -------- | ----------- |
| `pos` | Position to insert with the following keys: |
| &emsp;`ch` | Number, character position |
| &emsp;`line` | Number, line position |
| `files` | [FIleList](https://developer.mozilla.org/en-US/docs/Web/API/FileList), or an Array of [File](https://developer.mozilla.org/en-US/docs/Web/API/File) or [NativeImage](https://electronjs.org/docs/api/native-image) to insert. |

### editor:jump-to-line

* Selector: `.mde-cm-wrapper`

Toggles a dialog which allows you to jump to the line at the specified number

### editor:kill-line

* Selector: `.mde-cm-wrapper`

Deletes the line at the cursor

### editor:new-line

* Selector: `.mde-cm-wrapper`

Insert a new line below the cursor

### editor:open-line

* Selector: `.mde-cm-wrapper`

Insert a new line above the cursor

### editor:redo-selection

* Selector: `.mde-cm-wrapper`

Redoes the last selection.

### editor:replace

Initiates the replace sequence in the editor

### editor:replace-selection

* Selector: `.mde-cm-wrapper`

Replaces selected text with the given text

| Argument | Description |
| -------- | ----------- |
| `text` | String, the text to replace. |

### editor:save-editor-scroll

<div class="ui warning message">It's a private command</div>

### editor:save-preview-scroll

<div class="ui warning message">It's a private command</div>

### editor:scroll-editor-to-line

Scrolls the editor to the given line

| Argument | Description |
| -------- | ----------- |
| `line` | Number, the destination line number. |

### editor:scroll-preview-to-line

Scrolls the preview to the given line

| Argument | Description |
| -------- | ----------- |
| `line` | Number, the destination line number. |

### editor:select-all

* Selector: `.mde-cm-wrapper`

Selects all text in the editor

### editor:select-lines-downward

* Selector: `.mde-cm-wrapper`

Adds a cursor downward

### editor:select-lines-upward

* Selector: `.mde-cm-wrapper`

Adds a cursor upward

### editor:single-selection

* Selector: `.mde-cm-wrapper`

Removes all cursors except the primary one

### editor:sync-editor-scroll

Syncs the scroll position of the editor with the same position of the preview pane

### editor:sync-preview-scroll

Syncs the scroll position of the preview pane with the same position of the editor

### editor:title:focus

Moves focus to the title input bar of the editor

### editor:toggle-overwrite

* Selector: `.mde-cm-wrapper`

Toggles overwrite mode

### editor:toggle-task-list

* Selector: `.mde-cm-wrapper`

Toggles task list to the current selections

### editor:transpose-chars

* Selector: `.mde-cm-wrapper`

Transposes characters at the cursor

### editor:undo-selection

* Selector: `.mde-cm-wrapper`

Undoes the last selection

### editor:unindent

* Selector: `.mde-cm-wrapper`

Unindents the current lines

## Export commands

### export-as-html:export

Exports selected notes on the note list bar as HTML to disk

### export-as-markdown:all

Exports all notes as Markdown to disk

### export-as-markdown:single

Exports the editing note as Markdown to disk

### export-print:export-as-pdf

Exports the editing note as PDF to disk

### export-print:print

Prints the editing note

## Import commands

### import-html:import-from-file

Imports a note from a HTML file

## View commands

### view:sort-by-date-created

Sorts the note list by date created

### view:sort-by-date-updated

Sorts the note list by date updated

### view:sort-by-title

Sorts the note list by title

### view:sort-in-ascending

Sorts the note list in ascending

### view:sort-in-descending

Sorts the note list in descending

### view:toggle-distraction-free

Toggles distraction free mode.

### view:toggle-preview

Toggles the preview pane.

### view:toggle-side-by-side

Toggles the side-by-side mode.

### view:toggle-sidebar

Toggles the side bar.

## Window commands

### window:close

Closes the window

### window:decrease-font-size

Decreases the font size in the editor

### window:increase-font-size

Increases the font size in the editor

### window:install-shell-commands

Installs `ipm` command to your system

### window:new-inkdrop-window

Opens up a new window

### window:reload

Reloads the window

### window:toggle-dev-tools

Toggles the Developer Tools window

### window:toggle-full-screen

Toggles full screen mode

