<script setup>
import { ref } from 'vue'

//const listValues = [0, 1, 2, 3, 4, 5, 6, 7, 8]
const items = ref([
  {id: 0, val: '', toggle: false},
  {id: 1, val: '', toggle: false},
  {id: 2, val: '', toggle: false},
  {id: 3, val: '', toggle: false},
  {id: 4, val: '', toggle: false},
  {id: 5, val: '', toggle: false},
  {id: 6, val: '', toggle: false},
  {id: 7, val: '', toggle: false},
  {id: 8, val: '', toggle: false},
])

const status = ['TURNO X', 'TURNO B', 'PLAYER X WIN!', 'PLAYER O WIN!']
const turno = ref(false)
const cambioTurno = () => {
  turno.value = !turno.value
  console.log('Cambio de turno', turno.value)
}

const showValue = (id) => {
  items.value[id].toggle = !items.value[id].toggle
  console.log(items.value[id].toggle, id)
  cambioTurno()
  if(turno.value == true){
    items.value[id].val = 'X'
  } else {
    items.value[id].val = 'O'
  }
  console.log(items.value[id].val)
}


//item.toggle == true ? item.val = 'X' : item.val = 'O'
</script>
<template>

  <div class="grid content-center justify-items-center h-full">

    <div class="w-96">
    <div class="bg-slate-200 text-center text-xl">TIC TAC TOE</div>
    <div class="bg-slate-200 text-center text-xl">TURNO X</div>

    <div class="dahsboard grid grid-cols-3"> 
      <div 
        v-for="item in items"
        :key="item.id"
        class="text-center bg-slate-200 h-24"
      >
        <div class="value grid content-center h-24" @click="showValue(item.id)">
          {{ item.val }}
        </div>
      </div>
    
    </div>
    
    </div>
  
  </div>

</template>
