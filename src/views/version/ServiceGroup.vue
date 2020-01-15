<template>
    <div>
        <el-table style="width: 100%">
            <el-table-column
                prop="ServiceType"
                label="服务类型"
                min-width>
            </el-table-column>
            <el-table-column
                prop="comment"
                label="备注"
                min-width>
            </el-table-column>
            <el-table-column
                prop="operation"
                label="操作"
                min-width>
                <template slot-scope="scope">
                    <el-button @click="handleClick(scope.row)" type="text" size="small">查看</el-button>
                    <el-button type="text" size="small">编辑</el-button>
                </template>
            </el-table-column>
        </el-table>
        <div>
            <el-link href="https://element.eleme.io" target="_blank">
                <el-button type="primary">添加服务类型</el-button>
            </el-link>
        </div>
    </div>
</template>

<script>
    export default {
        name: "VersionGroup",
        data() {
            return{
                ServiceGroup: [],
            };
        },
        created() {
            this.getServiceGroup()
        },
        methods: {
            getServiceGroup(){
                this.axios.defaults.baseURL = 'http://localhost:8000';
                this.axios.get('/ServiceType/')
                    .then(function (response) {
                        this.ServiceGroup.push(response.data)
                        console.log(response);
                    }
                ).catch(function (error) {
                    console.log(error)
                })
            }
        },
    }
</script>

<style scoped>

</style>