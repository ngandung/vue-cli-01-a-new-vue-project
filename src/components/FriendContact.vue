<template>
    <li>
        <h2>{{ friends.name }}</h2>
        <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
        <ul v-if="detailsAreVisible">
            <li><strong>Phone:</strong> {{ friends.phone }}</li>
            <li><strong>Email:</strong> {{ friends.email }}</li>
        </ul>
    </li>
</template>

<script>
export default {
    data() {
        return {
            detailsAreVisible: false,
            friends: {
                id: 'manuel',
                name: 'Manuel Lorenz',
                phone: '0123 456 90',
                email: 'manuel@mail.com'
            }
        };
    },
    methods: {
        toggleDetails() {
            this.detailsAreVisible = !this.detailsAreVisible;
        }
    }
};
</script>