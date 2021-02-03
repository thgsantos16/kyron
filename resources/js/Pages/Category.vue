<template>
  <div class="home">
    <div class="logo">
        <jet-application-logo class="block w-auto" />
    </div>
  </div>
</template>

<style scoped lang="scss">

.home {
  background: no-repeat center/cover;
  background-image: url(../assets/bg.jpg);
  display: flex;
  width: 100%;
  height: 100%;
  position: absolute;
  align-items: center;
  justify-content: center;

  .logo {
    max-width: 80%;

    img {
      max-width: 100%;
    }
  }
}

</style>

<script>
    import JetApplicationLogo from '@/Jetstream/ApplicationLogo'

    export default {
        components: {
            JetApplicationLogo,
        },
        props: {
            canLogin: Boolean,
            canRegister: Boolean,
            laravelVersion: String,
            phpVersion: String,
        }
    }
</script>
