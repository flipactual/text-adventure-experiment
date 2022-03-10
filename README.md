# text-adventure-engine

```mermaid
classDiagram
class EngineArgs~Flags extends Record❬string, boolean❭, Scenes extends Record❬string, Scene❭~ {
  <<Type>>
  flags: Flags
  scenes: Scenes
  startingScene: keyof Scenes
}
EngineArgs .. Scene
class Executable~T~ {
  <<Interface>>
  execute(flags: ReadOnly~EngineArgs['flags']~) T
}
class Scene {
  description: string
  actions: Action[]
  execute(flags: ReadOnly~EngineArgs['flags']~) string
}
Scene .. Action
Scene --|> Executable : extends
class Action {
  trigger: Trigger
  execute(flags: ReadOnly~EngineArgs['flags']~) Result
}
Action .. Trigger
Action .. Result
Action --|> Executable : extends
class Trigger {
  @TODO
}
class Result {
  <<Enum>>
  FLAG_TRUE
  FLAG_FALSE
  FLAG_TOGGLE
  GOTO
}
class Engine {
  -flags: EngineArgs['flags']
  -scenes: EngineArgs['scenes']
  +constructor(args: EngineArgs)
  +handleInput(input: string)
  -parseInput(verb: string, noun: string) Command
  -executeCommand(flags: ReadOnly~EngineArgs['flags']~, command: Command)
}
Engine .. EngineArgs
Engine .. Command
class Command {
  +string verb
  +string noun
}
```
