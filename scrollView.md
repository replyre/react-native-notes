## 📜 React Native: `ScrollView` – Complete Notes

---

### 🧠 What is `ScrollView`?

* `ScrollView` is a core component used to make **content scrollable** vertically or horizontally.
* It can contain **multiple child components** and renders all of them at once.
* It’s suitable for **small to medium content** that may not fit the screen.

---

### 📦 Basic Usage

```jsx
import { ScrollView, Text, View } from 'react-native';

const App = () => {
  return (
    <ScrollView style={{ padding: 20 }}>
      <Text>Item 1</Text>
      <Text>Item 2</Text>
      {/* Add many more items here */}
    </ScrollView>
  );
};
```

---

### 📐 Scroll Direction

#### ✅ Vertical Scroll (default)

```jsx
<ScrollView>
  {/* Content goes here */}
</ScrollView>
```

#### ✅ Horizontal Scroll

```jsx
<ScrollView horizontal={true}>
  {/* Content goes side by side */}
</ScrollView>
```

---

### ⚙️ Common Props

| Prop                             | Description                                   |
| -------------------------------- | --------------------------------------------- |
| `horizontal`                     | Makes the scroll horizontal                   |
| `showsVerticalScrollIndicator`   | Show/hide vertical scrollbar (`true`/`false`) |
| `showsHorizontalScrollIndicator` | Show/hide horizontal scrollbar                |
| `contentContainerStyle`          | Style for the inner container                 |
| `onScroll`                       | Event called while scrolling                  |
| `refreshControl`                 | Used for pull-to-refresh functionality        |
| `keyboardShouldPersistTaps`      | Control keyboard dismissal on tap             |

---

### 🎯 Example with Vertical Scroll and Styling

```jsx
import { ScrollView, Text, StyleSheet, View } from 'react-native';

const App = () => {
  return (
    <ScrollView style={styles.scrollContainer} contentContainerStyle={styles.content}>
      {Array.from({ length: 20 }, (_, i) => (
        <View key={i} style={styles.box}>
          <Text style={styles.text}>Item {i + 1}</Text>
        </View>
      ))}
    </ScrollView>
  );
};

const styles = StyleSheet.create({
  scrollContainer: {
    backgroundColor: '#fff',
  },
  content: {
    padding: 20,
  },
  box: {
    backgroundColor: '#f2f2f2',
    padding: 20,
    marginBottom: 10,
    borderRadius: 10,
  },
  text: {
    fontSize: 18,
  },
});
```

---

### 🔄 Pull to Refresh Example

```jsx
import { ScrollView, RefreshControl } from 'react-native';
import React, { useState } from 'react';

const App = () => {
  const [refreshing, setRefreshing] = useState(false);

  const onRefresh = () => {
    setRefreshing(true);
    setTimeout(() => setRefreshing(false), 2000);
  };

  return (
    <ScrollView
      refreshControl={
        <RefreshControl refreshing={refreshing} onRefresh={onRefresh} />
      }
    >
      {/* Scrollable content */}
    </ScrollView>
  );
};
```

---

### ⚠️ Notes

* `ScrollView` **renders all items at once**, which can affect performance for large lists.
* For large lists, prefer **`FlatList`** or **`SectionList`**, which support lazy loading and better performance.
