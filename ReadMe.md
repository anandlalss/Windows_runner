# Description
ClearScript is a library that makes it easy to add scripting to your .NET applications. It currently supports JavaScript (via [V8](https://developers.google.com/v8/) and [JScript](https://docs.microsoft.com/en-us/previous-versions//hbxc2t98(v=vs.85))) and [VBScript](https://docs.microsoft.com/en-us/previous-versions//t0aew7h6(v=vs.85)).

# Features
* Simple usage; create a script engine, add your objects and/or types, run scripts
* Support for several script engines: [Google's V8](https://developers.google.com/v8/), [Microsoft's JScript](https://docs.microsoft.com/en-us/previous-versions//hbxc2t98(v=vs.85)) and [VBScript](https://docs.microsoft.com/en-us/previous-versions//t0aew7h6(v=vs.85))
* Exposed resources require no modification, decoration, or special coding of any kind
* Scripts get simple access to most of the features of exposed objects and types:
  * Methods, properties, fields, events
  * (Objects) Indexers, extension methods, conversion operators, explicitly implemented interfaces
  * (Types) Constructors, nested types
* Full support for generic types and methods, including C#-like type inference and explicit type arguments
* Scripts can invoke methods with output parameters, optional parameters, and parameter arrays
* Script delegates enable callbacks into script code
* Support for exposing all the types defined in one or more assemblies in one step
* Optional support for importing types and assemblies from script code
* The host can invoke script functions and access script objects directly
* Full support for script debugging
* (V8) Support for fast data transfer to and from [JavaScript typed arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Typed_arrays)
* (V8) Support for [JavaScript modules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
* (JavaScript) Support for [CommonJS modules](http://wiki.commonjs.org/wiki/Modules)
* :new: Support for .NET Core 3.1 and .NET 5.0 on Windows (x86/x64/arm64), Linux (x64/arm64), and macOS (x64).

# Installation
### Composite packages
* [![ClearScript](https://img.shields.io/nuget/vpre/Microsoft.ClearScript?label=Windows%20(x86/x64)&logo=Windows&logoColor=white)](https://www.nuget.org/packages/Microsoft.ClearScript)
* [![ClearScript.linux-x64](https://img.shields.io/nuget/vpre/Microsoft.ClearScript.linux-x64?label=Linux%20(x64)&logo=Linux&logoColor=white)](https://www.nuget.org/packages/Microsoft.ClearScript.linux-x64)
* [![ClearScript.osx-x64](https://img.shields.io/nuget/vpre/Microsoft.ClearScript.osx-x64?label=macOS%20(x64)&logo=Apple&logoColor=white)](https://www.nuget.org/packages/Microsoft.ClearScript.osx-x64)
### Component packages
* [![ClearScript.Core](https://img.shields.io/nuget/vpre/Microsoft.ClearScript.Core?label=ClearScript.Core&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB3aWR0aD0iNjguNjU5bW0iIGhlaWdodD0iNjMuMTYzbW0iIHZlcnNpb249IjEuMSIgdmlld0JveD0iMCAwIDY4LjY1OSA2My4xNjMiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6Y2M9Imh0dHA6Ly9jcmVhdGl2ZWNvbW1vbnMub3JnL25zIyIgeG1sbnM6ZGM9Imh0dHA6Ly9wdXJsLm9yZy9kYy9lbGVtZW50cy8xLjEvIiB4bWxuczpyZGY9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkvMDIvMjItcmRmLXN5bnRheC1ucyMiPgogPG1ldGFkYXRhPgogIDxyZGY6UkRGPgogICA8Y2M6V29yayByZGY6YWJvdXQ9IiI+CiAgICA8ZGM6Zm9ybWF0PmltYWdlL3N2Zyt4bWw8L2RjOmZvcm1hdD4KICAgIDxkYzp0eXBlIHJkZjpyZXNvdXJjZT0iaHR0cDovL3B1cmwub3JnL2RjL2RjbWl0eXBlL1N0aWxsSW1hZ2UiLz4KICAgIDxkYzp0aXRsZS8+CiAgIDwvY2M6V29yaz4KICA8L3JkZjpSREY+CiA8L21ldGFkYXRhPgogPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoLS4xNzM2MykiPgogIDxnIGZpbGw9IiNmZmYiIHN0cm9rZS13aWR0aD0iLjI2NDU4IiBhcmlhLWxhYmVsPSJDICAgIFMiPgogICA8cGF0aCBkPSJtMTguODc2LTIuNDQwMWUtN3EzLjYyMTUgMCA2Ljk5NDkgMS41ODc1IDEuNTg3NSAwLjc0NDE0IDIuMjA3NiAwLjc0NDE0IDAuNDQ2NDggMCAxLjQzODctMC4yMjMyNCAwLjMyMjQ2LTAuMDc0NDE0IDAuNzE5MzQtMC4wNzQ0MTQgMS4yODk4IDAgMi4yNTcyIDEuMTkwNiAyLjM4MTIgMi44NzczIDIuMzgxMiA3LjE0MzcgMCAzLjAwMTQtMi4wNTg4IDQuMzkwNC0xLjExNjIgMC43NDQxNC0yLjUwNTMgMC43NDQxNC0xLjI2NSAwLTIuMDU4OC0wLjU0NTd0LTEuNTM3OS0xLjkzNDhxLTEuMDY2Ni0xLjk1OTYtMS43MzYzLTIuODAyOS0wLjY2OTczLTAuODY4MTYtMS42MzcxLTEuNTYyNy0yLjQwNjEtMS42ODY3LTUuMDM1NC0xLjY4NjctMi41NTQ5IDAtNC4wNjggMS44NjA0LTEuNDg4MyAxLjgzNTUtMS40ODgzIDQuOTM2MSAwIDQuMjY2NCAyLjE1OCA3LjgxMzUgMi45MjcgNC43Mzc3IDguMzg0IDQuNzM3NyAyLjAwOTIgMCAzLjk2ODgtMC42Njk3MyAxLjk4NDQtMC42Njk3MyAzLjA3NTgtMS43MzYzIDAuOTQyNTgtMC44OTI5NyAxLjUzNzktMC44OTI5NyAwLjg2ODE2IDAgMS40ODgzIDAuODE4NTYgMC42MjAxMiAwLjc5Mzc1IDAuNjIwMTIgMS45MzQ4IDAgMS40Mzg3LTAuODY4MTYgMy4yMjQ2dC0yLjA4MzYgMi44MDI5cS0wLjUyMDkgMC40MjE2OC0yLjE1OCAwLjc0NDE0LTAuOTQyNTggMC4xNzM2My0yLjUwNTMgMC45MTc3Ny0zLjY3MTEgMS43NjExLTcuNjM5OCAxLjc2MTEtNC4xNDI0IDAtOC4yNi0xLjg2MDQtNC43ODczLTIuMTU4LTcuNTY1NC02LjYyMjktMi43Mjg1LTQuMzQwOC0yLjcyODUtOS4wNzg1IDAtNS41MDY2IDMuNDIzLTEwLjA0NiAyLjk3NjYtMy45NDM5IDcuNzYzOS02LjAyNzUgMy42NDYzLTEuNTg3NSA3LjUxNTgtMS41ODc1eiIvPgogICA8cGF0aCBkPSJtNTMuMDU3IDI3Ljk0cTIuNTU0OSAwIDYuNjk3MyAxLjI2NSAwLjQ5NjA5IDAuMTQ4ODMgMC43OTM3NSAwLjE0ODgzIDAuMjQ4MDUgMCAxLjQ4ODMtMC40NDY0OCAwLjM5Njg4LTAuMTQ4ODMgMC44NDMzNi0wLjE0ODgzIDEuNjYxOSAwIDMuNDk3NSAyLjYyOTMgMS44NjA0IDIuNjI5MyAxLjg2MDQgNS4wMTA1IDAgMS4zODkxLTAuODQzMzYgMi4zNTY0LTAuODE4NTYgMC45NDI1OC0yLjAwOTIgMC45NDI1OC0wLjk5MjE5IDAtMS42MTIzLTAuMzk2ODgtMC42MjAxMi0wLjM5Njg4LTIuNzI4NS0yLjM1NjQtMi45NzY2LTIuNzc4MS01Ljg1MzktMi43NzgxLTEuMzg5MSAwLTIuMjMyNCAwLjY2OTczLTAuODE4NTYgMC42Njk3My0wLjgxODU2IDEuNzYxMSAwIDIuMTU4IDMuNzk1MSAzLjI0OTQgNS4xMzQ2IDEuNTEzMSA2LjU3MzIgMi4yMDc2IDYuMzI1MiAzLjA3NTggNi4zMjUyIDkuMDUzNyAwIDUuMjgzNC00LjMxNiA4LjYzMi00LjQxNTIgMy40MjMtMTEuNTM0IDMuNDIzLTMuMTc1IDAtNi42OTczLTAuNzQ0MTQtMy41MjIzLTAuNzY4OTQtNS4wODUtMS43ODU5LTEuMTkwNi0wLjc5Mzc1LTIuMTU4LTMuNDQ3OS0wLjk0MjU4LTIuNjc4OS0wLjk0MjU4LTUuMjA5IDAtMS4yMTU0IDAuNDk2MDktMS44MzU1IDAuNjIwMTItMC43OTM3NSAxLjU2MjctMC43OTM3NSAwLjk0MjU4IDAgMS44MTA3IDAuOTY3MzggMC41MjA5IDAuNTQ1NyAyLjQ1NTcgMy40OTc1IDAuOTE3NzcgMS4zODkxIDIuOTAyMSAyLjMwNjggMi4wMDkyIDAuOTE3NzcgNC4xNDI0IDAuOTE3NzcgMS44MzU1IDAgMi45NzY2LTAuNjY5NzMgMS4xNDEtMC42OTQ1MyAxLjE0MS0xLjc2MTEgMC0wLjk5MjE5LTAuODkyOTctMS43MTE1dC0yLjkwMjEtMS4zMzk1cS0zLjU0NzEtMS4xMTYyLTUuNDA3NC0yLjAzNC0xLjg2MDQtMC45NDI1OC0zLjQ3MjctMi4zNTY0LTMuOTE5MS0zLjQ3MjctMy45MTkxLTcuODg3OSAwLTIuMTgyOCAxLjAxNy00LjI0MTYgMS4wMTctMi4wODM2IDIuODc3My0zLjU5NjcgNC4xNjcyLTMuNDk3NSAxMC4xNy0zLjQ5NzV6Ii8+CiAgPC9nPgogPC9nPgo8L3N2Zz4K&logoColor=white)](https://www.nuget.org/packages/Microsoft.ClearScript.Core)
* [![ClearScript.Windows](https://img.shields.io/nuget/vpre/Microsoft.ClearScript.Windows?label=ClearScript.Windows&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB3aWR0aD0iNjguNjU5bW0iIGhlaWdodD0iNjMuMTYzbW0iIHZlcnNpb249IjEuMSIgdmlld0JveD0iMCAwIDY4LjY1OSA2My4xNjMiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6Y2M9Imh0dHA6Ly9jcmVhdGl2ZWNvbW1vbnMub3JnL25zIyIgeG1sbnM6ZGM9Imh0dHA6Ly9wdXJsLm9yZy9kYy9lbGVtZW50cy8xLjEvIiB4bWxuczpyZGY9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkvMDIvMjItcmRmLXN5bnRheC1ucyMiPgogPG1ldGFkYXRhPgogIDxyZGY6UkRGPgogICA8Y2M6V29yayByZGY6YWJvdXQ9IiI+CiAgICA8ZGM6Zm9ybWF0PmltYWdlL3N2Zyt4bWw8L2RjOmZvcm1hdD4KICAgIDxkYzp0eXBlIHJkZjpyZXNvdXJjZT0iaHR0cDovL3B1cmwub3JnL2RjL2RjbWl0eXBlL1N0aWxsSW1hZ2UiLz4KICAgIDxkYzp0aXRsZS8+CiAgIDwvY2M6V29yaz4KICA8L3JkZjpSREY+CiA8L21ldGFkYXRhPgogPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoLS4xNzM2MykiPgogIDxnIGZpbGw9IiNmZmYiIHN0cm9rZS13aWR0aD0iLjI2NDU4IiBhcmlhLWxhYmVsPSJDICAgIFMiPgogICA8cGF0aCBkPSJtMTguODc2LTIuNDQwMWUtN3EzLjYyMTUgMCA2Ljk5NDkgMS41ODc1IDEuNTg3NSAwLjc0NDE0IDIuMjA3NiAwLjc0NDE0IDAuNDQ2NDggMCAxLjQzODctMC4yMjMyNCAwLjMyMjQ2LTAuMDc0NDE0IDAuNzE5MzQtMC4wNzQ0MTQgMS4yODk4IDAgMi4yNTcyIDEuMTkwNiAyLjM4MTIgMi44NzczIDIuMzgxMiA3LjE0MzcgMCAzLjAwMTQtMi4wNTg4IDQuMzkwNC0xLjExNjIgMC43NDQxNC0yLjUwNTMgMC43NDQxNC0xLjI2NSAwLTIuMDU4OC0wLjU0NTd0LTEuNTM3OS0xLjkzNDhxLTEuMDY2Ni0xLjk1OTYtMS43MzYzLTIuODAyOS0wLjY2OTczLTAuODY4MTYtMS42MzcxLTEuNTYyNy0yLjQwNjEtMS42ODY3LTUuMDM1NC0xLjY4NjctMi41NTQ5IDAtNC4wNjggMS44NjA0LTEuNDg4MyAxLjgzNTUtMS40ODgzIDQuOTM2MSAwIDQuMjY2NCAyLjE1OCA3LjgxMzUgMi45MjcgNC43Mzc3IDguMzg0IDQuNzM3NyAyLjAwOTIgMCAzLjk2ODgtMC42Njk3MyAxLjk4NDQtMC42Njk3MyAzLjA3NTgtMS43MzYzIDAuOTQyNTgtMC44OTI5NyAxLjUzNzktMC44OTI5NyAwLjg2ODE2IDAgMS40ODgzIDAuODE4NTYgMC42MjAxMiAwLjc5Mzc1IDAuNjIwMTIgMS45MzQ4IDAgMS40Mzg3LTAuODY4MTYgMy4yMjQ2dC0yLjA4MzYgMi44MDI5cS0wLjUyMDkgMC40MjE2OC0yLjE1OCAwLjc0NDE0LTAuOTQyNTggMC4xNzM2My0yLjUwNTMgMC45MTc3Ny0zLjY3MTEgMS43NjExLTcuNjM5OCAxLjc2MTEtNC4xNDI0IDAtOC4yNi0xLjg2MDQtNC43ODczLTIuMTU4LTcuNTY1NC02LjYyMjktMi43Mjg1LTQuMzQwOC0yLjcyODUtOS4wNzg1IDAtNS41MDY2IDMuNDIzLTEwLjA0NiAyLjk3NjYtMy45NDM5IDcuNzYzOS02LjAyNzUgMy42NDYzLTEuNTg3NSA3LjUxNTgtMS41ODc1eiIvPgogICA8cGF0aCBkPSJtNTMuMDU3IDI3Ljk0cTIuNTU0OSAwIDYuNjk3MyAxLjI2NSAwLjQ5NjA5IDAuMTQ4ODMgMC43OTM3NSAwLjE0ODgzIDAuMjQ4MDUgMCAxLjQ4ODMtMC40NDY0OCAwLjM5Njg4LTAuMTQ4ODMgMC44NDMzNi0wLjE0ODgzIDEuNjYxOSAwIDMuNDk3NSAyLjYyOTMgMS44NjA0IDIuNjI5MyAxLjg2MDQgNS4wMTA1IDAgMS4zODkxLTAuODQzMzYgMi4zNTY0LTAuODE4NTYgMC45NDI1OC0yLjAwOTIgMC45NDI1OC0wLjk5MjE5IDAtMS42MTIzLTAuMzk2ODgtMC42MjAxMi0wLjM5Njg4LTIuNzI4NS0yLjM1NjQtMi45NzY2LTIuNzc4MS01Ljg1MzktMi43NzgxLTEuMzg5MSAwLTIuMjMyNCAwLjY2OTczLTAuODE4NTYgMC42Njk3My0wLjgxODU2IDEuNzYxMSAwIDIuMTU4IDMuNzk1MSAzLjI0OTQgNS4xMzQ2IDEuNTEzMSA2LjU3MzIgMi4yMDc2IDYuMzI1MiAzLjA3NTggNi4zMjUyIDkuMDUzNyAwIDUuMjgzNC00LjMxNiA4LjYzMi00LjQxNTIgMy40MjMtMTEuNTM0IDMuNDIzLTMuMTc1IDAtNi42OTczLTAuNzQ0MTQtMy41MjIzLTAuNzY4OTQtNS4wODUtMS43ODU5LTEuMTkwNi0wLjc5Mzc1LTIuMTU4LTMuNDQ3OS0wLjk0MjU4LTIuNjc4OS0wLjk0MjU4LTUuMjA5IDAtMS4yMTU0IDAuNDk2MDktMS44MzU1IDAuNjIwMTItMC43OTM3NSAxLjU2MjctMC43OTM3NSAwLjk0MjU4IDAgMS44MTA3IDAuOTY3MzggMC41MjA5IDAuNTQ1NyAyLjQ1NTcgMy40OTc1IDAuOTE3NzcgMS4zODkxIDIuOTAyMSAyLjMwNjggMi4wMDkyIDAuOTE3NzcgNC4xNDI0IDAuOTE3NzcgMS44MzU1IDAgMi45NzY2LTAuNjY5NzMgMS4xNDEtMC42OTQ1MyAxLjE0MS0xLjc2MTEgMC0wLjk5MjE5LTAuODkyOTctMS43MTE1dC0yLjkwMjEtMS4zMzk1cS0zLjU0NzEtMS4xMTYyLTUuNDA3NC0yLjAzNC0xLjg2MDQtMC45NDI1OC0zLjQ3MjctMi4zNTY0LTMuOTE5MS0zLjQ3MjctMy45MTkxLTcuODg3OSAwLTIuMTgyOCAxLjAxNy00LjI0MTYgMS4wMTctMi4wODM2IDIuODc3My0zLjU5NjcgNC4xNjcyLTMuNDk3NSAxMC4xNy0zLjQ5NzV6Ii8+CiAgPC9nPgogPC9nPgo8L3N2Zz4K&logoColor=white)](https://www.nuget.org/packages/Microsoft.ClearScript.Windows)
* [![ClearScript.V8](https://img.shields.io/nuget/vpre/Microsoft.ClearScript.V8?label=ClearScript.V8&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB3aWR0aD0iNjguNjU5bW0iIGhlaWdodD0iNjMuMTYzbW0iIHZlcnNpb249IjEuMSIgdmlld0JveD0iMCAwIDY4LjY1OSA2My4xNjMiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6Y2M9Imh0dHA6Ly9jcmVhdGl2ZWNvbW1vbnMub3JnL25zIyIgeG1sbnM6ZGM9Imh0dHA6Ly9wdXJsLm9yZy9kYy9lbGVtZW50cy8xLjEvIiB4bWxuczpyZGY9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkvMDIvMjItcmRmLXN5bnRheC1ucyMiPgogPG1ldGFkYXRhPgogIDxyZGY6UkRGPgogICA8Y2M6V29yayByZGY6YWJvdXQ9IiI+CiAgICA8ZGM6Zm9ybWF0PmltYWdlL3N2Zyt4bWw8L2RjOmZvcm1hdD4KICAgIDxkYzp0eXBlIHJkZjpyZXNvdXJjZT0iaHR0cDovL3B1cmwub3JnL2RjL2RjbWl0eXBlL1N0aWxsSW1hZ2UiLz4KICAgIDxkYzp0aXRsZS8+CiAgIDwvY2M6V29yaz4KICA8L3JkZjpSREY+CiA8L21ldGFkYXRhPgogPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoLS4xNzM2MykiPgogIDxnIGZpbGw9IiNmZmYiIHN0cm9rZS13aWR0aD0iLjI2NDU4IiBhcmlhLWxhYmVsPSJDICAgIFMiPgogICA8cGF0aCBkPSJtMTguODc2LTIuNDQwMWUtN3EzLjYyMTUgMCA2Ljk5NDkgMS41ODc1IDEuNTg3NSAwLjc0NDE0IDIuMjA3NiAwLjc0NDE0IDAuNDQ2NDggMCAxLjQzODctMC4yMjMyNCAwLjMyMjQ2LTAuMDc0NDE0IDAuNzE5MzQtMC4wNzQ0MTQgMS4yODk4IDAgMi4yNTcyIDEuMTkwNiAyLjM4MTIgMi44NzczIDIuMzgxMiA3LjE0MzcgMCAzLjAwMTQtMi4wNTg4IDQuMzkwNC0xLjExNjIgMC43NDQxNC0yLjUwNTMgMC43NDQxNC0xLjI2NSAwLTIuMDU4OC0wLjU0NTd0LTEuNTM3OS0xLjkzNDhxLTEuMDY2Ni0xLjk1OTYtMS43MzYzLTIuODAyOS0wLjY2OTczLTAuODY4MTYtMS42MzcxLTEuNTYyNy0yLjQwNjEtMS42ODY3LTUuMDM1NC0xLjY4NjctMi41NTQ5IDAtNC4wNjggMS44NjA0LTEuNDg4MyAxLjgzNTUtMS40ODgzIDQuOTM2MSAwIDQuMjY2NCAyLjE1OCA3LjgxMzUgMi45MjcgNC43Mzc3IDguMzg0IDQuNzM3NyAyLjAwOTIgMCAzLjk2ODgtMC42Njk3MyAxLjk4NDQtMC42Njk3MyAzLjA3NTgtMS43MzYzIDAuOTQyNTgtMC44OTI5NyAxLjUzNzktMC44OTI5NyAwLjg2ODE2IDAgMS40ODgzIDAuODE4NTYgMC42MjAxMiAwLjc5Mzc1IDAuNjIwMTIgMS45MzQ4IDAgMS40Mzg3LTAuODY4MTYgMy4yMjQ2dC0yLjA4MzYgMi44MDI5cS0wLjUyMDkgMC40MjE2OC0yLjE1OCAwLjc0NDE0LTAuOTQyNTggMC4xNzM2My0yLjUwNTMgMC45MTc3Ny0zLjY3MTEgMS43NjExLTcuNjM5OCAxLjc2MTEtNC4xNDI0IDAtOC4yNi0xLjg2MDQtNC43ODczLTIuMTU4LTcuNTY1NC02LjYyMjktMi43Mjg1LTQuMzQwOC0yLjcyODUtOS4wNzg1IDAtNS41MDY2IDMuNDIzLTEwLjA0NiAyLjk3NjYtMy45NDM5IDcuNzYzOS02LjAyNzUgMy42NDYzLTEuNTg3NSA3LjUxNTgtMS41ODc1eiIvPgogICA8cGF0aCBkPSJtNTMuMDU3IDI3Ljk0cTIuNTU0OSAwIDYuNjk3MyAxLjI2NSAwLjQ5NjA5IDAuMTQ4ODMgMC43OTM3NSAwLjE0ODgzIDAuMjQ4MDUgMCAxLjQ4ODMtMC40NDY0OCAwLjM5Njg4LTAuMTQ4ODMgMC44NDMzNi0wLjE0ODgzIDEuNjYxOSAwIDMuNDk3NSAyLjYyOTMgMS44NjA0IDIuNjI5MyAxLjg2MDQgNS4wMTA1IDAgMS4zODkxLTAuODQzMzYgMi4zNTY0LTAuODE4NTYgMC45NDI1OC0yLjAwOTIgMC45NDI1OC0wLjk5MjE5IDAtMS42MTIzLTAuMzk2ODgtMC42MjAxMi0wLjM5Njg4LTIuNzI4NS0yLjM1NjQtMi45NzY2LTIuNzc4MS01Ljg1MzktMi43NzgxLTEuMzg5MSAwLTIuMjMyNCAwLjY2OTczLTAuODE4NTYgMC42Njk3My0wLjgxODU2IDEuNzYxMSAwIDIuMTU4IDMuNzk1MSAzLjI0OTQgNS4xMzQ2IDEuNTEzMSA2LjU3MzIgMi4yMDc2IDYuMzI1MiAzLjA3NTggNi4zMjUyIDkuMDUzNyAwIDUuMjgzNC00LjMxNiA4LjYzMi00LjQxNTIgMy40MjMtMTEuNTM0IDMuNDIzLTMuMTc1IDAtNi42OTczLTAuNzQ0MTQtMy41MjIzLTAuNzY4OTQtNS4wODUtMS43ODU5LTEuMTkwNi0wLjc5Mzc1LTIuMTU4LTMuNDQ3OS0wLjk0MjU4LTIuNjc4OS0wLjk0MjU4LTUuMjA5IDAtMS4yMTU0IDAuNDk2MDktMS44MzU1IDAuNjIwMTItMC43OTM3NSAxLjU2MjctMC43OTM3NSAwLjk0MjU4IDAgMS44MTA3IDAuOTY3MzggMC41MjA5IDAuNTQ1NyAyLjQ1NTcgMy40OTc1IDAuOTE3NzcgMS4zODkxIDIuOTAyMSAyLjMwNjggMi4wMDkyIDAuOTE3NzcgNC4xNDI0IDAuOTE3NzcgMS44MzU1IDAgMi45NzY2LTAuNjY5NzMgMS4xNDEtMC42OTQ1MyAxLjE0MS0xLjc2MTEgMC0wLjk5MjE5LTAuODkyOTctMS43MTE1dC0yLjkwMjEtMS4zMzk1cS0zLjU0NzEtMS4xMTYyLTUuNDA3NC0yLjAzNC0xLjg2MDQtMC45NDI1OC0zLjQ3MjctMi4zNTY0LTMuOTE5MS0zLjQ3MjctMy45MTkxLTcuODg3OSAwLTIuMTgyOCAxLjAxNy00LjI0MTYgMS4wMTctMi4wODM2IDIuODc3My0zLjU5NjcgNC4xNjcyLTMuNDk3NSAxMC4xNy0zLjQ5NzV6Ii8+CiAgPC9nPgogPC9nPgo8L3N2Zz4K&logoColor=white)](https://www.nuget.org/packages/Microsoft.ClearScript.V8)
### V8 native assembly packages
* [![ClearScript.V8.Native.win-x86](https://img.shields.io/nuget/vpre/Microsoft.ClearScript.V8.Native.win-x86?label=Windows%20(x86)&logo=V8&logoColor=white)](https://www.nuget.org/packages/Microsoft.ClearScript.V8.Native.win-x86)
* [![ClearScript.V8.Native.win-x64](https://img.shields.io/nuget/vpre/Microsoft.ClearScript.V8.Native.win-x64?label=Windows%20(x64)&logo=V8&logoColor=white)](https://www.nuget.org/packages/Microsoft.ClearScript.V8.Native.win-x64)
* [![ClearScript.V8.Native.linux-x64](https://img.shields.io/nuget/vpre/Microsoft.ClearScript.V8.Native.linux-x64?label=Linux%20(x64)&logo=V8&logoColor=white)](https://www.nuget.org/packages/Microsoft.ClearScript.V8.Native.linux-x64)
* [![ClearScript.V8.Native.osx-x64](https://img.shields.io/nuget/vpre/Microsoft.ClearScript.V8.Native.osx-x64?label=macOS%20(x64)&logo=V8&logoColor=white)](https://www.nuget.org/packages/Microsoft.ClearScript.V8.Native.osx-x64)

# Documentation
* [Examples](https://microsoft.github.io/ClearScript/Examples/Examples.html)
* [Tutorial](https://microsoft.github.io/ClearScript/Tutorial/FAQtorial.html)
* [API reference](https://microsoft.github.io/ClearScript/Reference/index.html)
* [Building, integrating, and deploying ClearScript](https://microsoft.github.io/ClearScript/Details/Build.html)
* [Old project site on CodePlex](https://clearscript.codeplex.com/)
