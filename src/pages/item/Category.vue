<template>
  <v-card>
      <v-flex xs12 sm10>
        <v-tree url="/item-services/category/list"
                :isEdit="isEdit"
                @handleAdd="handleAdd"
                @handleEdit="handleEdit"
                @handleDelete="handleDelete"
                @handleClick="handleClick"
        />
      </v-flex>
  </v-card>
</template>

<script>
  import {treeData} from "../../mockDB";

  export default {
    name: "category",
    data() {
      return {
        isEdit:true,
       /* treeData*/
      }
    },
    methods: {
      handleAdd(node) {
        console.log("add .... ");
        console.log(node);
        this.$http.get("/item-services/category/add",{
          params:{
            node
          }
        }).then(() => {
          this.$message.success("添加成功！");
        })
          .catch(() => {
            this.$message.error("添加失败！");
          });
      },
      handleEdit(id, name) {
        console.log("edit... id: " + id + ", name: " + name)
        this.$http.get("/item-services/category/edit",{
          params:{
            id,
            name
          }
        }).then(() => {
          this.$message.success("修改成功！");
        })
          .catch(() => {
            this.$message.error("修改失败！");
          });
      },
      handleDelete(id) {
        console.log("delete ... " + id)
        this.$http.get("/item-services/category/delete",{
          params:{
            id,
          }
        }).then(() => {
          this.$message.success("删除成功！");
        })
          .catch(() => {
            this.$message.error("删除失败！");
          });
      },
      handleClick(node) {
        console.log(node)
      }
    }
  };
</script>

<style scoped>

</style>
