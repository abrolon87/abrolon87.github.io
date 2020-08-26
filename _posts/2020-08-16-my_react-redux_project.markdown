---
layout: post
title:      "My React-Redux Project"
date:       2020-08-16 00:04:30 -0400
permalink:  my_react-redux_project
---


I was relieved to find that this project wasn't nearly as complicated as the last project I did. It is much bigger and there was a lot more setup to be done but it was less complicated. I decided to make an app that a user can log natural remedy products and their uses. 

## About React

React is made up of components. Components do help with keeping things organized however, the app gets very big very quickly. Different components have different responsabilities and in order to use them in other components, we need to export the component. We also need to import components in the components that we want to use them in. There are different kinds of components. Functional components, presentational components, 

### Props 

Props is an object of the properties of the object that it is passed into. This makes it easier to work dynamically. Props are not to be manipulated by the component that it is imported to. That is where "state" comes in.....

### State
"State" is the data that a component maintains. It can change it's own state. 

## About Redux 
Redux is something that we use to manage state. The cool thing about it is that Redux state is separate from the component tree and we can access whatever data we want from any component. We just need to connect the component. 

### About Thunk

Thunk is middleware that we can use in Redux to allow us to make calls to the API and control the flow. It gives us direct control of the dispatch method and allows us to do things asynchronously. 
