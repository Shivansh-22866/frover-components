# frover-components
This repo is for Frover Components

## CustomInput Component

The CustomInput component is a reusable React component that provides a customizable input field with various validation options. It can be used for different input types, including text, password, and more.

### Props required

- `options` with the following properties
-- `type`: The type of the input field (e.g., "text", "password").
-- `value`: The current value of the input field.
-- `placeholder`: The placeholder text for the input field.
-- `pattern`: A regular expression pattern that the input value must match.
-- `includeAll?`: An array of strings that the input value must include.
-- `includeOneOf?`: An array of strings, of which the input value must include at least one.
-- `exclude?`: An array of strings that the input value must not include.
-- `passwordRequirements?`: An object that specifies the password requirements, including `requireCapitalLetter`, `requireSymbol`, and `requireNumber`.
-- `name`: The name of the input field.
-- `required`: A boolean indicating whether the input field is required.
-- `minLength?`: The minimum length of the input value.
-- `maxLength?`: The maximum length of the input value.
- `label`: Label of the input field to distinguish
- `isVisible?`: A boolean that determines whether the input field should be visible. True by default. Password is exceptional in this case, as it is the only input that can toggle isVisible via a button

### Dependencies

The CustomInput component uses the following dependencies:
- `react-icons/fa`: A library that provides the FaRegEye and FaRegEyeSlash icons.
To install react-icons:
```
npm i react react-icons
```

### Example Usage
Use options object in the `<CustomInput/>` component

```
import React, { useState } from 'react';
import CustomInput from './CustomInput';

const MyForm = () => {
  const [password, setPassword] = useState('');

  return (
    <form>
      <CustomInput
        options={{
        type: 'password' as const,
        includeAll: [] as string[],
        exclude: [],
        placeholder: 'Enter your password',
        required: true,
        minLength: 8,
        maxLength: 20,
        value: passwordValue,
        setValue: setPasswordValue,
        pattern: '^[a-zA-Z0-9!@#$%^&*]*$',
        name: 'password-input',
        passwordRequirements: {
          requireCapitalLetter: true,
          requireSymbol: true,
          requireNumber: true,
        }
        }}
        label="Password"
      />
      {/* Add more input fields as needed */}
    </form>
  );
};

export default MyForm;
```

## CustomCard Component

The CustomCard component is a reusable React component that displays a card with optional features such as an image, title, content, time, unread message count, and an active indicator. It also includes a ripple effect animation upon clicking the card.

### Props required

- `title`: The title of the card.
- `content`: The content or description displayed on the card.
- `imageSrc`: The URL or path to the image displayed on the card.
- `time`: The timestamp or time-related information associated with the card.
- `unreadMessages` (optional): The number of unread messages, displayed as a badge on the card.
- `isActive` (optional): A boolean indicating whether the card is active, typically denoted by a visual indicator like a colored dot.

### Dependencies

The SubmitButton component utilizes Material-UI's `Button` and `CircularProgress` components.
To install Material-UI, use the following command:
```
npm install @mui/material
```

### Example Usage

```
import React, { useState } from 'react';
import SubmitButton from './SubmitButton';

const MyForm = () => {
  const [isLoading, setIsLoading] = useState(false);

  const handleClick = () => {
    setIsLoading(true);
    // Simulate an async operation
    setTimeout(() => {
      setIsLoading(false);
    }, 2000);
  };

  return (
    <form onSubmit={(e) => { e.preventDefault(); }}>
      <SubmitButton
        isLoading={isLoading}
        onClick={handleClick}
        backgroundColor="#2196f3"
        rippleColor="#64b5f6"
        textColor="white"
      >
        Submit
      </SubmitButton>
    </form>
  );
};

export default MyForm;

```
### Notes
- The button supports a loading state (`isLoading`) with a CircularProgress spinner displayed when active.
- It disables clicks (`onClick`) and adjusts styling based on the loading state.
- The `backgroundColor`, `rippleColor`, and `textColor` props allow customization of the button's appearance and interaction states. Adjust these props as per your design requirements.


## SubmitButton Component

The SubmitButton component is a reusable React component that provides a customizable button with loading state and ripple effect. It integrates Material-UI's Button and CircularProgress components to handle asynchronous actions elegantly.

### Props required

- `isLoading` with the following properties
- `onClick`: Label of the input field to distinguish
- `children`: The content to be displayed inside the button.
- `backgroundColor`: The background color of the button.
- `rippleColor`: The color of the ripple effect when hovering over the button.
- `textColor`: The color of the text inside the button.

### Dependencies

The SubmitButton component utilizes Material-UI's `Button` and `CircularProgress` components.
To install Material-UI, use the following command:
```
npm install @mui/material
```

### Example Usage

```
import React from 'react';
import CustomCard from './CustomCard';

const App = () => {
  return (
    <div>
      <CustomCard
        title="Sample Card Title"
        content="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam eget efficitur mauris."
        imageSrc="https://example.com/image.jpg"
        time="2 hours ago"
        unreadMessages={3}
        isActive={true}
      />
    </div>
  );
};

export default App;

```
### Notes
- Ensure that the required props (`title`, `content`, `imageSrc`, `time`) are provided to render the card correctly.
- Customize the `isActive` prop to show active state indicators as needed.
- The ripple effect animation enhances user interaction by providing visual feedback on click events.
