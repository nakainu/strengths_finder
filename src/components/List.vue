<template>
  <div>
    <b-container>
        <b-table striped hover :items="items" :fields="fields" @row-clicked="row"></b-table>
        <b-modal v-model="modalShow">
            <b-form @submit="edit">
                <b-form-group class="left" id="input-group-1" label="所属チーム:" label-for="input-1">
                    <b-form-select
                    id="input-1"
                    v-model="form.team"
                    :options="teams"
                    required
                    ></b-form-select>
                </b-form-group>

                <b-form-group class="left" id="input-group-2" label="氏名:" label-for="input-2">
                    <b-form-input
                    id="input-2"
                    v-model="form.name"
                    required
                    ></b-form-input>
                </b-form-group>
                
                <b-form-group class="left" id="input-group-3" label="strength1:" label-for="input-3">
                    <b-form-input
                    id="input-3"
                    v-model="form.strength1"
                    required
                    ></b-form-input>
                </b-form-group>

                <b-form-group class="left" id="input-group-4" label="strength2:" label-for="input-4">
                    <b-form-input
                    id="input-4"
                    v-model="form.strength2"
                    required
                    ></b-form-input>
                </b-form-group>

                <b-form-group class="left" id="input-group-5" label="strength3:" label-for="input-5">
                    <b-form-input
                    id="input-5"
                    v-model="form.strength3"
                    required
                    ></b-form-input>
                </b-form-group>

                <b-form-group class="left" id="input-group-6" label="strength4:" label-for="input-6">
                    <b-form-input
                    id="input-6"
                    v-model="form.strength4"
                    required
                    ></b-form-input>
                </b-form-group>

                <b-form-group class="left" id="input-group-7" label="strength5:" label-for="input-7">
                    <b-form-input
                    id="input-7"
                    v-model="form.strength5"
                    required
                    ></b-form-input>
                </b-form-group>
                <b-button type="submit">編集</b-button>
            </b-form>
        </b-modal> 
    </b-container>
  </div>
</template>

<script>
export default {
    data() {
        return {
            fields: ['id', 'team', 'name', 'strength1', 'strength2', 'strength3' , 'strength4', 'strength5'],
            items: [],
            modalShow: false,
            form: {
                id: null,
                team: null,
                name: '',
                strength1: '',
                strength2: '',
                strength3: '',
                strength4: '',
                strength5: '',
            },
            teams: [{ text: '選択してください', value: null }, 'MD', 'CRM', 'POS', 'コーポ', 'グループ内', 'グループ外外販', 'プロジェクト支援室', 'セールスマーケ', '新卒', '企画推進', '保守管理'],
        }
    },
    watch: {
        // レコードを更新した時に呼ばれる
        items: {
            handler: function () {
                this.axios.get('https://sheetdb.io/api/v1/3snlhppfxzhqj')
                .then( response => {
                    this.items = response.data;
                });
            },
            deep: true,
        }
    },
    created() {
        // apiからすべてのデータを取得
        this.axios.get('https://sheetdb.io/api/v1/3snlhppfxzhqj')
        .then( response => {
            this.items = response.data;
        });
    },
    methods: { 
        row(record) {
            this.form.id = record.id
            // フォームに値を代入
            this.form.team = record.team;
            this.form.name = record.name;
            this.form.strength1 = record.strength1;
            this.form.strength2 = record.strength2;
            this.form.strength3 = record.strength3;
            this.form.strength4 = record.strength4;
            this.form.strength5 = record.strength5;
            // modalの表示
            this.modalShow = !this.modalShow;
        },
        async edit(evt) {
            // レコードの編集
            evt.preventDefault()
            const url = 'https://sheetdb.io/api/v1/3snlhppfxzhqj/id/'
            this.axios.patch(url + this.form.id,{
                "data": {
                    "team": this.form.team,
                    "name": this.form.name,
                    "strength1": this.form.strength1,
                    "strength2": this.form.strength2,
                    "strength3": this.form.strength3,
                    "strength4": this.form.strength4,
                    "strength5": this.form.strength5
                    }
            }).then( response => {
                console.log(response.data);
                alert(this.form.name + 'さんを変更しました');
            });
            // modalの非表示
            this.modalShow = !this.modalShow;
        }
    }
}
</script>
