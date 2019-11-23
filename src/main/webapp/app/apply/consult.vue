<template>
  <div>
    <b-row>
    <b-col><h2>
        <b-button variant="info" class="pull-right" v-b-modal.modal-1>我要求助</b-button>
        <b-modal id="modal-1" title="请填写你的信息">
        <b-form @submit="onSubmit"  @reset="onReset" v-if="show">
<!--           @submit="onSubmit"
 -->            <b-form-group
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

            <b-form-group id="input-group-3" label="Target Country:" label-for="input-3">
                <b-form-select
                id="input-3"
                v-model="form.country"
                :options="countries"
                required
                ></b-form-select>
            </b-form-group>

            <b-form-group id="input-group-2" label="Other Content:" label-for="input-2">
                <b-form-input
                id="input-2"
                v-model="form.content"
                required
                placeholder="Enter content"
                ></b-form-input>
            </b-form-group>

            <b-form-group id="input-group-2" label="TOFEL:" label-for="input-2">
                <b-form-input
                id="input-2"
                v-model="form.tofel"
                required
                placeholder="Enter TOFEL"
                ></b-form-input>
            </b-form-group>
            <b-form-group id="input-group-2" label="GRE:" label-for="input-2">
                <b-form-input
                id="input-2"
                v-model="form.gre"
                required
                placeholder="Enter GRE"
                ></b-form-input>
            </b-form-group>
            <b-form-group id="input-group-2" label="GPA:" label-for="input-2">
                <b-form-input
                id="input-2"
                v-model="form.gpa"
                required
                placeholder="Enter GPA"
                ></b-form-input>
            </b-form-group>
            <b-form-group id="input-group-3" label="Your School:" label-for="input-3">
                <b-form-select
                id="input-3"
                v-model="form.school"
                :options="schools"
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
          { title: "CS@NJU 4.6/5.0+110+330 2020US选校", last_reply_time: '2019.11.23', author: 'Macdonald' },
          { title: "Top2 111+333 两段科研经历", last_reply_time: '2019.11.23', author: 'Shaw' },
          { title: "SE@NJU 4.65/5 一般TOEFL,gre 一篇sci二区", last_reply_time: '2019.11.23', author: 'Wilson' },
          { title: "Top2 3.7/4 MSRA实习+Upenn暑研", last_reply_time: '2019.11.23', author: 'Carney' }
        ],
        form: {
          title: '',
          conetnt: '',
          name:'',
          country: null,
          gpa:null,
          gre:null,
          tofel:null,
          school:null,
        },
        countries: [{ text: 'Select One', value: null }, 'US', 'UK', 'EU', 'AUS','JAP'],
        schools: [{ text: 'Select One', value: null }, 'OverSea', 'Top2', '985', '211','other schools'],
        show: true
      }
    },
   created(){
        //this.items=JSON.parse(sessionStorage.getItem('items'))
        //console.log(JSON.stringify(this.items[0]))
    },
    methods: {
      onSubmit(evt) {
        evt.preventDefault()
        this.items.push({title:this.form.title,last_reply_time:"2019.11.24",author:this.form.name})
        sessionStorage.setItem('items',JSON.stringify(this.items[this.items.length()-1]))
                alert(sessionStorage.getItem('items'))

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