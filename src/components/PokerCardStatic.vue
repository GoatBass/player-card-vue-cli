<template>
    <span>
        <img :src="cardImage" alt="back-card" width="100" />
    </span>
</template>

<script>
export default {
    props: ['cardImage']
}
</script>