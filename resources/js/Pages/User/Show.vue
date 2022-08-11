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
                        {{ customer.name }}
                        {{ customer.email }}
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
        props: ['customer'],
        data() {
        },
        components: {
            AppLayout
        },
        methods: {
            submit() {
                Inertia.post(route('user.store'), this.form);
            },
        },
    }
   
</script>

