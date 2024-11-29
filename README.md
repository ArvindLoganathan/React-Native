# React-Native

React native is an open source framework by META for building cross plateform app.
<br>

Expo is also open source framenwork maintained by expo for building bundles/(support for device testing) for cross plateform apps using React Native. Provide streamlined experiance for initaila developer to set up project easily.
<br>

Expo quick start(expo manages)  vs REact Native CLI quickstart(we need to manage like android studio).
<br>

## **using EXPO**
<br>

1. npx create-expo-app@latest my-demo-app
2. npx expo start

<br>
-----------

For Template:
npx react-native init MyNewProject --template react-native-template-blank
cd MyNewProject
npx react-native run-android    # For Android
npx react-native run-ios        # For iOS (macOS only)

<br>
-----------

## **Core Compoennt:**

Equalent tag Below:

react native    | Andriod       |       IOS          |   web
<View>          | <ViewGroup>   |   <UIView>         |  <div>
<Text>          | <TextView>    |   <UITextView>     |  <p>
<Image>         | <ImageView>   |   <UIImageView>    |  <img>
<ScrollView>    | <ScrollView>  |   <UIScrollView>   |  <div>
<TextInput>     | <EditText>    |   <UITextField>    |  <input type="text">

<br>
-----------

## **View**

1. act as layout using flexbox.
2. view takes the place only when it has felx: 1 (takes entire view port available)
<view style={{flex: 1}}> </view> 

<br>
-----------

## **Text**

1. all the text need to be warpped by <Text>hello <Text style={{color: "red" }}>World</Text></Text> 

<br>
-----------

## **Image**
const img=require("@./assert/1.png");

<Image
    source={img}
    <!-- source={{uri:"https://img1.com"}} convert byte to image we are using uri object  -->
    style={{
    width:"100px",
    height:"100px"
    }}
/>

Image as backGround
<ImageBackground source={img}>
    <Text>Hello world</Text>
</ImageBackground>
<br>
-----------

## **ScrollView**

when  text or particular view is  too large, there we need to wrap Scrollview to add scrollbar in android and ios. 
<br>it provide plateform specific scroll 

<br>
-----------

## **Button**

button is different in different platform.

<Button title="continue" onPress={() => console.log("clicked")} disabled/>
-----------

<br>

## **Pressable**

to make component as pressable to add onPress function.
used to build custom button component for all env.

Events:
1. onPressIn(press activated)
2. onPress(after onPressIn then onPress is called)
3. onLongPress(press is activated for 500ms)
4. onPressOut(after hand out)

-----------

<br>

## **Modal**

1. by default modal is always visible
2. use state to handle visibility
3. onRequestClose is called on user click on back button on mobile


const [showModal,setShowModal] = useState(false)

<Modal
    visible={showModal}
    onRequestClose={()=> setShowModal(false)} // click on backbutton on mobile
    animationType="slide"  // none(default when none is set),slide(from bottom),fade(transition)
    presentationStyle="pageSheet" // pageSheet or formsheet or fullscreen(wider) // only for IOS not for Andriod
>
    <View style={{flex: 1}} > 
        <Text>HI Modal</Text>
        <Botton onPress={()=> setShowModal(false)}>close</Botton>
    </View>
</Modal>

-----------
<br>

## **StatusBar**

show native status like battery status , current time,wifi network etc

we can only chnage the text color in ios in andriod we can change background color and text color. we can hide status bar in both os.

<StatusBar 
    backgroundColor = "lightgreen" // to update background only apply ti android
    barStyle="default" // light-content to update color 
    hidden // to hide statusbar
/>

<br>
to fix padding top issue with notch we can use status bar height .
<br>

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    paddingTop: StatusBar.currentHeight
  },
});

<br>

-----------
<br>

## **ActivityIndicator**

loading indicator

<ActivityIndicator 
    size = "large" //small 
    color= "midnightblue"
    animating={true} if false indicator will not be shown use state variable to toggle
/>

-----------
<br>

