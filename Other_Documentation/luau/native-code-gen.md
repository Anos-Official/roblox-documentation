<!-- Source: https://create.roblox.com/docs/luau/native-code-gen -->

Native code generation | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/luau/native-code-gen.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/scripting)
6. /
7. Advanced

# Native code generation

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/luau/native-code-gen.md)

With Luau support for native code generation, scripts¹ in your game can be compiled directly into the machine code instructions that CPUs execute, rather than regular bytecode that the Luau VM operates on. This feature can improve execution speed for some supported scripts, particularly those with a lot of numerical computation and few calls to heavy Luau libraries or Roblox APIs.

1  Native code generation is only supported for server-side scripts and client-side scripts on Android devices. In the future, more devices may be supported.

## [Enable native code generation](#enable-native-code-generation)[](#enable-native-code-generation)

To enable native code generation for a [Script](/docs/reference/engine/classes/Script) , add the --!native  comment at the top:²

```

--!native

print("Hello from native code!")

```

This enables native code generation for all functions in the script, and the top-level scope, if deemed profitable. No additional changes are required; behavior of the natively executing scripts is exactly the same as before and only the performance is different. All features of the Luau language and all Roblox APIs remain supported.

Alternatively, you can enable native code generation for an individual function by adding the @native  attribute:

```

@native

local function f(x)

  return (x + 1)

end

```

 2  In the future, some scripts might automatically start running natively if it is determined to be profitable, but manually placed --!native  comments are currently required.

## [Best practices](#best-practices)[](#best-practices)

The following tips will help you benefit most from native code generation:

-

It's best to enable this feature inside scripts that perform a lot of computation directly inside Luau. If you have a lot of mathematical operations on tables and especially [buffer](/docs/reference/engine/libraries/buffer)  types, the script may be a good candidate.

-

Only the script's [functions](/docs/luau/functions)  are compiled natively. The code in the top outer [scope](/docs/luau/scope)  is often executed only once and doesn't benefit as much as functions that are called many times, especially those that are called every frame.

-

