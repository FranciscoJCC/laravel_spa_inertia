<script setup>
    import { Link } from '@inertiajs/inertia-vue3';
    import { ref, watch, reactive } from 'vue';
    import AppLayout from '@/Layouts/AppLayout.vue';
    import { Inertia } from '@inertiajs/inertia';

    const props = defineProps({
        notes : Array,
    });

    const q = ref(null);

    /* watch(q, () =>{
        Inertia.get(route('notes.index', {q}, {},{
            preserveState:true,
        }));
    }); */
    const search = () =>{
        let q = q.value;
        Inertia.get(route('notes.index',{q}), {}, {
            preserveState:ture
        });
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
                            <h3 class="text-lg text-gray-900">Listado de notas</h3>
                            <p class="text-sm text-gray-600">Toma el registro correcto y ejecuta cualquier función. (Ver, editar o eliminar)</p>
                        </div>
                    </div>
                    <div class="md:col-span-2 mt-5 md:mt-0">
                        <div class="shadow bg-white md:rounded-md p-4">
                            <div class="flex justify-between">
                                <input type="text" class="form-input rounded-md shadow-sm" placeholder="Buscar..." v-model="q" @keyup="search()">
                                <Link :href="route('notes.create')" class="bg-blue-500 text-white font-bold py-2 px-4 my-2 rounded-md ">Nueva nota</Link>
                            </div>
                            <hr class="my-6">
                            <table>
                                <tr v-for="note in notes" :key="note.id">
                                    <td class="border px-4 py-2">
                                        {{ note.excerpt }}
                                    </td>
                                    <td class="px-4 py-2">
                                        <Link :href="route('notes.show', note.id)">
                                            Ver
                                        </Link>
                                    </td>
                                    <td class="px-4 py-2">
                                        <Link :href="route('notes.edit', note.id)">
                                            Editar
                                        </Link>
                                    </td>
                                </tr>
                            </table>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </AppLayout>
</template>
