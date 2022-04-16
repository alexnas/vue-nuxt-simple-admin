<template>
    <section>
        <h1>{{ pageTitle }}</h1>

        <ul>
            <li v-for="user in users" :key="user.id">
                <a href="#" @click.prevent="goTo(user)"> User: {{ user.name }} ({{ user.email }})</a>
            </li>
        </ul>
    </section>
</template>

<script>
export default {
    data() {
        return {
            pageTitle: 'Users Page Content',
        }
    },

    async fetch({ store, error }) {
        try {
            await store.dispatch('users/fetchUsers')
        } catch (err) {
            error(err)
        }
    },

    computed: {
        users() {
            return this.$store.getters['users/users']
        },
    },

    methods: {
        goTo(user) {
            this.$router.push(`/users/${user.id}`)
        },
    },
}
</script>
