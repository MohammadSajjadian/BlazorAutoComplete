# Blazor AutoComplete Component

[![NuGet](https://img.shields.io/nuget/v/MSJD.AutoComplete.svg)](https://www.nuget.org/packages/MSJD.AutoComplete)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

A flexible and reusable AutoComplete component for Blazor that supports multi-selection, custom display logic, dark/light mode, and keyboard navigation.

---

## Features
- Generic Multi-Select: Supports any type (@typeparam TItem) with multiple selectable items.
- Customizable Display: ItemTemplate for dropdown items, ChipTemplate for selected chips, and ItemText for complex types.
- Search-As-You-Type: Case-insensitive filtering of items.
- Keyboard Support: Backspace removes last item, Escape closes dropdown, Arrow keys navigate, Enter selects.
- Dark/Light Mode Styling: Toggle styling via the DarkMode parameter.
- Event Callback: SelectedItemsChanged triggers whenever selection changes.
---

## Installation

Install via .NET CLI:

```.NET CLI
dotnet add package MSJD.AutoComplete --version 1.2.0
```


## Add the component to your Blazor project

```razor
<AutoComplete TItem="YourItemType"
              Items="YourItemList"
              DisplayItem="item => item.Name"
              Placeholder="Search items..."
              EmptyText="No items found"
              DarkMode="true"
              SelectedItemsChanged="OnSelectedItemsChanged" />

```


## Parameters

| Parameter               | Type                           | Description                                                                                  |
|-------------------------|--------------------------------|----------------------------------------------------------------------------------------------|
| `Items`                 | `List<TItem>`                  | List of items to search from. **Required.**                                                  |
| `SelectedItemsChanged`  | `EventCallback<List<TItem>>`   | Invoked when selected items change.                                                         |
| `DisplayItem`           | `Func<TItem, string>`          | Function to define how each item is displayed. Defaults to `item.ToString()`.               |
| `EmptyText`             | `string`                        | Text displayed when no matching item is found. Default: `"No record found..."`.             |
| `Placeholder`           | `string`                        | Input placeholder text. Default: `"Type to search..."`.                                      |
| `IsDisabled`            | `bool`                          | Disables input when `true`.                                                                 |
| `DarkMode`              | `bool`                          | Enables dark mode styling when `true`.                                                      |

---

## Usage

- Multi-select with removable chips.
- Keyboard shortcuts:
  - **Backspace**: Removes the last selected item if input is empty.
  - **Escape**: Closes the dropdown.
- Event callback `SelectedItemsChanged` receives updated selected items:

```csharp
private async Task OnSelectedItemsChanged(List<YourItemType> items)
{
    // Handle updated list
}
```

---

## Demo

Here’s how the **Blazor AutoComplete** component looks in action 👇

### Demo Video
![Untitled design](https://github.com/user-attachments/assets/679db2d8-267a-43ff-afa5-23560f718938)




### Dark mode
<img width="1558" height="267" alt="Screenshot 2025-10-16 173243" src="https://github.com/user-attachments/assets/b4112a63-4c99-4a4c-9e49-0a7266e67b37" />

See the live demo on: www.mohammadsajjadian.ir/demo/auto-complete
---

## Notes

- Ensure `DisplayItem` is set for custom types; otherwise, `.ToString()` is used.
- The dropdown opens on focus and closes shortly after losing focus.

---

## License

MIT License

