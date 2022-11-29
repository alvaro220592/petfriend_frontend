<script setup>
import { useUsers } from '@/stores/user'
import { computed, ref } from 'vue'
import PrimaryButton from '@/components/PrimaryButton.vue'
import GuestLayout from '@/layouts/GuestLayout.vue'
import TextInput from '@/components/TextInput.vue'
import InputLabel from '@/components/InputLabel.vue'
import ValidationErrors from '@/components/ValidationErrors.vue'

const store = useUsers()

const form = ref({
    email: '',
})

const processing = ref(false)

const setStatus = ref()

const setErrors = ref()

const status = computed(() => setStatus.value)

const errors = computed(() => setErrors.value)

const submit = () => {
    store.forgotPassword(form, setStatus, setErrors, processing)
}
</script>

<template>
    <GuestLayout>
        <div class="instrucoes">
            <p>Esqueceu a senha?</p>
            <p>Insira seu email para receber o link de redefinição.</p>
        </div>

        <div v-if="status" class="mb-4 font-medium text-sm text-green-600">
            {{ status }}
        </div>

        <ValidationErrors class="mb-4" :errors="errors" />

        <form @submit.prevent="submit">
            <div>
                <InputLabel for="email" value="Email" />
                <TextInput
                    id="email"
                    type="email"
                    class="mt-1 block w-full"
                    v-model="form.email"
                    required
                    autofocus
                    autocomplete="username" />
            </div>

            <div class="flex items-center justify-end mt-4">
                <PrimaryButton class="ml-4" :processing="processing">
                    Enviar
                </PrimaryButton>
            </div>
        </form>
    </GuestLayout>
</template>

<style lang="scss" scoped>
    
    .instrucoes {
        text-align: center;
        margin-bottom: 20px;
    }

</style>
