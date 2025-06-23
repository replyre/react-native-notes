## 📚 React Native Stack Navigation Notes

### 🧭 What is Stack Navigation?

Stack Navigation allows users to navigate between different screens in a way that mimics a call stack – pushing a new screen on top and popping it off when navigating back.

---

### 📦 Required Packages

Install the core navigation libraries:

```bash
npm install @react-navigation/native @react-navigation/stack react-native-screens react-native-safe-area-context react-native-gesture-handler react-native-reanimated react-native-vector-icons
```

For iOS (if not using Expo):

```bash
cd ios && pod install && cd ..
```

---

### 🧱 Folder Structure (Example)

```
/project-root
  /screens
    Home.js
    Profile.js
  App.js
  index.js
```

---

### 🛠️ Basic Setup (index.js)

```js
import 'react-native-gesture-handler'; // Must be at the top
import { AppRegistry } from 'react-native';
import App from './App';
import { name as appName } from './app.json';

AppRegistry.registerComponent(appName, () => App);
```

---

### 📄 App.js - Stack Navigation Setup

```js
import React from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';
import Home from './screens/Home';
import Profile from './screens/Profile';

const Stack = createStackNavigator();

const App = () => {
  return (
    <NavigationContainer>
      <Stack.Navigator initialRouteName="Home">
        <Stack.Screen name="Home" component={Home} />
        <Stack.Screen name="Profile" component={Profile} />
      </Stack.Navigator>
    </NavigationContainer>
  );
};

export default App;
```

---

### 🧭 Key Stack.Navigator Props

| Prop               | Description                                         |
| ------------------ | --------------------------------------------------- |
| `initialRouteName` | First screen to load in the stack                   |
| `screenOptions`    | Default styles/settings for all screens             |
| `headerMode`       | Show or hide the header (`screen`, `float`, `none`) |

---

### 🧾 Stack.Screen Props

| Prop        | Description                             |
| ----------- | --------------------------------------- |
| `name`      | Unique identifier for the screen        |
| `component` | The screen component                    |
| `options`   | Customize header, title, gestures, etc. |

Example:

```js
<Stack.Screen 
  name="Profile" 
  component={Profile} 
  options={{ title: 'User Profile', headerShown: false }} 
/>
```

---

### 🧭 Navigation Methods

Use the `navigation` prop to move between screens:

```js
// Navigate to Profile
navigation.navigate('Profile');

// Go back
navigation.goBack();
```

---

### 💡 Passing Data Between Screens

**From Home.js:**

```js
navigation.navigate('Profile', { userId: 42 });
```

**In Profile.js:**

```js
const route = useRoute();
console.log(route.params.userId);
```

---

### 🎨 Styling the Header

Customize with `screenOptions` or per screen:

```js
<Stack.Navigator
  screenOptions={{
    headerStyle: { backgroundColor: 'tomato' },
    headerTintColor: '#fff',
    headerTitleStyle: { fontWeight: 'bold' },
  }}
>
```

---

### ⚙️ Common Header Options

| Option             | Purpose                             |
| ------------------ | ----------------------------------- |
| `headerShown`      | Show/hide header                    |
| `title`            | Set title of the header             |
| `headerStyle`      | Change header background            |
| `headerTintColor`  | Change color of back arrow and text |
| `headerTitleStyle` | Style the header title text         |

---

### 📦 Nesting Stack Navigators

You can nest Stack Navigators inside Tab or Drawer Navigators and vice versa.

Example:

```js
<Tab.Navigator>
  <Tab.Screen name="HomeTab" component={HomeStackScreen} />
</Tab.Navigator>
```

---

### 🧪 Testing Navigation

Use `navigation.navigate()` and `console.log` to test transitions. Use the dev menu to enable hot reloading for faster development.

---

### 🧼 Common Errors and Fixes

| Error Message                                                  | Fix                                                           |
| -------------------------------------------------------------- | ------------------------------------------------------------- |
| `RNGestureHandlerModule not found`                             | Ensure `react-native-gesture-handler` is installed and linked |
| `TypeError: undefined is not a function (navigation.navigate)` | Ensure screen is inside a `Stack.Navigator`                   |
| Screens don't render                                           | Wrap everything inside `<NavigationContainer>`                |

---

### 📝 Summary

* ✅ Install dependencies
* ✅ Import and use `NavigationContainer` and `createStackNavigator`
* ✅ Define screens inside `Stack.Navigator`
* ✅ Use `navigation.navigate()` and `goBack()` for routing
* ✅ Customize headers and pass data easily
