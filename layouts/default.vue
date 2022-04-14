<template>
  <div>
    <NavBar />
    <main>
      <b-container>
        <nuxt />
      </b-container>
    </main>
  </div>
</template>

<script>
import NavBar from "@/components/NavBar";

export default {
  components: {
    NavBar,
  },
};
</script>

<style lang="scss" scoped></style>
