# Command line access

Both Flax Engine and builded game (Flax executable) support various input command line arguments.
Using this feature can help with games development and can be involved in testing various scenarios.
It’s very common technique to build games on the separate machines or even in the cloud. For example, [Jenkins](https://jenkins-ci.org/) server can be used to invoke Flax Game Cooker to build game for a QA team so it will be ready right in the morning to test it.

Here is an example command that will build game project for Windows platform:

```
FlaxEditor.exe -project "<project-path>" -headless -std -build "Development.Windows 64bit"
```

It will also send the log (including C# API [Debug.Log](https://docs.flaxengine.com/api/FlaxEngine.Debug.html#FlaxEngine_Debug_Log_System_Object_)) to the standard process output so in case of issues they can be easily detected. What is, even more, the editor may start without a window (headless mode) and perform some additional actions like clearing cooker cache or project cache.
Of course, all those things can be made manually by using Flax Editor C# API and Editor Plugins (see [here](https://github.com/FlaxEngine/FlaxAPI/blob/master/FlaxEditor/API/Static/GameCooker.cs#L110)).

## Options

| Command | Description |
|--------|--------|
| **-widowed** | Starts the game in windowed mode (even if default builded game setting was fullscreen). |
| **-fullscreen** | Starts the game in fullscreen mode (even if default builded game setting was windowed). |
| **-vsync** | Forces to enable vertical synchronization when presenting the frame on screen. |
| **-novsync** | Forces to disable vertical synchronization when presenting the frame on screen. |
| **-nolog** | Disables output log file. |
| **-std** | Redirects log to the standard process output (std). |
| **-debug <ip:port>** | Sets the Mono debugger adress and port used for the remote debugging. The default Mono debugger IP=127.0.0.1, Port=41000+(process_id%1000). |
| **-headless** | Starts without windows, used by CL. |

## Editor-only options

| Command | Description |
|--------|--------|
| **-project <path>** | Startup project path. It must be specified to start the editor. |
| **-clearcache** | Clears the project cache before starting the editor. |
| **-clearcooker** | Clears the project Game Cooker cache before starting the editor. |
| **-build <preset.target>** | Starts the game building after editor launch and closes editor after building end. You can specify the single present name to build all its targets or specify both the present name and target name (separated by a dot. You can use braces if your preset/target name contains space characters. |
