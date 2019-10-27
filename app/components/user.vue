<template>
    <Page class="page">
       <GridLayout rows="auto, auto, auto" id="user">
                    <StackLayout row="0" class="input-field">
                        <TextField class="name" hint="Name" v-model="name"/>
                        <StackLayout class="hr-light"></StackLayout>
                    </StackLayout>
               

                    <StackLayout row="1" class="input-field">
                        <StackLayout class="hr-light"></StackLayout>
                        <Button text="Go" @tap="adduser" class="btn-primary "></Button>
                    </StackLayout>
                </GridLayout>
    </Page>
</template>
<script>
import menu_item from "./item";
var firebase = require("nativescript-plugin-firebase");
export default {
  name: "user",
  props: ['user'],
  data() {
    return {
      name: "",
      email: this.user.email
    };
  },
  methods: {
    
    adduser: function() {
      console.log(this.user);
      
      const person = firebase.firestore.collection("user");
      person
        .add({
          name: this.name,
          email: this.user.email
        })
        .then(doc => {
          console.log("found id ...." + doc.id);
        });
      this.$navigateTo(menu_item, {props: {user:this.$user}});
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
