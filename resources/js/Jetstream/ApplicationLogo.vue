<template>
    <img :src="img" />
</template>

<script>

import logo from "../assets/logo.png"

export default {
    data() {
        return {
            img: logo
        }
    }
}
</script>
