<script>
import { h } from "vue";
import Child from "./Child.vue";
export default {
  name: "SlotInChildRender",
  compoent: [Child],
  render() {
    // One child component, not use arr
    /* return h('div', 
        h(
          Child,
          {},
          // 将 `slots` 以 { name: props => VNode | Array<VNode> } 的形式传递给子对象。
          {
            test: (props) => h('h1', props.text)
          },
        )
    ) */

    //Multiple child component, use arr
    return h("div", [
      h(
        Child,
        {},
        // 将 `slots` 以 { name: props => VNode } 的形式传递给子对象。
        {
          test: (props) => h("h1", props.text),
        }
      ),
      h(
        Child,
        {},
        // 将 `slots` 以 { name: props => Array<VNode> } 的形式传递给子对象。
        {
          test: (props) => [h("h1", props.text), h("h1", props.title)],
        }
      ),
    ]);
  },
};
</script>
