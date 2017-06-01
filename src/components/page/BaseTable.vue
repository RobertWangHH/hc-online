<template>
    <div class="table">
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item><i class="el-icon-menu"></i> 表格</el-breadcrumb-item>
                <el-breadcrumb-item>基础表格</el-breadcrumb-item>
            </el-breadcrumb>
        </div>

        <el-table :data="tableData" border style="width: 100%">
            <el-table-column prop="creatTime" label="日期" :formatter="formatDateStamp" sortable width="190">
            </el-table-column>
            <el-table-column prop="city" label="城市" width="150">
            </el-table-column>
            <el-table-column prop="address" label="地址" :formatter="formatter" width="250">
            </el-table-column>
            <el-table-column label="操作" width="180">
                <template scope="scope">
                    <el-button size="small"
                            @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
                    <el-button size="small" type="danger"
                            @click="handleDelete(scope.$index, scope.row)">删除</el-button>
                </template>
            </el-table-column>
        </el-table>
        <div class="pagination">
            <el-pagination
                    @current-change ="handleCurrentChange"
                    layout="prev, pager, next"
                    :page-size="size"
                    :total="total">
            </el-pagination>
        </div>
    </div>
</template>

<script>
    import {formatDate} from '../../../static/js/date.js';
    export default {
        data() {
            return {
                url: '',
                tableData: [],
                cur_page: 1,
                total:0,
                size:10
            }
        },
        created(){
            this.getData();
        },
        methods: {
            handleCurrentChange(val){
                this.cur_page = val;
                this.getData();
            },
            getData(){
                let self = this;
                if(process.env.NODE_ENV === 'development'){
                    self.url = '/zy/sell?page=';
                };
                self.$axios.get(self.url+self.cur_page).then((res) => {
                    self.tableData = res.data.data;
                    self.total = res.data.count;
                })
            },
            formatter(row, column) {
                return row.address;
            },
            formatDateStamp(row, column){
                if (row.creatTime == undefined) {
                     return "";
                }
                let date = new Date(row.creatTime);
                return formatDate(date, "yyyy-MM-dd hh:mm");
            },
            filterTag(value, row) {
                return row.tag === value;
            },
            handleEdit(index, row) {
                this.$message('编辑主键是'+(row.cfid)+'，哈哈');
            },
            handleDelete(index, row) {
                this.$message.error('删除第'+(index+1)+'行');
            }
        }
    }
</script>
