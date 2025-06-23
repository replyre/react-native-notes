## 🚀 React Native Tab Navigation – Complete Notes

---

### 📦 1. **What is Tab Navigation?**

Tab Navigation lets users switch between screens using a **bottom tab bar** (like Instagram, WhatsApp, etc.). It's commonly implemented using the **React Navigation** library.

---

### 📥 2. **Installation Steps**

Install required packages:

```bash
npm install @react-navigation/native
npx expo install react-native-screens react-native-safe-area-context
npm install @react-navigation/bottom-tabs react-native-vector-icons react-native-gesture-handler react-native-reanimated
```

Also, make sure this is wrapped in the root of your app:

```jsx
import { NavigationContainer } from '@react-navigation/native';

<NavigationContainer>
  {/* Navigator goes here */}
</NavigationContainer>
```

---

### 🧱 3. **Basic Tab Navigator Structure**

```jsx
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
import HomeScreen from './screens/HomeScreen';
import ProfileScreen from './screens/ProfileScreen';

const Tab = createBottomTabNavigator();

function MyTabs() {
  return (
    <Tab.Navigator>
      <Tab.Screen name="Home" component={HomeScreen} />
      <Tab.Screen name="Profile" component={ProfileScreen} />
    </Tab.Navigator>
  );
}
```

---

### 🎨 4. **Adding Icons to Tabs**

To use icons (commonly with `react-native-vector-icons`):

```jsx
import Icon from 'react-native-vector-icons/Ionicons';

<Tab.Navigator
  screenOptions={({ route }) => ({
    tabBarIcon: ({ focused, color, size }) => {
      let iconName;

      if (route.name === 'Home') {
        iconName = focused ? 'home' : 'home-outline';
      } else if (route.name === 'Profile') {
        iconName = focused ? 'person' : 'person-outline';
      }

      return <Icon name={iconName} size={size} color={color} />;
    },
    tabBarActiveTintColor: 'tomato',
    tabBarInactiveTintColor: 'gray',
  })}
>
  <Tab.Screen name="Home" component={HomeScreen} />
  <Tab.Screen name="Profile" component={ProfileScreen} />
</Tab.Navigator>
```

✅ You can use other icon sets like:

* `Ionicons`
* `MaterialIcons`
* `FontAwesome`
* `Feather`

> Make sure the corresponding icon set is linked or installed in Expo.

---

### ⚙️ 5. **Customizing Tab Bar Appearance**

```js
tabBarOptions={{
  showLabel: false, // Hide tab labels
  style: {
    backgroundColor: '#000',
    borderTopWidth: 0,
    height: 60,
  },
}}
```

> Use `screenOptions` in latest versions instead of `tabBarOptions`.

---

### 🧩 6. **Hiding Tab Bar on Specific Screens**

```jsx
<Tab.Screen
  name="Profile"
  component={ProfileScreen}
  options={{ tabBarStyle: { display: 'none' } }}
/>
```

---

### 🧭 7. **Full Example**

```jsx
import React from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
import Icon from 'react-native-vector-icons/Ionicons';
import HomeScreen from './screens/HomeScreen';
import ProfileScreen from './screens/ProfileScreen';

const Tab = createBottomTabNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Tab.Navigator
        screenOptions={({ route }) => ({
          headerShown: false,
          tabBarIcon: ({ focused, color, size }) => {
            let iconName;

            if (route.name === 'Home') {
              iconName = focused ? 'home' : 'home-outline';
            } else if (route.name === 'Profile') {
              iconName = focused ? 'person' : 'person-outline';
            }

            return <Icon name={iconName} size={size} color={color} />;
          },
          tabBarActiveTintColor: 'tomato',
          tabBarInactiveTintColor: 'gray',
        })}
      >
        <Tab.Screen name="Home" component={HomeScreen} />
        <Tab.Screen name="Profile" component={ProfileScreen} />
      </Tab.Navigator>
    </NavigationContainer>
  );
}
```

---

### 🧠 Notes

* You must wrap the navigator inside `NavigationContainer`.
* Use `screenOptions` to customize tabs globally.
* Use `tabBarIcon` to return any icon component.
* Icons change based on `focused` state (active/inactive).
* Always give `name` prop properly to match routing logic.
