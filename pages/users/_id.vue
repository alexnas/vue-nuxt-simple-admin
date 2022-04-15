<template>
    <div>
        <h1>User {{ user.name }}</h1>
        <hr />
        <b>{{ user.email }}</b>
    </div>
</template>

<script>
export default {
    validate({ params }) {
        return /^\d+$/.test(params.id)
    },

    async asyncData({ params, error, $axios }) {
        try {
            const user = await $axios.$get(`https://jsonplaceholder.typicode.com/users/${params.id}`)
            return { user }
        } catch (err) {
            error(err)
        }
    },
}
</script>
