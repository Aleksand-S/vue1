<template>
<div>
  <label>Priority</label>
  <select v-model="note.status" >
    <option v-for="priority in priorities" :key="priority.id">{{ priority.name }}</option>
  </select>
</div>
</template>

<script>
export default {
  props: {
    note: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      priorities: [
        { id: 1, name: "стандарт" },
        { id: 2, name: "важно" },
        { id: 3, name: "очень важно" },
      ],
    };
  },
};
</script>

<style lang="stylus" scoped></style>