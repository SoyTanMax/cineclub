<template>
    <nav class="navbar is-transparent">
        <svg @click="showMenu = !showMenu" width="26" height="17" viewBox="0 0 26 17" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect width="26" height="3" fill="white"/>
            <rect y="7" width="26" height="3" fill="white"/>
            <rect y="14" width="26" height="3" fill="white"/>
        </svg>
        <Menu class="menu" :class="{'is-active': showMenu}"
            :showMenu="showMenu"
            @closeMenu="close"
        />
        <p class="logo">CINE<strong class="italic">CLUB</strong></p>
        <div class="ticket">
            <div class="counter-container">
                <p class="counter">{{ counter }}</p>
            </div>
            <svg width="23" height="19" viewBox="0 0 23 19" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M23 6.90268V2.30224C23 1.02561 21.965 0.00201416 20.7 0.00201416L2.3 0.00201416C1.035 0.00201416 0.0115 1.02561 0.0115 2.30224L0.0115 6.90268C1.2765 6.90268 2.3 7.93778 2.3 9.2029C2.3 10.468 1.2765 11.5031 0 11.5031L0 16.1036C0 17.3687 1.035 18.4038 2.3 18.4038H20.7C21.965 18.4038 23 17.3687 23 16.1036V11.5031C21.735 11.5031 20.7 10.468 20.7 9.2029C20.7 7.93778 21.735 6.90268 23 6.90268ZM20.7 5.22352C19.3315 6.0171 18.4 7.51224 18.4 9.2029C18.4 10.8936 19.3315 12.3887 20.7 13.1823V16.1036H2.3V13.1823C3.6685 12.3887 4.6 10.8936 4.6 9.2029C4.6 7.50074 3.68 6.0171 2.3115 5.22352L2.3 2.30224L20.7 2.30224V5.22352ZM10.35 12.6532H12.65V14.9535H10.35V12.6532ZM10.35 8.05279H12.65V10.353H10.35V8.05279ZM10.35 3.45235L12.65 3.45235V5.75257H10.35V3.45235Z" fill="white"/>
            </svg>
        </div>
    </nav>
</template>

<script>
    import Menu from '@/components/Menu.vue'
    export default {
        name: 'Navbar',
        components: { Menu },
        data() {
            return {
                counter: 0,
                showMenu: false
            }
        },
        methods:{
            close(){
                this.showMenu = false
            }
        }
    }
</script>

<style scoped>
/*Estoy consciente de que el navbar llevaba una opacidad
 pero al aplicar los estilos hacía el fondo gris y no transparente,
 por eso lo dejé color negro*/
.navbar{
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: relative;
    top: 0;
    width: 100%;
    height: 52px;
    background: black;
}
svg{
    width: 24px;
    padding-left: 24px;
    padding-right: 24px;
    z-index: 97;
}
.logo{
    color: white;
    font-size: 25px;
    font-family: 'Montserrat', sans-serif;
}
.italic{
    font-style: italic;
}
.ticket{
    position: relative;
}
.counter-container{
    position: absolute;
    top: -10px;
    right: 15px;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 98;
    width: 19px;
    height: 19px;
    background: #FF2E2E;
    border-radius: 50%;
}
.counter{
    color: white;
    font-size: 13px;
}
.menu{
    visibility: hidden;
    width: 0%;
    transition: all 0.3s ease;
}
.menu.is-active{
    visibility: visible;
    width: 73vw;
}
</style>