<template>
    <div class="schedule">
        <div class="close-button" @click="closeSchedule" >
            <svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="20" cy="20" r="20" fill="#E0E0E0"/>
                <rect x="10.9979" y="13.1981" width="3.11168" height="21.7817" transform="rotate(-45 10.9979 13.1981)" fill="#464646"/>
                <rect x="13.1981" y="28.6001" width="3.11168" height="21.7817" transform="rotate(-135 13.1981 28.6001)" fill="#464646"/>
            </svg>
        </div>
        <div class="schedule-container" >
            <div class="time">{{ copy.time }}</div>
            <div class="options-container">
                <div v-for="option in copy.schedule" :key="option">
                    <p class="option">{{ option }}</p>
                </div>
            </div>
        </div>
        
    </div>
</template>

<script>
    import copy from '@/copy.js'
    export default {
        props: ['showSchedule'],
        name: 'Schedule',
        data() {
            return {
                copy: copy
            }
        },
        methods: {
            closeSchedule(){
                this.$emit('closeSchedule');
            }
        }
    }
</script>

<style scoped>
.schedule{
    position: absolute;
    bottom: 0;
    z-index: 99;
    width: 100vw;
    height: 94vh;
    padding-top: 13px;
    border-radius: 32px 32px 0px 0px;
    background: white;
}
.schedule-container{
    padding: 18px 40px
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
.options-container{
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(100px, 106px));
    gap: 7px;
}
.option{
    text-align: center;
    background: #FFFFFF;
    border: 1px solid #C7C7C7;
    padding: 8px 14px;
    border-radius: 5px;
}
.time{
    padding-top: 18;
    font-size: 23px;
    padding-bottom: 19px;
}
</style>