## **Alert**

to show alert dialog to user with ok button
1. first argument is title 
2. second argument is message
3. third argument is for button and functionality for that buttons array
<br>
<Button 
onPress= {()=>Alert.alert("invaid req")} 
/>
<br>

<Button 
onPress= {()=>Alert.alert("invaid req","DOB is invalid")}
/>
<br>
<Button 
onPress= {()=>
Alert.alert("invaid req", "DOB is invalid",[
    {text: "Cancel",onPress:()}
])}
/>
<br>
-----------
<br>

## **Styling**
<br>

1. inline style - style={{flex: 1}} <br>
2. react native stylesheet - 
<br>

example 1:
<View style={styles.container}><Text> hello </Text></View>
<br>

example of multiple style: **to apply multiple style wrap with Array and array of last get high priority on same priority level**
<br>

```React
<View style={styles.container}>
    <View style={[styles.box,styles.titlered]}>
        <Text> hello </Text>
    </View>
     <View style={[styles.box,styles.titleblue]}>
        <Text> hello </Text>
    </View>
</View>
export const styles= StyleSheet.create({
    container:{
        flex: 1
    },
    box:{
        width: 100px,
        height: 100px
    },
    titlered:{
        color: "red"
    },
    titleblue:{
        color: "blue"
    }
}) 
```

<br>

## **Box Modal**

<br>
simialr to web (margin,border,padding,content)
<br>

**padding & Margin**
padding: 10 // both x & y <br>
paddingHorizontal: 10 // x <br>
paddingVertical: 10 // y <br>
marginLeft: 10 // left similar to other sides <br>
<br>

**border always apply to view** <br>

border bit differnt from web we need to set explicilty everything.

borderWidth: 2 <br>
borderColor: blue <br>
borderRadius: blue <br> **border radius apply to view in ios & android but in text component it applies only to android not in IOS**
borderStyle: 'dashed' <br>
<br>

**Box Shadow** <br>


## works only in IOS
shadowColor: red // work in both android & ios
shadowOffset:{
    width: 5,
    height: 5
}
shadowOpacity: 0.6
shadowRadius:4

## Android need to use elevation property
elevation: 10 // to work box shadow in android

## **style inheritance**
There is no css inheritance in react native(if we apply color property to parent div. all child element will apply same color property which is not present in react native)

we need to apply color property to <Text> tag specifically. Apply to parent <View> tag will not inherite to child <Text>. Inhertaince support within <Text> Hello <Text> world</Text></Text>

<br>

**Layout=>Flexbox**
<br>

we can arrange flex item in horizontal/vertical to the flex container .
<br>

1. main axis(**in React Native, top to bottom**)(in web left to right)<br>
2. cross axis(**in React Native,left to right**)(in top to bottom)<br>

<b>default view is flex but if don't have any childers then no space.<b><br>
<b>flex: 1 takes all available space </b><br>
<b>flexDirection is column by default</b>values are column,column-reverse,row,row-reverse<br>
<b>alignSelf on item is value to auto, it inherits from parent alignItem which has default streach value.</b>
<b>flex: wrap to prevent overflow the container. mowrap,wrap-reverse</b>
<b>alignContent align content from left to right initial vaue is flex-start.center,flex-end,stretch,space-between,space-around</b>
<b>gap provide gap between item.rowGap provide row gap . columGap to provide gap between column</b>
<b>flexBasis: 140 provide inital height for flex item when there is available height. when pareten container is flex: column when flex : row it add height</b>
<b>flexShrink default 0 so so wheinking when overfloe the with of the item. by setting shrink to 2 it shrink twice as other</b>
<b>flexGrow: grow relatove to other item, default is 0.when set 1 to takes avaulable space if its 2 then takes 2 times of space based on availale space.
when flex: 1 is equikant to flexGrow:1 , flexShrink:1 ,flexBasis: 0
</b>
<br>

## **Relative and Absolute Layout**

