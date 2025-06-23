## 🎨 React Native Styling Notes (CSS Equivalent)

---

### 📌 1. **What is Styling in React Native?**

React Native does not use traditional CSS. Instead, it uses **JavaScript objects** to style components. These styles are **similar to CSS** but follow camelCase naming instead of kebab-case.

Example:

```js
background-color → backgroundColor  
font-size → fontSize
```

---

### 🧱 2. **Styling Methods in React Native**

#### ✅ **Inline Styling**

```js
<Text style={{ color: 'red', fontSize: 20 }}>Hello</Text>
```

#### ✅ **Using `StyleSheet.create()`**

```js
const styles = StyleSheet.create({
  title: {
    color: 'red',
    fontSize: 20,
  },
});

<Text style={styles.title}>Hello</Text>
```

✅ Recommended for performance and readability.

---

### 🎯 3. **Main Style Properties in React Native**

#### 📐 Layout & Flexbox

| Property         | Description                                           |
| ---------------- | ----------------------------------------------------- |
| `flex`           | Defines how a component grows/shrinks.                |
| `flexDirection`  | Row or column layout. (`'row'`, `'column'`)           |
| `justifyContent` | Align children vertically (or horizontally if `row`). |
| `alignItems`     | Align children horizontally (or vertically if `row`). |
| `alignSelf`      | Override alignment for a specific child.              |

Example:

```js
container: {
  flex: 1,
  flexDirection: 'row',
  justifyContent: 'space-between',
  alignItems: 'center',
}
```

---

#### 📏 Dimensions

| Property    | Description          |
| ----------- | -------------------- |
| `width`     | Set component width  |
| `height`    | Set component height |
| `minWidth`  | Minimum width        |
| `maxHeight` | Maximum height       |

```js
box: {
  width: 100,
  height: 100,
}
```

---

#### 🎨 Colors & Backgrounds

| Property          | Description      |
| ----------------- | ---------------- |
| `backgroundColor` | Background color |
| `color`           | Text color       |
| `opacity`         | Opacity (0 to 1) |

---

#### 🖋️ Typography

| Property             | Description                                          |
| -------------------- | ---------------------------------------------------- |
| `fontSize`           | Size of the text                                     |
| `fontWeight`         | Weight like `'bold'`, `'normal'`, `'100'` to `'900'` |
| `fontStyle`          | `'normal'` or `'italic'`                             |
| `textAlign`          | `'left'`, `'right'`, `'center'`                      |
| `textDecorationLine` | `'underline'`, `'line-through'`                      |

```js
text: {
  fontSize: 18,
  fontWeight: 'bold',
  textAlign: 'center',
}
```

---

#### 🧱 Borders & Radius

| Property       | Description             |
| -------------- | ----------------------- |
| `borderWidth`  | Thickness of the border |
| `borderColor`  | Border color            |
| `borderRadius` | Round corners           |

```js
box: {
  borderWidth: 2,
  borderColor: 'black',
  borderRadius: 10,
}
```

---

#### 📦 Padding & Margin

| Property            | Description        |
| ------------------- | ------------------ |
| `padding`           | Inside space       |
| `margin`            | Outside space      |
| `paddingHorizontal` | Horizontal padding |
| `marginVertical`    | Vertical margin    |

```js
container: {
  padding: 10,
  margin: 20,
}
```

---

#### 🔄 Positioning

| Property                         | Description                            |
| -------------------------------- | -------------------------------------- |
| `position`                       | `'relative'` (default) or `'absolute'` |
| `top`, `left`, `right`, `bottom` | Positioning values                     |
| `zIndex`                         | Stack order                            |

```js
absoluteBox: {
  position: 'absolute',
  top: 50,
  left: 30,
}
```

---

### ✅ 4. **Responsive Units in React Native**

* No `px`, `%`, `em`, etc.
* Only **numbers** are used (they act like `dp` in Android).
* `%` is only supported in limited layout properties like `width: '100%'`.

---

### 🧪 5. **Style Inheritance**

* Unlike HTML, styles do **not inherit** automatically.
* Always explicitly define styles for each component.

---

### 🔄 6. **Combining Styles**

```js
<Text style={[styles.title, { color: 'blue' }]} />
```

* Combines multiple style objects; later ones override earlier ones.

---

### 🧰 7. **Example: Full Component Styling**

```js
import { StyleSheet, Text, View } from 'react-native';

const App = () => {
  return (
    <View style={styles.container}>
      <Text style={styles.heading}>React Native Styling</Text>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#f2f2f2',
  },
  heading: {
    fontSize: 24,
    fontWeight: 'bold',
    color: 'purple',
  },
});
```
- Js object loads evertime the componet renders
-  StyleSheet object loads only once when the component mounts -
-  Static CSS
- Dynamic styles are in line CSS
