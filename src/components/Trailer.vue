<template>
    <div class="trailer">
        <div class="close-button" @click="closeTrailer">
            <svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="20" cy="20" r="20" fill="#E0E0E0"/>
                <rect x="10.9979" y="13.1981" width="3.11168" height="21.7817" transform="rotate(-45 10.9979 13.1981)" fill="#464646"/>
                <rect x="13.1981" y="28.6001" width="3.11168" height="21.7817" transform="rotate(-135 13.1981 28.6001)" fill="#464646"/>
            </svg>
        </div>
        <p class="title">{{ copy.title }}</p>
        <div class="trailer-container">
            <iframe width="368" height="207"
                src="https://www.youtube.com/embed/HjzATzdlN2A?controls=1">
            </iframe>
        </div>
    </div>
</template>

<script>
    import copy from '@/copy.js'
    export default {
        name: 'Trailer',
        props: ['showTrailer'],
        data() {
            return {
                copy: copy
            }
        },
        computed: {
            player() {
                return this.$refs.youtube.player
            }
        },
        methods: {
            closeTrailer(){
                this.$emit('closeTrailer');
            }
        }
    }
</script>

<style scoped>
.trailer{
    position: absolute;
    bottom: 0;
    z-index: 99;
    width: 100vw;
    height: 94vh;
    padding-top: 13px;
    border-radius: 32px 32px 0px 0px;
    background: white;
}
.trailer-container{
    padding: 18px 24px;
}
svg{
    display: flex;
    width: 40px;
}
.close-button{
    display: flex;
    justify-content: flex-end;
    padding-right: 16px;
}
.title{
    padding-left: 24px;
    font-size: 23px;
    line-height: 27px;
}
</style>