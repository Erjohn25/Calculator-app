<template>
  <div class="bg-dark rounded py-3 px-6 text-white text-2xl text-right">
    <span  :class="{'text-base': total.length >= 25}">{{ parseInt(total) }}</span>
  </div>
</template>

<script>
export default {
    props:['total'],
}
</script>