1. Releative (normal flow,ofset like left,right,top can be uesd to contorl within releative parent)
2. Absolute (independ of its sibiling controlled by relative to parent )
<br>

## Dynamic Interfaces

Dyanmic intercae are mandatory to accomodate landscap & portrate mdoe. even device size changes ios 11 & 14. similrly android.
<br>
adding percent width and height solve most problem still we have dimension api to solve as perfect fit.
<br>

const {width,height}=Dimentions.get("window") // screen(enitre area include notches) or window(visibile area)

make use of width and height to create sytlesheet width: width>500 ? "70%" : "90%"


<b>Not recomended approach during landscape mode there might be some width & height issue sd its not calculated everytime like responsive need hard refresh.
we can use state variable and recalclute using useeffect.

```React

  const [windowDimensions, setWindowDimensions] = useState({
    width: Dimensions.get('window').width,
    height: Dimensions.get('window').height,
  });

  useEffect(() => {
    // Function to update the dimensions when the screen size changes
    const onChange = ({ window }) => {
      setWindowDimensions({
        width: window.width,
        height: window.height,
      });
    };

    // Add event listener for dimension change
    Dimensions.addEventListener('change', onChange);

    // Cleanup event listener on component unmount
    return () => {
      Dimensions.removeEventListener('change', onChange);
    };
  }, []);


```

or

using useWindowDimentions is direct approach and recommended.

```
import { useWindowDimentions } from "React-Native"
const width = useWindowDimentions().width;
const height = useWindowDimentions().height;

```


</b>

<br>

## **SafeAreaVIew**

few text is hidden below the notch, inprder to avoid we need to use wrap this .

we need to add bacgroundColor to this along with flex:1 to look better.

<br>

## **Plateform specific code**

cross plateform app required maximum code reuseablility.we also need to wriet few plateform specific code.

1. plateform module
2. plateform specific file extension


<b>plateform module </b>

make use of  Platform.select or Platform.OS === 'ios'

```
import { View, Text, Platform } from 'react-native';

const PlatformSpecificComponent = () => {
  return (
    <View>
      {Platform.OS === 'ios' ? (
        <Text>This is iOS specific text</Text>
      ) : (
        <Text>This is Android specific text</Text>
      )}
    </View>
  );
};


or 

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
  },
  text: Platform.select({
    ios: { fontSize: 20, color: 'blue' },
    android: { fontSize: 18, color: 'green' },
    default: { fontSize: 16, color: 'black' },
  }),
});

or

import { Platform, Image } from 'react-native';

const Logo = () => {
  const logoSource = Platform.select({
    ios: require('./assets/logo.ios.png'),
    android: require('./assets/logo.android.png'),
  });

  return <Image source={logoSource} />;
};

```

<b>plateform specific file extension </b>

use:

1. Component.ios.js
2. Component.android.js 

<br>


## **LIST**

handling list is similar to map in js.
when large record performance is the issue inorder to solve this we have flatlist 

## **flatlist**

fetch few item item into memory fetch next record when scroll is done.
<br>

``` React
    <FlatList
    data={data}
    renderItem={({ item }) => (
        <View style={styles.item}>
        <Text style={styles.title}>{item.title}</Text>
        </View>
    )}
    keyExtractor={(item) => item.id}
    refreshing={refreshing}
    onRefresh={handleRefresh} //pull-to-refresh
    onEndReached={handleLoadMore}
    onEndReachedThreshold={0.1} // Trigger when the user reaches 90% of the list
    ListHeaderComponent={() =><View><Text>Header starts</Text></View>}
    ListFooterComponent={() => loading ? <Text>Loading...</Text> : null} // we can display static footer also
    ItemSeparatorComponent={<View style={{height: 16}}></View>} // Item separator adding height between list as sepeator
    ListEmptyComponent={<Text style={styles.norecord}>No record</Text>}
    />

```
<br>

## **SectionList**

used to provide section heading  before list.

<br>

