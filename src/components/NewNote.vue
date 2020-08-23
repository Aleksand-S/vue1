<template>
  <!-- new note -->
  <div class="new-note">

      <label>Title</label>
      <input v-model="note.title" type="text" />

      <!-- select @actStatus="changeStatus"-->
      <priority :note="note" />

    <label>Description</label>
    <textarea v-model="note.descr" style="margin-bottom: 10px"></textarea>
    <button class="btn btnPrimary" @click="addNote">New note</button>
  </div>
</template>

<script>
import priority from "@/components/ui/SelectPrior.vue"
export default {
  components: {
    priority
  },
  props: {
    note: {
      type: Object,
      required: true,
    },
    // status1: {
    //   type: String,
    //   required: true,
    // },
  },
  data() {
    return {
      // statt: this.status1
    }
  },
  methods: {
    addNote() {
      this.$emit("addNote", this.note)
    },
    changeStatus (data) {
      this.statt = data
    },
  },
};
</script>

<style lang="scss" scope>
  .new-note {
    text-align: center;
  }
</style>
