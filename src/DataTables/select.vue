<template>
<div style="width: 760px;">
  <ag-grid-vue style="width: 500px; height: 500px;" class="ag-theme-balham" @grid-ready="onGridReady" :columnDefs="columnDefs" :rowData="rowData">
  </ag-grid-vue>
</div>
</template>

<script>
import {
  AgGridVue
} from "@ag-grid-community/vue";
import Editor from './Editor.vue';

export default {
  name: 'App',
  data() {
    return {
      columnDefs: null,
      rowData: null,
      api: null
    }
  },
  components: {
    AgGridVue,
    Editor
  },
  beforeMount() {
    this.columnDefs = [{
        field: 'make',
        editable: true,
        cellEditor: 'agSelectCellEditor',
        cellEditorParams: {
          values: ['Porsche', 'Toyota', 'Ford', 'AAA', 'BBB', 'CCC']
        }
      },
      {
        field: 'price',
        editable: true,
        cellEditorFramework: 'Editor'
      },
      {
        field: 'hoge',
        editable: true,
      }
    ];

    this.rowData = [{
      make: 'Toyota',
      price: '35000',
      hoge: 'day'
    }, ];
  },
  methods: {
    onGridReady(params) {
      this.api = params.api;
    }
  }
}
</script>
