<template>

    <Page class="page">
        <ActionBar title="Add Item" android:flat="true"/>
            
                <GridLayout rows="auto, auto, auto" id="item1">
                    <StackLayout row="0" class="input-field">
                        <!-- <TextField class="id" hint="ID" v-model="id"/> -->
                        <TextField class="name" hint="Name" v-model="name"/>
                        <TextField class="uid" hint="Uid" v-model="uid"/> 
                        <!-- <Button text="Add Item" @tap="add_item" class="btn-primary "></Button>
                        <Button @tap="this.$navigateBack" text="Go Back"></Button> -->
                        <!-- <StackLayout class="hr-light"></StackLayout> -->
                    </StackLayout>
               

                    <StackLayout row="1" class="input-field">
                        <StackLayout class="hr-light"></StackLayout>
                        <Button text="Add Item" @tap="add_item" class="btn-primary "></Button>
                        <Button @tap="this.$navigateBack" text="Go Back"></Button>
                        
                    </StackLayout>
                </GridLayout>
    </Page>
</template>

<script>
import back_item from "./item";
var firebase = require("nativescript-plugin-firebase");
export default {
  name: "item",
  
  data() {
    return {
    //  email: this.user.email,
      name: "",
      uid: ""
    };
  },
  methods: {
    // goToSecond() {
    //     this.$navigateTo(Second)
    // },
    add_item: function() {
      const item = firebase.firestore.collection("item");
      item
        .add({
          // id: this.id
          // email: this.user.email,
          name: this.name,
          uid: this.uid
        })
        .then(doc => {
          console.log("found item ...." + doc.id);
          this.$navigateTo(back_item);
        });
       //this.$navigateBack;
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
