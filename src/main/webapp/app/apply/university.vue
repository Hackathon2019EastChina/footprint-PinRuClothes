<template>
  <div>
    <b-row>
    <b-col><h2>
        <b-button variant="info" class="pull-right" v-b-modal.modal-1>发布院校信息</b-button>
        <b-modal id="modal-1" title="院校分享">
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
                label="School:"
                label-for="input-4"
            >
                <b-form-input
                id="input-4"
                v-model="form.school"
                required
                placeholder="Enter school"
                ></b-form-input>
            </b-form-group>
            <b-form-group id="input-group-2" label="Introduction:" label-for="input-2">
                <b-form-input
                id="input-2"
                v-model="form.content"
                required
                placeholder="Enter content"
                ></b-form-input>
            </b-form-group>

            <b-form-group id="input-group-3" label="Major:" label-for="input-3">
                <b-form-select
                id="input-3"
                v-model="form.major"
                :options="majors"
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
        count:0,
        items: [
          { title: "院校巡礼:Stanford", last_reply_time: '2019.11.23', author: 'Macdonald' },
          { title: "UCBerkeley申请情况分析", last_reply_time: '2019.11.23', author: 'Shaw' },
          { title: "CS@CMU项目介绍与近年数据", last_reply_time: '2019.11.23', author: 'Wilson' },
          { title: "2020MIT金工申请前景", last_reply_time: '2019.11.23', author: 'Carney' }
        ],
        form: {
          title: '',
          conetnt: '',
          school:'',
          major: null,
        },
        majors: [{ text: 'Select The Major', value: null }, '理学', '商科', '社科文学', '信息','工科'],
        show: true
      }
    },
    created(){
        if(sessionStorage.getItem('items')!=null)
        this.items=JSON.parse(sessionStorage.getItem('items'))
    },
    methods: {
      onSubmit(evt) {
        //evt.preventDefault()
        this.items.push({title:this.form.title,last_reply_time:"2019.11.24",author:this.form.name})
        var temp=this.items
        sessionStorage.setItem('items',JSON.stringify(temp))
        //alert(sessionStorage.getItem('items'))
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