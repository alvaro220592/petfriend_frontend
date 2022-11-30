<script setup>
import ApplicationLogo from '@/components/ApplicationLogo.vue'
</script>

<template>
    
    <div class="guestContainer">
        <div>
            <router-link to="/">
                <!-- <ApplicationLogo
                    class="w-20 h-20 fill-current text-gray-500" /> -->
            </router-link>
        </div>

        <!-- <div class="w-full sm:max-w-md mt-6 px-6 py-4 bg-red-700 shadow-md overflow-hidden sm:rounded-lg"> -->
        <div class="guestCard">
            <div class="logo">
                <div class="logo__text">
                    <h1>
                        PetFriend
                    </h1>
                </div>
                <div class="logo__img">
                    <!-- <i class="bi bi-twitter"></i> -->
                    <!-- <a href="https://www.flaticon.com/free-icons/animals" title="animals icons">Animals icons created by Eucalyp - Flaticon</a> -->
                    <!-- <img src="@/img/logo__img.png" alt=""> -->
                </div>
            </div>
            <slot />
        </div>
    </div>
</template>

<style lang="scss" scoped>

    @import '@/assets/scss/_main';

    .guestContainer {
        min-height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-image: linear-gradient($fundo_guest, $fundo_guest), url("@/assets/img/animais/animais2.jpg");
        background-repeat: no-repeat;
        background-size: 100% 100%;
        background-color: $turquesa;
        
        .guestCard {
            padding: 20px;
            border-radius: 4px;
            background-color: $pastel;
            border: 3px solid $laranja;
            box-shadow: 1px 1px 2px $sombra;

            .logo {
                display: flex;

                .logo__text {
                    width: 100%;

                    h1 {
                        font-size: 50px;
                        border-radius: 4px;
                        padding: 10px;
                        width: 100%;
                        text-align: center;
                        color: $turquesa;
                        -webkit-text-stroke-width: 2px;
                        -webkit-text-stroke-color: $sombra;
                        text-shadow: 2px 2px 5px $abobora;
                        font-weight: 700;
                        // background-color: $laranja;
                        // box-shadow: 1px 1px 3px 3px $laranja;
                    }
                }
            }
        }
    }

    @media screen and (max-width: 768px) {
        
        .guestContainer {
            background-size: 300% 100%;
            background-position-x: 18%;

            .guestCard {
                max-width: 90%;
            }
        }

    }

</style>