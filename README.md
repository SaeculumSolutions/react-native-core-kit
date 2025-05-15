# React Native Core Kit

![npm version](https://img.shields.io/npm/v/react-native-core-kit.svg)
![license](https://img.shields.io/npm/l/react-native-core-kit.svg)
![downloads](https://img.shields.io/npm/dm/react-native-core-kit.svg)

A comprehensive collection of customizable React Native components built on top of React Native Paper. Designed to accelerate development with themeable, responsive, and internationalized UI components.

## Features

✨ **Enhanced Paper Components** - Beautiful UI components extending React Native Paper  
🎨 **Theming Support** - Light/dark theme with easy customization  
🌐 **Internationalization** - Built-in i18n support for all components  
📱 **Responsive Design** - Components that scale across different devices  
⏰ **Timezone Utilities** - Format and display time in different timezones  
🔄 **Modern Dropdowns** - Flexible select components with search capability  
📋 **Form Components** - Validated input fields with customizable styling

## Installation

```bash
# Using npm
npm install react-native-core-kit

# Using yarn
yarn add react-native-core-kit
```

### Dependencies

This package requires the following peer dependencies:

```bash
npm install react-native-paper react-native-svg @react-native-picker/picker dayjs i18next react-i18next react-native-super-responsive
```

## Basic Usage

```jsx
import React, { useState } from "react";
import { View } from "react-native";
import {
  ThemeProvider,
  CustomButton,
  TextInput,
  CustomSearchBar,
  CustomDropdown,
} from "react-native-core-kit";

const App = () => {
  const [text, setText] = useState("");
  const [search, setSearch] = useState("");
  const [selectedValue, setSelectedValue] = useState("");

  const options = [
    { label: "Option 1", value: "opt1" },
    { label: "Option 2", value: "opt2" },
    { label: "Option 3", value: "opt3" },
  ];

  return (
    <ThemeProvider>
      <View style={{ padding: 16 }}>
        <TextInput
          value={text}
          onChangeText={setText}
          labelKey="input.label"
          placeholderKey="input.placeholder"
        />

        <CustomSearchBar
          value={search}
          onChangeText={setSearch}
          placeholderKey="search.placeholder"
        />

        <CustomDropdown
          options={options}
          selectedValue={selectedValue}
          onValueChange={setSelectedValue}
          placeholderKey="dropdown.placeholder"
        />

        <CustomButton
          title="Submit"
          onPress={() => console.log("Button pressed")}
        />
      </View>
    </ThemeProvider>
  );
};

export default App;
```

## Components

### ThemeProvider

Provides theming context to all components. Supports light and dark themes with custom color schemes.

```jsx
import {
  ThemeProvider,
  useAppTheme,
  lightTheme,
  darkTheme,
} from "react-native-core-kit";

// Custom theme colors
const myLightTheme = {
  ...lightTheme,
  primaryColor: "#8e44ad",
  secondaryColor: "#2ecc71",
};

const App = () => <ThemeProvider>{/* Your app content */}</ThemeProvider>;

// Access theme in components
const MyComponent = () => {
  const { theme, toggleTheme } = useAppTheme();

  return (
    <View style={{ backgroundColor: theme.background }}>
      <Text style={{ color: theme.text }}>Themed Text</Text>
      <Button onPress={() => toggleTheme(myLightTheme)}>Toggle Theme</Button>
    </View>
  );
};
```

### CustomButton

Enhanced button component with theming and internationalization support.

```jsx
import { CustomButton } from 'react-native-core-kit';

<CustomButton
  title="Regular Button"
  onPress={() => {}}
  mode="contained"
/>

<CustomButton
  titleKey="button.submit" // i18n key
  onPress={() => {}}
  disabled={false}
  loading={isLoading}
  icon="check"
  color="#3498db"
  textColor="#ffffff"
/>
```

### TextInput

Enhanced text input with theming and internationalization support.

```jsx
import { TextInput } from 'react-native-core-kit';

<TextInput
  value={text}
  onChangeText={setText}
  labelKey="input.email"
  placeholderKey="input.emailPlaceholder"
  mode="outlined"
  error={emailError}
/>

<TextInput
  value={description}
  onChangeText={setDescription}
  labelKey="input.description"
  multiline={true}
  numberOfLines={4}
  themeColor="#e74c3c"
/>

// With timezone-based placeholder
<TextInput
  value={meetingTime}
  onChangeText={setMeetingTime}
  timezone="America/New_York"
/>
```

### CustomDropdown

Flexible dropdown selector with search and multi-select capabilities.

```jsx
import { CustomDropdown } from 'react-native-core-kit';

const options = [
  { label: 'Option 1', value: 'opt1' },
  { label: 'Option 2', value: 'opt2' },
  { label: 'Option 3', value: 'opt3' },
];

// Single select dropdown
<CustomDropdown
  options={options}
  selectedValue={selectedValue}
  onValueChange={setSelectedValue}
  placeholderKey="dropdown.select"
  searchable={true}
/>

// Multi-select dropdown with custom styling
<CustomDropdown
  options={options}
  selectedValue={selectedValues}
  onValueChange={setSelectedValues}
  multiSelect={true}
  placeholderKey="dropdown.multiSelect"
  triggerStyle={{ borderRadius: 10 }}
  modalContentStyle={{ backgroundColor: '#f5f5f5' }}
/>
```

### SimpleDropdown

A lightweight dropdown alternative with customizable position and appearance.

```jsx
import { SimpleDropdown } from 'react-native-core-kit';

<SimpleDropdown
  options={options}
  selectedValue={selectedValue}
  onValueChange={setSelectedValue}
  placeholder="Select an option"
  title="Category"
  listPosition="bottom" // 'top', 'bottom', or 'middle'
  enableSearch={true}
/>

// Multi-select with custom icons
<SimpleDropdown
  options={options}
  selectedValue={multiValues}
  onValueChange={setMultiValues}
  isMultiSelect={true}
  customDropdownIcon={MyCustomIcon}
  customCheckboxSelected={MySelectedIcon}
/>
```

### CustomSearchBar

Enhanced search bar with theming and internationalization support.

```jsx
import { CustomSearchBar } from 'react-native-core-kit';

<CustomSearchBar
  value={search}
  onChangeText={setSearch}
  placeholderKey="search.products"
  onIconPress={() => performSearch(search)}
/>

// With custom icons and styling
<CustomSearchBar
  value={search}
  onChangeText={setSearch}
  icon="filter"
  themeColor="#9b59b6"
  style={{ borderRadius: 25 }}
/>
```

### Time Utilities

Utilities for working with time and timezones.

```jsx
import { getCurrentTime } from "react-native-core-kit";

// Get current time in a specific timezone
const tokyoTime = getCurrentTime("Asia/Tokyo");
console.log(`Current time in Tokyo: ${tokyoTime}`);
```

## Productivity Benefits

- **Development Speed**: Reduce development time by up to 40% with ready-to-use components
- **Consistent UI**: Maintain a consistent look and feel across your entire application
- **Internationalization Ready**: Support multiple languages without additional configuration
- **Responsive by Default**: Components adapt to different screen sizes automatically
- **Themeable**: Switch between light and dark themes or create custom themes
- **Code Reusability**: Stop reinventing common UI patterns with every project

## Contributing

We welcome contributions! Please feel free to submit a Pull Request.

## License

ISC
