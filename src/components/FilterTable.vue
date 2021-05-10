<template>
  <div style="width: 600px">
    <vue-table-dynamic 
      :params="params" 
      ref="table"
    >
    </vue-table-dynamic>
  </div>
</template>

<script>
import VueTableDynamic from 'vue-table-dynamic'
var tableData = [];

export default {
  name: 'FilterTable',
  data() {
    return {
      params: {
        data: tableData,
        header: 'row',
        enableSearch: true
      }
    }
  },
  mounted(){
    this.getDataForTable();
  },
  methods : {
    getDataForTable : function() {
      return fetch('https://api.publicapis.org/categories')
      .then(res => res.json())
      .then((response) => { 
        if (response != null) {
          var headcol = ["#", "Category"];
          tableData.push(headcol);
          response.forEach((element,index) => {
            var col = [];
            col.push(index+1);
            col.push(element);
            tableData.push(col);
          });
        }
        return response; 
      });
    }
  },
  components: { VueTableDynamic }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
