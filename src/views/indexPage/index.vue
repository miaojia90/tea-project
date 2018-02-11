<template>
    <section class="userInfo">

    </section>
</template>
<script>
import { mapState, mapActions } from 'vuex';
export default {
    data() {
        return {
        }
    },
    computed: {
        ...mapState([
            'userCenterInfo'
        ])
    },
    methods: {},
    mounted() {
        document.title="新会陈皮柑普茶交易所";
        //生成二维码
    },
    components: {}
}
</script>
<style lang="scss" rel="stylesheet/scss" scoped>
$r_750:640/750/2/32;
@function rem($px) {
    @return $px * $r_750 *1rem;
}
</style>