``` React
const DATA = [
  {
    title: 'Fruits',  // Section header
    data: ['Apple', 'Banana', 'Orange'],  // Items in this section
  },
  {
    title: 'Vegetables',  // Section header
    data: ['Carrot', 'Tomato', 'Cucumber'],
  },
  {
    title: 'Dairy',  // Section header
    data: ['Milk', 'Cheese', 'Butter'],
  },
];

<SectionList
        sections={DATA}  // Array of sections
        renderItem={({ item }) => (
          <View style={styles.item}>
            <Text style={styles.itemText}>{item}</Text>
          </View>
        )}
        renderSectionHeader={({ section }) => (
          <View style={styles.header}>
            <Text style={styles.headerText}>{section.title}</Text>
          </View>
        )}
        keyExtractor={(item, index) => item + index}  // Key extractor for each item
      />

```
<br>

## **TextInput & Switch**
<br>

```
const App = () => {
  // State variables to manage TextInput and Switch values
  const [text, setText] = useState('');
  const [isSwitchOn, setIsSwitchOn] = useState(false);

  // Handle the change for the TextInput
  const handleTextChange = (inputText) => {
    setText(inputText);
  };

  // Handle the toggle for the Switch
  const toggleSwitch = () => {
    setIsSwitchOn(previousState => !previousState);
  };

  return (
    <View style={styles.container}>
      {/* TextInput */}
      <TextInput
        style={styles.input}
        value={text}
        onChangeText={handleTextChange}
        placeholder="Type something..."
        secureTextEntry // to make astrik for password
        keyboardType="num" // numeric there are differnttype
        autoCorrect={false}
        autoCapitalize="none"
        multiline // to add multiline we need to set min height to textinput 
      />
      
      {/* Display the current text */}
      <Text style={styles.text}>You typed: {text}</Text>

      {/* Switch */}
      <View style={styles.switchContainer}>
        <Text>Is the switch ON?</Text>
        <Switch
          value={isSwitchOn}
          onValueChange={toggleSwitch}
          thumbColor={isSwitchOn ? "#f5dd4b" : "#f4f3f4"}
          trackColor={{ false: "#767577", true: "#81b0ff" }}
        />
      </View>

      {/* Display the switch state */}
      <Text style={styles.text}>
        Switch is {isSwitchOn ? 'ON' : 'OFF'}
      </Text>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    padding: 20,
    backgroundColor: '#f0f0f0',
  },
  input: {
    width: '100%',
    height: 40,
    borderColor: '#ccc',
    borderWidth: 1,
    borderRadius: 5,
    paddingLeft: 10,
    marginBottom: 20,
    textAlignVertical: "top" // android text start at center but ios at lop for multiline
  },
  switchContainer: {
    flexDirection: 'row',
    alignItems: 'center',
    marginBottom: 20,
  },
  text: {
    fontSize: 16,
    color: '#333',
  },
});

```
<br>

## **keyBoardAvoidView**

to push form/textinput to top when keyboard open for input. we need to wrap the contanier where behaviour is paddingf for ios & height for andriod. we can also use **keyBoardVerticalOffset={Platform.OS==='ios'?100:0}** to move view 100px for keyboard

 <KeyboardAvoidingView
      style={styles.container}
      behavior={Platform.OS === 'ios' ? 'padding' : 'height'} // Adjust for iOS and Android
    >

      <ScrollView contentContainerStyle={styles.scrollContainer}>
        <Text style={styles.title}>Login</Text>
        
        <TextInput
          style={styles.input}
          placeholder="Enter your email"
          value={text}
          onChangeText={handleTextChange}
        />
        
        <TextInput
          style={styles.input}
          placeholder="Enter your password"
          secureTextEntry
        />

        <Button title="Submit" onPress={() => alert('Form Submitted')} />
      </ScrollView>
    </KeyboardAvoidingView>

<br>

## **Navigation**

we can use react navigation library or expo build in routing feature
<br>
types of navigation:

1. stack(screen is placed on top of it)
2. Drawer(open and close gesture)
3. tab(bottom of screen)

<br>
<br>

