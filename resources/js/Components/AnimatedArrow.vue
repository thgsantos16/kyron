<template>
    <div class="custom-arrow" :class="direction">
        <div class="row">
            <div class="col-6" v-for="i in 40" :key="i">
                <div />
            </div>
        </div>
        <div class="arrow-icon">
            <b-icon :icon="'chevron-' + direction"></b-icon>
        </div>
    </div>
</template>

<script>
export default {
    props: [ 'direction' ]
}
</script>

<style lang="scss" scoped>

.custom-arrow {
    position: absolute;
    right: 15px;
    width: 10vh;
    height: 100vh;

    &.left {
        right: auto;
        left: 15px;

        .col-6 {
            &:nth-child(even) {
                div {
                    background: rgb(0,0,0);
                    background: linear-gradient(90deg, rgba(0,0,0,0.43) 0%, rgba(0,0,0,0) 100%);
                }
            }
        }
    }

    &.right {
        .col-6 {
            &:nth-child(odd) {
                div {
                    background: rgb(0,0,0);
                    background: linear-gradient(90deg, rgba(0,0,0,0) 0%, rgba(0,0,0,0.43) 100%);
                }
            }
        }

    }

    &:hover {
        cursor: pointer;

        .col-6 {
            div {
                width: 100%;
                height: 100%;
                margin: 0;
                border-radius: 0;
            }
        }

        .arrow-icon {
            top: calc(50% - 72px);
            font-size: 72px;
            opacity: 1;
            animation: arrow .7s linear infinite;
        }
    }

    .col-6 {
        height: 5vh;
        padding: 0;


        @for $i from 1 through 20 {
            &:nth-child(#{$i}) {
                div {
                    transition-delay: calc(16ms * #{$i});
                }
            }
        }

        @for $i from 1 through 20 {
            &:nth-child(40n - #{$i}) {
                div {
                    transition-delay: calc(16ms * #{$i});
                }
            }
        }

        div {
            transition: all 0.43s;
            height: 0;
            width: 0;
            margin: -1vh 0 0 -1vh;
            background: rgba(0, 0, 0, 0.43);
            border-radius: 50%;
        }
    }

    .arrow-icon {
        transition: all 0.43s;
        color: #FFF;
        position: absolute;
        z-index: 999;
        top: calc(50% - 36px);
        text-align: center;
        width: 10vh;
        font-size: 48px;
        opacity: 0.52;
    }
}

@keyframes arrow {
    0% { margin-left: 0; }
    25% { margin-left: -.7vh; }
    75% { margin-left: .7vh; }
    100% { margin-left: 0; }
}

</style>
