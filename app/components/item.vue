<template>
    <Page class="page">
        <ActionBar title="Menu" class="action-bar" />
        <StackLayout>
            <Button @tap="item" text="Add Item"></Button>
        </StackLayout>
    </Page>
</template>

<script>
import add_item from './Add';

export default {
    props: ['user'],
    data () {
        return {
        };
    },
    methods: {
        item() {
            this.$navigateTo(add_item, {props: {user:this.$user}})
        }
    }
}
</script>