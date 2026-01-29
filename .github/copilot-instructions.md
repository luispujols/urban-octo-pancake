# Copilot Workspace Instructions

## ⚠️ Mandatory Before Committing
```bash
dotnet build SocOps/SocOps.csproj  # Must pass with no errors/warnings
dotnet test                         # Run when tests exist
```

## Project Overview

**Soc Ops**: Blazor WebAssembly (.NET 10) social bingo game. Players find people matching icebreaker questions to get 5 in a row.

## Architecture

- **Services**: `BingoGameService` (stateful, localStorage persistence via JSInterop) → `BingoLogicService` (pure static methods)
- **Components**: `Home.razor` → `GameScreen`/`StartScreen` → `BingoBoard` → `BingoSquare`
- **Data**: [Questions.cs](SocOps/Data/Questions.cs) - add strings to `QuestionsList`

## Key Patterns

- **State**: Components subscribe to `GameService.OnStateChanged` event; use `_ = SaveGameStateAsync();` for fire-and-forget
- **Props**: `[Parameter]` for data, `EventCallback<T>` for events
- **Styling**: Custom utilities in [app.css](SocOps/wwwroot/css/app.css) (`.bg-accent`, `.bg-marked`, `.grid-cols-5`). Add new classes there, not inline.
