<template>
  <router-link to="/about" :class="styleing">{{message}}</router-link>
</template>

<script setup>
defineProps({
    styleing: String,
    message: String
})

</script>

<style  scoped>
.success{
    padding: 10px;
    background: white;
    text-decoration: none;
    color: #412918;
    transition: .25s all ease-in-out;
}

.success:hover{
    color: #291507;
    background: rgb(170, 168, 168);
    border-radius: 5px;
}
</style>