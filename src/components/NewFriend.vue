<template>
    <!-- prevent is use for browser not reload after sumbit form -->
    <form @submit.prevent="saveData">
        <div>
            <label>Name</label>
            <input type="text" v-model="inputName">
        </div>
        <div>
            <label>Phone</label>
            <input type="tel" v-model="inputPhone">
        </div>
        <div>
            <label>E-Mail</label>
            <input type="email" v-model="inputEmail">
        </div>
        <div>
            <button>Add Contact</button>
        </div>
    </form>
    
</template>
<script>
    export default {
        data() {
            return {
                inputName: '',
                inputPhone: '',
                inputEmail: ''
            };
        },
        emits: ['submit-form'],
        methods: {
            saveData() {
                this.$emit('submit-form', this.inputName, this.inputPhone, this.inputEmail);
            }
        }
    };
</script>