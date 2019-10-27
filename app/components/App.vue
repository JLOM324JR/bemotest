<script>
import { login } from "nativescript-plugin-firebase";
// import { __values } from 'tslib';

        // Initialize Firebase
        var config = {
            apiKey: "AIzaSyDKrCGhNHswEoSJXUB7WvrdtsCdLAeUZTU",
            authDomain: "test1bemo.firebaseapp.com",
        };
        firebase.initializeApp(config);
    </script>


<template>
    <FlexboxLayout class="page">
        <StackLayout class="form">
            <Page   android:BackgroundColor="#53ba82"
                    android:TextColor="#c4ffdf"
                    android:selectedTextColor="#ffffff"
                    androidSelectedHighlightColor="#ffffff">
            
            <ActionBar title="Welcome" android:flat="true"/>
            
                <GridLayout rows="auto, auto, auto" id="user">
                    <StackLayout row="0" class="input-field">
                        <TextField class="email" hint="Email" v-model="email"/>
                        <!-- <TextField class="name" hint="Name" v-model="name"/> -->
                        <TextField class="password" hint="Password" secure="true" v-model="password"/>
                        <StackLayout class="hr-light"></StackLayout>
                    </StackLayout>
               

                    <StackLayout row="1" class="input-field">
                        <StackLayout class="hr-light"></StackLayout>
                        <Button text="Sign In" @tap="login" class="btn-primary "></Button>
                        <!--<Button text="Add Item" @tap="gotoApp" fontSize="18"></Button>-->
                         <!-- <Button @tap="goToSecond" text="Go to Second"></Button> -->
                    </StackLayout>
                </GridLayout>

               
                
           </Page> </StackLayout>
        </FlexboxLayout>

    
            
      
    
</template>
<script>
import username from "./user";
var firebase = require("nativescript-plugin-firebase");

export default {
  name: "user",
  data() {
   
    return {
      email: "",
      password: ""
      
    };
  },
  methods: {
    
    // goToSecond() {
    //     this.$navigateTo(Second)
    // },
    login: function() {
    
      firebase.login(
      {
        type: firebase.LoginType.PASSWORD,
        passwordOptions: {
          email: this.email,
          password: this.password
        }
      })
      .then(result => {
        
        // Vue.prototype.$result = JSON.stringify(result);
        console.log(JSON.stringify(result));
        
        this.$user = result;
        console.log(this.$user);
        this.$navigateTo(username, {props: {user:this.$user}});
        
        }) 
      
      .catch(error => console.log(error)

      );

    }
  }
};
</script>

<style scoped>
ActionBar {
  background-color: #53ba82;
  color: #ffffff;
}

.message {
  vertical-align: center;
  text-align: center;
  font-size: 20;
  color: #333333;
}
</style>
