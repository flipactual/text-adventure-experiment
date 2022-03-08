# text-adventure-engine

```mermaid
classDiagram
class Engine~State extends Record~ {
  -State state
  +processInput(input: string)
  -parseCommand(verb: string, noun: string) Command
  -executeCommand(world: World, command: Command) State
}
class Command {
  +string verb
  +string noun
}
```
