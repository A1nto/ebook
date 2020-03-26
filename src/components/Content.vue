<template>
    <transition name="slide-right">
        <div class="content">
            <div class="content-wrapper" v-if="bookAvailable">
                <div
                    class="content-item"
                    v-for="(item, index) in navigation.toc"
                    :key="index"
                    @click="jumpTo(item.href)"
                >
                    <span class="text">{{ item.label }}</span>
                </div>
            </div>
            <div class="empty" v-else>加载中...</div>
        </div>
    </transition>
</template>

<script>
export default {
    props: {
        ifShowContent: Boolean,
        navigation: Object,
        bookAvailable: Boolean
    },
    methods: {
        jumpTo (target) {
            this.$emit('jumpTo', target)
        }
    }
}
</script>

<style lang="scss" scoped>
@import "../assets/styles/global.scss";
.content {
    position: absolute;
    top: 0;
    left: 0;
    width: px2rem(240);
    height: 100%;
    overflow: hidden;
    background: #fff;
    z-index: 102;
    .content-wrapper {
        padding: px2rem(10);
        height: 100%;
        box-sizing: border-box;
        overflow: scroll;
        .content-item {
            line-height: px2rem(16);
            padding: px2rem(10) 0;
            .text {
                font-size: px2rem(16);
            }
        }
    }
    .empty {
        height: 100%;
        font-size: px2rem(16);
        @include center;
    }
}
</style>
