# Sublime Text standards guide

Version 1.1.0
Last updated: Tuesday 19 July 2016

<!-- MarkdownTOC -->

- [1. Version](#1-version)
- [2. Package control](#2-package-control)
	- [2.1 Batch install packages](#21-batch-install-packages)
	- [2.2 Package descriptions](#22-package-descriptions)
- [3. User preferences](#3-user-preferences)
	- [MarkdownTOC user settings](#markdowntoc-user-settings)

<!-- /MarkdownTOC -->




---

## 1. Version

We recommend using **Sublime Text 3 beta**.

All the plugins work with Sublime Text 2 so it's up to user preference.




---

## 2. Package control

Plugins for Sublime Text are called 'packages'.

Perhaps the most useful plugin we use is [Package Control](https://packagecontrol.io/). This makes it very simple to find, install and keep packages (plugins) up to date.

Install via the console (`Ctrl + '` or `View > Show Console`). Copy and paste the appropriate [install script](https://packagecontrol.io/installation) then press Enter. You may need to restart Sublime Text, but follow onscreen instructions.

Packages can then be searched via `Preferences > Browse Packages...`.


### 2.1 Batch install packages

To speed up getting started, when you first install Sublime Text you can batch import packages (plugins).

First make sure that Package Control is installed, then go to `Preferences > Package Settings > Package Control > Settings - User`. This will open a JSON file called `Package Control.sublime-settings`.

These are stored in the following locations:

**Windows**
`C:\Users\{USER_NAME}\AppData\Roaming\Sublime Text 3\Packages\User`

**Mac OS X**
`/Users/{USER_NAME}/Library/Application Support/Sublime Text 3/Packages/User`

Simply copy and paste the following code into your `Package Control.sublime-settings` file, remove any that look redundant (e.g. if you don't do any WordPress development then remove the WordPress-related packages), save the file, then restart Sublime Text.

	{
		"bootstrapped": true,
		"in_process_packages":
		[],
		"installed_packages":
		[
			"Alignment",
			"Autoprefixer",
			"Bootstrap 3 Snippets",
			"BracketHighlighter",
			"Color Highlighter",
			"CSScomb",
			"DevDocs",
			"Emmet",
			"GitGutter",
			"jQuery",
			"JSHint Gutter",
			"Markdown Preview",
			"MarkdownEditing",
			"MarkdownTOC",
			"Package Control",
			"Placeholders",
			"Sass",
			"SideBarEnhancements",
			"SyncedSideBar",
			"Theme - Minimal",
			"TodoReview",
			"Tomorrow Color Schemes",
			"View In Browser",
			"WordPress",
			"WordPress Developer Resources",
			"WordPress Generate Salts",
		]
	}


### 2.2 Package descriptions

* [Alignment](https://packagecontrol.io/packages/Alignment) - Key-binding to align multi-line and multiple selections.
* [Autoprefixer](https://packagecontrol.io/packages/Autoprefixer) - Auto-add vendor prefixes.
* [Bootstrap 3 Snippets](https://packagecontrol.io/packages/Bootstrap%203%20Snippets) - Autocomplete Bootstrap 3 code.
* [BracketHighlighter](https://packagecontrol.io/packages/BracketHighlighter) - Highlight content between `[ ]`, `( )`, `{ }`, `" "`, `' '`.
* [CSScomb](https://packagecontrol.io/packages/CSScomb) - Code style formatter for CSS.
* [DevDocs](https://packagecontrol.io/packages/DevDocs) - Easily search [DevDocs](http://devdocs.io/) (repository of documentation for multiple APIs).
* [Emmet](https://packagecontrol.io/packages/Emmet) - Autocomplete or programmatically generating code.
* [GitGutter](https://packagecontrol.io/packages/GitGutter) - Show icon in the gutter area indicating differences compared with the previous Git commit.
* [jQuery](https://packagecontrol.io/packages/jQuery) - Syntax highlighting and snippets for almost all jQuery methods.
* [JSHint Gutter](https://packagecontrol.io/packages/JSHint%20Gutter) - Check JavaScript code for errors, coding conventions, etc.
* [Markdown Preview](https://packagecontrol.io/packages/Markdown%20Preview) - Preview and build your markdown files quickly in your web browser.
* [MarkdownEditing](https://packagecontrol.io/packages/MarkdownEditing) - Colour scheme with syntax highlighting for markdown files.
* [MarkdownTOC](https://packagecontrol.io/packages/MarkdownTOC) - Search headings in markdown documents and insert table of contents (TOC).
* [Placeholders](https://packagecontrol.io/packages/Placeholders) - Basic HTML placeholder content, e.g. lorem ipsum text, forms, images etc.
* [Sass](https://packagecontrol.io/packages/Sass) - Syntax highlighting and tab/code completion for Sass and SCSS files.
* [SideBarEnhancements](https://packagecontrol.io/packages/SideBarEnhancements) - Enhancements to sidebar for files and folders.
* [SyncedSideBar](https://packagecontrol.io/packages/SyncedSideBar) - Sync project sidebar (folder view) with currently active file.
* [TodoReview](https://packagecontrol.io/packages/TodoReview) - Search your code for `TODO:`, `FIXME:`, `NOTE:` comments within your project.
* [Tomorrow Color Schemes](https://packagecontrol.io/packages/Tomorrow%20Color%20Schemes) - Tomorrow (dark) colour scheme.
* [View In Browser](https://packagecontrol.io/packages/View%20In%20Browser) - Open the contents of your current view/tab in a web browser.
* [WordPress](https://packagecontrol.io/packages/WordPress) - Collection of WordPress snippets and autocompletions.
* [WordPress Developer Resources](https://packagecontrol.io/packages/WordPress%20Developer%20Resources) - Search Wordpress Developer Resources (developer.wordpress.org) from within your code.
* [WordPress Generate Salts](https://packagecontrol.io/packages/WordPress%20Generate%20Salts) - Generating new WordPress salt keys (for installing WordPress).




---

## 3. User preferences

The following user preferences settings, found at `Preferences > Settings — User`, offers a very usable coding environment:

```
{
	"always_show_minimap_viewport": true,
	"bold_folder_labels": true,
	"caret_extra_bottom": 1,
	"caret_extra_top": 1,
	"caret_extra_width": 1,
	"caret_style": "phase",
	"default_encoding": "UTF-8",
	"default_line_ending": "LF",
	"dictionary": "Packages/Language - English/en_GB.dic",
	"draw_white_space": "selection",
	"fade_fold_buttons": false,
	"font_size": 20,
	"highlight_line": true,
	"highlight_modified_tabs": true,
	"hot_exit": true,
	"ignored_packages":
	[
		"Vintage"
	],
	"indent_guide_options":
	[
		"draw_normal",
		"draw_active"
	],
	"line_padding_bottom": 1,
	"line_padding_top": 1,
	"remember_open_files": true,
	"rulers":
	[
		80
	],
	"save_on_focus_lost": true,
	"show_encoding": true,
	"show_line_endings": true,
	"tab_size": 4,
	"translate_tabs_to_spaces": true,
	"trim_trailing_white_space_on_save": true,
	"wordwrap": true
}
```


### MarkdownTOC user settings

```
{
  "default_autolink": true,
  "default_bracket": "round",
  "default_depth": 4,
  "id_replacements": {
    "-": " ",
    "" : ["!","#","$","&","'","(",")","*","+",",","/",":",";","=","?","@","[","]","`","\"", ".","<",">","{","}","™","®","©"]
  },
  "default_autoanchor": false,
  "default_style": "unordered",
  "default_indent": "\t"
}
```