<template>
    <div class="group realtimedb">
        <h2>Realtime Datastore</h2>
        <div class="input-group half left">
            <label>Firstname</label>
            <input 
              type="text"
              v-model="firstname"
              @input="handleFisrtNameUpdate()"
            />
        </div>
        <div class="input-group half">
            <label>Lastname</label>
            <input 
              type="text" 
              v-model="lastname"
              @input="handleLastNameUpdate()"
            />
        </div>
    </div>
</template>
<script>
export default {
    name: 'my-record',
    props: ["ds"],
    data() {
        return {
            firstname: "",
            lastname: ""
        };
    },
    created() {
        this.record = this.ds.record.getRecord("test/johndoe");

        this.record.subscribe(values => {
            this.firstname = values.firstname;
            this.lastname = values.lastname;
        });
    },
    methods: {
        handleFisrtNameUpdate() {
            this.record.set("firstname", this.firstname);
        },
        handleLastNameUpdate() {
            this.record.set("lastname", this.lastname);
        }
    }
};
</script>