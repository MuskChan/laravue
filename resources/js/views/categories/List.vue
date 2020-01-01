<template>
  <div class="app-container">
    <el-table v-loading="loading" :data="list" border fit highlight-current-row>
      <el-table-column align="center" label="ID" width="80">
        <template slot-scope="scope">
          <span>{{ scope.row.id }}</span>
        </template>
      </el-table-column>

      <el-table-column align="center" label="Name" width="200">
        <template slot-scope="scope">
          <span>{{ scope.row.name }}</span>
        </template>
      </el-table-column>

      <el-table-column align="center" label="Code" width="200">
        <template slot-scope="scope">
          <span>{{ scope.row.code }}</span>
        </template>
      </el-table-column>

      <el-table-column align="center" label="Description">
        <template slot-scope="scope">
          <span>{{ scope.row.description }}</span>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
  import Resource from '@/api/resource';
  const categoryResource = new Resource('categories');

  export default {
    name: 'CategoryList',
    data() {
      return {
        list: [],
      };
    },
    created() {
      this.getList();
    },
    methods: {
      async getList() {
        const { data } = await categoryResource.list({});
        this.list = data;
      },
    },
  };
</script>
