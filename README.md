# POC Premake with Xcode
This proof of concept was created to test Premake with Xcode

## Steps
- Create a `main.cpp` with some code.
- Download [Premake](https://premake.github.io)
- Create a `premake5.lua` (you should use this name) with the following script:
```lua
  -- premake5.lua
workspace "HelloWorld"
    configurations { "Debug", "Release" }

project "HelloWorld"
    kind "ConsoleApp"
    language "C++"
    cppdialect "C++17"
    targetdir "bin/%{cfg.buildcfg}"

    files { "**.cpp" }

    filter "configurations:Debug"
        defines { "DEBUG" }
        symbols "On"

    filter "configurations:Release"
        defines { "NDEBUG" }
        optimize "On"
  ```
- Create Xcode project files with command `premake5 xcode4`
- Open `HelloWorld.xcworkspace` and run the project on Xcode
