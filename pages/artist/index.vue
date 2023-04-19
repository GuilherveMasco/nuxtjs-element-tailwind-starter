<template>
    <div>
        <el-table
        :data="tableData"
        style="width: 100%">
        <el-table-column
            prop="name"
            label="Nome"
            width="180">
        </el-table-column>
        <el-table-column
            prop="description"
            label="Descrição"
            width="180">
        </el-table-column>
        <el-table-column align="right">
            <template slot="header" slot-scope="scope">
                <el-button
                    size="mini"
                    type="primary"
                    @click="handleAdd(scope.$index, scope.row)"
                >
                    Adicionar
                </el-button>
            </template>
        </el-table-column>
        </el-table>

        <el-drawer
            title="Cadastrar Artista"
            :visible.sync="drawer"
            direction="rtl">
            <el-form ref="ruleForm" :model="ruleForm" :rules="rules" label-width="120px">
                <el-form-item label="Nome" prop="name">
                    <el-input v-model="ruleForm.name"></el-input>
                </el-form-item>
                <el-form-item label="Descrição" prop="description">
                    <el-input v-model="ruleForm.description"></el-input>
                </el-form-item>
                <el-form-item label="Imagem" prop="image">
                    <el-input v-model="ruleForm.image"></el-input>
                </el-form-item>
                <el-form-item>
                    <el-button type="primary" @click="submitForm('ruleForm')">
                        Adicionar
                    </el-button>
                    <el-button @click="resetForm('ruleForm')">
                        Cancelar
                    </el-button>
                </el-form-item>
            </el-form>
        </el-drawer>
    </div>
</template>

  <script>
    export default {
        data() {
            return {
                drawer: false,
                tableData: [],
                ruleForm: {
                    name: '',
                    description: '',
                    image: ''
                },
                rules: {
                    name: [
                        { required: true, message: 'Por favor, insira o nome do artista', trigger: 'blur' },
                    ],
                    description: [
                        { required: true, message: 'Por favor, insira a descrição do artista', trigger: 'blur' },
                    ],
                    image: [
                        { required: true, message: 'Por favor, insira a imagem do artista', trigger: 'blur' },
                    ],
                }
            }
        },

        mounted() {
            this.getArtists()
        },

        methods: {
            async getArtists() {
                try {
                    const response = await this.$axios.$get('/artists/list')
                    this.tableData = response.data
                } catch (error) {
                    this.$notify.error({
                        title: 'Erro',
                        message: 'Erro ao carregar artistas'
                    })
                }
            },
            handleAdd(index, row) {
                this.drawer = true
            },
            submitForm(formName) {
                this.$refs[formName].validate(async (valid) => {
                    if (valid) {
                        try{
                            await this.$axios.$post('/artists/create', this.ruleForm)
                            this.$notify.success({
                                title: 'Sucesso',
                                message: 'Artista cadastrado com sucesso'
                            })
                            this.resetForm(formName)
                            this.getArtists()
                        } catch (error) {
                            this.$notify.error({
                                title: 'Erro',
                                message: 'Erro ao cadastrar artista'
                            })
                            return false;
                        }
                    } else {
                        this.$notify.error({
                            title: 'Erro',
                            message: 'Preencha todos os campos'
                        })
                        return false;
                    }
                });
            },
            resetForm(formName) {
                this.$refs[formName].resetFields();
                this.drawer = false
            }
        },
    }
  </script>