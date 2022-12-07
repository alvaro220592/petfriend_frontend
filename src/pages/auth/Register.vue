<script setup>
import { useUsers } from '@/stores/user'
import { computed, ref } from 'vue'
import PrimaryButton from '@/components/PrimaryButton.vue'
// import GuestLayout from '@/layouts/GuestLayout.vue'
import AuthenticatedLayout from '@/layouts/AuthenticatedLayout.vue'
import TextInput from '@/components/TextInput.vue'
import InputLabel from '@/components/InputLabel.vue'
import ValidationErrors from '@/components/ValidationErrors.vue'

const store = useUsers()

const form = ref({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
    terms: false,
})

const processing = ref(false)

const setErrors = ref()

const errors = computed(() => setErrors.value)

const submitRegister = () => {
    store.register(form, setErrors, processing)
}
</script>

<template>
    <AuthenticatedLayout :routeTitle="currentRouteName">

        <ValidationErrors class="mb-4" :errors="errors" />

        <form @submit.prevent="submitRegister">
            <div>
                <InputLabel for="name" value="Nome" />
                <TextInput
                    id="name"
                    type="text"
                    class="mt-1 block w-full"
                    v-model="form.name"
                    required
                    autofocus
                    autocomplete="name" />
            </div>

            <div class="mt-4">
                <InputLabel for="email" value="Email" />
                <TextInput
                    id="email"
                    type="email"
                    class="mt-1 block w-full"
                    v-model="form.email"
                    required
                    autocomplete="username" />
            </div>

            <div class="mt-4">
                <InputLabel for="role" value="Email" />
                <TextInput
                    id="role"
                    type="text"
                    class="mt-1 block w-full"
                    v-model="form.role"
                    required
                    autocomplete="username" />
            </div>

            <div class="mt-4">
                <InputLabel for="role" value="Perfil de acesso" />
                <select name="role" id="role" class="form-control">
                    <option value="1">Usuário</option>
                    <option value="2">Administrador</option>
                </select>
            </div>

            <div class="mt-4">
                <InputLabel for="password" value="Senha" />
                <TextInput
                    id="password"
                    type="password"
                    class="mt-1 block w-full"
                    v-model="form.password"
                    required
                    autocomplete="new-password" />
            </div>

            <div class="mt-4">
                <InputLabel
                    for="password_confirmation"
                    value="Confirmar senha" />
                <TextInput
                    id="password_confirmation"
                    type="password"
                    class="mt-1 block w-full"
                    v-model="form.password_confirmation"
                    required
                    autocomplete="new-password" />
            </div>

            <div class="flex items-center justify-end mt-4">
                <!-- <router-link
            to="/login"
            class="underline text-sm text-gray-600 hover:text-gray-900">
            Já tem cadastro?
        </router-link> -->

                <PrimaryButton class="ml-4" :processing="processing">
                    Cadastrar
                </PrimaryButton>
            </div>
        </form>
    </AuthenticatedLayout>
</template>

<script>
    export default {
        computed: {
            currentRouteName() {
                return this.$route.meta.title
            }
        }
    }
</script>