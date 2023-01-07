<template>
  <div class="tile large">
    <v-grid ref="grid" readonly="false" :source="rows" resize="false" :columns="columns" :editors="gridEditors"
      :filter="filterConfig" theme="material" @beforefocuslost="test" />
  </div>
</template>


<script lang="ts">
// beforeCellFocus
import { defineComponent, ref } from 'vue';
import { Components } from '@revolist/revogrid';
import VGrid, { VGridVueEditor, VGridVueTemplate } from '@revolist/vue-datagrid';
import Editor from './Editor.vue';
import Cell from './Cell.vue';
import { generateFakeDataObject } from './dataService';
import filterConfig from './FilterConfig.vue';


export default defineComponent({
  data() {
    return {
      filterConfig: filterConfig(),
      columns: [
        {
          name: 'ID',
          prop: 'id',
          sortable: true,
          readonly: true,
          order: 'asc',
          size: 350
        },

        {
          name: "date",
          prop: "date",
          sortable: true,
          readonly: true,
          order: 'asc',
        }
      ],
      rows: [
        {
          id: 34133,
          date: "25-10-2023 11:53:20 UTC"
        },
        {
          id: 31434,
          date: "30-10-2023 11:53:20 UTC"
        },
        {
          id: 1324,
          date: "29-10-2023 11:53:20 UTC"
        },
        {
          id: 41234,
          date: "26-10-2023 11:53:20 UTC"
        },
        {
          id: 41234,
          date: "25-10-2023 11:53:20 UTC"
        },
        {
          id: 34133,
          date: "50-10-2023 11:53:20 UTC"
        }
      ]
    }
  },
  components: {
    VGrid
  },
  setup() {
    const button = VGridVueEditor(Editor);
    const gridEditors = { button };
    const grid = ref<Components.RevoGrid | null>(null);

    return { grid, gridEditors };
  },
  methods: {
    test(e: CustomEvent) {
      console.log(e);
    }
  }
});
</script>

<style lang="scss">
body,
html {
  height: 100%;
  width: 100%;
  padding: 20px;
  margin: 0;
  overflow: hidden;
  background-color: #f7f9fc;
  text-align: center;
}

revo-grid {
  display: block;
}

.tile {
  background-color: #fff;
  display: flex;
  margin: 0 auto;
  padding: 20px 0;
  box-shadow: 0 0 14px 0 rgba(53, 64, 82, .05);
  border-radius: 10px;
  overflow: hidden;
}

.arrow-down svg {
  opacity: 1;
  width: 10px;
  height: 10px;
}

revo-grid {
  width: 100%;
}

.tile.dark {
  background-color: #333;
}

.tile.large {
  width: 800px;
  height: 400px;
}
</style>
