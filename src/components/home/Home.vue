<template>
  <div class="home">
    <!--<p>{{nameUser}}</p>
    <h2>{{myDetails()}}</h2>
    <div class="alert alert-info">
      <button type="button" class="close" data-dismiss="alert" aria-hidden="true">&times;</button>
      <strong>Title!</strong> Alert body ...
    </div>
    <ul>
      <li v-repeat="items">
        {{nameUser}} - {{$index}} &#45;&#45; {{nameFruit}}
      </li>
    </ul>
    <div>
      &lt;!&ndash;<a v-on="onkeyup | key 12">Trigger Event</a>&ndash;&gt;
      <ul v-repeat="item in items">
        &lt;!&ndash;<li v-on="click toggle(item)">Trigger Event</li>&ndash;&gt;
      </ul>
    </div>-->
    <home-top v-bind:items="items"></home-top>
    <router-view></router-view>
    <home-bottom></home-bottom>
  </div>
</template>

<script>
  import homeTop from './HomeTop';
  import homeBottom from './HomeBottom';

  export default {
    name: "Home",
    components: {
      homeTop,
      homeBottom
    },
    data() {
      return {
        nameUser: "Ivan",
        lastName: "Del",
        key: 12,
        n: 0,
        items: [
          {name: "Learn", sell: "20000", done: false},
          {name: "Community", sell: "14000", done: true},
          {name: "Try", sell: "14000", done: true}
        ]
      }
    },
    method: {
      myDetails() {
        return "My name is " + this.nameUser
      },
      toggle: function (item) {
        item.done = !item.done
      }
    },
    computed: {
      fullName: {
        get: function () {
          return this.nameUser + " - " + this.lastName
        },
        set: function (name) {
          const fName = name.split(" ");
          this.firstName = fName[0];
          this.lastName = fName[1];
        }
      }
    }
  }
</script>

<style scoped lang="scss">
  .home {
    position: relative;
  }
</style>
