# React Native Pin Code UI

## Installation
```sh
npm install react-native-pin-code-ui --save
```

## Usage

### Example
```js
import React, {Component} from 'react';
import {Platform, StyleSheet, Text, View,TouchableOpacity,Alert} from 'react-native';

import Pin from './Pin'

const instructions = Platform.select({
  ios: 'Press Cmd+R to reload,\n' + 'Cmd+D or shake for dev menu',
  android:
    'Double tap R on your keyboard to reload,\n' +
    'Shake or press menu button for dev menu',
});

type Props = {};

export default class App extends Component<Props> {
  state = {buttonDisabled:true,pin:''}

  async checkPin(){

    if (this.state.pin == '1234'){
      Alert.alert('Right Pin')
    }else{
      Alert.alert('Wrong Pin')
    }
    this.refs.pin.reset()
    
}

  render() {
    return (
      <View style={styles.container}>
        <Pin
            ref="pin" 
            onChangeValue={(value)=>{this.setState({pin:value})}} 
            onChangeStatus={(status)=>{this.setState({buttonDisabled:!status})}} 
            styleEmptyBox={{borderColor:'#ff0000'}}
            styleFullBox={{borderColor:'#00ff00'}}
            styleText={{fontSize:16}}
            styleButton={{backgroundColor:'#4b4648'}}
        />
        <View style={{justifyContent:'center'}}>
          <TouchableOpacity 
          onPress={()=>{
            this.checkPin()
          }}
          disabled={this.state.buttonDisabled} 
          style={styles.button}>
            <Text>Check</Text>
          </TouchableOpacity>
        </View>
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  },
  button:{
    borderRadius:5,
    height:30,
    width:120,
    backgroundColor:'#138D75',
    justifyContent:'center',
    alignItems:'center'
  },
  welcome: {
    fontSize: 20,
    textAlign: 'center',
    margin: 10,
  },
  instructions: {
    textAlign: 'center',
    color: '#333333',
    marginBottom: 5,
  },
});
```

## Screencasts

![demo](https://github.com/ekartal/react-native-pin-code-ui/ss/demo1.png)
![demo](https://github.com/ekartal/react-native-pin-code-ui/ss/demo2.png)

#### Props
- `onChangeValue` when value of pin is changed
- `onChangeStatus` status pass true if all of pin is set, otherwise false
- `styleEmptyBox` style of empty pin box 
- `styleFullBox` style of full pin box 
- `styleText` style of text in buttons 
- `styleButton` style of buttons 