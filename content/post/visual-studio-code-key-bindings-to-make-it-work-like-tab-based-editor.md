+++
date = "2015-11-08"
title = "Visual Studio Code Key Bindings To Make It Work Like Tab Based Editor"
slug = "visual-studio-code-key-bindings-to-make-it-work-like-tab-based-editor"
+++

Microsoft recently released a new open source text editor called <a href="https://code.visualstudio.com" target="_blank">Visual Studio Code</a>. It is based on Github's Electron platform and is a cross platform application that runs on Windows, Linux and Mac OS X which is surprising considering it came from Microsoft. Surprisingly, it is a great editor when it comes to working with JavaScript and Node.js and basically anything front end (React, Angular...).

One major gripe I had with it that was stopping me from making it my default editor for web application projects was that it used a concept of "Working Files" instead of tabs like most editors I have come across. It works fine once you get used to it, but since I was not using it as my primary editor for everything, it was hard going back and forth between tab based editor and VS Code. My main issue was that I could not switch between working files easily with the almost universal keyboard command to switch tabs "CMD + SHIFT + [" and "CMD + SHIFT + ]". Also pressing "CMD + W" would close the file from the editor but not remove it from the "Working Files Section".

<img src="/blog/img/visual-studio-code.png"/>

After spending a few minutes looking at the <a href="https://code.visualstudio.com/Docs/customization/keybindings" target="_blank">documentation for key bindings</a>, I changed a couple of things to make it work like any other tab based editor. Open up your key preferences json file (by going to Preferences -&gt; Keyboard Shortcuts) and paste or add the following:

**Mac**

    [
    	{
    		"key": "cmd+shift+[",
    		"command": "workbench.files.action.openPreviousWorkingFile"
    	},
    	{
    		"key": "cmd+shift+]",
    		"command": "workbench.files.action.openNextWorkingFile"
    	},
    	{
    		"key": "cmd+w",
    		"command": "workbench.files.action.closeFile"
    	}
    ]

**Windows / Linux:**

    [
    	{
    		"key": "win+shift+[",
    		"command": "workbench.files.action.openPreviousWorkingFile"
    	},
    	{
    		"key": "win+shift+]",
    		"command": "workbench.files.action.openNextWorkingFile"
    	},
    	{
    		"key": "win+w",
    		"command": "workbench.files.action.closeFile"
    	}
    ]
Let me know if you have a better way of doing this or any other suggestions!
