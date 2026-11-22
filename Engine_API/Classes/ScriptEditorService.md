<!-- Source: https://create.roblox.com/docs/reference/engine/classes/ScriptEditorService -->

ScriptEditorService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ScriptEditorService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [ScriptEditorService](/docs/reference/engine/classes/ScriptEditorService)

English

Feedback

Engine Class

ScriptEditorService

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[DeregisterAutocompleteCallback](#DeregisterAutocompleteCallback) (name :  [string](/docs/luau/strings) ) : ()

 |
| --- | --- |
|

[DeregisterScriptAnalysisCallback](#DeregisterScriptAnalysisCallback) (name :  [string](/docs/luau/strings) ) : ()

 |
|

[FindScriptDocument](#FindScriptDocument) (script :  [LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer) ) :[ScriptDocument](/docs/reference/engine/classes/ScriptDocument)

 |
|

[GetEditorSource](#GetEditorSource) (script :  [LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer) ) :[string](/docs/luau/strings)

 |
|

[GetScriptDocuments](#GetScriptDocuments) () : {[ScriptDocument](/docs/reference/engine/classes/ScriptDocument) }

 |
|

[OpenScriptDocumentAsync](#OpenScriptDocumentAsync) (script :  [LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer) , options :  [Dictionary](/docs/luau/tables#dictionaries) ) :[Tuple](/docs/luau/tuples)

 |
|

[RegisterAutocompleteCallback](#RegisterAutocompleteCallback) (name :  [string](/docs/luau/strings) , priority :  [number](/docs/luau/numbers) , callbackFunction :  [function](/docs/luau/functions) ) : ()

 |
|

[RegisterScriptAnalysisCallback](#RegisterScriptAnalysisCallback) (name :  [string](/docs/luau/strings) , priority :  [number](/docs/luau/numbers) , callbackFunction :  [function](/docs/luau/functions) ) : ()

 |
|

[UpdateSourceAsync](#UpdateSourceAsync) (script :  [LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer) , callback :  [function](/docs/luau/functions) ) : ()

 |

Events

|

[TextDocumentDidChange](#TextDocumentDidChange) (document :  [ScriptDocument](/docs/reference/engine/classes/ScriptDocument) , changesArray :  Variant ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[TextDocumentDidClose](#TextDocumentDidClose) (oldDocument :  [ScriptDocument](/docs/reference/engine/classes/ScriptDocument) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[TextDocumentDidOpen](#TextDocumentDidOpen) (newDocument :  [ScriptDocument](/docs/reference/engine/classes/ScriptDocument) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Methods

DeregisterAutocompleteCallback

Plugin Security

ScriptEditorService:DeregisterAutocompleteCallback (name :[string](/docs/luau/strings) ) : ()

Parameters

|

name :[string](/docs/luau/strings)

 |

Returns

()

Code Samples

DeregisterAutocompleteCallback()

```

local ScriptEditorService = game:GetService("ScriptEditorService")

ScriptEditorService:DeregisterAutocompleteCallback("foo")

```

Provide feedback

---

DeregisterScriptAnalysisCallback

Plugin Security

ScriptEditorService:DeregisterScriptAnalysisCallback (name :[string](/docs/luau/strings) ) : ()

Parameters

|

name :[string](/docs/luau/strings)

 |

Returns

()

Code Samples

DeregisterScriptAnalysisCallback()

```

local ScriptEditorService = game:GetService("ScriptEditorService")

ScriptEditorService:DeregisterScriptAnalysisCallback("foo")

```

Provide feedback

---

FindScriptDocument

Plugin Security

ScriptEditorService:FindScriptDocument (script :[LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer) ) :[ScriptDocument](/docs/reference/engine/classes/ScriptDocument)

Parameters

|

script :[LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer)

 |

Returns

[ScriptDocument](/docs/reference/engine/classes/ScriptDocument)

Code Samples

ScriptDocument:CloseAsync

```

--!nocheck

-- Run the following code in the Command Bar

local ScriptEditorService = game:GetService("ScriptEditorService")

local documents = ScriptEditorService:GetScriptDocuments()

local scriptDocument

-- Find the first open script document

for _, document in documents do

	-- The Command Bar can't be closed, so don't select it

	if not document:IsCommandBar() then

		scriptDocument = document

		break

	end

end

if scriptDocument then

	local success, err = scriptDocument:CloseAsync()

	if success then

		print(`Closed {scriptDocument.Name}`)

	else

		warn(`Failed to close {scriptDocument.Name} because: {err}`)

	end

else

	print("No open scripts")

end

```

Connecting to ScriptDocument.ViewportChanged

```

--!nocheck

--[[

	To run:

		1. Ensure Output view is open

		2. Run the below code in the Command Bar

		3. Scroll up and down in the opened Script window

	Print statements from the ViewportChanged event will appear in the Output

]]

local Workspace = game:GetService("Workspace")

local ScriptEditorService = game:GetService("ScriptEditorService")

-- Create text that spans many lines

local dummyText = string.rep("-- Dummy Text\n", 60)

-- Create a script containing the dummy text and open it

local otherScript = Instance.new("Script")

otherScript.Source = dummyText

otherScript.Parent = Workspace

local success, err = ScriptEditorService:OpenScriptDocumentAsync(otherScript)

if not success then

	warn(`Failed to open script because: {err}`)

	return

end

-- Get a reference to the opened script

local scriptDocument = ScriptEditorService:FindScriptDocument(otherScript)

local function onViewportChanged(startLine: number, endLine: number)

	print(`Script Viewport Changed - startLine: {startLine}, endLine: {endLine}`)

end

-- Connect the ViewportChanged event to the function above that prints the start and end line of the updated viewport

scriptDocument.ViewportChanged:Connect(onViewportChanged)

```

Provide feedback

---

GetEditorSource

Plugin Security

ScriptEditorService:GetEditorSource (script :[LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer) ) :[string](/docs/luau/strings)

Parameters

|

script :[LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer)

 |

Returns

[string](/docs/luau/strings)

Provide feedback

---

GetScriptDocuments

Plugin Security

ScriptEditorService:GetScriptDocuments () : {[ScriptDocument](/docs/reference/engine/classes/ScriptDocument) }

Returns

{[ScriptDocument](/docs/reference/engine/classes/ScriptDocument) }

Code Samples

Print the name of every script

```

--!nocheck

-- Run the following code in the Command Bar

local ScriptEditorService = game:GetService("ScriptEditorService")

local scriptDocuments = ScriptEditorService:GetScriptDocuments()

for _, scriptDocument in scriptDocuments do

	-- Prints the name of each script

	if not scriptDocument:IsCommandBar() then

		print(scriptDocument.Name)

	end

end

```

Provide feedback

---

OpenScriptDocumentAsync

Yields

Plugin Security

ScriptEditorService:OpenScriptDocumentAsync (

script :[LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer) , options :[Dictionary](/docs/luau/tables#dictionaries)

) :[Tuple](/docs/luau/tuples)

Parameters

|

script :[LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer)

 |
|

options :[Dictionary](/docs/luau/tables#dictionaries)

Default Value: nil |

Returns

[Tuple](/docs/luau/tuples)

Code Samples

OpenScriptDocumentAsync()

```

--!nocheck

-- Run the following code in the Command Bar

local ScriptEditorService = game:GetService("ScriptEditorService")

local Workspace = game:GetService("Workspace")

local newScript = Instance.new("Script")

newScript.Parent = Workspace

local success, err = ScriptEditorService:OpenScriptDocumentAsync(newScript)

if success then

	print("Opened script document")

else

	print(`Failed to open script document: {err}`)

end

```

OpenScriptDocumentAsync() with InitialReadOnlyReasons

```

local ScriptEditorService = game:GetService("ScriptEditorService")

local Workspace = game:GetService("Workspace")

local templateScript = Instance.new("Script")

templateScript.Source = "-- Template provided by MyPlugin"

templateScript.Parent = Workspace

local success, err = ScriptEditorService:OpenScriptDocumentAsync(templateScript, {

	InitialReadOnlyReasons = { "MyPluginTemplateScript" },

})

if success then

	local scriptDocument = ScriptEditorService:FindScriptDocument(templateScript)

	print(`Opened read-only template: {scriptDocument:IsReadOnly()}`)

else

	warn(`Failed to open script document: {err}`)

end

```

Provide feedback

---

RegisterAutocompleteCallback

Plugin Security

ScriptEditorService:RegisterAutocompleteCallback (

name :[string](/docs/luau/strings) , priority :[number](/docs/luau/numbers) , callbackFunction :[function](/docs/luau/functions)

) : ()

Parameters

|

name :[string](/docs/luau/strings)

 |
|

priority :[number](/docs/luau/numbers)

 |
|

callbackFunction :[function](/docs/luau/functions)

 |

Returns

()

Code Samples

RegisterAutocompleteCallback() and DeregisterAutocompleteCallback()

```

--!nocheck

-- Run the following code in the Command Bar

local ScriptEditorService = game:GetService("ScriptEditorService")

type Request = {

	position: {

		line: number,

		character: number,

	},

	textDocument: {

		document: ScriptDocument?,

		script: LuaSourceContainer?,

	},

}

type Response = {

	items: {

		{

			label: string,

			kind: Enum.CompletionItemKind?,

			tags: { Enum.CompletionItemTag }?,

			detail: string?,

			documentation: {

				value: string,

			}?,

			overloads: number?,

			learnMoreLink: string?,

			codeSample: string?,

			preselect: boolean?,

			textEdit: {

				newText: string,

				replace: {

					start: { line: number, character: number },

					["end"]: { line: number, character: number },

				},

			}?,

		}

	},

}

local autocompleteCallback = function(request: Request, response: Response): Response

	local item = {

		label = "foo",

		preselect = true,

	}

	table.insert(response.items, item)

	return response

end

ScriptEditorService:RegisterAutocompleteCallback("foo", 1, autocompleteCallback)

-- To deregister the callback, run the following code in the Command Bar

ScriptEditorService:DeregisterAutocompleteCallback("foo")

```

Provide feedback

---

RegisterScriptAnalysisCallback

Plugin Security

ScriptEditorService:RegisterScriptAnalysisCallback (

name :[string](/docs/luau/strings) , priority :[number](/docs/luau/numbers) , callbackFunction :[function](/docs/luau/functions)

) : ()

Parameters

|

name :[string](/docs/luau/strings)

 |
|

priority :[number](/docs/luau/numbers)

 |
|

callbackFunction :[function](/docs/luau/functions)

 |

Returns

()

Code Samples

RegisterScriptAnalysisCallback()

```

type Request = {

	["script"]: LuaSourceContainer,

}

type Response = {

	diagnostics: {

		{

			range: {

				start: {

					line: number,

					character: number,

				},

				["end"]: {

					line: number,

					character: number,

				},

			},

			code: string?,

			message: string,

			severity: Enum.Severity?,

			codeDescription: { href: string }?,

		}

	},

}

local ScriptEditorService = game:GetService("ScriptEditorService")

ScriptEditorService:RegisterScriptAnalysisCallback("foo", 1, function(Req: Request): Response

	local response = {

		diagnostics = {},

	}

	local lineNo = 1

	-- Iterate line by line

	for text, newline in Req.script.Source:gmatch("([^\r\n]*)([\r\n]*)") do

		local startIndex, endIndex = string.find(text, "Foo")

		if startIndex and endIndex then

			table.insert(response.diagnostics, {

				range = {

					["start"] = {

						line = lineNo,

						character = startIndex,

					},

					["end"] = {

						line = lineNo,

						character = endIndex,

					},

				},

				code = "FooFinder",

				message = "Foo found here!",

				severity = Enum.Severity.Warning,

			})

		end

		lineNo = lineNo + #newline:gsub("\n+", "\0%0\0"):gsub(".%z.", "."):gsub("%z", "")

	end

	return response

end)

```

Provide feedback

---

UpdateSourceAsync

Yields

Plugin Security

ScriptEditorService:UpdateSourceAsync (

script :[LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer) , callback :[function](/docs/luau/functions)

) : ()

Parameters

|

script :[LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer)

 |
|

callback :[function](/docs/luau/functions)

 |

Returns

()

Code Samples

Update Source Async

```

local ScriptEditorService = game:GetService("ScriptEditorService")

ScriptEditorService:UpdateSourceAsync(workspace.Script, function(oldContent)

	return oldContent .. " World!"

end)

```

Provide feedback

---

Events

TextDocumentDidChange

Plugin Security

ScriptEditorService.TextDocumentDidChange (

document :[ScriptDocument](/docs/reference/engine/classes/ScriptDocument) , changesArray : Variant

) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

document :[ScriptDocument](/docs/reference/engine/classes/ScriptDocument)

 |
|

changesArray : Variant

 |

Code Samples

ScriptEditorService.TextDocumentDidChange

```

--!nocheck

-- Run the following code in the Command Bar

local ScriptEditorService = game:GetService("ScriptEditorService")

ScriptEditorService.TextDocumentDidChange:Connect(function(scriptDocument, changes)

	print("Changed", scriptDocument, changes)

end)

```

Provide feedback

---

TextDocumentDidClose

Plugin Security

ScriptEditorService.TextDocumentDidClose (oldDocument :[ScriptDocument](/docs/reference/engine/classes/ScriptDocument) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

oldDocument :[ScriptDocument](/docs/reference/engine/classes/ScriptDocument)

 |

Code Samples

ScriptEditorService.TextDocumentDidClose

```

--!nocheck

-- Run the following code in the Command Bar

local ScriptEditorService = game:GetService("ScriptEditorService")

ScriptEditorService.TextDocumentDidClose:Connect(function(scriptDocument)

	print("Closed", scriptDocument)

end)

```

Provide feedback

---

TextDocumentDidOpen

Plugin Security

ScriptEditorService.TextDocumentDidOpen (newDocument :[ScriptDocument](/docs/reference/engine/classes/ScriptDocument) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

newDocument :[ScriptDocument](/docs/reference/engine/classes/ScriptDocument)

 |

Code Samples

ScriptEditorService.TextDocumentDidOpen

```

--!nocheck

-- Run the following code in the Command Bar

local ScriptEditorService = game:GetService("ScriptEditorService")

ScriptEditorService.TextDocumentDidOpen:Connect(function(scriptDocument)

	print("Opened", scriptDocument)

end)

```

Provide feedback

---

Jump to

▼

ScriptEditorService

[Summary](#summary)

[Methods](#summary-methods)

[Events](#summary-events)

[Methods](#methods)

[DeregisterAutocompleteCallback()](#DeregisterAutocompleteCallback)

[DeregisterScriptAnalysisCallback()](#DeregisterScriptAnalysisCallback)

[FindScriptDocument()](#FindScriptDocument)

[GetEditorSource()](#GetEditorSource)

[GetScriptDocuments()](#GetScriptDocuments)

[OpenScriptDocumentAsync()](#OpenScriptDocumentAsync)

[RegisterAutocompleteCallback()](#RegisterAutocompleteCallback)

[RegisterScriptAnalysisCallback()](#RegisterScriptAnalysisCallback)

[UpdateSourceAsync()](#UpdateSourceAsync)

[Events](#events)

[TextDocumentDidChange](#TextDocumentDidChange)

[TextDocumentDidClose](#TextDocumentDidClose)

[TextDocumentDidOpen](#TextDocumentDidOpen)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
