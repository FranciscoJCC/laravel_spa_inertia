<script setup>
    import { useForm } from '@inertiajs/inertia-vue3';
    import AppLayout from '@/Layouts/AppLayout.vue';

    const form = useForm({
        excerpt : '',
        content : '',
    });

    const submit = () => {
        form.post(route('notes.store'), form);
    };

</script>

<template>
    <AppLayout title="Dashboard">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Módulo de notas
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="md:grid md:grid-cols-3 md:gap-6">
                    <div class="md:col-span-1">
                        <div class="px-4 sm:px0">
                            <h3 class="text-lg text-gray-900">Nueva nota</h3>
                        </div>
                    </div>
                    <div class="md:col-span-2 mt-5 md:mt-0">
                        <div class="shadow bg-white md:rounded-md p-4">
                            <form @submit.prevent="submit">
                                <label for="" class="block font-medium text-sm text-gray-700">Resumen</label>
                                <textarea 
                                    v-model="form.excerpt"
                                    class="form-input w-full rounded-md shadow-sm"
                                ></textarea>
                                <label for="" class="block font-medium text-sm text-gray-700">Contenido</label>
                                <textarea 
                                    v-model="form.content"
                                    rows="8"
                                    class="form-input w-full rounded-md shadow-sm"
                                ></textarea>

                                <button

                                    class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-3 px-4 my-2"
                                >
                                    Guardar
                                </button>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </AppLayout>
</template>
