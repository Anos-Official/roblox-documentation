<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/CaptureService -->

CaptureService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/CaptureService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [CaptureService](/docs/en-us/reference/engine/classes/CaptureService)

English

Feedback

Engine Class

CaptureService

Not Creatable

Service

---

## Summary

Methods

|

[CaptureScreenshot](#CaptureScreenshot) (onCaptureReady :  [function](/docs/en-us/luau/functions) ) : ()

 |
| --- | --- |
|

[CheckUploadCaptureStatusAsync](#CheckUploadCaptureStatusAsync) (token :  [string](/docs/en-us/luau/strings) ) :[Tuple](/docs/en-us/luau/tuples)

 |
|

[PromptCaptureGalleryPermissionAsync](#PromptCaptureGalleryPermissionAsync) (captureGalleryPermission :  [Enum.CaptureGalleryPermission](/docs/en-us/reference/engine/enums/CaptureGalleryPermission) ) :[boolean](/docs/en-us/luau/booleans)

 |
|

[PromptSaveCapturesToGallery](#PromptSaveCapturesToGallery) (captures :  [{any}](/docs/en-us/luau/tables#arrays) , resultCallback :  [function](/docs/en-us/luau/functions) ) : ()

 |
|

[PromptShareCapture](#PromptShareCapture) (captureContent :  [Content](/docs/en-us/reference/engine/datatypes/Content) , launchData :  [string](/docs/en-us/luau/strings) , onAcceptedCallback :  [function](/docs/en-us/luau/functions) , onDeniedCallback :  [function](/docs/en-us/luau/functions) ) : ()

 |
|

[ReadCapturesFromGalleryAsync](#ReadCapturesFromGalleryAsync) (captureTypeFilters :  [{any}](/docs/en-us/luau/tables#arrays) , readFromAllEligibleExperiences :  [boolean](/docs/en-us/luau/booleans) ) :[Tuple](/docs/en-us/luau/tuples)

 |
|

[StartUploadCaptureAsync](#StartUploadCaptureAsync) (capture :  [Capture](/docs/en-us/reference/engine/classes/Capture) ) :[Tuple](/docs/en-us/luau/tuples)

 |
|

[StartVideoCaptureAsync](#StartVideoCaptureAsync) (onCaptureReady :  [function](/docs/en-us/luau/functions) , captureParams :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[Enum.VideoCaptureStartedResult](/docs/en-us/reference/engine/enums/VideoCaptureStartedResult)

 |
|

[StopVideoCapture](#StopVideoCapture) () : ()

 |
|

[TakeScreenshotCaptureAsync](#TakeScreenshotCaptureAsync) (onCaptureReady :  [function](/docs/en-us/luau/functions) , captureParams :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |
|

[UploadCaptureAsync](#UploadCaptureAsync) (capture :  [Capture](/docs/en-us/reference/engine/classes/Capture) ) :[Tuple](/docs/en-us/luau/tuples)

 |

Events

|

[CaptureBegan](#CaptureBegan) (captureType :  [Enum.CaptureType](/docs/en-us/reference/engine/enums/CaptureType) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[CaptureEnded](#CaptureEnded) (captureType :  [Enum.CaptureType](/docs/en-us/reference/engine/enums/CaptureType) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[CaptureSaved](#CaptureSaved) (captureInfo :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Deprecated

 |
|

[UserCaptureSaved](#UserCaptureSaved) (captureContentId :  ContentId ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

CaptureScreenshot

Capabilities: Capture

CaptureService:CaptureScreenshot (onCaptureReady :[function](/docs/en-us/luau/functions) ) : ()

Parameters

|

onCaptureReady :[function](/docs/en-us/luau/functions)

 |

Returns

()

Code Samples

Capture Screenshot

```

local CaptureService = game:GetService("CaptureService")

-- Reference to an ImageLabel parent of the script containing this code

local imageLabel = script.Parent

local function onCaptureReady(contentId)

	imageLabel.Image = contentId

end

CaptureService:CaptureScreenshot(onCaptureReady)

```

Provide feedback

---

CheckUploadCaptureStatusAsync

Yields

Capabilities: Capture

CaptureService:CheckUploadCaptureStatusAsync (token :[string](/docs/en-us/luau/strings) ) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

token :[string](/docs/en-us/luau/strings)

 |

Returns

[Tuple](/docs/en-us/luau/tuples)

Provide feedback

---

PromptCaptureGalleryPermissionAsync

Yields

Capabilities: Capture

CaptureService:PromptCaptureGalleryPermissionAsync (captureGalleryPermission :[Enum.CaptureGalleryPermission](/docs/en-us/reference/engine/enums/CaptureGalleryPermission) ) :[boolean](/docs/en-us/luau/booleans)

Parameters

|

captureGalleryPermission :[Enum.CaptureGalleryPermission](/docs/en-us/reference/engine/enums/CaptureGalleryPermission)

 |

Returns

[boolean](/docs/en-us/luau/booleans)

Code Samples

Prompt capture gallery permission

```

local CaptureService = game:GetService("CaptureService")

local function isGalleryAccessGranted()

	local accepted = CaptureService:PromptCaptureGalleryPermissionAsync(Enum.CaptureGalleryPermission.ReadAndUpload)

	return accepted

end

```

Provide feedback

---

PromptSaveCapturesToGallery

Capabilities: Capture

CaptureService:PromptSaveCapturesToGallery (

captures :[{any}](/docs/en-us/luau/tables#arrays) , resultCallback :[function](/docs/en-us/luau/functions)

) : ()

Parameters

|

captures :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

resultCallback :[function](/docs/en-us/luau/functions)

 |

Returns

()

Provide feedback

---

PromptShareCapture

Capabilities: Capture

CaptureService:PromptShareCapture (

captureContent :[Content](/docs/en-us/reference/engine/datatypes/Content) , launchData :[string](/docs/en-us/luau/strings) , onAcceptedCallback :[function](/docs/en-us/luau/functions) , onDeniedCallback :[function](/docs/en-us/luau/functions)

) : ()

Parameters

|

captureContent :[Content](/docs/en-us/reference/engine/datatypes/Content)

 |
|

launchData :[string](/docs/en-us/luau/strings)

 |
|

onAcceptedCallback :[function](/docs/en-us/luau/functions)

 |
|

onDeniedCallback :[function](/docs/en-us/luau/functions)

 |

Returns

()

Code Samples

Prompt Share Capture

```

local CaptureService = game:GetService("CaptureService")

local function onShareAccepted()

	print("Capture share was accepted!")

end

local function onShareDenied()

	print("Capture share was denied!")

end

local onCaptureReady = function(result, videoCapture)

	if videoCapture then

		local captureContent = Content.fromObject(videoCapture)

		CaptureService:PromptShareCapture(captureContent, "launchData" , onShareAccepted, onShareDenied)

	end

end

CaptureService:StartVideoCaptureAsync(onCaptureReady, {})

```

Provide feedback

---

ReadCapturesFromGalleryAsync

Yields

Capabilities: Capture

CaptureService:ReadCapturesFromGalleryAsync (

captureTypeFilters :[{any}](/docs/en-us/luau/tables#arrays) , readFromAllEligibleExperiences :[boolean](/docs/en-us/luau/booleans)

) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

captureTypeFilters :[{any}](/docs/en-us/luau/tables#arrays)

Default Value: {} |
|

readFromAllEligibleExperiences :[boolean](/docs/en-us/luau/booleans)

Default Value: false |

Returns

[Tuple](/docs/en-us/luau/tuples)

Code Samples

Read captures from gallery and iterate over pages

```

local CaptureService = game:GetService("CaptureService")

local function readCapturesFromGallery()

	local allCaptures = {}

	local capturesPages

	local success, result = pcall(function()

		local readResult, pages = CaptureService:ReadCapturesFromGalleryAsync({}, false)

		if readResult == Enum.ReadCapturesFromGalleryResult.Success then

			capturesPages = pages

		end

		return readResult

	end)

	if not success or result ~= Enum.ReadCapturesFromGalleryResult.Success then

		-- Likely a permissions error, see CaptureService:PromptCaptureGalleryPermissionAsync()

		warn("Failed to fetch initial captures: " .. result.Name)

		return

	end

	-- Iterate through current page

	local currentPage = capturesPages:GetCurrentPage()

	for _, capture in currentPage do

		table.insert(allCaptures, capture)

	end

	-- Advance to next page until finished

	while not capturesPages.IsFinished do

		local advanceToNextPageSuccess, _ = pcall(function()

			capturesPages:AdvanceToNextPageAsync()

		end)

		if not advanceToNextPageSuccess then

			return

		end

		currentPage = capturesPages:GetCurrentPage()

		for _, capture in currentPage do

			table.insert(allCaptures, capture)

		end

	end

	return allCaptures

end

```

Provide feedback

---

StartUploadCaptureAsync

Yields

Capabilities: Capture

CaptureService:StartUploadCaptureAsync (capture :[Capture](/docs/en-us/reference/engine/classes/Capture) ) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

capture :[Capture](/docs/en-us/reference/engine/classes/Capture)

 |

Returns

[Tuple](/docs/en-us/luau/tuples)

Provide feedback

---

StartVideoCaptureAsync

Yields

Capabilities: Capture

CaptureService:StartVideoCaptureAsync (

onCaptureReady :[function](/docs/en-us/luau/functions) , captureParams :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) :[Enum.VideoCaptureStartedResult](/docs/en-us/reference/engine/enums/VideoCaptureStartedResult)

Parameters

|

onCaptureReady :[function](/docs/en-us/luau/functions)

 |
|

captureParams :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

[Enum.VideoCaptureStartedResult](/docs/en-us/reference/engine/enums/VideoCaptureStartedResult)

Code Samples

Start Video Capture Async

```

local CaptureService = game:GetService("CaptureService")

local tool = Instance.new("Tool")

tool.Parent = workspace

local onCaptureReady = function(result, videoCapture)

	if result ~= Enum.VideoCaptureResult.Success and result ~= Enum.VideoCaptureResult.TimeLimitReached or not videoCapture then

		print("Video recording failed to complete for reason:", result)

	else

		-- Prompt the user to save the video capture to their gallery

		CaptureService:PromptSaveCapturesToGallery({ videoCapture }, function()

			print("Capture saved")

		end)

	end

end

tool.Activated:Connect(function()

	local videoRecordingAllowedResult: Enum.VideoCaptureStartedResult = CaptureService:StartVideoCaptureAsync(onCaptureReady, {})

	if videoRecordingAllowedResult ~= Enum.VideoCaptureStartedResult.Success then

		print("Video recording failed to start for reason:", videoRecordingAllowedResult)

	end

end)

```

Provide feedback

---

StopVideoCapture

Capabilities: Capture

CaptureService:StopVideoCapture () : ()

Returns

()

Provide feedback

---

TakeScreenshotCaptureAsync

Capabilities: Capture

CaptureService:TakeScreenshotCaptureAsync (

onCaptureReady :[function](/docs/en-us/luau/functions) , captureParams :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) : ()

Parameters

|

onCaptureReady :[function](/docs/en-us/luau/functions)

 |
|

captureParams :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

()

Code Samples

Take Screenshot Capture Async

```

local CaptureService = game:GetService("CaptureService")

local parent = Instance.new("Tool")

parent.Parent = workspace

local onCaptureReady = function(result, screenshotCapture)

	if result ~= Enum.ScreenshotCaptureResult.Success or not screenshotCapture then

		print("Screenshot failed to complete for reason:", result)

	else

		-- Prompt the user to save the screenshot capture to their gallery

		CaptureService:PromptSaveCapturesToGallery({ screenshotCapture }, function(results)

			for capture, result in pairs(results) do

				if result then

					print("Capture saved")

				end

			end

		end)

	end

end

parent.Activated:Connect(function()

	CaptureService:TakeScreenshotCaptureAsync(onCaptureReady, { UICaptureMode = Enum.UICaptureMode.All })

end)

```

Provide feedback

---

UploadCaptureAsync

Yields

Capabilities: Capture

CaptureService:UploadCaptureAsync (capture :[Capture](/docs/en-us/reference/engine/classes/Capture) ) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

capture :[Capture](/docs/en-us/reference/engine/classes/Capture)

 |

Returns

[Tuple](/docs/en-us/luau/tuples)

Code Samples

Upload capture to asset system

```

local CaptureService = game:GetService("CaptureService")

local function uploadCapture(capture: Capture)

	local success, result = pcall(function()

		local uploadCaptureResult, assetId = CaptureService:UploadCaptureAsync(capture)

		if uploadCaptureResult ~= Enum.UploadCaptureResult.Success then

			-- Handle failure

			return nil

		end

		return assetId

	end)

	if not success then

		-- Handle error

		return nil

	end

	return result

end

```

Provide feedback

---

Events

CaptureBegan

Capabilities: Capture

CaptureService.CaptureBegan (captureType :[Enum.CaptureType](/docs/en-us/reference/engine/enums/CaptureType) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

captureType :[Enum.CaptureType](/docs/en-us/reference/engine/enums/CaptureType)

 |

Provide feedback

---

CaptureEnded

Capabilities: Capture

CaptureService.CaptureEnded (captureType :[Enum.CaptureType](/docs/en-us/reference/engine/enums/CaptureType) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

captureType :[Enum.CaptureType](/docs/en-us/reference/engine/enums/CaptureType)

 |

Provide feedback

---

CaptureSaved

Deprecated

Show details

---

UserCaptureSaved

Capabilities: Capture

CaptureService.UserCaptureSaved (captureContentId : ContentId ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

captureContentId : ContentId

 |

Provide feedback

---

Jump to

▼

CaptureService

[Summary](#summary)

[Methods](#summary-methods)

[Events](#summary-events)

[Methods](#methods)

[CaptureScreenshot()](#CaptureScreenshot)

[CheckUploadCaptureStatusAsync()](#CheckUploadCaptureStatusAsync)

[PromptCaptureGalleryPermissionAsync()](#PromptCaptureGalleryPermissionAsync)

[PromptSaveCapturesToGallery()](#PromptSaveCapturesToGallery)

[PromptShareCapture()](#PromptShareCapture)

[ReadCapturesFromGalleryAsync()](#ReadCapturesFromGalleryAsync)

[StartUploadCaptureAsync()](#StartUploadCaptureAsync)

[StartVideoCaptureAsync()](#StartVideoCaptureAsync)

[StopVideoCapture()](#StopVideoCapture)

[TakeScreenshotCaptureAsync()](#TakeScreenshotCaptureAsync)

[UploadCaptureAsync()](#UploadCaptureAsync)

[Events](#events)

[CaptureBegan](#CaptureBegan)

[CaptureEnded](#CaptureEnded)

[CaptureSaved](#CaptureSaved)

[UserCaptureSaved](#UserCaptureSaved)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
