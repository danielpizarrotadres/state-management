- ### 1. Getting Started
        
    Some text explanation here

  - ### What is a Store?

    - [ ] A Store (like **Pinia**) is an entity holding state and business logic that is not bound to your Component tree. In othwe words, **it hosts global state**. It is a bit like a component that is always there and that everybody can read off and write to. It has **three concepts**, the *state*, *getters* and *actions* and it is safe to assume these concepts are the equivalent of *data*, *computed* and *methods* in components.

  - ### When should I use a Store?

    - [ ] A store should contain data that can be accessed throughout your application. This includes data that is used in many places, e.g. User information that is displayed in the navbar, as well as data that needs to be preserved through pages, e.g. a very complicated multi-step form.
   
    - [ ] On other hand, you should avoid including in the store local data that could be hosted in a component instead, e.g. the visibility of an element local to a page.
   
    - [ ] Not all applications need access to a global state, but if yours needs one, Pinia will make your life easier.

- ### 2. Core concepts
        
    - [ ] Some text explanation here
