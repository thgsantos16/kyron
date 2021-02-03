<template>
    <div class="main container-fluid">
        <div class="row">
            <div class="home">
                <animated-arrow direction="left" />

                <div class="logo">
                    <jet-application-logo class="block w-auto" />
                </div>

                <animated-arrow direction="right" />
            </div>
        </div>

        <div class="row">
            <div class="hero">
            </div>
        </div>
    </div>
</template>

<script>
    import JetApplicationLogo from '@/Jetstream/ApplicationLogo'
    import AnimatedArrow from '@/Components/AnimatedArrow'

    export default {
        components: {
            JetApplicationLogo,
            AnimatedArrow,
        },
        props: {
            canLogin: Boolean,
            canRegister: Boolean,
            laravelVersion: String,
            phpVersion: String,
        }
    }
</script>

<style scoped lang="scss">

.home {
  background: no-repeat center/cover;
  background-image: url(../assets/bg.jpg);
  display: flex;
  width: 100%;
  height: 100vh;
  position: relative;
  align-items: center;
  justify-content: center;

  .logo {
    max-width: 80%;

    img {
      max-width: 100%;
    }
  }
}

.hero {
    height: 100vh;
}

</style>
