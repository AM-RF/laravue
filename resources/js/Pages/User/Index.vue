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
                        <Link :href="route('user.create')">Crear User</Link>
                        <table class="table-auto w-full">
                            <thead>
                                <tr>
                                    <th class="p-3">Id</th>
                                    <th class="p-3">Nombre</th>
                                    <th class="p-3">Email</th>
                                    <th class="p-3">Acciones</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr v-for="u in users" :key="u.id">
                                    <td class="p-3 border text-center">{{ u.id }}</td>
                                    <td class="p-3 border text-center">{{ u.name }}</td>
                                    <td class="p-3 border text-center">{{ u.email }}</td>
                                    <td class="p-3 border text-center">
                                        <Link :href="route('user.show', { customer: u })">Ver</Link>
                                        <Link :href="route('user.edit', { customer: u })">Editar</Link>
                                        <button @click="daleteUser(u)">Eliminar</button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </AppLayout>
</template>

<script>
    import AppLayout from '@/Layouts/AppLayout.vue';
    import { Inertia } from '@inertiajs/inertia';
    import { Link } from '@inertiajs/inertia-vue3'
    export default {
        props: ['users'],
        components: {
            AppLayout,
            Link
        },
        methods: {
            daleteUser: function(data){
                if (!confirm("¿Quieres eliminar este usuario?")) return;
                Inertia.delete(route("user.destroy", {customer:data}))
            },
        },
    }
   
</script>