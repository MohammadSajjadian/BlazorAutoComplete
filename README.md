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
              AllItems="YourItemList"
              SelectedItems="SelectedItems"
              ItemText="item => item.Name"
              PlaceholderText="Search items..."
              EmptyMessage="No items found"
              DarkMode="true"
              SelectedItemsChanged="OnSelectedItemsChanged" />
```


## Parameters

| Parameter              | Type                         | Description                                                                                                                      |
|------------------------|------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| `AllItems`             | `List<TItem>`                | The list of all items available to select. **Required.**                                                                         |
| `SelectedItems`        | `List<TItem>`                | The list of items currently selected by the user.                                                                                |
| `SelectedItemsChanged` | `EventCallback<List<TItem>>` | Invoked whenever the selected items list changes.                                                                                |
| `ItemText`             | `Func<TItem, string>`        | Function defining how to display an item as text when no template is provided. Defaults to `item => item?.ToString() ?? ""`.     |
| `PlaceholderText`      | `string`                     | Text displayed in the input box when empty. Default: `"Type to search..."`.                                                      |
| `EmptyMessage`         | `string`                     | Text shown when no matching items are found. Default: `"No record found..."`.                                                    |
| `IsDisabled`           | `bool`                       | Disables the autocomplete input when `true`.                                                                                     |
| `DarkMode`             | `bool`                       | Enables dark mode styling when `true`.                                                                                           |
| `ItemTemplate`         | `RenderFragment<TItem>`      | Optional template for rendering each item in the dropdown.                                                                       |
| `ChipTemplate`         | `RenderFragment<TItem>`      | Optional template for rendering each selected item as a chip.                                                                    |

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
![Untitled design (1)](https://github.com/user-attachments/assets/c29c4231-170a-40f8-854d-3023a151a97e)


### Dark mode
<img width="966" height="180" alt="Screenshot 2025-11-09 213402" src="https://github.com/user-attachments/assets/d3c0c608-0fb4-4122-9f44-5ab4569ec6f5" />

See the live demo on: www.mohammadsajjadian.ir/demo/auto-complete
---

## Notes

- Ensure `DisplayItem` is set for custom types; otherwise, `.ToString()` is used.
- The dropdown opens on focus and closes shortly after losing focus.

---

## License

MIT License

