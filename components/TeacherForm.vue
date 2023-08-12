<template>
  <section>
    <h3>Anadir Profesor</h3>
    <div><label>Nombre:</label> <input type="text" v-model="teacher.teacherName"></div>
    <div><label>Apellidos:</label> <input type="text" v-model="teacher.surname"></div>
    <div><label>RUT:</label> <input type="text" v-model="teacher.rut"></div>
    <div><label>Asignaturas:</label> <input type="text" v-model="subject"><button @click="handleSubject">Agregar</button></div>
    <div>
      <ul>
        <li v-for="(elm, index) in teacher.asignature" :key="index">{{ elm }}</li>
      </ul>
    </div>
    <input type="checkbox" v-model="teacher.doc">Documentacion entregada
    <button @click="handleAddTeacher">Agregar</button>
  </section>

  <section>
    <h3>Listado de Profesores</h3>
    <table>
      <tr>
        <th>Nombre</th>
        <th>Apellidos</th>
        <th>RUT</th>
        <th>Asignaturas</th>
        <th>Documentacion Entregada</th>
      </tr>
      <tr v-for="elm in teachers" :key="elm.rut">
        <th>{{ elm.teacherName }}</th>
        <th>{{ elm.surname }}</th>
        <th>{{ elm.rut }}</th>
        <th>
          <ul>
            <li v-for="(item, index) in elm.asignature" :key="index">{{ item }}</li>
          </ul>
        </th>
        <th v-if="elm.doc">Entregada</th>
        <th v-else>No Entregada</th>
      </tr>
    </table>
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

    const handleSubject = () => {
      teacher.value.asignature.push(subject.value)
      subject.value = '' // Para limpiar el input
    }

    const handleAddTeacher = () => {
      teachers.value.push({
        teacherName: teacher.value.teacherName,
        surname: teacher.value.surname,
        rut: teacher.value.rut,
        asignature: teacher.value.asignature,
        doc: teacher.value.doc
      })
      teacher.value = {
        teacherName: '',
        surname: '',
        rut: '',
        asignature: [],
        doc: false
      }
    }
</script>

<style scoped>

</style>