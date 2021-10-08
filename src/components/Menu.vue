<template>
    <div class="menu">
        <div class="close-button">
            <svg @click="closeMenu" width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="20" cy="20" r="20" fill="#E0E0E0"/>
                <rect x="10.9979" y="13.1981" width="3.11168" height="21.7817" transform="rotate(-45 10.9979 13.1981)" fill="#464646"/>
                <rect x="13.1981" y="28.6001" width="3.11168" height="21.7817" transform="rotate(-135 13.1981 28.6001)" fill="#464646"/>
            </svg>
        </div>
        <div class="options" v-for="option in copy.menu" :key="option">
            <p class="option" v-if="showMenu">{{ option }}</p>
        </div>
    </div>
</template>

<script>
    import copy from '@/copy.js'
    export default {
        name: 'Menu',
        props: ['showMenu'],
        data() {
            return {
                copy: copy
            }
        },
        methods: {
            closeMenu(){
                this.$emit('closeMenu');
            }
        }
    }
</script>

<style scoped>
.menu{
    position: absolute;
    top: 0;
    left: 0;
    z-index: 99;
    width: 73vw;
    height: 100vh;
    padding: 14px 36px 0 29px;
    border-radius: 0px 30px 0px 0px;
    background: #EBEBEB;
}

svg{
    width: 40px;
}
.close-button{
    display: flex;
    justify-content: flex-end;
    margin-bottom: 38px;
}
.options-container{
    display: flex;
    flex-direction: column;
}
.option{
    width: 100%;
    border-bottom: 1px solid #9A9A9A;
    padding-top: 10px;
    padding-bottom: 10px;
    font-size: 35px;
    margin: 0;
}

</style>