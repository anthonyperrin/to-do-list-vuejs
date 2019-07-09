<template>
  <div class="todos">
    <div class="container">
      <div class="row">
        <div class="col-12">
          <div class="content mb-4">
            <div class="row-fluid mt-2">
              <div class="col-12">
                <div style="float: right" class="form-inline">
                  <i class="fas fa-filter mr-2"></i>
                  <input
                    class="form-control mr-3"
                    type="text"
                    placeholder="Filter ..."
                    v-model="filterString"
                    v-on:keyup="doFilter()"
                  />
                </div>
              </div>
            </div>
            <div class="row-fluid" style="width: 100%;">
              <h3 class="my-3 ml-3" style="width: 100%;">To-Dos<span class="lf-info"> - List of the things you have to do today.</span>
              </h3>
              <div class="list-group" style="width: 100%;">
                <a
                  v-for="toDo in this.toDosFiltered"
                  v-bind:key="toDo.Id"
                  class="list-group-item list-group-item-action d-flex justify-content-between align-items-center cursor-pointer"
                >
                  <div>
                    <span>
                      <span class="td-content">Item {{toDo.Id}}</span>
                      <br />
                      <span class="lf-info">{{toDo.Content}}</span>
                    </span>
                  </div>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Todos",
  created: function() {
    this.initToDos();
    this.filterString = "";
  },
  data: function() {
    return {
      toDos: [],
      toDosFiltered: [],
      filterString: ""
    };
  },
  methods: {
    initToDos: function() {
      this.toDos = [
        {
          Id: 1,
          Content: "Learn Vue.js"
        },
        {
          Id: 2,
          Content: "Enjoy!"
        }
      ];
      this.toDosFiltered = this.toDos;
    },
    deleteToDo: function(id) {
      let todo = this.toDos.filter(t => t.Id == id);
      this.toDos.splice(this.toDos.indexOf(todo) - 1, 1);
    },
    addToDo: function(toDo) {
      this.toDos = this.toDos.push(toDo);
    },
    doFilter: function() {
      console.log(this.filterString);
      this.toDosFiltered = this.toDos.filter(
        t =>
          t.Content.toUpperCase().indexOf(this.filterString.toUpperCase()) >= 0
      );
    }
  }
};
</script>

<style scoped>
.todos {
  margin-top: 200px;
}

h3 {
  letter-spacing: 1px;
  font-size: 24px;
  font-weight: 400;
}

.content {
  padding: 5px;
  border-radius: 10px;
  background: white;
  box-shadow: 0 2px 6px 0 hsla(0, 0%, 0%, 0.2);
}

.lf-cta {
  width: 100%;
  border-radius: 0 0 10px 10px;
  background: hsla(271, 100%, 30%, 0.2);
  color: hsla(271, 100%, 30%, 0.8);
  letter-spacing: 1px;
  text-transform: uppercase;
  font-weight: 700;
  font-size: 14px;
}

.lf-cta:hover {
  transition: all 0.25s;
  color: hsla(271, 100%, 30%, 0.8);
  background: hsla(271, 100%, 30%, 0);
}

.offset-top {
  margin-top: -150px;
}

.lf-avatar {
  height: 47px;
  width: 47px;
  border-radius: 50%;
  float: left;
}

.badge {
  padding: 7px 12px;
}

.badge-hc {
  background: hsla(360, 100%, 30%, 0.2);
  color: hsla(360, 100%, 22%, 0.8);
}

.badge-casual {
  background: hsla(106, 100%, 22%, 0.2);
  color: hsla(106, 100%, 18%, 0.8);
}

.badge-mc {
  background: hsla(58, 100%, 22%, 0.2);
  color: hsla(58, 100%, 18%, 0.8);
}

.lf-igname {
  font-weight: bold;
}

.lf-info {
  font-size: 14px;
  font-weight: 500;
  color: hsl(214, 7%, 47%);
}

.list-group-item {
  border: none;
  border-radius: 5px;
  padding: 12px 10px;
}

.list-group-item:hover {
  transition: background 0.25s;
  background: hsla(271, 100%, 30%, 0.2);
}

.cursor-pointer {
  cursor: pointer;
}
</style>
