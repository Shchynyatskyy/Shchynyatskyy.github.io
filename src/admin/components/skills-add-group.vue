<template lang="pug">
  .add-new-skills-group
    skills-card
      template(slot="title")
        add-group-name(
          :value="value"
          :errorText="errorText"
          @input="$emit('input', $event)"
          @approve="$emit('approve')"
          @closeOrRemove="$emit('closeOrRemove')"
        )
      template(slot="content")
        .add-new
          add-new-skill(
            :blocked="addingBlocked"
          )
</template>

<script>
export default {
  components: {
    skillsCard: () => import("components/card.vue"),
    addNewSkill: () => import("components/skills-add-item.vue"),
    addGroupName: () => import("components/skills-add-group-name.vue")
  },
  props: {
    value: String,
    errorText: String
  },
  data() {
    return {
      addingBlocked: true,
      editMode: true
    };
  }
};
</script>

<style lang="pcss" scoped>
.add-new {
  padding-left: 18%;
  margin-top: auto;
}
.add-new-skills-group {
  height: 100%;
}
</style>


