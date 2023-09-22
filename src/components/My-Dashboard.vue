<template>
  <div class="dashboard">
    <div class="section">
      <h2 class="section-title">People</h2>
      <draggable :list="people" :move="onMove" @end="onEnd">
        <template #item="{ element }">
          <div class="draggable-item">{{ element.name }} - {{ element.info }}</div>
        </template>
      </draggable>
    </div>

    <div class="section">
      <h2 class="section-title">Calendar</h2>
      <draggable :list="calendarEvents" :move="onMove" @end="onEnd">
        <template #item="{ element }">
          <div class="draggable-item">{{ element.title }} - {{ element.date }}</div>
        </template>
      </draggable>
    </div>

    <div class="section">
      <h2 class="section-title">Notes</h2>
      <draggable :list="notes" :move="onMove" @end="onEnd">
        <template #item="{ element }">
          <div class="draggable-item">
            {{ element }}
          </div>
        </template>
      </draggable>
    </div>
  </div>
</template>

<script lang="ts">
import { ref } from 'vue'
import draggable from 'vuedraggable'

export default {
  components: {
    draggable
  },
  setup() {
    const people = ref([
      { name: 'Alice', info: 'Developer' },
      { name: 'Bob', info: 'Designer' },
      { name: 'Charlie', info: 'Manager' }
    ])

    const calendarEvents = ref([
      { title: 'Meeting', date: '2023-09-23' },
      { title: 'Deadline', date: '2023-09-24' }
    ])

    const notes = ref(['Note 1', 'Note 2', 'Note 3'])

    const onMove = (event: any) => {
      console.log('Moved:', event)
    }

    const onEnd = (event: any) => {
      console.log('New positions:', event.newDraggableIndex, event.oldDraggableIndex)
    }

    return { people, calendarEvents, notes, onMove, onEnd }
  }
}
</script>
