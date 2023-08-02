- ### 1. Getting Started
        
    Some text explanation here

  - ### What is a Store?

    - [ ] A Store (like **Pinia**) is an entity holding state and business logic that is not bound to your Component tree. In othwe words, **it hosts global state**. It is a bit like a component that is always there and that everybody can read off and write to. It has **three concepts**, the *state*, *getters* and *actions* and it is safe to assume these concepts are the equivalent of *data*, *computed* and *methods* in components.

  - ### When should I use a Store?

    - [ ] A store should contain data that can be accessed throughout your application. This includes data that is used in many places, e.g. User information that is displayed in the navbar, as well as data that needs to be preserved through pages, e.g. a very complicated multi-step form.
   
    - [ ] On other hand, you should avoid including in the store local data that could be hosted in a component instead, e.g. the visibility of an element local to a page.
   
    - [ ] Not all applications need access to a global state, but if yours needs one, Pinia will make your life easier.

- ### 2. Core concepts
        
    Before diving into core concepts, we need to know that a store is defined using `definedStore()` and that it requires a **unique** name, passed as the first argument:

              
                        import { defineStore } from 'pinia'

                        // You can name the return value of `defineStore()`anything you want,
                        // but it is best to use the name of the store and surround it with ùse`
                        // and `Store`(e.g. `useUserStore`, `useCartStore`, `useProductStore`)
                        // the first argument is a unique id of the store across your application
                        export const useAlertStore = defineStore('alerts', {
                          // other options ...
                        })
  

    This name, also referred to as **id**, is necessary and is used by Pinia to connect the store to the devtools. Naming the returned function use... is a convention across composables to make it is usage idiomatic.

  `defineStore()` accepts two distinct values for its second argument: a Setup function or an Options object.


  - ### Option Stores
 
      Similar to Vue Options API, we can also pass an Options OBject with `state`, `actions`, and `getters` properties.
            
                        import { defineStore } from 'pinia'

                        export const useCounterStore = defineStore('counter', {
                          state: () => ({ count: 0, name: 'John Doe' }),
                          getters: {
                            doubleCount: (state) => state.count * 2,
                          },
                          actions: {
                            increment() {
                              this.count++;
                            }
                          }
                        })

    You can think of `state`as the `data`of the store, `getters` as the `computed` properties of the store, and `actions`as the `methods`.

    Option stores should feel intuitive and simple to get started with.


  - ### Setup Stores
 
      There is also another possible syntax to define stores. Similar to the Vue Composition API's **setup function**, we can pass in a function that defines reactive properties and methods and returns an object with the properties and methods we want to expose.
            
                        import { defineStore } from 'pinia'
                        import { ref, computed } from 'vue';

                        export const useCounterStore = defineStore('counter', () => {
                          const count = ref(0);
                          const name = ref('Eduardo');
                          const doubleCount = computed(() => count.value * 2);
                          function increment() {
                            count.value++
                          }
 
                          return { count, name, doubleCount, increment };
                        })

    In Setup Stores:

    - [ ] `ref()`s become `state`properties
    - [ ] `computed()`s become `getters`
    - [ ] `function()`s become `actions`

  - ### Using the store
 
      We are defining a store because the store will not be created until `use...Store()` is called within a component `<script setup>` (or within `setup()` **like all composables**):

                        <script setup>
                                import { useCounterStore } from '@/stores/counter'
        
                                // access the `store`variable anywhere in the component ✨
                                const store = useCounterStore()
                        </script>

      You can define as many stores as you want and **you should define each store in a different file** to get the most out of Pinia (like automatically alowwing your bundler to code split and providing TypeScript inference).

      Once the store is instantiated, you can access any property defined in `state`, `getters`, and `actions` directly on the store. We will look at these in detail in the next pages but autocompletion will help you.
