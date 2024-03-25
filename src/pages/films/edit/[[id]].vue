<script setup lang="ts">

// import Form from '@/components/Form.vue';
import AfficheFilm from "@/components/AfficheFilm.vue";
import { FormKit } from "@formkit/vue";
import { supabase } from "@/supabase";
import { ref } from "vue";
import { useRouter, useRoute } from "vue-router/auto";

const router = useRouter();
const films = ref({});
const route = useRoute('/films/edit/[[id]]');

async function upsertFilm(dataForm: any, node: { setErrors: (arg0: any[]) => void; }) {
    console.log("dataForm :",dataForm);
    
    const { data, error } = await supabase.from("films").upsert(dataForm).select("id");
    if (error) node.setErrors([error.message])
    else {
        console.log("data :",data);
        router.push({name:"/films/edit/[[id]]", params:{id: data[0].id}});
    }
}

if (route.params.id) {
    const { data, error } = await supabase.from("films").select("*").eq("id", route.params.id).single();
    if (error) console.error(error);
    else films.value = data;
}
console.log("films.value",films.value);

</script>

<template>

    <div>
        <div class="p-2">
            <h2 class="text-3xl text-center text-gray-200 mt-20">
                Résultat (Prévisualisation)
            </h2>
            <AfficheFilm  v-bind="films" />
        </div>
        <div class="p-2 m-auto flex justify-center">
            <FormKit @submit="upsertFilm" type="form" v-model="films"
            :config="{
                classes: {
                    input: 'p-1 rounded border-gray-300 text-gray-200 shadow-sm border',
                    label: 'text-gray-200 italic',
                    outer: 'py-2',
                    },
                }">
                <FormKit name="titre" label="Titre du film" />
                <FormKit name="synopsis" label="Description du film" />
                <FormKit name="note" type="number" label="Note /5" />
                <FormKit name="affiche" label="Images du film" />
                <FormKit name="date_de_sortie" type="number" label="Date de sortie" />
                <FormKit name="duree" type="time" label="Durée du film" />
                <FormKit name="banniere" label="Bannière" />
            </FormKit>
        </div>
    </div>
</template>