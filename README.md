# Awesome-macos-toolbar-app

# Open in Visual Studio Code
A Finder toolbar icon to open current selected file/folder with VS Code.

![](https://github.com/hamxiaoz/open-folder-with-vs-code/blob/master/demo.gif)

## How to use?
- Download [the zip file](https://github.com/hamxiaoz/open-folder-with-vs-code/raw/master/Open%20in%20VS%20Code.app.zip)
- Unzip to Applications folder (or any folder that you won't mistakenly delete the app)
- Right-click to open to pass the Mac security check
- Hold `Option+CMD` and drag the application to toolbar
- **Mojave users**: to disable the system warning "Allowing control will provide access to documents and data..." when using the app, [add the application in preferences -> security and privacy -> privacy -> accessibility](https://apple.stackexchange.com/a/335850)
- Enjoy

## How to create the app manually?
Open AppleScript Editor, copy the following source and export as Application.

```
(*
 Open in VS Code
 To use:
  * Drag Open In VS Code to the toolbar of any finder
  window to add it to the toolbar
*)

on run
	tell application "Finder"
		if selection is {} then
			set finderSelection to folder of the front window as string
		else
			set finderSelection to selection as alias list
		end if
	end tell
	
	subl(finderSelection)
end run

-- script was drag-and-dropped onto
on open (theList)
	subl(theList)
end open

-- open in Sublime Text
on subl(listOfAliases)
	tell application "Visual Studio Code"
		activate
		open listOfAliases
	end tell
end subl
```

# Open in Sublime Text 3
A Finder toolbar icon to open current selected file/folder with Sublime.

## How to create the app manually?
Open AppleScript Editor, copy the following source and export as Application.

```
(*
 Open in Sublime Text
 To use:
  * Drag Open In Sublime Text to the toolbar of any finder
  window to add it to the toolbar
*)

on run
	tell application "Finder"
		if selection is {} then
			set finderSelection to folder of the front window as string
		else
			set finderSelection to selection as alias list
		end if
	end tell
	
	subl(finderSelection)
end run

-- script was drag-and-dropped onto
on open (theList)
	subl(theList)
end open

-- open in Sublime Text
on subl(listOfAliases)
	tell application "Sublime Text"
		activate
		open listOfAliases
	end tell
end subl
```

## Open Terminal here 🚀

| Features | OpenInTerminal |
| --- | --- |
| Open current directory in Terminal (or Editor) | ![](./Resources/screenshots/main-open-in-terminal.gif) |
| Open selected folder or file in Terminal (or Editor) | ![](./Resources/screenshots/main-open-in-editor.gif) |
| Copy path of the selected file or Finder window to Clipboard | ![](./Resources/screenshots/main-copy-path-to-clipboard.gif) |
