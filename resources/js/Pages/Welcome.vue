<template>
    <div class="main container-fluid">
        <div class="row">
            <div class="home">
                <div class="bgs">
                    <transition-group name="fade" appear>
                        <div class="bg"
                            v-for="(bg, i) in bgs"
                            :key="bg"
                            :style="{ 'background-image': 'url(' + asImage(bg) + ')'}"
                            v-show="selectedBG === i" />
                    </transition-group>
                </div>

                <animated-arrow @click="toLeft()" direction="left" />

                <div class="logo">
                    <jet-application-logo class="block w-auto" />
                </div>

                <animated-arrow @click="toRight()" direction="right" />
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

    let timer

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
        },
        data() {
            return {
                bgs: [
                    'bg.jpg',
                    'bg2.jpg',
                ],
                selectedBG: 0,
                timeout: 5000
            }
        },
        beforeMount() {
            timer = setTimeout(this.toRight, this.timeout)
        },
        methods: {
            asImage(img) {
                var images = require.context('../assets/', false)
                return images('./' + img).default
            },
            toRight() {
                clearTimeout(timer)
                if(this.selectedBG < this.bgs.length - 1) this.selectedBG++
                else this.selectedBG = 0
                timer = setTimeout(this.toRight, this.timeout)
            },
            toLeft() {
                clearTimeout(timer)
                if(this.selectedBG > 0) this.selectedBG--
                else this.selectedBG = this.bgs.length - 1
                timer = setTimeout(this.toRight, this.timeout)
            }
        }
    }
</script>

<style scoped lang="scss">

.home {
  background: no-repeat center/cover #000;
  display: flex;
  width: 100%;
  height: 100vh;
  position: relative;
  align-items: center;
  justify-content: center;

  .logo {
    max-width: 80%;
    z-index: 99;

    img {
      max-width: 100%;
    }
  }

    .bg {
        position: absolute;
        height: 100%;
        width: 100%;
        top: 0;
        left: 0;
        background: center/cover no-repeat;
        z-index: 9;
    }
}

.hero {
    height: 100vh;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to  {
  opacity: 0;
}

</style>