It's recommended that you measure the time a script or a function takes with and without native compilation to judge when it's best to use it. The [Script Profiler](#script-profiler)  tool can measure the performance of functions in order to make informed decisions.

-

It may be tempting to place the --!native  comment in every  script just in case some of them will execute faster, but native code generation has some drawbacks:

-

Code compilation time is required which can increase the startup time of servers.

-

Extra memory is occupied to store natively compiled code.

-

There's a limit on the total allowed amount of natively compiled code in a game.

These problems can be addressed by a judicious use of the @native  attribute.

## [Code to avoid](#code-to-avoid)[](#code-to-avoid)

While all features will behave the same with or without native code generation enabled, some of them will not run natively and might cause de‑optimization or a fallback to interpreted execution. These include:

-

Use of deprecated [getfenv()](/docs/reference/engine/globals/LuaGlobals#getfenv) /[setfenv()](/docs/reference/engine/globals/LuaGlobals#setfenv)  calls.

-

Use of various Luau built‑in functions like [math.asin()](/docs/reference/engine/libraries/math#asin)  with non‑numeric arguments.

-

Passing improperly typed parameters to typed functions, for example calling foo(true)  when foo  is declared as function foo(arg: string) . Remember to always use correct [type annotations](#use-type-annotations) .

When using the [Script Profiler](#script-profiler) , you can compare time taken by a regular version of the function versus the one compiled natively. If a function inside a --!native  script or marked with @native  doesn't appear to be natively executing, one or more factors from the list above may be triggering de‑optimization.

## [Use type annotations](#use-type-annotations)[](#use-type-annotations)

Native code generation attempts to infer the most likely type for a given variable in order to optimize code paths. For example, it's assumed that a + b  is performed on numbers, or that a table is accessed in t.X . Given operator overloading, however, a  and b  may be tables or [Vector3](/docs/reference/engine/datatypes/Vector3)  types, or t  may be a Roblox datatype.

While native code generation will support any type, mispredictions may trigger unnecessary checks, resulting in slower code execution.

To solve some common issues, Luau type annotations on function arguments are checked, but it's especially recommended to annotate [Vector3](/docs/reference/engine/datatypes/Vector3)  arguments:

```

--!native

-- "v" is assumed to be a table; function performs slower due to table checks

local function sumComponentsSlow(v)

	return v.X + v.Y + v.Z

end

-- "v" is declared to be a Vector3; code specialized for vectors is generated

local function sumComponentsFast(v: Vector3)

	return v.X + v.Y + v.Z

end

```

## [Studio tooling](#studio-tooling)[](#studio-tooling)

The following Studio tooling is supported for --!native  scripts and @native  functions.

### [Debugging](#debugging)[](#debugging)

General [debugging](/docs/studio/debugging)  of scripts is supported, but the views for locals/upvalues may be incomplete and missing variables from [call stack](/docs/studio/debugging#call-stack-window)  frames that are executing natively.

Also note that when debugging code selected for native compilation, placing [breakpoints](/docs/studio/debugging#insert-breakpoints)  will disable native execution for those functions.

### [Script Profiler](#script-profiler)[](#script-profiler)

In the [Script Profiler](/docs/studio/optimization/scriptprofiler) , functions executing natively display <native>  next to them:

 ![Example of native functions flagged in the Script Profiler](https://prod.docsiteassets.roblox.com/assets/studio/console/ScriptProfiler-Native-Annotation.png)

If a function marked @native  or inside a --!native  script doesn't show the <native>  annotation, that function may not be executing natively due to [breakpoint](/docs/studio/debugging#insert-breakpoints)  placement, use of [discouraged code](#code-to-avoid) , or mismatched [type annotations](#use-type-annotations) .

### [Luau heap](#luau-heap)[](#luau-heap)

In the [Luau heap](/docs/studio/optimization/memory-usage#luau-heap)  profiler, memory taken by native functions displays as [native]  elements in the graph.

 ![Example of native memory usage flagged in the Luau Heap profiler](https://prod.docsiteassets.roblox.com/assets/studio/console/LuauHeap-Native-Annotation.png)

### [Size analysis](#size-analysis)[](#size-analysis)

Every natively-compiled script consumes memory. When the size of compiled code reaches a predefined limit, native compilation stops and the remaining code is run non‑natively. This makes it essential to choose scripts carefully for native compilation.

To monitor the native code size of individual functions and scripts:

1.

Make sure you're in Server  view through the [client/server toggle](/docs/studio/testing-modes#toggle-clientserver)  button.

2.

Invoke debug.dumpcodesize()  from the [Command Bar](/docs/studio/overview#command-bar) .

In the [Output](/docs/studio/output)  window, you'll see the total number of scripts and functions that have been natively compiled up to the point of invocation, the memory consumed by their native code, and the native code size limit. Following the summary, you'll see a table for every natively‑compiled script in descending order of code size.

 ![Example of native code size displayed in the Output window.](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Native-Code-Size-Analysis.png)

For each script, the output displays the number of functions compiled and the native code memory consumption. Each function is then listed in descending order of native code size, with anonymous functions shown as [anonymous]  and entire scripts shown as [top level] . In the final column, the percentage is computed with respect to the native code size limit. Note that native code size of functions is reported precisely but the memory consumption for scripts is rounded up to the nearest page size.

## [Limits and troubleshooting](#limits-and-troubleshooting)[](#limits-and-troubleshooting)

Compiling code into instructions for a particular CPU requires additional storage memory. Additionally, optimizations for complex functions may take too much time to perform. Hitting an internal limit will report an error in Studio's [Output](/docs/studio/output)  window, including:

* Function 'f' at line 20 exceeded single code block instruction limit*

This error means that a single block of code inside a function used more than 64K instructions. This can be avoided by simplifying the function or by splitting it into individual smaller functions.

* Function 'f' at line 20 exceeded function code block limit*

This error means that a single function contains more than 32K internal blocks of code. Internal blocks of code do not exactly map to the control‑flow blocks in your script, but this error can be avoided by simplifying the control‑flow in the function or by splitting it into individual smaller functions.

* Function 'f' at line 200 exceeded total module instruction limit*

This error means that, in total, the function has reached a limit of 1 million instructions for the entire script. In some cases, the reported function itself may have a lot of instructions, or the limit may have been reached by functions earlier in the script. To avoid this issue, it's recommended to either move particularly large functions into a separate non‑native script or use @native  on the other functions. You can also try marking that separate script with --!native , but 1 million instructions takes up a lot of memory and you may exceed the memory limit.

* Function 'f' at line 20 encountered an internal lowering failure*  (or)
 * Internal error: Native code generation failed (assembly lowering)*

Sometimes a function contains complex bits of code that the native code compiler cannot currently handle. To avoid this error, inspect complex expressions in the code and split them up or simplify them, but also consider opening a bug report with an example of the code that failed for this reason.

* Memory allocation limit reached for native code generation*

This error means that the overall memory limit for native code data has been reached. To avoid this, try removing --!native  from the more memory‑intensive scripts, allowing more smaller scripts to fit under the limit. Alternatively, move large or infrequently called functions to a separate non‑native module.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
