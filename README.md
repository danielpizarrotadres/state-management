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
