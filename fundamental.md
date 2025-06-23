## 📘 React Native Fundamentals – Personal Notes

---

### 🛠️ 1. **Core Imports**

```js
import {
  StyleSheet,
  SafeAreaView,
  Text,
  View,
  Image,
  Button,
  TouchableOpacity,
  Alert,
  Pressable
} from 'react-native';
import React from 'react';
```

* **SafeAreaView**: Keeps UI inside safe bounds (notches, status bar, etc.)
* **Text**: Used for displaying any string/text.
* **Image**: For rendering images.
* **Button**: Simple clickable button with a title.
* **TouchableOpacity**: For custom buttons with visual feedback on press.
* **Pressable**: Like Touchable but gives more flexibility.
* **Alert**: Built-in pop-up for messages or prompts.

---

### 🧩 2. **React Native Component Structure**

```js
const App = () => {
  return (
    <SafeAreaView style={{ padding: 20, flex: 1, backgroundColor: 'white' }}>
      {/* Components go here */}
    </SafeAreaView>
  );
};

export default App;
```

* Everything is placed inside `SafeAreaView`.
* We use `return()` to define the UI inside JSX.
* The component is exported at the end.

---

### 🎨 3. **Basic UI Components Used**

#### ✅ **Text Component**

```js
<Text>Hello Bhai</Text>
```

#### ✅ **Image Component**

```js
<Image src="..." height={200} width={200} />
```

#### ✅ **Button**

```js
<Button
  title="Click Me"
  onPress={() => {
    Alert.alert("Button Pressed", "You pressed the button!");
  }}
/>
```

#### ✅ **TouchableOpacity**

```js
<TouchableOpacity>
  <Text style={{ width: "100%", height: "30px", backgroundColor: "red" }}>Button</Text>
</TouchableOpacity>
```

#### ✅ **Pressable**

```js
<Pressable>
  <Text
    style={{ width: "100%", height: "30px", backgroundColor: "blue" }}
    onPress={() => {
      Alert.alert("hello");
    }}
  >
    Pressable
  </Text>
</Pressable>
```

---

### 🧠 4. **Key Learnings**

* All components in React Native must be **imported** from `react-native`.
* **Style** can be written inline or via `StyleSheet.create({})`.
* `onPress` is the most used interaction handler (like `onClick` in web).
* React Native components don’t use HTML — no `<div>`, `<h1>`, etc.
* Dimensions in styles are **numbers**, not strings (no `px`).

---

### 🧱 5. **Structure of a Custom Component**

```js
const styles = StyleSheet.create({
  example: {
    backgroundColor: 'blue',
    height: 50,
    width: 100,
  }
});
```

Use `StyleSheet` for organized and performant styling.

---

### 📌 6. **Alerts for Notifications**

```js
Alert.alert("Title", "Message to show");
```

Used to show simple pop-ups or notifications.

---

### 📄 7. **Component Export**

```js
export default App;
```

Always export your main component to run the app.

