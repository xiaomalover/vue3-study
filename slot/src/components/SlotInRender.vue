<script>
import { h } from "vue";
export default {
  name: "SlotInRender",
  props: ["message"],
  render() {
    return h(
      "div",
      {},
      this.$slots.default({
        text: "From props: " + this.message,
        title: "From fixed value: Test title",
      })
    );
  },
};
</script>
