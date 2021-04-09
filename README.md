# Angular Interview Questions

Angular Interview Questions with examples

**1. What is difference b/w AngularJS and Angular?**

- AngularJS is Javascript based framework where as Angular is based on Typescript. Typescript is a superset of ES6,
  which is backward compatible with ES5.
- AngularJS based javascript uses terms of scope and controller while Angular uses hierarchy of components. Angular is
  component based(here component is directive with a template), while AngularJS uses directives.
- AngularJS is MVC based framework while Angular is service/controller based.
- AngularJS does not provide mobile support while Angular supports mobile.
- In AngularJS {{}} and special methods(ng-bind) are used to bind data between view and mode, where as in Angular ()
  and [] attributes are used to bind data between view and model.
- Dependency Injection is not used in AngularJS where as Hierarchical DI system is used in Angular.

Reference: https://stackify.com/angular-vs-angularjs-differences-between-angular-and-angularjs/

**2. What is a data binding?**

 Data binding is a core concept in Angular and allows to define communication between a component and the DOM. Data
  binding automatically keeps your page up-to-date based on your application's state.

  There are four forms of data binding(divided as 3 categories) which differ in the way the data is flowing.
    
1. **From the Component to the DOM:**

   **Interpolation:** {{ value }}: Adds the value of a property from the component

   **Property binding:** [property]=”value”: The value is passed from the component to the specified property or
       simple HTML attribute
2. **From the DOM to the Component:**

   **Event binding:** (event)=”function”: When a specific DOM event happens (eg.: click, change, keyup), call the
       specified method in the component
3. **Two-way data binding:** [(ngModel)]=”value”:

   Two-way data binding allows to have the data flow both ways. For example, in the below code snippet, both the 
   email DOM input and component email property are in sync