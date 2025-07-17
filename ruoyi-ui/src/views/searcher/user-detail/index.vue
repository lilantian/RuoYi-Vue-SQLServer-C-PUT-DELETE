<template>
  <div>
    <el-container>
      <el-main>
        <el-form :model="form" label-width="0" :inline="true">
          <el-row>
            <el-col>
              <el-form-item>
                <el-button type="danger" plain icon="el-icon-plus" @click="addForm">条件</el-button>
              </el-form-item>
              <el-form-item>
                <el-button type="primary" icon="el-icon-search" @click="search">搜索</el-button>
              </el-form-item>
            </el-col>
          </el-row>
          <el-row v-for="(form, index) in forms" :key="index">
              <el-form-item label="">
                <el-select v-model="form.field" placeholder="选择查询字段">
                  <el-option label="字段1" value="field1"></el-option>
                  <el-option label="字段2" value="field2"></el-option>
                </el-select>
              </el-form-item>
              <el-form-item label="">
                <el-select v-model="form.condition" placeholder="选择查询条件">
                  <el-option label="等于" value="equals"></el-option>
                  <el-option label="不等于" value="notEquals"></el-option>
                  <el-option label="大于等于" value="greaterOrEquals"></el-option>
                </el-select>
              </el-form-item>
              <el-form-item label="">
                <el-input placeholder="值" v-model="form.value"></el-input>
              </el-form-item>
              <el-form-item label="">
                <el-col :span="7">
                  <el-select v-model="form.logic" placeholder="并且">
                    <el-option label="并且" value="and"></el-option>
                    <el-option label="或者" value="or"></el-option>
                  </el-select>
                </el-col>
                <el-col :span="1" :offset="1">
                  <el-button type="primary" @click="removeForm(index)">删除</el-button>
                </el-col>
              </el-form-item>
          </el-row>
        </el-form>
        <el-table :data="tableData" style="width: 100%">
          <el-table-column prop="table" label="表名"></el-table-column>
          <el-table-column prop="field" label="字段名"></el-table-column>
          <el-table-column prop="value" label="值"></el-table-column>
        </el-table>

        <el-pagination
          @size-change="handleSizeChange"
          @current-change="handleCurrentChange"
          :current-page="currentPage"
          :page-sizes="[10, 20, 30, 40]"
          :page-size="pageSize"
          layout="total, sizes, prev, pager, next, jumper"
          :total="100"
        >
        </el-pagination>
      </el-main>
    </el-container>
  </div>
</template>

<script>
export default {
  name: 'userDetail',
  data() {
    return {
      form: {
        keyword: '',
        table: '',
        field: '',
        condition: '',
        value: '',
        logic: ''
      },
      tableData: [
        { table: '表1', field: '字段1', value: '数值1' },
        { table: '表2', field: '字段2', value: '数值2' }
      ],
      forms: [
        { field: "", condition: "", value: "", logic: 'and' },
      ],
      currentPage: 1,
      pageSize: 10
    }
  },
  methods: {
    search() {
      // 处理搜索逻辑
    },
    handleSizeChange(size) {
      this.pageSize = size
    },
    handleCurrentChange(page) {
      this.currentPage = page
    },
    addForm() {
      this.forms.push({ field: "", condition: "", value: "" });
    },
    removeForm(index) {
      this.forms.splice(index, 1);
    },
  }
}
</script>

<style scoped>

</style>
