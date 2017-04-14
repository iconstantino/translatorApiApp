<template>
    <h2 class="translated-text">{{translatedText}}</h2>
</template>

<script>
export default {
  name: 'translateOutput',
  props: ['translatedText']
}
</script>

<style>
    .translated-text {
        color: brown;
    }
</style>