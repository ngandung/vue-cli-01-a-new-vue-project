<template>
    <li>
        <h2>{{ name }} {{ isFavorite ? '(Favorite)' : '' }}</h2>
        <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
        <button @click="toggleFavorite">Toggle Favorite</button>
        <ul v-if="detailsAreVisible">
            <li><strong>Phone:</strong> {{ phoneNumber }}</li>
            <li><strong>Email:</strong> {{ emailAddress }}</li>
        </ul>
        <button @click="$emit('delete', id)">Delete</button>
    </li>
</template>

<script>
export default {
    /*
    props: [
        'name',
        'phoneNumber',
        'emailAddress'
    ],*/
    props: {
        id: {
            type: String,
            required: true
        },
        name: {
            type: String,
            required: true
        },
        phoneNumber: {
            type: String,
            required: true
        },
        emailAddress: {
            type: String,
            required: true
        },
        isFavorite: {
            type: Boolean,
            required: false,
            default: false,
            // validator: function(value) {
            //     return value === '1' || value === '0';
            // }
        }
    },
    //to help developer show list of create emits attribute on methods
    emits: ['toggle-favorite', 'delete'],
    data() {
        return {
            detailsAreVisible: false,
            //create new variable to save data from property if u one to change the value on component
            fav: this.isFavorite
        };
    },
    methods: {
        toggleDetails() {
            this.detailsAreVisible = !this.detailsAreVisible;
        },
        toggleFavorite() {
            //use $emit to passing value from child (companent) to parent (app.vue) and change value to parent
            //this.fav = !this.fav;
            this.$emit('toggle-favorite',this.id)
        }
    }
};
</script>