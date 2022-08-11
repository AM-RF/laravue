<template>
    <AppLayout title="Dashboard">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                User
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                    <div class="p-6 sm:px-20 bg-white borde-b border-gray-200">
                        <form @submit.prevent="submit">
                            <label>Nombre</label>
                            <p class="text-red-400" v-if="errors.name"> {{ errors.name }} </p>
                            <input type="text" v-model="form.name"/>
                            <label>Email</label>
                            <p class="text-red-400" v-if="errors.email"> {{ errors.email }} </p>
                            <input type="email" v-model="form.email"/>
                            <label>Contraseña</label>
                            <p class="text-red-400" v-if="errors.password"> {{ errors.password }} </p>
                            <input type="password" v-model="form.password"/>

                            <button type="submit">Enviar</button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </AppLayout>
</template>

<script>
    import AppLayout from '@/Layouts/AppLayout.vue';
    import { Inertia } from '@inertiajs/inertia';

    export default {
        props: ['customer', "errors"],
        data() {
            return {
                form: {
                    name: this.customer.name,
                    email: this.customer.email,
                    password: '',
                },
            };
        },
        components: {
            AppLayout
        },
        methods: {
            submit() {
                Inertia.put(route('user.update', {'customer':this.customer}), this.form);
            },
        },
    }
   
</script>

