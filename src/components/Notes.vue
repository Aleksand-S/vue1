<template>
  <!-- note list -->
  <div class="notes">
    <div class="note"
    :class="{ full: !grid }"
    v-for="(note, index) in notes" :key="index"
    :style="{backgroundColor: colorChanger(note.status)}"
    >
      <div class="note-header" :class="{ full: !grid }" >
        <titleNote :currNote=note />
        <p style="cursor: pointer;" @click="removeNote(index)">X</p>
      </div>

      <div class="note-body">
        <p>{{ note.descr }}</p>
        <span>{{ note.date }}</span>
      </div>
    </div>
  </div>
</template>

<script>
import titleNote from "@/components/Title.vue"
export default {
  components: {
    titleNote,
  },
  data () {
    return {
    }
  },
  props: {
    notes: {
      type: Array,
      required: true,
    },
    grid: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    removeNote(index) {
      this.$emit("remove", index);
    },
    colorChanger (sta) {
      if (sta == 'стандарт') return "white"
      if (sta == 'важно') return "yellow"
      if (sta == 'очень важно') return "red"
    },
  },
  computed: {
  },
};
</script>

<style lang="scss">
.notes {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  padding: 40px 0;
}
.note {
  width: 48%;
  padding: 18px 20px;
  margin-bottom: 20px;
  background-color: #ffffff;
  transition: all 0.25s cubic-bezier(0.02, 0.01, 0.47, 1);
  box-shadow: 0 30px 30px rgba(0, 0, 0, 0.02);
  &.hover {
    box-shadow: 0 30px 30px rgba(0, 0, 0, 0.04);
    transform: translate(0, -6px);
    transition-delay: 0s !important;
  }

  &.full {
    width: 100%;
  }
}
.note-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  h1 {
    font-size: 32px;
  }
  p {
    font-size: 22px;
    color: blue;
  }
  svg {
    margin-right: 12px;
    color: #999999;
    &.active {
      color: blue;
    }
    &:last-child {
      margin-right: 0;
    }
  }
  &.full {
    justify-content: center;
    p {
      margin-right: 16px;
      &:last-child {
        margin-right: 0;
      }
    }
  }
}
.note-body {
  p {
    margin: 20px 0;
  }
  span {
    font-style: 14px;
    color: #999999;
  }
}
</style>