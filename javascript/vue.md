# Vue.js / Vue

## Basics

- <a href="https://vuejs.org/" target="_blank">Vue.org</a>
- <a href="https://cli.vuejs.org/" target="_blank">Vue CLI</a>
- <a href="https://router.vuejs.org/" target="_blank">Vue Router</a>
- <a href="https://vuex.vuejs.org/" target="_blank">Vuex</a>
- <a href="https://vuematerial.io" target="_blank">Vue Material</a>

### Component about.vue

```javascript
<template>
  <div>
    <h1>{{title}}</h1>
  </div>
</template>

<script>
export default {
  name: 'about',
  props: {
    state: {
      type: String,
      default: 'INIT'
    },
    showFadeIn: {
      type: Boolean,
      default: false
    },
    loadedGame: {
      type: Boolean,
      default: false
    },
    gameMode: {
      type: Object,
      default: function () {
        return {}
      }
    }
  },
  data() {
    return {
      title: 'This is an linked about page'
    }
  },
  watch: {},
  computed: {},
  beforeCreate() {},
  created() {},
  beforeMount() {},
  mounted() {},
  beforeUpdate() {},
  updated() {},
  beforeDestroy() {},
  destroyed() {}
}
</script>

<style scoped>
</style>
```

## Libraries

## Docs

- <a href="https://codeburst.io/dependency-injection-with-vue-js-f6b44a0dae6d" target="_blank">Dependency injection with Vue.js</a>

## How to

### Create a Service

You have 4 options:

- Stateless service: then you should use <a href="https://vuejs.org/v2/guide/mixins.html" target="_blank">mixins</a>
- Statefull service: use Vuex
- Export service and import from a vue code
- any javascript global object
- <a href="https://www.npmjs.com/package/axios" target="_blank">axios</a>
- <a href="https://github.com/pagekit/vue-resource" target="_blank">vue-resource</a>

RestResource.js:

```javascript
export default class RestResource {

  sendRequest() {
    // Use vue-resource or any other http library to send your request
  }

}
```

And in component this resource is required:

```javascript
import RestResource from './services/RestResource';

const restResourceService = new RestResource();

restResourceService.sendRequest();
```

#### Create Service with axios sample 1

./service/myApi.js:

```javascript
import axios from 'axios'

export default axios.create({
  baseURL: 'http://localhost:3000/api/v1',
  timeout: 5000,
  headers: {
    'X-Auth-Token': 'f2b6637ddf355a476918940289c0be016a4fe99e3b69c83d',
    'Content-Type': 'application/json'
  }
})
```

And in component this resource is required:

```javascript
methods: {
 getProducts () {
     myApi.get('products?id=' + prodId).then(response =>  this.product = response.data)
  }
}
```

And reuse it then via mixins:

```javascript
// define a mixin object
var myMixin = {
  methods: {
     getProducts () {
         myApi.get('products?id=' + prodId).then(response =>  this.product = response.data)
      }
  }
}

// define a component that uses this mixin
var Component = Vue.extend({
  mixins: [myMixin]
})

// alternate way to have a mixin while initialising
new Vue({
  mixins: [myMixin],
  created: function () {
    console.log('other code')
  }
})
```

#### Create Service with axios sample 2

./service/api.js:

```javascript
import axios from 'axios'

import { isProduction, env } from '@/utils/env'

var http = null // not possible to create a private property in JavaScript, so we move it outside of the class, so that it's only accessible within this module

class APIProvider {
  constructor ({ url }) {
    http = axios.create({
      baseURL: url,
       headers: { 'Content-Type': 'application/json' }
    })
  }

  // Authorization
  login (token) {
    http.defaults.headers.common.Authorization = `Bearer ${token}`
  }

  logout () {
    http.defaults.headers.common.Authorization = ''
  }

  // REST Methods
  find ({ resource, query }) {
    return http.get(resource, {
      params: query
    })
  }

  get ({ resource, id, query }) {
    return http.get(`${resource}/${id}`, {
      params: query
    })
  }

  create ({ resource, data, query }) {
    return http.post(resource, data, {
      params: query
    })
  }

  update ({ resource, id, data, query }) {
    return http.patch(`${resource}/${id}`, data, {
      params: query
    })
  }

  destroy ({ resource, id }) {
    return http.delete(`${resource}/${id}`)
  }
}

export default new APIProvider({
  url: env('API_URL')  // We assume 'https://api.example.com/v1' is set as the env variable
})
```

main.js:

```javascript
import api from '@/src/utils/api'

Vue.$api = api

Object.defineProperty(Vue.prototype, '$api', {
  get () {
    return api
  }
})
```

And in component this resource is required:

```javascript
<template>
  <div class="my-component">My Component</div
</template>

<script>
export default {
  name: 'MyComponent',
  data () {
    return {
      data: []
    }
  },
  async created () {
    const response = await this.$api.find({ resource: 'tasks', query: { page: 2 } })

    this.data = response.data
  }
}
</script>
```

or in actions.js from Vuex:
```javascript
// actions.js from Vuex
import Vue from 'vue'

export async function fetchTasks ({ commit }) {
  const response = await Vue.$api.find({ resource: 'tasks', query: { page: 2 } })

  commit('SAVE_TASKS', response.data)

  return response
}
```

#### Create Service with vue-resource

./service/PostsService.js:

```javascript
import Vue from 'vue'

export default {
  get() {
    return Vue.http.get('/api/posts)
  }
}
```

And in component this resource is required:

```javascript
import PostsService from '../services/PostsService'

export default {
  data() {
   return {
     items: []
   }
  },
  created() {
   this.fetchPosts()
  },
  methods: {
   fetchPosts() {
    return PostsService.get()
      .then(response => {
        this.items = response.data
      })
   }
  }
}
```

See also <a href="https://github.com/bedakb/vuewp/tree/master/public/app/themes/vuewp/app" target="_blank">github: bedakb/vuewp</a>

### Create Plugins

Sample for a new plugin

```javascript

var myPlugin = {
        install: function (Vue, options) {
            //private
            var myPrivateProperty = 'Private property';

            //instance properties and methods
            Vue.prototype.$myPublicProperty = 'Public Property';

            Vue.prototype.$myAddedMethod = function () {
                return myPrivateProperty;
            };
            Vue.prototype._getData = function (url) {
                return url;
            };

            //static properties and methods
            Vue.myStaticProperty = 'My static prop';
            Vue.myStaticMethod = function () {
                console.log('in');
            }
        }
    };

    Vue.use(myPlugin);

    new Vue({
        el: '#app',
        created: function () {
            //using instance
            console.log(this.$myAddedMethod());
            console.log('my get data: ' + this._getData('some url'));
            console.log(this.$myPublicProperty);

            //using static
            console.log(Vue.myStaticProperty);
            Vue.myStaticMethod();
        }
    });
```