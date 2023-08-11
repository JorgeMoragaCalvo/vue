<template>
  <section>
    <h3>Anadir Profesor</h3>
    <div><label>Nombre:</label> <input type="text" v-model="teacher.teacherName"></div>
    <div><label>Apellidos:</label> <input type="text" v-model="teacher.surname"></div>
    <div><label>RUT:</label> <input type="text" v-model="teacher.rut"></div>
    <div><label>Asignaturas:</label> <input type="text" v-model="subject"><button>Agregar</button></div>
    <input type="checkbox" v-model="teacher.doc">Documentacion entregada
    <button>Agregar</button>
  </section>

  <section>
    <h3>Listado de Profesores</h3>
  </section>
</template>
 
<script lang="ts" setup>
    import { Ref, ref } from 'vue';
    interface ITeacher {
        teacherName: string;
        surname: string;
        rut: string;
        asignature: Array<string>;
        doc: boolean;
    }

    let teacher:Ref<ITeacher> = ref ({
        teacherName: '',
        surname: '',
        rut: '',
        asignature: [],
        doc: false
    })

    /* JavaScript puro
    let teacher = ref ({
        teacherName: '',
        surname: '',
        rut: '',
        asignature: [],
        doc: false
    })*/

    let teachers:Ref<Array<ITeacher>> = ref ([])

    let subject:Ref<string> = ref ('')
</script>

<style scoped>

</style>