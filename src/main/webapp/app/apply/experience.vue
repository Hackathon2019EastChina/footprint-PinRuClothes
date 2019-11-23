<template>
  <div>
    <b-row>
    <b-col><h2>
        <b-button variant="info" class="pull-right" v-b-modal.modal-1>发布我的经历</b-button>
        <b-modal id="modal-1" title="你的留学经验">
        <b-form @submit="onSubmit" @reset="onReset" v-if="show">
            <b-form-group
                id="input-group-1"
                label="Title:"
                label-for="input-1"
                description="It will be shown to others."
            >
                <b-form-input
                id="input-1"
                v-model="form.title"
                required
                placeholder="Enter title"
                ></b-form-input>
            </b-form-group>
            <b-form-group
                id="input-group-4"
                label="Name:"
                label-for="input-4"
            >
                <b-form-input
                id="input-4"
                v-model="form.name"
                required
                placeholder="Enter name"
                ></b-form-input>
            </b-form-group>
            <b-form-group id="input-group-2" label="Content:" label-for="input-2">
                <b-form-input
                id="input-2"
                v-model="form.content"
                required
                placeholder="Enter content"
                ></b-form-input>
            </b-form-group>

            <b-form-group id="input-group-3" label="Country:" label-for="input-3">
                <b-form-select
                id="input-3"
                v-model="form.country"
                :options="countries"
                required
                ></b-form-select>
            </b-form-group>

            <b-button type="submit" variant="primary">Submit</b-button>
            <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
        </b-modal>
    </h2>  </b-col>
    </b-row>
    
    <b-table striped hover :items="items" ></b-table>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        items: [
          { title: "MSCS@CMU项目申请经验", last_reply_time: '2019.11.23', author: 'Macdonald' },
          { title: "Meng@UCB,一年制meng是否值得读", last_reply_time: '2019.11.22', author: 'Shaw' },
          { title: "东海岸与西海岸，不仅是时区差异", last_reply_time: '2019.11.8', author: 'Wilson' },
          { title: "19fall CSphD申请感想", last_reply_time: '2019.11.4', author: 'Carney' }
        ],
        form: {
          title: '',
          conetnt: '',
          name:'',
          country: null,
        },
        countries: [{ text: 'Select The Country', value: null }, 'US', 'UK', 'EU', 'AUS','JAP'],
        show: true
      }
    },
    created(){
        var name1 =sessionStorage.getItem('name');
        var title1 =sessionStorage.getItem('title');
        this.items.push({title:title1,last_reply_time:"2019.11.24",author:name1})
        console.log(this.items);
    },
    methods: {
      onSubmit() {
        console.log(this.items);
        sessionStorage.setItem('name', this.form.name)
        sessionStorage.setItem('title',this.form.title)
      },
      onReset(evt) {
        evt.preventDefault()
        // Reset our form values
        this.form.title = ''
        this.form.content = ''
        this.form.name = ''
        this.form.country = null
        // Trick to reset/clear native browser form validation state
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      }
    },
  }
</script>

<style scoped>
.pull-right{
    margin: 0 0 0 90%;
}
</style>